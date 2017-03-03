# Java VPN Detection

Allows you to detect whether or not a specified IPv4 Address belongs to a hosting or vpn / proxy organization.
This library facilitates and simplifies using the web API, and allows you to easily implement the functionality in your java applications.


## Usage

A very basic usage example:

```java
String ipToLookup = "192.184.93.53";
Boolean isHostingorVPN = new VPNDetection().getResponse(ipToLookup).hostip;
System.out.println(isHostingorVPN);
```

A more advanced example:

```java
VPNDetection vpn_detection = new VPNDetection();
new Thread(() -> {
    try {
        String ipToLookup = "192.184.93.53";
        Response api_response = vpn_detection.getResponse(ipToLookup);

        if(api_response.status.equals("success")) {
            System.out.println("Package: " + api_response.getPackage);
            if(api_response.getPackage.equals("Free")) {
                System.out.println("Remaining Requests: " + api_response.remaining_requests);
            }
            System.out.println("IP Address: " + api_response.ipaddress);
            System.out.println("Is this IP a VPN or Hosting Network? " + api_response.hostip);
            System.out.println("Organisation: " + api_response.org);
            if(api_response.country != null) {
                System.out.println("Country: " + api_response.country.name);
            }

        } else {
            System.out.println("Error: " + api_response.msg);
        }

    } catch (IOException ex) {
        System.out.println("Error: " + ex.getMessage());
    }
}).start();
```

## Jar Download
* [Latest Release](https://github.com/HiddenMotives/Java-VPNDetection/releases/latest)

## Required Dependencies
* Gson 2.3.x +
