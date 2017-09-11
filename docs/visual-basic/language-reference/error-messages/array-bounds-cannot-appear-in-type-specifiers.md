---
title: "Limites de matriz não podem aparecer em especificadores de tipo | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30638
- bc30638
dev_langs:
- VB
helpviewer_keywords:
- BC30638
ms.assetid: 93b654f4-70fa-4a48-baed-ffae42075550
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 81c7c6d2bbeeabb69233d4898cceb5feae66ceec
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="array-bounds-cannot-appear-in-type-specifiers"></a><span data-ttu-id="e38c9-102">Os limites de matriz não podem ser exibidos em especificadores de tipo</span><span class="sxs-lookup"><span data-stu-id="e38c9-102">Array bounds cannot appear in type specifiers</span></span>
<span data-ttu-id="e38c9-103">Tamanhos de matriz não podem ser declarados como parte de um especificador de tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="e38c9-103">Array sizes cannot be declared as part of a data type specifier.</span></span>  
  
 <span data-ttu-id="e38c9-104">**ID do erro:** BC30638</span><span class="sxs-lookup"><span data-stu-id="e38c9-104">**Error ID:** BC30638</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e38c9-105">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="e38c9-105">To correct this error</span></span>  
  
-   <span data-ttu-id="e38c9-106">Especifique o tamanho da matriz imediatamente após o nome da variável em vez de colocar o tamanho da matriz após o tipo, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="e38c9-106">Specify the size of the array immediately following the variable name instead of placing the array size after the type, as shown in the following example.</span></span>  
  
    ```  
    Dim Array(8) As Integer   
    ```  
  
-   <span data-ttu-id="e38c9-107">Definir uma matriz e inicialize-o com o número desejado de elementos, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="e38c9-107">Define an array and initialize it with the desired number of elements, as shown in the following example.</span></span>  
  
    ```  
    Dim Array2() As Integer = New Integer(8) {}  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="e38c9-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e38c9-108">See Also</span></span>  
 [<span data-ttu-id="e38c9-109">Matrizes</span><span class="sxs-lookup"><span data-stu-id="e38c9-109">Arrays</span></span>](../../../visual-basic/programming-guide/language-features/arrays/index.md)
