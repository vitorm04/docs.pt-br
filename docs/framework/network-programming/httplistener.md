---
title: HttpListener
ms.date: 03/30/2017
helpviewer_keywords:
- HTTP
ms.assetid: 5b89d3fb-3c9a-49e2-af1f-c34c020c68ac
ms.openlocfilehash: 902225085ccaceb9d90d0c25d9369ef65ae2730b
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50193104"
---
# <a name="httplistener"></a><span data-ttu-id="ae17e-102">HttpListener</span><span class="sxs-lookup"><span data-stu-id="ae17e-102">HttpListener</span></span>
<span data-ttu-id="ae17e-103">A classe <xref:System.Net.HttpListener> fornece um ouvinte de protocolo HTTP controlado programaticamente.</span><span class="sxs-lookup"><span data-stu-id="ae17e-103">The <xref:System.Net.HttpListener> class provides a programmatically controlled HTTP protocol listener.</span></span> <span data-ttu-id="ae17e-104">O ouvinte fica ativo durante o tempo de vida do objeto <xref:System.Net.HttpListener> e é executado dentro de seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ae17e-104">The listener is active for the lifetime of the <xref:System.Net.HttpListener> object and runs within your application.</span></span>  
  
## <a name="httpsys"></a><span data-ttu-id="ae17e-105">HTTP.SYS</span><span class="sxs-lookup"><span data-stu-id="ae17e-105">HTTP.SYS</span></span>  
 <span data-ttu-id="ae17e-106">A classe <xref:System.Net.HttpListener> é criada sobre HTTP.sys, que é o ouvinte de modo kernel que manipula todo o tráfego HTTP para o Windows.</span><span class="sxs-lookup"><span data-stu-id="ae17e-106">The <xref:System.Net.HttpListener> class is built on top of HTTP.sys, which is the kernel mode listener that handles all HTTP traffic for Windows.</span></span> <span data-ttu-id="ae17e-107">O HTTP.sys fornece gerenciamento de conexão, a limitação de largura de banda e registro em log do servidor Web.</span><span class="sxs-lookup"><span data-stu-id="ae17e-107">HTTP.sys provides connection management, bandwidth throttling, and Web server logging.</span></span> <span data-ttu-id="ae17e-108">Use a ferramenta `HttpCfg.exe` para adicionar certificados SSL.</span><span class="sxs-lookup"><span data-stu-id="ae17e-108">Use the `HttpCfg.exe` tool to add SSL certificates.</span></span> <span data-ttu-id="ae17e-109">Para obter mais informações, consulte a documentação sobre a ferramenta [HttpCfg.exe](https://go.microsoft.com/fwlink/?LinkID=178284) na documentação do [Servidor](https://go.microsoft.com/fwlink/?LinkID=178285).</span><span class="sxs-lookup"><span data-stu-id="ae17e-109">For more information, see the documentation on the [HttpCfg.exe](https://go.microsoft.com/fwlink/?LinkID=178284) tool in the [Server](https://go.microsoft.com/fwlink/?LinkID=178285) documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae17e-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ae17e-110">See Also</span></span>  
 <xref:System.Net.HttpListener>  
 <xref:System.Net.HttpWebRequest>  
 <xref:System.Net.HttpWebResponse>  
 [<span data-ttu-id="ae17e-111">Servidor HTTP</span><span class="sxs-lookup"><span data-stu-id="ae17e-111">HTTP Server</span></span>](https://go.microsoft.com/fwlink/?LinkID=178285)  
 [<span data-ttu-id="ae17e-112">Melhorias de segurança em informações da Internet</span><span class="sxs-lookup"><span data-stu-id="ae17e-112">Security Enhancements in Internet Information</span></span>](https://go.microsoft.com/fwlink/?LinkID=178286)  
 [<span data-ttu-id="ae17e-113">Amostra de aplicativo host ASPX HttpListener</span><span class="sxs-lookup"><span data-stu-id="ae17e-113">HttpListener ASPX Host Application Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=179560)  
 [<span data-ttu-id="ae17e-114">Amostra de tecnologia HttpListener</span><span class="sxs-lookup"><span data-stu-id="ae17e-114">HttpListener Technology Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=179558)  
 [<span data-ttu-id="ae17e-115">Amostras de programação de rede</span><span class="sxs-lookup"><span data-stu-id="ae17e-115">Network Programming Samples</span></span>](../../../docs/framework/network-programming/network-programming-samples.md)
