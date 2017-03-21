---
title: "Não há suporte para inferência de tipo anulável neste contexto | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc36629
- bc36629
dev_langs:
- VB
helpviewer_keywords:
- BC36629
ms.assetid: 0a1e2dbc-d9a4-433d-9306-c5540782b81d
caps.latest.revision: 5
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
ms.openlocfilehash: aaea05a7397a3805f6aadf1cd6f9dc0005b9af98
ms.lasthandoff: 03/13/2017

---
# <a name="nullable-type-inference-is-not-supported-in-this-context"></a>Inferência de tipo que permite valor nulo não suportada neste contexto
Tipos de valor e estruturas podem ser declaradas anuláveis.  
  
```vb  
Dim a? As Integer  
Dim b As Integer?  
```  
  
 No entanto, você não pode usar a declaração anulável em combinação com a inferência de tipos. Os exemplos a seguir causam esse erro.  
  
```vb  
' Not valid.  
' Dim c? = 10  
' Dim d? = a  
```  
  
 **ID do erro:** BC36629  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Use um `As` cláusula para declarar a variável como anulável.  
  
## <a name="see-also"></a>Consulte também  
 [Tipos de valor anulável](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)   
 [Inferência de Tipo de Variável Local](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
