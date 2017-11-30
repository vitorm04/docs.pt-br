---
title: HttpListener
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: HTTP
ms.assetid: 5b89d3fb-3c9a-49e2-af1f-c34c020c68ac
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: ca0a22ff1d06485658da75a46bd408a12a3a964c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="httplistener"></a><span data-ttu-id="378ef-102">HttpListener</span><span class="sxs-lookup"><span data-stu-id="378ef-102">HttpListener</span></span>
<span data-ttu-id="378ef-103">A classe <xref:System.Net.HttpListener> fornece um ouvinte de protocolo HTTP controlado programaticamente.</span><span class="sxs-lookup"><span data-stu-id="378ef-103">The <xref:System.Net.HttpListener> class provides a programmatically controlled HTTP protocol listener.</span></span> <span data-ttu-id="378ef-104">O ouvinte fica ativo durante o tempo de vida do objeto <xref:System.Net.HttpListener> e é executado dentro de seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="378ef-104">The listener is active for the lifetime of the <xref:System.Net.HttpListener> object and runs within your application.</span></span>  
  
## <a name="httpsys"></a><span data-ttu-id="378ef-105">HTTP.SYS</span><span class="sxs-lookup"><span data-stu-id="378ef-105">HTTP.SYS</span></span>  
 <span data-ttu-id="378ef-106">A classe <xref:System.Net.HttpListener> é criada sobre HTTP.sys, que é o ouvinte de modo kernel que manipula todo o tráfego HTTP para o Windows.</span><span class="sxs-lookup"><span data-stu-id="378ef-106">The <xref:System.Net.HttpListener> class is built on top of HTTP.sys, which is the kernel mode listener that handles all HTTP traffic for Windows.</span></span> <span data-ttu-id="378ef-107">O HTTP.sys fornece gerenciamento de conexão, a limitação de largura de banda e registro em log do servidor Web.</span><span class="sxs-lookup"><span data-stu-id="378ef-107">HTTP.sys provides connection management, bandwidth throttling, and Web server logging.</span></span> <span data-ttu-id="378ef-108">Use a ferramenta `HttpCfg.exe` para adicionar certificados SSL.</span><span class="sxs-lookup"><span data-stu-id="378ef-108">Use the `HttpCfg.exe` tool to add SSL certificates.</span></span> <span data-ttu-id="378ef-109">Para obter mais informações, consulte a documentação sobre a ferramenta [HttpCfg.exe](http://go.microsoft.com/fwlink/?LinkID=178284) na documentação do [Servidor](http://go.microsoft.com/fwlink/?LinkID=178285).</span><span class="sxs-lookup"><span data-stu-id="378ef-109">For more information, see the documentation on the [HttpCfg.exe](http://go.microsoft.com/fwlink/?LinkID=178284) tool in the [Server](http://go.microsoft.com/fwlink/?LinkID=178285) documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="378ef-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="378ef-110">See Also</span></span>  
 <xref:System.Net.HttpListener>  
 <xref:System.Net.HttpWebRequest>  
 <xref:System.Net.HttpWebResponse>  
 [<span data-ttu-id="378ef-111">Servidor HTTP</span><span class="sxs-lookup"><span data-stu-id="378ef-111">HTTP Server</span></span>](http://go.microsoft.com/fwlink/?LinkID=178285)  
 [<span data-ttu-id="378ef-112">Aprimoramentos de segurança de informações da Internet</span><span class="sxs-lookup"><span data-stu-id="378ef-112">Security Enhancements in Internet Information</span></span>](http://go.microsoft.com/fwlink/?LinkID=178286)  
 [<span data-ttu-id="378ef-113">Amostra de aplicativo host ASPX HttpListener</span><span class="sxs-lookup"><span data-stu-id="378ef-113">HttpListener ASPX Host Application Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=179560)  
 [<span data-ttu-id="378ef-114">Amostra de tecnologia HttpListener</span><span class="sxs-lookup"><span data-stu-id="378ef-114">HttpListener Technology Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=179558)  
 [<span data-ttu-id="378ef-115">Amostras de programação de rede</span><span class="sxs-lookup"><span data-stu-id="378ef-115">Network Programming Samples</span></span>](../../../docs/framework/network-programming/network-programming-samples.md)
