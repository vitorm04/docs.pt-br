---
title: Structs – Guia de C#
description: Saiba mais sobre os tipos de struct e como criá-los
ms.date: 10/12/2016
ms.technology: csharp-fundamentals
ms.assetid: a7094b8c-7229-4b6f-82fc-824d0ea0ec40
ms.openlocfilehash: cdfe2a763058b8f568ede2ff93c918c2dae874f7
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346896"
---
# <a name="structs"></a>Structs

Um *struct* é um tipo de valor. Quando um struct é criado, a variável à qual o struct está atribuído contém os dados reais do struct. Quando o struct é atribuído a uma nova variável, ele é copiado. A nova variável e a variável original, portanto, contêm duas cópias separadas dos mesmos dados. As alterações feitas em uma cópia não afetam a outra cópia.

As variáveis de tipo de valor contêm diretamente seus valores, o que significa que a memória é alocada embutida em qualquer contexto em que a variável é declarada. Não há nenhuma alocação de heap separada ou sobrecarga de coleta de lixo para variáveis do tipo de valor.

Há duas categorias de tipos de valor: [struct](language-reference/keywords/struct.md) e [enum](language-reference/builtin-types/enum.md).

Os tipos numéricos internos são structs e têm propriedades e métodos que você pode acessar:

[!code-csharp[Static Method](../../samples/snippets/csharp/concepts/structs/static-method.cs)]

Mas você declara e atribui valores a eles como se fossem tipos de não agregação simples:

[!code-csharp[Assign Values](../../samples/snippets/csharp/concepts/structs/assign-value.cs)]

Tipos de valor são *lacrados*, o que significa, por exemplo, que você não pode derivar um tipo de <xref:System.Int32> e não pode definir um struct para herdar de qualquer struct ou classe definida pelo usuário, porque um struct apenas pode herdar de <xref:System.ValueType>. No entanto, um struct pode implementar uma ou mais interfaces. Você pode converter um tipo de structs para um tipo de interface. Isso faz com que uma operação de *conversão boxing* encapsule o struct dentro de um objeto de tipo de referência no heap gerenciado. Operações de conversão boxing ocorrem quando você passa um tipo de valor para um método que usa um <xref:System.Object> como parâmetro de entrada. Para obter mais informações, consulte [Conversões boxing e unboxing](./programming-guide/types/boxing-and-unboxing.md ).

Você usa a palavra-chave [struct](./language-reference/keywords/struct.md) para criar seus próprios tipos de valor personalizados. Normalmente, um struct é usado como um contêiner para um pequeno conjunto de variáveis relacionadas, conforme mostrado no exemplo a seguir:

[!code-csharp[Struct Keyword](../../samples/snippets/csharp/concepts/structs/struct-keyword.cs)]

Para obter mais informações sobre os tipos de valor no .NET Framework, consulte [Common Type System](../standard/common-type-system.md).

Na maioria das vezes, os structs compartilham a mesma sintaxe das classes, embora os structs sejam mais limitados que as classes:

- Dentro de uma declaração de struct, os campos não podem ser inicializados, a menos que sejam declarados como `const` ou `static`.

- Um struct não pode declarar um construtor sem padrão (um construtor sem parâmetros) ou um finalizador.

- Os structs são copiados na atribuição. Quando um struct recebe uma nova variável, todos os dados são copiados e qualquer modificação na nova cópia não altera os dados da cópia original. É importante se lembrar disso ao trabalhar com coleções de tipos de valor como Dictionary<string, myStruct>.

- Structs são tipos de valor e classes são tipos de referência.

- Diferentemente das classes, os structs podem ser instanciados sem usar um operador `new`.

   > [!NOTE]
   > No .NET Core 2,1 e posterior, um tipo de struct deve ser instanciado usando o [novo operador](language-reference/operators/new-operator.md) ou o [literal padrão](language-reference/operators/default.md#default-literal), ou inicializando cada um de seus campos particulares. Para obter mais informações, consulte [alterações recentes de migração da versão 2,0 para 2,1](../core/compatibility/2.0-2.1.md#corefx).

- Os structs podem declarar construtores que têm parâmetros.

- Um struct não pode herdar de outra estrutura ou classe e ele não pode ser a base de uma classe. Todos os structs herdam diretamente do <xref:System.ValueType>, que herda do <xref:System.Object>.

- Uma struct, como uma classe, pode implementar interfaces.

## <a name="nullable-value-types"></a>tipos que permitem valor nulo

Os tipos comuns de valor não podem ter um valor [nulo](language-reference/keywords/null.md). No entanto, você pode criar tipos de valor anulável afixando uma `?` após o tipo. Por exemplo, `int?` é um tipo `int` que também pode ter o valor [nulo](./language-reference/keywords/null.md). Os tipos de valores anuláveis são instâncias do tipo struct genérico <xref:System.Nullable%601>. Os tipos de valor anulável são especialmente úteis quando você está passando dados de e para bancos de dado nos quais valores numéricos podem ser nulos ou indefinidos. Para obter mais informações, consulte [tipos de valor anulável](language-reference/builtin-types/nullable-value-types.md).

## <a name="see-also"></a>Veja também

- [Classes](programming-guide/classes-and-structs/classes.md)
- [Tipos Básicos](basic-types.md)
