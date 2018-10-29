---
title: Usando um soquete de cliente assíncrono
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application protocols, sockets
- sending data, sockets
- data requests, sockets
- asynchronous client sockets
- Socket class, asynchronous client sockets
- requesting data from Internet, sockets
- sockets, asynchronous client sockets
- receiving data, sockets
- protocols, sockets
- Internet, sockets
- client sockets
ms.assetid: fd85bc88-e06c-467d-a30d-9fd7cffcfca1
ms.openlocfilehash: 386b9d3cf0342784c09ed8fc7a815a242924b068
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50194950"
---
# <a name="using-an-asynchronous-client-socket"></a><span data-ttu-id="03eaa-102">Usando um soquete de cliente assíncrono</span><span class="sxs-lookup"><span data-stu-id="03eaa-102">Using an Asynchronous Client Socket</span></span>
<span data-ttu-id="03eaa-103">Um soquete de cliente assíncrono não suspende o aplicativo enquanto aguarda a conclusão das operações de rede.</span><span class="sxs-lookup"><span data-stu-id="03eaa-103">An asynchronous client socket does not suspend the application while waiting for network operations to complete.</span></span> <span data-ttu-id="03eaa-104">Em vez disso, ele usa o modelo padrão de programação assíncrona do .NET Framework para processar a conexão de rede em um thread, enquanto o aplicativo continua em execução no thread original.</span><span class="sxs-lookup"><span data-stu-id="03eaa-104">Instead, it uses the standard .NET Framework asynchronous programming model to process the network connection on one thread while the application continues to run on the original thread.</span></span> <span data-ttu-id="03eaa-105">Soquetes assíncronos são apropriados para aplicativos que fazem uso intenso da rede ou que não podem aguardar a conclusão das operações de rede antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="03eaa-105">Asynchronous sockets are appropriate for applications that make heavy use of the network or that cannot wait for network operations to complete before continuing.</span></span>  
  
 <span data-ttu-id="03eaa-106">A classe <xref:System.Net.Sockets.Socket> segue o padrão de nomenclatura do .NET Framework para métodos assíncronos; por exemplo, o método <xref:System.Net.Sockets.Socket.Receive%2A> síncrono corresponde aos métodos <xref:System.Net.Sockets.Socket.BeginReceive%2A> e <xref:System.Net.Sockets.Socket.EndReceive%2A> assíncronos.</span><span class="sxs-lookup"><span data-stu-id="03eaa-106">The <xref:System.Net.Sockets.Socket> class follows the .NET Framework naming pattern for asynchronous methods; for example, the synchronous <xref:System.Net.Sockets.Socket.Receive%2A> method corresponds to the asynchronous <xref:System.Net.Sockets.Socket.BeginReceive%2A> and <xref:System.Net.Sockets.Socket.EndReceive%2A> methods.</span></span>  
  
 <span data-ttu-id="03eaa-107">As operações assíncronas exigem um método de retorno de chamada para retornar o resultado da operação.</span><span class="sxs-lookup"><span data-stu-id="03eaa-107">Asynchronous operations require a callback method to return the result of the operation.</span></span> <span data-ttu-id="03eaa-108">Se o aplicativo não precisar saber o resultado, nenhum método de retorno de chamada será necessário.</span><span class="sxs-lookup"><span data-stu-id="03eaa-108">If your application does not need to know the result, then no callback method is required.</span></span> <span data-ttu-id="03eaa-109">O código de exemplo desta seção demonstra como usar um método para iniciar a conexão com um dispositivo de rede e um método de retorno de chamada para concluir a conexão, um método para iniciar o envio de dados e um método de retorno de chamada para concluir o envio, bem como um método para iniciar o recebimento de dados e um método de retorno de chamada para encerrar o recebimento de dados.</span><span class="sxs-lookup"><span data-stu-id="03eaa-109">The example code in this section demonstrates using a method to start connecting to a network device and a callback method to complete the connection, a method to start sending data and a callback method to complete the send, and a method to start receiving data and a callback method to end receiving data.</span></span>  
  
 <span data-ttu-id="03eaa-110">Os soquetes assíncronos usam vários threads do pool de threads do sistema para processar conexões de rede.</span><span class="sxs-lookup"><span data-stu-id="03eaa-110">Asynchronous sockets use multiple threads from the system thread pool to process network connections.</span></span> <span data-ttu-id="03eaa-111">Um thread é responsável por iniciar o envio ou recebimento de dados; outros threads concluem a conexão com o dispositivo de rede e enviam ou recebem dados.</span><span class="sxs-lookup"><span data-stu-id="03eaa-111">One thread is responsible for initiating the sending or receiving of data; other threads complete the connection to the network device and send or receive the data.</span></span> <span data-ttu-id="03eaa-112">Nos exemplos a seguir, instâncias da classe <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> são usadas para suspender a execução do thread principal e sinalizar quando a execução pode continuar.</span><span class="sxs-lookup"><span data-stu-id="03eaa-112">In the following examples, instances of the <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> class are used to suspend execution of the main thread and signal when execution can continue.</span></span>  
  
 <span data-ttu-id="03eaa-113">No exemplo a seguir, para conectar um soquete assíncrono com um dispositivo de rede, o método `Connect` inicializa um **Socket** e, em seguida, chama o método <xref:System.Net.Sockets.Socket.Connect%2A?displayProperty=nameWithType>, passando um ponto de extremidade remoto que representa o dispositivo de rede, o método de retorno de chamada de conexão e um objeto de estado, (o **Socket** de cliente), que é usado para passar informações de estado entre chamadas assíncronas.</span><span class="sxs-lookup"><span data-stu-id="03eaa-113">In the following example, to connect an asynchronous socket to a network device, the `Connect` method initializes a **Socket** and then calls the <xref:System.Net.Sockets.Socket.Connect%2A?displayProperty=nameWithType> method, passing a remote endpoint that represents the network device, the connect callback method, and a state object (the client **Socket**), which is used to pass state information between asynchronous calls.</span></span> <span data-ttu-id="03eaa-114">O exemplo implementa o método `Connect` para conectar o **Socket** especificado ao ponto de extremidade especificado.</span><span class="sxs-lookup"><span data-stu-id="03eaa-114">The example implements the `Connect` method to connect the specified **Socket** to the specified endpoint.</span></span> <span data-ttu-id="03eaa-115">Ele supõe que haja um **ManualResetEvent** global chamado `connectDone`.</span><span class="sxs-lookup"><span data-stu-id="03eaa-115">It assumes a global **ManualResetEvent** named `connectDone`.</span></span>  
  
```vb  
Public Shared Sub Connect(remoteEP As EndPoint, client As Socket)  
    client.BeginConnect(remoteEP, _  
       AddressOf ConnectCallback, client)  
  
    connectDone.WaitOne()  
End Sub 'Connect  
```  
  
```csharp  
public static void Connect(EndPoint remoteEP, Socket client) {  
    client.BeginConnect(remoteEP,   
        new AsyncCallback(ConnectCallback), client );  
  
   connectDone.WaitOne();  
}  
```  
  
 <span data-ttu-id="03eaa-116">O método de retorno de chamada de conexão `ConnectCallback` implementa o representante <xref:System.AsyncCallback>.</span><span class="sxs-lookup"><span data-stu-id="03eaa-116">The connect callback method `ConnectCallback` implements the <xref:System.AsyncCallback> delegate.</span></span> <span data-ttu-id="03eaa-117">Ele se conecta ao dispositivo remoto quando o dispositivo remoto está disponível e, em seguida, sinaliza ao thread de aplicativo que a conexão foi concluída definindo o **ManualResetEvent** como `connectDone`.</span><span class="sxs-lookup"><span data-stu-id="03eaa-117">It connects to the remote device when the remote device is available and then signals the application thread that the connection is complete by setting the **ManualResetEvent** `connectDone`.</span></span> <span data-ttu-id="03eaa-118">O código a seguir implementa o método `ConnectCallback`.</span><span class="sxs-lookup"><span data-stu-id="03eaa-118">The following code implements the `ConnectCallback` method.</span></span>  
  
```vb  
Private Shared Sub ConnectCallback(ar As IAsyncResult)  
    Try  
        ' Retrieve the socket from the state object.  
        Dim client As Socket = CType(ar.AsyncState, Socket)  
  
        ' Complete the connection.  
        client.EndConnect(ar)  
  
        Console.WriteLine("Socket connected to {0}", _  
            client.RemoteEndPoint.ToString())  
  
        ' Signal that the connection has been made.  
        connectDone.Set()  
    Catch e As Exception  
        Console.WriteLine(e.ToString())  
    End Try  
End Sub 'ConnectCallback  
```  
  
```csharp  
private static void ConnectCallback(IAsyncResult ar) {  
    try {  
        // Retrieve the socket from the state object.  
        Socket client = (Socket) ar.AsyncState;  
  
        // Complete the connection.  
        client.EndConnect(ar);  
  
        Console.WriteLine("Socket connected to {0}",  
            client.RemoteEndPoint.ToString());  
  
        // Signal that the connection has been made.  
        connectDone.Set();  
    } catch (Exception e) {  
        Console.WriteLine(e.ToString());  
    }  
}  
```  
  
 <span data-ttu-id="03eaa-119">O método de exemplo `Send` codifica os dados de cadeia de caracteres especificados no formato ASCII e envia-os de forma assíncrona para o dispositivo de rede representado pelo soquete especificado.</span><span class="sxs-lookup"><span data-stu-id="03eaa-119">The example method `Send` encodes the specified string data in ASCII format and sends it asynchronously to the network device represented by the specified socket.</span></span> <span data-ttu-id="03eaa-120">O exemplo a seguir implementa o método `Send`.</span><span class="sxs-lookup"><span data-stu-id="03eaa-120">The following example implements the `Send` method.</span></span>  
  
```vb  
Private Shared Sub Send(client As Socket, data As [String])  
    ' Convert the string data to byte data using ASCII encoding.  
    Dim byteData As Byte() = Encoding.ASCII.GetBytes(data)  
  
    ' Begin sending the data to the remote device.  
    client.BeginSend(byteData, 0, byteData.Length, SocketFlags.None, _  
        AddressOf SendCallback, client)  
End Sub 'Send  
```  
  
```csharp  
private static void Send(Socket client, String data) {  
    // Convert the string data to byte data using ASCII encoding.  
    byte[] byteData = Encoding.ASCII.GetBytes(data);  
  
    // Begin sending the data to the remote device.  
    client.BeginSend(byteData, 0, byteData.Length, SocketFlags.None,  
        new AsyncCallback(SendCallback), client);  
}  
```  
  
 <span data-ttu-id="03eaa-121">O método de retorno de chamada de envio `SendCallback` implementa o representante <xref:System.AsyncCallback>.</span><span class="sxs-lookup"><span data-stu-id="03eaa-121">The send callback method `SendCallback` implements the <xref:System.AsyncCallback> delegate.</span></span> <span data-ttu-id="03eaa-122">Ele envia os dados quando o dispositivo de rede está pronto para recebê-los.</span><span class="sxs-lookup"><span data-stu-id="03eaa-122">It sends the data when the network device is ready to receive.</span></span> <span data-ttu-id="03eaa-123">O exemplo a seguir mostra a implementação do método `SendCallback`.</span><span class="sxs-lookup"><span data-stu-id="03eaa-123">The following example shows the implementation of the `SendCallback` method.</span></span> <span data-ttu-id="03eaa-124">Ele supõe que haja um **ManualResetEvent** global chamado `sendDone`.</span><span class="sxs-lookup"><span data-stu-id="03eaa-124">It assumes a global **ManualResetEvent** named `sendDone`.</span></span>  
  
```vb  
Private Shared Sub SendCallback(ar As IAsyncResult)  
    Try  
        ' Retrieve the socket from the state object.  
        Dim client As Socket = CType(ar.AsyncState, Socket)  
  
        ' Complete sending the data to the remote device.  
        Dim bytesSent As Integer = client.EndSend(ar)  
        Console.WriteLine("Sent {0} bytes to server.", bytesSent)  
  
        ' Signal that all bytes have been sent.  
        sendDone.Set()  
    Catch e As Exception  
        Console.WriteLine(e.ToString())  
    End Try  
End Sub 'SendCallback  
```  
  
```csharp  
private static void SendCallback(IAsyncResult ar) {  
    try {  
        // Retrieve the socket from the state object.  
        Socket client = (Socket) ar.AsyncState;  
  
        // Complete sending the data to the remote device.  
        int bytesSent = client.EndSend(ar);  
        Console.WriteLine("Sent {0} bytes to server.", bytesSent);  
  
        // Signal that all bytes have been sent.  
        sendDone.Set();  
    } catch (Exception e) {  
        Console.WriteLine(e.ToString());  
    }  
}  
```  
  
 <span data-ttu-id="03eaa-125">A leitura de dados de um soquete de cliente exige um objeto de estado que passa valores entre chamadas assíncronas.</span><span class="sxs-lookup"><span data-stu-id="03eaa-125">Reading data from a client socket requires a state object that passes values between asynchronous calls.</span></span> <span data-ttu-id="03eaa-126">A classe a seguir é um objeto de estado de exemplo para recebimento dos dados de um soquete de cliente.</span><span class="sxs-lookup"><span data-stu-id="03eaa-126">The following class is an example state object for receiving data from a client socket.</span></span> <span data-ttu-id="03eaa-127">Ele contém um campo para o soquete de cliente, um buffer para os dados recebidos e um <xref:System.Text.StringBuilder> para conter a cadeia de caracteres de dados de entrada.</span><span class="sxs-lookup"><span data-stu-id="03eaa-127">It contains a field for the client socket, a buffer for the received data, and a <xref:System.Text.StringBuilder> to hold the incoming data string.</span></span> <span data-ttu-id="03eaa-128">A colocação desses campos no objeto de estado permite que seus valores sejam preservados em várias chamadas para a leitura de dados do soquete de cliente.</span><span class="sxs-lookup"><span data-stu-id="03eaa-128">Placing these fields in the state object allows their values to be preserved across multiple calls to read data from the client socket.</span></span>  
  
```vb  
Public Class StateObject  
    ' Client socket.  
    Public workSocket As Socket = Nothing   
    ' Size of receive buffer.  
    Public BufferSize As Integer = 256  
    ' Receive buffer.  
    Public buffer(256) As Byte   
    ' Received data string.  
    Public sb As New StringBuilder()  
End Class 'StateObject  
```  
  
```csharp  
public class StateObject {  
    // Client socket.  
    public Socket workSocket = null;  
    // Size of receive buffer.  
    public const int BufferSize = 256;  
    // Receive buffer.  
    public byte[] buffer = new byte[BufferSize];  
    // Received data string.  
    public StringBuilder sb = new StringBuilder();  
}  
```  
  
 <span data-ttu-id="03eaa-129">O método `Receive` de exemplo configura o objeto de estado e, em seguida, chama o método **BeginReceive** para ler os dados do soquete de cliente de forma assíncrona.</span><span class="sxs-lookup"><span data-stu-id="03eaa-129">The example `Receive` method sets up the state object and then calls the **BeginReceive** method to read the data from the client socket asynchronously.</span></span> <span data-ttu-id="03eaa-130">O exemplo a seguir implementa o método `Receive`.</span><span class="sxs-lookup"><span data-stu-id="03eaa-130">The following example implements the `Receive` method.</span></span>  
  
```vb  
Private Shared Sub Receive(client As Socket)  
    Try  
        ' Create the state object.  
        Dim state As New StateObject()  
        state.workSocket = client  
  
        ' Begin receiving the data from the remote device.  
        client.BeginReceive(state.buffer, 0, state.BufferSize, 0, _  
            AddressOf ReceiveCallback, state)  
    Catch e As Exception  
        Console.WriteLine(e.ToString())  
    End Try  
End Sub 'Receive  
```  
  
```csharp  
private static void Receive(Socket client) {  
    try {  
        // Create the state object.  
        StateObject state = new StateObject();  
        state.workSocket = client;  
  
        // Begin receiving the data from the remote device.  
        client.BeginReceive( state.buffer, 0, StateObject.BufferSize, 0,  
            new AsyncCallback(ReceiveCallback), state);  
    } catch (Exception e) {  
        Console.WriteLine(e.ToString());  
    }  
}  
```  
  
 <span data-ttu-id="03eaa-131">O método de retorno de chamada de recebimento `ReceiveCallback` implementa o representante **AsyncCallback**.</span><span class="sxs-lookup"><span data-stu-id="03eaa-131">The receive callback method `ReceiveCallback` implements the **AsyncCallback** delegate.</span></span> <span data-ttu-id="03eaa-132">Ele recebe os dados do dispositivo de rede e cria uma cadeia de caracteres de mensagem.</span><span class="sxs-lookup"><span data-stu-id="03eaa-132">It receives the data from the network device and builds a message string.</span></span> <span data-ttu-id="03eaa-133">Ele lê um ou mais bytes de dados da rede no buffer de dados e, em seguida, chama o método **BeginReceive** novamente até que os dados enviados pelo cliente estejam completos.</span><span class="sxs-lookup"><span data-stu-id="03eaa-133">It reads one or more bytes of data from the network into the data buffer and then calls the **BeginReceive** method again until the data sent by the client is complete.</span></span> <span data-ttu-id="03eaa-134">Depois que todos os dados são lidos do cliente, `ReceiveCallback` sinaliza ao thread de aplicativo que os dados estão completos definindo o **ManualResetEvent** como `sendDone`.</span><span class="sxs-lookup"><span data-stu-id="03eaa-134">Once all the data is read from the client, `ReceiveCallback` signals the application thread that the data is complete by setting the **ManualResetEvent** `sendDone`.</span></span>  
  
 <span data-ttu-id="03eaa-135">O exemplo de código a seguir implementa o método `ReceiveCallback`.</span><span class="sxs-lookup"><span data-stu-id="03eaa-135">The following example code implements the `ReceiveCallback` method.</span></span> <span data-ttu-id="03eaa-136">Ele supõe uma cadeia de caracteres global chamada `response` que contém a cadeia de caracteres recebida e um **ManualResetEvent** global chamado `receiveDone`.</span><span class="sxs-lookup"><span data-stu-id="03eaa-136">It assumes a global string named `response` that holds the received string and a global **ManualResetEvent** named `receiveDone`.</span></span> <span data-ttu-id="03eaa-137">O servidor deve desligar o soquete de cliente normalmente para encerrar a sessão de rede.</span><span class="sxs-lookup"><span data-stu-id="03eaa-137">The server must shut down the client socket gracefully to end the network session.</span></span>  
  
```vb  
Private Shared Sub ReceiveCallback(ar As IAsyncResult)  
    Try  
        ' Retrieve the state object and the client socket   
        ' from the asynchronous state object.  
        Dim state As StateObject = CType(ar.AsyncState, StateObject)  
        Dim client As Socket = state.workSocket  
  
        ' Read data from the remote device.  
        Dim bytesRead As Integer = client.EndReceive(ar)  
  
        If bytesRead > 0 Then  
            ' There might be more data, so store the data received so far.  
            state.sb.Append(Encoding.ASCII.GetString(state.buffer, 0, _  
                bytesRead))  
  
            '  Get the rest of the data.  
            client.BeginReceive(state.buffer, 0, state.BufferSize, 0, _  
                AddressOf ReceiveCallback, state)  
        Else  
            ' All the data has arrived; put it in response.  
            If state.sb.Length > 1 Then  
                response = state.sb.ToString()  
            End If  
            ' Signal that all bytes have been received.  
            receiveDone.Set()  
        End If  
    Catch e As Exception  
        Console.WriteLine(e.ToString())  
    End Try  
End Sub 'ReceiveCallback  
```  
  
```csharp  
private static void ReceiveCallback( IAsyncResult ar ) {  
    try {  
        // Retrieve the state object and the client socket   
        // from the asynchronous state object.  
        StateObject state = (StateObject) ar.AsyncState;  
        Socket client = state.workSocket;  
        // Read data from the remote device.  
        int bytesRead = client.EndReceive(ar);  
        if (bytesRead > 0) {  
            // There might be more data, so store the data received so far.  
            state.sb.Append(Encoding.ASCII.GetString(state.buffer,0,bytesRead));  
                //  Get the rest of the data.  
            client.BeginReceive(state.buffer,0,StateObject.BufferSize,0,  
                new AsyncCallback(ReceiveCallback), state);  
        } else {  
            // All the data has arrived; put it in response.  
            if (state.sb.Length > 1) {  
                response = state.sb.ToString();  
            }  
            // Signal that all bytes have been received.  
            receiveDone.Set();  
        }  
    } catch (Exception e) {  
        Console.WriteLine(e.ToString());  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="03eaa-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="03eaa-138">See Also</span></span>  
 [<span data-ttu-id="03eaa-139">Usando um soquete de cliente síncrono</span><span class="sxs-lookup"><span data-stu-id="03eaa-139">Using a Synchronous Client Socket</span></span>](../../../docs/framework/network-programming/using-a-synchronous-client-socket.md)  
 [<span data-ttu-id="03eaa-140">Escutando com soquetes</span><span class="sxs-lookup"><span data-stu-id="03eaa-140">Listening with Sockets</span></span>](../../../docs/framework/network-programming/listening-with-sockets.md)  
 [<span data-ttu-id="03eaa-141">Exemplo de soquete de cliente assíncrono</span><span class="sxs-lookup"><span data-stu-id="03eaa-141">Asynchronous Client Socket Example</span></span>](../../../docs/framework/network-programming/asynchronous-client-socket-example.md)
