---
title: "Usando os serviços TCP"
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
- requesting data from Internet, TCP
- receiving data, TCP
- TcpClient class, about TcpClient class
- data requests, TCP
- application protocols, TCP
- network resources, TCP
- sending data, TCP
- TCP
- protocols, TCP
- Internet, TCP
ms.assetid: d2811830-3bcb-495c-b82d-cda9cf919aad
caps.latest.revision: "11"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 5fce23d35c5c90799960a8075b610e5b7294ef66
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="using-tcp-services"></a><span data-ttu-id="e2aae-102">Usando os serviços TCP</span><span class="sxs-lookup"><span data-stu-id="e2aae-102">Using TCP Services</span></span>
<span data-ttu-id="e2aae-103">A classe <xref:System.Net.Sockets.TcpClient> solicita dados de um recurso da Internet usando o TCP.</span><span class="sxs-lookup"><span data-stu-id="e2aae-103">The <xref:System.Net.Sockets.TcpClient> class requests data from an Internet resource using TCP.</span></span> <span data-ttu-id="e2aae-104">Os métodos e as propriedades de **TcpClient** abstraem os detalhes para criar um <xref:System.Net.Sockets.Socket> para solicitar e receber dados usando o TCP.</span><span class="sxs-lookup"><span data-stu-id="e2aae-104">The methods and properties of **TcpClient** abstract the details for creating a <xref:System.Net.Sockets.Socket> for requesting and receiving data using TCP.</span></span> <span data-ttu-id="e2aae-105">Como a conexão com o dispositivo remoto é representada como um fluxo, os dados podem ser lidos e gravados com técnicas de manipulação de fluxo do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e2aae-105">Because the connection to the remote device is represented as a stream, data can be read and written with .NET Framework stream-handling techniques.</span></span>  
  
 <span data-ttu-id="e2aae-106">O protocolo TCP estabelece uma conexão com um ponto de extremidade remoto e, em seguida, usa essa conexão para enviar e receber pacotes de dados.</span><span class="sxs-lookup"><span data-stu-id="e2aae-106">The TCP protocol establishes a connection with a remote endpoint and then uses that connection to send and receive data packets.</span></span> <span data-ttu-id="e2aae-107">O TCP é responsável por garantir que os pacotes de dados são enviados para o ponto de extremidade e montados na ordem correta quando chegarem.</span><span class="sxs-lookup"><span data-stu-id="e2aae-107">TCP is responsible for ensuring that data packets are sent to the endpoint and assembled in the correct order when they arrive.</span></span>  
  
 <span data-ttu-id="e2aae-108">Para estabelecer uma conexão TCP, você deve saber o endereço do dispositivo de rede que hospeda o serviço necessário e saber a porta TCP usada pelo serviço para se comunicar.</span><span class="sxs-lookup"><span data-stu-id="e2aae-108">To establish a TCP connection, you must know the address of the network device hosting the service you need and you must know the TCP port that the service uses to communicate.</span></span> <span data-ttu-id="e2aae-109">A IANA (Internet Assigned Numbers Authority) define os números da porta de serviços comuns (consulte www.iana.org/assignments/port-numbers).</span><span class="sxs-lookup"><span data-stu-id="e2aae-109">The Internet Assigned Numbers Authority (Iana) defines port numbers for common services (see www.iana.org/assignments/port-numbers).</span></span> <span data-ttu-id="e2aae-110">Os serviços que não estão na lista da IANA podem ter números de porta no intervalo de 1.024 a 65.535.</span><span class="sxs-lookup"><span data-stu-id="e2aae-110">Services not on the Iana list can have port numbers in the range 1,024 to 65,535.</span></span>  
  
 <span data-ttu-id="e2aae-111">O exemplo a seguir demonstra a configuração de um **TcpClient** para se conectar a um servidor de horário na porta TCP 13.</span><span class="sxs-lookup"><span data-stu-id="e2aae-111">The following example demonstrates setting up a **TcpClient** to connect to a time server on TCP port 13.</span></span>  
  
```vb  
Imports System  
Imports System.Net.Sockets  
Imports System.Text  
  
Public Class TcpTimeClient  
    Private const portNum As Integer = 13  
    Private const hostName As String = "host.contoso.com"  
  
    ' Entry point  that delegates to C-style main Private Function.  
    Public Overloads Shared Sub Main()  
        System.Environment.ExitCode = _  
            Main(System.Environment.GetCommandLineArgs())  
    End Sub  
  
    Overloads Public Shared Function Main(args() As [String]) As Integer  
        Try  
            Dim client As New TcpClient(hostName, portNum)  
  
            Dim ns As NetworkStream = client.GetStream()  
  
            Dim bytes(1024) As Byte  
            Dim bytesRead As Integer = ns.Read(bytes, 0, bytes.Length)  
  
            Console.WriteLine(Encoding.ASCII.GetString(bytes, 0, bytesRead))  
  
        Catch e As Exception  
            Console.WriteLine(e.ToString())  
        End Try  
  
        client.Close()  
  
        Return 0  
    End Function 'Main  
End Class 'TcpTimeClient  
```  
  
```csharp  
using System;  
using System.Net.Sockets;  
using System.Text;  
  
public class TcpTimeClient {  
    private const int portNum = 13;  
    private const string hostName = "host.contoso.com";  
  
    public static int Main(String[] args) {  
        try {  
            TcpClient client = new TcpClient(hostName, portNum);  
  
            NetworkStream ns = client.GetStream();  
  
            byte[] bytes = new byte[1024];  
            int bytesRead = ns.Read(bytes, 0, bytes.Length);  
  
            Console.WriteLine(Encoding.ASCII.GetString(bytes,0,bytesRead));  
  
            client.Close();  
  
        } catch (Exception e) {  
            Console.WriteLine(e.ToString());  
        }  
  
        return 0;  
    }  
}  
```  
  
 <span data-ttu-id="e2aae-112"><xref:System.Net.Sockets.TcpListener> é usado para monitorar uma porta TCP para solicitações de entrada e, em seguida, criar um **Socket** ou um **TcpClient** que gerencia a conexão com o cliente.</span><span class="sxs-lookup"><span data-stu-id="e2aae-112"><xref:System.Net.Sockets.TcpListener> is used to monitor a TCP port for incoming requests and then create either a **Socket** or a **TcpClient** that manages the connection to the client.</span></span> <span data-ttu-id="e2aae-113">O método <xref:System.Net.Sockets.TcpListener.Start%2A> habilita a escuta e o método <xref:System.Net.Sockets.TcpListener.Stop%2A> desabilita a escuta na porta.</span><span class="sxs-lookup"><span data-stu-id="e2aae-113">The <xref:System.Net.Sockets.TcpListener.Start%2A> method enables listening, and the <xref:System.Net.Sockets.TcpListener.Stop%2A> method disables listening on the port.</span></span> <span data-ttu-id="e2aae-114">O método <xref:System.Net.Sockets.TcpListener.AcceptTcpClient%2A> aceita solicitações de conexão de entrada e cria um **TcpClient** para manipular a solicitação e o método <xref:System.Net.Sockets.TcpListener.AcceptSocket%2A> aceita solicitações de conexão de entrada e cria um **Socket** para manipular a solicitação.</span><span class="sxs-lookup"><span data-stu-id="e2aae-114">The <xref:System.Net.Sockets.TcpListener.AcceptTcpClient%2A> method accepts incoming connection requests and creates a **TcpClient** to handle the request, and the <xref:System.Net.Sockets.TcpListener.AcceptSocket%2A> method accepts incoming connection requests and creates a **Socket** to handle the request.</span></span>  
  
 <span data-ttu-id="e2aae-115">O exemplo a seguir demonstra como criar um servidor de horário da rede usando um **TcpListener** para monitorar a porta TCP 13.</span><span class="sxs-lookup"><span data-stu-id="e2aae-115">The following example demonstrates creating a network time server using a **TcpListener** to monitor TCP port 13.</span></span> <span data-ttu-id="e2aae-116">Quando uma solicitação de conexão de entrada é aceita, o servidor de horário responde com a data e hora atuais do servidor host.</span><span class="sxs-lookup"><span data-stu-id="e2aae-116">When an incoming connection request is accepted, the time server responds with the current date and time from the host server.</span></span>  
  
```vb  
Imports System  
Imports System.Net.Sockets  
Imports System.Text  
  
Public Class TcpTimeServer  
  
    Private const portNum As Integer = 13  
  
    ' Entry point that delegates to C-style main Private Function.  
    Public Overloads Shared Sub Main()  
        System.Environment.ExitCode = _  
            Main(System.Environment.GetCommandLineArgs())  
    End Sub  
  
    Overloads Public Shared Function Main(args() As [String]) As Integer  
        Dim done As Boolean = False  
  
        Dim listener As New TcpListener(portNum)  
  
        listener.Start()  
  
        While Not done  
            Console.Write("Waiting for connection...")  
            Dim client As TcpClient = listener.AcceptTcpClient()  
  
            Console.WriteLine("Connection accepted.")  
            Dim ns As NetworkStream = client.GetStream()  
  
            Dim byteTime As Byte() = _  
                Encoding.ASCII.GetBytes(DateTime.Now.ToString())  
  
            Try  
                ns.Write(byteTime, 0, byteTime.Length)  
                ns.Close()  
                client.Close()  
            Catch e As Exception  
                Console.WriteLine(e.ToString())  
            End Try  
        End While  
  
        listener.Stop()  
  
        Return 0  
    End Function 'Main  
End Class 'TcpTimeServer  
```  
  
```csharp  
using System;  
using System.Net.Sockets;  
using System.Text;  
  
public class TcpTimeServer {  
  
    private const int portNum = 13;  
  
    public static int Main(String[] args) {  
        bool done = false;  
  
        TcpListener listener = new TcpListener(portNum);  
  
        listener.Start();  
  
        while (!done) {  
            Console.Write("Waiting for connection...");  
            TcpClient client = listener.AcceptTcpClient();  
  
            Console.WriteLine("Connection accepted.");  
            NetworkStream ns = client.GetStream();  
  
            byte[] byteTime = Encoding.ASCII.GetBytes(DateTime.Now.ToString());  
  
            try {  
                ns.Write(byteTime, 0, byteTime.Length);  
                ns.Close();  
                client.Close();  
            } catch (Exception e) {  
                Console.WriteLine(e.ToString());  
            }  
        }  
  
        listener.Stop();  
  
        return 0;  
    }  
  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="e2aae-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e2aae-117">See Also</span></span>  
 
