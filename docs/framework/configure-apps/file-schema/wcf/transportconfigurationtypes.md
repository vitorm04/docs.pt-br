---
title: <transportConfigurationTypes>
ms.date: 03/30/2017
ms.assetid: 929c8b0a-5460-4f66-a098-2cb8d4e10b69
ms.openlocfilehash: bfd2147a8e772848fc98cab7a875a51bdb53b5cc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69941166"
---
# <a name="transportconfigurationtypes"></a>\<transportConfigurationTypes>
Representa uma coleção de elementos de configuração que identificam o tipo de um transporte específico. Isso pode ser usado para adicionar protocolos WAS personalizados.  
  
 \<system.ServiceModel>  
\<ServiceHostingEnvironment>  
\<transportConfigurationTypes>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<serviceHostingEnvironment>
  <transportConfigurationTypes>
    <add name="String"
         transportConfigurationType="String" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|name|O nome do transporte|  
|transportConfigurationType|O tipo que implementa o transporte|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<add>](add-of-transportconfigurationtype.md)|Adiciona um elemento de configuração que identifica o tipo de um transporte específico.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<serviceHostingEnvironment>](servicehostingenvironment.md)|Define o tipo que o ambiente de Hospedagem de serviço instancia para um transporte específico.|  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- <xref:System.ServiceModel.Configuration.TransportConfigurationTypeElementCollection>
- [Hospedagem](../../../wcf/feature-details/hosting.md)
