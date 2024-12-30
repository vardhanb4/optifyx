# optifyx Program for to do list
f main():
    tasks = []

    while True:
        print("\n===== To-Do List =====")
        print("1. Add Task")
        print("2. Show Tasks")
        print("3. Mark Task as Done")
        print("4. Delete Task")
        print("5. Exit")

        choice = input("Enter your choice: ")

        if choice == '1':
            print()
            try:
                n_tasks = int(input("How many tasks do you want to add: "))
                if n_tasks <= 0:
                    print("Please enter a valid number greater than 0.")
                    continue
                
                for i in range(n_tasks):
                    task = input(f"Enter task #{i + 1}: ")
                    tasks.append({"task": task, "done": False})
                    print(f"Task #{i + 1} added!")
            except ValueError:
                print("Please enter a valid number.")

        elif choice == '2':
            if tasks:
                print("\nTasks:")
                for index, task in enumerate(tasks):
                    status = "Completed" if task["done"] else "Pending"
                    print(f"{index + 1}. {task['task']} - {status}")
            else:
                print("No tasks available.")

        elif choice == '3':
            if tasks:
                try:
                    task_index = int(input("Enter the task number to mark as done: ")) - 1
                    if 0 <= task_index < len(tasks):
                        tasks[task_index]["done"] = True
                        print("Task marked as done!")
                    else:
                        print("Invalid task number.")
                except ValueError:
                    print("Please enter a valid number.")
            else:
                print("No tasks to mark as done.")

        elif choice == '4':
            if tasks:
                try:
                    task_index = int(input("Enter the task number to delete: ")) - 1
                    if 0 <= task_index < len(tasks):
                        deleted_task = tasks.pop(task_index)
                        print(f"Task '{deleted_task['task']}' deleted!")
                    else:
                        print("Invalid task number.")
                except ValueError:
                    print("Please enter a valid number.")
            else:
                print("No tasks to delete.")

        elif choice == '5':
            confirm_exit = input("Are you sure you want to exit? (yes/no): ").lower()
            if confirm_exit == 'yes':
                print("Exiting the To-Do List.")
                break
            else:
                print("Returning to main menu.")

        else:
            print("Invalid choice. Please try again.")

if __name__ == "__main__":
    main()
