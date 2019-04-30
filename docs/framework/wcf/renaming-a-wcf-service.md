---
title: Renomeando um serviço do WCF
ms.date: 03/30/2017
ms.assetid: 14235a65-b1c5-409d-b6cc-a979acd54bbd
ms.openlocfilehash: a215523b92757e3bde1dae2e50de22169020e870
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61955136"
---
# <a name="renaming-a-wcf-service"></a>Renomeando um serviço do WCF
Este tópico descreve como você pode renomear um serviço do Windows Communication Foundation (WCF).  
  
## <a name="renaming-a-wcf-service"></a>Renomeando um serviço do WCF  
 Execute as seguintes etapas para renomear um serviço em um modelo, o Windows Communication Foundation (WCF)  
  
- Altere o nome da classe que implementa o serviço.  
  
- No arquivo de configuração do serviço, altere o nome do serviço para o novo nome que você escolheu, conforme indicado no exemplo a seguir. O arquivo de configuração pode ser o arquivo App. config ou Web. config, dependendo de seu modelo de hospedagem.  
  
```xml  
<system.servicemodel>  
   <services>  
      <service name="WcfService.NewName">  
      </service>  
   </services>  
</system.servicemodel>  
```  
  
- Se seu serviço for webhosted, ele usa um arquivo *. svc. Abra o arquivo svc e modifique o nome do seu serviço, conforme indicado no exemplo a seguir. Essa etapa não é necessária para aplicativos auto-hospedados, pois não há nenhum arquivo svc.  
  
```  
<%@ ServiceHost Service="WcfService.NewName">  
```  
  
## <a name="renaming-a-wcf-service-contract"></a>Renomeando um contrato de serviço do WCF  
  
- Execute as seguintes etapas para renomear o contrato de serviço  
  
- Altere o nome do contrato de serviço.  
  
- No arquivo de configuração do serviço, altere o nome do contrato de serviço para o novo nome que você escolheu, conforme indicado no exemplo a seguir. O arquivo de configuração pode ser o arquivo App. config ou Web. config, dependendo de seu modelo de hospedagem.  
  
```xml  
<system.servicemodel>  
   <services>  
      <service>  
         <endpoint contract="WcfService.NewContractName" />  
      </service>  
   </services>  
</system.servicemodel>  
```
