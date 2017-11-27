---
title: "Cadeia de caracteres de padrão inválido"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
ms.assetid: ec1aecdb-5339-4a93-be71-eec56b1d7438
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f824a5844d6d2b365358030119826266a4b42ef3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="invalid-pattern-string"></a><span data-ttu-id="be679-102">Cadeia de caracteres de padrão inválido</span><span class="sxs-lookup"><span data-stu-id="be679-102">Invalid pattern string</span></span>
<span data-ttu-id="be679-103">A cadeia de caracteres padrão especificada no `Like` operação de uma pesquisa é inválida.</span><span class="sxs-lookup"><span data-stu-id="be679-103">The pattern string specified in the `Like` operation of a search is invalid.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="be679-104">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="be679-104">To correct this error</span></span>  
  
1.  <span data-ttu-id="be679-105">Examine os caracteres válidos para expressões da lista.</span><span class="sxs-lookup"><span data-stu-id="be679-105">Review the valid characters for list expressions.</span></span>  
  
2.  <span data-ttu-id="be679-106">O intervalo padrão, certifique-se de que o caractere de intervalo de início é menor que o caractere de intervalo de término, como em `[a-z]`.</span><span class="sxs-lookup"><span data-stu-id="be679-106">In the pattern range, ensure that the start range character is less than the end range character, as in `[a-z]`.</span></span>  
  
3.  <span data-ttu-id="be679-107">O intervalo padrão, certifique-se de que não haja vários hifens próximos um do outro, como em `[a--z]`.</span><span class="sxs-lookup"><span data-stu-id="be679-107">In the pattern range, ensure that there are not multiple hyphens next to each other, as in `[a--z]`.</span></span>  
  
4.  <span data-ttu-id="be679-108">Intervalos de padrão de término com um colchete de fechamento.</span><span class="sxs-lookup"><span data-stu-id="be679-108">End pattern ranges with a closing bracket.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be679-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="be679-109">See Also</span></span>  
 [<span data-ttu-id="be679-110">Operador Like</span><span class="sxs-lookup"><span data-stu-id="be679-110">Like Operator</span></span>](../../visual-basic/language-reference/operators/like-operator.md)
