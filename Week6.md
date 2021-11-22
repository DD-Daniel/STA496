Start to replicate the paper.

## **packages included:** 

### **data cleaning:**

install.packages("tidyverse")
library(tidyverse)
install.packages("pastecs")
library(pastecs)
install.packages("ltm")
library(ltm)
install.packages("psych")
library(psych)
install.packages("multilevel")
library(multilevel)

source("functions.R")

ed_level_fac_convert <- function(x){
  x[x == 1] <- "primary"
  x[x == 2] <- "secondary"
  x[x == 3] <- "A-level"
  x[x == 4] <- "undergraduate"
  x[x == 5] <- "postgraduate"
  fac <- factor(x)
  return(fac)
}

employ_level_fac_convert <- function(x){
  x[x == 1] <- "student"
  x[x == 2] <- "homemaker"
  x[x == 3] <- "unemployed"
  x[x == 4] <- "employed parttime"
  x[x == 5] <- "employed fulltime"
  x[x == 6] <- "retired"
  fac <- factor(x)
  return(fac)
}

income_level_fac_convert <- function(x){
  x[x == 1] <- "10.000 or less"
  x[x == 2] <- "10.001 - 30.000"
  x[x == 3] <- "30.001 - 50.000"
  x[x == 4] <- "50.001 - 70.000"
  x[x == 5] <- "70.001 or more"
  x[x == 6] <- "Prefer not to say"
  fac <- factor(x)
  return(fac)
}

covid_diagnosis_convert <- function(x){
  x[x == 1] <- "Yes, confirmed"
  x[x == 2] <- "Yes, but not confirmed"
  x[x == 3] <- "I am not sure, but think so"
  x[x == 4] <- "I am not sure, but don't think so"
  x[x == 5] <- "No"
  x[x == 6] <- "I don't know"
  fac <- factor(x)
  return(fac)
}

reversecode <- function(x){
  if (x == 1){
    x <- 5
  }
  else if (x == 2){
    x <- 4
  }
  else if (x == 4){
    x <- 2
  }
  else if (x == 5){
    x <- 1
  }
  else if (x == 6){
    x <- NA
  }
  return(x)
}

nacode <- function(x){
  if (x == 6){
    x <- NA
  }
  return(x)
}

kg_convert <- function(x){
  kg_buffer <- rep(0, nrow(x))
  for (i in seq(1, nrow(x))){
    if (x$objectiverisk_measurechoice1[i] == 2){
      st <- as.numeric(x$objectiverisk_weightstone[i])
      lbs <- as.numeric(x$objectiverisk_weightpounds[i])
      total_lbs <- st*14 + lbs
      kgs <- total_lbs/2.2046226218
      kg_buffer[i] <- kgs
    } else if (x$objectiverisk_measurechoice1[i] == 1){
      kgs <- as.numeric(x$objectiverisk_weightkilo[i])
      kg_buffer[i] <- kgs
    }
  }
  return(kg_buffer)
}

cm_convert <- function(x){
  cm_buffer <- rep(0, nrow(x))
  for (i in seq(1, nrow(x))){
    if (x$objectiverisk_measurechoice2[i] == 2){
      ft <- as.numeric(x$objectiverisk_heightfeet[i])
      inch <- as.numeric(x$objectiverisk_heightinches[i])
      total_inch <- ft*12 + inch
      centimetres <- total_inch*2.54
      cm_buffer[i] <- centimetres
    } else if (x$objectiverisk_measurechoice2[i] == 1){
      centimetres <- as.numeric(x$objectiverisk_heightcm[i])
      cm_buffer[i] <- centimetres
    }
  }
  return(cm_buffer)
}

objective_risk_scores <- function(x){
  adjustment <- rep(0, nrow(x))

  for (i in seq(1,nrow(x))){
    
    # Calculating score due to age
    if (x$objectiverisk_age[i] > 80){
      adjustment[i] <- adjustment[i] + 6
    } else if (x$objectiverisk_age[i] > 70){
      adjustment[i] <- adjustment[i] + 4
    } else if (x$objectiverisk_age[i] > 60){
      adjustment[i] <- adjustment[i] + 2
    } else if (x$objectiverisk_age[i] > 50){
      adjustment[i] <- adjustment[i] + 1
    }
    
    # Calculating score due to sex at birth
    if (x$objectiverisk_gender[i] == 1){
      adjustment[i] <- adjustment[i] + 1
    }
    
    # Ethnicity
    if (x$objectiverisk_ethnicity[i] == 5){
      adjustment[i] <- adjustment[i] + 2
    } else if (x$objectiverisk_ethnicity[i] == 7){
      adjustment[i] <- adjustment[i] + 1
    } else if (x$objectiverisk_ethnicity[i] == 8){
      adjustment[i] <- adjustment[i] + 1
    } else if (x$objectiverisk_ethnicity[i] == 9){
      adjustment[i] <- adjustment[i] + 1
    }
    
    # calculating diabetes and obesity
    # Ethnicity
    if (x$objectiverisk_diabetes[i] == 4){
      adjustment[i] <- adjustment[i] + 2
    } else if (x$objectiverisk_diabetes[i] == 1){
      adjustment[i] <- adjustment[i] + 1
    }
    
    # adding BMI
    if (x$bmi[i] >= 35){
      adjustment[i] <- adjustment[i] + 1
    }
    
    # calculating cardiovascular disease
    if (x$objectiverisk_cardovascular[i] == 1){
      adjustment[i] <- adjustment[i] + 1
    } else if (x$objectiverisk_cardovascular[i] == 2){
      adjustment[i] <- adjustment[i] + 2
    }
    
    # adding pulmonary disease
    if (x$objectiverisk_pulmonary[i] == 1){
      adjustment[i] <- adjustment[i] + 1
    } else if (x$objectiverisk_pulmonary[i] == 2){
      adjustment[i] <- adjustment[i] +2
    }
    
    # adding corticosteroids use
    if (!is.na(x$objectiverisk_corticosteroids[i])){
      if (x$objectiverisk_corticosteroids[i] == 1){
        adjustment[i] <- adjustment[i] + 1
      }
    }
    # malignant neoplasm
    if (x$objectiverisk_malignantneoplasm[i] == 1){
      adjustment[i] <- adjustment[i] + 3
    } else if (x$objectiverisk_malignantneoplasm[i] == 2){
      adjustment[i] <- adjustment[i] +1
    }
    
    # rheumatological conditions
    if (x$objectiverisk_rheumatological[i] == 1){
      adjustment[i] <- adjustment[i] + 2
    }
    
    # immunosuppressant therapy
    if (x$objectiverisk_immunosuppressant[i] == 1){
      adjustment[i] <- adjustment[i] +2
    }

  }
  return(adjustment)
}

reversecode_rp <- function(x){
  if (x == 1){
    x <- 5
  }
  else if (x == 2){
    x <- 4
  }
  else if (x == 4){
    x <- 2
  }
  else if (x == 5){
    x <- 1
  }
  return(x)
}

min_max_norm <- function(x, min, max){
  buffer <- rep(0, length(x))
  for (i in seq_along(buffer)){
    buffer[i] <- (x[i]-min)/(max-min)
  }
  return(buffer)
}

risk_attitudes_sum <- function(x){
  preferences <- rep(0, nrow(x))
  for (i in seq_along(preferences)){
    likelihood <- c(x[[i,51]], x[[i,52]], x[[i,53]], x[[i,54]], x[[i,55]], x[[i,56]])
    perception <- c(x[[i,57]], x[[i,58]], x[[i,59]], x[[i,60]], x[[i,61]], x[[i,62]])
    benefit <- c(x[[i,63]], x[[i,64]], x[[i,65]], x[[i,66]], x[[i,67]], x[[i,68]])
    df <- data.frame("likelihood" = likelihood, "perception" = perception, "benefit" = benefit)
    regression <- lm(likelihood ~ benefit + perception, data = df)
    preferences[i] <- sum(regression$coefficients)
  }
  return(preferences)
}

risk_attitudes_perception <- function(x){
  preferences <- rep(0, nrow(x))
  for (i in seq_along(preferences)){
    likelihood <- c(x[[i,50]], x[[i,51]], x[[i,52]], x[[i,53]], x[[i,54]], x[[i,55]])
    perception <- c(x[[i,56]], x[[i,57]], x[[i,58]], x[[i,59]], x[[i,60]], x[[i,61]])
    benefit <- c(x[[i,62]], x[[i,63]], x[[i,64]], x[[i,65]], x[[i,66]], x[[i,67]])
    df <- data.frame("likelihood" = likelihood, "perception" = perception, "benefit" = benefit)
    regression <- lm(likelihood ~ benefit + perception, data = df)
    preferences[i] <- regression$coefficients[3]
  }
  return(preferences)
}

dospert_data <- function(x){
  preferences <- rep(0, nrow(x))
  for (i in seq_along(preferences)){
    likelihood <- c(x[[i,51]], x[[i,52]], x[[i,53]], x[[i,54]], x[[i,55]], x[[i,56]])
    perception <- c(x[[i,57]], x[[i,58]], x[[i,59]], x[[i,60]], x[[i,61]], x[[i,62]])
    benefit <- c(x[[i,63]], x[[i,64]], x[[i,65]], x[[i,66]], x[[i,67]], x[[i,68]])
    df <- data.frame("likelihood" = likelihood, "perception" = perception, "benefit" = benefit)
  }
  return(ldf)
}





## packages in Analysis:

library(ggplot2)
library(tidyverse)
library(patchwork)
library(Hmisc)
library(ggcorrplot)
library(psych)
