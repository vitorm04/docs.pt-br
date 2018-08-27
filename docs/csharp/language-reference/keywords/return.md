---
title: return (Referência de C#)
ms.date: 07/20/2015
f1_keywords:
- return_CSharpKeyword
- return
helpviewer_keywords:
- return statement [C#]
- return keyword [C#]
ms.assetid: 6da6e152-5b58-4448-8f3f-470dd0617ecd
ms.openlocfilehash: 1b6a1ce2a8587c8630fece3d5c9a2186fbbc9c22
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2018
ms.locfileid: "43001470"
---
# <a name="return-c-reference"></a>return (Referência de C#)
A instrução `return` finaliza a execução do método em que aparece e retorna o controle para o método de chamada. Ela também pode retornar um valor opcional. Se o método for um tipo `void`, a instrução `return` poderá ser omitida.  
  
 Se a instrução return estiver dentro de um bloco `try`, o bloco `finally`, se houver, será executado antes que o controle retorne para o método de chamada.  
  
## <a name="example"></a>Exemplo  
 No exemplo a seguir, o método `CalculateArea()` retorna a variável `area` local como um valor [double](../../../csharp/language-reference/keywords/double.md).  
  
 [!code-csharp[csrefKeywordsJump#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/return_1.cs)]  
  
## <a name="c-language-specification"></a>Especificação da Linguagem C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Referência de C#](../../../csharp/language-reference/index.md)  
- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
- [Palavras-chave do C#](../../../csharp/language-reference/keywords/index.md)  
- [Instrução return](/cpp/cpp/return-statement-cpp)  
- [Instruções de atalho](../../../csharp/language-reference/keywords/jump-statements.md)
