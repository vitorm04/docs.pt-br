---
title: <Assembly> (.NET Nativo)
ms.date: 03/30/2017
ms.assetid: cfe629eb-1106-4113-86e1-052f402d8d8b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c0788c05edace2142d348c679c73aa1b4404ce75
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61868856"
---
# <a name="assembly-element-net-native"></a>\<Assembly > (.NET nativo)
Aplica a política de reflexão de tempo de execução a todos os tipos em um assembly especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<Assembly Name="assembly_name"   
          Activate="policy_setting"  
          Browse="policy_setting"  
          Dynamic="policy_setting"  
          Serialize="policy_setting"  
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
|`Name`|Geral|Atributo obrigatório. Especifica o nome simples de um assembly.|  
|`Activate`|Reflexão|Atributo opcional. Controla o acesso de tempo de execução a construtores para habilitar a ativação de instâncias.|  
|`Browse`|Reflexão|Atributo opcional. Controla consultas para obter informações sobre os tipos no assembly ou para enumerá-los, mas não permite qualquer acesso dinâmico no tempo de execução.|  
|`Dynamic`|Reflexão|Atributo opcional. Controla o acesso a todos os tipos de membro ao tempo de execução, incluindo construtores, métodos, campos, propriedades e eventos, habilitando a programação dinâmica.|  
|`Serialize`|Serialização|Atributo opcional. Controla o acesso ao tempo de execução para construtores, campos e propriedades para habilitar a serialização e desserialização das instâncias por bibliotecas como o serializador Newtonsoft JSON.|  
|`DataContractSerializer`|Serialização|Atributo opcional. Controla a política de serialização que usa a classe <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>.|  
|`DataContractJsonSerializer`|Serialização|Atributo opcional. Controla a política de serialização JSON que usa a classe <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType>.|  
|`XmlSerializer`|Serialização|Atributo opcional. Controla a política de serialização XML que usa a classe <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>.|  
|`MarshalObject`|Interoperabilidade|Atributo opcional. Política de controles de marshaling de tipos de referência para o Tempo de Execução do Windows e COM.|  
|`MarshalDelegate`|Interoperabilidade|Atributo opcional. Controla a diretiva de marshaling de tipos delegados como ponteiros de função para código nativo.|  
|`MarshalStructure`|Interoperabilidade|Atributo opcional. Controla a política de estruturas de marshaling para código nativo.|  
  
## <a name="name-attribute"></a>Atributo de nome  
  
|Valor|Descrição|  
|-----------|-----------------|  
|*assembly_name*|O nome simples do assembly, sem a extensão de arquivo. Este atributo corresponde à propriedade <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> . Por exemplo, o nome de um assembly denominado Extensions.dll é "Extensions".<br /><br /> Você também pode especificar a cadeia de caracteres literal `*Application*` para aplicar a política a todos os assemblies no pacote de aplicativos, sejam os assemblies carregados ou não. `*Application*` nunca aplica-se à política para assemblies .NET Framework.|  
  
## <a name="all-other-attributes"></a>Todos os outros atributos  
  
|Valor|Descrição|  
|-----------|-----------------|  
|*policy_setting*|A configuração a ser aplicada a este tipo de política para todos os tipos no assembly. Os valores possíveis são `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal` e `Required All`. Para obter mais informações, consulte [Configurações da política da diretiva de tempo de execução](../../../docs/framework/net-native/runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<Namespace>](../../../docs/framework/net-native/namespace-element-net-native.md)|Aplica a política de reflexão de tempo de execução a todos os tipos em um namespace filho.|  
|[\<Type>](../../../docs/framework/net-native/type-element-net-native.md)|Aplica a política de reflexão a um tipo.|  
|[\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|Aplica a política de reflexão a um tipo genérico construído.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<Application>](../../../docs/framework/net-native/application-element-net-native.md)|Serve como um contêiner para os tipos amplos de aplicativos cujos metadados estão disponíveis para reflexão no tempo de execução. O elemento [\<Application>](../../../docs/framework/net-native/application-element-net-native.md) pode ter zero, um ou mais elementos `<Assembly>`.|  
|[\<Library>](../../../docs/framework/net-native/library-element-net-native.md)|Define o assembly que contém tipos e membros de tipo cujos metadados estão disponíveis para reflexão em tempo de execução. O elemento [\<Library>](../../../docs/framework/net-native/library-element-net-native.md) pode ter zero, um ou mais elementos `<Assembly>`.|  
  
## <a name="remarks"></a>Comentários  
 O elemento `<Assembly>` define a política de tempo de execução para todos os tipos em um assembly. Ele é diferente do elemento [\<Library>](../../../docs/framework/net-native/library-element-net-native.md), que especifica uma biblioteca, mas depende de seus elementos filho para definir a política de reflexão em tempo de execução. O elemento `<Assembly>` aplica-se a todos os tipos em um assembly, a menos que eles sejam substituídos por um elemento filho.  
  
 O exemplo a seguir mostra como é possível aplicar a política em tempo de execução a todos os tipos em assemblies no pacote do aplicativo atribuindo o atributo `Name` a um valor de “*Application\*”. O elemento `<Assembly>` deve ser filho do elemento [\<Application>](../../../docs/framework/net-native/application-element-net-native.md).  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">   
  <Application>   
     <Assembly Name="*Application*" Dynamic="Required All" />   
  </Application>   
</Directives>  
```  
  
 Os atributos `Activate`, `Browse`, `Dynamic` e `Serialize` são todos opcionais. No entanto, o elemento `<Assembly>` deve conter pelo menos um desses atributos.  
  
## <a name="see-also"></a>Consulte também

- [Configurações da política da diretiva de tempo de execução](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
- [Referência do arquivo de configuração das diretivas de tempo de execução (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [Elementos da diretiva de tempo de execução](../../../docs/framework/net-native/runtime-directive-elements.md)
