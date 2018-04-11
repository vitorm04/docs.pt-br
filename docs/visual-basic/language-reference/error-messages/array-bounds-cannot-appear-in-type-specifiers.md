---
title: Os limites de matriz não podem ser exibidos em especificadores de tipo
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30638
- bc30638
helpviewer_keywords:
- BC30638
ms.assetid: 93b654f4-70fa-4a48-baed-ffae42075550
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 770f86ca960110965b6917a22d284678ff8b6f8c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="array-bounds-cannot-appear-in-type-specifiers"></a>Os limites de matriz não podem ser exibidos em especificadores de tipo
Tamanhos de matriz não podem ser declarados como parte de um especificador de tipo de dados.  
  
 **ID do erro:** BC30638  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Especifique o tamanho da matriz imediatamente após o nome da variável em vez de fazer o tamanho da matriz após o tipo, conforme mostrado no exemplo a seguir.  
  
    ```  
    Dim Array(8) As Integer   
    ```  
  
-   Defina uma matriz e inicialize-o com o número desejado de elementos, como mostrado no exemplo a seguir.  
  
    ```  
    Dim Array2() As Integer = New Integer(8) {}  
    ```  
  
## <a name="see-also"></a>Consulte também  
 [Matrizes](../../../visual-basic/programming-guide/language-features/arrays/index.md)
