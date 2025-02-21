import java.io.IOException;
import java.net.HttpURLConnection;
import java.net.URL;
import java.util.Scanner;
import org.json.JSONObject;

public class WeatherDataScraper {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.print("Enter city name: ");
        String city = scanner.nextLine();
        scanner.close();
        
        String apiKey = "your_api_key_here"; // Replace with your actual API key
        String urlString = "https://api.openweathermap.org/data/2.5/weather?q=" + city + "&appid=" + apiKey;
        
        try {
            URL url = new URL(urlString);
            HttpURLConnection conn = (HttpURLConnection) url.openConnection();
            conn.setRequestMethod("GET");
            int responseCode = conn.getResponseCode();
            
            if (responseCode == 200) {
                Scanner responseScanner = new Scanner(url.openStream());
                StringBuilder inline = new StringBuilder();
                while (responseScanner.hasNext()) {
                    inline.append(responseScanner.nextLine());
                }
                responseScanner.close();
                
                JSONObject jsonObject = new JSONObject(inline.toString());
                System.out.println("Weather Data: " + jsonObject.getJSONObject("main").toString());
            } else {
                System.out.println("Failed to fetch weather data.");
            }
        } catch (IOException e) {
            System.out.println("Error fetching weather data: " + e.getMessage());
        }
    }
}
