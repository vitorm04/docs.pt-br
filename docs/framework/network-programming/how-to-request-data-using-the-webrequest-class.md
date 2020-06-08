---
title: 'Como: solicitar dados usando a classe WebRequest'
description: Saiba como solicitar um recurso, como uma página da Web ou um arquivo, de um servidor usando a classe WebRequest na .NET Framework.
ms.date: 03/21/2019
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
ms.openlocfilehash: 5dcc1a7dad226288e3f74969b86e2dd457c0eed0
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502464"
---
# <a name="how-to-request-data-by-using-the-webrequest-class"></a><span data-ttu-id="c3f32-103">Como: solicitar dados usando a classe WebRequest</span><span class="sxs-lookup"><span data-stu-id="c3f32-103">How to: Request data by using the WebRequest class</span></span>

<span data-ttu-id="c3f32-104">O procedimento a seguir descreve as etapas usadas para solicitar um recurso, como uma página da Web ou um arquivo, de um servidor.</span><span class="sxs-lookup"><span data-stu-id="c3f32-104">The following procedure describes the steps to request a resource, such as a Web page or a file, from a server.</span></span> <span data-ttu-id="c3f32-105">O recurso deve ser identificado por um URI.</span><span class="sxs-lookup"><span data-stu-id="c3f32-105">The resource must be identified by a URI.</span></span>

## <a name="to-request-data-from-a-host-server"></a><span data-ttu-id="c3f32-106">Para solicitar dados de um servidor host</span><span class="sxs-lookup"><span data-stu-id="c3f32-106">To request data from a host server</span></span>

1. <span data-ttu-id="c3f32-107">Crie uma instância de <xref:System.Net.WebRequest> chamando <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> com o URI de um recurso.</span><span class="sxs-lookup"><span data-stu-id="c3f32-107">Create a <xref:System.Net.WebRequest> instance by calling <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> with the URI of a resource.</span></span> <span data-ttu-id="c3f32-108">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="c3f32-108">For example:</span></span>

    ```csharp
    WebRequest request = WebRequest.Create("https://docs.microsoft.com");
    ```

    ```vb
    Dim request as WebRequest = WebRequest.Create("https://docs.microsoft.com")
    ```

    > [!NOTE]
    > <span data-ttu-id="c3f32-109">O .NET Framework fornece classes específicas de protocolo derivadas das classes <xref:System.Net.WebRequest> e <xref:System.Net.WebResponse> para URIs que começam com *http:*, *https:*, *ftp:* e *file:*.</span><span class="sxs-lookup"><span data-stu-id="c3f32-109">The .NET Framework provides protocol-specific classes derived from the <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes for URIs that begin with *http:*, *https:*, *ftp:*, and *file:*.</span></span>

    <span data-ttu-id="c3f32-110">Caso precise definir ou ler propriedades específica de protocolo, converta o objeto <xref:System.Net.WebRequest> ou <xref:System.Net.WebResponse> em um tipo de objeto específico de protocolo.</span><span class="sxs-lookup"><span data-stu-id="c3f32-110">If you need to set or read protocol-specific properties, you must cast your <xref:System.Net.WebRequest> or <xref:System.Net.WebResponse> object to a protocol-specific object type.</span></span> <span data-ttu-id="c3f32-111">Para obter mais informações, confira [Programando protocolos conectáveis](programming-pluggable-protocols.md).</span><span class="sxs-lookup"><span data-stu-id="c3f32-111">For more information, see [Programming pluggable protocols](programming-pluggable-protocols.md).</span></span>

2. <span data-ttu-id="c3f32-112">Defina os valores de propriedade necessários no objeto `WebRequest`.</span><span class="sxs-lookup"><span data-stu-id="c3f32-112">Set any property values that you need in your `WebRequest` object.</span></span> <span data-ttu-id="c3f32-113">Por exemplo, para habilitar a autenticação, defina a propriedade <xref:System.Net.WebRequest.Credentials%2A?displayProperty=nameWithType> como uma instância da classe <xref:System.Net.NetworkCredential>:</span><span class="sxs-lookup"><span data-stu-id="c3f32-113">For example, to enable authentication, set the <xref:System.Net.WebRequest.Credentials%2A?displayProperty=nameWithType> property to an instance of the <xref:System.Net.NetworkCredential> class:</span></span>

    ```csharp
    request.Credentials = CredentialCache.DefaultCredentials;
    ```

    ```vb
    request.Credentials = CredentialCache.DefaultCredentials
    ```

3. <span data-ttu-id="c3f32-114">Envie a solicitação para o servidor chamando <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c3f32-114">Send the request to the server by calling <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="c3f32-115">Esse método retorna um objeto que contém a resposta do servidor.</span><span class="sxs-lookup"><span data-stu-id="c3f32-115">This method returns an object containing the server's response.</span></span> <span data-ttu-id="c3f32-116">O tipo do objeto <xref:System.Net.WebResponse> retornado é determinado pelo esquema do URI da solicitação.</span><span class="sxs-lookup"><span data-stu-id="c3f32-116">The returned <xref:System.Net.WebResponse> object's type is determined by the scheme of the request's URI.</span></span> <span data-ttu-id="c3f32-117">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="c3f32-117">For example:</span></span>

    ```csharp
    WebResponse response = request.GetResponse();
    ```

    ```vb
    Dim response As WebResponse = request.GetResponse()
    ```

4. <span data-ttu-id="c3f32-118">Você pode acessar as propriedades do objeto `WebResponse` ou convertê-lo em uma instância específica de protocolo para ler propriedades específicas de protocolo.</span><span class="sxs-lookup"><span data-stu-id="c3f32-118">You can access the properties of your `WebResponse` object or cast it to a protocol-specific instance to read protocol-specific properties.</span></span>

    <span data-ttu-id="c3f32-119">Por exemplo, para acessar as propriedades específicas de HTTP de <xref:System.Net.HttpWebResponse>, converta o objeto `WebResponse` em uma referência `HttpWebResponse`.</span><span class="sxs-lookup"><span data-stu-id="c3f32-119">For example, to access the HTTP-specific properties of <xref:System.Net.HttpWebResponse>, cast your `WebResponse` object to an `HttpWebResponse` reference.</span></span> <span data-ttu-id="c3f32-120">O seguinte exemplo de código mostra como exibir a propriedade <xref:System.Net.HttpWebResponse.StatusDescription%2A?displayProperty=nameWithType> específica de HTTP enviada com uma resposta:</span><span class="sxs-lookup"><span data-stu-id="c3f32-120">The following code example shows how to display the HTTP-specific <xref:System.Net.HttpWebResponse.StatusDescription%2A?displayProperty=nameWithType> property sent with a response:</span></span>

    ```csharp
    Console.WriteLine (((HttpWebResponse)response).StatusDescription);
    ```

    ```vb
    Console.WriteLine(CType(response,HttpWebResponse).StatusDescription)
    ```

5. <span data-ttu-id="c3f32-121">Para obter o fluxo que contém os dados de resposta enviados pelo servidor, chame o método <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c3f32-121">To get the stream containing response data sent by the server, call the <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="c3f32-122">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="c3f32-122">For example:</span></span>

    ```csharp
    Stream dataStream = response.GetResponseStream();
    ```

    ```vb
    Dim dataStream As Stream = response.GetResponseStream()
    ```

6. <span data-ttu-id="c3f32-123">Depois de ler os dados do objeto de resposta, feche-o com o método <xref:System.Net.WebResponse.Close%2A?displayProperty=nameWithType> ou feche o fluxo de resposta com o método <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c3f32-123">After you've read the data from the response object, either close it with the <xref:System.Net.WebResponse.Close%2A?displayProperty=nameWithType> method or close the response stream with the <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="c3f32-124">Se você não fechar o objeto de resposta ou o fluxo, seu aplicativo poderá ficar sem conexões com o servidor e sem a capacidade de processar solicitações adicionais.</span><span class="sxs-lookup"><span data-stu-id="c3f32-124">If you don't close either the response object or the stream, your application can run out of server connections and become unable to process additional requests.</span></span> <span data-ttu-id="c3f32-125">Como o método `WebResponse.Close` chama `Stream.Close` quando ele fecha a resposta, não é necessário chamar `Close` nos objetos de resposta e de fluxo, embora fazer isso não seja prejudicial.</span><span class="sxs-lookup"><span data-stu-id="c3f32-125">Because the `WebResponse.Close` method calls `Stream.Close` when it closes the response, it's not necessary to call `Close` on both the response and stream objects, although doing so isn't harmful.</span></span> <span data-ttu-id="c3f32-126">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="c3f32-126">For example:</span></span>

    ```csharp
    response.Close();
    ```

    ```vb
    response.Close()
    ```

## <a name="example"></a><span data-ttu-id="c3f32-127">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c3f32-127">Example</span></span>

<span data-ttu-id="c3f32-128">O seguinte exemplo de código mostra como criar uma solicitação para um servidor Web e ler os dados na resposta:</span><span class="sxs-lookup"><span data-stu-id="c3f32-128">The following code example shows how to create a request to a web server and read the data in its response:</span></span>

[!code-csharp[RequestDataUsingWebRequest](../../../samples/snippets/csharp/VS_Snippets_Network/RequestDataUsingWebRequest/cs/WebRequestGetExample.cs)]
[!code-vb[RequestDataUsingWebRequest](../../../samples/snippets/visualbasic/VS_Snippets_Network/RequestDataUsingWebRequest/vb/WebRequestGetExample.vb)]

## <a name="see-also"></a><span data-ttu-id="c3f32-129">Confira também</span><span class="sxs-lookup"><span data-stu-id="c3f32-129">See also</span></span>

- [<span data-ttu-id="c3f32-130">Criando solicitações da Internet</span><span class="sxs-lookup"><span data-stu-id="c3f32-130">Creating internet requests</span></span>](creating-internet-requests.md)
- [<span data-ttu-id="c3f32-131">Usando fluxos na rede</span><span class="sxs-lookup"><span data-stu-id="c3f32-131">Using Streams on the network</span></span>](using-streams-on-the-network.md)
- [<span data-ttu-id="c3f32-132">Acessando a Internet por meio de um proxy</span><span class="sxs-lookup"><span data-stu-id="c3f32-132">Accessing the internet through a proxy</span></span>](accessing-the-internet-through-a-proxy.md)
- [<span data-ttu-id="c3f32-133">Solicitando dados</span><span class="sxs-lookup"><span data-stu-id="c3f32-133">Requesting data</span></span>](requesting-data.md)
- [<span data-ttu-id="c3f32-134">Como: enviar dados usando a classe WebRequest</span><span class="sxs-lookup"><span data-stu-id="c3f32-134">How to: Send data by using the WebRequest class</span></span>](how-to-send-data-using-the-webrequest-class.md)
