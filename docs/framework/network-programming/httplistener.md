---
title: HttpListener
ms.date: 03/30/2017
helpviewer_keywords:
- HTTP
ms.assetid: 5b89d3fb-3c9a-49e2-af1f-c34c020c68ac
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 68c69de839ccbd51de9f0bfa74be018f877f7731
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43416865"
---
# <a name="httplistener"></a><span data-ttu-id="de543-102">HttpListener</span><span class="sxs-lookup"><span data-stu-id="de543-102">HttpListener</span></span>
<span data-ttu-id="de543-103">A classe <xref:System.Net.HttpListener> fornece um ouvinte de protocolo HTTP controlado programaticamente.</span><span class="sxs-lookup"><span data-stu-id="de543-103">The <xref:System.Net.HttpListener> class provides a programmatically controlled HTTP protocol listener.</span></span> <span data-ttu-id="de543-104">O ouvinte fica ativo durante o tempo de vida do objeto <xref:System.Net.HttpListener> e é executado dentro de seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="de543-104">The listener is active for the lifetime of the <xref:System.Net.HttpListener> object and runs within your application.</span></span>  
  
## <a name="httpsys"></a><span data-ttu-id="de543-105">HTTP.SYS</span><span class="sxs-lookup"><span data-stu-id="de543-105">HTTP.SYS</span></span>  
 <span data-ttu-id="de543-106">A classe <xref:System.Net.HttpListener> é criada sobre HTTP.sys, que é o ouvinte de modo kernel que manipula todo o tráfego HTTP para o Windows.</span><span class="sxs-lookup"><span data-stu-id="de543-106">The <xref:System.Net.HttpListener> class is built on top of HTTP.sys, which is the kernel mode listener that handles all HTTP traffic for Windows.</span></span> <span data-ttu-id="de543-107">O HTTP.sys fornece gerenciamento de conexão, a limitação de largura de banda e registro em log do servidor Web.</span><span class="sxs-lookup"><span data-stu-id="de543-107">HTTP.sys provides connection management, bandwidth throttling, and Web server logging.</span></span> <span data-ttu-id="de543-108">Use a ferramenta `HttpCfg.exe` para adicionar certificados SSL.</span><span class="sxs-lookup"><span data-stu-id="de543-108">Use the `HttpCfg.exe` tool to add SSL certificates.</span></span> <span data-ttu-id="de543-109">Para obter mais informações, consulte a documentação sobre a ferramenta [HttpCfg.exe](https://go.microsoft.com/fwlink/?LinkID=178284) na documentação do [Servidor](https://go.microsoft.com/fwlink/?LinkID=178285).</span><span class="sxs-lookup"><span data-stu-id="de543-109">For more information, see the documentation on the [HttpCfg.exe](https://go.microsoft.com/fwlink/?LinkID=178284) tool in the [Server](https://go.microsoft.com/fwlink/?LinkID=178285) documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de543-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="de543-110">See Also</span></span>  
 <xref:System.Net.HttpListener>  
 <xref:System.Net.HttpWebRequest>  
 <xref:System.Net.HttpWebResponse>  
 [<span data-ttu-id="de543-111">Servidor HTTP</span><span class="sxs-lookup"><span data-stu-id="de543-111">HTTP Server</span></span>](https://go.microsoft.com/fwlink/?LinkID=178285)  
 [<span data-ttu-id="de543-112">Melhorias de segurança em informações da Internet</span><span class="sxs-lookup"><span data-stu-id="de543-112">Security Enhancements in Internet Information</span></span>](https://go.microsoft.com/fwlink/?LinkID=178286)  
 [<span data-ttu-id="de543-113">Amostra de aplicativo host ASPX HttpListener</span><span class="sxs-lookup"><span data-stu-id="de543-113">HttpListener ASPX Host Application Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=179560)  
 [<span data-ttu-id="de543-114">Amostra de tecnologia HttpListener</span><span class="sxs-lookup"><span data-stu-id="de543-114">HttpListener Technology Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=179558)  
 [<span data-ttu-id="de543-115">Amostras de programação de rede</span><span class="sxs-lookup"><span data-stu-id="de543-115">Network Programming Samples</span></span>](../../../docs/framework/network-programming/network-programming-samples.md)
