# Chapter 4 Passing Data: Event Binding

## Objectives

- Add a button to each card that when clicked calls a function to display an alert

## Steps

1. Continue working in your **my-angular-albums** project. If you haven't completed previous exercises, you can copy the solution files from the last exercise.

1) In **album-card.component.ts** define a function to be called:

   ```javascript
    showAlbum() {
        alert('Album selected: ' + this.album.album_name)
    }
   ```

2) In **album-card.component.html**, after the element with `<div class="card-body">` , add a footer with a button and a click event that calls the **showAlbum** function like this:

   ```html
   <div class="card-footer">
     <button class="btn btn-primary float-right" (click)="showAlbum()">
       Raise Alert
     </button>
   </div>
   ```

3) In **album-card.component.css** add a rule for the card-footer class:

   ```css
   .card-footer {
     height: 75px;
   }
   ```

4) You should now see buttons for the 3 albums in the browser and when you click - an alert should be raised with the album name.

5) Once this is working, mark your work as complete.

## Bonus

1. On a hover event of a card, console.log the name of the artist.
