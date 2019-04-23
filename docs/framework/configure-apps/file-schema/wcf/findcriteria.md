---
title: <findCriteria>
ms.date: 03/30/2017
ms.assetid: 5454cd19-6bf5-4ba8-94d1-f58d10dc1917
ms.openlocfilehash: eaa3998d3d0b1642c0c92380ec1228eea69d4da8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59129540"
---
# <a name="findcriteria"></a>\<findCriteria>
Um elemento de configuração que fornece um conjunto de critérios utilizados por um aplicativo cliente para pesquisar para um serviço de descoberta. Critérios podem ser agrupados em critérios de pesquisa (especificando quais serviços você está procurando) e encontre os critérios de término (quanto tempo a pesquisa deve durar).  
  
 \<system.ServiceModel>  
\<standardEndpoints>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <dynamicEndpoint>
      <standardEndpoint>
        <discoveryClientSettings discoveryEndpoint="String">
          <findCriteria duration="TimeSpan"
                        maxResults="Integer"
                        scopeMatchBy="Uri">
            <contractTypeNames>
              <add name="String"
                   namespace="String" />
            </contractTypeNames>
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
|maxResults|Um inteiro que especifica o número máximo de respostas a esperar, de serviços em uma rede ou Internet. Se o máximo respostas são recebidas antes do valor especificado no `duration` atributo tiver decorrido, o término da operação de localizar.|  
|scopeMatchBy|Um URI que especifica o algoritmo correspondente a ser usado ao casar os escopos na mensagem do Probe com isso do ponto de extremidade.<br /><br /> Há cinco regras de correspondência de escopo com suporte. Se você não especificar uma regra de correspondência de escopo, `ScopeMatchByPrefix` é usado. Para obter mais informações sobre isso, consulte <xref:System.ServiceModel.Discovery.FindCriteria>.|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<contractTypeNames>](../../../../../docs/framework/configure-apps/file-schema/wcf/contracttypenames.md)|Uma coleção de elementos de configuração que contêm os nomes dos tipos de contrato de serviço de fluxo de trabalho.|  
|\<Extensões > de \<findCriteria >|Uma coleção de objetos de elemento XML que fornecem extensões.|  
|[\<scopes>](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)|Uma coleção de objetos que contêm URIs absolutos que são usados durante uma operação de localização para localizar um serviço específico ou serviços.<br /><br /> Se o serviço específico for encontrado, foi feita uma correspondência bem-sucedida entre o URI do serviço e o URI de escopo, às vezes, com a Ajuda das regras de escopo que lidam com complicações de correspondência.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<standardEndpoints>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|Contém as configurações necessitadas por um aplicativo para participar do processo de descoberta de serviço como um cliente.|  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Discovery.FindCriteria>
- <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>
