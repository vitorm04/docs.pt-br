---
title: Renomeando um serviço do WCF
ms.date: 03/30/2017
ms.assetid: 14235a65-b1c5-409d-b6cc-a979acd54bbd
ms.openlocfilehash: a215523b92757e3bde1dae2e50de22169020e870
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33498981"
---
# <a name="renaming-a-wcf-service"></a><span data-ttu-id="0cf5c-102">Renomeando um serviço do WCF</span><span class="sxs-lookup"><span data-stu-id="0cf5c-102">Renaming a WCF Service</span></span>
<span data-ttu-id="0cf5c-103">Este tópico descreve como você pode renomear um serviço do Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="0cf5c-103">This topic describes how you can rename a Windows Communication Foundation (WCF) service.</span></span>  
  
## <a name="renaming-a-wcf-service"></a><span data-ttu-id="0cf5c-104">Renomeando um serviço do WCF</span><span class="sxs-lookup"><span data-stu-id="0cf5c-104">Renaming a WCF Service</span></span>  
 <span data-ttu-id="0cf5c-105">Execute as seguintes etapas para renomear um serviço em um modelo, o Windows Communication Foundation (WCF)</span><span class="sxs-lookup"><span data-stu-id="0cf5c-105">Perform the following steps to rename a service in a Windows Communication Foundation (WCF) template,</span></span>  
  
-   <span data-ttu-id="0cf5c-106">Altere o nome da classe que implementa o serviço.</span><span class="sxs-lookup"><span data-stu-id="0cf5c-106">Change the name of the class that implements the service.</span></span>  
  
-   <span data-ttu-id="0cf5c-107">No arquivo de configuração do serviço, altere o nome do serviço para o novo nome que você escolheu, conforme indicado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="0cf5c-107">In the configuration file of the service, change the name of the service to the new name you have chosen, as indicated in the following example.</span></span> <span data-ttu-id="0cf5c-108">O arquivo de configuração pode ser um arquivo App. config ou Web. config, dependendo de seu modelo de hospedagem.</span><span class="sxs-lookup"><span data-stu-id="0cf5c-108">The configuration file can be either app.config or web.config file depending on your hosting model.</span></span>  
  
```xml  
<system.servicemodel>  
   <services>  
      <service name="WcfService.NewName">  
      </service>  
   </services>  
</system.servicemodel>  
```  
  
-   <span data-ttu-id="0cf5c-109">Se o serviço for webhosted, ele usa um arquivo svc.</span><span class="sxs-lookup"><span data-stu-id="0cf5c-109">If your service is webhosted, it uses an \*.svc file.</span></span> <span data-ttu-id="0cf5c-110">Abra o arquivo svc e modifique o nome do seu serviço, conforme indicado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="0cf5c-110">Open the svc file and modify the name of your service as indicated in the following example.</span></span> <span data-ttu-id="0cf5c-111">Essa etapa não é necessária para aplicativos hospedados automaticamente, pois não há nenhum arquivo svc.</span><span class="sxs-lookup"><span data-stu-id="0cf5c-111">This step is not necessary for self-hosted applications, as there is no svc file.</span></span>  
  
```  
<%@ ServiceHost Service="WcfService.NewName">  
```  
  
## <a name="renaming-a-wcf-service-contract"></a><span data-ttu-id="0cf5c-112">Renomeando um contrato de serviço do WCF</span><span class="sxs-lookup"><span data-stu-id="0cf5c-112">Renaming a WCF Service Contract</span></span>  
  
-   <span data-ttu-id="0cf5c-113">Execute as seguintes etapas para renomear o contrato de serviço</span><span class="sxs-lookup"><span data-stu-id="0cf5c-113">Perform the following steps to rename the service contract,</span></span>  
  
-   <span data-ttu-id="0cf5c-114">Altere o nome do contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="0cf5c-114">Change the name of the service contract.</span></span>  
  
-   <span data-ttu-id="0cf5c-115">No arquivo de configuração do serviço, altere o nome do contrato de serviço para o novo nome que você escolheu, conforme indicado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="0cf5c-115">In the configuration file of the service, change the name of the service contract to the new name you have chosen, as indicated in the following example.</span></span> <span data-ttu-id="0cf5c-116">O arquivo de configuração pode ser um arquivo App. config ou Web. config, dependendo de seu modelo de hospedagem.</span><span class="sxs-lookup"><span data-stu-id="0cf5c-116">The configuration file can be either app.config or web.config file depending on your hosting model.</span></span>  
  
```xml  
<system.servicemodel>  
   <services>  
      <service>  
         <endpoint contract="WcfService.NewContractName" />  
      </service>  
   </services>  
</system.servicemodel>  
```
