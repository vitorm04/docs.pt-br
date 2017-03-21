---
title: "Matriz declarada como variável de controle de loop não pode ser declarada com um tamanho inicial | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc32039
- bc32039
dev_langs:
- VB
helpviewer_keywords:
- BC32039
ms.assetid: 1d8b6560-c9eb-4b71-a038-24c6f5a5ce46
caps.latest.revision: 13
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
ms.openlocfilehash: b72c08b8c925c85136e1f6fc0f23f08e2b0723c5
ms.lasthandoff: 03/13/2017

---
# <a name="array-declared-as-for-loop-control-variable-cannot-be-declared-with-an-initial-size"></a>A matriz declarada para a variável de controle do loop não pode ser declarada com um tamanho inicial
A `For Each` usa uma matriz como seu *elemento* variável de iteração mas inicializa essa matriz.  
  
 As instruções a seguir mostram como esse erro pode ser gerado.  
  
```  
Dim arrayList As New List(Of Integer())  
For Each listElement() As Integer In arrayList  
For Each listElement(1) As Integer In arrayList  
```  
  
 A primeira `For Each` instrução é a maneira correta de acessar elementos de `arrayList`. O segundo `For Each` instrução gera esse erro.  
  
 **ID do erro:** BC32039  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Remova a inicialização da declaração do *elemento* variável de iteração.  
  
## <a name="see-also"></a>Consulte também  
 [Para... Próxima instrução](../../../visual-basic/language-reference/statements/for-next-statement.md)   
 [Matrizes](../../../visual-basic/programming-guide/language-features/arrays/index.md)   
 [Coleções](http://msdn.microsoft.com/library/e76533a9-5033-4a0b-b003-9c2be60d185b)
