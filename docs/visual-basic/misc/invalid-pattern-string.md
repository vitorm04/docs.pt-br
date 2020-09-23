---
title: Cadeia de caracteres de padrão inválida
ms.date: 07/20/2015
ms.assetid: ec1aecdb-5339-4a93-be71-eec56b1d7438
ms.openlocfilehash: 5ef12ac27e96205f9ef1c964293847f56b11cb78
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91090684"
---
# <a name="invalid-pattern-string"></a><span data-ttu-id="e8c6d-102">Cadeia de caracteres de padrão inválida</span><span class="sxs-lookup"><span data-stu-id="e8c6d-102">Invalid pattern string</span></span>

<span data-ttu-id="e8c6d-103">A cadeia de caracteres de padrão especificada na `Like` operação de uma pesquisa é inválida.</span><span class="sxs-lookup"><span data-stu-id="e8c6d-103">The pattern string specified in the `Like` operation of a search is invalid.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e8c6d-104">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="e8c6d-104">To correct this error</span></span>  
  
1. <span data-ttu-id="e8c6d-105">Examine os caracteres válidos para expressões de lista.</span><span class="sxs-lookup"><span data-stu-id="e8c6d-105">Review the valid characters for list expressions.</span></span>  
  
2. <span data-ttu-id="e8c6d-106">No intervalo de padrões, verifique se o caractere de intervalo inicial é menor que o caractere de intervalo final, como em `[a-z]` .</span><span class="sxs-lookup"><span data-stu-id="e8c6d-106">In the pattern range, ensure that the start range character is less than the end range character, as in `[a-z]`.</span></span>  
  
3. <span data-ttu-id="e8c6d-107">No intervalo de padrões, verifique se não há vários hifens próximos um do outro, como em `[a--z]` .</span><span class="sxs-lookup"><span data-stu-id="e8c6d-107">In the pattern range, ensure that there are not multiple hyphens next to each other, as in `[a--z]`.</span></span>  
  
4. <span data-ttu-id="e8c6d-108">Intervalos de padrão de término com um colchete de fechamento.</span><span class="sxs-lookup"><span data-stu-id="e8c6d-108">End pattern ranges with a closing bracket.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8c6d-109">Confira também</span><span class="sxs-lookup"><span data-stu-id="e8c6d-109">See also</span></span>

- [<span data-ttu-id="e8c6d-110">Operador Like</span><span class="sxs-lookup"><span data-stu-id="e8c6d-110">Like Operator</span></span>](../language-reference/operators/like-operator.md)
