---
title: '&#39;&lt;membername&gt; &#39; não pode expor o tipo &#39; &lt;typename&gt; &#39; fora do projeto por meio de &lt;containertype&gt; &#39; &lt;containertypename&gt;&#39;'
ms.date: 07/20/2015
f1_keywords:
- bc30909
- vbc30909
helpviewer_keywords:
- BC30909
ms.assetid: ffa7395d-e182-4087-8ce8-079810fdae54
ms.openlocfilehash: 36add48ebee2d1804921eeeec0b59cdd4cbafecc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="39ltmembernamegt39-cannot-expose-type-39lttypenamegt39-outside-the-project-through-ltcontainertypegt-39ltcontainertypenamegt39"></a><span data-ttu-id="306fe-102">&#39;&lt;membername&gt; &#39; não pode expor o tipo &#39; &lt;typename&gt; &#39; fora do projeto por meio de &lt;containertype&gt; &#39; &lt;containertypename&gt;&#39;</span><span class="sxs-lookup"><span data-stu-id="306fe-102">&#39;&lt;membername&gt;&#39; cannot expose type &#39;&lt;typename&gt;&#39; outside the project through &lt;containertype&gt; &#39;&lt;containertypename&gt;&#39;</span></span>
<span data-ttu-id="306fe-103">Uma variável, parâmetro de procedimento ou função de retorno é exposta fora de seu contêiner, mas ele é declarado como um tipo que não deve ser exposto fora do contêiner.</span><span class="sxs-lookup"><span data-stu-id="306fe-103">A variable, procedure parameter, or function return is exposed outside its container, but it is declared as a type that must not be exposed outside the container.</span></span>  
  
 <span data-ttu-id="306fe-104">O seguinte código esqueleto mostra uma situação que gera este erro.</span><span class="sxs-lookup"><span data-stu-id="306fe-104">The following skeleton code shows a situation that generates this error.</span></span>  
  
```  
Private Class privateClass  
End Class  
Public Class mainClass  
    Public exposedVar As New privateClass  
End Class  
```  
  
 <span data-ttu-id="306fe-105">Um tipo que é declarado `Protected`, `Friend`, `Protected Friend`, ou `Private` destina-se para ter acesso fora de seu contexto de declaração limitado.</span><span class="sxs-lookup"><span data-stu-id="306fe-105">A type that is declared `Protected`, `Friend`, `Protected Friend`, or `Private` is intended to have limited access outside its declaration context.</span></span> <span data-ttu-id="306fe-106">Usá-lo como os dados de tipo de uma variável com acesso restrito menos anularia essa finalidade.</span><span class="sxs-lookup"><span data-stu-id="306fe-106">Using it as the data type of a variable with less restricted access would defeat this purpose.</span></span> <span data-ttu-id="306fe-107">No código anterior esqueleto, `exposedVar` é `Public` e poderia expor `privateClass` ao código que não deve ter acesso a ele.</span><span class="sxs-lookup"><span data-stu-id="306fe-107">In the preceding skeleton code, `exposedVar` is `Public` and would expose `privateClass` to code that should not have access to it.</span></span>  
  
 <span data-ttu-id="306fe-108">**ID do erro:** BC30909</span><span class="sxs-lookup"><span data-stu-id="306fe-108">**Error ID:** BC30909</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="306fe-109">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="306fe-109">To correct this error</span></span>  
  
-   <span data-ttu-id="306fe-110">Altere o nível de acesso da variável, parâmetro de procedimento ou função de retorno para ser pelo menos tão restritivo quanto o nível de acesso do seu tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="306fe-110">Change the access level of the variable, procedure parameter, or function return to be at least as restrictive as the access level of its data type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="306fe-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="306fe-111">See Also</span></span>  
 [<span data-ttu-id="306fe-112">Níveis de acesso no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="306fe-112">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
