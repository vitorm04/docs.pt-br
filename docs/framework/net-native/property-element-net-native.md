---
title: <Property> (.NET Nativo)
ms.date: 03/30/2017
ms.assetid: ad4ba56d-3bcb-4c10-ba90-1cc66e2175a1
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 20657e0a583890b851ab8e15c50bce791a3641b2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61866763"
---
# <a name="property-element-net-native"></a>\<Propriedade > (.NET nativo)
Aplica a política de reflexão de tempo de execução a uma propriedade.  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<Property Name="property_name"  
          Browse="policy_type"  
          Dynamic="policy_type"  
          Serialize="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Tipo de atributo|Descrição|  
|---------------|--------------------|-----------------|  
|`Name`|Geral|Atributo obrigatório. Especifica o nome da propriedade.|  
|`Browse`|Reflexão|Atributo opcional. Controla consultas para obter informações sobre a propriedade ou para enumerá-la, mas não permite qualquer acesso dinâmico no tempo de execução.|  
|`Dynamic`|Reflexão|Atributo opcional. Controla o acesso do tempo de execução à propriedade para habilitar programação dinâmica. Essa política garante que uma propriedade pode ser definida ou recuperada dinamicamente no tempo de execução.|  
|`Serialize`|Serialização|Atributo opcional. Controla o acesso do tempo de execução a uma propriedade para habilitar as instâncias de tipo a serem serializadas por bibliotecas como o serializador Newtonsoft JSON ou a ser usado para a associação de dados.|  
  
## <a name="name-attribute"></a>Atributo de nome  
  
|Valor|Descrição|  
|-----------|-----------------|  
|*method_name*|O nome da propriedade. O tipo da propriedade é definido pelo elemento pai [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) ou [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md).|  
  
## <a name="all-other-attributes"></a>Todos os outros atributos  
  
|Valor|Descrição|  
|-----------|-----------------|  
|*policy_setting*|A configuração a ser aplicada a este tipo de política para a propriedade. Os valores possíveis são `Auto`, `Excluded`, `Included` e `Required`. Para obter mais informações, consulte [Configurações da política da diretiva de tempo de execução](../../../docs/framework/net-native/runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<Type>](../../../docs/framework/net-native/type-element-net-native.md)|Aplica a política de reflexão a um tipo e todos os seus membros.|  
|[\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|Aplica a política de reflexão a um tipo genérico construído e todos os seus membros.|  
  
## <a name="remarks"></a>Comentários  
 Se a política da propriedade não for definida explicitamente, ela herdará a política de tempo de execução do seu elemento pai.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa reflexão para instanciar um objeto `Book` e exibir seus valores de propriedade. O arquivo default.rd.xml original para o projeto aparece da seguinte maneira:  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Application>  
      <Namespace Name="LibraryApplications"  Browse="Required Public" >  
         <Type Name="Book"   Activate="All" />  
      </Namespace>  
   </Application>  
</Directives>  
```  
  
 O arquivo se aplica ao valor `All` para a política `Activate` da classe `Book`, que permite acesso aos construtores de classe por meio de reflexão. A política `Browse` para a classe `Book` é herdada do seu namespace pai. Isso é definido para `Required Public`, que disponibiliza metadados no tempo de execução.  
  
 Este é o código-fonte para o exemplo. O `outputBlock` variável representa um <xref:Windows.UI.Xaml.Controls.TextBlock> controle.  
  
 [!code-csharp[ProjectN_Reflection#6](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/property1.cs#6)]  
  
 No entanto, compilar e executar este exemplo gera uma exceção [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md). Embora tenhamos disponibilizados metadados para o tipo `Book` disponível, não realizamos implementações de getters de propriedades disponíveis dinamicamente. Podemos corrigir esse erro de uma das seguintes maneiras:  
  
- definindo a política `Dynamic` para o tipo `Book` no seu elemento [\<Type>](../../../docs/framework/net-native/type-element-net-native.md).  
  
- Adicionando um elemento [\<Property>](../../../docs/framework/net-native/property-element-net-native.md) aninhado para cada propriedade cujo getter gostaríamos de invocar, como faz o arquivo default.rd.xml a seguir.  
  
    ```xml  
    <Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
       <Application>  
          <Namespace Name="LibraryApplications"  Browse="Required Public" >  
             <Type Name="Book"   Activate="All" >  
                <Property Name="Title" Dynamic="Required" />  
                <Property Name="Author" Dynamic="Required" />  
                  <Property Name="ISBN" Dynamic="Required" />  
             </Type>  
          </Namespace>  
       </Application>  
    </Directives>  
    ```  
  
## <a name="see-also"></a>Consulte também

- [Referência do arquivo de configuração das diretivas de tempo de execução (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [Elementos da diretiva de tempo de execução](../../../docs/framework/net-native/runtime-directive-elements.md)
- [Configurações da política da diretiva de tempo de execução](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
