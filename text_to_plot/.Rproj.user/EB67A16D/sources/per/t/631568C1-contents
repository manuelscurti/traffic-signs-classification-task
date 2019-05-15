library(dplyr)
library(RMySQL)
library(data.table)
library(digest)
library(stringr)
library(DescTools)

# for analysis
library(ggplot2)
library(flextable)
library(officer)


performances_from_text <- function(in_text, net_name){
	
	performance_tab_df <- data.frame(net_name=character(),metric=integer(),epoch=integer(),value=double())
	
	lines <- stringr::str_split(in_text, "\n")[[1]]
	
	epoch <- 0
	for(i in 2:length(lines)){ # skip header line
		if((i %% 2) != 0){
			line <- lines[i]
			line_splitted <- stringr::str_split(line, " ")[[1]]
			
			train_acc <- as.double(line_splitted[8]) # 1
			val_acc <- as.double(line_splitted[14]) # 2
			train_loss <- as.double(line_splitted[5]) # 3
			val_loss <- as.double(line_splitted[11]) # 4
			
			performance_tab_df <- rbind(performance_tab_df, data.frame(net_name = net_name, metric = 1, epoch=epoch,value=train_acc))
			performance_tab_df <- rbind(performance_tab_df, data.frame(net_name = net_name, metric = 2, epoch=epoch,value=val_acc))
			performance_tab_df <- rbind(performance_tab_df, data.frame(net_name = net_name, metric = 3, epoch=epoch,value=train_loss))
			performance_tab_df <- rbind(performance_tab_df, data.frame(net_name = net_name, metric = 4, epoch=epoch,value=val_loss))
		} else {
			line <- lines[i]
			num <- stringr::str_split(line, "/")[[1]]
			num <- num[1]
			num <- stringr::str_split(num, " ")[[1]]
			num <- as.integer(num[2])
			epoch <- num
		}
	}
	
	return(performance_tab_df)
}


dense201 <- performances_from_text(text,"dense201")
inceptionV3 <- performances_from_text(text_inceptionV3, "InceptionV3")
inceptionresnet <- performances_from_text(text_inceptionresnet, "InceptionResNetV2")
nasnetmobile <- performances_from_text(text_nasnetmobile,"NASNetMobile")
vgg19 <- performances_from_text(text_vgg19, "VGG19")



