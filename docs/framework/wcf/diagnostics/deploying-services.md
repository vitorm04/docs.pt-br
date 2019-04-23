---
title: Implantando serviços
ms.date: 03/30/2017
ms.assetid: ac361bfb-017d-4da9-a2d7-fc0fb72d65bb
ms.openlocfilehash: 2c3cd17b597fafcd02b9155089bc583fafbc9dea
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59085736"
---
# <a name="deploying-services"></a><span data-ttu-id="5f662-102">Implantando serviços</span><span class="sxs-lookup"><span data-stu-id="5f662-102">Deploying Services</span></span>
<span data-ttu-id="5f662-103">Este tópico descreve como você pode implantar um aplicativo do Windows Communication Foundation (WCF) em um ambiente de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="5f662-103">This topic describes how you can deploy a Windows Communication Foundation (WCF) application to a run-time environment.</span></span>  
  
## <a name="choosing-the-hosting-environment-for-your-application"></a><span data-ttu-id="5f662-104">Escolhendo o ambiente de hospedagem para seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="5f662-104">Choosing the Hosting Environment for Your Application</span></span>  
 <span data-ttu-id="5f662-105">Os serviços do WCF são projetados para funcionar em qualquer processo do Windows que dá suporte a código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="5f662-105">WCF services are designed to run in any Windows process that supports managed code.</span></span> <span data-ttu-id="5f662-106">Para se tornar ativo, um serviço deve ser hospedado dentro de um ambiente de tempo de execução que cria e controla seu contexto e o tempo de vida.</span><span class="sxs-lookup"><span data-stu-id="5f662-106">To become active, a service must be hosted within a run-time environment that creates it and controls its context and lifetime.</span></span> <span data-ttu-id="5f662-107">As opções variam de execução dentro do aplicativo de console mais simples para ambientes de servidor como um serviço do Windows, serviços de informações da Internet (IIS), ou dentro de um processo de trabalho de hospedagem gerenciado pelo Windows Activation Service (WAS).</span><span class="sxs-lookup"><span data-stu-id="5f662-107">Hosting options range from running inside the simplest console application to server environments like a Windows service, Internet Information Services (IIS), or within a worker process managed by the Windows Activation Service (WAS).</span></span> <span data-ttu-id="5f662-108">Para examinar as diferentes opções de hospedagem para seu aplicativo do WCF, consulte [serviços de hospedagem](../../../../docs/framework/wcf/hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="5f662-108">To review the different hosting options for your WCF application, see [Hosting Services](../../../../docs/framework/wcf/hosting-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f662-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5f662-109">See also</span></span>

- [<span data-ttu-id="5f662-110">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="5f662-110">Hosting</span></span>](../../../../docs/framework/wcf/feature-details/hosting.md)
- [<span data-ttu-id="5f662-111">Hospedando serviços</span><span class="sxs-lookup"><span data-stu-id="5f662-111">Hosting Services</span></span>](../../../../docs/framework/wcf/hosting-services.md)
