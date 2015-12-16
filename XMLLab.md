### XML Lab

You are a data specialist for a movie theater. You have been asked to store the movies in an XML file.
The list must meet the following criteria:

- the parent of the file should be "movie_collection" with the prefix "collection" and the namespace "http://movies.com"
- the XML file must have at least 4 movies
- a movie must have a title and description
- a movie must have an id attribute
- a movie must have a child element called "showtimes, and it contains at least 3 showtime elements
- a movie should have 2 empty elements.

### Solution:

<movie_collection xmlns:collection="http://movies.com">

  <movie
    collection:id="1"
    collection:title="Gone With the Wind"
    collection:description="classics">

    <morning_showtime>10am</morning_showtime>
    <afternoon_showtime>1pm</afternoon_showtime>
    <evening_showtime>7pm</evening_showtime>
    <available></available>
    <rspv></rspv>
  </movie>

  <movie
      collection:id="2"
      collection:title="The Theory of Everything"
      collection:description="drama">

    <morning_showtime>11am</morning_showtime>
    <afternoon_showtime>2pm</afternoon_showtime>
    <evening_showtime>8pm</evening_showtime>
    <available></available>
    <rspv></rspv>
  </movie>

  <movie
      collection:id="3"
      collection:title="7 pounds"
      collection:description="drama">

    <morning_showtime>9am</morning_showtime>
    <afternoon_showtime>3pm</afternoon_showtime>
    <evening_showtime>8pm</evening_showtime>
    <available></available>
    <rspv></rspv>
  </movie>

  <movie
      collection:id="4"
      collection:title="Fountain"
      collection:description="philosophic">

    <morning_showtime>10am</morning_showtime>
    <afternoon_showtime>1pm</afternoon_showtime>
    <evening_showtime>8pm</evening_showtime>
    <available></available>
    <rspv></rspv>
  </movie>

</movie_collection>
