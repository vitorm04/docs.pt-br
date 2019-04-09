---
title: <protocolMapping>
ms.date: 03/30/2017
ms.assetid: 5076644b-1f33-4f26-9488-87de9fcda04c
ms.openlocfilehash: e26044340bda84fe38b7e286edf833affa94b86c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59118203"
---
# <a name="protocolmapping"></a>\<protocolMapping>
Representa uma seção de configuração para definir um conjunto padrão de mapeamento de protocolo entre esquemas de protocolo de transporte (por exemplo, http, NET. TCP, NET. pipe, etc.) e associações do WCF. Durante a criação de pontos de extremidade padrão em tempo de execução, o Windows Communication Foundation (WCF) analisa os mapeamentos configurados e decide em qual associação a ser usado para um determinado endereço de base.  
  
[**\<system.serviceModel>**](system-servicemodel.md)  
&nbsp;&nbsp;**\<protocolMapping>**  
  
## <a name="syntax"></a>Sintaxe  
  
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
 nenhuma.  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<filters>](filters-of-routing.md)|Contém um mapeamento de protocolo padrão entre um esquema de protocolo de transporte (por exemplo, http, NET. TCP, NET. pipe, etc.) e uma associação do WCF.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<system.serviceModel>](system-servicemodel.md)|O elemento raiz de todos os elementos de configuração do WCF.|  
  
## <a name="example"></a>Exemplo  
 O exemplo de configuração a seguir mostra o mapeamento de protocolo padrão no arquivo Machine. config. Você pode substituir esse mapeamento padrão no nível do computador, modificando o arquivo Machine. config. Ou, se você quiser apenas substituí-la dentro do escopo de um aplicativo, você pode substituir essa seção dentro de seu arquivo de configuração de aplicativo e alterar o mapeamento para esquemas de protocolo individual.  
  
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
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Configuration.ProtocolMappingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Configuration.ProtocolMappingElement?displayProperty=nameWithType>
