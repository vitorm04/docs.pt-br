---
title: Usando o protocolo SSL
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Networking
- SSL
- Secure Sockets Layer
- requesting data from Internet, Secure Sockets Layer
- sending data, Secure Sockets Layer
- Network Resources
- data requests, Secure Sockets Layer
- receiving data, Secure Sockets Layer
- Internet, Secure Sockets Layer
ms.assetid: 6e4289e6-d1b7-4e82-ab0d-e83e3b6063ed
ms.openlocfilehash: 9cfa8d6a71898a1d1ea91825ffc9a37f4654ebd5
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64583529"
---
# <a name="using-secure-sockets-layer"></a><span data-ttu-id="035b6-102">Usando o protocolo SSL</span><span class="sxs-lookup"><span data-stu-id="035b6-102">Using Secure Sockets Layer</span></span>
<span data-ttu-id="035b6-103">As classes <xref:System.Net> usam o protocolo SSL para criptografar a conexão para vários protocolos de rede.</span><span class="sxs-lookup"><span data-stu-id="035b6-103">The <xref:System.Net> classes use the Secure Sockets Layer (SSL) to encrypt the connection for several network protocols.</span></span>  
  
 <span data-ttu-id="035b6-104">Para conexões HTTP, as classes <xref:System.Net.WebRequest> e <xref:System.Net.WebResponse> usam o SSL para se comunicarem com hosts Web que dão suporte ao SSL.</span><span class="sxs-lookup"><span data-stu-id="035b6-104">For http connections, the <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes use SSL to communicate with web hosts that support SSL.</span></span> <span data-ttu-id="035b6-105">A decisão de usar o SSL é feita pela classe <xref:System.Net.WebRequest>, com base no URI fornecido.</span><span class="sxs-lookup"><span data-stu-id="035b6-105">The decision to use SSL is made by the <xref:System.Net.WebRequest> class, based on the URI it is given.</span></span> <span data-ttu-id="035b6-106">Se o URI começa com “https:”, o SSL é usado; se o URI começa com “http:”, uma conexão não criptografada é usada.</span><span class="sxs-lookup"><span data-stu-id="035b6-106">If the URI begins with "https:", SSL is used; if the URI begins with "http:", an unencrypted connection is used.</span></span>  
  
 <span data-ttu-id="035b6-107">Para usar o SSL com o protocolo FTP, defina a propriedade <xref:System.Net.FtpWebRequest.EnableSsl> como verdadeiro antes de chamar <xref:System.Net.FtpWebRequest.GetResponse>.</span><span class="sxs-lookup"><span data-stu-id="035b6-107">To use SSL with File Transfer Protocol (FTP), set the <xref:System.Net.FtpWebRequest.EnableSsl> property to true prior to calling <xref:System.Net.FtpWebRequest.GetResponse>.</span></span> <span data-ttu-id="035b6-108">Da mesma forma, para usar o SSL com o protocolo SMTP, defina a propriedade <xref:System.Net.Mail.SmtpClient.EnableSsl> como verdadeira antes de enviar o email.</span><span class="sxs-lookup"><span data-stu-id="035b6-108">Similarly, to use SSL with Simple Mail Transport Protocol (SMTP), set the <xref:System.Net.Mail.SmtpClient.EnableSsl> property to true prior to sending the email.</span></span>  
  
 <span data-ttu-id="035b6-109">A classe <xref:System.Net.Security.SslStream> fornece uma abstração baseada em fluxo para o SSL e oferece muitas maneiras de configurar o handshake SSL.</span><span class="sxs-lookup"><span data-stu-id="035b6-109">The <xref:System.Net.Security.SslStream> class provides a stream-based abstraction for SSL, and offers many ways to configure the SSL handshake.</span></span>  
  
## <a name="example"></a><span data-ttu-id="035b6-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="035b6-110">Example</span></span>  
  
### <a name="code"></a><span data-ttu-id="035b6-111">Código</span><span class="sxs-lookup"><span data-stu-id="035b6-111">Code</span></span>  
  
```vb  
Dim MyURI As String = "https://www.contoso.com/"  
Dim Wreq As WebRequest = WebRequest.Create(MyURI)  
  
Dim serverUri As String = "ftp://ftp.contoso.com/file.txt"  
Dim request As FtpWebRequest = CType(WebRequest.Create(serverUri), FtpWebRequest)  
request.Method = WebRequestMethods.Ftp.DeleteFile  
request.EnableSsl = True  
Dim response As FtpWebResponse = CType(request.GetResponse(), FtpWebResponse)  
```  
  
```csharp  
String MyURI = "https://www.contoso.com/";  
WebRequest WReq = WebRequest.Create(MyURI);  
  
String serverUri = "ftp://ftp.contoso.com/file.txt"  
FtpWebRequest request = (FtpWebRequest)WebRequest.Create(serverUri);  
request.EnableSsl = true;  
request.Method = WebRequestMethods.Ftp.DeleteFile;  
FtpWebResponse response = (FtpWebResponse)request.GetResponse();  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="035b6-112">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="035b6-112">Compiling the Code</span></span>  
 <span data-ttu-id="035b6-113">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="035b6-113">This example requires:</span></span>  
  
- <span data-ttu-id="035b6-114">Referências ao namespace **System.Net**.</span><span class="sxs-lookup"><span data-stu-id="035b6-114">References to the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="035b6-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="035b6-115">See also</span></span>

- [<span data-ttu-id="035b6-116">Segurança na programação de rede</span><span class="sxs-lookup"><span data-stu-id="035b6-116">Security in Network Programming</span></span>](../../../docs/framework/network-programming/security-in-network-programming.md)
- [<span data-ttu-id="035b6-117">Programação de rede no .NET Framework</span><span class="sxs-lookup"><span data-stu-id="035b6-117">Network Programming in the .NET Framework</span></span>](../../../docs/framework/network-programming/index.md)
- [<span data-ttu-id="035b6-118">Seleção e validação de certificado</span><span class="sxs-lookup"><span data-stu-id="035b6-118">Certificate Selection and Validation</span></span>](../../../docs/framework/network-programming/certificate-selection-and-validation.md)
