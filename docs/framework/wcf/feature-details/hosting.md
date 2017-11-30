---
title: Hosting2
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0820c7e5-0b50-4cde-80e7-74e346513002
caps.latest.revision: "20"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 8b0e8aa1dfe2e7a737e88530a206739eef39b2cb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="hosting"></a><span data-ttu-id="8197c-102">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="8197c-102">Hosting</span></span>
<span data-ttu-id="8197c-103">Os tópicos na seção descrevem a hospedagem de serviços.</span><span class="sxs-lookup"><span data-stu-id="8197c-103">The topics in the section describe service hosting.</span></span> <span data-ttu-id="8197c-104">Um serviço pode ser hospedado por serviços de informações da Internet (IIS), o serviço de ativação de processos do Windows (WAS), o Windows Server AppFabric, um serviço do Windows ou por um aplicativo gerenciado, esta opção também é conhecida como *hospedagem self*.</span><span class="sxs-lookup"><span data-stu-id="8197c-104">A service can be hosted by Internet Information Services (IIS), Windows Process Activation Service (WAS), Windows Server AppFabric, a Windows service, or by a managed application—this option is often referred to as *self hosting*.</span></span>  
  
 <span data-ttu-id="8197c-105">É importante observar que executando um serviço ou qualquer extensão de segurança de comprometer um host não confiável.</span><span class="sxs-lookup"><span data-stu-id="8197c-105">It is important to note that running a service or any extension from an untrusted host compromises security.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8197c-106">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="8197c-106">In This Section</span></span>  
 [<span data-ttu-id="8197c-107">Hospedagem no Internet Information Services</span><span class="sxs-lookup"><span data-stu-id="8197c-107">Hosting in Internet Information Services</span></span>](../../../../docs/framework/wcf/feature-details/hosting-in-internet-information-services.md)  
 <span data-ttu-id="8197c-108">Descreve como um [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] serviço é hospedado no Internet Information Services ou [do Windows Server AppFabric](http://go.microsoft.com/fwlink/?LinkId=196496).</span><span class="sxs-lookup"><span data-stu-id="8197c-108">Describes how a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service is hosted in Internet Information Services or [Windows Server AppFabric](http://go.microsoft.com/fwlink/?LinkId=196496).</span></span>  
  
 <span data-ttu-id="8197c-109">[Hosting in Windows Process Activation Service](../../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md) (Hospedagem no Serviço de Ativação de Processos do Windows)</span><span class="sxs-lookup"><span data-stu-id="8197c-109">[Hosting in Windows Process Activation Service](../../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md)</span></span>  
 <span data-ttu-id="8197c-110">Descreve como um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço é hospedado pelo serviço de ativação de processos do Windows.</span><span class="sxs-lookup"><span data-stu-id="8197c-110">Describes how a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service is hosted by Windows Process Activation Service.</span></span>  
  
 [<span data-ttu-id="8197c-111">Hospedando em um aplicativo de serviço do Windows</span><span class="sxs-lookup"><span data-stu-id="8197c-111">Hosting in a Windows Service Application</span></span>](../../../../docs/framework/wcf/feature-details/hosting-in-a-windows-service-application.md)  
 <span data-ttu-id="8197c-112">Descreve como um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço é hospedado por um serviço do Windows.</span><span class="sxs-lookup"><span data-stu-id="8197c-112">Describes how a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service is hosted by a Windows service.</span></span>  
  
 [<span data-ttu-id="8197c-113">Hospedando em um aplicativo gerenciado</span><span class="sxs-lookup"><span data-stu-id="8197c-113">Hosting in a Managed Application</span></span>](../../../../docs/framework/wcf/feature-details/hosting-in-a-managed-application.md)  
 <span data-ttu-id="8197c-114">Descreve como um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço é hospedado em um aplicativo gerenciado.</span><span class="sxs-lookup"><span data-stu-id="8197c-114">Describes how a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service is hosted in a managed application.</span></span>  
  
 [<span data-ttu-id="8197c-115">Ativação com base em configuração no IIS e WAS</span><span class="sxs-lookup"><span data-stu-id="8197c-115">Configuration-Based Activation in IIS and WAS</span></span>](../../../../docs/framework/wcf/feature-details/configuration-based-activation-in-iis-and-was.md)  
 <span data-ttu-id="8197c-116">Descreve como um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço é hospedado em IIS ou do WAS sem usar um arquivo. svc.</span><span class="sxs-lookup"><span data-stu-id="8197c-116">Describes how a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service is hosted under IIS or WAS without using a .svc file.</span></span>  
  
 [<span data-ttu-id="8197c-117">Suporte a ligações de Site do IIS</span><span class="sxs-lookup"><span data-stu-id="8197c-117">Supporting Multiple IIS Site Bindings</span></span>](../../../../docs/framework/wcf/feature-details/supporting-multiple-iis-site-bindings.md)  
 <span data-ttu-id="8197c-118">Descreve como especificar vários endereços de base para um serviço usando o mesmo esquema de URI em um único site.</span><span class="sxs-lookup"><span data-stu-id="8197c-118">Describes how to specify multiple base addresses for a service using the same URI scheme on a single Web site.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8197c-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8197c-119">See Also</span></span>  
 <span data-ttu-id="8197c-120">[Hosting Services](../../../../docs/framework/wcf/hosting-services.md) (Hospedando serviços)</span><span class="sxs-lookup"><span data-stu-id="8197c-120">[Hosting Services](../../../../docs/framework/wcf/hosting-services.md)</span></span>  
 [<span data-ttu-id="8197c-121">Recursos de hospedagem do Windows Server App Fabric</span><span class="sxs-lookup"><span data-stu-id="8197c-121">Windows Server App Fabric Hosting Features</span></span>](http://go.microsoft.com/fwlink/?LinkId=201276)
