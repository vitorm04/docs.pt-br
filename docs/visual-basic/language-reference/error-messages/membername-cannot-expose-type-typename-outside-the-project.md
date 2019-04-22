---
title: "'<membername>' não pode expor o tipo '<typename>' fora do projeto por meio de <containertype> '<containertypename>'"
ms.date: 07/20/2015
f1_keywords:
- bc30909
- vbc30909
helpviewer_keywords:
- BC30909
ms.assetid: ffa7395d-e182-4087-8ce8-079810fdae54
ms.openlocfilehash: 16f579a05236ba8977a071cb08068be8e98799f8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58818327"
---
# <a name="membername-cannot-expose-type-typename-outside-the-project-through-containertype-containertypename"></a><span data-ttu-id="be881-102">'\<membername >' não pode expor o tipo '\<typename >' fora do projeto até \<containertype > '\<containertypename >'</span><span class="sxs-lookup"><span data-stu-id="be881-102">'\<membername>' cannot expose type '\<typename>' outside the project through \<containertype> '\<containertypename>'</span></span>
<span data-ttu-id="be881-103">Uma variável, parâmetro de procedimento ou função de retorno seja exposta fora de seu contêiner, mas ele é declarado como um tipo que não deve ser exposto fora do contêiner.</span><span class="sxs-lookup"><span data-stu-id="be881-103">A variable, procedure parameter, or function return is exposed outside its container, but it is declared as a type that must not be exposed outside the container.</span></span>  
  
 <span data-ttu-id="be881-104">O seguinte código de esqueleto mostra uma situação que gera esse erro.</span><span class="sxs-lookup"><span data-stu-id="be881-104">The following skeleton code shows a situation that generates this error.</span></span>  
  
```  
Private Class privateClass  
End Class  
Public Class mainClass  
    Public exposedVar As New privateClass  
End Class  
```  
  
 <span data-ttu-id="be881-105">Um tipo que é declarado `Protected`, `Friend`, `Protected Friend`, ou `Private` destina-se para ter acesso fora de seu contexto de declaração limitado.</span><span class="sxs-lookup"><span data-stu-id="be881-105">A type that is declared `Protected`, `Friend`, `Protected Friend`, or `Private` is intended to have limited access outside its declaration context.</span></span> <span data-ttu-id="be881-106">Usando-a como os dados de tipo de uma variável com acesso restrito menos acabaria com essa finalidade.</span><span class="sxs-lookup"><span data-stu-id="be881-106">Using it as the data type of a variable with less restricted access would defeat this purpose.</span></span> <span data-ttu-id="be881-107">No código de esqueleto anterior, `exposedVar` está `Public` e poderia expor `privateClass` ao código que não deveriam ter acesso a ele.</span><span class="sxs-lookup"><span data-stu-id="be881-107">In the preceding skeleton code, `exposedVar` is `Public` and would expose `privateClass` to code that should not have access to it.</span></span>  
  
 <span data-ttu-id="be881-108">**ID do erro:** BC30909</span><span class="sxs-lookup"><span data-stu-id="be881-108">**Error ID:** BC30909</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="be881-109">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="be881-109">To correct this error</span></span>  
  
-   <span data-ttu-id="be881-110">Alterar o nível de acesso da variável, parâmetro de procedimento ou função de retorno para ser, pelo menos, tão restritivos quanto o nível de acesso de seu tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="be881-110">Change the access level of the variable, procedure parameter, or function return to be at least as restrictive as the access level of its data type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be881-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="be881-111">See also</span></span>

- [<span data-ttu-id="be881-112">Níveis de acesso no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="be881-112">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
