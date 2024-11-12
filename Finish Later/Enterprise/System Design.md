## Scaling

Suppose we have one machine running our web application, and it is running out of resources. How do we scale of that machine to handle more users? The easiest solution is to use **vertical scaling**, which is adding more resources to the machine. Alternatively, we can implement **horizontal scaling** by adding **replicas** to handle subsets or whole requests. Horizontal scaling is a better solution because it is infinitely scalable, adds redundancy, and adds fault tolerance.

## Load Balancing

When we use horizontal scaling, we need to be able to ensure that individual machines in our cluster are not overburdened by more requests than the rest. To fix this, we use a **load balancer** (also known as a **reverse proxy**), whose whole purpose is to receive all of the requests and route them to the correct server. These servers may use algorithms such as [[Round Robin|round-robin]] or [[Hashing|hashing]]. Additionally, if we have distributed server locations in different parts of the world, a load balancer is able to route to the nearest server location.

## Content Delivery

We use a **content-delivery network** (CDN) to deliver static content (content that does not need external data to operate). Some such content may be images, basic HTML, and more. They take content from the origin server, namely images, HTML, and other static content, and store it for faster delivery to nearby users. CDNs operate in either a **push** or **pull** fashion.

## Caching

We use [[06_link_layer|caching]] to store frequently used data for faster delivery.

<https://youtu.be/EN4fEbcFZ_E?si=o4xoQLAPtDYUgspo>
