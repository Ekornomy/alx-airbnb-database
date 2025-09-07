# alx-airbnb-database
# Query 1: INNER JOIN

Purpose: Retrieve only bookings that have associated users (excludes bookings without users and users without bookings)

sql
SELECT 
    b.booking_id,
    b.booking_date,
    b.status,
    u.user_id,
    u.username,
    u.email
FROM bookings b
INNER JOIN users u ON b.user_id = u.user_id;
# Query 2: LEFT JOIN

Purpose: Retrieve all properties, including those without any reviews

sql
SELECT
    p.property_id,
    p.property_name,
    p.location,
    r.review_id,
    r.rating,
    r.comment,
    r.review_date
FROM properties p
LEFT JOIN reviews r ON p.property_id = r.property_id;
# Query 3: FULL OUTER JOIN

Purpose: Retrieve all users AND all bookings, including unmatched records from both tables

sql
SELECT
    u.user_id,
    u.username,
    u.email,
    b.booking_id,
    b.booking_date,
    b.status
FROM users u
FULL OUTER JOIN bookings b ON u.user_id = b.user_id;
Key Differences:

INNER JOIN: Returns only matching records from both tables
LEFT JOIN: Returns all records from left table + matching records from right table (NULLs for non-matches)
FULL OUTER JOIN: Returns all records from both tables, with NULLs where no match exists
Note: MySQL doesn't support FULL OUTER JOIN directly, but it can be simulated with UNION of LEFT and RIGHT joins
