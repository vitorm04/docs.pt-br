---
title: Restrições a parâmetros de tipo – Guia de Programação em C#
ms.custom: seodec18
ms.date: 04/12/2018
helpviewer_keywords:
- generics [C#], type constraints
- type constraints [C#]
- type parameters [C#], constraints
- unbound type parameter [C#]
ms.openlocfilehash: d05307735506db0f0e4abab067334e4f0466ee6a
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/20/2019
ms.locfileid: "74204633"
---
# <a name="constraints-on-type-parameters-c-programming-guide"></a>Restrições a parâmetros de tipo (Guia de Programação em C#)

Restrições informam o compilador sobre as funcionalidades que um argumento de tipo deve ter. Sem nenhuma restrição, o argumento de tipo poderia ser qualquer tipo. O compilador pode assumir somente os membros de <xref:System.Object?displayProperty=nameWithType>, que é a classe base definitiva para qualquer tipo .NET. Para obter mais informações, consulte [Por que usar restrições](#why-use-constraints). Se o código de cliente tentar criar uma instância da classe usando um tipo não permitido por uma restrição, o resultado será um erro em tempo de compilação. Restrições são especificadas usando a palavra-chave contextual `where`. A tabela a seguir lista os sete tipos de restrições:

|Restrição|Descrição|
|----------------|-----------------|
|`where T : struct`|The type argument must be a non-nullable value type. For information about nullable value types, see [Nullable value types](../../language-reference/builtin-types/nullable-value-types.md). Because all value types have an accessible parameterless constructor, the `struct` constraint implies the `new()` constraint and can't be combined with the `new()` constraint. You also cannot combine the `struct` constraint with the `unmanaged` constraint.|
|`where T : class`|O argumento de tipo deve ser um tipo de referência. Essa restrição se aplica também a qualquer classe, interface, delegado ou tipo de matriz.|
|`where T : notnull`|The type argument must be a non-nullable type. The argument can be a non-nullable reference type in C# 8.0 or later, or a not nullable value type. Essa restrição se aplica também a qualquer classe, interface, delegado ou tipo de matriz.|
|`where T : unmanaged`|The type argument must be a non-nullable [unmanaged type](../../language-reference/builtin-types/unmanaged-types.md). The `unmanaged` constraint implies the `struct` constraint and can't be combined with either the `struct` or `new()` constraints.|
|`where T : new()`|O argumento de tipo deve ter um construtor público sem parâmetros. Quando usado em conjunto com outras restrições, a restrição `new()` deve ser a última a ser especificada. The `new()` constraint can't be combined with the `struct` and `unmanaged` constraints.|
|`where T :` *\<nome de classe base>*|O argumento de tipo deve ser ou derivar da classe base especificada.|
|`where T :` *\<nome da interface>*|O argumento de tipo deve ser ou implementar a interface especificada. Várias restrições de interface podem ser especificadas. A interface de restrição também pode ser genérica.|
|`where T : U`|O argumento de tipo fornecido para T deve ser ou derivar do argumento fornecido para U.|

## <a name="why-use-constraints"></a>Por que usar restrições

Ao restringir o parâmetro de tipo, aumenta-se a quantidade de operações e chamadas de método permitidas àqueles com suporte do tipo de restrição e de todos os tipos de sua hierarquia de herança. When you design generic classes or methods, if you'll be performing any operation on the generic members beyond simple assignment or calling any methods not supported by <xref:System.Object?displayProperty=nameWithType>, you'll have to apply constraints to the type parameter. Por exemplo, a restrição de classe base informa ao compilador que somente os objetos desse tipo ou derivados desse tipo serão usados como argumentos de tipo. Uma vez que o compilador tiver essa garantia, ele poderá permitir que métodos desse tipo sejam chamados na classe genérica. O exemplo de código a seguir demonstra a funcionalidade que pode ser adicionada à classe `GenericList<T>` (em [Introdução aos Genéricos](../../../standard/generics/index.md)) ao aplicar uma restrição de classe base.

[!code-csharp[using the class and struct constraints](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#9)]

A restrição permite que a classe genérica use a propriedade `Employee.Name`. A restrição especifica que todos os itens do tipo `T` são um objeto `Employee` ou um objeto que herda de `Employee`.

Várias restrições podem ser aplicadas ao mesmo parâmetro de tipo e as restrições em si podem ser tipos genéricos, da seguinte maneira:

[!code-csharp[using the class and struct constraints](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#10)]

Ao aplicar a restrição `where T : class`, evite os operadores `==` e `!=` no parâmetro de tipo, pois esses operadores testarão somente a identidade de referência e não a igualdade de valor. Esse comportamento ocorrerá mesmo se esses operadores forem sobrecarregados em um tipo usado como argumento. O código a seguir ilustra esse ponto; a saída é false, muito embora a classe <xref:System.String> sobrecarregue o operador `==`.

[!code-csharp[using the class and struct constraints](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#11)]

The compiler only knows that `T` is a reference type at compile time and must use the default operators that are valid for all reference types. Caso seja necessário testar a igualdade de valor, a maneira recomendada é também aplicar a restrição `where T : IEquatable<T>` ou `where T : IComparable<T>` e implementar a interface em qualquer classe que seja usada para construir a classe genérica.

## <a name="constraining-multiple-parameters"></a>Restringindo vários parâmetros

É possível aplicar restrições a vários parâmetros e várias restrições a um único parâmetro, conforme mostrado no exemplo a seguir:

[!code-csharp[using the class and struct constraints](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#12)]

## <a name="unbounded-type-parameters"></a>Parâmetros de tipo não associado

 Os parâmetros de tipo que não têm restrições, como o T na classe pública `SampleClass<T>{}`, são denominados “parâmetros de tipo não associado”. Os parâmetros de tipo não associado têm as seguintes regras:

- The `!=` and `==` operators can't be used because there's no guarantee that the concrete type argument will support these operators.
- Eles podem ser convertidos para e de `System.Object` ou explicitamente convertidos para qualquer tipo de interface.
- Você pode compará-los com [nulo](../../language-reference/keywords/null.md). Se um parâmetro não associado for comparado a `null`, a comparação sempre retornará false se o argumento de tipo for um tipo de valor.

## <a name="type-parameters-as-constraints"></a>Parâmetros de tipo como restrições

O uso de um parâmetro de tipo genérico como uma restrição será útil quando uma função membro com parâmetro de tipo próprio tiver que restringir esse parâmetro para o parâmetro de tipo do tipo recipiente, conforme mostrado no exemplo a seguir:

[!code-csharp[using the class and struct constraints](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#13)]

No exemplo anterior, `T` é uma restrição de tipo no contexto do método `Add` e um parâmetro de tipo não associado no contexto da classe `List`.

Parâmetros de tipo também podem ser usados como restrições em definições de classe genérica. O parâmetro de tipo deve ser declarado entre colchetes angulares junto com quaisquer outros parâmetros de tipo:

[!code-csharp[using the class and struct constraints](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#14)]

A utilidade dos parâmetros de tipo como restrições com classes genéricas é limitada, pois o compilador não pode presumir nada sobre o parâmetro de tipo, exceto que ele deriva de `System.Object`. Use parâmetros de tipo como restrições em classes genéricas em cenários nos quais deseja impor uma relação de herança entre dois parâmetros de tipo.

## <a name="notnull-constraint"></a>NotNull constraint

Beginning with C# 8.0, you can use the `notnull` constraint to specify that the type argument must be a non-nullable value type or non-nullable reference type. The `notnull` constraint can only be used in a `nullable enable` context. The compiler generates a warning if you add the `notnull` constraint in a nullable oblivious context. 

Unlike other constraints, when a type argument violates the `notnull` constraint, the compiler generates a warning when that code is compiled in a `nullable enable` context. If the code is compiled in a nullable oblivious context, the compiler doesn't generate any warnings or errors.

## <a name="unmanaged-constraint"></a>Restrição não gerenciada

Beginning with C# 7.3, you can use the `unmanaged` constraint to specify that the type parameter must be a non-nullable [unmanaged type](../../language-reference/builtin-types/unmanaged-types.md). A restrição `unmanaged` permite que você escreva rotinas reutilizáveis para trabalhar com tipos que podem ser manipulados como blocos de memória, conforme mostrado no exemplo a seguir:

[!code-csharp[using the unmanaged constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#15)]

O método anterior deve ser compilado em um contexto `unsafe` porque ele usa o operador `sizeof` em um tipo não conhecido como um tipo interno. Sem a restrição `unmanaged`, o operador `sizeof` não está disponível.

The `unmanaged` constraint implies the `struct` constraint and can't be combined with it. Because the `struct` constraint implies the `new()` constraint, the `unmanaged` constraint can't be combined with the `new()` constraint as well.

## <a name="delegate-constraints"></a>Restrições de delegado

Também começando com o C# 7.3, você pode usar <xref:System.Delegate?displayProperty=nameWithType> ou <xref:System.MulticastDelegate?displayProperty=nameWithType> como uma restrição de classe base. O CLR sempre permitia essa restrição, mas a linguagem C# não a permite. A restrição `System.Delegate` permite que você escreva código que funcione com delegados de uma maneira fortemente tipada. The following code defines an extension method that combines two delegates provided they're the same type:

[!code-csharp[using the delegate constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#16)]

Você pode usar o método acima para combinar delegados que são do mesmo tipo:

[!code-csharp[using the unmanaged constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#17)]

Se você remover a marca de comentário na última linha, ela não será compilada. Both `first` and `test` are delegate types, but they're different delegate types.

## <a name="enum-constraints"></a>Restrições de enum

Começando com o C# 7.3, você também pode especificar o tipo <xref:System.Enum?displayProperty=nameWithType> como uma restrição de classe base. O CLR sempre permitia essa restrição, mas a linguagem C# não a permite. Genéricos usando `System.Enum` fornecem programação fortemente tipada para armazenar em cache os resultados do uso de métodos estáticos em `System.Enum`. O exemplo a seguir localiza todos os valores válidos para um tipo enum e, em seguida, cria um dicionário que mapeia esses valores para sua representação de cadeia de caracteres.

[!code-csharp[using the unmanaged constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#18)]

Os métodos usados fazem uso de reflexão, o que tem implicações de desempenho. Você pode chamar esse método para criar uma coleção que é armazenada em cache e reutilizada, em vez de repetir as chamadas que exigem reflexão.

Você pode usá-lo conforme mostrado no exemplo a seguir para criar uma enum e compilar um dicionário de seus nomes e valores:

[!code-csharp[using the unmanaged constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#19)]

[!code-csharp[using the unmanaged constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#20)]

## <a name="see-also"></a>Consulte também

- <xref:System.Collections.Generic>
- [Guia de Programação em C#](../index.md)
- [Introdução aos genéricos](./index.md)
- [Classes genéricas](./generic-classes.md)
- [Restrição new](../../language-reference/keywords/new-constraint.md)
