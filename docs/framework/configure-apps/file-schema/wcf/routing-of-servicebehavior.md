---
title: '&lt;roteamento&gt; de &lt;serviceBehavior&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d8f9c844-4629-4a45-9599-856dc8f01794
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4e5c27b2b276e6659680dabfd9460c6d072bad3a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="ltroutinggt-of-ltservicebehaviorgt"></a>&lt;roteamento&gt; de &lt;serviceBehavior&gt;
Fornece acesso de tempo de execução para o serviço de roteamento para permitir a modificação dinâmica da configuração de roteamento.  
  
 \<sistema. ServiceModel >  
\<comportamentos >  
\<serviceBehaviors >  
\<comportamento >  
\<roteamento >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <routing filterTable="String" 
               routeOnHeadersOnly="Boolean" 
               SoapProcessingEnabled="Boolean" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|filterTable|Uma cadeia de caracteres que especifica o nome da tabela de roteamento que contém os filtros a ser avaliada pelo serviço de roteamento. Esse valor deve corresponder a `name` atributo de um [ \<filterTable >](../../../../../docs/framework/configure-apps/file-schema/wcf/filtertable.md) elemento o [ \<filterTables >](../../../../../docs/framework/configure-apps/file-schema/wcf/filtertables.md) seção.|  
|routeOnHeaderOnly|Um valor booleano que especifica se o filtro examinará o corpo da mensagem e o cabeçalho ou apenas o cabeçalho. O padrão é `true`.|  
|soapProcessingEnabled|Um valor booleano que especifica se o processamento SOAP deve ocorrer.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<comportamento >](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Especifica um elemento de comportamento.|  
  
## <a name="remarks"></a>Comentários  
 Quando adicionado à configuração de comportamento do serviço, este elemento de configuração permite que o roteamento para o serviço. Você pode especificar a tabela de roteamento real a ser usada pelo serviço neste elemento.  
  
 Usando esta seção de configuração, você pode alterar as configurações de roteamentos em tempo real quando o padrão de implantação é alterado. Em tempo de execução, você pode registrar sua própria extensão de roteamento com novas configurações de roteamentos e o serviço de roteamento será iniciado usando as informações de configuração atualizados para novas mensagens e sessões, deixando mensagens em trânsito/sessões usando quaisquer regras foram Coloque quando foram iniciados.  Isso lhe dá a capacidade de fazer a reconfiguração de sessão segura, sem a reciclagem do serviço de roteamento em tempo de execução.  
  
