---
title: Modificador static – Referência de C#
ms.date: 01/22/2020
f1_keywords:
- static
- static_CSharpKeyword
helpviewer_keywords:
- static keyword [C#]
ms.assetid: 5509e215-2183-4da3-bab4-6b7e607a4fdf
ms.openlocfilehash: e7671e9db488a7b50f4ed736864d6fa8d95eef1a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744667"
---
# <a name="static-c-reference"></a>static (Referência de C#)

Use o modificador `static` para declarar um membro estático que pertença ao próprio tipo, em vez de um objeto específico. O modificador de `static` pode ser usado para declarar `static` classes. Em classes, interfaces e structs, você pode adicionar o modificador de `static` a campos, métodos, propriedades, operadores, eventos e construtores. O modificador de `static` não pode ser usado com indexadores ou finalizadores. Para obter mais informações, consulte [Classes estáticas e membros de classes estáticas](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md).

## <a name="example"></a>{1&gt;Exemplo&lt;1}

A seguinte classe é declarada como `static` e contém apenas métodos `static`:

[!code-csharp[csrefKeywordsModifiers#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#18)]

Uma constante ou declaração de tipo é implicitamente um membro `static`. Um membro `static` não pode ser referenciado por meio de uma instância. Em vez disso, ele é referenciado por meio do nome do tipo. Por exemplo, considere a seguinte classe:

[!code-csharp[csrefKeywordsModifiers#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#19)]

Para consultar o membro `static` `x`, use o nome totalmente qualificado, `MyBaseC.MyStruct.x`, a menos que o membro seja acessível do mesmo escopo:

```csharp
Console.WriteLine(MyBaseC.MyStruct.x);
```

Embora uma instância de uma classe contenha uma cópia separada de todos os campos de instância da classe, há apenas uma cópia de cada campo de `static`.

Não é possível usar [`this`](this.md) para fazer referência a métodos `static` ou acessadores de propriedade.

Se a palavra-chave `static` for aplicada a uma classe, todos os membros da classe deverão ser `static`.

Classes, interfaces e classes de `static` podem ter construtores de `static`. Um construtor de `static` é chamado em algum ponto entre quando o programa é iniciado e a classe é instanciada.

> [!NOTE]
> A palavra-chave `static` tem utilizações mais limitadas do que no C++. Para comparar com a palavra-chave do C++, consulte [Storage classes (C++)](/cpp/cpp/storage-classes-cpp#static) (Classes de armazenamento (C++)).

Para demonstrar `static` Membros, considere uma classe que representa um funcionário da empresa. Suponha que a classe contém um método para contar funcionários e um campo para armazenar o número de funcionários. O método e o campo não pertencem a uma instância de funcionário. Em vez disso, eles pertencem à classe de funcionários como um todo. Eles devem ser declarados como membros `static` da classe.

## <a name="example"></a>{1&gt;Exemplo&lt;1}

Este exemplo lê o nome e a ID de um novo funcionário, incrementa o contador de funcionário em um e exibe as informações do novo funcionário e do novo número de funcionários. Este programa lê o número atual de funcionários do teclado.

[!code-csharp[csrefKeywordsModifiers#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#20)]  

## <a name="example"></a>{1&gt;Exemplo&lt;1}

Este exemplo mostra que você pode inicializar um campo de `static` usando outro campo de `static` que ainda não está declarado. Os resultados serão indefinidos até que você atribua explicitamente um valor ao campo `static`.

[!code-csharp[csrefKeywordsModifiers#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#21)]  

## <a name="c-language-specification"></a>Especificação da linguagem C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)
- [Guia de Programação em C#](../../programming-guide/index.md)
- [Palavras-chave do C#](index.md)
- [Modificadores](index.md)
- [Classes static e membros de classes static](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md)
