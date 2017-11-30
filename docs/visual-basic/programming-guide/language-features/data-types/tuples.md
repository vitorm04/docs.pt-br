---
title: Tuplas no Visual Basic
ms.custom: 
ms.date: 04/23/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords: tuples [Visual Basic]
ms.assetid: 3e66cd1b-3432-4e1d-8c37-5ebacae8f53f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: be50b22e9acca9ff8cfbde798d78869ee1c72634
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
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

## <a name="tuples-versus-structures"></a>Tuplas versus estruturas

Uma coleção de itens do Visual Basic é um tipo de valor que é uma instância de um a um **System.ValueTuple** tipos genéricos. Por exemplo, o `holiday` tupla definida no exemplo anterior é uma ocorrência da <xref:System.ValueTuple%603> estrutura. Ele é projetado para ser um contêiner leve para dados. Desde que a tupla vise para tornar mais fácil criar um objeto com vários itens de dados, ele não tem alguns dos recursos que pode ter uma estrutura personalizada. Elas incluem:

- Membros de cliente. Você não pode definir suas próprias propriedades, métodos ou eventos de uma tupla.

- Validação. Não é possível validar os dados atribuídos aos campos.

- Imutabilidade. Visual Basic tuplas serão mutáveis. Em contraste, uma estrutura personalizada permite controlar se uma instância é mutável ou imutável.

Se membros personalizados, a propriedade e a validação de campo ou a imutabilidade forem importante, você deve usar o Visual Basic [estrutura](../../../language-reference/statements/structure-statement.md) instrução para definir um tipo de valor personalizado.

Uma tupla de Visual Basic herdam os membros de sua **ValueTuple** tipo. Além de seus campos, eles incluem os seguintes métodos:

| Membro | Descrição |
| ---|---|
| CompareTo | Compara a tupla atual para outra tupla com o mesmo número de elementos. |
| Igual a | Determina se a tupla atual é igual a outro objeto ou tupla. |
| GetHashCode | Calcula o código hash para a instância atual. |
| ToString | Retorna a representação de cadeia de caracteres dessa tupla, que utiliza o formato `(Item1, Item2...)`, onde `Item1` e `Item2` representam os valores dos campos da tupla. |

Além disso, o **ValueTuple** tipos implementam <xref:System.Collections.IStructuralComparable> e <xref:System.Collections.IStructuralEquatable> interfaces, que permitem que você defina comparadores de cliente.

## <a name="assignment-and-tuples"></a>Atribuição e tuplas

Visual Basic oferece suporte à atribuição entre tipos de coleção de itens que têm o mesmo número de campos. Os tipos de campo podem ser convertidos se uma das seguintes opções for verdadeira:

- O campo de origem e destino são do mesmo tipo.

- Uma conversão de ampliação (ou implícita) do tipo de origem para o tipo de destino é definida. 

- `Option Strict`é `On`, e uma conversão de estreitamento (ou explícita) do tipo de origem para o tipo de destino é definida. Esta conversão pode lançar uma exceção se o valor de origem está fora do intervalo do tipo de destino.

Outras conversões não são consideradas para atribuições. Vamos examinar os tipos de atribuições que são permitidos entre tipos de tupla.

Considere estas variáveis usadas nos exemplos a seguir:

[!code-vb[Assign](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple3.vb#1)]

As primeiras duas variáveis, `unnamed` e `anonymous`, não tem semânticos nomes fornecidos para os campos. Seus nomes de campo são o padrão `Item1` e `Item2`. As duas últimas variáveis, `named` e `differentName` têm nomes de campo semântica. Observe que essas duas tuplas têm nomes diferentes para os campos.

Todos os quatro essas tuplas têm o mesmo número de campos (conhecido como 'arity') e os tipos desses campos são idênticos. Portanto, todas essas atribuições funcionam:

[!code-vb[Assign](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple3.vb#2)]

Observe que os nomes das tuplas não são atribuídos. Os valores dos campos são atribuídos na ordem dos campos na tupla.

Finalmente, observe que podemos atribuir a `named` tupla para o `conversion` tupla, mesmo que o primeiro campo de `named` é um `Integer`e o primeiro campo de `conversion` é um `Long`. Essa atribuição é bem-sucedido porque convertendo um `Integer` para um `Long` é uma conversão de ampliação.

[!code-vb[Assign](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple3.vb#3)]

Tuplas com diferentes números de campos não são atribuíveis:

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
