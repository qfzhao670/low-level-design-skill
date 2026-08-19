Undo/Redo Problem Statement
Think of a text editor like MS Word or Google Docs.
When you type, delete, or format text, the editor saves a
'snapshot" of what
the document looks like after each action.
This way, when you press CtrI+Z (undo), the editor can bring back the previous version of your document

Memento Pattern Structure
- Originator: This is the main object whose data you want to save and bring back later.
Think of it as the TextEditor that holds your content.
- Memento: This acts like a snapshot or save point that captures the originator's data at a specific moment. TextMemento Class
- Caretaker: This is the manager that keeps all the snapshots safe and organized.
It doesn't change the snapshots, just stores them and gives them back when you need them. Think of it as the History Class