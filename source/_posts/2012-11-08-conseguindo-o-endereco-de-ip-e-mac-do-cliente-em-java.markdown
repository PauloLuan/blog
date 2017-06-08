---
author: pauloluan
comments: true
date: 2012-11-08 08:51:34
layout: post
slug: conseguindo-o-endereco-de-ip-e-mac-do-cliente-em-java
title: Conseguindo o endereço de IP e Mac do cliente em Java
wordpress_id: 791
categories:
- Java
tags:
- ip
- java
- mac
- macaddress
- programação
---

``` java 


	// pegando o endereço de MAC
	public void testGetMacAddress() {
		try {
			InetAddress address = InetAddress.getLocalHost();
			NetworkInterface ni = NetworkInterface.getByInetAddress(address);
			byte[] mac = ni.getHardwareAddress();
			String macAddress = "";

			for (int i = 0; i < mac.length; i++) {
				String macTemporary = String.format("%02X%s", mac[i], (i < mac.length - 1) ? "-" : "");
				macAddress += macTemporary;
				//System.out.format("%02X%s", mac[i], (i < mac.length - 1) ? "-" : "");
			}
			System.out.println("Mac Address: " + macAddress);
		} catch (UnknownHostException e) {
			e.printStackTrace();
		} catch (SocketException e) {
			e.printStackTrace();
		}
	}

	// pegando o endereço de IP
	public void testGetIP() {
		try {
			String ip = InetAddress.getLocalHost().getHostAddress();
			System.out.println("Endereço de IP: " + ip);
		} catch (UnknownHostException e) {
			e.printStackTrace();
		}
	}

```


Testei no Mac o código anterior e funcionou corretamente, porém tive alguns problemas ao rodar no windows e linux, no entanto encontrei o código a seguir e ainda não testei...


``` java 

public final class NetworkInfo {

	public NetworkInfo(){

	}

    private final static String getMacAddress() throws IOException {
        String os = System.getProperty("os.name");
        try {
            if(os.startsWith("Windows")) {
                return windowsParseMacAddress(windowsRunIpConfigCommand());
            } else if(os.startsWith("Linux")) {
                return linuxParseMacAddress(linuxRunIfConfigCommand());
            } else {
                throw new IOException("Sistema operacional desconhecido: " + os);
            }
        } catch(ParseException ex) {
            ex.printStackTrace();
            throw new IOException(ex.getMessage());
        }
    }

    /*
     * Linux
     */
    private final static String linuxParseMacAddress(String ipConfigResponse) throws ParseException {
        String localHost = null;
        try {
            localHost = InetAddress.getLocalHost().getHostAddress();
        } catch(java.net.UnknownHostException ex) {
            ex.printStackTrace();
            throw new ParseException(ex.getMessage(), 0);
        }

        StringTokenizer tokenizer = new StringTokenizer(ipConfigResponse, "n");
        String lastMacAddress = null;

        while(tokenizer.hasMoreTokens()) {
            String line = tokenizer.nextToken().trim();
            boolean containsLocalHost = line.indexOf(localHost) >= 0;

            //IP
            if(containsLocalHost && lastMacAddress != null) {
                return lastMacAddress;
            }

            //MAC address
            int macAddressPosition = line.indexOf("HWaddr");
            if(macAddressPosition <= 0) continue;

            String macAddressCandidate = line.substring(macAddressPosition + 6).trim();
            if(linuxIsMacAddress(macAddressCandidate)) {
                lastMacAddress = macAddressCandidate;
                continue;
            }
        }

        ParseException ex = new ParseException
            ("Nao foi possível ler o MAC address para " + localHost + " de [" + ipConfigResponse + "]", 0);
        ex.printStackTrace();
        throw ex;
    }

    private final static boolean linuxIsMacAddress(String macAddressCandidate) {
        if(macAddressCandidate.length() != 17) return false;
        return true;
    }

    private final static String linuxRunIfConfigCommand() throws IOException {
        Process p = Runtime.getRuntime().exec("ifconfig");
        InputStream stdoutStream = new BufferedInputStream(p.getInputStream());

        StringBuffer buffer= new StringBuffer();
        for (;;) {
            int c = stdoutStream.read();
            if (c == -1) break;
            buffer.append((char)c);
        }
        String outputText = buffer.toString();

        stdoutStream.close();

        return outputText;
    }

    /*
     * Windows
     */
    private final static String windowsParseMacAddress(String ipConfigResponse) throws ParseException {
        String localHost = null;
        try {
            localHost = InetAddress.getLocalHost().getHostAddress();
        } catch(java.net.UnknownHostException ex) {
            ex.printStackTrace();
            throw new ParseException(ex.getMessage(), 0);
        }

        StringTokenizer tokenizer = new StringTokenizer(ipConfigResponse, "n");
        String lastMacAddress = null;

        while(tokenizer.hasMoreTokens()) {
            String line = tokenizer.nextToken().trim();

            //IP
            if(line.endsWith(localHost) && lastMacAddress != null) {
                return lastMacAddress;
            }

            //MAC address
            int macAddressPosition = line.indexOf(":");
            if(macAddressPosition <= 0) continue;

            String macAddressCandidate = line.substring(macAddressPosition + 1).trim();
            if(windowsIsMacAddress(macAddressCandidate)) {
                lastMacAddress = macAddressCandidate;
                continue;
            }
        }

        ParseException ex = new ParseException("Nao foi possível ler o MAC address de [" + ipConfigResponse + "]", 0);
        ex.printStackTrace();
        throw ex;
    }

    private final static boolean windowsIsMacAddress(String macAddressCandidate) {
        if(macAddressCandidate.length() != 17) return false;

        return true;
    }

    private final static String windowsRunIpConfigCommand() throws IOException {
        Process p = Runtime.getRuntime().exec("ipconfig /all");
        InputStream stdoutStream = new BufferedInputStream(p.getInputStream());

        StringBuffer buffer= new StringBuffer();
        for (;;) {
            int c = stdoutStream.read();
            if (c == -1) break;
            buffer.append((char)c);
        }
        String outputText = buffer.toString();

        stdoutStream.close();

        return outputText;
    }
public final static void main(String[] args) {
        try {
            System.out.println("Informacoes");
            System.out.println("Sistema operacional: " + System.getProperty("os.name"));
            System.out.println("IP/Localhost: " + InetAddress.getLocalHost().getHostAddress());
            System.out.println("MAC Address: " + getMacAddress());
            System.out.println("Nome da maquina: " + InetAddress.getLocalHost().getHostName());
            System.out.println("Nome completo da maquina: " + InetAddress.getLocalHost().getCanonicalHostName());
        } catch(Throwable t) {
            t.printStackTrace();
        }
    }

}
```


FONTES:

http://www.guj.com.br/java/83460-capturar-endereco-mac-e-ip-alguem
http://paulovittor23.org/2008/02/01/pegando-o-mac-address-antes-e-depois-do-mustang-java-6/
