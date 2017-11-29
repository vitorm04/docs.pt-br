---
title: '&lt;protocolMapping&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5076644b-1f33-4f26-9488-87de9fcda04c
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 769ca7b96c3671fdd1b154c99516778f7cbd542e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="ltprotocolmappinggt"></a>&lt;protocolMapping&gt;
Representa uma seção de configuração para definir um conjunto de mapeamento de padrão de protocolo entre esquemas de protocolo de transporte (por exemplo, http, net.tcp, NET. pipe, etc.) e as associações do WCF. Durante a criação de pontos de extremidade padrão em tempo de execução, [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] examina os mapeamentos configurados e decide em qual associação a ser usado para um determinado com base em endereço.  
  
 \<System. ServiceModel >  
\<protocolMapping >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml
   <protocolMapping>    <add binding="String"         bindingConfiguration="String"         scheme="http/net.msmq/net.pipe/net.tcp"/></protocolMapping>  
```

## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
 nenhuma.  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<Filtros >](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|Contém um mapeamento de protocolo padrão entre um esquema de protocolo de transporte (por exemplo, http, net.tcp, NET. pipe, etc.) e uma associação WCF.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|sistema.ServiceModel|O elemento raiz de todos os elementos de configuração do WCF.|  
  
## <a name="example"></a>Exemplo  
 O exemplo de configuração a seguir mostra o mapeamento de padrão de protocolo no arquivo Machine. config. Você pode substituir esse mapeamento padrão no nível do computador, modificando o arquivo Machine. config. Ou, se você apenas deseja substituí-la dentro do escopo de um aplicativo, você pode substituir esta seção dentro de seu arquivo de configuração do aplicativo e alterar o mapeamento para esquemas de protocolo individual.  
  
```xml  
<protocolMapping>  
        <add scheme="http" binding="basicHttpBinding"/>  
        <add scheme="net.tcp" binding="netTcpBinding"/>  
        <add scheme="net.pipe" binding="netNamedPipeBinding"/>  
        <add scheme="net.msmq" binding="netMsmqBinding"/>  
</protocolMapping>  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Configuration.ProtocolMappingSection?displayProperty=nameWithType>       
 <xref:System.ServiceModel.Configuration.ProtocolMappingElement?displayProperty=nameWithType>    
