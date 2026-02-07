## Product choice
- Wildberries.ru
- https://www.wildberries.ru/
- Wildberries is the largest Russian online retailer

## Main components 
![Wildberries Component Architecture](../../../docs/diagrams/out/wildberries/architecture-component/Component%20Diagram.svg)
[Wildberries Component Architecture PlantUML code](../../../docs/diagrams/src/wildberries/architecture-component.puml)

- Auth & ID Service: Handling user authentication/authorization, managing users' accesses (customers, sellers, VIP-users, etc.)
- Fintech & Payment Service: Handling payment processing, secure transactions (payments/refunds), and integration with external banks and payment providers.
- Notification Service: Handling and delivering notifications (push, email, SMS), such as order updates, promotions, alerts, and other.
- Logistics & Routing: Determining optimal shipping paths, calculating delivery timelines and costs, coordinating the delivery (internal or external) services.
- Order Management: Managing orders, checking the availability, coordinating the completion of the order (payment, delivery, etc.)

## Data flow

![Wildberries Sequence Architecture](../../../docs/diagrams/out/wildberries/architecture-sequence/Sequence%20Diagram.svg)
[Wildberries Sequence Architecture PlantUML code](../../../docs/diagrams/src/wildberries/architecture-sequence.puml)

Warehouse Fulfillment (Async)

Firstly, the OrderPaid event is consumed. After that, the closest warehouse is chosen, and the warehouse assembles the order physically. After that the order gets status "Assembly Completed" and awaits for shipping. After that the order becomes ready for shipping, the user gets notification and the goods are sent to the way to the user.


## Deployment
![Wildberries Deployment Architecture](../../../docs/diagrams/out/wildberries/architecture-deployment/Deployment%20Diagram.svg)
[Wildberries Deployment Architecture PlantUML code](../../../docs/diagrams/src/wildberries/architecture-deployment.puml)

Wildberries Deployment Architecture can be divided to 3 major parts. First part is frontend, which provides an app or website for user to interact with Wildberries. Second part is global infrastructure that can be represented as a cluster of various groups (such as microservices, DB system, search index, etc.). Finally, Wildberries use external services (payment providers, logistics, SMS / Push providers), so that any user can comfortably make orders.

## Assumptions

- I assume the Logistics & Routing service integrates with multiple delivery partners to optimize shipping costs and delivery times
- I assume Fintech & Payment Service collaborates with multiple banking and payment systems to provide for user a wider range of available ways for payment

## Open questions

- What specific caching strategies does Wildberries use to handle high traffic during sales events?
- Which factors does Catalog & Search Service rely on when processing a search request?