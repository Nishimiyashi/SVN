import java.util.LinkedList;
import java.util.Queue;

public class CarWashService {
    private Queue<String> carQueue;

    public CarWashService() {
        carQueue = new LinkedList<>();
    }

    // Car arrives at the car wash and joins the queue
    public void arriveAtCarWash(String car) {
        carQueue.offer(car);
        System.out.println(car + " has arrived at the car wash and joined the queue.");
    }

    // Retrieve the next car in the queue without dequeuing
    public String nextCarInQueue() {
        return carQueue.peek();
    }

    // Car wash completes for the next car in the queue
    public void carWashCompleted() {
        if (!carQueue.isEmpty()) {
            String car = carQueue.poll();
            System.out.println(car + " has completed the car wash.");
        } else {
            System.out.println("No cars in the queue.");
        }
    }

    // Check if the car queue is empty
    public boolean isEmpty() {
        return carQueue.isEmpty();
    }

    // Get the size of the car queue
    public int queueSize() {
        return carQueue.size();
    }

    // Display the cars currently in the queue
    public void displayQueue() {
        if (isEmpty()) {
            System.out.println("No cars in the queue.");
        } else {
            System.out.println("Cars currently in the queue:");
            for (String car : carQueue) {
                System.out.println(car);
            }
        }
    }

    public static void main(String[] args) {
        CarWashService carWash = new CarWashService();

        carWash.arriveAtCarWash("Car 1");
        carWash.arriveAtCarWash("Car 2");
        carWash.arriveAtCarWash("Car 3");

        carWash.displayQueue();

        System.out.println("Next car in queue: " + carWash.nextCarInQueue());

        carWash.carWashCompleted();
        carWash.carWashCompleted();
        carWash.carWashCompleted();

        carWash.displayQueue();
    }
}
