---
title: "base (Referência de C#)"
description: "Saiba mais sobre a palavra-chave base, que é usada para acessar membros da classe base de dentro de uma classe derivada em C#."
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- base
- BaseClass.BaseClass
- base_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- base keyword [C#]
ms.assetid: 8b645dbe-1a33-49b8-8716-1c401f9a5ea5
caps.latest.revision: 14
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 867f9eb286fa7ff5ef3e9167c1ab944c81161216
ms.openlocfilehash: b3a389d92373b6ba5995a7644b0440f9d8fad9ac
ms.contentlocale: pt-br
ms.lasthandoff: 08/17/2017

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

[!code-cs[csrefKeywordsAccess#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/base_1.cs)]

Para obter exemplos adicionais, consulte [new](../../../csharp/language-reference/keywords/new.md), [virtual](../../../csharp/language-reference/keywords/virtual.md) e [override](../../../csharp/language-reference/keywords/override.md).

## <a name="example"></a>Exemplo
Este exemplo mostra como especificar o construtor da classe base chamado ao criar instâncias de uma classe derivada.

[!code-cs[csrefKeywordsAccess#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/base_2.cs)]

## <a name="c-language-specification"></a>especificação da linguagem C#
[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Consulte também
 [Referência de C#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Palavras-chave de C#](../../../csharp/language-reference/keywords/index.md)   
 [this](../../../csharp/language-reference/keywords/this.md)
