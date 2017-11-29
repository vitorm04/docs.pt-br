---
title: "A matriz declarada para a variável de controle do loop não pode ser declarada com um tamanho inicial"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc32039
- bc32039
helpviewer_keywords: BC32039
ms.assetid: 1d8b6560-c9eb-4b71-a038-24c6f5a5ce46
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0635e1b18b24a241fabad6d67da34f8dde9530db
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="array-declared-as-for-loop-control-variable-cannot-be-declared-with-an-initial-size"></a>A matriz declarada para a variável de controle do loop não pode ser declarada com um tamanho inicial
Um `For Each` loop usa uma matriz como sua *elemento* variável de iteração mas inicializa essa matriz.  
  
 As instruções a seguir mostram como esse erro pode ser gerado.  
  
```  
Dim arrayList As New List(Of Integer())  
For Each listElement() As Integer In arrayList  
For Each listElement(1) As Integer In arrayList  
```  
  
 A primeira `For Each` instrução é a maneira correta de acessar elementos de `arrayList`. O segundo `For Each` instrução gera este erro.  
  
 **ID do erro:** BC32039  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Remova a inicialização da declaração de *elemento* variável de iteração.  
  
## <a name="see-also"></a>Consulte também  
 [Instrução For...Next](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [Matrizes](../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [Coleções](http://msdn.microsoft.com/library/e76533a9-5033-4a0b-b003-9c2be60d185b)
