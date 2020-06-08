---
title: Usando um soquete de servidor assíncrono
description: Este exemplo mostra um soquete de servidor assíncrono. A classe Socket usa .NET Framework programação assíncrona para processar solicitações de serviço de rede.
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
ms.openlocfilehash: 8b85afb3ffdf69973eff37ccbb067b470ed44e3a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502022"
---
# <a name="using-an-asynchronous-server-socket"></a><span data-ttu-id="cc6ee-104">Usando um soquete de servidor assíncrono</span><span class="sxs-lookup"><span data-stu-id="cc6ee-104">Using an Asynchronous Server Socket</span></span>
<span data-ttu-id="cc6ee-105">Os soquetes de servidor assíncrono usam o modelo de programação assíncrono do .NET Framework para processar solicitações de serviço da rede.</span><span class="sxs-lookup"><span data-stu-id="cc6ee-105">Asynchronous server sockets use the .NET Framework asynchronous programming model to process network service requests.</span></span> <span data-ttu-id="cc6ee-106">A classe <xref:System.Net.Sockets.Socket> segue o padrão de nomenclatura assíncrona do .NET Framework; por exemplo, o método <xref:System.Net.Sockets.Socket.Accept%2A> síncrono corresponde aos métodos <xref:System.Net.Sockets.Socket.BeginAccept%2A> e <xref:System.Net.Sockets.Socket.EndAccept%2A> assíncronos.</span><span class="sxs-lookup"><span data-stu-id="cc6ee-106">The <xref:System.Net.Sockets.Socket> class follows the standard .NET Framework asynchronous naming pattern; for example, the synchronous <xref:System.Net.Sockets.Socket.Accept%2A> method corresponds to the asynchronous <xref:System.Net.Sockets.Socket.BeginAccept%2A> and <xref:System.Net.Sockets.Socket.EndAccept%2A> methods.</span></span>  
  
 <span data-ttu-id="cc6ee-107">Um soquete de servidor assíncrono exige um método para começar a aceitar solicitações de conexão da rede, um método de retorno de chamada para manipular as solicitações de conexão e começar a receber dados da rede e um método de retorno de chamada para encerrar o recebimento dos dados.</span><span class="sxs-lookup"><span data-stu-id="cc6ee-107">An asynchronous server socket requires a method to begin accepting connection requests from the network, a callback method to handle the connection requests and begin receiving data from the network, and a callback method to end receiving the data.</span></span> <span data-ttu-id="cc6ee-108">Todos esses métodos são abordados mais diante nesta seção.</span><span class="sxs-lookup"><span data-stu-id="cc6ee-108">All these methods are discussed further in this section.</span></span>  
  
 <span data-ttu-id="cc6ee-109">No exemplo a seguir, para começar a aceitar solicitações de conexão da rede, o método `StartListening` inicializa o **Socket** e, em seguida, usa o método **BeginAccept** para começar a aceitar novas conexões.</span><span class="sxs-lookup"><span data-stu-id="cc6ee-109">In the following example, to begin accepting connection requests from the network, the method `StartListening` initializes the **Socket** and then uses the **BeginAccept** method to start accepting new connections.</span></span> <span data-ttu-id="cc6ee-110">O método de retorno de chamada de aceitação é chamado quando uma nova solicitação de conexão é recebida no soquete.</span><span class="sxs-lookup"><span data-stu-id="cc6ee-110">The accept callback method is called when a new connection request is received on the socket.</span></span> <span data-ttu-id="cc6ee-111">Ele é responsável por obter a instância **Socket** que manipulará a conexão e por entregar esse **Socket** ao thread que processará a solicitação.</span><span class="sxs-lookup"><span data-stu-id="cc6ee-111">It is responsible for getting the **Socket** instance that will handle the connection and handing that **Socket** off to the thread that will process the request.</span></span> <span data-ttu-id="cc6ee-112">O método de retorno de chamada de aceitação implementa o representante <xref:System.AsyncCallback>; ele retorna um nulo e usa um único parâmetro do tipo <xref:System.IAsyncResult>.</span><span class="sxs-lookup"><span data-stu-id="cc6ee-112">The accept callback method implements the <xref:System.AsyncCallback> delegate; it returns a void and takes a single parameter of type <xref:System.IAsyncResult>.</span></span> <span data-ttu-id="cc6ee-113">O exemplo a seguir é o shell de um método de retorno de chamada de aceitação.</span><span class="sxs-lookup"><span data-stu-id="cc6ee-113">The following example is the shell of an accept callback method.</span></span>  
  
```vb  
Sub AcceptCallback(ar As IAsyncResult)  
    ' Add the callback code here.  
End Sub 'AcceptCallback  
```  
  
```csharp  
void AcceptCallback(IAsyncResult ar)
{  
    // Add the callback code here.  
}  
```  
  
 <span data-ttu-id="cc6ee-114">O método **BeginAccept** usa dois parâmetros, um representante **AsyncCallback**, que aponta para o método de retorno de chamada de aceitação e um objeto, que é usado para passar informações de estado para o método de retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="cc6ee-114">The **BeginAccept** method takes two parameters, an **AsyncCallback** delegate that points to the accept callback method and an object that is used to pass state information to the callback method.</span></span> <span data-ttu-id="cc6ee-115">No exemplo a seguir, o **Socket** de escuta é passado para o método de retorno de chamada por meio do parâmetro *state*.</span><span class="sxs-lookup"><span data-stu-id="cc6ee-115">In the following example, the listening **Socket** is passed to the callback method through the *state* parameter.</span></span> <span data-ttu-id="cc6ee-116">Esse exemplo cria um representante **AsyncCallback** e começa a aceitar conexões da rede.</span><span class="sxs-lookup"><span data-stu-id="cc6ee-116">This example creates an **AsyncCallback** delegate and starts accepting connections from the network.</span></span>  
  
```vb  
listener.BeginAccept( _  
    New AsyncCallback(SocketListener.AcceptCallback),_  
    listener)  
```  
  
```csharp  
listener.BeginAccept(new AsyncCallback(SocketListener.AcceptCallback), listener);  
```  
  
 <span data-ttu-id="cc6ee-117">Os soquetes assíncronos usam threads do pool de threads do sistema para processar conexões de entrada.</span><span class="sxs-lookup"><span data-stu-id="cc6ee-117">Asynchronous sockets use threads from the system thread pool to process incoming connections.</span></span> <span data-ttu-id="cc6ee-118">Um thread é responsável por aceitar conexões, outro thread é usado para manipular cada conexão de entrada e outro thread é responsável por receber dados da conexão.</span><span class="sxs-lookup"><span data-stu-id="cc6ee-118">One thread is responsible for accepting connections, another thread is used to handle each incoming connection, and another thread is responsible for receiving data from the connection.</span></span> <span data-ttu-id="cc6ee-119">Eles podem ser o mesmo thread, dependendo de qual thread é atribuído pelo pool de threads.</span><span class="sxs-lookup"><span data-stu-id="cc6ee-119">These could be the same thread, depending on which thread is assigned by the thread pool.</span></span> <span data-ttu-id="cc6ee-120">No exemplo a seguir, a classe <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> suspende a execução do thread principal e sinaliza quando a execução pode continuar.</span><span class="sxs-lookup"><span data-stu-id="cc6ee-120">In the following example, the <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> class suspends execution of the main thread and signals when execution can continue.</span></span>  
  
 <span data-ttu-id="cc6ee-121">O exemplo a seguir mostra um método assíncrono que cria um soquete TCP/IP assíncrono no computador local e começa a aceitar conexões.</span><span class="sxs-lookup"><span data-stu-id="cc6ee-121">The following example shows an asynchronous method that creates an asynchronous TCP/IP socket on the local computer and begins accepting connections.</span></span> <span data-ttu-id="cc6ee-122">Ele supõe que haja um **ManualResetEvent** global chamado `allDone`, que o método seja um membro de uma classe chamada `SocketListener` e que um método de retorno de chamada chamado `AcceptCallback` esteja definido.</span><span class="sxs-lookup"><span data-stu-id="cc6ee-122">It assumes that there is a global **ManualResetEvent** named `allDone`, that the method is a member of a class named `SocketListener`, and that a callback method named `AcceptCallback` is defined.</span></span>  
  
```vb  
Public Sub StartListening()  
    Dim ipHostInfo As IPHostEntry = Dns.Resolve(Dns.GetHostName())  
    Dim localEP = New IPEndPoint(ipHostInfo.AddressList(0), 11000)  
  
    Console.WriteLine($"Local address and port : {localEP.ToString()}")  
  
    Dim listener As New Socket(localEP.Address.AddressFamily, _  
       SocketType.Stream, ProtocolType.Tcp)  
  
    Try  
        listener.Bind(localEP)  
        listener.Listen(10)  
  
        While True  
            allDone.Reset()  
  
            Console.WriteLine("Waiting for a connection...")  
            listener.BeginAccept(New _  
                AsyncCallback(SocketListener.AcceptCallback), _  
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
public void StartListening()
{  
    IPHostEntry ipHostInfo = Dns.Resolve(Dns.GetHostName());  
    IPEndPoint localEP = new IPEndPoint(ipHostInfo.AddressList[0], 11000);  
  
    Console.WriteLine($"Local address and port : {localEP.ToString()}");  
  
    Socket listener = new Socket(localEP.Address.AddressFamily, SocketType.Stream, ProtocolType.Tcp);  
  
    try
    {  
        listener.Bind(localEP);  
        listener.Listen(10);  
  
        while (true)
        {  
            allDone.Reset();  
  
            Console.WriteLine("Waiting for a connection...");  
            listener.BeginAccept(new AsyncCallback(SocketListener.AcceptCallback), listener);  
  
            allDone.WaitOne();  
        }  
    }
    catch (Exception e)
    {  
        Console.WriteLine(e.ToString());  
    }  
  
    Console.WriteLine("Closing the listener...");  
}  
```  
  
 <span data-ttu-id="cc6ee-123">O método de retorno de chamada de aceitação (`AcceptCallback` no exemplo anterior) é responsável por sinalizar o thread principal do aplicativo para continuar o processamento, estabelecendo a conexão com o cliente e por iniciar a leitura assíncrona de dados do cliente.</span><span class="sxs-lookup"><span data-stu-id="cc6ee-123">The accept callback method (`AcceptCallback` in the preceding example) is responsible for signaling the main application thread to continue processing, establishing the connection with the client, and starting the asynchronous read of data from the client.</span></span> <span data-ttu-id="cc6ee-124">O exemplo a seguir é a primeira parte de uma implementação do método `AcceptCallback`.</span><span class="sxs-lookup"><span data-stu-id="cc6ee-124">The following example is the first part of an implementation of the `AcceptCallback` method.</span></span> <span data-ttu-id="cc6ee-125">Esta seção do método sinaliza o thread principal do aplicativo para continuar o processamento e estabelece a conexão com o cliente.</span><span class="sxs-lookup"><span data-stu-id="cc6ee-125">This section of the method signals the main application thread to continue processing and establishes the connection to the client.</span></span> <span data-ttu-id="cc6ee-126">Ele supõe que haja um **ManualResetEvent** global chamado `allDone`.</span><span class="sxs-lookup"><span data-stu-id="cc6ee-126">It assumes a global **ManualResetEvent** named `allDone`.</span></span>  
  
```vb  
Public Sub AcceptCallback(ar As IAsyncResult)  
    allDone.Set()  
  
    Dim listener As Socket = CType(ar.AsyncState, Socket)  
    Dim handler As Socket = listener.EndAccept(ar)  
  
    ' Additional code to read data goes here.  
End Sub 'AcceptCallback  
```  
  
```csharp  
public void AcceptCallback(IAsyncResult ar)
{  
    allDone.Set();  
  
    Socket listener = (Socket) ar.AsyncState;  
    Socket handler = listener.EndAccept(ar);  
  
    // Additional code to read data goes here.
}  
```  
  
 <span data-ttu-id="cc6ee-127">A leitura de dados de um soquete de cliente exige um objeto de estado que passa valores entre chamadas assíncronas.</span><span class="sxs-lookup"><span data-stu-id="cc6ee-127">Reading data from a client socket requires a state object that passes values between asynchronous calls.</span></span> <span data-ttu-id="cc6ee-128">O exemplo a seguir implementa um objeto de estado para o recebimento de uma cadeia de caracteres do cliente remoto.</span><span class="sxs-lookup"><span data-stu-id="cc6ee-128">The following example implements a state object for receiving a string from the remote client.</span></span> <span data-ttu-id="cc6ee-129">Ele contém campos para o soquete de cliente, um buffer de dados para o recebimento de dados e um <xref:System.Text.StringBuilder> para a criação da cadeia de caracteres de dados enviada pelo cliente.</span><span class="sxs-lookup"><span data-stu-id="cc6ee-129">It contains fields for the client socket, a data buffer for receiving data, and a <xref:System.Text.StringBuilder> for creating the data string sent by the client.</span></span> <span data-ttu-id="cc6ee-130">A colocação desses campos no objeto de estado permite que seus valores sejam preservados em várias chamadas para a leitura de dados do soquete de cliente.</span><span class="sxs-lookup"><span data-stu-id="cc6ee-130">Placing these fields in the state object allows their values to be preserved across multiple calls to read data from the client socket.</span></span>  
  
```vb  
Public Class StateObject  
    Public workSocket As Socket = Nothing  
    Public BufferSize As Integer = 1024  
    Public buffer(BufferSize) As Byte  
    Public sb As New StringBuilder()  
End Class 'StateObject  
```  
  
```csharp  
public class StateObject
{  
    public Socket workSocket = null;  
    public const int BufferSize = 1024;  
    public byte[] buffer = new byte[BufferSize];  
    public StringBuilder sb = new StringBuilder();  
}  
```  
  
 <span data-ttu-id="cc6ee-131">A seção do método `AcceptCallback` que começa a receber os dados do soquete de cliente primeiro inicializa uma instância da classe `StateObject` e, em seguida, chama o método <xref:System.Net.Sockets.Socket.BeginReceive%2A> para começar a ler os dados do soquete de cliente de forma assíncrona.</span><span class="sxs-lookup"><span data-stu-id="cc6ee-131">The section of the `AcceptCallback` method that starts receiving the data from the client socket first initializes an instance of the `StateObject` class and then calls the <xref:System.Net.Sockets.Socket.BeginReceive%2A> method to start reading the data from the client socket asynchronously.</span></span>  
  
 <span data-ttu-id="cc6ee-132">O exemplo a seguir mostra todo o método `AcceptCallback`.</span><span class="sxs-lookup"><span data-stu-id="cc6ee-132">The following example shows the complete `AcceptCallback` method.</span></span> <span data-ttu-id="cc6ee-133">Ele supõe que haja um **ManualResetEvent** global chamado `allDone,`, que a classe `StateObject` esteja definida e que o método `ReadCallback` esteja definido em uma classe chamada `SocketListener`.</span><span class="sxs-lookup"><span data-stu-id="cc6ee-133">It assumes that there is a global **ManualResetEvent** named `allDone,` that the `StateObject` class is defined, and that the `ReadCallback` method is defined in a class named `SocketListener`.</span></span>  
  
```vb  
Public Shared Sub AcceptCallback(ar As IAsyncResult)  
    ' Get the socket that handles the client request.  
    Dim listener As Socket = CType(ar.AsyncState, Socket)  
    Dim handler As Socket = listener.EndAccept(ar)  
  
    ' Signal the main thread to continue.  
    allDone.Set()  
  
    ' Create the state object.  
    Dim state As New StateObject()  
    state.workSocket = handler  
    handler.BeginReceive(state.buffer, 0, state.BufferSize, 0, _  
        AddressOf AsynchronousSocketListener.ReadCallback, state)  
End Sub 'AcceptCallback  
```  
  
```csharp  
public static void AcceptCallback(IAsyncResult ar)
{  
    // Get the socket that handles the client request.  
    Socket listener = (Socket) ar.AsyncState;  
    Socket handler = listener.EndAccept(ar);  
  
    // Signal the main thread to continue.  
    allDone.Set();  
  
    // Create the state object.  
    StateObject state = new StateObject();  
    state.workSocket = handler;  
    handler.BeginReceive(state.buffer, 0, StateObject.BufferSize, 0,  
        new AsyncCallback(AsynchronousSocketListener.ReadCallback), state);  
}  
```  
  
 <span data-ttu-id="cc6ee-134">O método final que precisa ser implementado para o servidor de soquete assíncrono é o método de retorno de chamada de leitura que retorna os dados enviados pelo cliente.</span><span class="sxs-lookup"><span data-stu-id="cc6ee-134">The final method that needs to be implemented for the asynchronous socket server is the read callback method that returns the data sent by the client.</span></span> <span data-ttu-id="cc6ee-135">Assim como o método de retorno de chamada de aceitação, o método de retorno de chamada de leitura é um representante **AsyncCallback**.</span><span class="sxs-lookup"><span data-stu-id="cc6ee-135">Like the accept callback method, the read callback method is an **AsyncCallback** delegate.</span></span> <span data-ttu-id="cc6ee-136">Esse método lê um ou mais bytes do soquete do cliente no buffer de dados e, em seguida, chama o método **BeginReceive** novamente até que os dados enviados pelo cliente estejam completos.</span><span class="sxs-lookup"><span data-stu-id="cc6ee-136">This method reads one or more bytes from the client socket into the data buffer and then calls the **BeginReceive** method again until the data sent by the client is complete.</span></span> <span data-ttu-id="cc6ee-137">Depois que a mensagem inteira for lida do cliente, a cadeia de caracteres será exibida no console e o soquete de servidor que manipula a conexão com o cliente será fechado.</span><span class="sxs-lookup"><span data-stu-id="cc6ee-137">Once the entire message has been read from the client, the string is displayed on the console and the server socket handling the connection to the client is closed.</span></span>  
  
 <span data-ttu-id="cc6ee-138">A amostra a seguir implementa o método `ReadCallback`.</span><span class="sxs-lookup"><span data-stu-id="cc6ee-138">The following sample implements the `ReadCallback` method.</span></span> <span data-ttu-id="cc6ee-139">Ele supõe que a classe `StateObject` esteja definida.</span><span class="sxs-lookup"><span data-stu-id="cc6ee-139">It assumes that the `StateObject` class is defined.</span></span>  
  
```vb  
Public Shared Sub ReadCallback(ar As IAsyncResult)  
    Dim state As StateObject = CType(ar.AsyncState, StateObject)  
    Dim handler As Socket = state.workSocket  
  
    ' Read data from the client socket.
    Dim read As Integer = handler.EndReceive(ar)  
  
    ' Data was read from the client socket.  
    If read > 0 Then  
        state.sb.Append(Encoding.ASCII.GetString(state.buffer, 0, read))  
        handler.BeginReceive(state.buffer, 0, state.BufferSize, 0, _  
            AddressOf ReadCallback, state)  
    Else  
        If state.sb.Length > 1 Then  
            ' All the data has been read from the client;  
            ' display it on the console.  
            Dim content As String = state.sb.ToString()  
            Console.WriteLine($"Read {content.Length} bytes from socket. {ControlChars.Cr} Data : {content}")  
        End If  
    End If  
End Sub 'ReadCallback  
```  
  
```csharp  
public static void ReadCallback(IAsyncResult ar)
{  
    StateObject state = (StateObject) ar.AsyncState;  
    Socket handler = state.WorkSocket;  
  
    // Read data from the client socket.  
    int read = handler.EndReceive(ar);  
  
    // Data was read from the client socket.  
    if (read > 0)
    {  
        state.sb.Append(Encoding.ASCII.GetString(state.buffer,0,read));  
        handler.BeginReceive(state.buffer, 0, StateObject.BufferSize, 0,  
            new AsyncCallback(ReadCallback), state);  
    }
    else
    {  
        if (state.sb.Length > 1)
        {  
            // All the data has been read from the client;  
            // display it on the console.  
            string content = state.sb.ToString();  
            Console.WriteLine($"Read {content.Length} bytes from socket.\n Data : {content}");
        }  
        handler.Close();  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="cc6ee-140">Confira também</span><span class="sxs-lookup"><span data-stu-id="cc6ee-140">See also</span></span>

- [<span data-ttu-id="cc6ee-141">Usando um soquete de servidor síncrono</span><span class="sxs-lookup"><span data-stu-id="cc6ee-141">Using a Synchronous Server Socket</span></span>](using-a-synchronous-server-socket.md)
- [<span data-ttu-id="cc6ee-142">Exemplo de soquete de servidor assíncrono</span><span class="sxs-lookup"><span data-stu-id="cc6ee-142">Asynchronous Server Socket Example</span></span>](asynchronous-server-socket-example.md)
- [<span data-ttu-id="cc6ee-143">Threading</span><span class="sxs-lookup"><span data-stu-id="cc6ee-143">Threading</span></span>](../../standard/threading/index.md)
- [<span data-ttu-id="cc6ee-144">Escutando com soquetes</span><span class="sxs-lookup"><span data-stu-id="cc6ee-144">Listening with Sockets</span></span>](listening-with-sockets.md)
