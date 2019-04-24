---
title: Usando os serviços TCP
ms.date: 03/30/2017
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
ms.openlocfilehash: d9b3c9975c4d10649bdecd6f63cf362a2b2a2738
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2019
ms.locfileid: "59611946"
---
# <a name="using-tcp-services"></a>Usando os serviços TCP

A classe <xref:System.Net.Sockets.TcpClient> solicita dados de um recurso da Internet usando o TCP. Os métodos e as propriedades de **TcpClient** abstraem os detalhes para criar um <xref:System.Net.Sockets.Socket> para solicitar e receber dados usando o TCP. Como a conexão com o dispositivo remoto é representada como um fluxo, os dados podem ser lidos e gravados com técnicas de manipulação de fluxo do .NET Framework.  
  
 O protocolo TCP estabelece uma conexão com um ponto de extremidade remoto e, em seguida, usa essa conexão para enviar e receber pacotes de dados. O TCP é responsável por garantir que os pacotes de dados são enviados para o ponto de extremidade e montados na ordem correta quando chegarem.  
  
 Para estabelecer uma conexão TCP, você deve saber o endereço do dispositivo de rede que hospeda o serviço necessário e saber a porta TCP usada pelo serviço para se comunicar. A IANA (Internet Assigned Numbers Authority) define os números da porta de serviços comuns (veja [Registro de número da porta do protocolo de transporte e nome de serviço](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml)). Os serviços que não estão na lista da IANA podem ter números de porta no intervalo de 1.024 a 65.535.  
  
 O exemplo a seguir demonstra a configuração de um **TcpClient** para se conectar a um servidor de horário na porta TCP 13.  
  
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
  
 <xref:System.Net.Sockets.TcpListener> é usado para monitorar uma porta TCP para solicitações de entrada e, em seguida, criar um **Socket** ou um **TcpClient** que gerencia a conexão com o cliente. O método <xref:System.Net.Sockets.TcpListener.Start%2A> habilita a escuta e o método <xref:System.Net.Sockets.TcpListener.Stop%2A> desabilita a escuta na porta. O método <xref:System.Net.Sockets.TcpListener.AcceptTcpClient%2A> aceita solicitações de conexão de entrada e cria um **TcpClient** para manipular a solicitação e o método <xref:System.Net.Sockets.TcpListener.AcceptSocket%2A> aceita solicitações de conexão de entrada e cria um **Socket** para manipular a solicitação.  
  
 O exemplo a seguir demonstra como criar um servidor de horário da rede usando um **TcpListener** para monitorar a porta TCP 13. Quando uma solicitação de conexão de entrada é aceita, o servidor de horário responde com a data e hora atuais do servidor host.  
  
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
