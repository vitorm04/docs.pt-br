---
title: Cadeia de caracteres padrão inválida
ms.date: 07/20/2015
ms.assetid: ec1aecdb-5339-4a93-be71-eec56b1d7438
ms.openlocfilehash: 7390b9b32eea248969813b52f8d9799798718de0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61790592"
---
# <a name="invalid-pattern-string"></a><span data-ttu-id="aee4a-102">Cadeia de caracteres padrão inválida</span><span class="sxs-lookup"><span data-stu-id="aee4a-102">Invalid pattern string</span></span>
<span data-ttu-id="aee4a-103">A cadeia de caracteres padrão especificada no `Like` operação de uma pesquisa é inválida.</span><span class="sxs-lookup"><span data-stu-id="aee4a-103">The pattern string specified in the `Like` operation of a search is invalid.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="aee4a-104">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="aee4a-104">To correct this error</span></span>  
  
1. <span data-ttu-id="aee4a-105">Examine os caracteres válidos para expressões da lista.</span><span class="sxs-lookup"><span data-stu-id="aee4a-105">Review the valid characters for list expressions.</span></span>  
  
2. <span data-ttu-id="aee4a-106">No intervalo padrão, certifique-se de que o caractere de intervalo de início é menor que o caractere de intervalo de término, como em `[a-z]`.</span><span class="sxs-lookup"><span data-stu-id="aee4a-106">In the pattern range, ensure that the start range character is less than the end range character, as in `[a-z]`.</span></span>  
  
3. <span data-ttu-id="aee4a-107">No intervalo padrão, certifique-se de que não haja várias hifens próximos uns dos outros, como em `[a--z]`.</span><span class="sxs-lookup"><span data-stu-id="aee4a-107">In the pattern range, ensure that there are not multiple hyphens next to each other, as in `[a--z]`.</span></span>  
  
4. <span data-ttu-id="aee4a-108">Intervalos de padrão de término com um colchete de fechamento.</span><span class="sxs-lookup"><span data-stu-id="aee4a-108">End pattern ranges with a closing bracket.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aee4a-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="aee4a-109">See also</span></span>

- [<span data-ttu-id="aee4a-110">Operador Like</span><span class="sxs-lookup"><span data-stu-id="aee4a-110">Like Operator</span></span>](../../visual-basic/language-reference/operators/like-operator.md)
