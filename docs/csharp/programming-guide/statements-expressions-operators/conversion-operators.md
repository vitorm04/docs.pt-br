---
title: Operadores de conversão – Guia de Programação em C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, conversion operators
- conversion operators [C#]
- operators [C#], conversion
- user-defined conversions [C#]
ms.assetid: c5ad73a3-d57b-4d2b-b4c9-24e3c2856efc
ms.openlocfilehash: 539a554da2ea2f785a54bd7e5ff81d09b908c9e4
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56965209"
---
# <a name="conversion-operators-c-programming-guide"></a>Operadores de conversão (Guia de Programação em C#)

O C# habilita os programadores a declarar conversões em classes ou structs, para que tais classes ou structs possam ser convertidas para e/ou de outras classes ou structs ou tipos básicos. As conversões são definidas como operadores e nomeadas para o tipo para o qual são convertidas. O tipo do argumento a ser convertido ou o tipo do resultado da conversão, mas não ambos, deve ser o tipo recipiente.  
  
 [!code-csharp[csProgGuideStatements#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#10)]  
  
## <a name="conversion-operators-overview"></a>Visão geral dos operadores de conversão

 Os operadores de conversão têm as seguintes propriedades:  
  
-   Conversões declaradas como `implicit` ocorrem automaticamente quando for necessário.  
  
-   Conversões declaradas como `explicit` exigem que uma conversão seja chamada.  
  
-   Todas as conversões devem ser declaradas como `static`.  
  
## <a name="related-sections"></a>Seções relacionadas

 Para saber mais:  
  
-   [Usando operadores de conversão](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md)  
  
-   [Transmissões e conversões de tipo](../../../csharp/programming-guide/types/casting-and-type-conversions.md)  
  
-   [Como: implementar conversões definidas pelo usuário entre structs](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)  
  
-   [explicit](../../../csharp/language-reference/keywords/explicit.md)  
  
-   [implicit](../../../csharp/language-reference/keywords/implicit.md)  
  
-   [static](../../../csharp/language-reference/keywords/static.md)  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Convert>
- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)
- [Conversões explícitas encadeadas definidas pelo usuário em C#](https://blogs.msdn.microsoft.com/ericlippert/2007/04/16/chained-user-defined-explicit-conversions-in-c/)
