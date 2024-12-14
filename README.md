Info = (('001', 'jitu'), ('002', 'piyush'))
Id = input("Enter ID: ")
Name = input("Enter Name: ")
Details = (Id, Name)

if Details in Info:
    print("Details are present.")
else:
    print("Details are not present.")
L = []

def add():
    Id_ = input("Enter ID: ")
    Name = input("Enter Name: ")
    Details = (Id_, Name)
    L.append(Details)

def view():
    print("ID\tName")
    print("----------------")
    for id_, name in L:
        print(f"{id_}\t{name}")

def rem():
    Id_to_remove = input("Enter ID to remove: ")
    for item in L:
        if item[0] == Id_to_remove:
            L.remove(item)
            break
    else:
        print("ID not found!")

def edit():
    Id_to_edit = input("Enter ID to edit: ")
    new_name = input("Enter the new name: ")
    for index, item in enumerate(L):
        if item[0] == Id_to_edit:
            L[index] = (Id_to_edit, new_name)
            break
    else:
        print("ID not found!")

def mark_attendance():
    date = input("Enter the date (YYYY-MM-DD): ")
    attendance_list = []
    print("Mark attendance by typing 'P' for present or 'A' for absent.")
    for id_, name in L:
        attendance = input(f"{name}'s attendance (P/A): ").upper()
        attendance_list.append((id_, name, attendance, date))
    return attendance_list

def view_attendance_by_student():
    student_id = input("Enter the ID of the student: ")
    print("Attendance Records:")
    print("Date\t\tName\t\tAttendance")
    print("-----------------------------------")
    found = False
    for id_, name, attendance, date in attendance_list:
        if id_ == student_id:
            print(f"{date}\t{name}\t{'Present' if attendance == 'P' else 'Absent'}")
            found = True
    if not found:

        print("No attendance records found for the specified student.")

attendance_list = []

while True:
    print("\n1. Add\n2. Remove\n3. Edit\n4. View\n5. Mark Attendance\n6. View Attendance by Student\n7. Exit")
    ch = input("Enter the operation you want to perform (1-7): ")

    if ch == '1':
        add()
        print("After adding:")
        view()
    elif ch == '2':
        rem()
        print("After removing:")
        view()
    elif ch == '3':
        edit()
        print("After updating:")
        view()
    elif ch == '4':
        view()
    elif ch == '5':
        attendance_list = mark_attendance()
        print("Attendance marked for the following individuals:")
        for id_, name, attendance, date in attendance_list:
            print(f"Date: {date}, Name: {name}, Attendance: {'Present' if attendance == 'P' else 'Absent'}")
    elif ch == '6':
        view_attendance_by_student()
    elif ch == '7':
        print("Exiting the program.")
        break
    else:
        print("Invalid choice.")
