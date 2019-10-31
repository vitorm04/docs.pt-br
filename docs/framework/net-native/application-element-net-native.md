---
title: <Application> (.NET Nativo)
ms.date: 03/30/2017
ms.assetid: b4e9b37a-059b-4076-8f56-cb3f9cef0cd9
ms.openlocfilehash: e26826b3d8674b536ab0897182da58bc02cfd00b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128526"
---
# <a name="application-element-net-native"></a>Elemento de > de aplicativo \<(.NET Native)
Serve como um contêiner para tipos em todo o aplicativo e membros de tipo cujos metadados estão disponível para reflexão no tempo de execução e aplica-se à política de reflexão no tempo de execução a todos os elementos de programa em um aplicativo.  
  
 Elemento \<Directives>  
Elemento \<Application> (rd.xml)  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<Application Activate="policy_setting"  
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
 As seções a seguir descrevem atributos, elementos filho e elementos pai. Na tabela Elementos Filhos, a política refere-se ao tipo de metadados que é disponibilizado para elementos de programa específicos no tempo de execução.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Tipo de atributo|Descrição|  
|---------------|--------------------|-----------------|  
|`Activate`|Reflexão|Atributo opcional. Controla o acesso de tempo de execução a construtores para habilitar a ativação de instâncias.|  
|`Browse`|Reflexão|Atributo opcional. Controla consultas para obter informações sobre os tipos ou para enumerá-los, mas não permite qualquer acesso dinâmico no tempo de execução.|  
|`Dynamic`|Reflexão|Atributo opcional. Controla o acesso a todos os tipos de membro ao tempo de execução, incluindo construtores, métodos, campos, propriedades e eventos, habilitando a programação dinâmica.|  
|`Serialize`|Serialização|Atributo opcional. Controla o acesso ao tempo de execução para construtores, campos e propriedades para habilitar a serialização e desserialização das instâncias por bibliotecas como o serializador Newtonsoft JSON.|  
|`DataContractSerializer`|Serialização|Atributo opcional. Controla a política de serialização que usa a classe <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>.|  
|`DataContractJsonSerializer`|Serialização|Atributo opcional. Controla a política de serialização JSON que usa a classe <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType>.|  
|`XmlSerializer`|Serialização|Atributo opcional. Controla a política de serialização XML que usa a classe <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>.|  
|`MarshalObject`|Interoperabilidade|Atributo opcional. Política de controles de marshaling de tipos de referência para o Tempo de Execução do Windows e COM.|  
|`MarshalDelegate`|Interoperabilidade|Atributo opcional. Controla a diretiva de marshaling de tipos delegados como ponteiros de função para código nativo.|  
|`MarshalStructure`|Interoperabilidade|Atributo opcional. Controla a política de estruturas de marshaling para código nativo.|  
  
## <a name="all-attributes"></a>Todos os atributos  
  
|Valor|Descrição|  
|-----------|-----------------|  
|*policy_setting*|A configuração para essa política para ser aplicada aos tipos no aplicativo. Os valores possíveis são `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal` e `Required All`. Para obter mais informações, consulte [Configurações da política da diretiva de tempo de execução](runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<Assembly>](assembly-element-net-native.md)|Aplica a política a todos os tipos em um assembly específico.|  
|[\<Namespace>](namespace-element-net-native.md)|Aplica a política a todos os tipos em um namespace específico.|  
|[\<Type>](type-element-net-native.md)|Aplica a política a um tipo específico, como uma classe ou estrutura.|  
|[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|Aplica a política a um tipo genérico construído. Por exemplo, um elemento [\<TypeInstantiation>](typeinstantiation-element-net-native.md) pode ser usado para definir a política para um tipo `List<String>`.|  
|[\<Method>](method-element-net-native.md)|Aplica a política a um método em um tipo específico.|  
|[\<MethodInstantiation>](methodinstantiation-element-net-native.md)|Aplica a política a um tipo genérico construído.|  
|[\<Property>](property-element-net-native.md)|Aplica a política a uma propriedade em um tipo específico.|  
|[\<Field>](field-element-net-native.md)|Aplica a política a um campo em um tipo específico.|  
|[\<Event>](event-element-net-native.md)|Aplica a política a um evento em um determinado tipo.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<Directives>](directives-element-net-native.md)|O elemento raiz de um arquivo de diretivas de tempo de execução.|  
  
## <a name="remarks"></a>Comentários  
 O elemento [\<Directives>](directives-element-net-native.md) pode conter zero ou um elemento `<Application>`. Vários elementos `<Application>` em um mesmo arquivo de diretivas de reflexão não são suportados.  
  
 O elemento `<Application>` pode ser usado em uma de duas formas:  
  
- Como um contêiner para definir os elementos do programa cujos metadados são necessários no tempo de execução. Nesse caso, o elemento `<Application>` não precisa ter todos os atributos. No tempo de compilação, as ferramentas do compilador pesquisam todas as bibliotecas, incluindo bibliotecas principais do .NET Framework, buscando elementos do programa identificados por elementos filhos do elemento `<Application>`. Por outro lado, as ferramentas do compilador pesquisam somente a biblioteca designada pelo elemento [\<Library>](library-element-net-native.md) em busca de elementos do programa identificados pelos elementos filhos de [\<Library>](library-element-net-native.md).  
  
- Como um elemento que define a política de todo o aplicativo para reflexão, serialização e interoperabilidade. Os atributos do elemento `<Application>` definem a política de todo o aplicativo, que pode ser substituída pelos elementos filhos definidos pelo elemento `<Application>` ou [\<Library>](library-element-net-native.md).  
  
## <a name="see-also"></a>Consulte também

- [Elemento de > de biblioteca de \<](library-element-net-native.md)
- [Elemento de > de diretivas de \<](directives-element-net-native.md)
- [Elementos da diretiva de tempo de execução](runtime-directive-elements.md)
- [Referência do arquivo de configuração das diretivas de tempo de execução (rd.xml)](runtime-directives-rd-xml-configuration-file-reference.md)
