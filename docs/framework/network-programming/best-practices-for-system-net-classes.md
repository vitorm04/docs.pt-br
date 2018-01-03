---
title: "Melhores práticas para classes System.Net"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- sending data, best practices
- requesting data from Internet, best practices
- WebRequest class, best practices
- data requests, best practices
- WebResponse class, best practices
- best practices, data requests
- receiving data, best practices
ms.assetid: 716decc6-5952-47b7-9c5a-ba6fc5698684
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 83254955138c99ec0187e5cf74566266c2ecb303
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="best-practices-for-systemnet-classes"></a><span data-ttu-id="ebd8a-102">Melhores práticas para classes System.Net</span><span class="sxs-lookup"><span data-stu-id="ebd8a-102">Best Practices for System.Net Classes</span></span>
<span data-ttu-id="ebd8a-103">As seguintes recomendações ajudarão você a usar as classes contidas em <xref:System.Net> para seu melhor proveito:</span><span class="sxs-lookup"><span data-stu-id="ebd8a-103">The following recommendations will help you use the classes contained in <xref:System.Net> to their best advantage:</span></span>  
  
-   <span data-ttu-id="ebd8a-104">Use <xref:System.Net.WebRequest> e <xref:System.Net.WebResponse> sempre que possível, em vez da conversão de tipo para classes descendentes.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-104">Use <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> whenever possible instead of type casting to descendant classes.</span></span> <span data-ttu-id="ebd8a-105">Os aplicativos que usam **WebRequest** e **WebResponse** podem aproveitar os novos protocolos da Internet sem a necessidade de alterações de código extensas.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-105">Applications that use **WebRequest** and **WebResponse** can take advantage of new Internet protocols without needing extensive code changes.</span></span>  
  
-   <span data-ttu-id="ebd8a-106">Ao escrever aplicativos ASP.NET executados em um servidor usando as classes **System.Net**, geralmente é melhor, de um ponto de vista de desempenho, usar os métodos assíncronos para <xref:System.Net.WebRequest.GetResponse%2A> e <xref:System.Net.WebResponse.GetResponseStream%2A>.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-106">When writing ASP.NET applications that run on a server using the **System.Net** classes, it is often better, from a performance standpoint, to use the asynchronous methods for <xref:System.Net.WebRequest.GetResponse%2A> and <xref:System.Net.WebResponse.GetResponseStream%2A>.</span></span>  
  
-   <span data-ttu-id="ebd8a-107">O número de conexões abertas para um recurso da Internet pode ter um impacto significativo no desempenho da rede e na taxa de transferência.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-107">The number of connections opened to an Internet resource can have a significant impact on network performance and throughput.</span></span> <span data-ttu-id="ebd8a-108">**System.Net** usa duas conexões por aplicativo e host, por padrão.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-108">**System.Net** uses two connections per application per host by default.</span></span> <span data-ttu-id="ebd8a-109">A configuração da propriedade <xref:System.Net.ServicePoint.ConnectionLimit%2A> no <xref:System.Net.ServicePoint> para o aplicativo pode aumentar esse número para um host específico.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-109">Setting the <xref:System.Net.ServicePoint.ConnectionLimit%2A> property in the <xref:System.Net.ServicePoint> for your application can increase this number for a particular host.</span></span> <span data-ttu-id="ebd8a-110">A configuração da propriedade <xref:System.Net.ServicePointManager.DefaultPersistentConnectionLimit?displayProperty=nameWithType> pode aumentar esse padrão para todos os hosts.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-110">Setting the <xref:System.Net.ServicePointManager.DefaultPersistentConnectionLimit?displayProperty=nameWithType> property can increase this default for all hosts.</span></span>  
  
-   <span data-ttu-id="ebd8a-111">Ao gravar protocolos no nível do soquete, tente usar <xref:System.Net.Sockets.TcpClient> ou <xref:System.Net.Sockets.UdpClient> sempre que possível, em vez de gravar diretamente em um <xref:System.Net.Sockets.Socket>.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-111">When writing socket-level protocols, try to use <xref:System.Net.Sockets.TcpClient> or <xref:System.Net.Sockets.UdpClient> whenever possible instead of writing directly to a <xref:System.Net.Sockets.Socket>.</span></span> <span data-ttu-id="ebd8a-112">Essas duas classes de cliente encapsulam a criação de soquetes TCP e UDP sem a necessidade de lidar com os detalhes da conexão.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-112">These two client classes encapsulate the creation of TCP and UDP sockets without requiring you to handle the details of the connection.</span></span>  
  
-   <span data-ttu-id="ebd8a-113">Ao acessar sites que exigem credenciais, use a classe <xref:System.Net.CredentialCache> para criar um cache de credenciais, em vez de fornecê-las com cada solicitação.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-113">When accessing sites that require credentials, use the <xref:System.Net.CredentialCache> class to create a cache of credentials rather than supplying them with every request.</span></span> <span data-ttu-id="ebd8a-114">A classe **CredentialCache** procura o cache para localizar as credenciais apropriadas a serem apresentadas com uma solicitação, liberando-o da responsabilidade de criar e apresentar credenciais baseadas na URL.</span><span class="sxs-lookup"><span data-stu-id="ebd8a-114">The **CredentialCache** class searches the cache to find the appropriate credential to present with a request, relieving you of the responsibility of creating and presenting credentials based on the URL.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebd8a-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ebd8a-115">See Also</span></span>  
 [<span data-ttu-id="ebd8a-116">Programação de rede no .NET Framework</span><span class="sxs-lookup"><span data-stu-id="ebd8a-116">Network Programming in the .NET Framework</span></span>](../../../docs/framework/network-programming/index.md)
