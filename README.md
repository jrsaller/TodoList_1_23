# Todo App Using Vue Slots

I want you to build a brand new Todo List Vue 3 app from scratch (You can use the cli but don’t use a boilerplate app or anything).  I recommend doing it in Vite, but you can use whatever build tools you want. I’m not concerned about the styles, so you can do as much or as little CSS work as you want.

The requirements of a simple Todo App are:
- Ability to add an item to your todo list (typically using some kind of text input)
- Ability to complete an item
- Ability to delete an item

Here are some additional requirements specifically for this challenge:
- The components should all use the Composition API and be created using the script setup syntax.
- It should use proper TS types.
- Your TodoList component should allow a slot to override the individual TodoItem components.  This is a bit of a contrived problem, but I think it’s important for us all to get more experience working with Slots since Vuetify uses them extensively. 