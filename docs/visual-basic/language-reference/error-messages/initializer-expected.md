---
title: Inicializador esperado
ms.date: 07/20/2015
f1_keywords:
- vbc30996
- bc30996
helpviewer_keywords:
- BC30996
ms.assetid: 6e183fe0-8888-43ed-a062-01571079455f
ms.openlocfilehash: 0795fdc1c4b177e13979d7555cd7588217b8cb4c
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59334959"
---
# <a name="initializer-expected"></a>Inicializador esperado
Você tentou declarar uma instância de uma classe usando um inicializador de objeto no qual a lista de inicialização está vazia, conforme mostrado no exemplo a seguir.  
  
 `' Not valid.`  
  
 `' Dim aStudent As New Student With {}`  
  
 Pelo menos um campo ou propriedade deve ser inicializada na lista de inicializadores, conforme mostrado no exemplo a seguir.  
  
 `Dim aStudent As New Student With {.year = "Senior"}`  
  
 **ID do erro:** BC30996  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1. Inicializar pelo menos um campo ou propriedade no inicializador, ou não usar um inicializador de objeto.  
  
## <a name="see-also"></a>Consulte também

- [Inicializadores de objeto: Tipos nomeados e anônimos](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [Como: declarar um objeto usando um inicializador de objeto](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)
