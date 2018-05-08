---
title: Inicializador esperado
ms.date: 07/20/2015
f1_keywords:
- vbc30996
- bc30996
helpviewer_keywords:
- BC30996
ms.assetid: 6e183fe0-8888-43ed-a062-01571079455f
ms.openlocfilehash: 9d786fd1e929129c420b7bec62efd0bd445d85eb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="initializer-expected"></a>Inicializador esperado
Você tentou declarar uma instância de uma classe usando um inicializador de objeto no qual a lista de inicialização está vazia, conforme mostrado no exemplo a seguir.  
  
 `' Not valid.`  
  
 `' Dim aStudent As New Student With {}`  
  
 Pelo menos um campo ou propriedade deve ser inicializada na lista de inicializador, conforme mostrado no exemplo a seguir.  
  
 `Dim aStudent As New Student With {.year = "Senior"}`  
  
 **ID do erro:** BC30996  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Inicializar pelo menos um campo ou propriedade no inicializador, ou não use um inicializador de objeto.  
  
## <a name="see-also"></a>Consulte também  
 [Inicializadores de objeto: tipos nomeados e anônimos](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)  
 [Como declarar um objeto usando um inicializador de objeto](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)
