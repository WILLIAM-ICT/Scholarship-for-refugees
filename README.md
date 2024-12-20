# Load the dataset
file_path <- "path_to_your_file/Scholarship_Data Cleaning.xlsx"
data <- read_excel(file_path, sheet = "Sheet1")
# Preview the data
head(data)
summary(data)
str(data)
# Rename columns for easier access (optional)
data <- data %>%
  rename(
    Name = `your name in full`,
    Gender = `your Gender`,
    Email = `your email address`,
    ID = `your individual number/ID number`,
    Nationality = `what is your nationality?`,
    Marital_Status = `what is your marital status ?`,
    Location = `where are you currently located ?`,
    Language = `what is your preferred language of communication?`,
    Education_Level = `what is your level of Education ?`,
    Year_of_Completion = `what was the year  of completion ?`,
    Final_Grade = `what is your final Grade?`,
    School_Name = `name of your school of completion?`,
    Vocational_College = `Have your attended any vocational or university/college ?`,
    Course_Details = `if yes , mention the vocational or university/college name and the course you studied.`,
    Field_of_Study = `What is your field of study or intended course/program?`,
    Employment_Status = `Are you currently employed or involved in any community service or volunteer work?`,
    Job_Details = `if yes , mention the job you are in`,
    Financial_Situation = `What is your current financial situation?`,
    Certified_Accurate = `I certify that all information provided is accurate.`,
    Agree_Terms = `I agree to the terms and conditions of the scholarship.`  )
# Check for missing values
missing_values <- colSums(is.na(data))
print(missing_values)
# Basic Descriptive Statistics
summary(data)
# Count unique values in categorical columns
categorical_counts <- data %>%
  select(Gender, Nationality, Marital_Status, Language, Education_Level, Employment_Status) %>%
  summarise_all(~ n_distinct(.))
print(categorical_counts)
# Gender Distribution
gender_plot <- ggplot(data, aes(x = Gender)) +
  geom_bar(fill = "skyblue") +
  labs(title = "Gender Distribution", x = "Gender", y = "Count") +
  theme_minimal()
print(gender_plot)
# Education Level Distribution
education
