`getMovies`
This function handles the retrieval of all movies stored in the system. It sets the response header content type to JSON and encodes the `movies` slice (which contains `Movie` structs) into JSON format using `json.NewEncoder(w).Encode(movies)` before writing it to the response body.

`deleteMovie`
It deletes a movie by its ID from the `movies` slice. It retrieves the movie ID from the request parameters using `mux.Vars(r)`, iterates through the `movies` slice, finds the movie with the matching ID, and removes it from the slice. After deleting the movie, it encodes the updated `movies` slice into JSON and writes it to the response body.

`getMovie`
This function retrieves a specific movie by its ID. It sets the response header content type to JSON, extracts the movie ID from the request parameters using `mux.Vars(r)`, then iterates through the `movies` slice to find the movie with the matching ID. Once found, it encodes that specific movie into JSON and sends it as the response.

`createMovie`
It handles the creation of a new movie. It decodes the JSON data from the request body into a `Movie` struct, assigns a unique ID (generated using `rand.Intn`) to the new movie, appends the new movie to the `movies` slice, encodes the newly created movie into JSON, and sends it back as the response.

`updateMovie`
This function updates an existing movie. It retrieves the movie ID from the request parameters, iterates through the `movies` slice to find the movie with the matching ID, removes the existing movie, decodes the JSON data from the request body into a `Movie` struct, assigns the ID to the updated movie, appends the updated movie to the `movies` slice, encodes the updated movie into JSON, and sends it back as the response.

In the `main` function, a router (`mux.NewRouter()`) is created to handle different HTTP methods (`GET`, `POST`, `PUT`, `DELETE`) on different endpoints (`/movies`, `/movies/{id}`). Movies are pre-populated with some data for demonstration purposes. Finally, the server is started on port 8000 using `http.ListenAndServe(":8000", r)`.
