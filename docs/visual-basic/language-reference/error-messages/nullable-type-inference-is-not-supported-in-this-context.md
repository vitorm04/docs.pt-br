---
title: Inferência de tipo que permite valor nulo não suportada neste contexto
ms.date: 07/20/2015
f1_keywords:
- vbc36629
- bc36629
helpviewer_keywords:
- BC36629
ms.assetid: 0a1e2dbc-d9a4-433d-9306-c5540782b81d
ms.openlocfilehash: 42bde0b1843e52bbc16118bb056ade791591904e
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249494"
---
# <a name="nullable-type-inference-is-not-supported-in-this-context"></a>Inferência de tipo que permite valor nulo não suportada neste contexto
Tipos e estruturas de valor podem ser declaradas anuladas.  
  
```vb  
Dim a? As Integer  
Dim b As Integer?  
```  
  
 No entanto, você não pode usar a declaração anulada em combinação com a inferência do tipo. Os exemplos a seguir causam esse erro.  
  
```vb  
' Not valid.  
' Dim c? = 10  
' Dim d? = a  
```  
  
 **ID de erro:** BC36629  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
- Use `As` uma cláusula para declarar a variável como um tipo de valor anulado.  
  
## <a name="see-also"></a>Confira também

- [Tipos de valor anulados](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [Inferência de Tipo de Variável Local](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
