# Real-Time Notification System with Go and Kafka

This project demonstrates a real-time notification system built with Go and Apache Kafka. It consists of a producer that sends notifications and a consumer that receives and stores them.

## Prerequisites

- Go (1.23.2 or later)
- Docker and Docker Compose
- curl (for testing)

## Setup

1. Clone the repository:
   ```
   git clone https://github.com/afzalhussain23/kafka-notify.git
   cd kafka-notify
   ```

2. Start the Kafka broker:
   ```
   docker compose up -d
   ```

3. Install the required Go packages:
   ```
   go mod tidy
   ```

## Running the Application

1. Start the producer:
   ```
   go run cmd/producer/producer.go
   ```
   The producer will start on `http://localhost:8080`.

2. In a new terminal, start the consumer:
   ```
   go run cmd/consumer/consumer.go
   ```
   The consumer will start on `http://localhost:8081`.

## Testing the System

1. Send a notification:
   ```
   curl -X POST http://localhost:8080/send \
   -d "fromID=2&toID=1&message=Bruno started following you."
   ```

2. Retrieve notifications for a user:
   ```
   curl http://localhost:8081/notifications/1
   ```

## Project Structure

- `cmd/producer/producer.go`: Contains the Kafka producer and API endpoint for sending notifications.
- `cmd/consumer/consumer.go`: Contains the Kafka consumer and API endpoint for retrieving notifications.
- `pkg/models/models.go`: Defines the data models used in the application.

## References

This project is based on the tutorial: [How to Build a Real-Time Notification System with Go and Kafka](https://www.freecodecamp.org/news/build-a-real-time-notification-system-with-go-and-kafka)

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for more details.
