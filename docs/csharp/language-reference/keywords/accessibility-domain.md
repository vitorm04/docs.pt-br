---
title: Domínio de acessibilidade (Referência de C#)
ms.date: 07/20/2015
helpviewer_keywords:
- accessibility domain [C#]
ms.assetid: 8af779c1-275b-44be-a864-9edfbca71bcc
ms.openlocfilehash: 8e6af35ea41f6d062bc2b8ee771a1fac21667462
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36207835"
---
# <a name="accessibility-domain-c-reference"></a>Domínio de acessibilidade (Referência de C#)
O domínio de acessibilidade de um membro especifica em que seções do programa um membro pode ser referenciado. Se o membro estiver aninhado dentro de outro tipo, seu domínio de acessibilidade será determinado pelo [nível de acessibilidade](../../../csharp/language-reference/keywords/accessibility-levels.md) do membro e pelo domínio de acessibilidade do tipo imediatamente contido.  
  
 O domínio de acessibilidade de um tipo de nível superior é, pelo menos, o texto do programa do projeto no qual ele é declarado. Isto é, o domínio inclui todos os arquivos de origem deste projeto. O domínio de acessibilidade de um tipo aninhado é, pelo menos, o texto do programa do tipo no qual ele é declarado. Isto é, o domínio é o corpo do tipo, que inclui todos os tipos aninhados. O domínio de acessibilidade de um tipo aninhado nunca excede o do tipo contido. Esses conceitos são demonstrados no exemplo a seguir.  
  
## <a name="example"></a>Exemplo  
 Este exemplo contém um tipo de nível superior, `T1` e duas classes aninhadas, `M1` e `M2`. As classes contêm campos que têm diferentes acessibilidades declaradas. No método `Main`, um comentário segue cada instrução para indicar o domínio de acessibilidade de cada membro. Observe que as instruções que tentam fazer referência aos membros inacessíveis são tornadas inertes ao serem transformadas em comentários. Se você quiser ver os erros de compilador causados ao referenciar um membro inacessível, remova os comentários um por vez.  
  
[!code-csharp[csrefKeywordsModifiers#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#4)]
  
## <a name="c-language-specification"></a>Especificação da Linguagem C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Referência de C#](../../../csharp/language-reference/index.md)  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
 [Palavras-chave do C#](../../../csharp/language-reference/keywords/index.md)  
 [Modificadores de acesso](../../../csharp/language-reference/keywords/access-modifiers.md)  
 [Níveis de acessibilidade](../../../csharp/language-reference/keywords/accessibility-levels.md)  
 [Restrições ao uso de níveis de acessibilidade](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md)  
 [Modificadores de acesso](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
 [public](../../../csharp/language-reference/keywords/public.md)  
 [private](../../../csharp/language-reference/keywords/private.md)  
 [protected](../../../csharp/language-reference/keywords/protected.md)  
 [internal](../../../csharp/language-reference/keywords/internal.md)
