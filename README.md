# google-maps-jmeter

Google Maps basic performance test example with JMeter.

## Installation

To get started with this project, follow the steps below to install and configure JMeter:

- Download JMeter: Visit the official Apache JMeter website at https://jmeter.apache.org and download the latest version of JMeter suitable for your operating system.
- Install Java Development Kit (JDK): JMeter requires Java to run. Make sure you have Java Development Kit (JDK) installed on your machine. You can download the JDK from the official Oracle website.
- Extract JMeter: Once the JMeter zip file is downloaded, extract its contents to a directory of your choice.
- Launch JMeter: Navigate to the JMeter installation directory and run the jmeter.bat file (Windows) or jmeter.sh file (Linux/Mac). This will start the JMeter application.
- Verify Installation: To ensure JMeter is installed correctly, you can check the version by selecting Help > About Apache JMeter from the menu bar within the JMeter application.

## Usage

To run the JMeter test, run the following command in your terminal:

```bash
 jmeter -n -t tests/smoke.jmx -l jmeter_log.log -e -f -o reports/ --loglevel INFO
```

It will generate HTML report in the `reports` folder.

## Troubleshooting

- Check that you have a compatible version of Java installed (Java 8 or higher).
- Ensure the JMeter files are extracted correctly and present in the installation directory.
- Increase memory allocation for JMeter if needed.
- Configure firewall settings to allow JMeter communication.
- Set up proxy settings if required.
- Install JMeter plugins correctly and review their documentation.
