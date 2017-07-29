---
title: "goto (Referência de C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- goto_CSharpKeyword
- goto
dev_langs:
- CSharp
helpviewer_keywords:
- goto keyword [C#]
ms.assetid: 2c03c9c1-8119-44ef-b740-fb3d287a42fe
caps.latest.revision: 22
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
ms.openlocfilehash: cd298809ab883f425f3bb88239f2951ab98cc03e
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="goto-c-reference"></a>goto (Referência de C#)
A declaração `goto` transfere o controle do programa diretamente para uma instrução rotulada.  
  
 Um uso comum de `goto` é a transferência do controle para um rótulo de caso de opção específico ou para o rótulo padrão em uma instrução `switch`.  
  
 A instrução `goto` também é útil para sair de loops profundamente aninhados.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra o uso de `goto` em uma instrução [switch](../../../csharp/language-reference/keywords/switch.md).  
  
 [!code-cs[csrefKeywordsJump#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/goto_1.cs)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra o uso de `goto` para sair de loops aninhados.  
  
 [!code-cs[csrefKeywordsJump#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/goto_2.cs)]  
  
## <a name="c-language-specification"></a>Especificação da Linguagem C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Referência de C#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Palavras-chave de C#](../../../csharp/language-reference/keywords/index.md)   
 [Instrução goto](/cpp/cpp/goto-statement-cpp)   
 [Instruções de atalho](../../../csharp/language-reference/keywords/jump-statements.md)

