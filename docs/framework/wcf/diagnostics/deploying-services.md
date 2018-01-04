---
title: "Implantando serviços"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ac361bfb-017d-4da9-a2d7-fc0fb72d65bb
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6e32570b381d6cab4326a13246dfe053b5032589
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="deploying-services"></a><span data-ttu-id="2e512-102">Implantando serviços</span><span class="sxs-lookup"><span data-stu-id="2e512-102">Deploying Services</span></span>
<span data-ttu-id="2e512-103">Este tópico descreve como você pode implantar um [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] aplicativo em um ambiente de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="2e512-103">This topic describes how you can deploy a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] application to a run-time environment.</span></span>  
  
## <a name="choosing-the-hosting-environment-for-your-application"></a><span data-ttu-id="2e512-104">Escolher o ambiente de hospedagem para o seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="2e512-104">Choosing the Hosting Environment for Your Application</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="2e512-105">os serviços são projetados para funcionar em qualquer processo do Windows que dá suporte a código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="2e512-105"> services are designed to run in any Windows process that supports managed code.</span></span> <span data-ttu-id="2e512-106">Para se tornar ativa, um serviço deve ser hospedado em um ambiente de tempo de execução que cria e controla o contexto e o tempo de vida.</span><span class="sxs-lookup"><span data-stu-id="2e512-106">To become active, a service must be hosted within a run-time environment that creates it and controls its context and lifetime.</span></span> <span data-ttu-id="2e512-107">As opções variam de execução dentro do aplicativo de console mais simples para ambientes de servidor como um serviço do Windows, serviços de informações da Internet (IIS), ou dentro de um processo de trabalho de hospedagem gerenciado pelo serviço de ativação do Windows (WAS).</span><span class="sxs-lookup"><span data-stu-id="2e512-107">Hosting options range from running inside the simplest console application to server environments like a Windows service, Internet Information Services (IIS), or within a worker process managed by the Windows Activation Service (WAS).</span></span> <span data-ttu-id="2e512-108">Para examinar as diferentes opções de hospedagem para o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplicativo, consulte [serviços de hospedagem](../../../../docs/framework/wcf/hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="2e512-108">To review the different hosting options for your [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] application, see [Hosting Services](../../../../docs/framework/wcf/hosting-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e512-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2e512-109">See Also</span></span>  
 [<span data-ttu-id="2e512-110">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="2e512-110">Hosting</span></span>](../../../../docs/framework/wcf/feature-details/hosting.md)  
 [<span data-ttu-id="2e512-111">Hospedando serviços</span><span class="sxs-lookup"><span data-stu-id="2e512-111">Hosting Services</span></span>](../../../../docs/framework/wcf/hosting-services.md)
