---
title: Palavra-chave class – Referência de C#
ms.custom: seodec18
ms.date: 07/18/2017
f1_keywords:
- class_CSharpKeyword
- class
helpviewer_keywords:
- class keyword [C#]
ms.assetid: b95d8815-de18-4c3f-a8cc-a0a53bdf8690
ms.openlocfilehash: 0c4fc9645e43f23e340804b46bbe8a5faa19525d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69922384"
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

Classes que você declara diretamente dentro de um namespace, não aninhadas em outras classes, podem ser [públicas](./public.md) ou [internas](./internal.md). As classes são `internal` por padrão.

Os membros da classe, incluindo classes aninhadas, podem ser [públicos](public.md), [internos protegidos](protected-internal.md), [protegidos](protected.md), [internos](internal.md), [privados](private.md) ou [protegidos privados](private-protected.md). Os membros são `private` por padrão.

Para obter mais informações, consulte [Modificadores de Acesso](../../programming-guide/classes-and-structs/access-modifiers.md).

É possível declarar classes genéricas que têm parâmetros de tipo. Para obter mais informações, consulte [Classes genéricas](../../programming-guide/generics/generic-classes.md).

Uma classe pode conter declarações dos seguintes membros:

- [Construtores](../../programming-guide/classes-and-structs/constructors.md)

- [Constantes](../../programming-guide/classes-and-structs/constants.md)

- [Campos](../../programming-guide/classes-and-structs/fields.md)

- [Finalizadores](../../programming-guide/classes-and-structs/destructors.md)

- [Métodos](../../programming-guide/classes-and-structs/methods.md)

- [Propriedades](../../programming-guide/classes-and-structs/properties.md)

- [Indexadores](../../programming-guide/indexers/index.md)

- [Operadores](../operators/index.md)

- [Eventos](../../programming-guide/events/index.md)

- [Delegados](../../programming-guide/delegates/index.md)

- [Classes](../../programming-guide/classes-and-structs/classes.md)

- [Interfaces](../../programming-guide/interfaces/index.md)

- [Estruturas](../../programming-guide/classes-and-structs/structs.md)

- [Enumerações](../../programming-guide/enumeration-types.md)

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

Por fim, observe que, para o objeto criado usando o construtor sem parâmetro (`child3`), o campo `age` foi inicializado como zero por padrão.

## <a name="c-language-specification"></a>Especificação da linguagem C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)
- [Guia de Programação em C#](../../programming-guide/index.md)
- [Palavras-chave do C#](./index.md)
- [Tipos de referência](./reference-types.md)
