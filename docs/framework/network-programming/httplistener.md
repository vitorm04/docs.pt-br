---
title: HttpListener
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- HTTP
ms.assetid: 5b89d3fb-3c9a-49e2-af1f-c34c020c68ac
caps.latest.revision: 9
author: mcleblanc
ms.author: markl
manager: markl
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 44620273fc2497675a26a6905dfdc52db1aaab3f
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="httplistener"></a><span data-ttu-id="df5d7-102">HttpListener</span><span class="sxs-lookup"><span data-stu-id="df5d7-102">HttpListener</span></span>
<span data-ttu-id="df5d7-103">A classe <xref:System.Net.HttpListener> fornece um ouvinte de protocolo HTTP controlado programaticamente.</span><span class="sxs-lookup"><span data-stu-id="df5d7-103">The <xref:System.Net.HttpListener> class provides a programmatically controlled HTTP protocol listener.</span></span> <span data-ttu-id="df5d7-104">O ouvinte fica ativo durante o tempo de vida do objeto <xref:System.Net.HttpListener> e é executado dentro de seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="df5d7-104">The listener is active for the lifetime of the <xref:System.Net.HttpListener> object and runs within your application.</span></span>  
  
## <a name="httpsys"></a><span data-ttu-id="df5d7-105">HTTP.SYS</span><span class="sxs-lookup"><span data-stu-id="df5d7-105">HTTP.SYS</span></span>  
 <span data-ttu-id="df5d7-106">A classe <xref:System.Net.HttpListener> é criada sobre HTTP.sys, que é o ouvinte de modo kernel que manipula todo o tráfego HTTP para o Windows.</span><span class="sxs-lookup"><span data-stu-id="df5d7-106">The <xref:System.Net.HttpListener> class is built on top of HTTP.sys, which is the kernel mode listener that handles all HTTP traffic for Windows.</span></span> <span data-ttu-id="df5d7-107">O HTTP.sys fornece gerenciamento de conexão, a limitação de largura de banda e registro em log do servidor Web.</span><span class="sxs-lookup"><span data-stu-id="df5d7-107">HTTP.sys provides connection management, bandwidth throttling, and Web server logging.</span></span> <span data-ttu-id="df5d7-108">Use a ferramenta `HttpCfg.exe` para adicionar certificados SSL.</span><span class="sxs-lookup"><span data-stu-id="df5d7-108">Use the `HttpCfg.exe` tool to add SSL certificates.</span></span> <span data-ttu-id="df5d7-109">Para obter mais informações, consulte a documentação sobre a ferramenta [HttpCfg.exe](http://go.microsoft.com/fwlink/?LinkID=178284) na documentação do [Servidor](http://go.microsoft.com/fwlink/?LinkID=178285).</span><span class="sxs-lookup"><span data-stu-id="df5d7-109">For more information, see the documentation on the [HttpCfg.exe](http://go.microsoft.com/fwlink/?LinkID=178284) tool in the [Server](http://go.microsoft.com/fwlink/?LinkID=178285) documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df5d7-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="df5d7-110">See Also</span></span>  
 <span data-ttu-id="df5d7-111"><xref:System.Net.HttpListener></span><span class="sxs-lookup"><span data-stu-id="df5d7-111"><xref:System.Net.HttpListener></span></span>   
 <span data-ttu-id="df5d7-112"><xref:System.Net.HttpWebRequest></span><span class="sxs-lookup"><span data-stu-id="df5d7-112"><xref:System.Net.HttpWebRequest></span></span>   
 <span data-ttu-id="df5d7-113"><xref:System.Net.HttpWebResponse></span><span class="sxs-lookup"><span data-stu-id="df5d7-113"><xref:System.Net.HttpWebResponse></span></span>   
 <span data-ttu-id="df5d7-114">[Servidor HTTP](http://go.microsoft.com/fwlink/?LinkID=178285) </span><span class="sxs-lookup"><span data-stu-id="df5d7-114">[HTTP Server](http://go.microsoft.com/fwlink/?LinkID=178285) </span></span>  
 <span data-ttu-id="df5d7-115">[Melhorias de segurança em informações da Internet](http://go.microsoft.com/fwlink/?LinkID=178286) </span><span class="sxs-lookup"><span data-stu-id="df5d7-115">[Security Enhancements in Internet Information](http://go.microsoft.com/fwlink/?LinkID=178286) </span></span>  
 <span data-ttu-id="df5d7-116">[Amostra de aplicativo host ASPX HttpListener](http://go.microsoft.com/fwlink/?LinkID=179560) </span><span class="sxs-lookup"><span data-stu-id="df5d7-116">[HttpListener ASPX Host Application Sample](http://go.microsoft.com/fwlink/?LinkID=179560) </span></span>  
 <span data-ttu-id="df5d7-117">[Amostra de tecnologia HttpListener](http://go.microsoft.com/fwlink/?LinkID=179558) </span><span class="sxs-lookup"><span data-stu-id="df5d7-117">[HttpListener Technology Sample](http://go.microsoft.com/fwlink/?LinkID=179558) </span></span>  
 [<span data-ttu-id="df5d7-118">Amostras de programação de rede</span><span class="sxs-lookup"><span data-stu-id="df5d7-118">Network Programming Samples</span></span>](../../../docs/framework/network-programming/network-programming-samples.md)

