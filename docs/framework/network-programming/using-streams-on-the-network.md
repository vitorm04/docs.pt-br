---
title: Usando fluxos na rede
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- requesting data from Internet, streams
- Networking
- response to Internet request, streams
- network resources, stream capabilities
- receiving data, stream capabilities
- Network Resources
- sending data, stream capabilities
- downloading Internet resources, streams
- streams, capabilities
- Internet, streams
- streams
ms.assetid: 02b05fba-7235-45ce-94e5-060436ee0875
ms.openlocfilehash: aa3fc56dc461d4fe22e2ff391f3561d8834128d8
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71046870"
---
# <a name="using-streams-on-the-network"></a><span data-ttu-id="b98c4-102">Usando fluxos na rede</span><span class="sxs-lookup"><span data-stu-id="b98c4-102">Using Streams on the Network</span></span>
<span data-ttu-id="b98c4-103">Os recursos de rede são representados no .NET Framework como fluxos.</span><span class="sxs-lookup"><span data-stu-id="b98c4-103">Network resources are represented in the .NET Framework as streams.</span></span> <span data-ttu-id="b98c4-104">Tratando os fluxos de forma genérica, o .NET Framework oferece as seguintes funcionalidades:</span><span class="sxs-lookup"><span data-stu-id="b98c4-104">By treating streams generically, the .NET Framework offers the following capabilities:</span></span>  
  
- <span data-ttu-id="b98c4-105">Uma maneira comum de enviar e receber dados da Web.</span><span class="sxs-lookup"><span data-stu-id="b98c4-105">A common way to send and receive Web data.</span></span> <span data-ttu-id="b98c4-106">Seja qual for o conteúdo real do arquivo – HTML, XML ou qualquer outra coisa –, o aplicativo usará <xref:System.IO.Stream.Write%2A?displayProperty=nameWithType> e <xref:System.IO.Stream.Read%2A?displayProperty=nameWithType> para enviar e receber dados.</span><span class="sxs-lookup"><span data-stu-id="b98c4-106">Whatever the actual contents of the file — HTML, XML, or anything else — your application will use <xref:System.IO.Stream.Write%2A?displayProperty=nameWithType> and <xref:System.IO.Stream.Read%2A?displayProperty=nameWithType> to send and receive data.</span></span>  
  
- <span data-ttu-id="b98c4-107">Compatibilidade com fluxos no .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b98c4-107">Compatibility with streams across the .NET Framework.</span></span> <span data-ttu-id="b98c4-108">Os fluxos são usados em todo o .NET Framework, que tem uma infraestrutura avançada para manipulá-los.</span><span class="sxs-lookup"><span data-stu-id="b98c4-108">Streams are used throughout the .NET Framework, which has a rich infrastructure for handling them.</span></span> <span data-ttu-id="b98c4-109">Por exemplo, é possível modificar um aplicativo que lê dados XML de um <xref:System.IO.FileStream> para ler dados de um <xref:System.Net.Sockets.NetworkStream> alterando apenas as poucas linhas de código que inicializam o fluxo.</span><span class="sxs-lookup"><span data-stu-id="b98c4-109">For example, you can modify an application that reads XML data from a <xref:System.IO.FileStream> to read data from a <xref:System.Net.Sockets.NetworkStream> instead by changing only the few lines of code that initialize the stream.</span></span> <span data-ttu-id="b98c4-110">As principais diferenças entre a classe **NetworkStream** e outros fluxos são que **NetworkStream** não é pesquisável, a propriedade <xref:System.Net.Sockets.NetworkStream.CanSeek%2A> sempre retorna **false** e os métodos <xref:System.Net.Sockets.NetworkStream.Seek%2A> e <xref:System.Net.Sockets.NetworkStream.Position%2A> geram uma <xref:System.NotSupportedException>.</span><span class="sxs-lookup"><span data-stu-id="b98c4-110">The major differences between the **NetworkStream** class and other streams are that **NetworkStream** is not seekable, the <xref:System.Net.Sockets.NetworkStream.CanSeek%2A> property always returns **false**, and the <xref:System.Net.Sockets.NetworkStream.Seek%2A> and <xref:System.Net.Sockets.NetworkStream.Position%2A> methods throw a <xref:System.NotSupportedException>.</span></span>  
  
- <span data-ttu-id="b98c4-111">Processamento de dados conforme eles são recebidos.</span><span class="sxs-lookup"><span data-stu-id="b98c4-111">Processing of data as it arrives.</span></span> <span data-ttu-id="b98c4-112">Os fluxos fornecem acesso aos dados conforme eles são recebidos da rede, em vez de forçar o aplicativo a aguardar que um conjunto de dados inteiro seja baixado.</span><span class="sxs-lookup"><span data-stu-id="b98c4-112">Streams provide access to data as it arrives from the network, rather than forcing your application to wait for an entire data set to be downloaded.</span></span>  
  
 <span data-ttu-id="b98c4-113">O namespace <xref:System.Net.Sockets> contém uma classe **NetworkStream** que implementa a classe <xref:System.IO.Stream> especificamente para uso com recursos de rede.</span><span class="sxs-lookup"><span data-stu-id="b98c4-113">The <xref:System.Net.Sockets> namespace contains a **NetworkStream** class that implements the <xref:System.IO.Stream> class specifically for use with network resources.</span></span> <span data-ttu-id="b98c4-114">As classes do namespace <xref:System.Net.Sockets> usam a classe **NetworkStream** para representar fluxos.</span><span class="sxs-lookup"><span data-stu-id="b98c4-114">Classes in the <xref:System.Net.Sockets> namespace use the **NetworkStream** class to represent streams.</span></span>  
  
 <span data-ttu-id="b98c4-115">Para enviar dados para a rede usando o fluxo retornado, chame <xref:System.Net.WebRequest.GetRequestStream%2A> na <xref:System.Net.WebRequest>.</span><span class="sxs-lookup"><span data-stu-id="b98c4-115">To send data to the network using the returned stream, call <xref:System.Net.WebRequest.GetRequestStream%2A> on your <xref:System.Net.WebRequest>.</span></span> <span data-ttu-id="b98c4-116">A **WebRequest** enviará cabeçalhos de solicitação para o servidor; em seguida, você poderá enviar dados para o recurso de rede chamando o método <xref:System.IO.Stream.BeginWrite%2A>, <xref:System.IO.Stream.EndWrite%2A> ou <xref:System.IO.Stream.Write%2A> no fluxo retornado.</span><span class="sxs-lookup"><span data-stu-id="b98c4-116">The **WebRequest** will send request headers to the server; then you can send data to the network resource by calling the <xref:System.IO.Stream.BeginWrite%2A>, <xref:System.IO.Stream.EndWrite%2A>, or <xref:System.IO.Stream.Write%2A> method on the returned stream.</span></span> <span data-ttu-id="b98c4-117">Alguns protocolos, como HTTP, podem exigir a definição de propriedades específicas ao protocolo antes de enviar dados.</span><span class="sxs-lookup"><span data-stu-id="b98c4-117">Some protocols, such as HTTP, may require you to set protocol-specific properties before sending data.</span></span> <span data-ttu-id="b98c4-118">O exemplo de código a seguir mostra como definir propriedades específicas de HTTP para envio de dados.</span><span class="sxs-lookup"><span data-stu-id="b98c4-118">The following code example shows how to set HTTP-specific properties for sending data.</span></span> <span data-ttu-id="b98c4-119">Ele supõe que a variável `sendData` contém os dados a serem enviados e que a variável `sendLength` é o número de bytes de dados a serem enviados.</span><span class="sxs-lookup"><span data-stu-id="b98c4-119">It assumes that the variable `sendData` contains the data to send and that the variable `sendLength` is the number of bytes of data to send.</span></span>  
  
```csharp  
HttpWebRequest request =   
   (HttpWebRequest) WebRequest.Create("http://www.contoso.com/");  
request.Method = "POST";  
request.ContentLength = sendLength;  
try  
{  
   Stream sendStream = request.GetRequestStream();  
   sendStream.Write(sendData,0,sendLength);  
   sendStream.Close();  
}  
catch  
{  
   // Handle errors . . .  
}  
```  
  
```vb  
Dim request As HttpWebRequest = _  
   CType(WebRequest.Create("http://www.contoso.com/"), HttpWebRequest)  
request.Method = "POST"  
request.ContentLength = sendLength  
Try  
   Dim sendStream As Stream = request.GetRequestStream()  
   sendStream.Write(sendData, 0, sendLength)  
   sendStream.Close()  
Catch  
   ' Handle errors . . .  
End Try  
```  
  
 <span data-ttu-id="b98c4-120">Para receber dados da rede, chame <xref:System.Net.WebResponse.GetResponseStream%2A> na <xref:System.Net.WebResponse>.</span><span class="sxs-lookup"><span data-stu-id="b98c4-120">To receive data from the network, call <xref:System.Net.WebResponse.GetResponseStream%2A> on your <xref:System.Net.WebResponse>.</span></span> <span data-ttu-id="b98c4-121">Em seguida, você poderá ler dados do recurso de rede chamando o método <xref:System.IO.Stream.BeginRead%2A>, <xref:System.IO.Stream.EndRead%2A> ou <xref:System.IO.Stream.Read%2A> no fluxo retornado.</span><span class="sxs-lookup"><span data-stu-id="b98c4-121">You can then read data from the network resource by calling the <xref:System.IO.Stream.BeginRead%2A>, <xref:System.IO.Stream.EndRead%2A>, or <xref:System.IO.Stream.Read%2A> method on the returned stream.</span></span>  
  
 <span data-ttu-id="b98c4-122">Ao usar fluxos em recursos de rede, tenha em mente os seguintes pontos:</span><span class="sxs-lookup"><span data-stu-id="b98c4-122">When using streams from network resources, keep in mind the following points:</span></span>  
  
- <span data-ttu-id="b98c4-123">A propriedade **CanSeek** sempre retorna **false**, pois a classe **NetworkStream** não pode mudar de posição no fluxo.</span><span class="sxs-lookup"><span data-stu-id="b98c4-123">The **CanSeek** property always returns **false** since the **NetworkStream** class cannot change position in the stream.</span></span> <span data-ttu-id="b98c4-124">Os métodos **Seek** e **Position** geram uma **NotSupportedException**.</span><span class="sxs-lookup"><span data-stu-id="b98c4-124">The **Seek** and **Position** methods throw a **NotSupportedException**.</span></span>  
  
- <span data-ttu-id="b98c4-125">Quando você usa **WebRequest** e **WebResponse**, as instâncias de fluxo criadas com a chamada a **GetResponseStream** são somente leitura e as instâncias de fluxo criadas com a chamada a **GetRequestStream** são somente gravação.</span><span class="sxs-lookup"><span data-stu-id="b98c4-125">When you use **WebRequest** and **WebResponse**, stream instances created by calling **GetResponseStream** are read-only and stream instances created by calling **GetRequestStream** are write-only.</span></span>  
  
- <span data-ttu-id="b98c4-126">Use a classe <xref:System.IO.StreamReader> para facilitar a codificação.</span><span class="sxs-lookup"><span data-stu-id="b98c4-126">Use the <xref:System.IO.StreamReader> class to make encoding easier.</span></span> <span data-ttu-id="b98c4-127">O exemplo de código a seguir usa um **StreamReader** para ler um fluxo codificado em ASCII de uma **WebResponse** (o exemplo não mostra a criação da solicitação).</span><span class="sxs-lookup"><span data-stu-id="b98c4-127">The following code example uses a **StreamReader** to read an ASCII-encoded stream from a **WebResponse** (the example does not show creating the request).</span></span>  
  
- <span data-ttu-id="b98c4-128">A chamada a **GetResponse** poderá ser bloqueada se os recursos de rede não estiverem disponíveis.</span><span class="sxs-lookup"><span data-stu-id="b98c4-128">The call to **GetResponse** can block if network resources are not available.</span></span> <span data-ttu-id="b98c4-129">Considere o uso de uma solicitação assíncrona com os métodos <xref:System.Net.WebRequest.BeginGetResponse%2A> e <xref:System.Net.WebRequest.EndGetResponse%2A>.</span><span class="sxs-lookup"><span data-stu-id="b98c4-129">You should consider using an asynchronous request with the <xref:System.Net.WebRequest.BeginGetResponse%2A> and <xref:System.Net.WebRequest.EndGetResponse%2A> methods.</span></span>  
  
- <span data-ttu-id="b98c4-130">A chamada a **GetRequestStream** pode ser bloqueada enquanto a conexão com o servidor é criada.</span><span class="sxs-lookup"><span data-stu-id="b98c4-130">The call to **GetRequestStream** can block while the connection to the server is created.</span></span> <span data-ttu-id="b98c4-131">Considere o uso de uma solicitação assíncrona para o fluxo com os métodos <xref:System.Net.WebRequest.BeginGetRequestStream%2A> e <xref:System.Net.WebRequest.EndGetRequestStream%2A>.</span><span class="sxs-lookup"><span data-stu-id="b98c4-131">You should consider using an asynchronous request for the stream with the <xref:System.Net.WebRequest.BeginGetRequestStream%2A> and <xref:System.Net.WebRequest.EndGetRequestStream%2A> methods.</span></span>  
  
```csharp  
// Create a response object.  
WebResponse response = request.GetResponse();  
// Get a readable stream from the server.  
StreamReader sr =   
   new StreamReader(response.GetResponseStream(), Encoding.ASCII);  
// Use the stream. Remember when you are through with the stream to close it.  
sr.Close();  
```  
  
```vb  
' Create a response object.  
Dim response As WebResponse = request.GetResponse()  
' Get a readable stream from the server.  
Dim sr As _   
   New StreamReader(response.GetResponseStream(), Encoding.ASCII)  
' Use the stream. Remember when you are through with the stream to close it.  
sr.Close()  
```  
  
## <a name="see-also"></a><span data-ttu-id="b98c4-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b98c4-132">See also</span></span>

- [<span data-ttu-id="b98c4-133">Como: Solicitar dados usando a classe WebRequest</span><span class="sxs-lookup"><span data-stu-id="b98c4-133">How to: Request Data Using the WebRequest Class</span></span>](how-to-request-data-using-the-webrequest-class.md)
- [<span data-ttu-id="b98c4-134">Solicitando dados</span><span class="sxs-lookup"><span data-stu-id="b98c4-134">Requesting Data</span></span>](requesting-data.md)
