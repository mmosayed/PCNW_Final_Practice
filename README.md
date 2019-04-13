# Final Exam Practice Assessment

## Opening Remarks

This final exam, like many of the exams before it, will be an open-book, project-driven exam. Therefore, don't time yourself on this entire project to the minute. Instead, time yourself on the implementation of specific features. What do you get stuck on? What do you blaze through? These observations are important when you decide what to study.

Utilize this practice exam as an opportunity to _plan_. Plan what API endpoints you'll need. Plan what your component structure will look like, and where your state will be managed. An ounce of planning is, truly, worth a pound of debugging.

That being said, also practice _debugging_. Debugging is a hugely important part of the work we do as developers - because, well, we're human, and we make mistakes. We don't care if you console.log or use a debugger - just make sure you're diligent and equipped to handle the bugs that come to you. Remember - Google is your friend!

## The Practice Exam - A Movie App

For this exam, we're going to be making a full-stack application for reviewing movies. Users should be able to browse movies, find them by name and by genre, see movie ratings, and rate movies themselves. They should also be able to comment on movies.

Note that, for this exam, we are _not_ implementing user authentication. We are allowing users to come in, search, and rate without having to log in. Comments are anonymous.

### Database Schema

Therefore, you should have the following tables and columns:

- Movies
  - id
  - title - _The movie's title._
  - genre_id - _Movies have one genre. A genre can be applied to many movies._
  - img_url - *A nice image for the movie - perhaps a poster?*
- Genres
  - id
  - name - _The genre name. Say, action, or comedy._
- Ratings
  - id
  - stars - _The number of stars the user rated the movie, from 1 to 5._
  - movie_id - *Movies can have many ratings. A rating can only be applied to one movie.*
- Comments
  - id
  - text - _What the comment said._
  - movie_id - *Comments can only be applied to one movie. A movie can have many comments.*

Create a `.sql` file to create these tables and seed this database with at least **10 movies**, **5 genres**, **20 ratings**, and **15 comments**.

### API Endpoints

Largely, your API endpoints are up to you as a developer. However, based on a consideration of what we'll need on the frontend, a few potential needs become apparent. While we may be able to process some of this stuff on the frontend, we'll probably want API endpoints that:

- Fetch all movies.
- Fetch all information and comments for a specific movie.
- Fetch all the movies that have a certain genre.

### Frontend Routes

You should have the following routes on your frontend:

- `/` - A homepage that reads: "Welcome to MovieApp" in an `h1` tag.
  - Also renders a navigation bar across the top of the page, visible on every subsequent route.
  - Navbar should have the following links: "Home," "All Movies," "By Genre".
- `/movies` - A page that fetches and renders all movies, including their image URLs and average ratings.
  - Includes a `form` tag containing a `text` input and a `submit` button. Label - "Search By Title."
  - When a user enters part or all of a movie's title (not case sensitive) and clicks "Search" (submit), the list of movies should be filtered to only the movies with titles that correspond to what the user was searching for.
  - Each movie should link to that movie's individual page (route described below).
- `/movies/byGenre` - A page that fetches and renders all movies, including their image URLs and average ratings. This time with a different search metric!
  - Includes a `form` tag containing a `select` input and a `submit` button. Label - "Search By Genre."
  - The `select` input should contain all valid Genres as `option`s. By default, the selected option should be blank, and this should render all movies.
  - When a user selects a genre and clicks `submit`, the list of movies should be filtered to only movies that have that genre.
  - Each movie should link to that movie's individual page (route described below).
- `/movies/:id` - A page that renders all information for that individual movie, including average rating, title, and image. Below this information, all comments are listed.
  - Includes two `form`s:
    - One below the average rating with a `radio` input with options from 1 to 5 stars. When a user selects an option and clicks `submit`, a new Rating should be added to that movie. The average rating should immediately change.
    - One above the list of comments with a `text` input. When the user enters text and clicks `submit`, a new Comment should be added to that movie and rendered above all other Comments.

All non-search-related `form`s should send information to the backend and database via an AJAX POST request.

## Styling

Besides the specific instructions outlined here, styling is up to you.

- Navbar
  - The Navbar should be 75 pixels tall and should be dark blue.
  - All options should be 20px in size, should be a sans-serif font of your choice, and should be white.
  - "Home" should be justified to the left. "All Movies" and "By Genre" should be justified right.
- Homepage
  - The Homepage's background color should be black.
  - The `h1` tag should justified to the center horizontally, with 200px of space to distance itself from the Navbar. It should be red, in a serif font of your choice.
- All Movies and By Genre
  - These pages' background colors should be black.
  - All text should be in a sans-serif font of your choice. If it is against the black background (read: not in a form), it should be yellow.
  - All content should be justified toward the center, with 75 px of space to distance it from the Navbar.
  - Each movie item should include a 100x100px area of space for the movie's image. The movie image should **not warp**, but adjust its size to fit this space. Each movie item should have a 2px solid white border, with at least 15px of vertical space between each item.
- Single Movie
  - This page's background color should, also, be black.
  - All text should be in a sans-serif font of your choice. If it's against the black background (read: not in a form), it should be orange.
  - All movie information, including average rating, should render at the top of the page, justified center, with 75px of space to differentiate it from the navbar.
  - Comments, including the comment submission form, should render below this information, justified left. Each comment should have a 2px solid white border on the bottom, with at least 10px of vertical space between each comment.
