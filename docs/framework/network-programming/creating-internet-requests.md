---
title: Criando solicitações da Internet
description: Saiba como os aplicativos criam instâncias de WebRequest por meio do método WebRequest. Create, que cria uma classe derivada com base no esquema de URI passado para ela.
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
ms.openlocfilehash: 389c7bf5969eca4322aa680a6f28dec0b899709a
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325631"
---
# <a name="create-internet-requests"></a><span data-ttu-id="da84b-103">Criar solicitações da Internet</span><span class="sxs-lookup"><span data-stu-id="da84b-103">Create internet requests</span></span>

<span data-ttu-id="da84b-104">Os aplicativos criam instâncias <xref:System.Net.WebRequest> por meio do método <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="da84b-104">Applications create <xref:System.Net.WebRequest> instances through the <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="da84b-105"><xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType>é um método estático que cria uma classe derivada de <xref:System.Net.WebRequest> com base no esquema de URI passado para ela.</span><span class="sxs-lookup"><span data-stu-id="da84b-105"><xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> is a static method that creates a class derived from <xref:System.Net.WebRequest> based on the URI scheme passed to it.</span></span>  
  
## <a name="web-file-and-ftp-requests"></a><span data-ttu-id="da84b-106">Solicitações de Web, arquivo e FTP</span><span class="sxs-lookup"><span data-stu-id="da84b-106">Web, file, and FTP requests</span></span>

<span data-ttu-id="da84b-107">.NET Framework fornece a <xref:System.Net.HttpWebRequest> classe, derivada de `WebRequest` , para lidar com solicitações HTTP e HTTPS.</span><span class="sxs-lookup"><span data-stu-id="da84b-107">.NET Framework provides the <xref:System.Net.HttpWebRequest> class, which is derived from `WebRequest`, to handle HTTP and HTTPS requests.</span></span> <span data-ttu-id="da84b-108">Na maioria dos casos, a `WebRequest` classe fornece todas as propriedades necessárias para fazer uma solicitação; no entanto, se necessário, você pode converter `WebRequest` objetos criados pelo `WebRequest.Create` método no `HttpWebRequest` tipo para acessar as propriedades específicas de http da solicitação.</span><span class="sxs-lookup"><span data-stu-id="da84b-108">In most cases, the `WebRequest` class provides all the properties you need to make a request; however, if necessary, you can cast `WebRequest` objects created by the `WebRequest.Create` method to the `HttpWebRequest` type to access the HTTP-specific properties of the request.</span></span> <span data-ttu-id="da84b-109">Da mesma forma, o `HttpWebResponse` objeto manipula as respostas de solicitações HTTP e HTTPS.</span><span class="sxs-lookup"><span data-stu-id="da84b-109">Similarly, the `HttpWebResponse` object handles the responses from HTTP and HTTPS requests.</span></span> <span data-ttu-id="da84b-110">Para acessar as propriedades específicas de HTTP do `HttpWebResponse` objeto, você precisa converter `WebResponse` objetos no `HttpWebResponse` tipo.</span><span class="sxs-lookup"><span data-stu-id="da84b-110">To access the HTTP-specific properties of the `HttpWebResponse` object, you need to cast `WebResponse` objects to the `HttpWebResponse` type.</span></span>  
  
<span data-ttu-id="da84b-111">O .NET Framework também fornece <xref:System.Net.FileWebRequest> as <xref:System.Net.FileWebResponse> classes e para lidar com solicitações de recursos que usam o esquema de URI "file:".</span><span class="sxs-lookup"><span data-stu-id="da84b-111">.NET Framework also provides the <xref:System.Net.FileWebRequest> and <xref:System.Net.FileWebResponse> classes to handle requests for resources that use the "file:" URI scheme.</span></span> <span data-ttu-id="da84b-112">Da mesma forma, as classes <xref:System.Net.FtpWebRequest> e <xref:System.Net.FtpWebResponse> são fornecidas para manipular solicitações para recursos que usam o esquema “ftp:”.</span><span class="sxs-lookup"><span data-stu-id="da84b-112">Likewise, the <xref:System.Net.FtpWebRequest> and <xref:System.Net.FtpWebResponse> classes are provided to handle requests for resources that use the "ftp:" scheme.</span></span> <span data-ttu-id="da84b-113">Se sua solicitação for para um recurso que usa qualquer um desses esquemas, você poderá usar o `WebRequest.Create` método para obter um objeto com o qual fazer sua solicitação.</span><span class="sxs-lookup"><span data-stu-id="da84b-113">If your request is for a resource that uses any of these schemes, you can use the `WebRequest.Create` method to obtain an object with which to make your request.</span></span>  
  
<span data-ttu-id="da84b-114">Para lidar com solicitações que usam outros protocolos de nível de aplicativo, implemente classes específicas de protocolo derivadas de `WebRequest` e `WebResponse` .</span><span class="sxs-lookup"><span data-stu-id="da84b-114">To handle requests that use other application-level protocols, implement protocol-specific classes derived from `WebRequest` and `WebResponse`.</span></span> <span data-ttu-id="da84b-115">Para obter mais informações, consulte [Programming Pluggable Protocols](programming-pluggable-protocols.md).</span><span class="sxs-lookup"><span data-stu-id="da84b-115">For more information, see [Programming Pluggable Protocols](programming-pluggable-protocols.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da84b-116">Veja também</span><span class="sxs-lookup"><span data-stu-id="da84b-116">See also</span></span>

- [<span data-ttu-id="da84b-117">Como solicitar dados usando a classe WebRequest</span><span class="sxs-lookup"><span data-stu-id="da84b-117">How to: Request Data Using the WebRequest Class</span></span>](how-to-request-data-using-the-webrequest-class.md)
- [<span data-ttu-id="da84b-118">Solicitando dados</span><span class="sxs-lookup"><span data-stu-id="da84b-118">Requesting Data</span></span>](requesting-data.md)
