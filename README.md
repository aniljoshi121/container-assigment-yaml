Python YAML Use Case
This is a simple Python project that demonstrates how to use YAML files to store and retrieve student information. The application reads student details from a students.yaml file and provides options to display all students and filter them based on GPA.

Features
Read student data from a YAML file.

Display all students.

Filter students by a minimum GPA.

Prerequisites
Ensure you have Python installed (Python 3 recommended). Install the required package using:

bash
Copy
Edit
pip install pyyaml
Project Structure
bash
Copy
Edit
Python_Yaml_Use_Case/
│── students.yaml   # YAML file containing student data
│── app.py          # Python script to process YAML data
│── README.md       # Project documentation
YAML File (students.yaml)
yaml
Copy
Edit
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
Python Script (app.py)
python
Copy
Edit
import yaml

def load_data(file_path):
    """Load data from a YAML file."""
    with open(file_path, 'r') as file:
        data = yaml.safe_load(file)
    return data

def display_students(students):
    """Display all students."""
    print("\nAll Students:")
    for student in students:
        print(f"Name: {student['name']}, Age: {student['age']}, Major: {student['major']}, GPA: {student['gpa']}")

def filter_students_by_gpa(students, min_gpa):
    """Filter students with GPA above the given threshold."""
    filtered_students = [s for s in students if s['gpa'] >= min_gpa]

    print(f"\nStudents with GPA >= {min_gpa}:")
    if filtered_students:
        for student in filtered_students:
            print(f"Name: {student['name']}, Age: {student['age']}, Major: {student['major']}, GPA: {student['gpa']}")
    else:
        print("No students found.")

def main():
    data = load_data('students.yaml')
    students = data['students']

    display_students(students)

    min_gpa = float(input("\nEnter minimum GPA to filter students: "))
    filter_students_by_gpa(students, min_gpa)

if __name__ == "__main__":
    main()
How to Run
Ensure students.yaml and app.py are in the same directory.

Open a terminal and navigate to the project folder.

Run the script using:

bash
Copy
Edit
python app.py
The script will display all students and then prompt for a minimum GPA to filter students.

Expected Output
yaml
Copy
Edit
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
Conclusion
This project demonstrates how to work with YAML files in Python, allowing for easy data storage and retrieval. It can be extended by adding features such as sorting, updating student records, and writing changes back to the YAML file.

