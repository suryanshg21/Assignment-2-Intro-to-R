#Question
# Load the iris dataset
data(iris)

# Install and load the necessary packages
install.packages("ggplot2")  # If not already installed
library(ggplot2)

# Boxplots of continuous variables by Species
ggplot(iris, aes(x = Species, y = Sepal.Length, fill = Species)) +
  geom_boxplot() +
  labs(x = "Species", y = "Sepal Length") +
  ggtitle("Boxplot of Sepal Length by Species")

ggplot(iris, aes(x = Species, y = Petal.Length, fill = Species)) +
  geom_boxplot() +
  labs(x = "Species", y = "Petal Length") +
  ggtitle("Boxplot of Petal Length by Species")

# Scatterplot of Sepal.Length and Petal.Length, colored by Species
ggplot(iris, aes(x = Sepal.Length, y = Petal.Length, color = Species)) +
  geom_point() +
  labs(x = "Sepal Length", y = "Petal Length") +
  ggtitle("Scatterplot of Sepal Length and Petal Length") +
  scale_color_manual(values = c("setosa" = "red", "versicolor" = "blue", "virginica" = "green"))

#Question 2
# Load the imager package
library(imager)

flip <- function(image) {
  # Get image dimensions
  width <- dim(image)[1]
  height <- dim(image)[2]
  
  # Create an empty image with the same dimensions
  flipped_image <- imager(width, height)
  
  # Flip the image by copying pixels from right to left
  for (x in 1:width) {
    for (y in 1:height) {
      flipped_image[x, y] <- image[width - x + 1, y]
    }
  }
  
  # Return the flipped image
  return(flipped_image)
}

# Provide the correct file path to your image with double backslashes
image_path <- "C:\\Users\\surya\\Downloads\\97578-sailing-sailing_ship-sea.jpg"

# Load the image using the correct file path
image <- load.image(image_path)

# Flip the image
flipped_image <- flip(image)

# Display the original and flipped images
par(mfrow = c(1, 2))
plot(image, main = "Original Image")
plot(flipped_image, main = "Flipped Image")
