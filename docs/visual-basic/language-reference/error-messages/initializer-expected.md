---
title: Inicializador esperado
ms.date: 07/20/2015
f1_keywords:
- vbc30996
- bc30996
helpviewer_keywords:
- BC30996
ms.assetid: 6e183fe0-8888-43ed-a062-01571079455f
ms.openlocfilehash: 2c5a65443dc16a600e25fcf6dfd11c4597b3a086
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873949"
---
# <a name="initializer-expected"></a>Inicializador esperado

Você tentou declarar uma instância de uma classe usando um inicializador de objeto no qual a lista de inicialização está vazia, conforme mostrado no exemplo a seguir.  
  
 `' Not valid.`  
  
 `' Dim aStudent As New Student With {}`  
  
 Pelo menos um campo ou propriedade deve ser inicializado na lista de inicializadores, conforme mostrado no exemplo a seguir.  
  
 `Dim aStudent As New Student With {.year = "Senior"}`  
  
 **ID do erro:** BC30996  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1. Inicialize pelo menos um campo ou propriedade no inicializador ou não use um inicializador de objeto.  
  
## <a name="see-also"></a>Confira também

- [Inicializadores de objeto: tipos nomeados e anônimos](../../programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [Como declarar um objeto usando um inicializador de objeto](../../programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)
