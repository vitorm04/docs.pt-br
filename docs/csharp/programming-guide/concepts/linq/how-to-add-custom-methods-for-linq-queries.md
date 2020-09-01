---
title: Como adicionar métodos personalizados para consultas LINQ (C#)
description: Saiba como estender a sintaxe de consultas LINQ adicionando métodos de extensão à <T> interface IEnumerable em C#.
ms.date: 08/26/2020
ms.assetid: 1a500f60-2e10-49fb-8b2a-d8d08e4817cb
ms.openlocfilehash: 768882fce40a2fc6e018f24c8928341e7c65bc4b
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89122419"
---
# <a name="how-to-add-custom-methods-for-linq-queries-c"></a>Como adicionar métodos personalizados para consultas LINQ (C#)

Você estende o conjunto de métodos que você usa para consultas LINQ adicionando métodos de extensão à <xref:System.Collections.Generic.IEnumerable%601> interface. Por exemplo, além das operações média padrão ou máximo, você cria um método de agregação personalizado para computar um único valor de uma sequência de valores. Você também cria um método que funciona como um filtro personalizado ou uma transformação de dados específica para uma sequência de valores e retorna uma nova sequência. Exemplos desses métodos são <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Skip%2A> e <xref:System.Linq.Enumerable.Reverse%2A>.

Ao estender a interface <xref:System.Collections.Generic.IEnumerable%601>, você pode aplicar seus métodos personalizados para qualquer coleção enumerável. Para obter mais informações, consulte [Métodos de extensão](../../classes-and-structs/extension-methods.md).

## <a name="adding-an-aggregate-method"></a>Adicionando um método de agregação

Um método de agregação calcula um valor único de um conjunto de valores. O LINQ fornece vários métodos de agregação, incluindo <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Min%2A> e <xref:System.Linq.Enumerable.Max%2A>. Você pode criar seu próprio método de agregação, adicionando um método de extensão à interface <xref:System.Collections.Generic.IEnumerable%601>.

O exemplo de código a seguir mostra como criar um método de extensão chamado `Median` para calcular uma mediana de uma sequência de números do tipo `double`.

:::code language="csharp" source="./snippets/LinqExtensions.cs" ID="LinqExtensionClass":::

Você chama esse método de extensão para qualquer coleção enumerável da mesma maneira que chama outros métodos de agregação da interface <xref:System.Collections.Generic.IEnumerable%601>.

O exemplo de código a seguir mostra como usar o método `Median` para uma matriz do tipo `double`.

:::code language="csharp" source="./snippets/Program.cs" ID="MedianUsage":::

### <a name="overloading-an-aggregate-method-to-accept-various-types"></a>Sobrecarregando um método de agregação para aceitar vários tipos

Você pode sobrecarregar o método de agregação para que ele aceite sequências de vários tipos. A abordagem padrão é criar uma sobrecarga para cada tipo. Outra abordagem é criar uma sobrecarga que vai pegar um tipo genérico e convertê-lo em um tipo específico, usando um delegado. Você também pode combinar as duas abordagens.

#### <a name="to-create-an-overload-for-each-type"></a>Para criar uma sobrecarga para cada tipo

Você pode criar uma sobrecarga específica para cada tipo que deseja oferecer suporte. O exemplo de código a seguir mostra uma sobrecarga do método `Median` para o tipo `int`.

:::code language="csharp" source="./snippets/LinqExtensions.cs" ID="IntOverload":::

Agora você pode chamar as sobrecargas `Median` para os tipos `integer` e `double`, conforme mostrado no código a seguir:

:::code language="csharp" source="./snippets/Program.cs" ID="OverloadUsage":::

#### <a name="to-create-a-generic-overload"></a>Para criar uma sobrecarga genérica

Você também pode criar uma sobrecarga que aceita uma sequência de objetos genéricos. Essa sobrecarga recebe um delegado como parâmetro e usa-o para converter uma sequência de objetos de um tipo genérico em um tipo específico.

O código a seguir mostra uma sobrecarga do método `Median` que recebe o delegado <xref:System.Func%602> como um parâmetro. Esse delegado recebe um objeto de tipo genérico T e retorna um objeto do tipo `double`.

:::code language="csharp" source="./snippets/LinqExtensions.cs" ID="GenericOverload":::

Agora você pode chamar o método `Median` para uma sequência de objetos de qualquer tipo. Se o tipo não tiver sua própria sobrecarga de método, você precisará passar um parâmetro delegado. No C# você pode usar uma expressão lambda para essa finalidade. Além disso, no Visual Basic, se você usar a cláusula `Aggregate` ou `Group By` em vez da chamada de método, você pode passar qualquer valor ou expressão que estiver no escopo dessa cláusula.

O exemplo de código a seguir mostra como chamar o método `Median` para uma matriz de inteiros e para uma matriz de cadeias de caracteres. Será calculada a mediana dos comprimentos das cadeias de caracteres na matriz. O exemplo também mostra como passar o parâmetro delegado <xref:System.Func%602> ao método `Median` para cada caso.

:::code language="csharp" source="./snippets/Program.cs" ID="GenericUsage":::

## <a name="adding-a-method-that-returns-a-sequence"></a>Adicionando um método que retorna uma sequência

Você pode estender a interface <xref:System.Collections.Generic.IEnumerable%601> com um método de consulta personalizada que retorna uma sequência de valores. Nesse caso, o método deve retornar uma coleção do tipo <xref:System.Collections.Generic.IEnumerable%601>. Esses métodos podem ser usados para aplicar transformações de dados ou filtros a uma sequência de valores.

O exemplo a seguir mostra como criar um método de extensão chamado `AlternateElements` que retorna todos os outros elementos em uma coleção, começando pelo primeiro elemento.

:::code language="csharp" source="./snippets/LinqExtensions.cs" ID="SequenceElement":::

Você pode chamar esse método de extensão para qualquer coleção enumerável exatamente como chamaria outros métodos da interface <xref:System.Collections.Generic.IEnumerable%601>, conforme mostrado no código a seguir:

:::code language="csharp" source="./snippets/Program.cs" ID="SequenceUsage":::

## <a name="see-also"></a>Confira também

- <xref:System.Collections.Generic.IEnumerable%601>
- [Métodos de Extensão](../../classes-and-structs/extension-methods.md)
