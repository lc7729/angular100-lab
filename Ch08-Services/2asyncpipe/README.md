# Chapter 8 Services: 2 AsyncPipe

## Objectives

- Start a server and use HttpClient and asyncPipe to display it in the browser

## Steps

1. Continue working in your **my-angular-albums** project. If you haven't completed previous exercises, you can copy the solution files from the last exercise.

2. In this readme folder here is a folder called data with a file inside called **music-info.json**. Copy this directory to the root of your project folder - the same location as your **package.json**.

3. Install json server and npm-run-all packages.

   ```bash
   npm i json-server npm-run-all -S
   ```

4. Modify **package.json** scripts to start up json-server by pointing it at the music-info.json file.

   ```javascript
   "start": "run-p start-db start-app",
   "start-app": "ng serve --port 4444 -o",
   "start-db": "json-server --watch data/music-info.json --port 4445",
   ```

5. Start the project using **npm start**

6. The json-server and the angular server should both start. Test the url works for the resources, as listed in the console.

7. Inside the **app.module.ts** - add the use of **HttpClientModule** to the **@NgModule** imports property. You will also need to have this added to the imports at the top of the file.

8) Modify the **album.service** to be dependency injected with httpClient, and use this to request the albums from the given URL.

   ```javascript
   import { Injectable } from '@angular/core';
   import { HttpClient } from '@angular/common/http';
   import { Observable } from 'rxjs';
   import { Album } from './album.model';

   @Injectable({
    providedIn: 'root'
   })
   export class AlbumService {
        url = "http://localhost:4445/albums";

        constructor(private http: HttpClient) { }

        getAlbums(): Observable<Album[]> {
            return this.http.get<Album[]>(this.url);
        }
   }

   ```

   **NOTICE**: the return type is an Observable<Album[]>

9) In the **AlbumListComponent** change the data type of the albums from Album[] to an Observable of Album[]. this requires an import of **import { Observable } from 'rxjs';**

```javascript
     albums: Observable<Album[]>;
```

11. In the album-list.component.html use the async pipe

```html
<app-album-card *ngFor="let album of albums | async"
```

11. Check that your app is working, and mark your work as complete.
