---
title: base (Referência de C#)
description: Saiba mais sobre a palavra-chave base, que é usada para acessar membros da classe base de dentro de uma classe derivada em C#.
ms.date: 07/20/2015
f1_keywords:
- base
- BaseClass.BaseClass
- base_CSharpKeyword
helpviewer_keywords:
- base keyword [C#]
ms.assetid: 8b645dbe-1a33-49b8-8716-1c401f9a5ea5
ms.openlocfilehash: 69885ba0b2d05c79f2b7ba9458e7ba8c8b7aa0c2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33214475"
---
# <a name="base-c-reference"></a>base (Referência de C#)

A palavra-chave `base` é usada para acessar membros de classe base de dentro de uma classe derivada:

- Chamar um método que foi substituído por outro método na classe base.

- Especificar qual construtor de classe base deve ser chamado ao criar instâncias da classe derivada.

Um acesso de classe base é permitido somente em um construtor, em um método de instância ou em um acessador de propriedade de instância.

É um erro usar a palavra-chave `base` de dentro de um método estático.

A classe base que é acessada é a que é especificada na declaração de classe. Por exemplo, se você especificar `class ClassB : ClassA`, os membros da ClassA são acessados da ClassB, independentemente da classe base da ClassA.

## <a name="example"></a>Exemplo
Neste exemplo, as classes base `Person` e a classe derivada `Employee` têm um método chamado `Getinfo`. Usando a palavra-chave `base`, é possível chamar o método `Getinfo` na classe base, de dentro da classe derivada.

[!code-csharp[csrefKeywordsAccess#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/base_1.cs)]

Para obter exemplos adicionais, consulte [new](../../../csharp/language-reference/keywords/new.md), [virtual](../../../csharp/language-reference/keywords/virtual.md) e [override](../../../csharp/language-reference/keywords/override.md).

## <a name="example"></a>Exemplo
Este exemplo mostra como especificar o construtor da classe base chamado ao criar instâncias de uma classe derivada.

[!code-csharp[csrefKeywordsAccess#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/base_2.cs)]

## <a name="c-language-specification"></a>especificação da linguagem C#
[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Consulte também
 [Referência de C#](../../../csharp/language-reference/index.md)  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
 [Palavras-chave do C#](../../../csharp/language-reference/keywords/index.md)  
 [this](../../../csharp/language-reference/keywords/this.md)