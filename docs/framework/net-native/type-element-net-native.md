---
title: Elemento &lt;Type&gt; (.NET Nativo)
ms.date: 03/30/2017
ms.assetid: 1e88d368-a886-4f1e-8eb6-6127979a9fce
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aaf5103dfee366466ff701ce3669bbabb97233ac
ms.sourcegitcommit: ba5c189bf44d44204a3e8838e59ec378a62d82f3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/12/2018
ms.locfileid: "44708439"
---
# <a name="lttypegt-element-net-native"></a>Elemento &lt;Type&gt; (.NET Nativo)
Aplica a política de tempo de execução a um tipo específico, como uma classe ou estrutura.  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<Type Name="type_name"  
      Activate="policy_type"  
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
|`Name`|Geral|Atributo obrigatório. Especifica o nome do tipo.|  
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
  
## <a name="name-attribute"></a>Atributo de nome  
  
|Valor|Descrição|  
|-----------|-----------------|  
|*type_name*|O nome do tipo. Se este elemento `<Type>` for o filho de um elemento [\<Namespace>](../../../docs/framework/net-native/namespace-element-net-native.md) ou de outro elemento `<Type>`, o *type_name* poderá incluir o nome do tipo sem seu namespace. Caso contrário, o *type_name* deverá incluir o nome do tipo totalmente qualificado.|  
  
## <a name="all-other-attributes"></a>Todos os outros atributos  
  
|Valor|Descrição|  
|-----------|-----------------|  
|*policy_setting*|A configuração a ser aplicada a este tipo de política. Os valores possíveis são `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal` e `Required All`. Para obter mais informações, consulte [Configurações da política da diretiva de tempo de execução](../../../docs/framework/net-native/runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<AttributeImplies>](../../../docs/framework/net-native/attributeimplies-element-net-native.md)|Se o tipo recipiente for um atributo, ele define a política de tempo de execução para elementos de código à qual o atributo é aplicado.|  
|[\<Event>](../../../docs/framework/net-native/event-element-net-native.md)|Aplica a política de reflexão a um evento pertencente a esse tipo.|  
|[\<Field>](../../../docs/framework/net-native/field-element-net-native.md)|Aplica a política de reflexão a um campo pertencente a esse tipo.|  
|[\<GenericParameter>](../../../docs/framework/net-native/genericparameter-element-net-native.md)|Aplica a política ao tipo de parâmetro de um tipo genérico.|  
|[\<ImpliesType>](../../../docs/framework/net-native/impliestype-element-net-native.md)|Aplica a política a um tipo, se esta política tiver sido aplicada ao tipo representado pelo elemento `<Type>` recipiente.|  
|[\<Method>](../../../docs/framework/net-native/method-element-net-native.md)|Aplica a política de reflexão a um método pertencente a esse tipo.|  
|[\<MethodInstantiation>](../../../docs/framework/net-native/methodinstantiation-element-net-native.md)|Aplica a política de reflexão a um método construído genérico pertencente a esse tipo.|  
|[\<Property>](../../../docs/framework/net-native/property-element-net-native.md)|Aplica a política de reflexão a uma propriedade pertencente a esse tipo.|  
|[\<Subtypes>](../../../docs/framework/net-native/subtypes-element-net-native.md)|Aplica a política de tempo de execução a todas as classes herdadas do tipo recipiente.|  
|`<Type>`|Aplica a política de reflexão a um tipo aninhado.|  
|[\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|Aplica a política de reflexão a um tipo genérico construído.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<Application>](../../../docs/framework/net-native/application-element-net-native.md)|Serve como um contêiner para os tipos amplos de aplicativos cujos metadados estão disponíveis para reflexão no tempo de execução.|  
|[\<Assembly>](../../../docs/framework/net-native/assembly-element-net-native.md)|Aplica a política de reflexão para todos os tipos em um assembly especificado.|  
|[\<Library>](../../../docs/framework/net-native/library-element-net-native.md)|Define o assembly que contém tipos e membros de tipo cujos metadados estão disponíveis para reflexão em tempo de execução.|  
|[\<Namespace>](../../../docs/framework/net-native/namespace-element-net-native.md)|Aplica a política de reflexão a todos os tipos em um namespace.|  
|`<Type>`|Aplica a política de reflexão a um tipo e todos os seus membros.|  
|[\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|Aplica a política de reflexão a um tipo genérico construído e todos os seus membros.|  
  
## <a name="remarks"></a>Comentários  
 Os atributos de reflexão, serialização e interoperabilidade são todos opcionais. Se nenhum estiver presente, o elemento `<Type>` serve como um contêiner cujos tipos filho definem a política de membros individuais.  
  
 Se um elemento `<Type>` for o filho de um elemento [\<Assembly>](../../../docs/framework/net-native/assembly-element-net-native.md), [\<Namespace>](../../../docs/framework/net-native/namespace-element-net-native.md), `<Type>` ou [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md), ele substituirá as configurações de política definidas pelo elemento pai.  
  
 Um elemento `<Type>` de um tipo genérico aplica sua política a todas as instanciações que não possuem sua própria política. A política dos tipos genéricos construídos é definida pelo elemento [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md).  
  
 Se o tipo for um tipo genérico, seu nome é decorado por um símbolo de acento grave (\`) seguido pelo número de parâmetros genéricos. Por exemplo, o atributo `Name` de um elemento `<Type>` da classe <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> aparece como `Name="System.Collections.Generic.List`1"`.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa a reflexão para exibir informações sobre os campos, propriedades e métodos da classe <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>. A variável `b` no exemplo é um controle [TextBlock](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.textblock.aspx). Como o exemplo simplesmente recupera informações sobre o tipo, a disponibilidade de metadados é controlada pela configuração da política `Browse`.  
  
 [!code-csharp[ProjectN_Reflection#3](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/browsegenerictype1.cs#3)]  
  
 Como metadados para a classe <xref:System.Collections.Generic.List%601> não estão automaticamente incluídos na cadeia de ferramentas [!INCLUDE[net_native](../../../includes/net-native-md.md)], o exemplo não exibe as informações do membro solicitado no tempo de execução. Para fornecer os metadados necessários, adicione o seguinte elemento `<Type>` ao arquivo de diretivas de tempo de execução. Observe que, como fornecemos um elemento [<Namespace\>](../../../docs/framework/net-native/namespace-element-net-native.md) pai, não precisamos fornecer um nome do tipo totalmente qualificado no elemento `<Type>`.  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Application>  
      <Assembly Name="*Application*" Dynamic="Required All" />  
      <Namespace Name ="System.Collections.Generic" >  
        <Type Name="List`1" Browse="Required All" />   
     </Namespace>  
   </Application>  
</Directives>  
```  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa reflexão para recuperar um objeto <xref:System.Reflection.PropertyInfo> que representa a propriedade <xref:System.String.Chars%2A?displayProperty=nameWithType>. Ele usa o método <xref:System.Reflection.PropertyInfo.GetValue%28System.Object%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> para recuperar o valor do sétimo caractere de uma cadeia de caracteres e exibir todos os caracteres na cadeia de caracteres. A variável `b` no exemplo é um controle [TextBlock](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.textblock.aspx).  
  
 [!code-csharp[ProjectN_Reflection#1](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/propertyinfo1.cs#1)]  
  
 Como os metadados do objeto <xref:System.String> não estão disponíveis, a chamada para o método <xref:System.Reflection.PropertyInfo.GetValue%28System.Object%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> gera uma exceção <xref:System.NullReferenceException> no tempo de execução quando compilado com a cadeia de ferramentas [!INCLUDE[net_native](../../../includes/net-native-md.md)]. Para eliminar a exceção e fornecer os metadados necessários, adicione o seguinte elemento `<Type>` ao arquivo de diretivas de tempo de execução:  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
  <Application>  
    <Assembly Name="*Application*" Dynamic="Required All" />  
    <Type Name="System.String" Dynamic="Required Public"/> -->  
  </Application>  
</Directives>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Referência do arquivo de configuração das diretivas de tempo de execução (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [Elementos da diretiva de tempo de execução](../../../docs/framework/net-native/runtime-directive-elements.md)  
 [Configurações da política da diretiva de tempo de execução](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
