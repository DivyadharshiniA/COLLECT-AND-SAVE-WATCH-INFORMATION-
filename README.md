import java.io.BufferedWriter;
import java.io.FileWriter;
import java.io.IOException;
import java.util.Scanner;

 class Watch {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.println("Enter watch brand: ");
        String watch_brand = scanner.nextLine();

        System.out.println("Enter watch model: ");
        String watch_model = scanner.nextLine();

        System.out.println("Enter watch category: ");
        String watch_category = scanner.nextLine();

        System.out.println("Enter watch price: ");
        double watch_price = Double.parseDouble(scanner.nextLine());

        System.out.println("Enter watch warranty (in months): ");
        int watch_warranty = Integer.parseInt(scanner.nextLine());

        // Create a CSV file and write the data
        writeToCSV(watch_brand, watch_model, watch_category, watch_price, watch_warranty);
        System.out.println("Data has been saved to CSV file.");
    }

    private static void writeToCSV(String watch_brand, String watch_model, String watch_category,
                                   double watch_price, int watch_warranty) {
        String csvFileName = "watch_information.csv";

        try (BufferedWriter writer = new BufferedWriter(new FileWriter(csvFileName, true))) {
            // Append the data to the CSV file
            writer.write(watch_brand + "," + watch_model + "," + watch_category + "," +
                    watch_price + "," + watch_warranty);
            writer.newLine(); // Move to the next line
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
