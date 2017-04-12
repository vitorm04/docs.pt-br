---
title: "Estouro (erro de tempo de execução do Visual Basic) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrERRID_Overflow
dev_langs:
- VB
ms.assetid: c6a23279-3086-412a-bcff-ff8ed2cb8c6f
caps.latest.revision: 8
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
ms.openlocfilehash: 34ae8915ba665550b3fb83788cdab8d8accef56a
ms.lasthandoff: 03/13/2017

---
# <a name="overflow-visual-basic-run-time-error"></a>Estouro (erro de tempo de execução do Visual Basic)
Um estouro ocorre quando você tentar uma atribuição que excede os limites do destino da atribuição.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Certifique-se de que os resultados do tipo de dados, cálculos e atribuições de conversões não são muito grande para ser representado dentro do intervalo permitido para esse tipo de valor de variáveis e atribuir o valor a uma variável de um tipo que podem conter um intervalo maior de valores, se necessário.  
  
2.  Certifique-se de atribuições de propriedades se encaixam no intervalo da propriedade à qual são feitas.  
  
3.  Certifique-se de que números usados nos cálculos de imposto em inteiros não têm resultados maiores inteiros.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Int32.MaxValue?displayProperty=fullName></xref:System.Int32.MaxValue?displayProperty=fullName>   
 <xref:System.Double.MaxValue?displayProperty=fullName></xref:System.Double.MaxValue?displayProperty=fullName>   
 [Tipos de dados](../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Tipos de Erro](../../../visual-basic/programming-guide/language-features/error-types.md)
