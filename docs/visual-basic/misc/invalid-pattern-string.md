---
title: "Cadeia de caracteres de padrão inválido | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
ms.assetid: ec1aecdb-5339-4a93-be71-eec56b1d7438
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: ad95a23a19ed4e8b40664a27f0bb41cdbf786ddd
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="invalid-pattern-string"></a><span data-ttu-id="2b350-102">Cadeia de caracteres de padrão inválido</span><span class="sxs-lookup"><span data-stu-id="2b350-102">Invalid pattern string</span></span>
<span data-ttu-id="2b350-103">A cadeia de caracteres padrão especificada no `Like` operação de uma pesquisa é inválida.</span><span class="sxs-lookup"><span data-stu-id="2b350-103">The pattern string specified in the `Like` operation of a search is invalid.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="2b350-104">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="2b350-104">To correct this error</span></span>  
  
1.  <span data-ttu-id="2b350-105">Examine os caracteres válidos para expressões da lista.</span><span class="sxs-lookup"><span data-stu-id="2b350-105">Review the valid characters for list expressions.</span></span>  
  
2.  <span data-ttu-id="2b350-106">O intervalo padrão, certifique-se de que o caractere de intervalo de início é menor que o caractere de intervalo de término, como em `[a-z]`.</span><span class="sxs-lookup"><span data-stu-id="2b350-106">In the pattern range, ensure that the start range character is less than the end range character, as in `[a-z]`.</span></span>  
  
3.  <span data-ttu-id="2b350-107">O intervalo padrão, certifique-se de que não haja vários hifens próximos uns dos outros, como em `[a--z]`.</span><span class="sxs-lookup"><span data-stu-id="2b350-107">In the pattern range, ensure that there are not multiple hyphens next to each other, as in `[a--z]`.</span></span>  
  
4.  <span data-ttu-id="2b350-108">Finalizar intervalos padrão com um colchete de fechamento.</span><span class="sxs-lookup"><span data-stu-id="2b350-108">End pattern ranges with a closing bracket.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b350-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2b350-109">See Also</span></span>  
 [<span data-ttu-id="2b350-110">Operador Like</span><span class="sxs-lookup"><span data-stu-id="2b350-110">Like Operator</span></span>](../../visual-basic/language-reference/operators/like-operator.md)
