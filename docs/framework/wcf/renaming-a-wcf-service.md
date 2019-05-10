---
title: Renomeando um serviço do WCF
ms.date: 03/30/2017
ms.assetid: 14235a65-b1c5-409d-b6cc-a979acd54bbd
ms.openlocfilehash: 8cb86621972423f55bfa18c60c1d4eb60cacb205
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64651057"
---
# <a name="renaming-a-wcf-service"></a><span data-ttu-id="c46f0-102">Renomeando um serviço do WCF</span><span class="sxs-lookup"><span data-stu-id="c46f0-102">Renaming a WCF Service</span></span>
<span data-ttu-id="c46f0-103">Este tópico descreve como você pode renomear um serviço do Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="c46f0-103">This topic describes how you can rename a Windows Communication Foundation (WCF) service.</span></span>  
  
## <a name="renaming-a-wcf-service"></a><span data-ttu-id="c46f0-104">Renomeando um serviço do WCF</span><span class="sxs-lookup"><span data-stu-id="c46f0-104">Renaming a WCF Service</span></span>  
 <span data-ttu-id="c46f0-105">Execute as seguintes etapas para renomear um serviço em um modelo, o Windows Communication Foundation (WCF)</span><span class="sxs-lookup"><span data-stu-id="c46f0-105">Perform the following steps to rename a service in a Windows Communication Foundation (WCF) template,</span></span>  
  
- <span data-ttu-id="c46f0-106">Altere o nome da classe que implementa o serviço.</span><span class="sxs-lookup"><span data-stu-id="c46f0-106">Change the name of the class that implements the service.</span></span>  
  
- <span data-ttu-id="c46f0-107">No arquivo de configuração do serviço, altere o nome do serviço para o novo nome que você escolheu, conforme indicado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="c46f0-107">In the configuration file of the service, change the name of the service to the new name you have chosen, as indicated in the following example.</span></span> <span data-ttu-id="c46f0-108">O arquivo de configuração pode ser o arquivo App. config ou Web. config, dependendo de seu modelo de hospedagem.</span><span class="sxs-lookup"><span data-stu-id="c46f0-108">The configuration file can be either app.config or web.config file depending on your hosting model.</span></span>  
  
```xml  
<system.servicemodel>  
   <services>  
      <service name="WcfService.NewName">  
      </service>  
   </services>  
</system.servicemodel>  
```  
  
- <span data-ttu-id="c46f0-109">Se seu serviço for webhosted, ele usa um arquivo \*. svc.</span><span class="sxs-lookup"><span data-stu-id="c46f0-109">If your service is webhosted, it uses an \*.svc file.</span></span> <span data-ttu-id="c46f0-110">Abra o arquivo svc e modifique o nome do seu serviço, conforme indicado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="c46f0-110">Open the svc file and modify the name of your service as indicated in the following example.</span></span> <span data-ttu-id="c46f0-111">Essa etapa não é necessária para aplicativos auto-hospedados, pois não há nenhum arquivo svc.</span><span class="sxs-lookup"><span data-stu-id="c46f0-111">This step is not necessary for self-hosted applications, as there is no svc file.</span></span>  
  
```  
<%@ ServiceHost Service="WcfService.NewName">  
```  
  
## <a name="renaming-a-wcf-service-contract"></a><span data-ttu-id="c46f0-112">Renomeando um contrato de serviço do WCF</span><span class="sxs-lookup"><span data-stu-id="c46f0-112">Renaming a WCF Service Contract</span></span>  
  
- <span data-ttu-id="c46f0-113">Execute as seguintes etapas para renomear o contrato de serviço</span><span class="sxs-lookup"><span data-stu-id="c46f0-113">Perform the following steps to rename the service contract,</span></span>  
  
- <span data-ttu-id="c46f0-114">Altere o nome do contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="c46f0-114">Change the name of the service contract.</span></span>  
  
- <span data-ttu-id="c46f0-115">No arquivo de configuração do serviço, altere o nome do contrato de serviço para o novo nome que você escolheu, conforme indicado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="c46f0-115">In the configuration file of the service, change the name of the service contract to the new name you have chosen, as indicated in the following example.</span></span> <span data-ttu-id="c46f0-116">O arquivo de configuração pode ser o arquivo App. config ou Web. config, dependendo de seu modelo de hospedagem.</span><span class="sxs-lookup"><span data-stu-id="c46f0-116">The configuration file can be either app.config or web.config file depending on your hosting model.</span></span>  
  
```xml  
<system.servicemodel>  
   <services>  
      <service>  
         <endpoint contract="WcfService.NewContractName" />  
      </service>  
   </services>  
</system.servicemodel>  
```
