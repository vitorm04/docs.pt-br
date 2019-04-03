---
title: 'Como: Enviar dados usando a classe WebRequest'
ms.date: 03/25/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WebRequest class, sending data to a host
- Sending data to a host, using WebRequest class
ms.assetid: 66686878-38ac-4aa6-bf42-ffb568ffc459
ms.openlocfilehash: 591a1129625a4ff08c9aa37ce651bbc0320ff25d
ms.sourcegitcommit: d938c39afb9216db377d0f0ecdaa53936a851059
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/29/2019
ms.locfileid: "58634265"
---
# <a name="how-to-send-data-by-using-the-webrequest-class"></a><span data-ttu-id="c167c-102">Como: Enviar dados usando a classe WebRequest</span><span class="sxs-lookup"><span data-stu-id="c167c-102">How to: Send data by using the WebRequest class</span></span>
<span data-ttu-id="c167c-103">O procedimento a seguir descreve as etapas usadas para enviar dados para um servidor.</span><span class="sxs-lookup"><span data-stu-id="c167c-103">The following procedure describes the steps to send data to a server.</span></span> <span data-ttu-id="c167c-104">Esse procedimento normalmente é usado para enviar dados para uma página da Web.</span><span class="sxs-lookup"><span data-stu-id="c167c-104">This procedure is commonly used to post data to a Web page.</span></span> 
  
## <a name="to-send-data-to-a-host-server"></a><span data-ttu-id="c167c-105">Para enviar dados para um servidor de host</span><span class="sxs-lookup"><span data-stu-id="c167c-105">To send data to a host server</span></span>  
  
1.  <span data-ttu-id="c167c-106">Crie uma instância de <xref:System.Net.WebRequest> chamando <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> com o URI do recurso, como um script ou uma página ASP.NET, que aceite dados.</span><span class="sxs-lookup"><span data-stu-id="c167c-106">Create a <xref:System.Net.WebRequest> instance by calling <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> with the URI of a resource, such as a script or ASP.NET page, that accepts data.</span></span> <span data-ttu-id="c167c-107">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="c167c-107">For example:</span></span> 
  
    ```csharp  
    WebRequest request = WebRequest.Create("http://www.contoso.com/PostAccepter.aspx");  
    ```  
  
    ```vb  
    Dim request as WebRequest = WebRequest.Create("http://www.contoso.com/PostAccepter.aspx")  
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="c167c-108">O .NET Framework fornece classes específicas de protocolo derivadas das classes <xref:System.Net.WebRequest> e <xref:System.Net.WebResponse> para URIs que começam com *http:*, *https:*, *ftp:* e *file:*.</span><span class="sxs-lookup"><span data-stu-id="c167c-108">The .NET Framework provides protocol-specific classes derived from the <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes for URIs that begin with *http:*, *https:*, *ftp:*, and *file:*.</span></span>
    <span data-ttu-id="c167c-109">Caso precise definir ou ler propriedades específica de protocolo, converta o objeto <xref:System.Net.WebRequest> ou <xref:System.Net.WebResponse> em um tipo de objeto específico de protocolo.</span><span class="sxs-lookup"><span data-stu-id="c167c-109">If you need to set or read protocol-specific properties, you must cast your <xref:System.Net.WebRequest> or <xref:System.Net.WebResponse> object to a protocol-specific object type.</span></span> <span data-ttu-id="c167c-110">Para obter mais informações, confira [Programando protocolos conectáveis](programming-pluggable-protocols.md).</span><span class="sxs-lookup"><span data-stu-id="c167c-110">For more information, see [Programming pluggable protocols](programming-pluggable-protocols.md).</span></span> 
  
2.  <span data-ttu-id="c167c-111">Defina os valores de propriedade necessários no objeto `WebRequest`.</span><span class="sxs-lookup"><span data-stu-id="c167c-111">Set any property values that you need in your `WebRequest` object.</span></span> <span data-ttu-id="c167c-112">Por exemplo, para habilitar a autenticação, defina a propriedade <xref:System.Net.WebRequest.Credentials%2A?displayProperty=nameWithType> como uma instância da classe <xref:System.Net.NetworkCredential>:</span><span class="sxs-lookup"><span data-stu-id="c167c-112">For example, to enable authentication, set the <xref:System.Net.WebRequest.Credentials%2A?displayProperty=nameWithType> property to an instance of the <xref:System.Net.NetworkCredential> class:</span></span>
  
    ```csharp  
    request.Credentials = CredentialCache.DefaultCredentials;  
    ```  
  
    ```vb  
    request.Credentials = CredentialCache.DefaultCredentials  
    ```  
  
3.  <span data-ttu-id="c167c-113">Especifique um método de protocolo que permite que os dados sejam enviados com uma solicitação, como o método `POST` HTTP:</span><span class="sxs-lookup"><span data-stu-id="c167c-113">Specify a protocol method that permits data to be sent with a request, such as the HTTP `POST` method:</span></span>  
  
    ```csharp  
    request.Method = "POST";  
    ```  
  
    ```vb  
    request.Method = "POST"  
    ```  
  
4.  <span data-ttu-id="c167c-114">Defina a propriedade <xref:System.Web.HttpRequest.ContentLength> com o número de bytes incluídos com a solicitação.</span><span class="sxs-lookup"><span data-stu-id="c167c-114">Set the <xref:System.Web.HttpRequest.ContentLength> property to the number of bytes you're including with your request.</span></span> <span data-ttu-id="c167c-115">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="c167c-115">For example:</span></span> 
  
    ```csharp  
    request.ContentLength = byteArray.Length;  
    ```  
  
    ```vb  
    request.ContentLength = byteArray.Length  
    ```  
  
5.  <span data-ttu-id="c167c-116">Defina a propriedade <xref:System.Web.HttpRequest.ContentType> com um valor apropriado.</span><span class="sxs-lookup"><span data-stu-id="c167c-116">Set the <xref:System.Web.HttpRequest.ContentType> property to an appropriate value.</span></span> <span data-ttu-id="c167c-117">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="c167c-117">For example:</span></span>
  
    ```csharp  
    request.ContentType = "application/x-www-form-urlencoded";  
    ```  
  
    ```vb  
    request.ContentType = "application/x-www-form-urlencoded"  
    ```  
  
6.  <span data-ttu-id="c167c-118">Obtenha o fluxo que mantém dados de solicitação chamando o método <xref:System.Net.WebRequest.GetRequestStream%2A>.</span><span class="sxs-lookup"><span data-stu-id="c167c-118">Get the stream that holds request data by calling the <xref:System.Net.WebRequest.GetRequestStream%2A> method.</span></span> <span data-ttu-id="c167c-119">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="c167c-119">For example:</span></span>
  
    ```csharp  
    Stream dataStream = request.GetRequestStream();  
    ```  
  
    ```vb  
    Stream dataStream = request.GetRequestStream()  
    ```  
  
7.  <span data-ttu-id="c167c-120">Grave os dados no objeto <xref:System.IO.Stream> retornado pelo método `GetRequestStream`.</span><span class="sxs-lookup"><span data-stu-id="c167c-120">Write the data to the <xref:System.IO.Stream> object returned by the `GetRequestStream` method.</span></span> <span data-ttu-id="c167c-121">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="c167c-121">For example:</span></span>
  
    ```csharp  
    dataStream.Write(byteArray, 0, byteArray.Length);  
    ```  
  
    ```vb  
    dataStream.Write(byteArray, 0, byteArray.Length)  
    ```  
  
8.  <span data-ttu-id="c167c-122">Feche o fluxo de solicitação chamando o método <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c167c-122">Close the request stream by calling the <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="c167c-123">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="c167c-123">For example:</span></span>
  
    ```csharp  
    dataStream.Close();  
    ```  
  
    ```vb  
    dataStream.Close()  
    ```  
  
9. <span data-ttu-id="c167c-124">Envie a solicitação para o servidor chamando <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c167c-124">Send the request to the server by calling <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="c167c-125">Esse método retorna um objeto que contém a resposta do servidor.</span><span class="sxs-lookup"><span data-stu-id="c167c-125">This method returns an object containing the server's response.</span></span> <span data-ttu-id="c167c-126">O tipo do objeto `WebResponse` retornado é determinado pelo esquema do URI da solicitação.</span><span class="sxs-lookup"><span data-stu-id="c167c-126">The returned `WebResponse` object's type is determined by the scheme of the request's URI.</span></span> <span data-ttu-id="c167c-127">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="c167c-127">For example:</span></span>
  
    ```csharp  
    WebResponse response = request.GetResponse();  
    ```  
  
    ```vb  
    Dim response As WebResponse = request.GetResponse()  
    ```  
  
10. <span data-ttu-id="c167c-128">Você pode acessar as propriedades do objeto `WebResponse` ou convertê-lo em uma instância específica de protocolo para ler propriedades específicas de protocolo.</span><span class="sxs-lookup"><span data-stu-id="c167c-128">You can access the properties of your `WebResponse` object or cast it to a protocol-specific instance to read protocol-specific properties.</span></span> 

    <span data-ttu-id="c167c-129">Por exemplo, para acessar as propriedades específicas de HTTP de <xref:System.Net.HttpWebResponse>, converta o objeto `WebResponse` em uma referência <xref:System.Net.HttpWebResponse>.</span><span class="sxs-lookup"><span data-stu-id="c167c-129">For example, to access the HTTP-specific properties of <xref:System.Net.HttpWebResponse>, cast your `WebResponse` object to an <xref:System.Net.HttpWebResponse> reference.</span></span> <span data-ttu-id="c167c-130">O seguinte exemplo de código mostra como exibir a propriedade <xref:System.Net.HttpWebResponse.StatusDescription%2A?displayProperty=nameWithType> específica de HTTP enviada com uma resposta:</span><span class="sxs-lookup"><span data-stu-id="c167c-130">The following code example shows how to display the HTTP-specific <xref:System.Net.HttpWebResponse.StatusDescription%2A?displayProperty=nameWithType> property sent with a response:</span></span>
  
    ```csharp  
    Console.WriteLine(((HttpWebResponse)response).StatusDescription);    
    ```  
  
    ```vb  
    Console.WriteLine(CType(response, HttpWebResponse).StatusDescription)  
    ```  
  
11. <span data-ttu-id="c167c-131">Para obter o fluxo que contém os dados de resposta enviados pelo servidor, chame o método <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> do objeto `WebResponse`.</span><span class="sxs-lookup"><span data-stu-id="c167c-131">To get the stream containing response data sent by the server, call the <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> method of your `WebResponse` object.</span></span> <span data-ttu-id="c167c-132">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="c167c-132">For example:</span></span>
  
    ```csharp  
    Stream dataStream = response.GetResponseStream();  
    ```  
  
    ```vb  
    Dim dataStream As Stream = response.GetResponseStream()  
    ```  
  
12. <span data-ttu-id="c167c-133">Depois de ler os dados do objeto de resposta, feche-o com o método <xref:System.Net.WebResponse.Close%2A?displayProperty=nameWithType> ou feche o fluxo de resposta com o método <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c167c-133">After you've read the data from the response object, either close it with the <xref:System.Net.WebResponse.Close%2A?displayProperty=nameWithType> method or close the response stream with the <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="c167c-134">Se você não fechar a resposta ou o fluxo, seu aplicativo poderá ficar sem conexões com o servidor e sem a capacidade de processar solicitações adicionais.</span><span class="sxs-lookup"><span data-stu-id="c167c-134">If you don't close either the response or the stream, your application can run out of server connections and become unable to process additional requests.</span></span> <span data-ttu-id="c167c-135">Como o método `WebResponse.Close` chama `Stream.Close` quando ele fecha a resposta, não é necessário chamar `Close` nos objetos de resposta e de fluxo, embora fazer isso não seja prejudicial.</span><span class="sxs-lookup"><span data-stu-id="c167c-135">Because the `WebResponse.Close` method calls `Stream.Close` when it closes the response, it's not necessary to call `Close` on both the response and stream objects, although doing so isn't harmful.</span></span> <span data-ttu-id="c167c-136">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="c167c-136">For example:</span></span>
  
    ```csharp  
    response.Close();  
    ```  
  
    ```vb  
    response.Close()  
    ```  
  
## <a name="example"></a><span data-ttu-id="c167c-137">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c167c-137">Example</span></span>  
  
<span data-ttu-id="c167c-138">O seguinte exemplo de código mostra como enviar dados para um servidor Web e ler os dados na resposta:</span><span class="sxs-lookup"><span data-stu-id="c167c-138">The following code example shows how to send data to a web server and read the data in its response:</span></span>  

```csharp  
using System;  
using System.IO;  
using System.Net;  
using System.Text;  
  
namespace Examples.System.Net  
{  
    public class WebRequestPostExample  
    {  
        public static void Main()  
        {  
            // Create a request by using a URL that can receive a post.   
            WebRequest request = WebRequest.Create("http://www.contoso.com/PostAccepter.aspx ");  
            // Set the Method property of the request to POST.  
            request.Method = "POST";  

            // Create POST data and convert it to a byte array.  
            string postData = "This is a test that posts this string to a Web server.";  
            byte[] byteArray = Encoding.UTF8.GetBytes(postData);  

            // Set the ContentType property of the request.  
            request.ContentType = "application/x-www-form-urlencoded";  
            // Set the ContentLength property of the request.  
            request.ContentLength = byteArray.Length;  

            // Get the request stream.  
            Stream dataStream = request.GetRequestStream();  
            // Write the data to the request stream.  
            dataStream.Write(byteArray, 0, byteArray.Length);  
            // Close the stream.  
            dataStream.Close();  

            // Get the response.  
            WebResponse response = request.GetResponse();  
            // Display the status.  
            Console.WriteLine(((HttpWebResponse)response).StatusDescription);  

            // Get the stream containing content returned by the server.  
            dataStream = response.GetResponseStream();  
            // Open the stream by using a StreamReader for easy access.  
            StreamReader reader = new StreamReader(dataStream);  

            // Read the content.  
            string responseFromServer = reader.ReadToEnd();  
            // Display the content.  
            Console.WriteLine(responseFromServer);  

            // Clean up the response.  
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

    Public Class WebRequestPostExample  
  
        Public Shared Sub Main()  

            ' Create a request by using a URL that can receive a post.   
            Dim request As WebRequest = WebRequest.Create("http://www.contoso.com/PostAccepter.aspx ")  
            ' Set the Method property of the request to POST.  
            request.Method = "POST"  

            ' Create POST data and convert it to a byte array.  
            Dim postData As String = "This is a test that posts this string to a Web server."  
            Dim byteArray As Byte() = Encoding.UTF8.GetBytes(postData)  

            ' Set the ContentType property of the WebRequest.  
            request.ContentType = "application/x-www-form-urlencoded"  
            ' Set the ContentLength property of the WebRequest.  
            request.ContentLength = byteArray.Length  

            ' Get the request stream.  
            Dim dataStream As Stream = request.GetRequestStream()  
            ' Write the data to the request stream.  
            dataStream.Write(byteArray, 0, byteArray.Length)  
            ' Close the stream.  
            dataStream.Close()  

            ' Get the response.  
            Dim response As WebResponse = request.GetResponse()  
            ' Display the status.  
            Console.WriteLine(CType(response, HttpWebResponse).StatusDescription)  

            ' Get the stream containing content returned by the server.  
            dataStream = response.GetResponseStream()  
            ' Open the stream by using a StreamReader for easy access.  
            Dim reader As New StreamReader(dataStream)  

            ' Read the content.  
            Dim responseFromServer As String = reader.ReadToEnd()  
            ' Display the content.  
            Console.WriteLine(responseFromServer)  

            ' Clean up the response.  
            reader.Close()  
            response.Close()  

        End Sub  

    End Class  

End Namespace  
```  
  
## <a name="see-also"></a><span data-ttu-id="c167c-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c167c-139">See also</span></span>
- [<span data-ttu-id="c167c-140">Criando solicitações da Internet</span><span class="sxs-lookup"><span data-stu-id="c167c-140">Creating internet requests</span></span>](creating-internet-requests.md)
- [<span data-ttu-id="c167c-141">Usando fluxos na rede</span><span class="sxs-lookup"><span data-stu-id="c167c-141">Using streams on the network</span></span>](using-streams-on-the-network.md)
- [<span data-ttu-id="c167c-142">Acessando a Internet por meio de um proxy</span><span class="sxs-lookup"><span data-stu-id="c167c-142">Accessing the internet through a proxy</span></span>](accessing-the-internet-through-a-proxy.md)
- [<span data-ttu-id="c167c-143">Solicitando dados</span><span class="sxs-lookup"><span data-stu-id="c167c-143">Requesting data</span></span>](requesting-data.md)
- [<span data-ttu-id="c167c-144">Como: Solicitar dados usando a classe WebRequest</span><span class="sxs-lookup"><span data-stu-id="c167c-144">How to: Request data by using the WebRequest class</span></span>](how-to-request-data-using-the-webrequest-class.md)
