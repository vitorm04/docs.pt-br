---
title: Solicitando dados
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sending data
- WebRequest class, sending and receiving data
- requesting data from Internet, about requesting data
- WebClient class, sending and receiving data
- network, requesting data
- receiving data
- sending data, about sending data
- response to Internet request, about responding to Internet requests
- data requests
- receiving data, about receiving data
- Internet, requesting data
ms.assetid: df6f1e1d-6f2a-45dd-8141-4a85c3dafe1d
author: mcleblanc
ms.author: markl
ms.openlocfilehash: a163374810cbc06ca048c1bdd304de9519db140c
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47195700"
---
# <a name="requesting-data"></a><span data-ttu-id="6cda6-102">Solicitando dados</span><span class="sxs-lookup"><span data-stu-id="6cda6-102">Requesting Data</span></span>
<span data-ttu-id="6cda6-103">Desenvolver aplicativos que são executados no ambiente operacional distribuído da Internet de hoje requer um método eficiente e fácil de usar para recuperar dados de recursos de todos os tipos.</span><span class="sxs-lookup"><span data-stu-id="6cda6-103">Developing applications that run in the distributed operating environment of today's Internet requires an efficient, easy-to-use method for retrieving data from resources of all types.</span></span> <span data-ttu-id="6cda6-104">Protocolos conectáveis permitem desenvolver aplicativos que usam uma única interface para recuperar dados de vários protocolos de Internet.</span><span class="sxs-lookup"><span data-stu-id="6cda6-104">Pluggable protocols let you develop applications that use a single interface to retrieve data from multiple Internet protocols.</span></span>  
  
## <a name="uploading-and-downloading-data-from-an-internet-server"></a><span data-ttu-id="6cda6-105">Carregando e baixando dados de um servidor de Internet</span><span class="sxs-lookup"><span data-stu-id="6cda6-105">Uploading and Downloading Data from an Internet Server</span></span>  
 <span data-ttu-id="6cda6-106">Para transações simples de solicitação e resposta, a classe <xref:System.Net.WebClient> fornece o método mais fácil para carregar dados para ou fazer o download de dados de um servidor de Internet.</span><span class="sxs-lookup"><span data-stu-id="6cda6-106">For simple request and response transactions, the <xref:System.Net.WebClient> class provides the easiest method for uploading data to or downloading data from an Internet server.</span></span> <span data-ttu-id="6cda6-107">**WebClient** fornece métodos para carregar e baixar arquivos, enviar e receber fluxos e enviar um buffer de dados para o servidor e receber uma resposta.</span><span class="sxs-lookup"><span data-stu-id="6cda6-107">**WebClient** provides methods for uploading and downloading files, sending and receiving streams, and sending a data buffer to the server and receiving a response.</span></span> <span data-ttu-id="6cda6-108">O **WebClient** usa as classes <xref:System.Net.WebRequest> e <xref:System.Net.WebResponse> para fazer as conexões reais para o recurso de Internet, de modo que qualquer protocolo conectável registrado fica disponível para uso.</span><span class="sxs-lookup"><span data-stu-id="6cda6-108">**WebClient** uses the <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes to make the actual connections to the Internet resource, so any registered pluggable protocol is available for use.</span></span>  
  
 <span data-ttu-id="6cda6-109">Aplicativos cliente que precisam fazer transações mais complexas solicitam dados de servidores usando a classe **WebRequest** e seus descendentes.</span><span class="sxs-lookup"><span data-stu-id="6cda6-109">Client applications that need to make more complex transactions request data from servers using the **WebRequest** class and its descendants.</span></span> <span data-ttu-id="6cda6-110">**WebRequest** encapsula os detalhes da conexão com o servidor, do envio da solicitação do recebimento da resposta.</span><span class="sxs-lookup"><span data-stu-id="6cda6-110">**WebRequest** encapsulates the details of connecting to the server, sending the request, and receiving the response.</span></span> <span data-ttu-id="6cda6-111">**WebRequest** é uma classe abstrata que define um conjunto de propriedades e métodos que estão disponíveis para todos os aplicativos que usam protocolos conectáveis.</span><span class="sxs-lookup"><span data-stu-id="6cda6-111">**WebRequest** is an abstract class that defines a set of properties and methods that are available to all applications that use pluggable protocols.</span></span> <span data-ttu-id="6cda6-112">Descendentes de **WebRequest**, tais como <xref:System.Net.HttpWebRequest>, implementam as propriedades e métodos definidos pelo **WebRequest** de maneira consistente com o protocolo subjacente.</span><span class="sxs-lookup"><span data-stu-id="6cda6-112">Descendants of **WebRequest**, such as <xref:System.Net.HttpWebRequest>, implement the properties and methods defined by **WebRequest** in a way that is consistent with the underlying protocol.</span></span>  
  
 <span data-ttu-id="6cda6-113">A classe **WebRequest** cria instâncias específicas de protocolo de descendentes de **WebRequest**, usando o valor do URI passado para o método <xref:System.Net.WebRequest.Create%2A> a fim de determinar a instância da classe derivada específica para criar.</span><span class="sxs-lookup"><span data-stu-id="6cda6-113">The **WebRequest** class creates protocol-specific instances of **WebRequest** descendants, using the value of the URI passed to its <xref:System.Net.WebRequest.Create%2A> method to determine the specific derived-class instance to create.</span></span> <span data-ttu-id="6cda6-114">Aplicativos indicam qual descendente de **WebRequest** deve ser usado para lidar com uma solicitação ao registrar o construtor do descendente com o método <xref:System.Net.WebRequest.RegisterPrefix%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6cda6-114">Applications indicate which **WebRequest** descendant should be used to handle a request by registering the descendant's constructor with the <xref:System.Net.WebRequest.RegisterPrefix%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="6cda6-115">É feita uma solicitação para o recurso de Internet chamando o método <xref:System.Net.WebRequest.GetResponse%2A> no **WebRequest**.</span><span class="sxs-lookup"><span data-stu-id="6cda6-115">A request is made to the Internet resource by calling the <xref:System.Net.WebRequest.GetResponse%2A> method on the **WebRequest**.</span></span> <span data-ttu-id="6cda6-116">O método **GetResponse** constrói a solicitação específica de protocolo nas propriedades da **WebRequest**, faz a conexão de soquete TCP ou UDP para o servidor e envia a solicitação.</span><span class="sxs-lookup"><span data-stu-id="6cda6-116">The **GetResponse** method constructs the protocol-specific request from the properties of the **WebRequest**, makes the TCP or UDP socket connection to the server, and sends the request.</span></span> <span data-ttu-id="6cda6-117">Para solicitações que enviam dados para o servidor, tais como solicitações HTTP **Post** ou FTP **Put**, o método <xref:System.Net.WebRequest.GetRequestStream%2A?displayProperty=nameWithType> fornece um fluxo de rede no qual enviar os dados.</span><span class="sxs-lookup"><span data-stu-id="6cda6-117">For requests that send data to the server, such as HTTP **Post** or FTP **Put** requests, the <xref:System.Net.WebRequest.GetRequestStream%2A?displayProperty=nameWithType> method provides a network stream in which to send the data.</span></span>  
  
 <span data-ttu-id="6cda6-118">O método **GetResponse** retorna uma **WebResponse** específica de protocolo que corresponde a **WebRequest.**</span><span class="sxs-lookup"><span data-stu-id="6cda6-118">The **GetResponse** method returns a protocol-specific **WebResponse** that matches the **WebRequest.**</span></span>  
  
 <span data-ttu-id="6cda6-119">A classe **WebResponse** é também uma classe abstrata que define propriedades e métodos que estão disponíveis para todos os aplicativos que usam protocolos conectáveis.</span><span class="sxs-lookup"><span data-stu-id="6cda6-119">The **WebResponse** class is also an abstract class that defines properties and methods that are available to all applications that use pluggable protocols.</span></span> <span data-ttu-id="6cda6-120">Descendentes de **WebResponse** implementam essas propriedades e métodos para o protocolo subjacente.</span><span class="sxs-lookup"><span data-stu-id="6cda6-120">**WebResponse** descendants implement these properties and methods for the underlying protocol.</span></span> <span data-ttu-id="6cda6-121">A classe <xref:System.Net.HttpWebResponse>, por exemplo, implementa a classe **WebResponse** para HTTP.</span><span class="sxs-lookup"><span data-stu-id="6cda6-121">The <xref:System.Net.HttpWebResponse> class, for example, implements the **WebResponse** class for HTTP.</span></span>  
  
 <span data-ttu-id="6cda6-122">Os dados retornados pelo servidor são apresentados para o aplicativo no fluxo retornado pelo método <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6cda6-122">The data returned by the server is presented to the application in the stream returned by the <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="6cda6-123">Você pode usar esse fluxo como qualquer outro, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="6cda6-123">You can use this stream like any other, as shown in the following example.</span></span>  
  
```csharp  
StreamReader sr =  
   new StreamReader(resp.GetResponseStream(), Encoding.ASCII);  
```  
  
```vb  
Dim sr As StreamReader  
sr = New StreamReader(resp.GetResponseStream(), Encoding.ASCII)  
```  
  
## <a name="see-also"></a><span data-ttu-id="6cda6-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6cda6-124">See Also</span></span>  
 [<span data-ttu-id="6cda6-125">Programação de rede no .NET Framework</span><span class="sxs-lookup"><span data-stu-id="6cda6-125">Network Programming in the .NET Framework</span></span>](../../../docs/framework/network-programming/index.md)  
 [<span data-ttu-id="6cda6-126">Como solicitar uma página da Web e recuperar os resultados como um fluxo</span><span class="sxs-lookup"><span data-stu-id="6cda6-126">How to: Request a Web Page and Retrieve the Results as a Stream</span></span>](../../../docs/framework/network-programming/how-to-request-a-web-page-and-retrieve-the-results-as-a-stream.md)  
 [<span data-ttu-id="6cda6-127">Como recuperar uma WebResponse específica de protocolo que corresponde a uma WebRequest</span><span class="sxs-lookup"><span data-stu-id="6cda6-127">How to: Retrieve a Protocol-Specific WebResponse that Matches a WebRequest</span></span>](../../../docs/framework/network-programming/how-to-retrieve-a-protocol-specific-webresponse-that-matches-a-webrequest.md)
