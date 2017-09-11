---
title: "Exemplo de soquete de servidor síncrono"
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
- synchronous server sockets
- sockets, code examples
- sockets, synchronous server sockets
ms.assetid: 5916c764-879f-4716-99fb-1d21c6237f1c
caps.latest.revision: 8
author: mcleblanc
ms.author: markl
manager: markl
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 6918042ac04a24f646ce8fd10a86d64c2aa4fd39
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="synchronous-server-socket-example"></a><span data-ttu-id="3f9e9-102">Exemplo de soquete de servidor síncrono</span><span class="sxs-lookup"><span data-stu-id="3f9e9-102">Synchronous Server Socket Example</span></span>
<span data-ttu-id="3f9e9-103">O programa de exemplo a seguir cria um servidor que recebe solicitações de conexão de clientes.</span><span class="sxs-lookup"><span data-stu-id="3f9e9-103">The following example program creates a server that receives connection requests from clients.</span></span> <span data-ttu-id="3f9e9-104">O servidor é criado com um soquete síncrono e, portanto, a execução do aplicativo para servidores é suspensa enquanto ele aguarda uma conexão de um cliente.</span><span class="sxs-lookup"><span data-stu-id="3f9e9-104">The server is built with a synchronous socket, so execution of the server application is suspended while it waits for a connection from a client.</span></span> <span data-ttu-id="3f9e9-105">O aplicativo recebe uma cadeia de caracteres do cliente, exibe a cadeia de caracteres no console e, em seguida, retorna-a ao cliente.</span><span class="sxs-lookup"><span data-stu-id="3f9e9-105">The application receives a string from the client, displays the string on the console, and then echoes the string back to the client.</span></span> <span data-ttu-id="3f9e9-106">A cadeia de caracteres do cliente deve conter a cadeia de caracteres “\<EOF>” para sinalizar o final da mensagem.</span><span class="sxs-lookup"><span data-stu-id="3f9e9-106">The string from the client must contain the string "\<EOF>" to signal the end of the message.</span></span>  
  
```vb  
Imports System  
Imports System.Net  
Imports System.Net.Sockets  
Imports System.Text  
Imports Microsoft.VisualBasic  
  
Public Class SynchronousSocketListener  
  
    ' Incoming data from the client.  
    Public Shared data As String = Nothing  
  
    Public Shared Sub Main()  
        ' Data buffer for incoming data.  
        Dim bytes() As Byte = New [Byte](1024) {}  
  
        ' Establish the local endpoint for the socket.  
        ' Dns.GetHostName returns the name of the   
        ' host running the application.  
        Dim ipHostInfo As IPHostEntry = Dns.Resolve(Dns.GetHostName())  
        Dim ipAddress As IPAddress = ipHostInfo.AddressList(0)  
        Dim localEndPoint As New IPEndPoint(ipAddress, 11000)  
  
        ' Create a TCP/IP socket.  
        Dim listener As New Socket(AddressFamily.InterNetwork, _  
            SocketType.Stream, ProtocolType.Tcp)  
  
        ' Bind the socket to the local endpoint and   
        ' listen for incoming connections.  
  
        listener.Bind(localEndPoint)  
        listener.Listen(10)  
  
        ' Start listening for connections.  
        While True  
            Console.WriteLine("Waiting for a connection...")  
            ' Program is suspended while waiting for an incoming connection.  
            Dim handler As Socket = listener.Accept()  
            data = Nothing  
  
            ' An incoming connection needs to be processed.  
            While True  
                bytes = New Byte(1024) {}  
                Dim bytesRec As Integer = handler.Receive(bytes)  
                data += Encoding.ASCII.GetString(bytes, 0, bytesRec)  
                If data.IndexOf("<EOF>") > -1 Then  
                    Exit While  
                End If  
            End While  
            ' Show the data on the console.  
            Console.WriteLine("Text received : {0}", data)  
            ' Echo the data back to the client.  
            Dim msg As Byte() = Encoding.ASCII.GetBytes(data)  
            handler.Send(msg)  
            handler.Shutdown(SocketShutdown.Both)  
            handler.Close()  
        End While  
    End Sub  
  
End Class 'SynchronousSocketListener  
```  
  
```csharp  
using System;  
using System.Net;  
using System.Net.Sockets;  
using System.Text;  
  
public class SynchronousSocketListener {  
  
    // Incoming data from the client.  
    public static string data = null;  
  
    public static void StartListening() {  
        // Data buffer for incoming data.  
        byte[] bytes = new Byte[1024];  
  
        // Establish the local endpoint for the socket.  
        // Dns.GetHostName returns the name of the   
        // host running the application.  
        IPHostEntry ipHostInfo = Dns.Resolve(Dns.GetHostName());  
        IPAddress ipAddress = ipHostInfo.AddressList[0];  
        IPEndPoint localEndPoint = new IPEndPoint(ipAddress, 11000);  
  
        // Create a TCP/IP socket.  
        Socket listener = new Socket(AddressFamily.InterNetwork,  
            SocketType.Stream, ProtocolType.Tcp );  
  
        // Bind the socket to the local endpoint and   
        // listen for incoming connections.  
        try {  
            listener.Bind(localEndPoint);  
            listener.Listen(10);  
  
            // Start listening for connections.  
            while (true) {  
                Console.WriteLine("Waiting for a connection...");  
                // Program is suspended while waiting for an incoming connection.  
                Socket handler = listener.Accept();  
                data = null;  
  
                // An incoming connection needs to be processed.  
                while (true) {  
                    bytes = new byte[1024];  
                    int bytesRec = handler.Receive(bytes);  
                    data += Encoding.ASCII.GetString(bytes,0,bytesRec);  
                    if (data.IndexOf("<EOF>") > -1) {  
                        break;  
                    }  
                }  
  
                // Show the data on the console.  
                Console.WriteLine( "Text received : {0}", data);  
  
                // Echo the data back to the client.  
                byte[] msg = Encoding.ASCII.GetBytes(data);  
  
                handler.Send(msg);  
                handler.Shutdown(SocketShutdown.Both);  
                handler.Close();  
            }  
  
        } catch (Exception e) {  
            Console.WriteLine(e.ToString());  
        }  
  
        Console.WriteLine("\nPress ENTER to continue...");  
        Console.Read();  
  
    }  
  
    public static int Main(String[] args) {  
        StartListening();  
        return 0;  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="3f9e9-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3f9e9-107">See Also</span></span>  
 <span data-ttu-id="3f9e9-108">[Exemplo de soquete de cliente síncrono](../../../docs/framework/network-programming/synchronous-client-socket-example.md) </span><span class="sxs-lookup"><span data-stu-id="3f9e9-108">[Synchronous Client Socket Example](../../../docs/framework/network-programming/synchronous-client-socket-example.md) </span></span>  
 <span data-ttu-id="3f9e9-109">[Usando um soquete de servidor síncrono](../../../docs/framework/network-programming/using-a-synchronous-server-socket.md) </span><span class="sxs-lookup"><span data-stu-id="3f9e9-109">[Using a Synchronous Server Socket](../../../docs/framework/network-programming/using-a-synchronous-server-socket.md) </span></span>  
 [<span data-ttu-id="3f9e9-110">Exemplos de código de soquete</span><span class="sxs-lookup"><span data-stu-id="3f9e9-110">Socket Code Examples</span></span>](../../../docs/framework/network-programming/socket-code-examples.md)

