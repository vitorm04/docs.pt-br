---
title: Inferência de tipo que permite valor nulo não suportada neste contexto
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc36629
- bc36629
helpviewer_keywords:
- BC36629
ms.assetid: 0a1e2dbc-d9a4-433d-9306-c5540782b81d
caps.latest.revision: 5
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e7a5450d812260d3916296dff56abee27b3d586c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="nullable-type-inference-is-not-supported-in-this-context"></a>Inferência de tipo que permite valor nulo não suportada neste contexto
Estruturas e tipos de valor podem ser declaradas anuláveis.  
  
```vb  
Dim a? As Integer  
Dim b As Integer?  
```  
  
 No entanto, você não pode usar a declaração anulável em combinação com a inferência de tipo. Os exemplos a seguir causam esse erro.  
  
```vb  
' Not valid.  
' Dim c? = 10  
' Dim d? = a  
```  
  
 **ID do erro:** BC36629  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Use um `As` cláusula para declarar a variável como anulável.  
  
## <a name="see-also"></a>Consulte também  
 [Tipos de Valor Anulável](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)  
 [Inferência de Tipo de Variável Local](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
