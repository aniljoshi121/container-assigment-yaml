Python YAML Use Case
This repository demonstrates how to use YAML files in Python. The project includes a simple application that reads student data from a YAML file and provides functionalities to display and filter the data.

📌 Features
Load student data from a YAML file.

Display all student records.

Filter students by GPA.

🛠 Installation
Ensure you have Python installed, then install the required dependency:

bash
Copy
Edit
pip install pyyaml
📄 YAML File Structure
Create a file named students.yaml and include student data as shown:

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
📝 Usage
Create a Python script named app.py with the following code:

python
Copy
Edit
import yaml

def load_data(file_path):
    """Load data from a YAML file."""
    with open(file_path, 'r') as file:
        return yaml.safe_load(file)

def display_students(students):
    """Display information about all students."""
    print("\nAll Students:")
    for student in students:
        print(f"Name: {student['name']}, Age: {student['age']}, Major: {student['major']}, GPA: {student['gpa']}")

def filter_students_by_gpa(students, min_gpa):
    """Filter and display students with a GPA above the specified minimum."""
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
🚀 Running the Application
Ensure that app.py and students.yaml are in the same directory. Run the script using:

bash
Copy
Edit
python app.py
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
📌 Future Enhancements
Add functionality to update student records.

Sort students by GPA or name.

Save updated data back to the YAML file.

📜 License
This project is licensed under the MIT License.

Let me know if you need any modifications! 🚀
