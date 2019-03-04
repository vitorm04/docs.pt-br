---
title: Parâmetros de tipo genérico – Guia de Programação em C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], type parameters
- type parameters [C#]
ms.assetid: a03b0ab2-0606-4b41-b7bf-e64d5bb4d18f
ms.openlocfilehash: f6acbfee5c6b5ec426076d7bf766a3c6894b736f
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56972177"
---
# <a name="generic-type-parameters-c-programming-guide"></a>Parâmetros de tipo genérico (Guia de Programação em C#)
Na definição de um tipo genérico ou método, parâmetros de tipo são um espaço reservado para um tipo específico que o um cliente especifica ao instanciar uma variável do tipo genérico. Uma classe genérica, como `GenericList<T>`, listada em [Introdução aos Genéricos](../../../csharp/programming-guide/generics/introduction-to-generics.md), não pode ser usada no estado em que se encontra porque não é realmente um tipo, mas um plano gráfico de um tipo. Para usar `GenericList<T>`, o código cliente deve declarar e instanciar um tipo construído, especificando um argumento de tipo entre colchetes. O argumento de tipo para essa classe específica pode ser qualquer tipo reconhecido pelo compilador. É possível criar qualquer quantidade de instâncias do tipo construído, cada uma usando um argumento de tipo diferente, da seguinte maneira:  
  
 [!code-csharp[csProgGuideGenerics#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#7)]  
  
 Em cada uma dessas instâncias de `GenericList<T>`, todas as ocorrências de `T` na classe serão substituídas em tempo de execução com o argumento de tipo. Por meio dessa substituição, cria-se três objetos separados eficientes e fortemente tipados usando uma única definição de classe. Para obter mais informações sobre como essa substituição é executada pelo CLR, consulte [Genéricos em Tempo de Execução](../../../csharp/programming-guide/generics/generics-in-the-run-time.md).  
  
## <a name="type-parameter-naming-guidelines"></a>Diretrizes para a Nomenclatura de Parâmetros de Tipo  
  
-   **Nomeie** parâmetros de tipo genérico com nomes descritivos, a menos que um nome com uma única letra seja autoexplicativo e um nome descritivo não agregue valor.  
  
     [!code-csharp[csProgGuideGenerics#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#8)]  
  
-   **Considere** usar T como o nome do parâmetro de tipo em tipos com parâmetro de tipo de uma letra.  
  
     [!code-csharp[csProgGuideGenerics#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#9)]  
  
-   **Insira** o prefixo “T” em nomes descritivos de parâmetro de tipo.  
  
     [!code-csharp[csProgGuideGenerics#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#10)]  
  
-   **Considere** indicar as restrições colocadas em um parâmetro de tipo no nome do parâmetro. Por exemplo, um parâmetro restrito a `ISession` pode ser chamado `TSession`.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Collections.Generic>
- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)
- [Genéricos](../../../csharp/programming-guide/generics/index.md)
- [Diferenças entre modelos C++ e genéricos C#](../../../csharp/programming-guide/generics/differences-between-cpp-templates-and-csharp-generics.md)
