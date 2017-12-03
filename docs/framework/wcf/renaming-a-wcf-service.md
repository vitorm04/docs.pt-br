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
# <a name="renaming-a-wcf-service"></a>Renomeando um serviço do WCF
Este tópico descreve como você pode renomear um [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] serviço.  
  
## <a name="renaming-a-wcf-service"></a>Renomeando um serviço do WCF  
 Execute as seguintes etapas para renomear um serviço em um [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] modelo  
  
-   Altere o nome da classe que implementa o serviço.  
  
-   No arquivo de configuração do serviço, altere o nome do serviço para o novo nome que você escolheu, conforme indicado no exemplo a seguir. O arquivo de configuração pode ser um arquivo App. config ou Web. config, dependendo de seu modelo de hospedagem.  
  
```xml  
<system.servicemodel>  
   <services>  
      <service name="WcfService.NewName">  
      </service>  
   </services>  
</system.servicemodel>  
```  
  
-   Se o serviço for webhosted, ele usa um arquivo svc. Abra o arquivo svc e modifique o nome do seu serviço, conforme indicado no exemplo a seguir. Essa etapa não é necessária para aplicativos hospedados automaticamente, pois não há nenhum arquivo svc.  
  
```  
<%@ ServiceHost Service="WcfService.NewName">  
```  
  
## <a name="renaming-a-wcf-service-contract"></a>Renomeando um contrato de serviço do WCF  
  
-   Execute as seguintes etapas para renomear o contrato de serviço  
  
-   Altere o nome do contrato de serviço.  
  
-   No arquivo de configuração do serviço, altere o nome do contrato de serviço para o novo nome que você escolheu, conforme indicado no exemplo a seguir. O arquivo de configuração pode ser um arquivo App. config ou Web. config, dependendo de seu modelo de hospedagem.  
  
```xml  
<system.servicemodel>  
   <services>  
      <service>  
         <endpoint contract="WcfService.NewContractName" />  
      </service>  
   </services>  
</system.servicemodel>  
```
