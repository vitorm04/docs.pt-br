---
title: Como enviar dados usando a classe WebRequest
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WebRequest class, sending data to a host
- Sending data to a host, using WebRequest class
ms.assetid: 66686878-38ac-4aa6-bf42-ffb568ffc459
ms.openlocfilehash: 1f10c5e0c6c266b7b31d658ec561bd8d6d85697b
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53129461"
---
# <a name="how-to-send-data-using-the-webrequest-class"></a>Como enviar dados usando a classe WebRequest
O procedimento a seguir descreve as etapas usadas para enviar dados para um servidor. Esse procedimento normalmente é usado para enviar dados para uma página da Web.  
  
### <a name="to-send-data-to-a-host-server"></a>Para enviar dados para um servidor de host  
  
1.  Criar uma instância <xref:System.Net.WebRequest> chamando <xref:System.Net.WebRequest.Create%2A> com o URI do recurso que aceita dados, por exemplo, um script ou a página ASP.NET.  
  
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
  
     Na maioria dos casos, a própria instância de **WebRequest** é suficiente para enviar dados. No entanto, se você precisar definir propriedades específicas de protocolo, você deverá converter a **WebRequest** para o tipo específico do protocolo. Por exemplo, acessar propriedades HTTP específicas de <xref:System.Net.HttpWebRequest>, converta a **WebRequest** para uma referência de **HttpWebRequest**. O exemplo de código a seguir mostra como definir a propriedade <xref:System.Net.HttpWebRequest.UserAgent%2A> específica de HTTP.  
  
    ```csharp  
    ((HttpWebRequest)request).UserAgent = ".NET Framework Example Client";  
    ```  
  
    ```vb  
    Ctype(request,HttpWebRequest).UserAgent = ".NET Framework Example Client"  
    ```  
  
3.  Especifique um método de protocolo que permite que os dados sejam enviados com uma solicitação, tal como o método HTTP **POST**.  
  
    ```csharp  
    request.Method = "POST";  
    ```  
  
    ```vb  
    request.Method = "POST"  
    ```  
  
4.  Defina a propriedade **ContentLength**.  
  
    ```csharp  
    request.ContentLength = byteArray.Length;  
    ```  
  
    ```vb  
    request.ContentLength = byteArray.Length  
    ```  
  
5.  Defina a propriedade **ContentType** para um valor apropriado.  
  
    ```csharp  
    request.ContentType = "application/x-www-form-urlencoded";  
    ```  
  
    ```vb  
    request.ContentType = "application/x-www-form-urlencoded"  
    ```  
  
6.  Obtenha o fluxo que mantém dados de solicitação chamando o método <xref:System.Net.WebRequest.GetRequestStream%2A>.  
  
    ```csharp  
    Stream dataStream = request.GetRequestStream ();  
    ```  
  
    ```vb  
    Stream dataStream = request.GetRequestStream ()  
    ```  
  
7.  Grave os dados no objeto <xref:System.IO.Stream> retornado por este método.  
  
    ```csharp  
    dataStream.Write (byteArray, 0, byteArray.Length);  
    ```  
  
    ```vb  
    dataStream.Write (byteArray, 0, byteArray.Length)  
    ```  
  
8.  Feche o fluxo da solicitação chamando o método **Stream.Close**.  
  
    ```csharp  
    dataStream.Close ();  
    ```  
  
    ```vb  
    dataStream.Close ()  
    ```  
  
9. Envie a solicitação para o servidor chamando <xref:System.Net.WebRequest.GetResponse%2A>. Esse método retorna um objeto que contém a resposta do servidor. O tipo do objeto <xref:System.Net.WebResponse> retornado é determinado pelo esquema do URI da solicitação.  
  
    ```csharp  
    WebResponse response = request.GetResponse();  
    ```  
  
    ```vb  
    Dim response As WebResponse = request.GetResponse()  
    ```  
  
    > [!NOTE]
    >  Depois de terminar de usar um objeto <xref:System.Net.WebResponse>, você deve fechá-lo chamando o método <xref:System.Net.WebResponse.Close%2A>. Alternativamente, se você obteve o fluxo de resposta do objeto de resposta, você pode fechar o fluxo chamando o método <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType>. Se você não fechar a resposta ou o fluxo, o seu aplicativo poderá ficar sem conexões para o servidor e, nesse caso, ficará incapaz de processar solicitações adicionais.  
  
10. Você pode acessar as propriedades da **WebResponse** ou converter a **WebResponse** para uma instância específica de protocolo para ler as propriedades específicas de protocolo. Por exemplo, para acessar as propriedades específicas de HTTP de <xref:System.Net.HttpWebResponse>, converta a **WebResponse** para uma referência de **HttpWebResponse**.  
  
    ```csharp  
    Console.WriteLine (((HttpWebResponse)response).StatusDescription);  
    ```  
  
    ```vb  
    Console.WriteLine(CType(response, HttpWebResponse).StatusDescription)  
    ```  
  
11. Para obter o fluxo que contém os dados de resposta enviados pelo servidor, chame o método <xref:System.Net.WebResponse.GetResponseStream%2A> da **WebResponse**.  
  
    ```csharp  
    Stream data = response.GetResponseStream;  
    ```  
  
    ```vb  
    Dim data As Stream = response.GetResponseStream  
    ```  
  
12. Depois de ler os dados da resposta ou você deve fechar o fluxo de resposta usando o método **Stream.Close** ou fechar a resposta usando o método **WebResponse.Close**. Não é necessário chamar o método **Close** tanto no fluxo de resposta quanto na **WebResponse**, mas fazer isso não é prejudicial.  
  
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
    public class WebRequestPostExample  
    {  
        public static void Main ()  
        {  
            // Create a request using a URL that can receive a post.   
            WebRequest request = WebRequest.Create ("http://www.contoso.com/PostAccepter.aspx ");  
            // Set the Method property of the request to POST.  
            request.Method = "POST";  
            // Create POST data and convert it to a byte array.  
            string postData = "This is a test that posts this string to a Web server.";  
            byte[] byteArray = Encoding.UTF8.GetBytes (postData);  
            // Set the ContentType property of the WebRequest.  
            request.ContentType = "application/x-www-form-urlencoded";  
            // Set the ContentLength property of the WebRequest.  
            request.ContentLength = byteArray.Length;  
            // Get the request stream.  
            Stream dataStream = request.GetRequestStream ();  
            // Write the data to the request stream.  
            dataStream.Write (byteArray, 0, byteArray.Length);  
            // Close the Stream object.  
            dataStream.Close ();  
            // Get the response.  
            WebResponse response = request.GetResponse ();  
            // Display the status.  
            Console.WriteLine (((HttpWebResponse)response).StatusDescription);  
            // Get the stream containing content returned by the server.  
            dataStream = response.GetResponseStream ();  
            // Open the stream using a StreamReader for easy access.  
            StreamReader reader = new StreamReader (dataStream);  
            // Read the content.  
            string responseFromServer = reader.ReadToEnd ();  
            // Display the content.  
            Console.WriteLine (responseFromServer);  
            // Clean up the streams.  
            reader.Close ();  
            dataStream.Close ();  
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
    Public Class WebRequestPostExample  
  
        Public Shared Sub Main()  
            ' Create a request using a URL that can receive a post.   
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
            ' Close the Stream object.  
            dataStream.Close()  
            ' Get the response.  
            Dim response As WebResponse = request.GetResponse()  
            ' Display the status.  
            Console.WriteLine(CType(response, HttpWebResponse).StatusDescription)  
            ' Get the stream containing content returned by the server.  
            dataStream = response.GetResponseStream()  
            ' Open the stream using a StreamReader for easy access.  
            Dim reader As New StreamReader(dataStream)  
            ' Read the content.  
            Dim responseFromServer As String = reader.ReadToEnd()  
            ' Display the content.  
            Console.WriteLine(responseFromServer)  
            ' Clean up the streams.  
            reader.Close()  
            dataStream.Close()  
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
 [Como solicitar dados usando a classe WebRequest](../../../docs/framework/network-programming/how-to-request-data-using-the-webrequest-class.md)
