---
title: Tipos de estrutura - Referência C#
ms.date: 04/14/2020
f1_keywords:
- struct_CSharpKeyword
helpviewer_keywords:
- struct keyword [C#]
- struct type [C#]
- structure type [C#]
ms.assetid: ff3dd9b7-dc93-4720-8855-ef5558f65c7c
ms.openlocfilehash: 8013aab5580ac007875debc78208532a2d0ad1dc
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/15/2020
ms.locfileid: "81388987"
---
# <a name="structure-types-c-reference"></a>Tipos de estrutura (referência C#)

Um *tipo de estrutura* (ou tipo de *estrutura)* é um tipo de [valor](value-types.md) que pode encapsular dados e funcionalidades relacionadas. Você usa `struct` a palavra-chave para definir um tipo de estrutura:

[!code-csharp[struct example](snippets/StructType.cs#StructExample)]

Os tipos de estrutura têm *semântica de valor.* Ou seja, uma variável de um tipo de estrutura contém uma instância do tipo. Por padrão, os valores variáveis são copiados na atribuição, passando um argumento para um método e retornando um resultado do método. No caso de uma variável do tipo estrutura, uma instância do tipo é copiada. Para obter mais informações, consulte [Tipos de valor](value-types.md).

Normalmente, você usa tipos de estrutura para projetar pequenos tipos centrados em dados que fornecem pouco ou nenhum comportamento. Por exemplo, .NET usa tipos de estrutura para representar um número [(inteiro](integral-numeric-types.md) e [real),](floating-point-numeric-types.md)um [valor booleano,](bool.md)um [caractere Unicode,](char.md)uma [instância de tempo](xref:System.DateTime). Se você está focado no comportamento de um tipo, considere definir uma [classe.](../keywords/class.md) Os tipos de classe têm *semântica de referência.* Ou seja, uma variável de um tipo de classe contém uma referência a uma instância do tipo, não à instância em si.

Como os tipos de estrutura têm semântica de valor, recomendamos que você defina tipos de estrutura *imutáveis.*

## <a name="readonly-struct"></a>`readonly`Struct

Começando com C# 7.2, `readonly` você usa o modificador para declarar que um tipo de estrutura é imutável:

[!code-csharp[readonly struct](snippets/StructType.cs#ReadonlyStruct)]

Todos os membros `readonly` de dados de uma estrutura devem ser lidos apenas da seguinte forma:

- Qualquer declaração de campo deve ter o [ `readonly` modificador](../keywords/readonly.md)
- Qualquer propriedade, incluindo as implementadas automaticamente, deve ser somente leitura

Isso garante que nenhum `readonly` membro de uma estrutura modifica o estado da estrutura.

> [!NOTE]
> Em `readonly` uma estrutura, um membro de dados de um tipo de referência mutável ainda pode mutar seu próprio estado. Por exemplo, você <xref:System.Collections.Generic.List%601> não pode substituir uma instância, mas você pode adicionar novos elementos a ela.

## <a name="readonly-instance-members"></a>`readonly`membros de instância

Começando com C# 8.0, você `readonly` também pode usar o modificador para declarar que um membro de instância não modifica o estado de uma estrutura. Se você não puder declarar `readonly`todo `readonly` o tipo de estrutura como , use o modificador para marcar os membros de ocorrência que não modificam o estado da estrutura. Em `readonly` uma estrutura, cada membro de `readonly`instância é implicitamente .

Dentro `readonly` de um membro de instância, você não pode atribuir aos campos de instância da estrutura. No entanto, um `readonly` membro`readonly` pode chamar um não-membro. Nesse caso, o compilador cria uma cópia da instância`readonly` da estrutura e chama o não-membro nessa cópia. Como resultado, a instância original da estrutura não é modificada.

Normalmente, você `readonly` aplica o modificador aos seguintes tipos de membros de instância:

- Métodos:

  [!code-csharp[readonly method](snippets/StructType.cs#ReadonlyMethod)]

  Você também pode `readonly` aplicar o modificador a métodos <xref:System.Object?displayProperty=nameWithType>que anulam métodos declarados em :

  [!code-csharp[readonly override](snippets/StructType.cs#ReadonlyOverride)]

- propriedades e indexadores:

  [!code-csharp[readonly property get](snippets/StructType.cs#ReadonlyProperty)]

  Se você precisar `readonly` aplicar o modificador em ambos os acessórios de uma propriedade ou indexador, aplique-o na declaração do imóvel ou indexador.

  > [!NOTE]
  > O compilador declara `get` um acessório de uma `readonly` [propriedade auto-implementada](../../programming-guide/classes-and-structs/auto-implemented-properties.md) `readonly` como , independentemente da presença do modificador em uma declaração de propriedade.

Não é `readonly` possível aplicar o modificador a membros estáticos de um tipo de estrutura.

O compilador pode fazer `readonly` uso do modificador para otimizações de desempenho. Para obter mais informações, consulte [Escrever código C# seguro e eficiente](../../write-safe-efficient-code.md).

## <a name="limitations-with-the-design-of-a-structure-type"></a>Limitações com o design de um tipo de estrutura

Quando você projeta um tipo de estrutura, você tem os mesmos recursos que com um tipo [de classe,](../keywords/class.md) com as seguintes exceções:

- Você não pode declarar um construtor sem parâmetros. Cada tipo de estrutura já fornece um construtor implícito sem parâmetros que produz o [valor padrão](default-values.md) do tipo.

- Você não pode inicializar um campo de instância ou propriedade em sua declaração. No entanto, você pode inicializar um campo [estático](../keywords/static.md) ou [const](../keywords/const.md) ou uma propriedade estática em sua declaração.

- Um construtor de um tipo de estrutura deve inicializar todos os campos de instância do tipo.

- Um tipo de estrutura não pode herdar de outra classe ou tipo de estrutura e não pode ser a base de uma classe. No entanto, um tipo de estrutura pode implementar [interfaces.](../keywords/interface.md)

- Você não pode declarar um [finalizador](../../programming-guide/classes-and-structs/destructors.md) dentro de um tipo de estrutura.

## <a name="instantiation-of-a-structure-type"></a>Instantiva de um tipo de estrutura

Em C#, você deve inicializar uma variável declarada antes que ela possa ser usada. Como uma variável do `null` tipo de estrutura não pode ser (a menos que seja uma variável de um tipo de [valor anulado),](nullable-value-types.md)você deve instanciar uma instância do tipo correspondente. Há várias maneiras de fazer isso.

Normalmente, você instancia um tipo de estrutura [`new`](../operators/new-operator.md) ligando para um construtor apropriado com o operador. Cada tipo de estrutura tem pelo menos um construtor. É um construtor implícito sem parâmetros, que produz o [valor padrão](default-values.md) do tipo. Você também pode usar uma [expressão de valor padrão](../operators/default.md) para produzir o valor padrão de um tipo.

Se todos os campos de exemplo de um tipo de `new` estrutura estiverem acessíveis, você também poderá instancia-lo sem o operador. Nesse caso, você deve inicializar todos os campos de instância antes do primeiro uso da instância. O seguinte exemplo mostra como fazer isso:

[!code-csharp[without new](snippets/StructType.cs#WithoutNew)]

No caso dos [tipos de valor embutidos,](value-types.md#built-in-value-types)use os literais correspondentes para especificar um valor do tipo.

## <a name="passing-structure-type-variables-by-reference"></a>Passando variáveis de tipo de estrutura por referência

Quando você passa uma variável de tipo de estrutura para um método como argumento ou retorna um valor de tipo de estrutura a partir de um método, toda a instância de um tipo de estrutura é copiada. Isso pode afetar o desempenho do seu código em cenários de alto desempenho que envolvem grandes tipos de estrutura. Você pode evitar a cópia de valor passando uma variável tipo de estrutura por referência. Use [`ref`](../keywords/ref.md#passing-an-argument-by-reference)os [`out`](../keywords/out-parameter-modifier.md)modificadores do parâmetro , ou [`in`](../keywords/in-parameter-modifier.md) método para indicar que um argumento deve ser aprovado por referência. Use [o retorno do ref](../../programming-guide/classes-and-structs/ref-returns.md) para retornar um resultado do método por referência. Para obter mais informações, consulte [Escrever código C# seguro e eficiente](../../write-safe-efficient-code.md).

## <a name="conversions"></a>Conversões

Para qualquer tipo de estrutura, existem conversões <xref:System.ValueType?displayProperty=nameWithType> de <xref:System.Object?displayProperty=nameWithType> boxe [e unboxing](../../programming-guide/types/boxing-and-unboxing.md) para e de e tipos. Existem também conversões de boxe e unboxing entre um tipo de estrutura e qualquer interface que implemente.

## <a name="c-language-specification"></a>especificação da linguagem C#

Para obter mais informações, consulte a seção [Structs](~/_csharplang/spec/structs.md) da [especificação do idioma C#.](~/_csharplang/spec/introduction.md)

Para obter mais informações sobre os recursos introduzidos no C# 7.2 e posteriores, consulte as seguintes notas de proposta de recurso:

- [Structs somente leitura](~/_csharplang/proposals/csharp-7.2/readonly-ref.md#readonly-structs)
- [Membros da instância ReadOnly](~/_csharplang/proposals/csharp-8.0/readonly-instance-members.md)

## <a name="see-also"></a>Confira também

- [Referência do C#](../index.md)
- [Diretrizes de design - Escolha entre classe e estrutura](../../../standard/design-guidelines/choosing-between-class-and-struct.md)
- [Diretrizes de design - Projeto de estrutura](../../../standard/design-guidelines/struct.md)
- [Aulas e estruturas](../../programming-guide/classes-and-structs/index.md)
