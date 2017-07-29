---
title: "when (Referência de C#)"
ms.date: 2017-03-07
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- when_CSharpKeyword
- when
dev_langs:
- CSharp
helpviewer_keywords:
- when keyword [C#]
ms.assetid: dd543335-ae37-48ac-9560-bd5f047b9aea
caps.latest.revision: 30
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
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: ae869fa04d2dfb963694f258624c5cd594ff1184
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
 # <a name="when-c-reference"></a>when (Referência de C#)

Você pode usar a palavra-chave contextual `when` para especificar uma condição de filtro em dois contextos:

- Na instrução `catch` de um bloco [try/catch](try-catch.md) ou [try/catch/finally](try-catch-finally.md).
- No rótulo `case` de uma instrução [switch](switch.md).

## <a name="when-in-a-catch-statement"></a>`when` em uma instrução `catch`

Começando com o C# 6, `When` pode ser usado em uma instrução `catch` para especificar uma condição que deve ser verdadeira para o manipulador para uma exceção específica a ser executada. A sintaxe é:

```csharp
catch ExceptionType [e] when (expr)
```
em que *expr* é uma expressão que é avaliada como um valor booliano. Se ele retornar `true`, o manipulador de exceção será executado, se `false`, não executará. 

O exemplo a seguir usa a palavra-chave `when` para executar os manipuladores condicionalmente para um @System.Net.HttpRequestException dependendo do texto da mensagem de exceção.

 [!code-cs[when-with-catch](../../../../samples/snippets/csharp/language-reference/keywords/when/catch.cs)]  
  
## <a name="when-in-a-switch-statement"></a>`when` em uma instrução `switch`

Iniciando com 7, os rótulos `case` não precisam mais ser mutuamente exclusivos e a ordem na qual os rótulos `case` são exibidos em uma instrução `switch` pode determinar qual bloco switch é executado. A palavra-chave `when` pode ser usada para especificar uma condição de filtro que faz com que seu rótulo case associado seja verdadeiro somente se a condição de filtro também for verdadeira. A sintaxe é:

```csharp
case (expr) where (when-condition):
```
em que *expr* é um padrão de constante ou padrão de tipo que é comparado com a expressão de correspondência e *when-condition* é qualquer expressão booliana. 

O exemplo a seguir usa a palavra-chave `when` para testar os objetos `Shape` que têm uma área de zero, bem como para testar uma variedade de objetos `Shape` que têm uma área maior que zero. 

 [!code-cs[when-with-case#1](../../../../samples/snippets/csharp/language-reference/keywords/when/when.cs#1)]  

## <a name="see-also"></a>Consulte também 
  [instrução switch](switch.md)  
  [instruções try/catch](try-catch.md)  
  [instrução try/catch/finally](try-catch-finally.md) 


