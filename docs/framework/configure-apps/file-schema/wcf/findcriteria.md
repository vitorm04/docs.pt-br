---
title: '&lt;findCriteria&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5454cd19-6bf5-4ba8-94d1-f58d10dc1917
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: b428d1a95ec6f1f493c831f66223f52e4723990c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ltfindcriteriagt"></a>&lt;findCriteria&gt;
Um elemento de configuração que fornece um conjunto de critérios usados por um aplicativo cliente para pesquisar para um serviço de descoberta. Critérios podem ser agrupados em critérios de pesquisa (especificando quais serviços você está procurando) e localizar os critérios de encerramento (quanto tempo a pesquisa deve durar).  
  
 \<sistema. ServiceModel >  
\<standardEndpoints >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>
    <dynamicEndpoint>
      <standardEndpoint>
        <discoveryClientSettings discoveryEndpoint="String">
          <findCriteria duration="TimeSpan" maxResults="Integer" scopeMatchBy="Uri">
            <contractTypeNames>
              <add name="String" namespace="String" />
            <contractTypeNames>
            <extensions />
            <scopes>
              <add scope="URI" />
            </scopes>
          </findCriteria>
        </discoveryClientSettings>
      </standardEndpoint>
    </dynamicEndpoint>
  </standardEndpoints>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|duration|Um valor de Timespan que especifica o tempo máximo de espera por respostas de serviços na rede. A duração padrão é 20 segundos.|  
|maxResults|Um inteiro que especifica o número máximo de respostas a esperar, de serviços em uma rede ou na Internet. Se máximo respostas são recebidas antes do valor especificado no `duration` atributo tiver decorrido, o término da operação de localizar.|  
|scopeMatchBy|Um URI que especifica o algoritmo de correspondência a ser usado ao casar os escopos na mensagem do Probe com aquela do ponto de extremidade.<br /><br /> Há cinco regras de correspondência de escopo com suporte. Se você não especificar uma regra de correspondência de escopo, `ScopeMatchByPrefix` é usado. Para obter mais informações sobre isso, consulte <xref:System.ServiceModel.Discovery.FindCriteria>.|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<contractTypeNames >](../../../../../docs/framework/configure-apps/file-schema/wcf/contracttypenames.md)|Uma coleção de elementos de configuração que contêm os nomes dos tipos de contrato de serviço de fluxo de trabalho.|  
|\<Extensões > de \<findCriteria >|Uma coleção de objetos do elemento XML que fornecem extensões.|  
|[\<escopos >](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)|Uma coleção de objetos que contêm URIs absolutos que são usados durante uma operação de localização para localizar um serviço específico ou serviços.<br /><br /> Se o serviço específico for encontrado, foi feita uma correspondência entre o URI do serviço e o URI do escopo, às vezes, com a Ajuda das regras de escopo que manipulam complicações de correspondência.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<standardEndpoints >](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|Contém as configurações necessitadas por um aplicativo para participar do processo de descoberta de serviço como um cliente.|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Discovery.FindCriteria>  
 <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>
