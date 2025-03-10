# YUDI - Threat Intelligence Lookup Tool

**YUDI** is an open-source tool designed to help cybersecurity professionals and researchers investigate threat intelligence data from various sources and feeds. The tool focuses on querying Indicators of Compromise (IOCs), filtering data, and drawing relations between different types of IOCs.

YUDI provides an easy way to look up IOCs, including IP addresses, hashes, domains, URLs, and more. It integrates with various external threat intelligence platforms to gather valuable data on security threats.

## Features

- **IOC Lookup**: Query a variety of IOCs including IPs, URLs, domains, and hashes.
- **Integration with OTX**: Fetch threat intelligence from the Open Threat Exchange (OTX) and other feeds.
- **Asynchronous Calls**: Handle multiple IOC lookups concurrently for efficient threat intelligence investigations.
- **Comprehensive IOC Classification**: Automatically classify IOCs into different types (IP, hash, domain, URL).
- **Error Handling and Debugging**: Built-in error handling and debug logging for easier troubleshooting.

## Installation

Clone the repository:

   ```bash
      git clone https://github.com/yourusername/yudi.git
      cd yudi
   ```

## 🚀 Usage

### **Basic Command Format**  
```bash
python threat_lookup.py -t <IOC_TYPE> -i <IOC_VALUE>
```

### **Options and Flags:**  
| Flag | Description | Example |
|------|------------|---------|
| `-t, --type` | Specifies the IOC type (`ip`, `hash`, `url`, or `domain`). | `-t ip` |
| `-i, --ioc` | The IOC (Indicator of Compromise) to be analyzed. | `-i 8.8.8.8` |
| `-h, --help` | Displays usage information. | `-h` |

### **Examples:**  

#### **Check an IP Address**  
```bash
python threat_lookup.py -t ip -i 8.8.8.8
```

#### **Analyze a File Hash**  
```bash
python threat_lookup.py -t hash -i d41d8cd98f00b204e9800998ecf8427e
```

#### **Scan a URL**  
```bash
python threat_lookup.py -t url -i https://malicious-site.com
```

#### **Investigate a Domain**  
```bash
python threat_lookup.py -t domain -i example.com
```

### **Output**  
- The script collects data from multiple threat intelligence sources like **VirusTotal, AbuseIPDB, URLScan, and Shodan**.
- Results are saved in a structured JSON file based on the IOC type.
- Example output file: `report.json`  

```json
{
    "check_abuseipdb": { "ip": "8.8.8.8", "score": 25, "country": "US" },
    "search_virus_total": { "hash": "abcd1234", "positives": 5 },
    "urlscan_submission": { "url": "example.com", "status": "malicious" },
    "shodan": { "ip": "8.8.8.8", "ports": [80, 443] }
}
```

## 🛠 Backend Requirements
- Python 3.7+
- Install dependencies using:
  ```bash
  pip install -r requirements.txt
  ```

## 📡 Serving `report.json` via Quart
You can serve the `report.json` file using **FastAPI** to expose the threat intelligence data through an API.

### **Running the FastAPI Server**
Start the FastAPI server with:
```bash
python app.py
```

### **Access the Report**
Once the server is running, access the report via:
```bash
curl http://127.0.0.1:8000/get_report
```
This will return the contents of `report.json`.

## 🌐 Frontend Installation and Requirements
The frontend is built using **Vite + React + TypeScript** to provide an interactive dashboard for visualizing threat intelligence data.

### **Frontend Requirements**
- Node.js 16+
- npm or yarn

### **Installing the Frontend**
Navigate to the `frontend` directory and install dependencies:
```bash
cd yudi-frontend
npm install  # or yarn install
```

### **Running the Frontend**
Start the development server:
```bash
npm run dev  # or yarn dev
```
This will start the Vite development server. Open **http://localhost:5173** in your browser.

### **Connecting the Frontend to the Backend**
To link the frontend with the backend, update the API URL in `src/config.ts`:
```ts
export const API_BASE_URL = "http://0.0.0.0:5000";
```
Now, the frontend will fetch IOC data from the backend's API.

## 📢 Contributing
Feel free to open issues and pull requests for improvements. Your contributions are welcome! 🚀

## 🔥 Making a Pull Request

🚀 **Contribute to the Threat Intelligence Lookup Tool!**  

Found a bug or have an improvement? Fork the repo, create a new branch, make your changes, and submit a pull request! We appreciate your contributions. 🔍✨  

📌 **Steps:**  
1. Fork the repository  
2. Create a new branch (`git checkout -b feature-branch`)  
3. Commit your changes (`git commit -m "Add feature/fix"`)  
4. Push to your branch (`git push origin feature-branch`)  
5. Open a pull request 🚀  

Looking forward to your contributions! 🔥

