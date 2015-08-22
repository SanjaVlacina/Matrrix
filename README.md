library('MASS')

## implimenting matrix 

makeCacheMatrix <- function(x = matrix()) 
{
	inverse = NULL
	set_matrix <- function(y)
	{
		x <<- y
		inverse <<- NULL
	}
	get_matrix <- function() x
	set_inverse <- function(the_inverse) inverse <<- the_inverse
	get_inverse <- function() inverse
	list(set_inverse = set_inverse, get_inverse = get_inverse,
	     set_matrix = set_matrix, get_matrix = get_matrix)
 }
 
 
## Return a matrix that is the inverse of x
 
cacheSolve <- function(x, ...) {
cacheSolve <- function(x, ...) 
{
	inverse <- x$get_inverse()
	if(!is.null(inverse))
	{
		return(inverse)
	}
	matrix <- x$get_matrix()
	matrix_inverse <- solve(matrix)
	x$set_inverse(matrix_inverse)
	matrix_inverse
 }
