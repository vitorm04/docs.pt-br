---
title: Elemento &lt;AttributeImplies&gt; (.NET Nativo)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 82db7193-a860-418b-84fc-fff2fdf2e025
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 92a886ab09978aef6694c37d74af49b27c37c6c4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltattributeimpliesgt-element-net-native"></a>Elemento &lt;AttributeImplies&gt; (.NET Nativo)
Define a política para os elementos de código ao qual o atributo recipiente é aplicado.  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<AttributeImplies Activate="policy_type"  
                  Browse="policy_type"  
                  Dynamic="policy_type"  
                  Serialize="policy_type"   
                  DataContractSerializer="policy_setting"  
                  DataContractJsonSerializer="policy_setting"  
                  XmlSerializer="policy_setting"  
                  MarshalObject="policy_setting"  
                  MarshalDelegate="policy_setting"  
                  MarshalStructure="policy_setting" />  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Tipo de atributo|Descrição|  
|---------------|--------------------|-----------------|  
|`Activate`|Reflexão|Atributo opcional. Controla o acesso de tempo de execução a construtores para habilitar a ativação de instâncias.|  
|`Browse`|Reflexão|Atributo opcional. Controla a consulta para obter informações sobre elementos do programa, mas não permite qualquer acesso de tempo de execução.|  
|`Dynamic`|Reflexão|Atributo opcional. Controla o acesso a todos os tipos de membro ao tempo de execução, incluindo construtores, métodos, campos, propriedades e eventos, habilitando a programação dinâmica.|  
|`Serialize`|Serialização|Atributo opcional. Controla o acesso ao tempo de execução para construtores, campos e propriedades para habilitar a serialização e desserialização das instâncias por bibliotecas como o serializador Newtonsoft JSON.|  
|`DataContractSerializer`|Serialização|Atributo opcional. Controla a política de serialização que usa a classe <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>.|  
|`DataContractJsonSerializer`|Serialização|Atributo opcional. Controla a política de serialização JSON que usa a classe <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType>.|  
|`XmlSerializer`|Serialização|Atributo opcional. Controla a política de serialização XML que usa a classe <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>.|  
|`MarshalObject`|Interoperabilidade|Atributo opcional. Política de controles de marshaling de tipos de referência para o Tempo de Execução do Windows e COM.|  
|`MarshalDelegate`|Interoperabilidade|Atributo opcional. Controla a diretiva de marshaling de tipos delegados como ponteiros de função para código nativo.|  
|`MarshalStructure`|Interoperabilidade|Atributo opcional. Controla a política de marshaling de tipos de valor para código nativo.|  
  
## <a name="all-attributes"></a>Todos os atributos  
  
|Valor|Descrição|  
|-----------|-----------------|  
|*policy_setting*|A configuração a ser aplicada a este tipo de política. Os valores possíveis são `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal` e `Required All`. Para obter mais informações, consulte [Configurações da política da diretiva de tempo de execução](../../../docs/framework/net-native/runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<Type>](../../../docs/framework/net-native/type-element-net-native.md)|Aplica a política de reflexão a um tipo e todos os seus membros.|  
  
## <a name="remarks"></a>Comentários  
 O elemento `<AttributeImplies>` é usado se o seu tipo recipiente for um atributo (isto é, uma classe derivada de <xref:System.Attribute?displayProperty=nameWithType>). Se o atributo for aplicado a um elemento de programa específico, a política definida pelo elemento `<AttributeImplies>` aplica-se a esse elemento de programa.  
  
 Os atributos de reflexão, serialização e interoperabilidade são todos opcionais, embora pelo menos um deve estar presente.  
  
## <a name="see-also"></a>Consulte também  
 [\<Tipo > elemento](../../../docs/framework/net-native/type-element-net-native.md)  
 [Referência do arquivo de configuração das diretivas de tempo de execução (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [Elementos da diretiva de tempo de execução](../../../docs/framework/net-native/runtime-directive-elements.md)  
 [Configurações da política da diretiva de tempo de execução](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
