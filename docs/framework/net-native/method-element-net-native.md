---
title: Elemento &lt;Method&gt; (.NET Nativo)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 348b49e5-589d-4eb2-a597-d6ff60ab52d1
caps.latest.revision: 22
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 523ec4fd2c8d19dc9086e417fa99c89a619caa71
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="ltmethodgt-element-net-native"></a>Elemento &lt;Method&gt; (.NET Nativo)
Aplica a política de reflexão de tempo de execução a um construtor ou método.  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<Method Name="method_name"  
        Signature="method_signature"  
        Browse="policy_type"  
        Dynamic="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Tipo de atributo|Descrição|  
|---------------|--------------------|-----------------|  
|`Name`|Geral|Atributo obrigatório. Especifica o nome do método.|  
|`Signature`|Geral|Atributo opcional. Especifica a assinatura do método. Se vários parâmetros estiverem presentes, eles são separados por vírgulas. Por exemplo, o elemento `<Method>` a seguir define a política para o método <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29>.<br /><br /> `<Type Name="System.DateTime">    <Method Name="ToString" Signature="System.String,System.IFormatProvider"            Dynamic="Required" /> </Type>`<br /><br /> Se o atributo estiver ausente, a diretiva de tempo de execução se aplica a todas as sobrecargas do método.|  
|`Browse`|Reflexão|Atributo opcional. Controla consultas para obter informações sobre o método ou para enumerá-lo, mas não permite qualquer invocação dinâmica no tempo de execução.|  
|`Dynamic`|Reflexão|Atributo opcional. Controla o acesso do tempo de execução a um construtor ou método para habilitar a programação dinâmica. Essa política garante que um membro pode ser invocado dinamicamente no tempo de execução.|  
  
## <a name="name-attribute"></a>Atributo de nome  
  
|Valor|Descrição|  
|-----------|-----------------|  
|*method_name*|O nome do método. O tipo do método é definido pelo elemento pai [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) ou [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md).|  
  
## <a name="signature-attribute"></a>Atributo de assinatura  
  
|Valor|Descrição|  
|-----------|-----------------|  
|*method_signature*|Os tipos de parâmetros que formam a assinatura do método. Vários parâmetros são separados por vírgulas, por exemplo, `"System.String,System.Int32,System.Int32)"`. Nomes de tipo de parâmetro devem ser totalmente qualificados.|  
  
## <a name="all-other-attributes"></a>Todos os outros atributos  
  
|Valor|Descrição|  
|-----------|-----------------|  
|*policy_setting*|A configuração a ser aplicada a este tipo de política. Os valores possíveis são `Auto`, `Excluded`, `Included` e `Required`. Para obter mais informações, consulte [Configurações da política da diretiva de tempo de execução](../../../docs/framework/net-native/runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<Parameter>](../../../docs/framework/net-native/parameter-element-net-native.md)|Aplica a política ao tipo do argumento passado para um método.|  
|[\<GenericParameter>](../../../docs/framework/net-native/genericparameter-element-net-native.md)|Aplica a política ao tipo de parâmetro de um tipo ou método genérico.|  
|[\<ImpliesType>](../../../docs/framework/net-native/impliestype-element-net-native.md)|Aplica a política a um tipo, se esta política tiver sido aplicada ao método representado pelo elemento `<Method>` recipiente.|  
|[\<TypeParameter>](../../../docs/framework/net-native/typeparameter-element-net-native.md)|Aplica a política ao tipo representado por um argumento <xref:System.Type> passado para um método.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<Type>](../../../docs/framework/net-native/type-element-net-native.md)|Aplica a política de reflexão a um tipo e todos os seus membros.|  
|[\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|Aplica a política de reflexão a um tipo genérico construído e todos os seus membros.|  
  
## <a name="remarks"></a>Comentários  
 Um elemento `<Method>` de um método genérico aplica sua política a todas as instanciações que não possuem sua própria política.  
  
 Você pode usar o atributo `Signature` para especificar uma política para uma sobrecarga de método específico. Caso contrário, se o atributo `Signature` estiver ausente, a diretiva de tempo de execução se aplicará a todas as sobrecargas do método.  
  
 Não é possível definir a política de reflexão de tempo de execução de um construtor usando o `<Method>` elemento. Em vez disso, use o atributo `Activate` do elemento [\<Assembly>](../../../docs/framework/net-native/assembly-element-net-native.md), [\<Namespace>](../../../docs/framework/net-native/namespace-element-net-native.md), [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) ou [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md).  
  
## <a name="example"></a>Exemplo  
 O método `Stringify` no exemplo a seguir é um método de formatação para fins gerais que usa reflexão para converter um objeto em sua representação de cadeia de caracteres. Além de chamar o método `ToString` padrão do objeto, o método pode produzir uma cadeia de caracteres de resultados formatada passando um método `ToString` do objeto método em uma cadeia de caracteres, uma implementação de <xref:System.IFormatProvider> ou ambos. Ele também pode chamar uma das sobrecargas de <xref:System.Convert.ToString%2A?displayProperty=fullName> que converte um número em sua representação octal, hexadecimal ou binária.  
  
 [!code-csharp[ProjectN_Reflection#7](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/method1.cs#7)]  
  
 O método `Stringify` pode ser chamado pelo código da seguinte maneira:  
  
 [!code-csharp[ProjectN_Reflection#7](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/method1.cs#7)]  
  
 No entanto, quando compilado com .NET Native, o exemplo pode acionar diversas exceções no tempo de execução, incluindo as exceções <xref:System.NullReferenceException> e [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md). Isso ocorre porque o método `Stringify` destina-se principalmente a oferecer suporte à formatação dinâmica dos tipos primitivos na Biblioteca de Classes do .NET Framework. No entanto, seus metadados não são disponibilizados pelo arquivo de diretivas padrão. Mesmo quando seus metadados são disponibilizados, o exemplo aciona exceções [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) porque as devidas implementações `ToString` não foram incluídas no código nativo.  
  
 Essas exceções podem ser eliminadas usando o elemento [Type>\<](../../../docs/framework/net-native/type-element-net-native.md) para definir os tipos cujos metadados devem estar presentes e adicionando elementos `<Method>` para garantir que a implementação das sobrecargas de método que podem ser chamadas dinamicamente também estejam presentes. Veja a seguir o arquivo default.rd.xml que elimina essas exceções e permite que o exemplo seja executado sem erros.  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
  <Application>  
     <Assembly Name="*Application*" Dynamic="Required All" />  
  
     <Type Name = "System.Convert" Browse="Required Public" Dynamic="Required Public" >  
        <Method Name="ToString"    Dynamic ="Required" />  
     </Type>  
     <Type Name="System.Double" Browse="Required Public">  
        <Method Name="ToString" Dynamic="Required" />  
     </Type>  
     <Type Name ="System.Int32" Browse="Required Public" >  
        <Method Name="ToString" Dynamic="Required" />  
     </Type>  
     <Type Name ="System.Int64" Browse="Required Public" >  
        <Method Name="ToString" Dynamic="Required" />  
     </Type>  
     <Namespace Name="System" >  
        <Type Name="Byte" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="DateTime" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="Decimal" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="Guid" Browse ="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="Int16" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="SByte" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="Single" Browse="Required Public" >  
          <Method Name="ToString" Dynamic="Required" />           
        </Type>  
        <Type Name="TimeSpan" Browse="Required Public" >  
          <Method Name="ToString" Dynamic="Required" />           
        </Type>  
        <Type Name="UInt16" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="UInt32" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="UInt64" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
     </Namespace>  
  </Application>  
</Directives>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Referência do arquivo de configuração das diretivas de tempo de execução (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)   
 [Elementos da diretiva de tempo de execução](../../../docs/framework/net-native/runtime-directive-elements.md)   
 [Configurações da política da diretiva de tempo de execução](../../../docs/framework/net-native/runtime-directive-policy-settings.md)   
 [Elemento \<MethodInstantiation>](../../../docs/framework/net-native/methodinstantiation-element-net-native.md)

