#Task-1

import sys

class ToDoList:
    def __init__(self):
        self.tasks = {}
        self.next_id = 1

    def add_task(self, description):
        self.tasks[self.next_id] = {'description': description, 'completed': False}
        print(f"Task added with ID: {self.next_id}")
        self.next_id += 1

    def update_task(self, task_id, new_description):
        if task_id in self.tasks:
            self.tasks[task_id]['description'] = new_description
            print(f"Task ID {task_id} updated.")
        else:
            print(f"Task ID {task_id} not found.")

    def delete_task(self, task_id):
        if task_id in self.tasks:
            del self.tasks[task_id]
            print(f"Task ID {task_id} deleted.")
        else:
            print(f"Task ID {task_id} not found.")

    def complete_task(self, task_id):
        if task_id in self.tasks:
            self.tasks[task_id]['completed'] = True
            print(f"Task ID {task_id} marked as completed.")
        else:
            print(f"Task ID {task_id} not found.")

    def view_tasks(self):
        if not self.tasks:
            print("No tasks available.")
        else:
            for task_id, task in self.tasks.items():
                status = "Completed" if task['completed'] else "Pending"
                print(f"ID: {task_id} | Description: {task['description']} | Status: {status}")

def print_menu():
    print("\nTo-Do List Application")
    print("1. Add Task")
    print("2. Update Task")
    print("3. Delete Task")
    print("4. Complete Task")
    print("5. View Tasks")
    print("6. Exit")

def main():
    todo_list = ToDoList()

    while True:
        print_menu()
        choice = input("Enter your choice: ")

        if choice == '1':
            description = input("Enter task description: ")
            todo_list.add_task(description)
        elif choice == '2':
            task_id = int(input("Enter task ID to update: "))
            new_description = input("Enter new task description: ")
            todo_list.update_task(task_id, new_description)
        elif choice == '3':
            task_id = int(input("Enter task ID to delete: "))
            todo_list.delete_task(task_id)
        elif choice == '4':
            task_id = int(input("Enter task ID to complete: "))
            todo_list.complete_task(task_id)
        elif choice == '5':
            todo_list.view_tasks()
        elif choice == '6':
            print("Exiting...")
            sys.exit()
        else:
            print("Invalid choice. Please try again.")

if __name__ == "__main__":
    main()
