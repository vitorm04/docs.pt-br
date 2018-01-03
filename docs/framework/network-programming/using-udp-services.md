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
- csharp
- vb
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
caps.latest.revision: "15"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 86f44c5aa4c744ab6966f0cb6b3834dd1f5f0f48
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="using-udp-services"></a><span data-ttu-id="f1091-102">Usando os serviços UDP</span><span class="sxs-lookup"><span data-stu-id="f1091-102">Using UDP Services</span></span>
<span data-ttu-id="f1091-103">A classe <xref:System.Net.Sockets.UdpClient> se comunica com os serviços de rede usando o UDP.</span><span class="sxs-lookup"><span data-stu-id="f1091-103">The <xref:System.Net.Sockets.UdpClient> class communicates with network services using UDP.</span></span> <span data-ttu-id="f1091-104">As propriedades e os métodos da classe <xref:System.Net.Sockets.UdpClient> abstraem os detalhes da criação de um <xref:System.Net.Sockets.Socket> para solicitar e receber dados usando o UDP.</span><span class="sxs-lookup"><span data-stu-id="f1091-104">The properties and methods of the <xref:System.Net.Sockets.UdpClient> class abstract the details of creating a <xref:System.Net.Sockets.Socket> for requesting and receiving data using UDP.</span></span>  
  
 <span data-ttu-id="f1091-105">O protocolo UDP é um protocolo simples que se esforça para fornecer dados para um host remoto.</span><span class="sxs-lookup"><span data-stu-id="f1091-105">User Datagram Protocol (UDP) is a simple protocol that makes a best effort to deliver data to a remote host.</span></span> <span data-ttu-id="f1091-106">No entanto, como o protocolo UDP é um protocolo sem conexão, os datagramas UDP enviados para o ponto de extremidade remoto não têm a garantia de serem recebidos, nem a garantia de serem recebidos na mesma sequência em que são enviados.</span><span class="sxs-lookup"><span data-stu-id="f1091-106">However, because the UDP protocol is a connectionless protocol, UDP datagrams sent to the remote endpoint are not guaranteed to arrive, nor are they guaranteed to arrive in the same sequence in which they are sent.</span></span> <span data-ttu-id="f1091-107">Os aplicativos que usam o UDP devem estar preparados para manipular datagramas ausentes, duplicados e fora de sequência.</span><span class="sxs-lookup"><span data-stu-id="f1091-107">Applications that use UDP must be prepared to handle missing, duplicate, and out-of-sequence datagrams.</span></span>  
  
 <span data-ttu-id="f1091-108">Para enviar um datagrama usando o UDP, você deve saber o endereço de rede do dispositivo de rede que hospeda o serviço necessário e o número da porta UDP usada pelo serviço para se comunicar.</span><span class="sxs-lookup"><span data-stu-id="f1091-108">To send a datagram using UDP, you must know the network address of the network device hosting the service you need and the UDP port number that the service uses to communicate.</span></span> <span data-ttu-id="f1091-109">A IANA (Internet Assigned Numbers Authority) define os números da porta de serviços comuns (consulte www.iana.org/assignments/port-numbers).</span><span class="sxs-lookup"><span data-stu-id="f1091-109">The Internet Assigned Numbers Authority (Iana) defines port numbers for common services (see www.iana.org/assignments/port-numbers).</span></span> <span data-ttu-id="f1091-110">Os serviços que não estão na lista da IANA podem ter números de porta no intervalo de 1.024 a 65.535.</span><span class="sxs-lookup"><span data-stu-id="f1091-110">Services not on the Iana list can have port numbers in the range 1,024 to 65,535.</span></span>  
  
 <span data-ttu-id="f1091-111">Endereços de rede especiais são usados para dar suporte a mensagens de difusão do UDP em redes baseadas em IP.</span><span class="sxs-lookup"><span data-stu-id="f1091-111">Special network addresses are used to support UDP broadcast messages on IP-based networks.</span></span> <span data-ttu-id="f1091-112">A discussão a seguir usa a família de endereços IP versão 4 usada na Internet como exemplo.</span><span class="sxs-lookup"><span data-stu-id="f1091-112">The following discussion uses the IP version 4 address family used on the Internet as an example.</span></span>  
  
 <span data-ttu-id="f1091-113">Os endereços IP versão 4 usam 32 bits para especificar um endereço de rede.</span><span class="sxs-lookup"><span data-stu-id="f1091-113">IP version 4 addresses use 32 bits to specify a network address.</span></span> <span data-ttu-id="f1091-114">Para endereços de classe C que usam uma máscara de rede 255.255.255.0, esses bits estão separados em quatro octetos.</span><span class="sxs-lookup"><span data-stu-id="f1091-114">For class C addresses using a netmask of 255.255.255.0, these bits are separated into four octets.</span></span> <span data-ttu-id="f1091-115">Quando expressos em decimais, os quatro octetos formam a notação quádrupla pontilhada conhecida, como 192.168.100.2.</span><span class="sxs-lookup"><span data-stu-id="f1091-115">When expressed in decimal, the four octets form the familiar dotted-quad notation, such as 192.168.100.2.</span></span> <span data-ttu-id="f1091-116">Os dois primeiros octetos (192.168, neste exemplo) formam o número da rede, o terceiro octeto (100) define a sub-rede e o octeto final (2) é o identificador do host.</span><span class="sxs-lookup"><span data-stu-id="f1091-116">The first two octets (192.168 in this example) form the network number, the third octet (100) defines the subnet, and the final octet (2) is the host identifier.</span></span>  
  
 <span data-ttu-id="f1091-117">A configuração de todos os bits de um endereço IP como um ou 255.255.255.255, forma o endereço de difusão limitada.</span><span class="sxs-lookup"><span data-stu-id="f1091-117">Setting all the bits of an IP address to one, or 255.255.255.255, forms the limited broadcast address.</span></span> <span data-ttu-id="f1091-118">O envio de um datagrama UDP para esse endereço entrega a mensagem para qualquer host no segmento de rede local.</span><span class="sxs-lookup"><span data-stu-id="f1091-118">Sending a UDP datagram to this address delivers the message to any host on the local network segment.</span></span> <span data-ttu-id="f1091-119">Como os roteadores nunca encaminham mensagens enviadas para esse endereço, somente os hosts no segmento de rede recebem a mensagem de difusão.</span><span class="sxs-lookup"><span data-stu-id="f1091-119">Because routers never forward messages sent to this address, only hosts on the network segment receive the broadcast message.</span></span>  
  
 <span data-ttu-id="f1091-120">As difusões podem ser direcionadas a partes específicas de uma rede, com a configuração de todos os bits do identificador do host.</span><span class="sxs-lookup"><span data-stu-id="f1091-120">Broadcasts can be directed to specific portions of a network by setting all bits of the host identifier.</span></span> <span data-ttu-id="f1091-121">Por exemplo, para enviar uma difusão para todos os hosts na rede identificada por endereços IP que começam com 192.168.1, use o endereço 192.168.1.255.</span><span class="sxs-lookup"><span data-stu-id="f1091-121">For example, to send a broadcast to all hosts on the network identified by IP addresses starting with 192.168.1, use the address 192.168.1.255.</span></span>  
  
 <span data-ttu-id="f1091-122">O exemplo de código a seguir usa um <xref:System.Net.Sockets.UdpClient> para ouvir datagramas UDP enviados para o endereço de difusão direcionado 192.168.1.255 na porta 11.000.</span><span class="sxs-lookup"><span data-stu-id="f1091-122">The following code example uses a <xref:System.Net.Sockets.UdpClient> to listen for UDP datagrams sent to the directed broadcast address 192.168.1.255 on port 11,000.</span></span> <span data-ttu-id="f1091-123">O cliente recebe uma cadeia de caracteres de mensagem e grava a mensagem no console.</span><span class="sxs-lookup"><span data-stu-id="f1091-123">The client receives a message string and writes the message to the console.</span></span>  
  
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
  
 <span data-ttu-id="f1091-124">O exemplo de código a seguir usa um <xref:System.Net.Sockets.UdpClient> para enviar datagramas UDP para o endereço de difusão direcionado 192.168.1.255, usando a porta 11.000.</span><span class="sxs-lookup"><span data-stu-id="f1091-124">The following code example uses a <xref:System.Net.Sockets.UdpClient> to send UDP datagrams to the directed broadcast address 192.168.1.255, using port 11,000.</span></span> <span data-ttu-id="f1091-125">O cliente envia a cadeia de caracteres de mensagem especificada na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="f1091-125">The client sends the message string specified on the command line.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f1091-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f1091-126">See Also</span></span>  
 <xref:System.Net.Sockets.UdpClient>  
 <xref:System.Net.IPAddress>  
 
