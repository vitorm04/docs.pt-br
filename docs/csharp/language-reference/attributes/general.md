---
title: 'C# atributos reservados: Condicional, obsoleto, atributoUso'
ms.date: 04/09/2020
description: Esses atributos são interpretados pelo compilador para afetar o código gerado pelo compilador
ms.openlocfilehash: c6d697dd08233ffc88900949998047137ee170a9
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021767"
---
# <a name="reserved-attributes-conditionalattribute-obsoleteattribute-attributeusageattribute"></a>Atributos reservados: ConditionalAttribute, ObsoleteAttribute, AttributeUseAttribute

Esses atributos podem ser aplicados a elementos do seu código. Eles adicionam significado semântico a esses elementos. O compilador usa esses significados semânticos para alterar sua saída e relatar possíveis erros por parte dos desenvolvedores usando seu código.

## <a name="conditional-attribute"></a>Atributo `Conditional`

O atributo `Conditional` torna a execução de um método dependente de um identificador de pré-processamento. O atributo `Conditional` é um alias para <xref:System.Diagnostics.ConditionalAttribute> e pode ser aplicado a um método ou uma classe de atributo.

No exemplo a `Conditional` seguir, é aplicado a um método para ativar ou desativar a exibição de informações de diagnóstico específicas do programa:

:::code language="csharp" source="snippets/trace.cs" interactive="try-dotnet" :::

Se `TRACE_ON` o identificador não for definido, a saída de rastreamento não será exibida. Explore você mesmo na janela interativa.

O `Conditional` atributo é `DEBUG` frequentemente usado com o identificador para habilitar recursos de rastreamento e registro para compilações de depuração, mas não em compilações de versão, como mostrado no exemplo a seguir:

:::code language="csharp" source="snippets/ConditionalExamples.cs" id="SnippetConditional" :::

Quando um método marcado como condicional é chamado, a presença ou ausência do símbolo de pré-processamento especificado determina se a chamada está incluída ou omitida. Se o símbolo estiver definido, a chamada será incluída, caso contrário, a chamada será omitida. Um método condicional deve ser um método em uma declaração `void` de classe ou estrutura e deve ter um tipo de retorno. O `Conditional` uso é mais limpo, mais elegante e menos `#if…#endif` propenso a erros do que os métodos de fechamento dentro de blocos.

Se um método `Conditional` tiver vários atributos, uma chamada ao método será incluída se em um ou mais símbolos condicionais for definido (os símbolos estão logicamente ligados juntos usando o operador OR). No exemplo a seguir, `A` a `B` presença de um ou resulta em uma chamada de método:

:::code language="csharp" source="snippets/ConditionalExamples.cs" id="SnippetMultipleConditions" :::

### <a name="using-conditional-with-attribute-classes"></a>Usando `Conditional` com classes de atributos

O atributo `Conditional` também pode ser aplicado a uma definição de classe de atributos. No exemplo a seguir, `Documentation` o atributo personalizado só `DEBUG` adicionará informações aos metadados se for definido.

:::code language="csharp" source="snippets/ConditionalExamples.cs" id="SnippetConditionalConditionalAttribute" :::

## <a name="obsolete-attribute"></a>Atributo `Obsolete`

O `Obsolete` atributo marca um elemento de código como não mais recomendado para uso. O uso de uma entidade marcada como obsoleta gera um aviso ou um erro. O atributo `Obsolete` é um atributo de uso único e pode ser aplicado a qualquer entidade que permite atributos. `Obsolete` é um alias para <xref:System.ObsoleteAttribute>.

No exemplo a `Obsolete` seguir, o `A` atributo `B.OldMethod`é aplicado à classe e ao método . Como o segundo argumento do construtor de atributo aplicado a `B.OldMethod` está definido como `true`, esse método causará um erro do compilador, enquanto que ao usar a classe `A`, produzirá apenas um aviso. Chamar `B.NewMethod`, no entanto, não produz aviso nem erro. Por exemplo, ao usá-lo com as definições anteriores, o código a seguir gera um erro e dois avisos:

:::code language="csharp" source="snippets/ObsoleteExample.cs" interactive="try-dotnet" :::

A seqüência fornecida como o primeiro argumento para o construtor de atributos será exibida como parte do aviso ou erro. São gerados dois avisos para a classe `A`: um para a declaração da referência de classe e outro para o construtor de classe. O `Obsolete` atributo pode ser usado sem argumentos, mas incluindo uma explicação do que usar em vez disso é recomendado.

## <a name="attributeusage-attribute"></a>Atributo `AttributeUsage`

O `AttributeUsage` atributo determina como uma classe de atributo suidua pode ser usada. <xref:System.AttributeUsageAttribute> é um atributo aplicado a definições de atributo personalizado. O atributo `AttributeUsage` permite que você controle:

- A quais elementos do programa o atributo pode ser aplicado. A menos que você restrinja seu uso, um atributo poderá ser aplicado a qualquer um dos seguintes elementos do programa:
  - assembly
  - module
  - field
  - event
  - method
  - param
  - propriedade
  - return
  - type
- Indica se um atributo pode ser aplicado a um único elemento do programa várias vezes.
- Indica se os atributos são herdados por classes derivadas.

As configurações padrão se parecem com o seguinte exemplo quando aplicadas explicitamente:

:::code language="csharp" source="snippets/NewAttribute.cs" id="SnippetUsageFirst" :::

Neste exemplo, a classe `NewAttribute` pode ser aplicada a qualquer elemento de programa compatível. Porém, ele pode ser aplicado apenas uma vez para cada entidade. O atributo é herdado por classes derivadas quando aplicado a uma classe base.

Os argumentos <xref:System.AttributeUsageAttribute.AllowMultiple> e <xref:System.AttributeUsageAttribute.Inherited> são opcionais e, portanto, o seguinte código tem o mesmo efeito:

:::code language="csharp" source="snippets/NewAttribute.cs" id="SnippetUsageSecond" :::

O primeiro argumento <xref:System.AttributeUsageAttribute> deve ser um ou mais elementos da enumeração <xref:System.AttributeTargets>. Vários tipos de destino podem ser vinculados junto com o operador OR, como mostra o seguinte exemplo:

:::code language="csharp" source="snippets/NewPropertyOrFieldAttribute.cs" id="SnippetDefinePropertyAttribute" :::

Do C# 7.3 em diante, os atributos podem ser aplicados à propriedade ou ao campo de suporte de uma propriedade autoimplementada. O atributo se aplica à propriedade, a menos que você especifique o especificador `field` no atributo. Ambos são mostrados no seguinte exemplo:

:::code language="csharp" source="snippets/NewPropertyOrFieldAttribute.cs" id="SnippetUsePropertyAttribute" :::

Se o argumento <xref:System.AttributeUsageAttribute.AllowMultiple> for `true`, o atributo resultante poderá ser aplicado mais de uma vez a uma única entidade, conforme mostrado no seguinte exemplo:

:::code language="csharp" source="snippets/MultiUseAttribute.cs" id="SnippetMultiUse" :::

Nesse caso, `MultiUseAttribute` pode ser aplicado repetidas vezes porque `AllowMultiple` está definido como `true`. Os dois formatos mostrados para a aplicação de vários atributos são válidos.

Se <xref:System.AttributeUsageAttribute.Inherited> for `false`, o atributo não será herdado por classes derivadas de uma classe atribuída. Por exemplo:

:::code language="csharp" source="snippets/NonInheritedAttribute.cs" id="SnippetNonInherited" :::

Nesse caso, `NonInheritedAttribute` não é aplicado a `DClass` por meio de herança.

## <a name="see-also"></a>Confira também

- <xref:System.Attribute>
- <xref:System.Reflection>
- [Atributos](../../../standard/attributes/index.md)
- [Reflexão](../../programming-guide/concepts/reflection.md)
