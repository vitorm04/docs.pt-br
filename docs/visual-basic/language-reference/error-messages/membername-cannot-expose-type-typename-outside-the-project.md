---
title: "'<membername>' não pode expor o tipo '<typename>' fora do projeto por meio de <containertype> '<containertypename>'"
ms.date: 07/20/2015
f1_keywords:
- bc30909
- vbc30909
helpviewer_keywords:
- BC30909
ms.assetid: ffa7395d-e182-4087-8ce8-079810fdae54
ms.openlocfilehash: a3972eabfe297b89c0e4d0f36943ac58e5bdf688
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162460"
---
# <a name="bc30909-membername-cannot-expose-type-typename-outside-the-project-through-containertype-containertypename"></a><span data-ttu-id="9da8d-102">BC30909: ' \<membername> ' não pode expor o tipo ' \<typename> ' fora do projeto por meio de \<containertype> ' \<containertypename> '</span><span class="sxs-lookup"><span data-stu-id="9da8d-102">BC30909: '\<membername>' cannot expose type '\<typename>' outside the project through \<containertype> '\<containertypename>'</span></span>

<span data-ttu-id="9da8d-103">Uma variável, um parâmetro de procedimento ou um retorno de função é exposto fora de seu contêiner, mas é declarado como um tipo que não deve ser exposto fora do contêiner.</span><span class="sxs-lookup"><span data-stu-id="9da8d-103">A variable, procedure parameter, or function return is exposed outside its container, but it is declared as a type that must not be exposed outside the container.</span></span>

 <span data-ttu-id="9da8d-104">O código esqueleto a seguir mostra uma situação que gera esse erro.</span><span class="sxs-lookup"><span data-stu-id="9da8d-104">The following skeleton code shows a situation that generates this error.</span></span>

```vb
Private Class privateClass
End Class
Public Class mainClass
    Public exposedVar As New privateClass
End Class
```

 <span data-ttu-id="9da8d-105">Um tipo declarado `Protected` , `Friend` , `Protected Friend` ou `Private` destinado a ter acesso limitado fora de seu contexto de declaração.</span><span class="sxs-lookup"><span data-stu-id="9da8d-105">A type that is declared `Protected`, `Friend`, `Protected Friend`, or `Private` is intended to have limited access outside its declaration context.</span></span> <span data-ttu-id="9da8d-106">Usá-lo como o tipo de dados de uma variável com acesso menos restrito anularia essa finalidade.</span><span class="sxs-lookup"><span data-stu-id="9da8d-106">Using it as the data type of a variable with less restricted access would defeat this purpose.</span></span> <span data-ttu-id="9da8d-107">No código esqueleto anterior, `exposedVar` é `Public` e seria exposto `privateClass` ao código que não deveria ter acesso a ele.</span><span class="sxs-lookup"><span data-stu-id="9da8d-107">In the preceding skeleton code, `exposedVar` is `Public` and would expose `privateClass` to code that should not have access to it.</span></span>

 <span data-ttu-id="9da8d-108">**ID do erro:** BC30909</span><span class="sxs-lookup"><span data-stu-id="9da8d-108">**Error ID:** BC30909</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="9da8d-109">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="9da8d-109">To correct this error</span></span>

- <span data-ttu-id="9da8d-110">Altere o nível de acesso da variável, do parâmetro de procedimento ou da função retornar para ser pelo menos tão restritivo quanto o nível de acesso de seu tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="9da8d-110">Change the access level of the variable, procedure parameter, or function return to be at least as restrictive as the access level of its data type.</span></span>

## <a name="see-also"></a><span data-ttu-id="9da8d-111">Veja também</span><span class="sxs-lookup"><span data-stu-id="9da8d-111">See also</span></span>

- [<span data-ttu-id="9da8d-112">Níveis de acesso no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9da8d-112">Access levels in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/access-levels.md)
