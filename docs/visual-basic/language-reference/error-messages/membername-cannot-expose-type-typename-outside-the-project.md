---
title: "'<membername>' não pode expor o tipo '<typename>' fora do projeto por meio de <containertype> '<containertypename>'"
ms.date: 07/20/2015
f1_keywords:
- bc30909
- vbc30909
helpviewer_keywords:
- BC30909
ms.assetid: ffa7395d-e182-4087-8ce8-079810fdae54
ms.openlocfilehash: ca67e74d7790352bd1842cb8a59fe1525af6e18c
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71700895"
---
# <a name="membername-cannot-expose-type-typename-outside-the-project-through-containertype-containertypename"></a><span data-ttu-id="3d1d2-102">' \<membername > ' não pode expor o tipo ' \<typename > ' fora do projeto por meio de \<containertype > ' \<containertypename > '</span><span class="sxs-lookup"><span data-stu-id="3d1d2-102">'\<membername>' cannot expose type '\<typename>' outside the project through \<containertype> '\<containertypename>'</span></span>
<span data-ttu-id="3d1d2-103">Uma variável, um parâmetro de procedimento ou um retorno de função é exposto fora de seu contêiner, mas é declarado como um tipo que não deve ser exposto fora do contêiner.</span><span class="sxs-lookup"><span data-stu-id="3d1d2-103">A variable, procedure parameter, or function return is exposed outside its container, but it is declared as a type that must not be exposed outside the container.</span></span>  
  
 <span data-ttu-id="3d1d2-104">O código esqueleto a seguir mostra uma situação que gera esse erro.</span><span class="sxs-lookup"><span data-stu-id="3d1d2-104">The following skeleton code shows a situation that generates this error.</span></span>  
  
```vb  
Private Class privateClass  
End Class  
Public Class mainClass  
    Public exposedVar As New privateClass  
End Class  
```  
  
 <span data-ttu-id="3d1d2-105">Um tipo declarado `Protected`, `Friend`, `Protected Friend` ou `Private` destina-se a ter acesso limitado fora de seu contexto de declaração.</span><span class="sxs-lookup"><span data-stu-id="3d1d2-105">A type that is declared `Protected`, `Friend`, `Protected Friend`, or `Private` is intended to have limited access outside its declaration context.</span></span> <span data-ttu-id="3d1d2-106">Usá-lo como o tipo de dados de uma variável com acesso menos restrito anularia essa finalidade.</span><span class="sxs-lookup"><span data-stu-id="3d1d2-106">Using it as the data type of a variable with less restricted access would defeat this purpose.</span></span> <span data-ttu-id="3d1d2-107">No código esqueleto anterior, `exposedVar` é `Public` e exporia `privateClass` ao código que não deveria ter acesso a ele.</span><span class="sxs-lookup"><span data-stu-id="3d1d2-107">In the preceding skeleton code, `exposedVar` is `Public` and would expose `privateClass` to code that should not have access to it.</span></span>  
  
 <span data-ttu-id="3d1d2-108">**ID do erro:** BC30909</span><span class="sxs-lookup"><span data-stu-id="3d1d2-108">**Error ID:** BC30909</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="3d1d2-109">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="3d1d2-109">To correct this error</span></span>  
  
- <span data-ttu-id="3d1d2-110">Altere o nível de acesso da variável, do parâmetro de procedimento ou da função retornar para ser pelo menos tão restritivo quanto o nível de acesso de seu tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="3d1d2-110">Change the access level of the variable, procedure parameter, or function return to be at least as restrictive as the access level of its data type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d1d2-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3d1d2-111">See also</span></span>

- [<span data-ttu-id="3d1d2-112">Níveis de acesso no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3d1d2-112">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
