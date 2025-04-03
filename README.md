## Python YAML Use Case

This repository demonstrates how to read and process student data from a YAML file using Python. The script allows users to display all students and filter them based on GPA.

# 📌 Features

Reads student information from a students.yaml file.

Displays all students.

Filters students based on GPA input from the user.

# 🚀 Installation

Ensure you have Python installed (version 3.x recommended). Then, install the required dependencies:
bash
Copy
Edit
pip install pyyaml
# 📄 YAML File (students.yaml)

Create a YAML file named students.yaml with the following content:
```
students:
  - name: Alice
    age: 21
    major: Computer Science
    gpa: 3.8
  - name: Bob
    age: 22
    major: Mathematics
    gpa: 3.5
  - name: Charlie
    age: 20
    major: Physics
    gpa: 3.9
  - name: David
    age: 23
    major: Chemistry
    gpa: 3.2
  - name: Eva
    age: 21
    major: Computer Science
    gpa: 3.7
```
# 📝 Python Script (app.py)

Create a Python script app.py with the following code:
```
import yaml

def load_data(file_path):
    """
    Load data from a YAML file.

    :param file_path: Path to the YAML file.
    :return: Data loaded from the YAML file.
    """
    with open(file_path, 'r') as file:
        data = yaml.safe_load(file)  # Load the data as a Python dictionary
    return data

def display_students(students):
    """
    Display information about all students.

    :param students: List of student dictionaries.
    """
    print("\nAll Students:")
    for student in students:
        print(f"Name: {student['name']}, Age: {student['age']}, Major: {student['major']}, GPA: {student['gpa']}")

def filter_students_by_gpa(students, min_gpa):
    """
    Filter and display students with a GPA above the specified minimum.

    :param students: List of student dictionaries.
    :param min_gpa: Minimum GPA for filtering.
    """
    filtered_students = [s for s in students if s['gpa'] >= min_gpa]

    print(f"\nStudents with GPA >= {min_gpa}:")
    if filtered_students:
        for student in filtered_students:
            print(f"Name: {student['name']}, Age: {student['age']}, Major: {student['major']}, GPA: {student['gpa']}")
    else:
        print("No students found.")

def main():
    """
    Main function to load and process student data.
    """
    file_path = "students.yaml"  # Replace with your actual YAML file path
    try:
        data = load_data(file_path)

        # Ensure the data contains a 'students' key
        if 'students' not in data:
            raise KeyError("Missing 'students' key in YAML file.")

        students = data['students']

        # Display all students
        display_students(students)

        # Filter students by GPA
        min_gpa = float(input("\nEnter minimum GPA to filter students: "))
        filter_students_by_gpa(students, min_gpa)

    except FileNotFoundError:
        print(f"Error: The file '{file_path}' was not found.")
    except yaml.YAMLError:
        print("Error: Failed to parse the YAML file.")
    except ValueError:
        print("Error: Invalid input. Please enter a numeric GPA value.")
    except KeyError as e:
        print(f"Error: {e}")
    except Exception as e:
        print(f"An unexpected error occurred: {e}")

if __name__ == "__main__":  # Corrected syntax
    main()

```

# ▶️ Running the Application

Ensure app.py and students.yaml are in the same directory. Then, run:
bash
Copy
Edit
python app.py

# 🖥️ Expected Output
```
All Students:
Name: Alice, Age: 21, Major: Computer Science, GPA: 3.8
Name: Bob, Age: 22, Major: Mathematics, GPA: 3.5
Name: Charlie, Age: 20, Major: Physics, GPA: 3.9
Name: David, Age: 23, Major: Chemistry, GPA: 3.2
Name: Eva, Age: 21, Major: Computer Science, GPA: 3.7

Enter minimum GPA to filter students: 3.6

Students with GPA >= 3.6:
Name: Alice, Age: 21, Major: Computer Science, GPA: 3.8
Name: Charlie, Age: 20, Major: Physics, GPA: 3.9
Name: Eva, Age: 21, Major: Computer Science, GPA: 3.7
```

# 🔍 Additional Features
Expand functionality by adding sorting, updating student information, or saving changes back to the YAML file.

Convert the script into a GUI-based application for better usability.

