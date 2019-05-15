
merged <- rbind(dense201, inceptionresnet, inceptionV3, nasnetmobile)

merged$metric <- as.factor(merged$metric)
merged$net_name <- as.factor(merged$net_name)

train_accuracy <- merged[merged$metric == 1,]

net_names <- unique(train_accuracy$net_name)


ggplot(data=train_accuracy, aes(x=train_accuracy$epoch, y=train_accuracy$value, group=train_accuracy$net_name)) +
	geom_line(aes(color=train_accuracy$net_name), size = 1)+
	#geom_point(aes(color=train_accuracy$net_name)) +
	ggtitle("Train accuracy") +
	xlab("Epoch") + ylab("") +
	scale_color_discrete(name = "Net", labels = net_names)




val_accuracy <- merged[merged$metric == 2,]
net_names <- unique(val_accuracy$net_name)

ggplot(data=val_accuracy, aes(x=val_accuracy$epoch, y=val_accuracy$value, group=val_accuracy$net_name)) +
	geom_line(aes(color=val_accuracy$net_name), size = 1)+
	#geom_point(aes(color=train_accuracy$net_name)) +
	ggtitle("Validation accuracy") +
	xlab("Epoch") + ylab("") +
	scale_color_discrete(name = "Net", labels = net_names)


train_loss <- merged[merged$metric == 3,]
net_names <- unique(train_loss$net_name)

ggplot(data=train_loss, aes(x=train_loss$epoch, y=train_loss$value, group=train_loss$net_name)) +
	geom_line(aes(color=train_loss$net_name), size = 1)+
	#geom_point(aes(color=train_accuracy$net_name)) +
	ggtitle("Train loss") +
	xlab("Epoch") + ylab("") +
	scale_color_discrete(name = "Net", labels = net_names)


val_loss <- merged[merged$metric == 4,]
net_names <- unique(val_loss$net_name)

ggplot(data=val_loss, aes(x=val_loss$epoch, y=val_loss$value, group=val_loss$net_name)) +
	geom_line(aes(color=val_loss$net_name), size = 1)+
	#geom_point(aes(color=train_accuracy$net_name)) +
	ggtitle("Validation loss") +
	xlab("Epoch") + ylab("") +
	scale_color_discrete(name = "Net", labels = net_names)



