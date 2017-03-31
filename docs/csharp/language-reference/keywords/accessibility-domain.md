---
title: "Domínio de acessibilidade (Referência de C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- accessibility domain [C#]
ms.assetid: 8af779c1-275b-44be-a864-9edfbca71bcc
caps.latest.revision: 17
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
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: c7f575aa65680ccc886ac0246c589a8cac1302d7
ms.lasthandoff: 03/13/2017

---
# <a name="accessibility-domain-c-reference"></a>Domínio de acessibilidade (Referência de C#)
O domínio de acessibilidade de um membro especifica em que seções do programa um membro pode ser referenciado. Se o membro estiver aninhado dentro de outro tipo, seu domínio de acessibilidade será determinado pelo [nível de acessibilidade](../../../csharp/language-reference/keywords/accessibility-levels.md) do membro e pelo domínio de acessibilidade do tipo imediatamente contido.  
  
 O domínio de acessibilidade de um tipo de nível superior é, pelo menos, o texto do programa do projeto no qual ele é declarado. Isto é, o domínio inclui todos os arquivos de origem deste projeto. O domínio de acessibilidade de um tipo aninhado é, pelo menos, o texto do programa do tipo no qual ele é declarado. Isto é, o domínio é o corpo do tipo, que inclui todos os tipos aninhados. O domínio de acessibilidade de um tipo aninhado nunca excede o do tipo contido. Esses conceitos são demonstrados no exemplo a seguir.  
  
## <a name="example"></a>Exemplo  
 Este exemplo contém um tipo de nível superior, `T1` e duas classes aninhadas, `M1` e `M2`. As classes contêm campos que têm diferentes acessibilidades declaradas. No método `Main`, um comentário segue cada instrução para indicar o domínio de acessibilidade de cada membro. Observe que as instruções que tentam fazer referência aos membros inacessíveis são tornadas inertes ao serem transformadas em comentários. Se você quiser ver os erros de compilador causados ao referenciar um membro inacessível, remova os comentários um por vez.  
  
 [!code-cs[csrefKeywordsModifiers#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/accessibility-domain_1.cs)]  
  
## <a name="c-language-specification"></a>Especificação da Linguagem C#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Referência de C#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Palavras-chave de C#](../../../csharp/language-reference/keywords/index.md)   
 [Modificadores de acesso](../../../csharp/language-reference/keywords/access-modifiers.md)   
 [Níveis de Acessibilidade](../../../csharp/language-reference/keywords/accessibility-levels.md)   
 [Restrições ao uso de níveis de acessibilidade](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md)   
 [Modificadores de acesso](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)   
 [public](../../../csharp/language-reference/keywords/public.md)   
 [private](../../../csharp/language-reference/keywords/private.md)   
 [protected](../../../csharp/language-reference/keywords/protected.md)   
 [internal](../../../csharp/language-reference/keywords/internal.md)
