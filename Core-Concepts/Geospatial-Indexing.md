**Geospatial Indexing**

**What is Geospatial Indexing?**

Geospatial indexing is a method used to efficiently store, query, and manage geographic data (like locations on a map). It allows applications to perform operations like finding points within a specific region, calculating distances, or sorting points based on proximity.

Eg. Ride Sharing Apps (Uber, Lyft) to find available drivers nearby, Restaurant Finder/rating (Yelp), and Finding Partners (Tinder).

--------------------------------------------------------------

**How does Geospatial Indexing Work?**

- Geographic locations are represented using **latitude** and **longitude**. These are numerical values that define a specific point on Earth.
- The Earth is divided into a **grid**, each cell representing a geographical area.
- Each cell is recursively subdivided into smaller cells as the geohash becomes longer.
- Each grid cell is assigned a **unique alphanumeric code** based on the coordinate range it represents.
- The more characters in the geohash, the smaller the grid cell (higher precision).
- By matching prefixes, geohashing quickly narrows down the search to locations within the same or nearby grids, avoiding the need to scan all data points.

--------------------------------------------------------------
