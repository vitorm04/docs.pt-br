---
title: Como solicitar dados usando a classe WebRequest
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "8"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: bd714a9e006f87a817ca931757aaaaed920f50f7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-request-data-using-the-webrequest-class"></a>Como solicitar dados usando a classe WebRequest
O procedimento a seguir descreve as etapas usadas para solicitar um recurso de um servidor, por exemplo, uma página da Web ou arquivo. O recurso deve ser identificado por um URI.  
  
### <a name="to-request-data-from-a-host-server"></a>Para solicitar dados de um servidor host  
  
1.  Criar uma instância de <xref:System.Net.WebRequest> chamando <xref:System.Net.WebRequest.Create%2A> com o URI do recurso.  
  
    ```csharp  
    WebRequest request = WebRequest.Create("http://www.contoso.com/");  
    ```  
  
    ```vb  
    Dim request as WebRequest = WebRequest.Create("http://www.contoso.com/")  
    ```  
  
    > [!NOTE]
    >  O .NET Framework fornece classes específicas de protocolo derivadas de **WebRequest** e **WebResponse** para URIs que começam com "http:", "https:", "ftp:" e "file:". Para acessar recursos usando outros protocolos, você deve implementar classes específicas de protocolo derivadas de **WebRequest** e **WebResponse**. Para obter mais informações, consulte [Programando protocolos conectáveis](../../../docs/framework/network-programming/programming-pluggable-protocols.md).  
  
2.  Definir quaisquer valores de propriedade dos quais você precisa na **WebRequest**. Por exemplo, para habilitar a autenticação, defina a propriedade **Credentials** para uma instância da classe <xref:System.Net.NetworkCredential>.  
  
    ```csharp  
    request.Credentials = CredentialCache.DefaultCredentials;  
    ```  
  
    ```vb  
    request.Credentials = CredentialCache.DefaultCredentials  
    ```  
  
     Na maioria dos casos, a classe **WebRequest** é suficiente para receber dados. No entanto, se você precisar definir propriedades específicas de protocolo, você deverá converter a **WebRequest** para o tipo específico do protocolo. Por exemplo, acessar propriedades HTTP específicas de <xref:System.Net.HttpWebRequest>, converta a **WebRequest** para uma referência de **HttpWebRequest**. O exemplo de código a seguir mostra como definir a propriedade <xref:System.Net.HttpWebRequest.UserAgent%2A> específica de HTTP.  
  
    ```csharp  
    ((HttpWebRequest)request).UserAgent = ".NET Framework Example Client";  
    ```  
  
    ```vb  
    Ctype(request,HttpWebRequest).UserAgent = ".NET Framework Example Client"  
    ```  
  
3.  Para enviar a solicitação para o servidor, chame <xref:System.Net.HttpWebRequest.GetResponse%2A>. O tipo real do objeto **WebResponse** retornado é determinado pelo esquema do URI solicitado.  
  
    ```csharp  
    WebResponse response = request.GetResponse();  
    ```  
  
    ```vb  
    Dim response As WebResponse = request.GetResponse()  
    ```  
  
    > [!NOTE]
    >  Depois de terminar de usar um objeto <xref:System.Net.WebResponse>, você deve fechá-lo chamando o método <xref:System.Net.WebResponse.Close%2A>. Alternativamente, se você obteve o fluxo de resposta do objeto de resposta, você pode fechar o fluxo chamando o método <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType>. Se você não fechar a resposta ou o fluxo, o seu aplicativo poderá ficar sem conexões para o servidor e, nesse caso, ficará incapaz de processar solicitações adicionais.  
  
4.  Você pode acessar as propriedades da **WebResponse** ou converter a **WebResponse** para uma instância específica de protocolo para ler as propriedades específicas de protocolo. Por exemplo, para acessar as propriedades específicas de HTTP de <xref:System.Net.HttpWebResponse>, converta a **WebResponse** para uma referência de **HttpWebResponse**. O exemplo de código a seguir mostra como exibir as informações de status enviadas com uma resposta.  
  
    ```csharp  
    Console.WriteLine (((HttpWebResponse)response).StatusDescription);  
    ```  
  
    ```vb  
    Console.WriteLine(CType(response,HttpWebResponse).StatusDescription)  
    ```  
  
5.  Para obter o fluxo que contém os dados de resposta enviados pelo servidor, use o método <xref:System.Net.HttpWebResponse.GetResponseStream%2A> da **WebResponse**.  
  
    ```csharp  
    Stream dataStream = response.GetResponseStream ();  
    ```  
  
    ```vb  
    Dim dataStream As Stream = response.GetResponseStream()  
    ```  
  
6.  Depois de ler os dados da resposta ou você deve fechar o fluxo de resposta usando o método **Stream.Close** ou fechar a resposta usando o método **WebResponse.Close**. Não é necessário chamar o método **Close** tanto no fluxo de resposta quanto na **WebResponse**, mas fazer isso não é prejudicial. **WebResponse.Close** chama **Stream.Close** ao fechar a resposta.  
  
    ```csharp  
    response.Close();  
    ```  
  
    ```vb  
    response.Close()  
    ```  
  
## <a name="example"></a>Exemplo  
  
```csharp  
using System;  
using System.IO;  
using System.Net;  
using System.Text;  
  
namespace Examples.System.Net  
{  
    public class WebRequestGetExample  
    {  
        public static void Main ()  
        {  
            // Create a request for the URL.   
            WebRequest request = WebRequest.Create (  
              "http://www.contoso.com/default.html");  
            // If required by the server, set the credentials.  
            request.Credentials = CredentialCache.DefaultCredentials;  
            // Get the response.  
            WebResponse response = request.GetResponse ();  
            // Display the status.  
            Console.WriteLine (((HttpWebResponse)response).StatusDescription);  
            // Get the stream containing content returned by the server.  
            Stream dataStream = response.GetResponseStream ();  
            // Open the stream using a StreamReader for easy access.  
            StreamReader reader = new StreamReader (dataStream);  
            // Read the content.  
            string responseFromServer = reader.ReadToEnd ();  
            // Display the content.  
            Console.WriteLine (responseFromServer);  
            // Clean up the streams and the response.  
            reader.Close ();  
            response.Close ();  
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
  
## <a name="see-also"></a>Consulte também  
 [Criar solicitações de Internet](../../../docs/framework/network-programming/creating-internet-requests.md)  
 [Usando fluxos na rede](../../../docs/framework/network-programming/using-streams-on-the-network.md)  
 [Acessando a Internet por meio de um proxy](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)  
 [Solicitando dados](../../../docs/framework/network-programming/requesting-data.md)  
 [Como enviar dados usando a classe WebRequest](../../../docs/framework/network-programming/how-to-send-data-using-the-webrequest-class.md)
