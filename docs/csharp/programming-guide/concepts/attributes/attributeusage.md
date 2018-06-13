---
title: AttributeUsage (C#)
ms.date: 04/25/2018
ms.openlocfilehash: 869e6509e55268767915a783a8652f7f950d7137
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/10/2018
ms.locfileid: "33955922"
---
# <a name="attributeusage-c"></a>AttributeUsage (C#)

Determina como uma classe de atributo personalizado pode ser usada. <xref:System.AttributeUsageAttribute> é um atributo aplicado a definições de atributo personalizado. O atributo `AttributeUsage` permite que você controle:

- A quais elementos do programa o atributo pode ser aplicado. A menos que você restrinja seu uso, um atributo pode ser aplicado a um dos seguintes elementos do programa:
  - assembly
  - module
  - campo
  - evento
  - method
  - param
  - propriedade
  - return
  - tipo
- Indica se um atributo pode ser aplicado a um único elemento do programa várias vezes.
- Indica se os atributos são herdados por classes derivadas.

As configurações padrão se parecem com o seguinte exemplo quando aplicadas explicitamente:

[!code-csharp[Define a new attribute](../../../../../samples/snippets/csharp/attributes/NewAttribute.cs#1)]

Neste exemplo, a classe `NewAttribute` pode ser aplicada a qualquer elemento de programa compatível. Porém, ele pode ser aplicado apenas uma vez para cada entidade. O atributo é herdado por classes derivadas quando aplicado a uma classe base.

Os argumentos <xref:System.AttributeUsageAttribute.AllowMultiple> e <xref:System.AttributeUsageAttribute.Inherited> são opcionais e, portanto, o seguinte código tem o mesmo efeito:

[!code-csharp[Omit optional attributes](../../../../../samples/snippets/csharp/attributes/NewAttribute.cs#2)]

O primeiro argumento <xref:System.AttributeUsageAttribute> deve ser um ou mais elementos da enumeração <xref:System.AttributeTargets>. Vários tipos de destino podem ser vinculados junto com o operador OR, como mostra o seguinte exemplo:

[!code-csharp[Create an attribute for fields or properties](../../../../../samples/snippets/csharp/attributes/NewPropertyOrFieldAttribute.cs#1)]

Do C# 7.3 em diante, os atributos podem ser aplicados à propriedade ou ao campo de suporte de uma propriedade autoimplementada. O atributo se aplica à propriedade, a menos que você especifique o especificador `field` no atributo. Ambos são mostrados no seguinte exemplo:

[!code-csharp[Create an attribute for fields or properties](../../../../../samples/snippets/csharp/attributes/NewPropertyOrFieldAttribute.cs#2)]

Se o argumento <xref:System.AttributeUsageAttribute.AllowMultiple> for `true`, o atributo resultante poderá ser aplicado mais de uma vez a uma única entidade, conforme mostrado no seguinte exemplo:

[!code-csharp[Create and use an attribute that can be applied multiple times](../../../../../samples/snippets/csharp/attributes/MultiUseAttribute.cs#1)]

Nesse caso, `MultiUseAttribute` pode ser aplicado repetidas vezes porque `AllowMultiple` está definido como `true`. Os dois formatos mostrados para a aplicação de vários atributos são válidos.

Se <xref:System.AttributeUsageAttribute.Inherited> for `false`, o atributo não será herdado por classes derivadas de uma classe atribuída. Por exemplo:

[!code-csharp[Create and use an attribute that can be applied multiple times](../../../../../samples/snippets/csharp/attributes/NonInheritedAttribute.cs#1)]

Nesse caso, `NonInheritedAttribute` não é aplicado a `DClass` por meio de herança.

## <a name="remarks"></a>Comentários

O atributo `AttributeUsage` é um atributo de uso único. Ele não pode ser aplicado mais de uma vez à mesma classe. `AttributeUsage` é um alias para <xref:System.AttributeUsageAttribute>.

Para obter mais informações, consulte [Acessando atributos usando reflexão (C#)](accessing-attributes-by-using-reflection.md).

## <a name="example"></a>Exemplo

O exemplo a seguir demonstra o efeito dos argumentos <xref:System.AttributeUsageAttribute.Inherited> e <xref:System.AttributeUsageAttribute.AllowMultiple> no atributo <xref:System.AttributeUsageAttribute> e como os atributos personalizados aplicados a uma classe podem ser enumerados.

[!code-csharp[Applying and querying attributes](../../../../../samples/snippets/csharp/attributes/Program.cs#1)]

## <a name="sample-output"></a>Saída de Exemplo

```text
Attributes on Base Class:
FirstAttribute
SecondAttribute
Attributes on Derived Class:
ThirdAttribute
ThirdAttribute
SecondAttribute
```

## <a name="see-also"></a>Consulte também
 <xref:System.Attribute>  
 <xref:System.Reflection>  
 [Guia de Programação em C#](../..//index.md)  
 [Atributos](../../../..//standard/attributes/index.md)  
 [Reflexão (C#)](../reflection.md)  
 [Atributos](index.md)  
 [Criando atributos personalizados (C#)](creating-custom-attributes.md)  
 [Acessando atributos usando reflexão (C#)](accessing-attributes-by-using-reflection.md)
