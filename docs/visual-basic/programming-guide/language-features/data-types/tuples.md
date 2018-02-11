---
title: Tuplas no Visual Basic
ms.custom: 
ms.date: 04/23/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- tuples [Visual Basic]
ms.assetid: 3e66cd1b-3432-4e1d-8c37-5ebacae8f53f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2653b9dc8a6ecbcb718c20be8bd6275edf4cfb6e
ms.sourcegitcommit: be1fb5d9447ad459bef22b91a91c72e3e0b2d916
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2018
---
# <a name="tuples-visual-basic"></a>Tuplas (Visual Basic)

A partir do Visual Basic de 2017, a linguagem Visual Basic oferece suporte interno para tuplas que faz com que criar tuplas e acessar os elementos de tuplas mais fácil. Uma tupla é uma estrutura de dados leve que tem um número específico e a sequência de valores. Quando você cria uma instância de coleção de itens, você deve definir o número e o tipo de dados de cada valor (ou elemento). Por exemplo, uma tupla de 2 (ou par) tem dois elementos. O primeiro pode ser um `Boolean` de valor, enquanto o segundo é um `String`. Porque tuplas facilitam armazenar vários valores em um único objeto, eles geralmente são usados como uma maneira simples de retornar vários valores de um método.

> [!IMPORTANT]
> Suporte de tupla requer o <xref:System.ValueTuple> tipo. Se o .NET Framework 4.7 não estiver instalado, você deve adicionar o pacote NuGet `System.ValueTuple`, que está disponível na Galeria do NuGet. Sem esse pacote, você pode receber um erro de compilação semelhante a "Tipo predefinido 'ValueTuple(Of,,,)' não está definido ou importado."

## <a name="instantiating-and-using-a-tuple"></a>Criando e usando uma tupla

Você pode instanciar uma tupla colocando os parênteses de im valores delimitados por vírgulas. Cada um desses valores, em seguida, torna-se um campo da tupla. Por exemplo, o código a seguir define um triplo (ou uma tupla de 3) com um `Date` como o primeiro valor, um `String` como seu segundo e um `Boolean` como seu terceiro.

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#1)]

Por padrão, o nome de cada campo em uma tupla consiste da cadeia de caracteres `Item` juntamente com base em uma posição na tupla. Para essa tupla de 3, o `Date` campo é `Item1`, o `String` campo é `Item2`e o `Boolean` campo é `Item3`. O exemplo a seguir exibe os valores dos campos da tupla instanciado na linha de código anterior

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#2)]

Os campos de uma tupla de Visual Basic são de leitura-gravação; Depois de instanciar uma tupla, você pode modificar seus valores. O exemplo a seguir modifica duas os três campos da tupla criado no exemplo anterior e exibe o resultado.

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#3)]

## <a name="instantiating-and-using-a-named-tuple"></a>Criando e usando uma tupla nomeada

Em vez de usar os nomes padrão para campos de uma tupla, você pode instanciar uma *chamado tupla* atribuindo seus próprios nomes de elementos da tupla. Os campos da tupla possam ser acessados pelos nomes atribuídos *ou* por seus nomes padrão. O exemplo a seguir cria a mesmo tupla de 3 como anteriormente, exceto que ele explicitamente nomeia o primeiro campo `EventDate`, a segunda `Name`e o terceiro `IsHoliday`. Em seguida, exibe os valores de campo, modifica e exibe os valores de campo novamente.

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#4)]

## <a name="inferred-tuple-element-names"></a>Nomes de elemento de tupla deduzido

Começando com 15,3 do Visual Basic, Visual Basic pode deduzir os nomes dos elementos de tupla; Você não precisa atribuí-las explicitamente. Nomes de tupla deduzidos são úteis quando você inicializar uma tupla de um conjunto de variáveis, e você deseja que o nome do elemento de tupla para ser o mesmo que o nome da variável. 

O exemplo a seguir cria um `stateInfo` tupla que contém três explicitamente chamado elementos, `state`, `stateName`, e `capital`. Observe que, em nomes de elementos, a instrução de inicialização de tupla simplesmente atribui os elementos nomeados os valores das variáveis com o mesmo nome.

[!code-vb[ExplicitlyNamed](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/named-tuples/program.vb#1)]
 
Como variáveis e os elementos têm o mesmo nome, o compilador do Visual Basic pode deduzir os nomes de campos, como mostra o exemplo a seguir.

[!code-vb[ExplicitlyNamed](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/named-tuples/program.vb#2)]

Para habilitar os nomes de elemento de tupla interred, você deve definir a versão do compilador do Visual Basic para usar em seu projeto do Visual Basic (\*. vbproj) arquivo: 

```xml 
<PropertyGroup> 
  <LangVersion>15.3</LangVersion> 
</PropertyGroup> 

The version number can be any version of the Visual Basic compiler starting with 15.3. Rather than hard-coding a specific compiler version, you can also specify "Latest" as the value of `LangVersion` to compile with the most recent version of the Visual Basic compiler installed on your system.

In some cases, the Visual Basic compiler cannot infer the tuple element name from the candidate name, and the tuple field can only be referenced using its default name, such as `Item1`, `Item2`, etc. These include:

- The candidate name is the same as the name of a tuple member, such as `Item3`, `Rest`, or `ToString`.

- The candidate name is duplicated in the tuple.
 
When field name inference fails, Visual Basic does not generate a compiler error, nor is an exception thrown at runtime. Instead, tuple fields must be referenced by their predefined names, such as `Item1` and `Item2`. 
  
## Tuples versus structures

A Visual Basic tuple is a value type that is an instance of one of the a **System.ValueTuple** generic types. For example, the `holiday` tuple defined in the previous example is an instance of the <xref:System.ValueTuple%603> structure. It is designed to be a lightweight container for data. Since the tuple aims to make it easy to create an object with multiple data items, it lacks some of the features that a custom structure might have. These include:

- Customer members. You cannot define your own properties, methods, or events for a tuple.

- Validation. You cannot validate the data assigned to fields.

- Immutability. Visual Basic tuples are mutable. In contrast, a custom structure allows you to control whether an instance is mutable or immutable.

If custom members, property and field validation, or immutability are important, you should use the Visual Basic [Structure](../../../language-reference/statements/structure-statement.md) statement to define a custom value type.

A Visual Basic tuple does inherit the members of its **ValueTuple** type. In addition to its fields, these include the following methods:

| Member | Description |
| ---|---|
| CompareTo | Compares the current tuple to another tuple with the same number of elements. |
| Equals | Determines whether the current tuple is equal to another tuple or object. |
| GetHashCode | Calculates the hash code for the current instance. |
| ToString | Returns the string representation of this tuple, which takes the form `(Item1, Item2...)`, where `Item1` and `Item2` represent the values of the tuple's fields. |

In addition, the **ValueTuple** types implement <xref:System.Collections.IStructuralComparable> and <xref:System.Collections.IStructuralEquatable> interfaces, which allow you to define customer comparers.

## Assignment and tuples

Visual Basic supports assignment between tuple types that have the same number of fields. The field types can be converted if one of the following is true:

- The source and target field are of the same type.

- A widening (or implicit) conversion of the source type to the target type is defined. 

- `Option Strict` is `On`, and a narrowing (or explicit) conversion of the source type to the target type is defined. This conversion can throw an exception if the source value is outside the range of the target type.

Other conversions are not considered for assignments. Let's look at the kinds of assignments that are allowed between tuple types.

Consider these variables used in the following examples:

[!code-vb[Assign](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple3.vb#1)]

The first two variables, `unnamed` and `anonymous`, do not have semantic names provided for the fields. Their field names are the default `Item1` and `Item2`. The last two variables, `named` and `differentName` have semantic field names. Note that these two tuples have different names for the fields.

All four of these tuples have the same number of fields (referred to as 'arity'), and the types of those fields are identical. Therefore, all of these assignments work:

[!code-vb[Assign](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple3.vb#2)]

Notice that the names of the tuples are not assigned. The values of the fields are assigned following the order of the fields in the tuple.

Finally, notice that we can assign the `named` tuple to the `conversion` tuple, even though the first field of `named` is an `Integer`, and the first field of `conversion` is a `Long`. This assignment succeeds because converting an `Integer` to a `Long` is a widening conversion.

[!code-vb[Assign](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple3.vb#3)]

Tuples with different numbers of fields are not assignable:

```vb
' Does not compile.
' VB30311: Value of type '(Integer, Integer, Integer)' cannot be converted
'          to '(Answer As Integer, Message As String)'
var differentShape = (1, 2, 3)
named = differentShape
```

## <a name="tuples-as-method-return-values"></a>Tuplas como valores retornados do método

Um método pode retornar apenas um único valor. Com frequência, no entanto, você gostaria que uma chamada de método para retornar vários valores. Há várias maneiras de contornar essa limitação:

- Você pode criar uma classe personalizada ou estrutura cujas propriedades ou campos representam os valores retornados pelo método. Portanto, é uma solução de peso; ele requer que você defina um tipo personalizado cujo único propósito é recuperar valores de uma chamada de método.

- Você pode retornar um único valor do método e retornar os valores restantes, passando-os por referência para o método. Isso envolve a sobrecarga de criar uma instância de uma variável e riscos sobrescrever inadvertidamente o valor da variável é passada por referência.

- Você pode usar uma tupla, que fornece uma solução simples para recuperar vários valores de retorno.

Por exemplo, o **TryParse** métodos de retorno de .NET um `Boolean` valor que indica se a operação de análise foi bem-sucedida. O resultado da operação de análise é retornado em uma variável passada por referência para o método. Normalmente, uma chamada para a um método de análise, como <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> parece com o seguinte:

[!code-vb[Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#1)]

É possível retornar uma tupla da operação de análise se encerrar a chamada para o <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> método no nosso próprio método. No exemplo a seguir, `NumericLibrary.ParseInteger` chama o <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> método e retorna uma tupla nomeada com dois elementos. 

[!code-vb[Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#2)]

Em seguida, você pode chamar o método com o código como o seguinte:

[!code-vb[Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#3)]

## <a name="visual-basic-tuples-and-tuples-in-the-net-framework"></a>Tuplas de Visual Basic e tuplas no .NET Framework

Uma coleção de itens do Visual Basic é uma instância de uma a **System.ValueTuple** tipos genéricos, que foram introduzidos no .NET Framework 4.7. O .NET Framework também inclui um conjunto de genérica **System.Tuple** classes. Essas classes, no entanto, são diferentes de tuplas do Visual Basic e o **System.ValueTuple** tipos genéricos de várias maneiras:

- Os elementos do **tupla** classes são propriedades chamadas `Item1`, `Item2`e assim por diante. No Visual Basic tuplas e **ValueTuple** tipos de elementos de tupla são campos.

- Você não pode atribuir nomes significativos para os elementos de um **tupla** instância ou de um **ValueTuple** instância. Visual Basic permite que você atribua nomes que se comunicam o significado dos campos.

- As propriedades de um **tupla** instância são somente leitura; as tuplas imutáveis. No Visual Basic tuplas e **ValueTuple** tipos, campos de tupla são leitura / gravação; as tuplas são mutáveis.

- Genérica **tupla** tipos são tipos de referência. Usando esses **tupla** tipos significa que a alocação de objetos. Em caminhos de acesso, isso pode ter um impacto mensurável no desempenho do aplicativo. Tuplas de Visual Basic e o **ValueTuple** tipos são tipos de valor.

Métodos de extensão no <xref:System.TupleExtensions> classe facilitam a conversão entre tuplas do Visual Basic e o .NET **tupla** objetos. O **ToTuple** método converte uma tupla de Visual Basic .NET **tupla** objeto e o **ToValueTuple** método converte .NET **tupla** objeto para uma coleção de itens do Visual Basic.

O exemplo a seguir cria uma tupla, converte-o em .NET **tupla** objeto e converte-o novamente para uma coleção de itens do Visual Basic. O exemplo, em seguida, compara essa tupla com o original para garantir que eles são iguais.

[!code-vb[Convert](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple2.vb#1)]

## <a name="see-also"></a>Consulte também

[Referência da linguagem Visual Basic](index.md)  
