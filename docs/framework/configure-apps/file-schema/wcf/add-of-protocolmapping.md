---
title: '&lt;adicionar&gt; &lt;protocolMapping&gt;'
ms.date: 03/30/2017
ms.assetid: 08e62249-1641-41d1-91b1-66d7b46244e4
ms.openlocfilehash: b9559a6921bdededf760f54f58abadb46612b174
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltaddgt-of-ltprotocolmappinggt"></a>&lt;adicionar&gt; &lt;protocolMapping&gt;
Representa um mapeamento de protocolo padrão entre um esquema de protocolo de transporte (por exemplo, http, net.tcp, NET. pipe, etc.) e uma associação do Windows Communication Foundation (WCF). Durante a criação de pontos de extremidade padrão em tempo de execução, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] examina os mapeamentos configurados e decide em qual associação a ser usado para um determinado com base em endereço.  
  
 \<system.serviceModel>  
\<protocolMapping >  
\<add>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml
   <protocolMapping>    <add binding="String"         bindingConfiguration="String"         scheme="http/net.msmq/net.pipe/net.tcp"/></protocolMapping>
```

## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|associação|Uma cadeia de caracteres que especifica o tipo de associação a ser usado para um ponto de extremidade durante a criação do ponto de extremidade padrão.|  
|bindingConfiguration|Uma cadeia de caracteres que especifica o nome da seção de configuração de associação a ser referenciado.|  
|esquema|O esquema de protocolo de transporte a ser usado para o ponto de extremidade padrão.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<protocolMapping >](../../../../../docs/framework/configure-apps/file-schema/wcf/protocolmapping.md)|Representa uma seção de configuração para definir mapeamentos de protocolo padrão entre esquemas de protocolo de transporte (por exemplo, http, net.tcp, NET. pipe, etc.) e as associações do Windows Communication Foundation (WCF).|  
  
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
