---
title: Tipo de dados SByte (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.sbyte
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
- SByte data type
ms.assetid: 5c38374a-18a1-4cc2-b493-299e3dcaa60f
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
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
ms.openlocfilehash: 33c17cb85cbee758002f19bce8b868e507a2bf24
ms.lasthandoff: 03/13/2017

---
# <a name="sbyte-data-type-visual-basic"></a>Tipo de dados SByte (Visual Basic)
Armazena inteiros de 8 bits (1 byte) que variam em valor de -128 a 127.  
  
## <a name="remarks"></a>Comentários  
 Use o `SByte` tipo de dados para conter valores inteiros que não requerem a largura total de dados de `Integer` ou até mesmo a metade dos bits de `Short`. Em alguns casos, o common language runtime pode ser possível empacotar sua `SByte` variáveis próximas uma da outra e economizar memória.  
  
 O valor padrão de `SByte` é 0.  
  
## <a name="programming-tips"></a>Dicas de programação  
  
-   **Compatibilidade com CLS.** O `SByte` o tipo de dados não é parte do [independência da linguagem e componentes independentes de linguagem](https://msdn.microsoft.com/library/12a7a7h3) (CLS), então um código compatível com CLS não pode consumir um componente que o utilize.  
  
-   **Ampliação.** The `SByte` data type widens to `Short`, `Integer`, `Long`, `Decimal`, `Single`, and `Double`. Isso significa que você pode converter `SByte` para qualquer um desses tipos sem a ocorrência de um <xref:System.OverflowException?displayProperty=fullName>erro.</xref:System.OverflowException?displayProperty=fullName>  
  
-   **Caracteres de tipo.** `SByte`não possui caractere de tipo literal ou caractere de tipo identificador.  
  
-   **Tipo de estrutura.** O tipo correspondente no .NET Framework é o <xref:System.SByte?displayProperty=fullName>estrutura.</xref:System.SByte?displayProperty=fullName>  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.SByte?displayProperty=fullName></xref:System.SByte?displayProperty=fullName>   
 [Tipos de dados](../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Funções de conversão de tipo](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [Resumo da conversão](../../../visual-basic/language-reference/keywords/conversion-summary.md)   
 [Tipo de dados Short](../../../visual-basic/language-reference/data-types/short-data-type.md)   
 [Tipo de dados inteiro](../../../visual-basic/language-reference/data-types/integer-data-type.md)   
 [Tipo de dados Long](../../../visual-basic/language-reference/data-types/long-data-type.md)   
 [Uso Eficiente de Tipos de Dados](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
