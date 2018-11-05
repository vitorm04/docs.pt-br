---
title: Palavra-chave class (Referência de C#)
ms.date: 07/18/2017
f1_keywords:
- class_CSharpKeyword
- class
helpviewer_keywords:
- class keyword [C#]
ms.assetid: b95d8815-de18-4c3f-a8cc-a0a53bdf8690
ms.openlocfilehash: 3f30fb473b486efc8381faa9076b98763935b0ae
ms.sourcegitcommit: 2eb5ca4956231c1a0efd34b6a9cab6153a5438af
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/11/2018
ms.locfileid: "49086058"
---
# <a name="class-c-reference"></a>class (Referência de C#)

Classes são declaradas usando a palavra-chave `class`, conforme mostrado no exemplo a seguir:

```csharp
class TestClass
{
    // Methods, properties, fields, events, delegates
    // and nested classes go here.
}
```

## <a name="remarks"></a>Comentários

Somente a herança única é permitida em C#. Em outras palavras, uma classe pode herdar a implementação de apenas uma classe base. No entanto, uma classe pode implementar mais de uma interface. A tabela a seguir mostra exemplos de implementação de interface e herança de classe:

|Herança|Exemplo|
|-----------------|-------------|
|Nenhum|`class ClassA { }`|
|Simples|`class DerivedClass: BaseClass { }`|
|Nenhuma, implementa duas interfaces|`class ImplClass: IFace1, IFace2 { }`|
|Única, implementa uma interface|`class ImplDerivedClass: BaseClass, IFace1 { }`|

Classes que você declara diretamente dentro de um namespace, não aninhadas em outras classes, podem ser [públicas](../../../csharp/language-reference/keywords/public.md) ou [internas](../../../csharp/language-reference/keywords/internal.md). As classes são `internal` por padrão.

Os membros da classe, incluindo classes aninhadas, podem ser [públicos](public.md), [internos protegidos](protected-internal.md), [protegidos](protected.md), [internos](internal.md), [privados](private.md) ou [protegidos privados](private-protected.md). Os membros são `private` por padrão.

Para obter mais informações, consulte [Modificadores de Acesso](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).

É possível declarar classes genéricas que têm parâmetros de tipo. Para obter mais informações, consulte [Classes genéricas](../../../csharp/programming-guide/generics/generic-classes.md).

Uma classe pode conter declarações dos seguintes membros:

- [Construtores](../../../csharp/programming-guide/classes-and-structs/constructors.md)

- [Constantes](../../../csharp/programming-guide/classes-and-structs/constants.md)

- [Campos](../../../csharp/programming-guide/classes-and-structs/fields.md)

- [Finalizadores](../../../csharp/programming-guide/classes-and-structs/destructors.md)

- [Métodos](../../../csharp/programming-guide/classes-and-structs/methods.md)

- [Propriedades](../../../csharp/programming-guide/classes-and-structs/properties.md)

- [Indexadores](../../../csharp/programming-guide/indexers/index.md)

- [Operadores](../../../csharp/programming-guide/statements-expressions-operators/operators.md)

- [Eventos](../../../csharp/programming-guide/events/index.md)

- [Delegados](../../../csharp/programming-guide/delegates/index.md)

- [Classes](../../../csharp/programming-guide/classes-and-structs/classes.md)

- [Interfaces](../../../csharp/programming-guide/interfaces/index.md)

- [Estruturas](../../../csharp/programming-guide/classes-and-structs/structs.md)

- [Enumerações](../../../csharp/programming-guide/enumeration-types.md)

## <a name="example"></a>Exemplo

O exemplo a seguir demonstra a declaração de métodos, construtores e campos de classe. Ele também demonstra a instanciação de objetos e a impressão de dados de instância. Neste exemplo, duas classes são declaradas. A primeira classe, `Child`, contém dois campos particulares (`name` e `age`), dois construtores públicos e um método público. A segunda classe, `StringTest`, é usada para conter `Main`.

[!code-csharp[csrefKeywordsTypes#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#5)]

## <a name="comments"></a>Comentários

Observe que, no exemplo anterior, os campos particulares (`name` e `age`) só podem ser acessados por meio dos métodos públicos da classe `Child`. Por exemplo, você não pode imprimir o nome do filho, do método `Main`, usando uma instrução como esta:

```csharp
Console.Write(child1.name);   // Error
```

Acessar membros particulares de `Child` de `Main` seria possível apenas se `Main` fosse um membro da classe.

Tipos declarados dentro de uma classe sem um modificador de acesso têm o valor padrão de `private`, portanto, os membros de dados neste exemplo ainda seriam `private` se a palavra-chave fosse removida.

Por fim, observe que, para o objeto criado usando o construtor padrão (`child3`), o campo de idade foi inicializado como zero por padrão.

## <a name="c-language-specification"></a>especificação da linguagem C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Consulte também

- [Referência de C#](../../../csharp/language-reference/index.md)  
- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
- [Palavras-chave do C#](../../../csharp/language-reference/keywords/index.md)  
- [Tipos de referência](../../../csharp/language-reference/keywords/reference-types.md)
