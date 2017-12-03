---
title: "Como implantar uma aplicação de integração + COM"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2e5a0510-db3c-4988-a09c-696285836650
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c63478620a2b604d27f2d9d154383cb0bae6b6da
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-deploy-a-com-integration-application"></a><span data-ttu-id="afb6d-102">Como implantar uma aplicação de integração + COM</span><span class="sxs-lookup"><span data-stu-id="afb6d-102">How to: Deploy a COM+ Integration Application</span></span>
<span data-ttu-id="afb6d-103">Uma vez você gravou um aplicativo COM+ integration, você talvez queira implantá-lo em outro computador.</span><span class="sxs-lookup"><span data-stu-id="afb6d-103">Once you have written a COM+ integration application, you may want to deploy it on another machine.</span></span> <span data-ttu-id="afb6d-104">Este tópico descreve como mover um aplicativo de integração COM+ de um computador para outro.</span><span class="sxs-lookup"><span data-stu-id="afb6d-104">This topic describes how to move a COM+ integration application from one machine to another.</span></span>  
  
### <a name="moving-a-com-hosted-integration-app"></a><span data-ttu-id="afb6d-105">Mover um COM+ hospedado integração do aplicativo</span><span class="sxs-lookup"><span data-stu-id="afb6d-105">Moving a COM+ hosted Integration App</span></span>  
  
1.  <span data-ttu-id="afb6d-106">Certifique-se de que [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] está instalado nos dois computadores.</span><span class="sxs-lookup"><span data-stu-id="afb6d-106">Ensure that [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] is installed on both machines.</span></span>  
  
2.  <span data-ttu-id="afb6d-107">Exportar o aplicativo de máquina A.</span><span class="sxs-lookup"><span data-stu-id="afb6d-107">Export the application from machine A.</span></span>  
  
3.  <span data-ttu-id="afb6d-108">Importe o aplicativo na máquina B.</span><span class="sxs-lookup"><span data-stu-id="afb6d-108">Import the application on machine B.</span></span>  
  
4.  <span data-ttu-id="afb6d-109">Defina o diretório raiz do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="afb6d-109">Set the Application Root Directory.</span></span> <span data-ttu-id="afb6d-110">Por convenção, isso é %PROGRAMFILES%/ComPlus aplicativos / {AppGUID}.</span><span class="sxs-lookup"><span data-stu-id="afb6d-110">By convention, this is %PROGRAMFILES%/ComPlus Applications/{AppGUID}.</span></span>  
  
5.  <span data-ttu-id="afb6d-111">Copie os arquivos config e Application.manifest do diretório raiz do aplicativo em um computador para o diretório raiz do aplicativo na máquina B.</span><span class="sxs-lookup"><span data-stu-id="afb6d-111">Copy the Application.config and Application.manifest files from the application root directory on machine A to the application root directory on machine B.</span></span>  
  
6.  <span data-ttu-id="afb6d-112">Edite os endereços de ponto de extremidade de serviço no arquivo config no computador B para identificar o computador apropriado.</span><span class="sxs-lookup"><span data-stu-id="afb6d-112">Edit the service endpoint addresses in the Application.config file on machine B to identify the appropriate machine.</span></span> <span data-ttu-id="afb6d-113">Por exemplo, altere http://machineA/MyService para http://machineB/MyService.</span><span class="sxs-lookup"><span data-stu-id="afb6d-113">For example, change http://machineA/MyService to http://machineB/MyService.</span></span>  
  
### <a name="moving-a-web-hosted-integration-application"></a><span data-ttu-id="afb6d-114">Mover um aplicativo Web hospedado integração</span><span class="sxs-lookup"><span data-stu-id="afb6d-114">Moving a Web-hosted integration application</span></span>  
  
1.  <span data-ttu-id="afb6d-115">Certifique-se de que [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] está instalado nos dois computadores.</span><span class="sxs-lookup"><span data-stu-id="afb6d-115">Ensure that [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] is installed on both machines.</span></span>  
  
2.  <span data-ttu-id="afb6d-116">Exportar o aplicativo de máquina A.</span><span class="sxs-lookup"><span data-stu-id="afb6d-116">Export the application from machine A.</span></span>  
  
3.  <span data-ttu-id="afb6d-117">Importe o aplicativo na máquina B.</span><span class="sxs-lookup"><span data-stu-id="afb6d-117">Import the application on machine B.</span></span>  
  
4.  <span data-ttu-id="afb6d-118">Crie uma vroot do IIS no computador B.</span><span class="sxs-lookup"><span data-stu-id="afb6d-118">Create an IIS vroot on machine B.</span></span>  
  
5.  <span data-ttu-id="afb6d-119">Copiar o arquivo. svc (componentName.svc) e o arquivo Web. config de vroot em um computador para o vroot recém-criado na máquina B.</span><span class="sxs-lookup"><span data-stu-id="afb6d-119">Copy the .svc file (componentName.svc) and the Web.config file from the vroot on machine A to the newly created vroot on machine B.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afb6d-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="afb6d-120">See Also</span></span>  
 [<span data-ttu-id="afb6d-121">Integração com visão geral de aplicativos COM+</span><span class="sxs-lookup"><span data-stu-id="afb6d-121">Integrating with COM+ Applications Overview</span></span>](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications-overview.md)  
 [<span data-ttu-id="afb6d-122">Como: definir configurações de serviço COM+</span><span class="sxs-lookup"><span data-stu-id="afb6d-122">How to: Configure COM+ Service Settings</span></span>](../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)  
 [<span data-ttu-id="afb6d-123">Como: usar a ferramenta de configuração de modelo de serviço COM+</span><span class="sxs-lookup"><span data-stu-id="afb6d-123">How to: Use the COM+ Service Model Configuration Tool</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-com-service-model-configuration-tool.md)
