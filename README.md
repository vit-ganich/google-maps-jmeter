![build](https://github.com/vit-ganich/google-maps-jmeter/actions/workflows/main.yml/badge.svg)

# google-maps-jmeter

Google Maps basic performance test example with JMeter.

## Installation

To get started with this project, follow the steps below to install and configure JMeter:

- Download JMeter: Visit the official Apache JMeter website at https://jmeter.apache.org and download the latest version of JMeter suitable for your operating system.
- Install Java Development Kit (JDK): JMeter requires Java to run. Make sure you have Java Development Kit (JDK) installed on your machine. You can download the JDK from the official Oracle website.
- Extract JMeter: Once the JMeter zip file is downloaded, extract its contents to a directory of your choice.
- Launch JMeter: Navigate to the JMeter installation directory and run the jmeter.bat file (Windows) or jmeter.sh file (Linux/Mac). This will start the JMeter application.
- Verify Installation: To ensure JMeter is installed correctly, you can check the version by selecting Help > About Apache JMeter from the menu bar within the JMeter application.

---

## Usage

To run the JMeter test, run the following command in your terminal:

```bash
 jmeter -n -t tests/smoke.jmx -l jmeter_log.log -e -f -o reports/ --loglevel INFO
```

It will generate HTML report in the `reports` folder.

---

## Scripts explanation

- `User Defined Variables`  
  Contains the shared variables for all the controllers, i.e. HOST, PROTOCOL, LOOPS_COUNT, etc.
- `HTTP Request Defaults`  
  This section is empty, but usually this config element is used when all requests in the JMeter script are sent to the same server
- `HTTP Cookie Manager`  
  Cookie management
- `CSV Data Set Config`  
  Handling the csv data set. In our case the csv file contains city names. Used by all the threads/users
- `Thread group`  
  Entry point for the test script, here can be speicified the amount of test users/threads, ramp-up, etc.  
  Scripts:
  - `View maps`
  - `Search by a city name`
  - `Get directions`

---

### CI configuration

```yaml
on:
  workflow_dispatch:
    inputs:
      threads:
        type: number
        required: true
        description: Threads number
        default: 5
```

Only workflow_dispatch trigger is enabled. The amount of threads can be specified.  
Test report is stored in artifacts.

> This CI configuration is created for demonstration purposes. It is not recommended to run a real perfomance testing from the CI jobs.  
> It is better to run tests from the local machine to avoid possible performance and network issues, connected with the AWS/Azure instances.

---

### How to set the threads number correctly?

The number of threads or concurrent users that a system can handle depends on various factors:

- performance requirements
- hardware capabilities
- software architecture

Here are some considerations when determining the appropriate number of threads for a system:

> _Performance Requirements_: Define the desired performance metrics for your system, such as response time, throughput, and resource utilization.
> These requirements will influence the number of threads you need to handle the expected workload.

> _Planned Daily Visitors_: Estimate the number of visitors your system is expected to handle per day.
> This will give you an idea of the potential concurrent users and the load on the system.

> _Workload Characteristics_: Understand the nature of the workload your system will encounter.
> Different types of applications (e.g., web applications, API services, background tasks) may have varying concurrency patterns and resource requirements.

> _Hardware and Infrastructure_: Consider the capabilities of your hardware and infrastructure.
> Factors like CPU cores, memory, network bandwidth, and storage can influence the number of concurrent users your system can handle effectively.

> _Software Architecture_: Evaluate the design and architecture of your software.
> Some applications are naturally more scalable and can handle a larger number of concurrent users by design. Ensure your software can efficiently utilize multiple threads and scale horizontally if necessary.

> _Load Testing and Performance Tuning_: Perform load testing to simulate realistic workloads and measure system performance under different loads.
> Adjust the number of threads and tune your system based on the observed results to find the optimal balance between performance and resource utilization.

The optimal number of threads may vary depending on your specific system and requirements. It's important to monitor system performance in production and be prepared to scale resources, adjust thread counts, or optimize code as needed to ensure smooth operation under real-world conditions.

---

## Troubleshooting

- Check that you have a compatible version of Java installed (Java 8 or higher).
- Ensure the JMeter files are extracted correctly and present in the installation directory.
- Increase memory allocation for JMeter if needed.
- Configure firewall settings to allow JMeter communication.
- Set up proxy settings if required.
- Install JMeter plugins correctly and review their documentation.

```

```
