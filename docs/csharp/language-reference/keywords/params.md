---
title: "params (Referência de C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- params_CSharpKeyword
- params
dev_langs:
- CSharp
helpviewer_keywords:
- parameters [C#], params
- params keyword [C#]
ms.assetid: 1690815e-b52b-4967-8380-5780aff08012
caps.latest.revision: 24
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 16e65f6087592239cbd5df10a56201a5240cf299
ms.contentlocale: pt-br
ms.lasthandoff: 03/13/2017

---
# <a name="params-c-reference"></a>params (Referência de C#)
Usando a palavra-chave `params`, você pode especificar um [parâmetro do método](../../../csharp/language-reference/keywords/method-parameters.md) que aceita um número variável de argumentos.  
  
 Você pode enviar uma lista separada por vírgulas dos argumentos do tipo especificado na declaração de parâmetros ou uma matriz de argumentos do tipo especificado. Você também pode não enviar nenhum argumento. Se você não enviar nenhum argumento, o comprimento da lista `params` será zero.  
  
 Nenhum parâmetro adicional é permitido após a palavra-chave `params` em uma declaração de método e apenas uma palavra-chave `params` é permitida em uma declaração de método.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra várias maneiras em que os argumentos podem ser enviados para um parâmetro `params`.  
  
 [!code-cs[csrefKeywordsMethodParams#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/params_1.cs)]  
  
## <a name="c-language-specification"></a>Especificação da Linguagem C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Referência de C#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Palavras-chave de C#](../../../csharp/language-reference/keywords/index.md)   
 [Parâmetros de método](../../../csharp/language-reference/keywords/method-parameters.md)
