---
title: Class 8 Prep Exercises
currentMenu: classes
---

Add edit functionality to the `cheese-mvc` application by following these steps. It assumes that you've added all of the code from both of the [models lessons](../../videos/).

1. Stub out two handler methods in `CheeseController`. We'll add code to these in a moment, so just put the method outline in place for now.
    - Create a method to display the form with this signature:
        ```java
        public String displayEditForm(Model model, @PathVariable int cheeseId)
        ```
    - Create a method to process the form with this signature:
        ```java
        public String processEditForm(int cheeseId, String name, String description)
        ```
2. Add the necessary annotations to these forms for them to both live at the path `/cheese/edit` (not that we've configured `@RequestMapping` on the controller class already), and so that the first handles `GET` requests, and the second `POST` requests. You'll need to configure the route for `displayEditForm` to include the path variable, so that paths like `/cheese/edit/3` will work.
3. Create an `edit.html` view template in `resources/templates/cheese`.
4. Copy the code from `add.html` into `edit.html`. You can copy the entire file contents.
5. Back in the `displayEditForm` handler, ask `CheeseData` for the object with the given `cheeseId` and put it in the `model`. Return the appropriate template string.
6. Within the form fields in `edit.html`, get the name and description from the cheese that was passed in via the `model` and set them as the values of the form fields.
7. Add another input to hold the id of the cheese being edited. This should be hidden from the user:
    ```html
    <input type="hidden" th:value="${cheese.cheeseId}" name="cheeseId" />
    ```
8. Add a heading at the top of `edit.html` that says "Edit Cheese NAME (id=ID)" where NAME and ID are replaced by the values of the given cheese.
9. Back in `processEditForm`, query `CheeseData` for the cheese with the given id, and then update its name and description. Redirect the user to the home page.
10. In `resources/templates/cheese/index.html`, add a link to edit the cheese:
    ```html
    <a th:href="@{'/cheese/edit/' + ${cheese.cheeseId}}">edit</a>
    ```
    You can put this link in a third table column, or in one of the existing table cells.
11. Test your code! With so many changes, it's likely that you made an error somewhere. Be patient, use IntelliJ's debugger, and read your error messages.
