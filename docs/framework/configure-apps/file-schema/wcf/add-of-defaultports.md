---
title: <add> De <defaultPorts>
ms.date: 03/30/2017
ms.assetid: f162ce42-963b-4779-96a7-d6d8b4ea0d2f
ms.openlocfilehash: 799715ef008274ead6b745e8ab97e769cb59e6b5
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55261588"
---
# <a name="add-of-defaultports"></a>\<Adicionar > de \<defaultPorts >
Um comunicação ponto de extremidade padrão que o aplicativo cliente ouve.  
  
 \<system.ServiceModel>  
\<comportamentos >  
\<serviceBehaviors>  
\<behavior>  
\<useRequestHeadersForMetadataAddress>  
\<defaultPorts>  
\<add>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add port="Integer"
         scheme="String" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|porta|Um inteiro que especifica o número de porta de comunicação padrão|  
|esquema|Uma cadeia de caracteres que especifica o grupo de configurações de protocolo associado a uma porta de comunicação.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<defaultPorts>](../../../../../docs/framework/configure-apps/file-schema/wcf/defaultports.md)|Uma coleção de portas padrão listando os pontos de extremidade de comunicação padrão que o aplicativo cliente ouve.|  
  
## <a name="see-also"></a>Consulte também
- <xref:System.ServiceModel.Configuration.DefaultPortElement>
