---
title: Como solicitar dados usando a classe WebRequest
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- downloading Internet resources, steps
- requesting data from Internet, steps
- WebRequest class, receiving data
- receiving data, using WebRequest class
- Internet, requesting data
ms.assetid: 368b8d0f-dc5e-4469-a8b8-b2adbf5dd800
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 8928ce8790f58b6920c16cbfd9fc8d9aa6644a44
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47197819"
---
# <a name="how-to-request-data-using-the-webrequest-class"></a><span data-ttu-id="3eeda-102">Como solicitar dados usando a classe WebRequest</span><span class="sxs-lookup"><span data-stu-id="3eeda-102">How to: Request Data Using the WebRequest Class</span></span>
<span data-ttu-id="3eeda-103">O procedimento a seguir descreve as etapas usadas para solicitar um recurso de um servidor, por exemplo, uma página da Web ou arquivo.</span><span class="sxs-lookup"><span data-stu-id="3eeda-103">The following procedure describes the steps used to request a resource from a server, for example, a Web page or file.</span></span> <span data-ttu-id="3eeda-104">O recurso deve ser identificado por um URI.</span><span class="sxs-lookup"><span data-stu-id="3eeda-104">The resource must be identified by a URI.</span></span>  
  
### <a name="to-request-data-from-a-host-server"></a><span data-ttu-id="3eeda-105">Para solicitar dados de um servidor host</span><span class="sxs-lookup"><span data-stu-id="3eeda-105">To request data from a host server</span></span>  
  
1.  <span data-ttu-id="3eeda-106">Criar uma instância de <xref:System.Net.WebRequest> chamando <xref:System.Net.WebRequest.Create%2A> com o URI do recurso.</span><span class="sxs-lookup"><span data-stu-id="3eeda-106">Create a <xref:System.Net.WebRequest> instance by calling <xref:System.Net.WebRequest.Create%2A> with the URI of the resource.</span></span>  
  
    ```csharp  
    WebRequest request = WebRequest.Create("http://www.contoso.com/");  
    ```  
  
    ```vb  
    Dim request as WebRequest = WebRequest.Create("http://www.contoso.com/")  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="3eeda-107">O .NET Framework fornece classes específicas de protocolo derivadas de **WebRequest** e **WebResponse** para URIs que começam com "http:", "https:", "ftp:" e "file:".</span><span class="sxs-lookup"><span data-stu-id="3eeda-107">The .NET Framework provides protocol-specific classes derived from **WebRequest** and **WebResponse** for URIs that begin with "http:", "https:'', "ftp:", and "file:".</span></span> <span data-ttu-id="3eeda-108">Para acessar recursos usando outros protocolos, você deve implementar classes específicas de protocolo derivadas de **WebRequest** e **WebResponse**.</span><span class="sxs-lookup"><span data-stu-id="3eeda-108">To access resources using other protocols, you must implement protocol-specific classes that derive from **WebRequest** and **WebResponse**.</span></span> <span data-ttu-id="3eeda-109">Para obter mais informações, consulte [Programando protocolos conectáveis](../../../docs/framework/network-programming/programming-pluggable-protocols.md).</span><span class="sxs-lookup"><span data-stu-id="3eeda-109">For more information, see [Programming Pluggable Protocols](../../../docs/framework/network-programming/programming-pluggable-protocols.md) .</span></span>  
  
2.  <span data-ttu-id="3eeda-110">Definir quaisquer valores de propriedade dos quais você precisa na **WebRequest**.</span><span class="sxs-lookup"><span data-stu-id="3eeda-110">Set any property values that you need in the **WebRequest**.</span></span> <span data-ttu-id="3eeda-111">Por exemplo, para habilitar a autenticação, defina a propriedade **Credentials** para uma instância da classe <xref:System.Net.NetworkCredential>.</span><span class="sxs-lookup"><span data-stu-id="3eeda-111">For example, to enable authentication, set the **Credentials** property to an instance of the <xref:System.Net.NetworkCredential> class.</span></span>  
  
    ```csharp  
    request.Credentials = CredentialCache.DefaultCredentials;  
    ```  
  
    ```vb  
    request.Credentials = CredentialCache.DefaultCredentials  
    ```  
  
     <span data-ttu-id="3eeda-112">Na maioria dos casos, a classe **WebRequest** é suficiente para receber dados.</span><span class="sxs-lookup"><span data-stu-id="3eeda-112">In most cases, the **WebRequest** class is sufficient to receive data.</span></span> <span data-ttu-id="3eeda-113">No entanto, se você precisar definir propriedades específicas de protocolo, você deverá converter a **WebRequest** para o tipo específico do protocolo.</span><span class="sxs-lookup"><span data-stu-id="3eeda-113">However, if you need to set protocol-specific properties, you must cast the **WebRequest** to the protocol-specific type.</span></span> <span data-ttu-id="3eeda-114">Por exemplo, acessar propriedades HTTP específicas de <xref:System.Net.HttpWebRequest>, converta a **WebRequest** para uma referência de **HttpWebRequest**.</span><span class="sxs-lookup"><span data-stu-id="3eeda-114">For example, to access the HTTP-specific properties of <xref:System.Net.HttpWebRequest>, cast the **WebRequest** to an **HttpWebRequest** reference.</span></span> <span data-ttu-id="3eeda-115">O exemplo de código a seguir mostra como definir a propriedade <xref:System.Net.HttpWebRequest.UserAgent%2A> específica de HTTP.</span><span class="sxs-lookup"><span data-stu-id="3eeda-115">The following code example shows how to set the HTTP-specific <xref:System.Net.HttpWebRequest.UserAgent%2A> property.</span></span>  
  
    ```csharp  
    ((HttpWebRequest)request).UserAgent = ".NET Framework Example Client";  
    ```  
  
    ```vb  
    Ctype(request,HttpWebRequest).UserAgent = ".NET Framework Example Client"  
    ```  
  
3.  <span data-ttu-id="3eeda-116">Para enviar a solicitação para o servidor, chame <xref:System.Net.HttpWebRequest.GetResponse%2A>.</span><span class="sxs-lookup"><span data-stu-id="3eeda-116">To send the request to the server, call <xref:System.Net.HttpWebRequest.GetResponse%2A>.</span></span> <span data-ttu-id="3eeda-117">O tipo real do objeto **WebResponse** retornado é determinado pelo esquema do URI solicitado.</span><span class="sxs-lookup"><span data-stu-id="3eeda-117">The actual type of the returned **WebResponse** object is determined by the scheme of the requested URI.</span></span>  
  
    ```csharp  
    WebResponse response = request.GetResponse();  
    ```  
  
    ```vb  
    Dim response As WebResponse = request.GetResponse()  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="3eeda-118">Depois de terminar de usar um objeto <xref:System.Net.WebResponse>, você deve fechá-lo chamando o método <xref:System.Net.WebResponse.Close%2A>.</span><span class="sxs-lookup"><span data-stu-id="3eeda-118">After you are finished with a <xref:System.Net.WebResponse> object, you must close it by calling the <xref:System.Net.WebResponse.Close%2A> method.</span></span> <span data-ttu-id="3eeda-119">Alternativamente, se você obteve o fluxo de resposta do objeto de resposta, você pode fechar o fluxo chamando o método <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3eeda-119">Alternatively, if you have gotten the response stream from the response object, you can close the stream by calling the <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="3eeda-120">Se você não fechar a resposta ou o fluxo, o seu aplicativo poderá ficar sem conexões para o servidor e, nesse caso, ficará incapaz de processar solicitações adicionais.</span><span class="sxs-lookup"><span data-stu-id="3eeda-120">If you do not close either the response or the stream, your application can run out of connections to the server and become unable to process additional requests.</span></span>  
  
4.  <span data-ttu-id="3eeda-121">Você pode acessar as propriedades da **WebResponse** ou converter a **WebResponse** para uma instância específica de protocolo para ler as propriedades específicas de protocolo.</span><span class="sxs-lookup"><span data-stu-id="3eeda-121">You can access the properties of the **WebResponse** or cast the **WebResponse** to a protocol-specific instance to read protocol-specific properties.</span></span> <span data-ttu-id="3eeda-122">Por exemplo, para acessar as propriedades específicas de HTTP de <xref:System.Net.HttpWebResponse>, converta a **WebResponse** para uma referência de **HttpWebResponse**.</span><span class="sxs-lookup"><span data-stu-id="3eeda-122">For example, to access the HTTP-specific properties of <xref:System.Net.HttpWebResponse>, cast the **WebResponse** to a **HttpWebResponse** reference.</span></span> <span data-ttu-id="3eeda-123">O exemplo de código a seguir mostra como exibir as informações de status enviadas com uma resposta.</span><span class="sxs-lookup"><span data-stu-id="3eeda-123">The following code example shows how to display the status information sent with a response.</span></span>  
  
    ```csharp  
    Console.WriteLine (((HttpWebResponse)response).StatusDescription);  
    ```  
  
    ```vb  
    Console.WriteLine(CType(response,HttpWebResponse).StatusDescription)  
    ```  
  
5.  <span data-ttu-id="3eeda-124">Para obter o fluxo que contém os dados de resposta enviados pelo servidor, use o método <xref:System.Net.HttpWebResponse.GetResponseStream%2A> da **WebResponse**.</span><span class="sxs-lookup"><span data-stu-id="3eeda-124">To get the stream containing response data sent by the server, use the <xref:System.Net.HttpWebResponse.GetResponseStream%2A> method of the **WebResponse**.</span></span>  
  
    ```csharp  
    Stream dataStream = response.GetResponseStream();  
    ```  
  
    ```vb  
    Dim dataStream As Stream = response.GetResponseStream()  
    ```  
  
6.  <span data-ttu-id="3eeda-125">Depois de ler os dados da resposta ou você deve fechar o fluxo de resposta usando o método **Stream.Close** ou fechar a resposta usando o método **WebResponse.Close**.</span><span class="sxs-lookup"><span data-stu-id="3eeda-125">After reading the data from the response, you must either close the response stream using the **Stream.Close** method or close the response using the **WebResponse.Close** method.</span></span> <span data-ttu-id="3eeda-126">Não é necessário chamar o método **Close** tanto no fluxo de resposta quanto na **WebResponse**, mas fazer isso não é prejudicial.</span><span class="sxs-lookup"><span data-stu-id="3eeda-126">It is not necessary to call the **Close** method on both the response stream and the **WebResponse**, but doing so is not harmful.</span></span> <span data-ttu-id="3eeda-127">**WebResponse.Close** chama **Stream.Close** ao fechar a resposta.</span><span class="sxs-lookup"><span data-stu-id="3eeda-127">**WebResponse.Close** calls **Stream.Close** when closing the response.</span></span>  
  
    ```csharp  
    response.Close();  
    ```  
  
    ```vb  
    response.Close()  
    ```  
  
## <a name="example"></a><span data-ttu-id="3eeda-128">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3eeda-128">Example</span></span>  
  
```csharp  
using System;  
using System.IO;  
using System.Net;  
using System.Text;  
  
namespace Examples.System.Net  
{  
    public class WebRequestGetExample  
    {  
        public static void Main()  
        {  
            // Create a request for the URL.   
            WebRequest request = WebRequest.Create(  
              "http://www.contoso.com/default.html");  
            // If required by the server, set the credentials.  
            request.Credentials = CredentialCache.DefaultCredentials;  
            // Get the response.  
            WebResponse response = request.GetResponse();  
            // Display the status.  
            Console.WriteLine (((HttpWebResponse)response).StatusDescription);  
            // Get the stream containing content returned by the server.  
            Stream dataStream = response.GetResponseStream();  
            // Open the stream using a StreamReader for easy access.  
            StreamReader reader = new StreamReader(dataStream);  
            // Read the content.  
            string responseFromServer = reader.ReadToEnd();  
            // Display the content.  
            Console.WriteLine(responseFromServer);  
            // Clean up the streams and the response.  
            reader.Close();  
            response.Close();  
        }  
    }  
}  
```  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Net  
Imports System.Text  
Namespace Examples.System.Net  
    Public Class WebRequestGetExample  
  
        Public Shared Sub Main()  
            ' Create a request for the URL.   
            Dim request As WebRequest = _  
              WebRequest.Create("http://www.contoso.com/default.html")  
            ' If required by the server, set the credentials.  
            request.Credentials = CredentialCache.DefaultCredentials  
            ' Get the response.  
            Dim response As WebResponse = request.GetResponse()  
            ' Display the status.  
            Console.WriteLine(CType(response,HttpWebResponse).StatusDescription)  
            ' Get the stream containing content returned by the server.  
            Dim dataStream As Stream = response.GetResponseStream()  
            ' Open the stream using a StreamReader for easy access.  
            Dim reader As New StreamReader(dataStream)  
            ' Read the content.  
            Dim responseFromServer As String = reader.ReadToEnd()  
            ' Display the content.  
            Console.WriteLine(responseFromServer)  
            ' Clean up the streams and the response.  
            reader.Close()  
            response.Close()  
        End Sub   
    End Class   
End Namespace  
```  
  
## <a name="see-also"></a><span data-ttu-id="3eeda-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3eeda-129">See Also</span></span>  
 [<span data-ttu-id="3eeda-130">Criar solicitações de Internet</span><span class="sxs-lookup"><span data-stu-id="3eeda-130">Creating Internet Requests</span></span>](../../../docs/framework/network-programming/creating-internet-requests.md)  
 [<span data-ttu-id="3eeda-131">Usando fluxos na rede</span><span class="sxs-lookup"><span data-stu-id="3eeda-131">Using Streams on the Network</span></span>](../../../docs/framework/network-programming/using-streams-on-the-network.md)  
 [<span data-ttu-id="3eeda-132">Acessando a Internet por meio de um proxy</span><span class="sxs-lookup"><span data-stu-id="3eeda-132">Accessing the Internet Through a Proxy</span></span>](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)  
 [<span data-ttu-id="3eeda-133">Solicitando dados</span><span class="sxs-lookup"><span data-stu-id="3eeda-133">Requesting Data</span></span>](../../../docs/framework/network-programming/requesting-data.md)  
 [<span data-ttu-id="3eeda-134">Como enviar dados usando a classe WebRequest</span><span class="sxs-lookup"><span data-stu-id="3eeda-134">How to: Send Data Using the WebRequest Class</span></span>](../../../docs/framework/network-programming/how-to-send-data-using-the-webrequest-class.md)
