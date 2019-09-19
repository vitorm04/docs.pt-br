---
title: 'Como: Solicitar dados usando a classe WebRequest'
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
ms.openlocfilehash: e670a2a503ce704eff847e9e0b3ee340ab52fe62
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71048162"
---
# <a name="how-to-request-data-by-using-the-webrequest-class"></a>Como: Solicitar dados usando a classe WebRequest

O procedimento a seguir descreve as etapas usadas para solicitar um recurso, como uma página da Web ou um arquivo, de um servidor. O recurso deve ser identificado por um URI.

## <a name="to-request-data-from-a-host-server"></a>Para solicitar dados de um servidor host

1. Crie uma instância de <xref:System.Net.WebRequest> chamando <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> com o URI de um recurso. Por exemplo:

    ```csharp
    WebRequest request = WebRequest.Create("https://docs.microsoft.com");
    ```

    ```vb
    Dim request as WebRequest = WebRequest.Create("https://docs.microsoft.com")
    ```

    > [!NOTE]
    > O .NET Framework fornece classes específicas de protocolo derivadas das classes <xref:System.Net.WebRequest> e <xref:System.Net.WebResponse> para URIs que começam com *http:* , *https:* , *ftp:* e *file:* .

    Caso precise definir ou ler propriedades específica de protocolo, converta o objeto <xref:System.Net.WebRequest> ou <xref:System.Net.WebResponse> em um tipo de objeto específico de protocolo. Para obter mais informações, confira [Programando protocolos conectáveis](programming-pluggable-protocols.md).

2. Defina os valores de propriedade necessários no objeto `WebRequest`. Por exemplo, para habilitar a autenticação, defina a propriedade <xref:System.Net.WebRequest.Credentials%2A?displayProperty=nameWithType> como uma instância da classe <xref:System.Net.NetworkCredential>:

    ```csharp
    request.Credentials = CredentialCache.DefaultCredentials;
    ```

    ```vb
    request.Credentials = CredentialCache.DefaultCredentials
    ```

3. Envie a solicitação para o servidor chamando <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType>. Esse método retorna um objeto que contém a resposta do servidor. O tipo do objeto <xref:System.Net.WebResponse> retornado é determinado pelo esquema do URI da solicitação. Por exemplo:

    ```csharp
    WebResponse response = request.GetResponse();
    ```

    ```vb
    Dim response As WebResponse = request.GetResponse()
    ```

4. Você pode acessar as propriedades do objeto `WebResponse` ou convertê-lo em uma instância específica de protocolo para ler propriedades específicas de protocolo.

    Por exemplo, para acessar as propriedades específicas de HTTP de <xref:System.Net.HttpWebResponse>, converta o objeto `WebResponse` em uma referência `HttpWebResponse`. O seguinte exemplo de código mostra como exibir a propriedade <xref:System.Net.HttpWebResponse.StatusDescription%2A?displayProperty=nameWithType> específica de HTTP enviada com uma resposta:

    ```csharp
    Console.WriteLine (((HttpWebResponse)response).StatusDescription);
    ```

    ```vb
    Console.WriteLine(CType(response,HttpWebResponse).StatusDescription)
    ```

5. Para obter o fluxo que contém os dados de resposta enviados pelo servidor, chame o método <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType>. Por exemplo:

    ```csharp
    Stream dataStream = response.GetResponseStream();
    ```

    ```vb
    Dim dataStream As Stream = response.GetResponseStream()
    ```

6. Depois de ler os dados do objeto de resposta, feche-o com o método <xref:System.Net.WebResponse.Close%2A?displayProperty=nameWithType> ou feche o fluxo de resposta com o método <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType>. Se você não fechar o objeto de resposta ou o fluxo, seu aplicativo poderá ficar sem conexões com o servidor e sem a capacidade de processar solicitações adicionais. Como o método `WebResponse.Close` chama `Stream.Close` quando ele fecha a resposta, não é necessário chamar `Close` nos objetos de resposta e de fluxo, embora fazer isso não seja prejudicial. Por exemplo:

    ```csharp
    response.Close();
    ```

    ```vb
    response.Close()
    ```

## <a name="example"></a>Exemplo

O seguinte exemplo de código mostra como criar uma solicitação para um servidor Web e ler os dados na resposta:

[!code-csharp[RequestDataUsingWebRequest](../../../samples/snippets/csharp/VS_Snippets_Network/RequestDataUsingWebRequest/cs/WebRequestGetExample.cs)]
[!code-vb[RequestDataUsingWebRequest](../../../samples/snippets/visualbasic/VS_Snippets_Network/RequestDataUsingWebRequest/vb/WebRequestGetExample.vb)]

## <a name="see-also"></a>Consulte também

- [Criando solicitações da Internet](creating-internet-requests.md)
- [Usando fluxos na rede](using-streams-on-the-network.md)
- [Acessando a Internet por meio de um proxy](accessing-the-internet-through-a-proxy.md)
- [Solicitando dados](requesting-data.md)
- [Como: Enviar dados usando a classe WebRequest](how-to-send-data-using-the-webrequest-class.md)
