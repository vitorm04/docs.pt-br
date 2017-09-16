---
title: "Usando os serviços UDP"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- protocols, UDP
- network resources, UDP
- requesting data from Internet, UDP
- UDP
- receiving data, UDP
- Internet, UDP
- broadcasting messages to multiple addresses
- data requests, UDP
- UdpClient class, about UdpClient class
- sending data, UDP
- application protocols, UDP
ms.assetid: d5c3477a-e798-454c-a890-738ba14c5707
caps.latest.revision: 15
author: mcleblanc
ms.author: markl
manager: markl
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 2986feda76b035e3651712609364b4194378a64c
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="using-udp-services"></a>Usando os serviços UDP
A classe <xref:System.Net.Sockets.UdpClient> se comunica com os serviços de rede usando o UDP. As propriedades e os métodos da classe <xref:System.Net.Sockets.UdpClient> abstraem os detalhes da criação de um <xref:System.Net.Sockets.Socket> para solicitar e receber dados usando o UDP.  
  
 O protocolo UDP é um protocolo simples que se esforça para fornecer dados para um host remoto. No entanto, como o protocolo UDP é um protocolo sem conexão, os datagramas UDP enviados para o ponto de extremidade remoto não têm a garantia de serem recebidos, nem a garantia de serem recebidos na mesma sequência em que são enviados. Os aplicativos que usam o UDP devem estar preparados para manipular datagramas ausentes, duplicados e fora de sequência.  
  
 Para enviar um datagrama usando o UDP, você deve saber o endereço de rede do dispositivo de rede que hospeda o serviço necessário e o número da porta UDP usada pelo serviço para se comunicar. A IANA (Internet Assigned Numbers Authority) define os números da porta de serviços comuns (consulte www.iana.org/assignments/port-numbers). Os serviços que não estão na lista da IANA podem ter números de porta no intervalo de 1.024 a 65.535.  
  
 Endereços de rede especiais são usados para dar suporte a mensagens de difusão do UDP em redes baseadas em IP. A discussão a seguir usa a família de endereços IP versão 4 usada na Internet como exemplo.  
  
 Os endereços IP versão 4 usam 32 bits para especificar um endereço de rede. Para endereços de classe C que usam uma máscara de rede 255.255.255.0, esses bits estão separados em quatro octetos. Quando expressos em decimais, os quatro octetos formam a notação quádrupla pontilhada conhecida, como 192.168.100.2. Os dois primeiros octetos (192.168, neste exemplo) formam o número da rede, o terceiro octeto (100) define a sub-rede e o octeto final (2) é o identificador do host.  
  
 A configuração de todos os bits de um endereço IP como um ou 255.255.255.255, forma o endereço de difusão limitada. O envio de um datagrama UDP para esse endereço entrega a mensagem para qualquer host no segmento de rede local. Como os roteadores nunca encaminham mensagens enviadas para esse endereço, somente os hosts no segmento de rede recebem a mensagem de difusão.  
  
 As difusões podem ser direcionadas a partes específicas de uma rede, com a configuração de todos os bits do identificador do host. Por exemplo, para enviar uma difusão para todos os hosts na rede identificada por endereços IP que começam com 192.168.1, use o endereço 192.168.1.255.  
  
 O exemplo de código a seguir usa um <xref:System.Net.Sockets.UdpClient> para ouvir datagramas UDP enviados para o endereço de difusão direcionado 192.168.1.255 na porta 11.000. O cliente recebe uma cadeia de caracteres de mensagem e grava a mensagem no console.  
  
```vb  
Imports System  
Imports System.Net  
Imports System.Net.Sockets  
Imports System.Text  
  
Public Class UDPListener  
   Private Const listenPort As Integer = 11000  
  
   Private Shared Sub StartListener()  
      Dim done As Boolean = False  
      Dim listener As New UdpClient(listenPort)  
      Dim groupEP As New IPEndPoint(IPAddress.Any, listenPort)  
      Try  
         While Not done  
            Console.WriteLine("Waiting for broadcast")  
            Dim bytes As Byte() = listener.Receive(groupEP)  
            Console.WriteLine("Received broadcast from {0} :", _  
                groupEP.ToString())   
            Console.WriteLine( _  
                Encoding.ASCII.GetString(bytes, 0, bytes.Length))  
            Console.WriteLine()  
         End While  
      Catch e As Exception  
         Console.WriteLine(e.ToString())  
      Finally  
         listener.Close()  
      End Try  
   End Sub 'StartListener  
  
   Public Shared Function Main() As Integer  
      StartListener()  
      Return 0  
   End Function 'Main  
End Class 'UDPListener  
```  
  
```csharp  
using System;  
using System.Net;  
using System.Net.Sockets;  
using System.Text;  
  
public class UDPListener   
{  
    private const int listenPort = 11000;  
  
    private static void StartListener()   
    {  
        bool done = false;  
  
        UdpClient listener = new UdpClient(listenPort);  
        IPEndPoint groupEP = new IPEndPoint(IPAddress.Any,listenPort);  
  
        try   
        {  
            while (!done)   
            {  
                Console.WriteLine("Waiting for broadcast");  
                byte[] bytes = listener.Receive( ref groupEP);  
  
                Console.WriteLine("Received broadcast from {0} :\n {1}\n",  
                    groupEP.ToString(),  
                    Encoding.ASCII.GetString(bytes,0,bytes.Length));  
            }  
  
        }   
        catch (Exception e)   
        {  
            Console.WriteLine(e.ToString());  
        }  
        finally  
        {  
            listener.Close();  
        }  
    }  
  
    public static int Main()   
    {  
        StartListener();  
  
        return 0;  
    }  
}  
```  
  
 O exemplo de código a seguir usa um <xref:System.Net.Sockets.UdpClient> para enviar datagramas UDP para o endereço de difusão direcionado 192.168.1.255, usando a porta 11.000. O cliente envia a cadeia de caracteres de mensagem especificada na linha de comando.  
  
```vb  
Imports System  
Imports System.Net  
Imports System.Net.Sockets  
Imports System.Text  
  
Public Class Program  
  
    Overloads Public Shared Function Main(args() As [String]) As Integer  
      Dim s As New Socket(AddressFamily.InterNetwork, SocketType.Dgram,  
          ProtocolType.Udp)  
      Dim broadcast As IPAddress = IPAddress.Parse("192.168.1.255")  
      Dim sendbuf As Byte() = Encoding.ASCII.GetBytes(args(0))  
      Dim ep As New IPEndPoint(broadcast, 11000)  
      s.SendTo(sendbuf, ep)  
      Console.WriteLine("Message sent to the broadcast address")  
   End Function 'Main  
End Class   
```  
  
```csharp  
using System;  
using System.Net;  
using System.Net.Sockets;  
using System.Text;  
  
class Program   
{  
    static void Main(string[] args)   
    {  
        Socket s = new Socket(AddressFamily.InterNetwork, SocketType.Dgram,  
            ProtocolType.Udp);  
  
        IPAddress broadcast = IPAddress.Parse("192.168.1.255");  
  
        byte[] sendbuf = Encoding.ASCII.GetBytes(args[0]);  
        IPEndPoint ep = new IPEndPoint(broadcast, 11000);  
  
        s.SendTo(sendbuf, ep);  
  
        Console.WriteLine("Message sent to the broadcast address");  
    }  
}  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Net.Sockets.UdpClient>   
 <xref:System.Net.IPAddress>   
 

