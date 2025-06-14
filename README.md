# http-github.com-JR-M29-repo-Issue-3

Issue 3:* Deleting a note does not work correctly
    - Label: functional
    - Description: When a user tries to delete a note, the note is not deleted correctly from local storage.


describe('Full flow: writing, saving, editing, and deleting a note', () => {
  it('should allow a user to write, save, edit, and delete a note', () => {
    // Write a note
    const note = { title: 'Test Note', content: 'This is a test note' };
    document.querySelector('#title').value = note.title;
    document.querySelector('#content').value = note.content;

    // Save the note
    document.querySelector('#save-note').click();
    expect(localStorage.getItem('notes')).toContain(note.title);
    expect(localStorage.getItem('notes')).toContain(note.content);

    // Edit the note
    const editedNote = { title: 'Edited Test Note', content: 'This is an edited test note' };
    document.querySelector('#title').value = editedNote.title;
    document.querySelector('#content').value = editedNote.content;
    document.querySelector('#save-note').click();
    expect(localStorage.getItem('notes')).toContain(editedNote.title);
    expect(localStorage.getItem('notes')).toContain(editedNote.content);

    // Delete the note
    document.querySelector('#delete-note').click();
    expect(localStorage.getItem('notes')).not.toContain(editedNote.title);
    expect(localStorage.getItem('notes')).not.toContain(editedNote.content);
  });
});
