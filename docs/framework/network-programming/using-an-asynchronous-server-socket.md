---
title: Usando um soquete de servidor assíncrono
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application protocols, sockets
- sending data, sockets
- Socket class, asynchronous server sockets
- data requests, sockets
- sockets, asynchronous server sockets
- requesting data from Internet, sockets
- server sockets
- receiving data, sockets
- asynchronous server sockets
- protocols, sockets
- Internet, sockets
ms.assetid: 813489a9-3efd-41b6-a33f-371d55397676
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: ad52291f5f5f40a65d2f9ec1c07bfb3a3f39fc01
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33396601"
---
# <a name="using-an-asynchronous-server-socket"></a><span data-ttu-id="7c7aa-102">Usando um soquete de servidor assíncrono</span><span class="sxs-lookup"><span data-stu-id="7c7aa-102">Using an Asynchronous Server Socket</span></span>
<span data-ttu-id="7c7aa-103">Os soquetes de servidor assíncrono usam o modelo de programação assíncrono do .NET Framework para processar solicitações de serviço da rede.</span><span class="sxs-lookup"><span data-stu-id="7c7aa-103">Asynchronous server sockets use the .NET Framework asynchronous programming model to process network service requests.</span></span> <span data-ttu-id="7c7aa-104">A classe <xref:System.Net.Sockets.Socket> segue o padrão de nomenclatura assíncrona do .NET Framework; por exemplo, o método <xref:System.Net.Sockets.Socket.Accept%2A> síncrono corresponde aos métodos <xref:System.Net.Sockets.Socket.BeginAccept%2A> e <xref:System.Net.Sockets.Socket.EndAccept%2A> assíncronos.</span><span class="sxs-lookup"><span data-stu-id="7c7aa-104">The <xref:System.Net.Sockets.Socket> class follows the standard .NET Framework asynchronous naming pattern; for example, the synchronous <xref:System.Net.Sockets.Socket.Accept%2A> method corresponds to the asynchronous <xref:System.Net.Sockets.Socket.BeginAccept%2A> and <xref:System.Net.Sockets.Socket.EndAccept%2A> methods.</span></span>  
  
 <span data-ttu-id="7c7aa-105">Um soquete de servidor assíncrono exige um método para começar a aceitar solicitações de conexão da rede, um método de retorno de chamada para manipular as solicitações de conexão e começar a receber dados da rede e um método de retorno de chamada para encerrar o recebimento dos dados.</span><span class="sxs-lookup"><span data-stu-id="7c7aa-105">An asynchronous server socket requires a method to begin accepting connection requests from the network, a callback method to handle the connection requests and begin receiving data from the network, and a callback method to end receiving the data.</span></span> <span data-ttu-id="7c7aa-106">Todos esses métodos são abordados mais diante nesta seção.</span><span class="sxs-lookup"><span data-stu-id="7c7aa-106">All these methods are discussed further in this section.</span></span>  
  
 <span data-ttu-id="7c7aa-107">No exemplo a seguir, para começar a aceitar solicitações de conexão da rede, o método `StartListening` inicializa o **Socket** e, em seguida, usa o método **BeginAccept** para começar a aceitar novas conexões.</span><span class="sxs-lookup"><span data-stu-id="7c7aa-107">In the following example, to begin accepting connection requests from the network, the method `StartListening` initializes the **Socket** and then uses the **BeginAccept** method to start accepting new connections.</span></span> <span data-ttu-id="7c7aa-108">O método de retorno de chamada de aceitação é chamado quando uma nova solicitação de conexão é recebida no soquete.</span><span class="sxs-lookup"><span data-stu-id="7c7aa-108">The accept callback method is called when a new connection request is received on the socket.</span></span> <span data-ttu-id="7c7aa-109">Ele é responsável por obter a instância **Socket** que manipulará a conexão e por entregar esse **Socket** ao thread que processará a solicitação.</span><span class="sxs-lookup"><span data-stu-id="7c7aa-109">It is responsible for getting the **Socket** instance that will handle the connection and handing that **Socket** off to the thread that will process the request.</span></span> <span data-ttu-id="7c7aa-110">O método de retorno de chamada de aceitação implementa o representante <xref:System.AsyncCallback>; ele retorna um nulo e usa um único parâmetro do tipo <xref:System.IAsyncResult>.</span><span class="sxs-lookup"><span data-stu-id="7c7aa-110">The accept callback method implements the <xref:System.AsyncCallback> delegate; it returns a void and takes a single parameter of type <xref:System.IAsyncResult>.</span></span> <span data-ttu-id="7c7aa-111">O exemplo a seguir é o shell de um método de retorno de chamada de aceitação.</span><span class="sxs-lookup"><span data-stu-id="7c7aa-111">The following example is the shell of an accept callback method.</span></span>  
  
```vb  
Sub acceptCallback(ar As IAsyncResult)  
    ' Add the callback code here.  
End Sub 'acceptCallback  
```  
  
```csharp  
void acceptCallback( IAsyncResult ar) {  
    // Add the callback code here.  
}  
```  
  
 <span data-ttu-id="7c7aa-112">O método **BeginAccept** usa dois parâmetros, um representante **AsyncCallback**, que aponta para o método de retorno de chamada de aceitação e um objeto, que é usado para passar informações de estado para o método de retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="7c7aa-112">The **BeginAccept** method takes two parameters, an **AsyncCallback** delegate that points to the accept callback method and an object that is used to pass state information to the callback method.</span></span> <span data-ttu-id="7c7aa-113">No exemplo a seguir, o **Socket** de escuta é passado para o método de retorno de chamada por meio do parâmetro *state*.</span><span class="sxs-lookup"><span data-stu-id="7c7aa-113">In the following example, the listening **Socket** is passed to the callback method through the *state* parameter.</span></span> <span data-ttu-id="7c7aa-114">Esse exemplo cria um representante **AsyncCallback** e começa a aceitar conexões da rede.</span><span class="sxs-lookup"><span data-stu-id="7c7aa-114">This example creates an **AsyncCallback** delegate and starts accepting connections from the network.</span></span>  
  
```vb  
listener.BeginAccept( _  
    New AsyncCallback(SocketListener.acceptCallback),_  
    listener)  
```  
  
```csharp  
listener.BeginAccept(  
    new AsyncCallback(SocketListener.acceptCallback),   
    listener);  
```  
  
 <span data-ttu-id="7c7aa-115">Os soquetes assíncronos usam threads do pool de threads do sistema para processar conexões de entrada.</span><span class="sxs-lookup"><span data-stu-id="7c7aa-115">Asynchronous sockets use threads from the system thread pool to process incoming connections.</span></span> <span data-ttu-id="7c7aa-116">Um thread é responsável por aceitar conexões, outro thread é usado para manipular cada conexão de entrada e outro thread é responsável por receber dados da conexão.</span><span class="sxs-lookup"><span data-stu-id="7c7aa-116">One thread is responsible for accepting connections, another thread is used to handle each incoming connection, and another thread is responsible for receiving data from the connection.</span></span> <span data-ttu-id="7c7aa-117">Eles podem ser o mesmo thread, dependendo de qual thread é atribuído pelo pool de threads.</span><span class="sxs-lookup"><span data-stu-id="7c7aa-117">These could be the same thread, depending on which thread is assigned by the thread pool.</span></span> <span data-ttu-id="7c7aa-118">No exemplo a seguir, a classe <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> suspende a execução do thread principal e sinaliza quando a execução pode continuar.</span><span class="sxs-lookup"><span data-stu-id="7c7aa-118">In the following example, the <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> class suspends execution of the main thread and signals when execution can continue.</span></span>  
  
 <span data-ttu-id="7c7aa-119">O exemplo a seguir mostra um método assíncrono que cria um soquete TCP/IP assíncrono no computador local e começa a aceitar conexões.</span><span class="sxs-lookup"><span data-stu-id="7c7aa-119">The following example shows an asynchronous method that creates an asynchronous TCP/IP socket on the local computer and begins accepting connections.</span></span> <span data-ttu-id="7c7aa-120">Ele supõe que haja um **ManualResetEvent** global chamado `allDone`, que o método seja um membro de uma classe chamada `SocketListener` e que um método de retorno de chamada chamado `acceptCallback` esteja definido.</span><span class="sxs-lookup"><span data-stu-id="7c7aa-120">It assumes that there is a global **ManualResetEvent** named `allDone`, that the method is a member of a class named `SocketListener`, and that a callback method named `acceptCallback` is defined.</span></span>  
  
```vb  
Public Sub StartListening()  
    Dim ipHostInfo As IPHostEntry = Dns.Resolve(Dns.GetHostName())  
    Dim localEP = New IPEndPoint(ipHostInfo.AddressList(0), 11000)  
  
    Console.WriteLine("Local address and port : {0}", localEP.ToString())  
  
    Dim listener As New Socket(localEP.Address.AddressFamily, _  
       SocketType.Stream, ProtocolType.Tcp)  
  
    Try  
        listener.Bind(localEP)  
        listener.Listen(10)  
  
        While True  
            allDone.Reset()  
  
            Console.WriteLine("Waiting for a connection...")  
            listener.BeginAccept(New _  
                AsyncCallback(SocketListener.acceptCallback), _  
                listener)  
  
            allDone.WaitOne()  
        End While  
    Catch e As Exception  
        Console.WriteLine(e.ToString())  
    End Try  
    Console.WriteLine("Closing the listener...")  
End Sub 'StartListening  
```  
  
```csharp  
public void StartListening() {  
    IPHostEntry ipHostInfo = Dns.Resolve(Dns.GetHostName());  
    IPEndPoint localEP = new IPEndPoint(ipHostInfo.AddressList[0],11000);  
  
    Console.WriteLine("Local address and port : {0}",localEP.ToString());  
  
    Socket listener = new Socket( localEP.Address.AddressFamily,  
        SocketType.Stream, ProtocolType.Tcp );  
  
    try {  
        listener.Bind(localEP);  
        listener.Listen(10);  
  
        while (true) {  
            allDone.Reset();  
  
            Console.WriteLine("Waiting for a connection...");  
            listener.BeginAccept(  
                new AsyncCallback(SocketListener.acceptCallback),   
                listener );  
  
            allDone.WaitOne();  
        }  
    } catch (Exception e) {  
        Console.WriteLine(e.ToString());  
    }  
  
    Console.WriteLine( "Closing the listener...");  
}  
```  
  
 <span data-ttu-id="7c7aa-121">O método de retorno de chamada de aceitação (`acceptCallback` no exemplo anterior) é responsável por sinalizar o thread principal do aplicativo para continuar o processamento, estabelecendo a conexão com o cliente e por iniciar a leitura assíncrona de dados do cliente.</span><span class="sxs-lookup"><span data-stu-id="7c7aa-121">The accept callback method (`acceptCallback` in the preceding example) is responsible for signaling the main application thread to continue processing, establishing the connection with the client, and starting the asynchronous read of data from the client.</span></span> <span data-ttu-id="7c7aa-122">O exemplo a seguir é a primeira parte de uma implementação do método `acceptCallback`.</span><span class="sxs-lookup"><span data-stu-id="7c7aa-122">The following example is the first part of an implementation of the `acceptCallback` method.</span></span> <span data-ttu-id="7c7aa-123">Esta seção do método sinaliza o thread principal do aplicativo para continuar o processamento e estabelece a conexão com o cliente.</span><span class="sxs-lookup"><span data-stu-id="7c7aa-123">This section of the method signals the main application thread to continue processing and establishes the connection to the client.</span></span> <span data-ttu-id="7c7aa-124">Ele supõe que haja um **ManualResetEvent** global chamado `allDone`.</span><span class="sxs-lookup"><span data-stu-id="7c7aa-124">It assumes a global **ManualResetEvent** named `allDone`.</span></span>  
  
```vb  
Public Sub acceptCallback(ar As IAsyncResult)  
    allDone.Set()  
  
    Dim listener As Socket = CType(ar.AsyncState, Socket)  
    Dim handler As Socket = listener.EndAccept(ar)  
  
    ' Additional code to read data goes here.  
End Sub 'acceptCallback  
```  
  
```csharp  
public void acceptCallback(IAsyncResult ar) {  
    allDone.Set();  
  
    Socket listener = (Socket) ar.AsyncState;  
    Socket handler = listener.EndAccept(ar);  
  
    // Additional code to read data goes here.    
}  
```  
  
 <span data-ttu-id="7c7aa-125">A leitura de dados de um soquete de cliente exige um objeto de estado que passa valores entre chamadas assíncronas.</span><span class="sxs-lookup"><span data-stu-id="7c7aa-125">Reading data from a client socket requires a state object that passes values between asynchronous calls.</span></span> <span data-ttu-id="7c7aa-126">O exemplo a seguir implementa um objeto de estado para o recebimento de uma cadeia de caracteres do cliente remoto.</span><span class="sxs-lookup"><span data-stu-id="7c7aa-126">The following example implements a state object for receiving a string from the remote client.</span></span> <span data-ttu-id="7c7aa-127">Ele contém campos para o soquete de cliente, um buffer de dados para o recebimento de dados e um <xref:System.Text.StringBuilder> para a criação da cadeia de caracteres de dados enviada pelo cliente.</span><span class="sxs-lookup"><span data-stu-id="7c7aa-127">It contains fields for the client socket, a data buffer for receiving data, and a <xref:System.Text.StringBuilder> for creating the data string sent by the client.</span></span> <span data-ttu-id="7c7aa-128">A colocação desses campos no objeto de estado permite que seus valores sejam preservados em várias chamadas para a leitura de dados do soquete de cliente.</span><span class="sxs-lookup"><span data-stu-id="7c7aa-128">Placing these fields in the state object allows their values to be preserved across multiple calls to read data from the client socket.</span></span>  
  
```vb  
Public Class StateObject  
    Public workSocket As Socket = Nothing  
    Public BufferSize As Integer = 1024  
    Public buffer(BufferSize) As Byte  
    Public sb As New StringBuilder()  
End Class 'StateObject  
```  
  
```csharp  
public class StateObject {  
    public Socket workSocket = null;  
    public const int BufferSize = 1024;  
    public byte[] buffer = new byte[BufferSize];  
    public StringBuilder sb = new StringBuilder();  
}  
```  
  
 <span data-ttu-id="7c7aa-129">A seção do método `acceptCallback` que começa a receber os dados do soquete de cliente primeiro inicializa uma instância da classe `StateObject` e, em seguida, chama o método <xref:System.Net.Sockets.Socket.BeginReceive%2A> para começar a ler os dados do soquete de cliente de forma assíncrona.</span><span class="sxs-lookup"><span data-stu-id="7c7aa-129">The section of the `acceptCallback` method that starts receiving the data from the client socket first initializes an instance of the `StateObject` class and then calls the <xref:System.Net.Sockets.Socket.BeginReceive%2A> method to start reading the data from the client socket asynchronously.</span></span>  
  
 <span data-ttu-id="7c7aa-130">O exemplo a seguir mostra todo o método `acceptCallback`.</span><span class="sxs-lookup"><span data-stu-id="7c7aa-130">The following example shows the complete `acceptCallback` method.</span></span> <span data-ttu-id="7c7aa-131">Ele supõe que haja um **ManualResetEvent** global chamado `allDone,`, que a classe `StateObject` esteja definida e que o método `readCallback` esteja definido em uma classe chamada `SocketListener`.</span><span class="sxs-lookup"><span data-stu-id="7c7aa-131">It assumes that there is a global **ManualResetEvent** named `allDone,` that the `StateObject` class is defined, and that the `readCallback` method is defined in a class named `SocketListener`.</span></span>  
  
```vb  
Public Shared Sub acceptCallback(ar As IAsyncResult)  
    ' Get the socket that handles the client request.  
    Dim listener As Socket = CType(ar.AsyncState, Socket)  
    Dim handler As Socket = listener.EndAccept(ar)  
  
    ' Signal the main thread to continue.  
    allDone.Set()  
  
    ' Create the state object.  
    Dim state As New StateObject()  
    state.workSocket = handler  
    handler.BeginReceive(state.buffer, 0, state.BufferSize, 0, _  
        AddressOf AsynchronousSocketListener.readCallback, state)  
End Sub 'acceptCallback  
```  
  
```csharp  
public static void acceptCallback(IAsyncResult ar) {  
    // Get the socket that handles the client request.  
    Socket listener = (Socket) ar.AsyncState;  
    Socket handler = listener.EndAccept(ar);  
  
    // Signal the main thread to continue.  
    allDone.Set();  
  
    // Create the state object.  
    StateObject state = new StateObject();  
    state.workSocket = handler;  
    handler.BeginReceive( state.buffer, 0, StateObject.BufferSize, 0,  
        new AsyncCallback(AsynchronousSocketListener.readCallback), state);  
}  
```  
  
 <span data-ttu-id="7c7aa-132">O método final que precisa ser implementado para o servidor de soquete assíncrono é o método de retorno de chamada de leitura que retorna os dados enviados pelo cliente.</span><span class="sxs-lookup"><span data-stu-id="7c7aa-132">The final method that needs to be implemented for the asynchronous socket server is the read callback method that returns the data sent by the client.</span></span> <span data-ttu-id="7c7aa-133">Assim como o método de retorno de chamada de aceitação, o método de retorno de chamada de leitura é um representante **AsyncCallback**.</span><span class="sxs-lookup"><span data-stu-id="7c7aa-133">Like the accept callback method, the read callback method is an **AsyncCallback** delegate.</span></span> <span data-ttu-id="7c7aa-134">Esse método lê um ou mais bytes do soquete do cliente no buffer de dados e, em seguida, chama o método **BeginReceive** novamente até que os dados enviados pelo cliente estejam completos.</span><span class="sxs-lookup"><span data-stu-id="7c7aa-134">This method reads one or more bytes from the client socket into the data buffer and then calls the **BeginReceive** method again until the data sent by the client is complete.</span></span> <span data-ttu-id="7c7aa-135">Depois que a mensagem inteira for lida do cliente, a cadeia de caracteres será exibida no console e o soquete de servidor que manipula a conexão com o cliente será fechado.</span><span class="sxs-lookup"><span data-stu-id="7c7aa-135">Once the entire message has been read from the client, the string is displayed on the console and the server socket handling the connection to the client is closed.</span></span>  
  
 <span data-ttu-id="7c7aa-136">A amostra a seguir implementa o método `readCallback`.</span><span class="sxs-lookup"><span data-stu-id="7c7aa-136">The following sample implements the `readCallback` method.</span></span> <span data-ttu-id="7c7aa-137">Ele supõe que a classe `StateObject` esteja definida.</span><span class="sxs-lookup"><span data-stu-id="7c7aa-137">It assumes that the `StateObject` class is defined.</span></span>  
  
```vb  
Public Shared Sub readCallback(ar As IAsyncResult)  
    Dim state As StateObject = CType(ar.AsyncState, StateObject)  
    Dim handler As Socket = state.workSocket  
  
    ' Read data from the client socket.   
    Dim read As Integer = handler.EndReceive(ar)  
  
    ' Data was read from the client socket.  
    If read > 0 Then  
        state.sb.Append(Encoding.ASCII.GetString(state.buffer, 0, read))  
        handler.BeginReceive(state.buffer, 0, state.BufferSize, 0, _  
            AddressOf readCallback, state)  
    Else  
        If state.sb.Length > 1 Then  
            ' All the data has been read from the client;  
            ' display it on the console.  
            Dim content As String = state.sb.ToString()  
            Console.WriteLine("Read {0} bytes from socket." + _  
                ControlChars.Cr + " Data : {1}", content.Length, content)  
        End If  
    End If  
End Sub 'readCallback  
```  
  
```csharp  
public static void readCallback(IAsyncResult ar) {  
    StateObject state = (StateObject) ar.AsyncState;  
    Socket handler = state.WorkSocket;  
  
    // Read data from the client socket.  
    int read = handler.EndReceive(ar);  
  
    // Data was read from the client socket.  
    if (read > 0) {  
        state.sb.Append(Encoding.ASCII.GetString(state.buffer,0,read));  
        handler.BeginReceive(state.buffer,0,StateObject.BufferSize, 0,  
            new AsyncCallback(readCallback), state);  
    } else {  
        if (state.sb.Length > 1) {  
            // All the data has been read from the client;  
            // display it on the console.  
            string content = state.sb.ToString();  
            Console.WriteLine("Read {0} bytes from socket.\n Data : {1}",  
               content.Length, content);  
        }  
        handler.Close();  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="7c7aa-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7c7aa-138">See Also</span></span>  
 [<span data-ttu-id="7c7aa-139">Usando um soquete de servidor síncrono</span><span class="sxs-lookup"><span data-stu-id="7c7aa-139">Using a Synchronous Server Socket</span></span>](../../../docs/framework/network-programming/using-a-synchronous-server-socket.md)  
 [<span data-ttu-id="7c7aa-140">Exemplo de soquete de servidor assíncrono</span><span class="sxs-lookup"><span data-stu-id="7c7aa-140">Asynchronous Server Socket Example</span></span>](../../../docs/framework/network-programming/asynchronous-server-socket-example.md)  
 [<span data-ttu-id="7c7aa-141">Threading</span><span class="sxs-lookup"><span data-stu-id="7c7aa-141">Threading</span></span>](../../../docs/standard/threading/index.md)  
 [<span data-ttu-id="7c7aa-142">Escutando com soquetes</span><span class="sxs-lookup"><span data-stu-id="7c7aa-142">Listening with Sockets</span></span>](../../../docs/framework/network-programming/listening-with-sockets.md)
