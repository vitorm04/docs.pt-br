---
title: Cadeia de caracteres padrão inválida
ms.date: 07/20/2015
ms.assetid: ec1aecdb-5339-4a93-be71-eec56b1d7438
ms.openlocfilehash: 3fa42632ad6d69642d7b8ec36bf2880bc10a5024
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54732473"
---
# <a name="invalid-pattern-string"></a><span data-ttu-id="a161d-102">Cadeia de caracteres padrão inválida</span><span class="sxs-lookup"><span data-stu-id="a161d-102">Invalid pattern string</span></span>
<span data-ttu-id="a161d-103">A cadeia de caracteres padrão especificada no `Like` operação de uma pesquisa é inválida.</span><span class="sxs-lookup"><span data-stu-id="a161d-103">The pattern string specified in the `Like` operation of a search is invalid.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a161d-104">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="a161d-104">To correct this error</span></span>  
  
1.  <span data-ttu-id="a161d-105">Examine os caracteres válidos para expressões da lista.</span><span class="sxs-lookup"><span data-stu-id="a161d-105">Review the valid characters for list expressions.</span></span>  
  
2.  <span data-ttu-id="a161d-106">No intervalo padrão, certifique-se de que o caractere de intervalo de início é menor que o caractere de intervalo de término, como em `[a-z]`.</span><span class="sxs-lookup"><span data-stu-id="a161d-106">In the pattern range, ensure that the start range character is less than the end range character, as in `[a-z]`.</span></span>  
  
3.  <span data-ttu-id="a161d-107">No intervalo padrão, certifique-se de que não haja várias hifens próximos uns dos outros, como em `[a--z]`.</span><span class="sxs-lookup"><span data-stu-id="a161d-107">In the pattern range, ensure that there are not multiple hyphens next to each other, as in `[a--z]`.</span></span>  
  
4.  <span data-ttu-id="a161d-108">Intervalos de padrão de término com um colchete de fechamento.</span><span class="sxs-lookup"><span data-stu-id="a161d-108">End pattern ranges with a closing bracket.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a161d-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a161d-109">See also</span></span>
- [<span data-ttu-id="a161d-110">Operador Like</span><span class="sxs-lookup"><span data-stu-id="a161d-110">Like Operator</span></span>](../../visual-basic/language-reference/operators/like-operator.md)
