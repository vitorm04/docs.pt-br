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
ms.openlocfilehash: ef36f14d5323a4592afe59573e249d8cfb218df9
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/21/2017
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
 [Coleções](../../../standard/collections/index.md)
