---
title: Configurações da política da diretiva de tempo de execução
ms.date: 03/30/2017
ms.assetid: cb52b1ef-47fd-4609-b69d-0586c818ac9e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ac5d80664bbca8cf950eb2e6f37badc485c398d2
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45516915"
---
# <a name="runtime-directive-policy-settings"></a>Configurações da política da diretiva de tempo de execução
> [!NOTE]
>  Este tópico refere-se ao Developer Preview do .NET Nativo, que é um software em pré-lançamento. Você pode baixar a versão prévia do [site Microsoft Connect](https://go.microsoft.com/fwlink/?LinkId=394611) (registro obrigatório).  
  
 As configurações de política de diretiva de tempo de execução para .NET Nativo determinam a disponibilidade de metadados para tipos e membros de tipo em tempo de execução. Sem os metadados necessários, operações que dependem de reflexão, serialização, desserialização ou marshaling dos tipos de .NET Framework para COM ou o Tempo de Execução do Windows podem falhar e gerar uma exceção. As exceções mais comuns são [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) e (no caso de interoperabilidade) [MissingInteropDataException](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md).  
  
 Configurações de política de tempo de execução são controladas pelo arquivo de diretivas de tempo de execução (.rd.xml). Cada diretiva de tempo de execução define uma política para um elemento específico do programa, tal como um assembly (o elemento [\<Assembly>](../../../docs/framework/net-native/assembly-element-net-native.md)), um tipo (o elemento [\<Type>](../../../docs/framework/net-native/type-element-net-native.md)) ou um método (o elemento [\<Method>](../../../docs/framework/net-native/method-element-net-native.md)). A diretiva inclui um ou mais atributos que definem os tipos de política de reflexão, os tipos de política de serialização e os tipos de política de interoperabilidade discutidos na próxima seção. O valor do atributo define a configuração de política.  
  
## <a name="policy-types"></a>Tipos de política  
 Arquivos de diretivas de tempo de execução reconhecem três categorias de tipos de política: reflexão, serialização e interoperabilidade.  
  
-   Tipos de política de reflexão determinam quais metadados são disponibilizados no tempo de execução para reflexão:  
  
    -   O `Activate` controla o acesso de tempo de execução a construtores para habilitar a ativação de instâncias.  
  
    -   O `Browse` controla as consultas para obter informações sobre elementos de programa.  
  
    -   O `Dynamic` controla o acesso de tempo de execução a todos os tipos e membros para habilitar programação dinâmica.  
  
     A tabela a seguir lista os tipos de política de reflexão e os elementos do programa com o qual podem ser usados.  
  
    |Elemento|Ativar|Procure|Dinâmico|  
    |-------------|--------------|------------|-------------|  
    |[\<Application>](../../../docs/framework/net-native/application-element-net-native.md)|✓|✓|✓|  
    |[\<Assembly>](../../../docs/framework/net-native/assembly-element-net-native.md)|✓|✓|✓|  
    |[\<AttributeImplies>](../../../docs/framework/net-native/attributeimplies-element-net-native.md)|✓|✓|✓|  
    |[\<Event>](../../../docs/framework/net-native/event-element-net-native.md)||✓|✓|  
    |[\<Field>](../../../docs/framework/net-native/field-element-net-native.md)||✓|✓|  
    |[\<GenericParameter>](../../../docs/framework/net-native/genericparameter-element-net-native.md)|✓|✓|✓|  
    |[\<ImpliesType>](../../../docs/framework/net-native/impliestype-element-net-native.md)|✓|✓|✓|  
    |[\<Method>](../../../docs/framework/net-native/method-element-net-native.md)||✓|✓|  
    |[\<MethodInstantiation>](../../../docs/framework/net-native/methodinstantiation-element-net-native.md)||✓|✓|  
    |[\<Namespace>](../../../docs/framework/net-native/namespace-element-net-native.md)|✓|✓|✓|  
    |[\<Parameter>](../../../docs/framework/net-native/parameter-element-net-native.md)|✓|✓|✓|  
    |[\<Property>](../../../docs/framework/net-native/property-element-net-native.md)||✓|✓|  
    |[\<Subtypes>](../../../docs/framework/net-native/subtypes-element-net-native.md)|✓|✓|✓|  
    |[\<Type>](../../../docs/framework/net-native/type-element-net-native.md)|✓|✓|✓|  
    |[\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|✓|✓|✓|  
    |[\<TypeParameter>](../../../docs/framework/net-native/typeparameter-element-net-native.md)|✓|✓|✓|  
  
-   Os tipos de política de serialização determinam quais metadados são disponibilizado no tempo de execução para serialização e desserialização:  
  
    -   O `Serialize` controla o acesso ao tempo de execução para construtores, campos e propriedades para habilitar a serialização por bibliotecas de terceiros como o serializador Newtonsoft JSON.  
  
    -   O `DataContractSerializer` controla o acesso de tempo de execução a construtores, campos e propriedades, para habilitar que instâncias de tipo sejam serializadas pela classe <xref:System.Runtime.Serialization.DataContractSerializer>.  
  
    -   O `DataContractJsonSerializer` controla o acesso de tempo de execução a construtores, campos e propriedades, para habilitar que instâncias de tipo sejam serializadas pela classe <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.  
  
    -   O `XmlSerializer` controla o acesso de tempo de execução a construtores, campos e propriedades, para habilitar que instâncias de tipo sejam serializadas pela classe <xref:System.Xml.Serialization.XmlSerializer>.  
  
     A tabela a seguir lista os tipos de política de serialização e os elementos do programa com o qual podem ser usados.  
  
    |Elemento|Serializar|DataContractSerializer|DataContractJsonSerializer|XmlSerializer|  
    |-------------|---------------|----------------------------|--------------------------------|-------------------|  
    |[\<Application>](../../../docs/framework/net-native/application-element-net-native.md)|✓|✓|✓|✓|  
    |[\<Assembly>](../../../docs/framework/net-native/assembly-element-net-native.md)|✓|✓|✓|✓|  
    |[\<AttributeImplies>](../../../docs/framework/net-native/attributeimplies-element-net-native.md)|✓|✓|✓|✓|  
    |[\<Event>](../../../docs/framework/net-native/event-element-net-native.md)|||||  
    |[\<Field>](../../../docs/framework/net-native/field-element-net-native.md)|✓||||  
    |[\<GenericParameter>](../../../docs/framework/net-native/genericparameter-element-net-native.md)|✓|✓|✓|✓|  
    |[\<ImpliesType>](../../../docs/framework/net-native/impliestype-element-net-native.md)|✓|✓|✓|✓|  
    |[\<Method>](../../../docs/framework/net-native/method-element-net-native.md)|||||  
    |[\<MethodInstantiation>](../../../docs/framework/net-native/methodinstantiation-element-net-native.md)|||||  
    |[\<Namespace>](../../../docs/framework/net-native/namespace-element-net-native.md)|✓|✓|✓|✓|  
    |[\<Parameter>](../../../docs/framework/net-native/parameter-element-net-native.md)|✓|✓|✓|✓|  
    |[\<Property>](../../../docs/framework/net-native/property-element-net-native.md)|✓||||  
    |[\<Subtypes>](../../../docs/framework/net-native/subtypes-element-net-native.md)|✓|✓|✓|✓|  
    |[\<Type>](../../../docs/framework/net-native/type-element-net-native.md)|✓|✓|✓|✓|  
    |[\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|✓|✓|✓|✓|  
    |[\<TypeParameter>](../../../docs/framework/net-native/typeparameter-element-net-native.md)|✓|✓|✓|✓|  
  
-   Os tipos de política de interoperabilidade determinam os metadados que são disponibilizados no tempo de execução para passar topos de referências, tipos de valor e apontadores de função ao COM e ao Tempo de Execução do Windows:  
  
    -   O `MarshalObject` controla o marshaling nativo para o COM e o Tempo de Execução do Windows para tipos de referência.  
  
    -   O `MarshalDelegate` controla o marshaling nativo de tipos de delegados como ponteiros de função.  
  
    -   O `MarshalStructure` controla o marshaling nativo para o COM e o Tempo de Execução do Windows para tipos de valor.  
  
     A tabela a seguir lista os tipos de política de interoperabilidade e os elementos do programa com o qual podem ser usados.  
  
    |Elemento|MarshalObject|MarshalDelegate|MarshalStructure|  
    |-------------|-------------------|---------------------|----------------------|  
    |[\<Application>](../../../docs/framework/net-native/application-element-net-native.md)|✓|✓|✓|  
    |[\<Assembly>](../../../docs/framework/net-native/assembly-element-net-native.md)|✓|✓|✓|  
    |[\<AttributeImplies>](../../../docs/framework/net-native/attributeimplies-element-net-native.md)|✓|✓|✓|  
    |[\<Event>](../../../docs/framework/net-native/event-element-net-native.md)||||  
    |[\<Field>](../../../docs/framework/net-native/field-element-net-native.md)||||  
    |[\<GenericParameter>](../../../docs/framework/net-native/genericparameter-element-net-native.md)|✓|✓|✓|  
    |[\<ImpliesType>](../../../docs/framework/net-native/impliestype-element-net-native.md)|✓|✓|✓|  
    |[\<Method>](../../../docs/framework/net-native/method-element-net-native.md)||||  
    |[\<MethodInstantiation>](../../../docs/framework/net-native/methodinstantiation-element-net-native.md)||||  
    |[\<Namespace>](../../../docs/framework/net-native/namespace-element-net-native.md)|✓|✓|✓|  
    |[\<Parameter>](../../../docs/framework/net-native/parameter-element-net-native.md)|✓|✓|✓|  
    |[\<Property>](../../../docs/framework/net-native/property-element-net-native.md)||||  
    |[\<Subtypes>](../../../docs/framework/net-native/subtypes-element-net-native.md)|✓|✓|✓|  
    |[\<Type>](../../../docs/framework/net-native/type-element-net-native.md)|✓|✓|✓|  
    |[\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|✓|✓|✓|  
    |[\<TypeParameter>](../../../docs/framework/net-native/typeparameter-element-net-native.md)|✓|✓|✓|  
  
## <a name="policy-settings"></a>Configurações de política  
 Cada tipo de política pode ser definido como um dos valores listados na tabela a seguir. Observe que elementos que representam os membros do tipo oferece suporte a um conjunto diferente de configurações de política que outros elementos.  
  
|Configurações de política|Descrição|Elementos `Assembly`, `Namespace`, `Type` e `TypeInstantiation`|Elementos `Event`, `Field`, `Method`, `MethodInstantiation` e `Property`|  
|--------------------|-----------------|-----------------------------------------------------------------------|--------------------------------------------------------------------------------|  
|`All`|Habilita a política para todos os tipos e membros que a cadeia de ferramentas do .NET Nativo não remover.|✓||  
|`Auto`|Especifica que a política padrão deve ser usada para o tipo de política desse elemento de programa. Isso é idêntico a omitir uma política para esse tipo de política. O `Auto` geralmente é usado para indicar que a diretiva é herdada de um elemento pai.|✓|✓|  
|`Excluded`|Especifica que a política está desabilitada para um elemento de programa específico. Por exemplo, a diretiva de tempo de execução:<br /><br /> `<Type Name="BusinessClasses.Person" Browse="Excluded" Dynamic="Excluded" />`<br /><br /> Especifica que os metadados para a classe `BusinessClasses.Person` não estão disponíveis para busca ou para instanciar e modificar dinamicamente objetos `Person`.|✓|✓|  
|`Included`|Habilita uma política se os metadados para o tipo de pai estiverem disponíveis.||✓|  
|`Public`|Habilita a política para tipos públicos ou membros, a menos que a cadeia de ferramentas determine que o tipo ou membro é desnecessário e, portanto, remove-o. Essa configuração é diferente de `Required Public`, que garante que os metadados para membros e tipos públicos estão sempre disponíveis mesmo se a cadeia de ferramentas determinar que não são necessários.|✓||  
|`PublicAndInternal`|Habilita a política para tipos ou membros públicos e internos, a menos que a cadeia de ferramentas determine que o tipo ou membro é desnecessário e, portanto, remove-o. Essa configuração é diferente de `Required PublicAndInternal`, que garante que os metadados para membros e tipos públicos e internos estão sempre disponíveis mesmo se a cadeia de ferramentas determinar que não são necessários.|✓||  
|`Required`|Especifica que a política de membro está habilitada e os metadados estarão disponíveis mesmo se o membro parecer ser usado.||✓|  
|`Required Public`|Habilita a política para tipos ou membros públicos e garante que os metadados para tipos e membros públicos estejam sempre disponíveis. Essa configuração é diferente de `Public`, disponibilizando metadados para tipos e membros públicos somente se a cadeia de ferramentas determinar que é necessário.|✓||  
|`Required PublicAndInternal`|Habilita a política para tipos ou membros públicos e internos e garante que os metadados para tipos e membros públicos e internos estejam sempre disponíveis. Essa configuração é diferente de `PublicAndInternal`, disponibilizando metadados para tipos e membros públicos e internos somente se a cadeia de ferramentas determinar que é necessário.|✓||  
|`Required All`|Necessita da cadeia de ferramentas para manter todos os tipos e membros, sejam usados ou não, e habilita a política para eles.|✓||  
  
## <a name="see-also"></a>Consulte também  
 [Referência do arquivo de configuração das diretivas de tempo de execução (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [Elementos da diretiva de tempo de execução](../../../docs/framework/net-native/runtime-directive-elements.md)
