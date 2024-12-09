# 1

Issue description: Sending all users at the same time

Technical description: Returning all of the users in single response, as user base will grow the response will take longer to be returned

Screenshot: ![Users screen](/screenshots/users.png?raw=true)

Recommendation: Lower default limit of the requested users, because on the frontend we are displaying 100 records by default

# 2

Issue description: Requesting user data on tab with finances

Technical description: All of the user data is returned on tab with finances, we don't need this data here cause we have all needed informations from operations route

Screenshot: ![Operations screen](/screenshots/operations.png?raw=true)

Recommendation: Request users data on tab change to Users

# 3

Issue description: Sending all operations at the same time

Technical description: Returning all of the operations in single response, as operations base will grow the response will take longer to be returned

Screenshot: ![Users screen](/screenshots/operations.png?raw=true)

Recommendation: Remove / change the default limit of the operations in endpoint as we now displaying only 101 of them

# 4

Issue description: Deposits, dividents and gains are taking some time to load

Technical description: In above mentioned routes we are performing heavy calculation every time we request data

Screenshot: ![Calculations first screen](/screenshots/calculation-in-routes.png?raw=true)
![Calculations second screen](/screenshots/calculation-in-routes-2.png?raw=true)

Recommendation: Implement caching on the backend and on the request check if there are some changes in data, if yes then call calculate() and return new data, if not return cached data

# 5

Issue description: Lighthouse reports that the image /images/map.jpg is not served in a next-generation format like WebP or AVIF. This leads to inefficient use of resources and slower loading times.

Technical description:
Next-gen formats like WebP or AVIF provide better compression compared to JPEG or PNG. This helps reduce the file size significantly while maintaining image quality, which improves page load speed and reduces bandwidth usage.

Screenshot: ![Lighthouse](/screenshots/lighthouse.png?raw=true)

Recommendation: Convert the image /images/map.jpg to WebP or AVIF format using an image optimization tool or library (e.g., Sharp for Node.js or libwebp for command line).

# 6

Issue description: The image /images/map.jpg is larger than necessary for its display dimensions on the page. This results in wasted bandwidth and slower page performance.

Technical description: Serving oversized images consumes additional resources since the browser has to download the large image and then resize it to fit the actual dimensions used on the page.

Screenshot: ![Lighthouse](/screenshots/lighthouse.png?raw=true)

Recommendation: Determine the exact display dimensions for the image and resize it using an image editor or optimization tool. Ensure that the displayed dimensions in the HTML/CSS match the actual dimensions of the resized image.

# 7

Issue description: The image /images/map.jpg is the largest contentful element painted in the viewport. Its loading contributes significantly to the Largest Contentful Paint (LCP) time of 4,210 ms, which negatively impacts the user-perceived performance of the page.

Technical description: LCP measures how quickly the largest visible content on the screen (e.g., an image or text block) is rendered. High LCP times are often caused by slow server response, unoptimized images, or render-blocking resources. As seen here, the image /images/map.jpg causes delays due to rendering and loading inefficiencies.

Screenshot: ![LCP](/screenshots/LCP.png?raw=true)

Recommendation:

- Optimize image size and format: Compress the image or switch to next-gen formats (e.g., WebP or AVIF).
- Lazy loading: Defer loading the image using loading="lazy" if it is not critical to the above-the-fold content.

# 8

Issue description: The page has a large DOM size, with 1,507 total DOM elements. Excessive DOM size increases memory usage, slows down style calculations, and can cause costly layout reflows. This negatively impacts performance, especially on resource-constrained devices.

Technical description: Large DOM sizes create more work for the browser's rendering engine when processing CSS, JavaScript, and layout updates. The high Maximum DOM Depth (13) and Maximum Child Elements (100) further compound the issue, leading to slower rendering and interactivity.

Screenshot: ![DOM size](/screenshots/DOM-size.png?raw=true)

Recommendation:

- Implement pagination for table
- Lazy load content: Fetch additional data only when necessary, rather than rendering it all upfront.
