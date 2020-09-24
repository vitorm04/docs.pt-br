---
title: <protocolMapping>
ms.date: 03/30/2017
ms.assetid: 5076644b-1f33-4f26-9488-87de9fcda04c
ms.openlocfilehash: 0a79aa18c74ddb8ec47f02620d16d391b4a36b68
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91162290"
---
# \<protocolMapping>

Representa uma seção de configuração para definir um conjunto de mapeamentos de protocolo padrão entre esquemas de protocolo de transporte (por exemplo, http, net. TCP, net. pipe, etc.) e associações do WCF. Ao criar pontos de extremidade padrão em tempo de execução, Windows Communication Foundation (WCF) examina os mapeamentos configurados e decide qual associação usar para um endereço baseado em particular.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<protocolMapping>**  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<protocolMapping>
  <add binding="String"
       bindingConfiguration="String"
       scheme="http/net.msmq/net.pipe/net.tcp" />
</protocolMapping>
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  

 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  

 Nenhum.  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<filters>](filters-of-routing.md)|Contém um mapeamento de protocolo padrão entre um esquema de protocolo de transporte (por exemplo, http, net. TCP, net. pipe, etc.) e uma associação do WCF.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<system.serviceModel>](system-servicemodel.md)|O elemento raiz de todos os elementos de configuração do WCF.|  
  
## <a name="example"></a>Exemplo  

 O exemplo de configuração a seguir mostra o mapeamento de protocolo padrão no arquivo de machine.config. Você pode substituir esse mapeamento padrão no nível do computador modificando o arquivo de machine.config. Ou, se você quiser apenas substituí-lo no escopo de um aplicativo, poderá substituir esta seção no arquivo de configuração do aplicativo e alterar o mapeamento para esquemas de protocolo individuais.  
  
```xml  
<protocolMapping>
  <add scheme="http"
       binding="basicHttpBinding" />
  <add scheme="net.tcp"
       binding="netTcpBinding" />
  <add scheme="net.pipe"
       binding="netNamedPipeBinding" />
  <add scheme="net.msmq"
       binding="netMsmqBinding" />
</protocolMapping>
```  
  
## <a name="see-also"></a>Confira também

- <xref:System.ServiceModel.Configuration.ProtocolMappingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Configuration.ProtocolMappingElement?displayProperty=nameWithType>
