#### -- Packrat Autoloader (version 0.5.0) -- ####
source("packrat/init.R")
#### -- End Packrat Autoloader -- ####

if(is.na(Sys.getenv('PROJECT_ROOT', unset=NA))){
    PROJECT_ROOT <- system('git rev-parse --show-toplevel', intern=TRUE)
    Sys.setenv(PROJECT_ROOT=PROJECT_ROOT)
}

if(is.na(Sys.getenv('EMOD_INPUT_ROOT', unset=NA))) {
    EMOD_INPUT_ROOT <- file.path(PROJECT_ROOT, 'Demographics_Files')
    Sys.setenv(EMOD_INPUT_ROOT=EMOD_INPUT_ROOT)
}

library(RColorBrewer)
library(rjson)
library(igraph)
library(deSolve)

emod <- function(config = "config.json", input = EMOD_INPUT_ROOT) {
    emod_app = file.path(PROJECT_ROOT, 'bin', 'Eradication')
    if (Sys.info()['sysname'] == 'Windows'){
        emod_app = file.path(PROJECT_ROOT, 'bin', 'Eradication.exe')
    }
    command_line = sprintf("%s --config %s --input-path %s", emod_app, config, input)
    system(command_line)
}