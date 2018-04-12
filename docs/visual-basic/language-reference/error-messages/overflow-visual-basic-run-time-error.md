---
title: Estouro (erro de tempo de execução do Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrERRID_Overflow
ms.assetid: c6a23279-3086-412a-bcff-ff8ed2cb8c6f
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d1908ad576a499e79102aff23e3e2f11d7d99d52
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="overflow-visual-basic-run-time-error"></a>Estouro (erro de tempo de execução do Visual Basic)
Um estouro ocorre quando você tentar uma atribuição que excede os limites de destino da atribuição.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Certifique-se de que os resultados do tipo de dados, cálculos e atribuições de conversões não são muito grande para ser representado dentro do intervalo permitido para esse tipo de valor de variáveis e atribuir o valor a uma variável de um tipo que podem conter um intervalo maior de valores , se necessário.  
  
2.  Certifique-se de atribuições às propriedades ajustar o intervalo da propriedade ao qual eles são feitos.  
  
3.  Certifique-se de que números usados em cálculos que são forçados em inteiros não tem resultados maiores que inteiros.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Int32.MaxValue?displayProperty=nameWithType>  
 <xref:System.Double.MaxValue?displayProperty=nameWithType>  
 [Tipos de Dados](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [Tipos de Erro](../../../visual-basic/programming-guide/language-features/error-types.md)
