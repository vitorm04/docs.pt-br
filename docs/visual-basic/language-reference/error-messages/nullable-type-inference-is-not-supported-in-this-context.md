---
title: Inferência de tipo que permite valor nulo não suportada neste contexto
ms.date: 07/20/2015
f1_keywords:
- vbc36629
- bc36629
helpviewer_keywords:
- BC36629
ms.assetid: 0a1e2dbc-d9a4-433d-9306-c5540782b81d
ms.openlocfilehash: ea531c7be676e940a263b019a66cc80cf280a772
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
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
