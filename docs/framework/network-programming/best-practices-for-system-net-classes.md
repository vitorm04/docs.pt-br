---
title: Melhores práticas para classes System.Net
ms.date: 03/30/2017
helpviewer_keywords:
- sending data, best practices
- requesting data from Internet, best practices
- WebRequest class, best practices
- data requests, best practices
- WebResponse class, best practices
- best practices, data requests
- receiving data, best practices
ms.assetid: 716decc6-5952-47b7-9c5a-ba6fc5698684
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 987e2294f1e34eb3a4da1e31285868877338ccf4
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/29/2018
ms.locfileid: "47192191"
---
# <a name="best-practices-for-systemnet-classes"></a><span data-ttu-id="c56ed-102">Melhores práticas para classes System.Net</span><span class="sxs-lookup"><span data-stu-id="c56ed-102">Best Practices for System.Net Classes</span></span>
<span data-ttu-id="c56ed-103">As seguintes recomendações ajudarão você a usar as classes contidas em <xref:System.Net> para seu melhor proveito:</span><span class="sxs-lookup"><span data-stu-id="c56ed-103">The following recommendations will help you use the classes contained in <xref:System.Net> to their best advantage:</span></span>  
  
-   <span data-ttu-id="c56ed-104">Para obter as melhores práticas do protocolo TLS, confira [Melhores práticas do protocolo TLS com o .NET Framework](tls.md).</span><span class="sxs-lookup"><span data-stu-id="c56ed-104">For Transport Layer Security (TLS) best practices, see [Transport Layer Security (TLS) best practices with .NET Framework](tls.md).</span></span>

-   <span data-ttu-id="c56ed-105">Use <xref:System.Net.WebRequest> e <xref:System.Net.WebResponse> sempre que possível, em vez da conversão de tipo para classes descendentes.</span><span class="sxs-lookup"><span data-stu-id="c56ed-105">Use <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> whenever possible instead of type casting to descendant classes.</span></span> <span data-ttu-id="c56ed-106">Os aplicativos que usam **WebRequest** e **WebResponse** podem aproveitar os novos protocolos da Internet sem a necessidade de alterações de código extensas.</span><span class="sxs-lookup"><span data-stu-id="c56ed-106">Applications that use **WebRequest** and **WebResponse** can take advantage of new Internet protocols without needing extensive code changes.</span></span>  
  
-   <span data-ttu-id="c56ed-107">Ao escrever aplicativos ASP.NET executados em um servidor usando as classes **System.Net**, geralmente é melhor, de um ponto de vista de desempenho, usar os métodos assíncronos para <xref:System.Net.WebRequest.GetResponse%2A> e <xref:System.Net.WebResponse.GetResponseStream%2A>.</span><span class="sxs-lookup"><span data-stu-id="c56ed-107">When writing ASP.NET applications that run on a server using the **System.Net** classes, it is often better, from a performance standpoint, to use the asynchronous methods for <xref:System.Net.WebRequest.GetResponse%2A> and <xref:System.Net.WebResponse.GetResponseStream%2A>.</span></span>  
  
-   <span data-ttu-id="c56ed-108">O número de conexões abertas para um recurso da Internet pode ter um impacto significativo no desempenho da rede e na taxa de transferência.</span><span class="sxs-lookup"><span data-stu-id="c56ed-108">The number of connections opened to an Internet resource can have a significant impact on network performance and throughput.</span></span> <span data-ttu-id="c56ed-109">**System.Net** usa duas conexões por aplicativo e host, por padrão.</span><span class="sxs-lookup"><span data-stu-id="c56ed-109">**System.Net** uses two connections per application per host by default.</span></span> <span data-ttu-id="c56ed-110">A configuração da propriedade <xref:System.Net.ServicePoint.ConnectionLimit%2A> no <xref:System.Net.ServicePoint> para o aplicativo pode aumentar esse número para um host específico.</span><span class="sxs-lookup"><span data-stu-id="c56ed-110">Setting the <xref:System.Net.ServicePoint.ConnectionLimit%2A> property in the <xref:System.Net.ServicePoint> for your application can increase this number for a particular host.</span></span> <span data-ttu-id="c56ed-111">A configuração da propriedade <xref:System.Net.ServicePointManager.DefaultPersistentConnectionLimit?displayProperty=nameWithType> pode aumentar esse padrão para todos os hosts.</span><span class="sxs-lookup"><span data-stu-id="c56ed-111">Setting the <xref:System.Net.ServicePointManager.DefaultPersistentConnectionLimit?displayProperty=nameWithType> property can increase this default for all hosts.</span></span>  
  
-   <span data-ttu-id="c56ed-112">Ao gravar protocolos no nível do soquete, tente usar <xref:System.Net.Sockets.TcpClient> ou <xref:System.Net.Sockets.UdpClient> sempre que possível, em vez de gravar diretamente em um <xref:System.Net.Sockets.Socket>.</span><span class="sxs-lookup"><span data-stu-id="c56ed-112">When writing socket-level protocols, try to use <xref:System.Net.Sockets.TcpClient> or <xref:System.Net.Sockets.UdpClient> whenever possible instead of writing directly to a <xref:System.Net.Sockets.Socket>.</span></span> <span data-ttu-id="c56ed-113">Essas duas classes de cliente encapsulam a criação de soquetes TCP e UDP sem a necessidade de lidar com os detalhes da conexão.</span><span class="sxs-lookup"><span data-stu-id="c56ed-113">These two client classes encapsulate the creation of TCP and UDP sockets without requiring you to handle the details of the connection.</span></span>  
  
-   <span data-ttu-id="c56ed-114">Ao acessar sites que exigem credenciais, use a classe <xref:System.Net.CredentialCache> para criar um cache de credenciais, em vez de fornecê-las com cada solicitação.</span><span class="sxs-lookup"><span data-stu-id="c56ed-114">When accessing sites that require credentials, use the <xref:System.Net.CredentialCache> class to create a cache of credentials rather than supplying them with every request.</span></span> <span data-ttu-id="c56ed-115">A classe **CredentialCache** procura o cache para localizar as credenciais apropriadas a serem apresentadas com uma solicitação, liberando-o da responsabilidade de criar e apresentar credenciais baseadas na URL.</span><span class="sxs-lookup"><span data-stu-id="c56ed-115">The **CredentialCache** class searches the cache to find the appropriate credential to present with a request, relieving you of the responsibility of creating and presenting credentials based on the URL.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c56ed-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c56ed-116">See Also</span></span>  
 [<span data-ttu-id="c56ed-117">Programação de rede no .NET Framework</span><span class="sxs-lookup"><span data-stu-id="c56ed-117">Network Programming in the .NET Framework</span></span>](../../../docs/framework/network-programming/index.md)
