---
title: "Renomeando um serviço do WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 14235a65-b1c5-409d-b6cc-a979acd54bbd
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5c2ecd78a7d72b86460f4d1972c42c8550010f02
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="renaming-a-wcf-service"></a><span data-ttu-id="caa3c-102">Renomeando um serviço do WCF</span><span class="sxs-lookup"><span data-stu-id="caa3c-102">Renaming a WCF Service</span></span>
<span data-ttu-id="caa3c-103">Este tópico descreve como você pode renomear um [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] serviço.</span><span class="sxs-lookup"><span data-stu-id="caa3c-103">This topic describes how you can rename a [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] service.</span></span>  
  
## <a name="renaming-a-wcf-service"></a><span data-ttu-id="caa3c-104">Renomeando um serviço do WCF</span><span class="sxs-lookup"><span data-stu-id="caa3c-104">Renaming a WCF Service</span></span>  
 <span data-ttu-id="caa3c-105">Execute as seguintes etapas para renomear um serviço em um [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] modelo</span><span class="sxs-lookup"><span data-stu-id="caa3c-105">Perform the following steps to rename a service in a [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] template,</span></span>  
  
-   <span data-ttu-id="caa3c-106">Altere o nome da classe que implementa o serviço.</span><span class="sxs-lookup"><span data-stu-id="caa3c-106">Change the name of the class that implements the service.</span></span>  
  
-   <span data-ttu-id="caa3c-107">No arquivo de configuração do serviço, altere o nome do serviço para o novo nome que você escolheu, conforme indicado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="caa3c-107">In the configuration file of the service, change the name of the service to the new name you have chosen, as indicated in the following example.</span></span> <span data-ttu-id="caa3c-108">O arquivo de configuração pode ser um arquivo App. config ou Web. config, dependendo de seu modelo de hospedagem.</span><span class="sxs-lookup"><span data-stu-id="caa3c-108">The configuration file can be either app.config or web.config file depending on your hosting model.</span></span>  
  
```xml  
<system.servicemodel>  
   <services>  
      <service name="WcfService.NewName">  
      </service>  
   </services>  
</system.servicemodel>  
```  
  
-   <span data-ttu-id="caa3c-109">Se o serviço for webhosted, ele usa um arquivo svc.</span><span class="sxs-lookup"><span data-stu-id="caa3c-109">If your service is webhosted, it uses an *.svc file.</span></span> <span data-ttu-id="caa3c-110">Abra o arquivo svc e modifique o nome do seu serviço, conforme indicado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="caa3c-110">Open the svc file and modify the name of your service as indicated in the following example.</span></span> <span data-ttu-id="caa3c-111">Essa etapa não é necessária para aplicativos hospedados automaticamente, pois não há nenhum arquivo svc.</span><span class="sxs-lookup"><span data-stu-id="caa3c-111">This step is not necessary for self-hosted applications, as there is no svc file.</span></span>  
  
```  
<%@ ServiceHost Service="WcfService.NewName">  
```  
  
## <a name="renaming-a-wcf-service-contract"></a><span data-ttu-id="caa3c-112">Renomeando um contrato de serviço do WCF</span><span class="sxs-lookup"><span data-stu-id="caa3c-112">Renaming a WCF Service Contract</span></span>  
  
-   <span data-ttu-id="caa3c-113">Execute as seguintes etapas para renomear o contrato de serviço</span><span class="sxs-lookup"><span data-stu-id="caa3c-113">Perform the following steps to rename the service contract,</span></span>  
  
-   <span data-ttu-id="caa3c-114">Altere o nome do contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="caa3c-114">Change the name of the service contract.</span></span>  
  
-   <span data-ttu-id="caa3c-115">No arquivo de configuração do serviço, altere o nome do contrato de serviço para o novo nome que você escolheu, conforme indicado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="caa3c-115">In the configuration file of the service, change the name of the service contract to the new name you have chosen, as indicated in the following example.</span></span> <span data-ttu-id="caa3c-116">O arquivo de configuração pode ser um arquivo App. config ou Web. config, dependendo de seu modelo de hospedagem.</span><span class="sxs-lookup"><span data-stu-id="caa3c-116">The configuration file can be either app.config or web.config file depending on your hosting model.</span></span>  
  
```xml  
<system.servicemodel>  
   <services>  
      <service>  
         <endpoint contract="WcfService.NewContractName" />  
      </service>  
   </services>  
</system.servicemodel>  
```
