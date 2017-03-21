---
title: Curta o tipo de dados (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Short
dev_langs:
- VB
helpviewer_keywords:
- numbers, whole
- whole numbers
- integral data types
- integer numbers
- numbers, integer
- integers, data types
- integers, types
- data types [Visual Basic], integral
- S literal type character
- Short data type
- literal type characters, S
ms.assetid: 65fcbcf3-a841-400e-885e-301497729a8b
caps.latest.revision: 18
author: stevehoag
ms.author: shoag
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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: e2bc79897b337cbab7f8de97741f2d6a32668fc7
ms.lasthandoff: 03/13/2017

---
# <a name="short-data-type-visual-basic"></a>Tipo de dados curto (Visual Basic)
Armazena inteiros de 16 bits (2 bytes) que variam de -32.768 a 32.767.  
  
## <a name="remarks"></a>Comentários  
 Use o `Short` tipo de dados para conter valores inteiros que não requerem a largura total de dados de `Integer`. Em alguns casos, o common language runtime pode empacotar seu `Short` variáveis próximas uma da outra e economizar memória.  
  
 O valor padrão de `Short` é 0.  
  
## <a name="programming-tips"></a>Dicas de programação  
  
-   **Ampliação.** The `Short` data type widens to `Integer`, `Long`, `Decimal`, `Single`, or `Double`. Isso significa que você pode converter `Short` para qualquer um desses tipos sem a ocorrência de um <xref:System.OverflowException?displayProperty=fullName>erro.</xref:System.OverflowException?displayProperty=fullName>  
  
-   **Caracteres de tipo.** Acrescentar o caractere de tipo literal `S` a um literal o força ao tipo de dados `Short`. `Short`não tem nenhum caractere de tipo identificador.  
  
-   **Tipo de estrutura.** O tipo correspondente no .NET Framework é o <xref:System.Int16?displayProperty=fullName>estrutura.</xref:System.Int16?displayProperty=fullName>  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Int16?displayProperty=fullName></xref:System.Int16?displayProperty=fullName>   
 [Tipos de dados](../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Funções de conversão de tipo](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [Resumo da conversão](../../../visual-basic/language-reference/keywords/conversion-summary.md)   
 [Tipo de dados inteiro](../../../visual-basic/language-reference/data-types/integer-data-type.md)   
 [Tipo de dados Long](../../../visual-basic/language-reference/data-types/long-data-type.md)   
 [Uso Eficiente de Tipos de Dados](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
