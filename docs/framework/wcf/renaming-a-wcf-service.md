---
title: Renomeando um serviço do WCF
ms.date: 03/30/2017
ms.assetid: 14235a65-b1c5-409d-b6cc-a979acd54bbd
ms.openlocfilehash: 1179e7b235130e1967c79843b7a11f55622a01fb
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: pt-BR
ms.lasthandoff: 07/07/2020
ms.locfileid: "86052046"
---
# <a name="renaming-a-wcf-service"></a><span data-ttu-id="6409b-102">Renomeando um serviço do WCF</span><span class="sxs-lookup"><span data-stu-id="6409b-102">Renaming a WCF Service</span></span>
<span data-ttu-id="6409b-103">Este tópico descreve como você pode renomear um serviço do Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="6409b-103">This topic describes how you can rename a Windows Communication Foundation (WCF) service.</span></span>  
  
## <a name="renaming-a-wcf-service"></a><span data-ttu-id="6409b-104">Renomeando um serviço do WCF</span><span class="sxs-lookup"><span data-stu-id="6409b-104">Renaming a WCF Service</span></span>  
 <span data-ttu-id="6409b-105">Execute as seguintes etapas para renomear um serviço em um modelo Windows Communication Foundation (WCF),</span><span class="sxs-lookup"><span data-stu-id="6409b-105">Perform the following steps to rename a service in a Windows Communication Foundation (WCF) template,</span></span>  
  
- <span data-ttu-id="6409b-106">Altere o nome da classe que implementa o serviço.</span><span class="sxs-lookup"><span data-stu-id="6409b-106">Change the name of the class that implements the service.</span></span>  
  
- <span data-ttu-id="6409b-107">No arquivo de configuração do serviço, altere o nome do serviço para o novo nome que você escolheu, conforme indicado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="6409b-107">In the configuration file of the service, change the name of the service to the new name you have chosen, as indicated in the following example.</span></span> <span data-ttu-id="6409b-108">O arquivo de configuração pode ser app.config ou web.config arquivo, dependendo do modelo de hospedagem.</span><span class="sxs-lookup"><span data-stu-id="6409b-108">The configuration file can be either app.config or web.config file depending on your hosting model.</span></span>  
  
```xml  
<system.servicemodel>  
   <services>  
      <service name="WcfService.NewName">  
      </service>  
   </services>  
</system.servicemodel>  
```  
  
- <span data-ttu-id="6409b-109">Se o serviço for webhostd, ele usará um arquivo \* \* . svc\* .</span><span class="sxs-lookup"><span data-stu-id="6409b-109">If your service is webhosted, it uses an *\*.svc* file.</span></span> <span data-ttu-id="6409b-110">Abra o arquivo svc e modifique o nome do serviço, conforme indicado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="6409b-110">Open the svc file and modify the name of your service as indicated in the following example.</span></span> <span data-ttu-id="6409b-111">Essa etapa não é necessária para aplicativos hospedados internamente, pois não há nenhum arquivo svc.</span><span class="sxs-lookup"><span data-stu-id="6409b-111">This step is not necessary for self-hosted applications, as there is no svc file.</span></span>  
  
```aspx-csharp
<%@ ServiceHost Service="WcfService.NewName">  
```  
  
## <a name="renaming-a-wcf-service-contract"></a><span data-ttu-id="6409b-112">Renomeando um contrato de serviço WCF</span><span class="sxs-lookup"><span data-stu-id="6409b-112">Renaming a WCF Service Contract</span></span>  
  
- <span data-ttu-id="6409b-113">Execute as seguintes etapas para renomear o contrato de serviço,</span><span class="sxs-lookup"><span data-stu-id="6409b-113">Perform the following steps to rename the service contract,</span></span>  
  
- <span data-ttu-id="6409b-114">Altere o nome do contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="6409b-114">Change the name of the service contract.</span></span>  
  
- <span data-ttu-id="6409b-115">No arquivo de configuração do serviço, altere o nome do contrato de serviço para o novo nome que você escolheu, conforme indicado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="6409b-115">In the configuration file of the service, change the name of the service contract to the new name you have chosen, as indicated in the following example.</span></span> <span data-ttu-id="6409b-116">O arquivo de configuração pode ser app.config ou web.config arquivo, dependendo do modelo de hospedagem.</span><span class="sxs-lookup"><span data-stu-id="6409b-116">The configuration file can be either app.config or web.config file depending on your hosting model.</span></span>  
  
```xml  
<system.servicemodel>  
   <services>  
      <service>  
         <endpoint contract="WcfService.NewContractName" />  
      </service>  
   </services>  
</system.servicemodel>  
```
