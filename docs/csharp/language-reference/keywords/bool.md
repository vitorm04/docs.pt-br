---
title: "bool (Referência de C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- bool_CSharpKeyword
- bool
dev_langs:
- CSharp
helpviewer_keywords:
- bool keyword [C#]
ms.assetid: 551cfe35-2632-4343-af49-33ad12da08e2
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
ms.translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: ef8cc9a0584829eeed06e7fc3c2227f0683ef413
ms.contentlocale: pt-br
ms.lasthandoff: 03/13/2017

---
# <a name="bool-c-reference"></a>bool (Referência de C#)
A palavra-chave `bool` é um alias de <xref:System.Boolean?displayProperty=fullName>. Ela é usada para declarar variáveis para armazenar os valores boolianos [true](../../../csharp/language-reference/keywords/true.md) e [false](../../../csharp/language-reference/keywords/false.md).  
  
> [!NOTE]
>  Se você precisar de uma variável booliana que também pode ter um valor de `null`, use `bool?`. Para obter mais informações, consulte [Nullable Types (Tipos que permitem valores nulos)](../../../csharp/programming-guide/nullable-types/index.md).  
  
## <a name="literals"></a>Literais  
 Você pode atribuir um valor booliano a uma variável `bool`. Você também pode atribuir uma expressão que é calculada como `bool` para um variável `bool`.  
  
 [!code-cs[csrefKeywordsTypes#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/bool_1.cs)]  
  
 O valor padrão de uma variável `bool` é `false`. O valor padrão de uma variável `bool?` é `null`.  
  
## <a name="conversions"></a>Conversões  
 No C++, um valor do tipo `bool` pode ser convertido em um valor do tipo `int`. Em outras palavras, `false` é equivalente a zero e `true` é equivalente a valores diferentes de zero. No C#, não há conversão entre o tipo `bool` e outros tipos. Por exemplo, a seguinte instrução `if` é inválida no C#:  
  
 [!code-cs[csrefKeywordsTypes#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/bool_2.cs)]  
  
 Para testar uma variável do tipo `int`, você precisa compará-la explicitamente com um valor, como zero, da seguinte maneira:  
  
 [!code-cs[csrefKeywordsTypes#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/bool_3.cs)]  
  
## <a name="example"></a>Exemplo  
 Neste exemplo, você insere um caractere do teclado e o programa verifica se o caractere de entrada é uma letra. Se for uma letra, ele verificará se é maiúscula ou minúscula. Essas verificações são executadas com os métodos <xref:System.Char.IsLetter%2A> e <xref:System.Char.IsLower%2A>, os quais retornam o tipo `bool`:  
  
 [!code-cs[csrefKeywordsTypes#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/bool_4.cs)]  
  
## <a name="c-language-specification"></a>Especificação da Linguagem C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Referência de C#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Palavras-chave de C#](../../../csharp/language-reference/keywords/index.md)   
 [Tabela de Tipos Integrais](../../../csharp/language-reference/keywords/integral-types-table.md)   
 [Tabela de Tipos Internos](../../../csharp/language-reference/keywords/built-in-types-table.md)   
 [Tabela de conversões numéricas implícitas](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)   
 [Tabela de conversões numéricas explícitas](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
