---
title: 'Como: enviar dados usando a classe WebRequest'
description: Saiba como enviar dados para um servidor usando a classe WebRequest no .NET Framework. Esse procedimento geralmente é usado para postar dados em uma página da Web.
ms.date: 03/25/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WebRequest class, sending data to a host
- Sending data to a host, using WebRequest class
ms.assetid: 66686878-38ac-4aa6-bf42-ffb568ffc459
ms.openlocfilehash: 4b353250fec778ee8b352f13de6d7faaf15c13ee
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502438"
---
# <a name="how-to-send-data-by-using-the-webrequest-class"></a><span data-ttu-id="a6ae3-104">Como: enviar dados usando a classe WebRequest</span><span class="sxs-lookup"><span data-stu-id="a6ae3-104">How to: Send data by using the WebRequest class</span></span>

<span data-ttu-id="a6ae3-105">O procedimento a seguir descreve as etapas usadas para enviar dados para um servidor.</span><span class="sxs-lookup"><span data-stu-id="a6ae3-105">The following procedure describes the steps to send data to a server.</span></span> <span data-ttu-id="a6ae3-106">Esse procedimento normalmente é usado para enviar dados para uma página da Web.</span><span class="sxs-lookup"><span data-stu-id="a6ae3-106">This procedure is commonly used to post data to a Web page.</span></span>

## <a name="to-send-data-to-a-host-server"></a><span data-ttu-id="a6ae3-107">Para enviar dados para um servidor de host</span><span class="sxs-lookup"><span data-stu-id="a6ae3-107">To send data to a host server</span></span>

1. <span data-ttu-id="a6ae3-108">Crie uma instância de <xref:System.Net.WebRequest> chamando <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> com o URI do recurso, como um script ou uma página ASP.NET, que aceite dados.</span><span class="sxs-lookup"><span data-stu-id="a6ae3-108">Create a <xref:System.Net.WebRequest> instance by calling <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> with the URI of a resource, such as a script or ASP.NET page, that accepts data.</span></span> <span data-ttu-id="a6ae3-109">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="a6ae3-109">For example:</span></span>

    ```csharp
    WebRequest request = WebRequest.Create("http://www.contoso.com/PostAccepter.aspx");
    ```

    ```vb
    Dim request as WebRequest = WebRequest.Create("http://www.contoso.com/PostAccepter.aspx")
    ```

    > [!NOTE]
    > <span data-ttu-id="a6ae3-110">O .NET Framework fornece classes específicas de protocolo derivadas das classes <xref:System.Net.WebRequest> e <xref:System.Net.WebResponse> para URIs que começam com *http:*, *https:*, *ftp:* e *file:*.</span><span class="sxs-lookup"><span data-stu-id="a6ae3-110">The .NET Framework provides protocol-specific classes derived from the <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes for URIs that begin with *http:*, *https:*, *ftp:*, and *file:*.</span></span>

    <span data-ttu-id="a6ae3-111">Caso precise definir ou ler propriedades específica de protocolo, converta o objeto <xref:System.Net.WebRequest> ou <xref:System.Net.WebResponse> em um tipo de objeto específico de protocolo.</span><span class="sxs-lookup"><span data-stu-id="a6ae3-111">If you need to set or read protocol-specific properties, you must cast your <xref:System.Net.WebRequest> or <xref:System.Net.WebResponse> object to a protocol-specific object type.</span></span> <span data-ttu-id="a6ae3-112">Para obter mais informações, confira [Programando protocolos conectáveis](programming-pluggable-protocols.md).</span><span class="sxs-lookup"><span data-stu-id="a6ae3-112">For more information, see [Programming pluggable protocols](programming-pluggable-protocols.md).</span></span>

2. <span data-ttu-id="a6ae3-113">Defina os valores de propriedade necessários no objeto `WebRequest`.</span><span class="sxs-lookup"><span data-stu-id="a6ae3-113">Set any property values that you need in your `WebRequest` object.</span></span> <span data-ttu-id="a6ae3-114">Por exemplo, para habilitar a autenticação, defina a propriedade <xref:System.Net.WebRequest.Credentials%2A?displayProperty=nameWithType> como uma instância da classe <xref:System.Net.NetworkCredential>:</span><span class="sxs-lookup"><span data-stu-id="a6ae3-114">For example, to enable authentication, set the <xref:System.Net.WebRequest.Credentials%2A?displayProperty=nameWithType> property to an instance of the <xref:System.Net.NetworkCredential> class:</span></span>

    ```csharp
    request.Credentials = CredentialCache.DefaultCredentials;
    ```

    ```vb
    request.Credentials = CredentialCache.DefaultCredentials
    ```

3. <span data-ttu-id="a6ae3-115">Especifique um método de protocolo que permite que os dados sejam enviados com uma solicitação, como o método `POST` HTTP:</span><span class="sxs-lookup"><span data-stu-id="a6ae3-115">Specify a protocol method that permits data to be sent with a request, such as the HTTP `POST` method:</span></span>

    ```csharp
    request.Method = "POST";
    ```

    ```vb
    request.Method = "POST"
    ```

4. <span data-ttu-id="a6ae3-116">Defina a propriedade <xref:System.Web.HttpRequest.ContentLength> com o número de bytes incluídos com a solicitação.</span><span class="sxs-lookup"><span data-stu-id="a6ae3-116">Set the <xref:System.Web.HttpRequest.ContentLength> property to the number of bytes you're including with your request.</span></span> <span data-ttu-id="a6ae3-117">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="a6ae3-117">For example:</span></span>

    ```csharp
    request.ContentLength = byteArray.Length;
    ```

    ```vb
    request.ContentLength = byteArray.Length
    ```

5. <span data-ttu-id="a6ae3-118">Defina a propriedade <xref:System.Web.HttpRequest.ContentType> com um valor apropriado.</span><span class="sxs-lookup"><span data-stu-id="a6ae3-118">Set the <xref:System.Web.HttpRequest.ContentType> property to an appropriate value.</span></span> <span data-ttu-id="a6ae3-119">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="a6ae3-119">For example:</span></span>

    ```csharp
    request.ContentType = "application/x-www-form-urlencoded";
    ```

    ```vb
    request.ContentType = "application/x-www-form-urlencoded"
    ```

6. <span data-ttu-id="a6ae3-120">Obtenha o fluxo que mantém dados de solicitação chamando o método <xref:System.Net.WebRequest.GetRequestStream%2A>.</span><span class="sxs-lookup"><span data-stu-id="a6ae3-120">Get the stream that holds request data by calling the <xref:System.Net.WebRequest.GetRequestStream%2A> method.</span></span> <span data-ttu-id="a6ae3-121">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="a6ae3-121">For example:</span></span>

    ```csharp
    Stream dataStream = request.GetRequestStream();
    ```

    ```vb
    Dim dataStream As Stream = request.GetRequestStream()
    ```

7. <span data-ttu-id="a6ae3-122">Grave os dados no objeto <xref:System.IO.Stream> retornado pelo método `GetRequestStream`.</span><span class="sxs-lookup"><span data-stu-id="a6ae3-122">Write the data to the <xref:System.IO.Stream> object returned by the `GetRequestStream` method.</span></span> <span data-ttu-id="a6ae3-123">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="a6ae3-123">For example:</span></span>

    ```csharp
    dataStream.Write(byteArray, 0, byteArray.Length);
    ```

    ```vb
    dataStream.Write(byteArray, 0, byteArray.Length)
    ```

8. <span data-ttu-id="a6ae3-124">Feche o fluxo de solicitação chamando o método <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a6ae3-124">Close the request stream by calling the <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="a6ae3-125">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="a6ae3-125">For example:</span></span>

    ```csharp
    dataStream.Close();
    ```

    ```vb
    dataStream.Close()
    ```

9. <span data-ttu-id="a6ae3-126">Envie a solicitação para o servidor chamando <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a6ae3-126">Send the request to the server by calling <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="a6ae3-127">Esse método retorna um objeto que contém a resposta do servidor.</span><span class="sxs-lookup"><span data-stu-id="a6ae3-127">This method returns an object containing the server's response.</span></span> <span data-ttu-id="a6ae3-128">O tipo do objeto `WebResponse` retornado é determinado pelo esquema do URI da solicitação.</span><span class="sxs-lookup"><span data-stu-id="a6ae3-128">The returned `WebResponse` object's type is determined by the scheme of the request's URI.</span></span> <span data-ttu-id="a6ae3-129">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="a6ae3-129">For example:</span></span>

    ```csharp
    WebResponse response = request.GetResponse();
    ```

    ```vb
    Dim response As WebResponse = request.GetResponse()
    ```

10. <span data-ttu-id="a6ae3-130">Você pode acessar as propriedades do objeto `WebResponse` ou convertê-lo em uma instância específica de protocolo para ler propriedades específicas de protocolo.</span><span class="sxs-lookup"><span data-stu-id="a6ae3-130">You can access the properties of your `WebResponse` object or cast it to a protocol-specific instance to read protocol-specific properties.</span></span>

    <span data-ttu-id="a6ae3-131">Por exemplo, para acessar as propriedades específicas de HTTP de <xref:System.Net.HttpWebResponse>, converta o objeto `WebResponse` em uma referência <xref:System.Net.HttpWebResponse>.</span><span class="sxs-lookup"><span data-stu-id="a6ae3-131">For example, to access the HTTP-specific properties of <xref:System.Net.HttpWebResponse>, cast your `WebResponse` object to an <xref:System.Net.HttpWebResponse> reference.</span></span> <span data-ttu-id="a6ae3-132">O seguinte exemplo de código mostra como exibir a propriedade <xref:System.Net.HttpWebResponse.StatusDescription%2A?displayProperty=nameWithType> específica de HTTP enviada com uma resposta:</span><span class="sxs-lookup"><span data-stu-id="a6ae3-132">The following code example shows how to display the HTTP-specific <xref:System.Net.HttpWebResponse.StatusDescription%2A?displayProperty=nameWithType> property sent with a response:</span></span>

    ```csharp
    Console.WriteLine(((HttpWebResponse)response).StatusDescription);
    ```

    ```vb
    Console.WriteLine(CType(response, HttpWebResponse).StatusDescription)
    ```

11. <span data-ttu-id="a6ae3-133">Para obter o fluxo que contém os dados de resposta enviados pelo servidor, chame o método <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> do objeto `WebResponse`.</span><span class="sxs-lookup"><span data-stu-id="a6ae3-133">To get the stream containing response data sent by the server, call the <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> method of your `WebResponse` object.</span></span> <span data-ttu-id="a6ae3-134">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="a6ae3-134">For example:</span></span>

    ```csharp
    Stream dataStream = response.GetResponseStream();
    ```

    ```vb
    Dim dataStream As Stream = response.GetResponseStream()
    ```

12. <span data-ttu-id="a6ae3-135">Depois de ler os dados do objeto de resposta, feche-o com o método <xref:System.Net.WebResponse.Close%2A?displayProperty=nameWithType> ou feche o fluxo de resposta com o método <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a6ae3-135">After you've read the data from the response object, either close it with the <xref:System.Net.WebResponse.Close%2A?displayProperty=nameWithType> method or close the response stream with the <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="a6ae3-136">Se você não fechar a resposta ou o fluxo, seu aplicativo poderá ficar sem conexões com o servidor e sem a capacidade de processar solicitações adicionais.</span><span class="sxs-lookup"><span data-stu-id="a6ae3-136">If you don't close either the response or the stream, your application can run out of server connections and become unable to process additional requests.</span></span> <span data-ttu-id="a6ae3-137">Como o método `WebResponse.Close` chama `Stream.Close` quando ele fecha a resposta, não é necessário chamar `Close` nos objetos de resposta e de fluxo, embora fazer isso não seja prejudicial.</span><span class="sxs-lookup"><span data-stu-id="a6ae3-137">Because the `WebResponse.Close` method calls `Stream.Close` when it closes the response, it's not necessary to call `Close` on both the response and stream objects, although doing so isn't harmful.</span></span> <span data-ttu-id="a6ae3-138">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="a6ae3-138">For example:</span></span>

    ```csharp
    response.Close();
    ```

    ```vb
    response.Close()
    ```

## <a name="example"></a><span data-ttu-id="a6ae3-139">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a6ae3-139">Example</span></span>

<span data-ttu-id="a6ae3-140">O seguinte exemplo mostra como enviar dados para um servidor Web e ler os dados na resposta:</span><span class="sxs-lookup"><span data-stu-id="a6ae3-140">The following example shows how to send data to a web server and read the data in its response:</span></span>

[!code-csharp[SendDataUsingWebRequest](../../../samples/snippets/csharp/VS_Snippets_Network/SendDataUsingWebRequest/cs/WebRequestPostExample.cs)]
[!code-vb[SendDataUsingWebRequest](../../../samples/snippets/visualbasic/VS_Snippets_Network/SendDataUsingWebRequest/vb/WebRequestPostExample.vb)]

## <a name="see-also"></a><span data-ttu-id="a6ae3-141">Confira também</span><span class="sxs-lookup"><span data-stu-id="a6ae3-141">See also</span></span>

- [<span data-ttu-id="a6ae3-142">Criando solicitações da Internet</span><span class="sxs-lookup"><span data-stu-id="a6ae3-142">Creating internet requests</span></span>](creating-internet-requests.md)
- [<span data-ttu-id="a6ae3-143">Usando fluxos na rede</span><span class="sxs-lookup"><span data-stu-id="a6ae3-143">Using streams on the network</span></span>](using-streams-on-the-network.md)
- [<span data-ttu-id="a6ae3-144">Acessando a Internet por meio de um proxy</span><span class="sxs-lookup"><span data-stu-id="a6ae3-144">Accessing the internet through a proxy</span></span>](accessing-the-internet-through-a-proxy.md)
- [<span data-ttu-id="a6ae3-145">Solicitando dados</span><span class="sxs-lookup"><span data-stu-id="a6ae3-145">Requesting data</span></span>](requesting-data.md)
- [<span data-ttu-id="a6ae3-146">Como: solicitar dados usando a classe WebRequest</span><span class="sxs-lookup"><span data-stu-id="a6ae3-146">How to: Request data by using the WebRequest class</span></span>](how-to-request-data-using-the-webrequest-class.md)
