---
title: Criando solicitações da Internet
ms.date: 03/30/2017
helpviewer_keywords:
- WebRequest class, sending and receiving data
- Networking
- HttpWebResponse class, sending and receiving data
- requesting data from Internet, creating requests
- Network Resources
- Internet, requesting data
- data requests, creating requests
ms.assetid: faab683e-3f1e-4eee-b5e9-59f7245033d5
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 201bc5e92aeedcbfe2f710681cf3bbc773a11424
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47193372"
---
# <a name="creating-internet-requests"></a><span data-ttu-id="37f08-102">Criando solicitações da Internet</span><span class="sxs-lookup"><span data-stu-id="37f08-102">Creating Internet Requests</span></span>
<span data-ttu-id="37f08-103">Os aplicativos criam instâncias <xref:System.Net.WebRequest> por meio do método <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="37f08-103">Applications create <xref:System.Net.WebRequest> instances through the <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="37f08-104">Este é um método estático que cria uma classe derivada de **WebRequest**, com base no esquema de URI passado para ele.</span><span class="sxs-lookup"><span data-stu-id="37f08-104">This is a static method that creates a class derived from **WebRequest** based on the URI scheme passed to it.</span></span>  
  
## <a name="web-file-and-ftp-requests"></a><span data-ttu-id="37f08-105">Solicitações da Web, de arquivo e de FTP</span><span class="sxs-lookup"><span data-stu-id="37f08-105">Web, File and FTP Requests</span></span>  
 <span data-ttu-id="37f08-106">O .NET Framework fornece a classe <xref:System.Net.HttpWebRequest>, que é derivada de **WebRequest**, para manipular solicitações HTTP e HTTPS.</span><span class="sxs-lookup"><span data-stu-id="37f08-106">The .NET Framework provides the <xref:System.Net.HttpWebRequest> class, which is derived from **WebRequest**, to handle HTTP and HTTPS requests.</span></span> <span data-ttu-id="37f08-107">Na maioria dos casos, a classe **WebRequest** fornece todas as propriedades necessárias para fazer uma solicitação; no entanto, se necessário, é possível converter objetos **WebRequest** criados pelo método **WebRequest.Create** no tipo **HttpWebRequest** para acessar as propriedades específicas de HTTP da solicitação.</span><span class="sxs-lookup"><span data-stu-id="37f08-107">In most cases, the **WebRequest** class provides all the properties you need to make a request; however, if necessary, you can cast **WebRequest** objects created by the **WebRequest.Create** method to the **HttpWebRequest** type to access the HTTP-specific properties of the request.</span></span> <span data-ttu-id="37f08-108">Da mesma forma, o objeto **HttpWebResponse** manipula as respostas das solicitações HTTP e HTTPS.</span><span class="sxs-lookup"><span data-stu-id="37f08-108">Similarly, the **HttpWebResponse** object handles the responses from HTTP and HTTPS requests.</span></span> <span data-ttu-id="37f08-109">Para acessar as propriedades específicas de HTTP do objeto **HttpWebResponse**, é necessário converter objetos **WebResponse** no tipo **HttpWebResponse**.</span><span class="sxs-lookup"><span data-stu-id="37f08-109">To access the HTTP-specific properties of the **HttpWebResponse** object, you need to cast **WebResponse** objects to the **HttpWebResponse** type.</span></span>  
  
 <span data-ttu-id="37f08-110">O .NET Framework também fornece as classes <xref:System.Net.FileWebRequest> e <xref:System.Net.FileWebResponse> para manipular solicitações para recursos que usam o esquema de URI “file:”.</span><span class="sxs-lookup"><span data-stu-id="37f08-110">The .NET Framework also provides the <xref:System.Net.FileWebRequest> and <xref:System.Net.FileWebResponse> classes to handle requests for resources that use the "file:" URI scheme.</span></span> <span data-ttu-id="37f08-111">Da mesma forma, as classes <xref:System.Net.FtpWebRequest> e <xref:System.Net.FtpWebResponse> são fornecidas para manipular solicitações para recursos que usam o esquema “ftp:”.</span><span class="sxs-lookup"><span data-stu-id="37f08-111">Likewise, the <xref:System.Net.FtpWebRequest> and <xref:System.Net.FtpWebResponse> classes are provided to handle requests for resources that use the "ftp:" scheme.</span></span> <span data-ttu-id="37f08-112">Se a solicitação for para um recurso que usa um desses esquemas, use o método **WebRequest.Create** para obter um objeto com o qual a solicitação será feita.</span><span class="sxs-lookup"><span data-stu-id="37f08-112">If your request is for a resource that uses any of these schemes, you can use the **WebRequest.Create** method to obtain an object with which to make your request.</span></span>  
  
 <span data-ttu-id="37f08-113">Para manipular solicitações que usam outros protocolos no nível de aplicativo, é necessário implementar classes específicas ao protocolo derivadas de **WebRequest** e **WebResponse**.</span><span class="sxs-lookup"><span data-stu-id="37f08-113">To handle requests that use other application-level protocols, you need to implement protocol-specific classes derived from **WebRequest** and **WebResponse**.</span></span> <span data-ttu-id="37f08-114">Para obter mais informações, consulte [Programando protocolos conectáveis](../../../docs/framework/network-programming/programming-pluggable-protocols.md).</span><span class="sxs-lookup"><span data-stu-id="37f08-114">For more information, see [Programming Pluggable Protocols](../../../docs/framework/network-programming/programming-pluggable-protocols.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37f08-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="37f08-115">See Also</span></span>  
 [<span data-ttu-id="37f08-116">Como solicitar dados usando a classe WebRequest</span><span class="sxs-lookup"><span data-stu-id="37f08-116">How to: Request Data Using the WebRequest Class</span></span>](../../../docs/framework/network-programming/how-to-request-data-using-the-webrequest-class.md)  
 [<span data-ttu-id="37f08-117">Solicitando dados</span><span class="sxs-lookup"><span data-stu-id="37f08-117">Requesting Data</span></span>](../../../docs/framework/network-programming/requesting-data.md)
