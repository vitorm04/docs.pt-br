---
title: "'<typename>' não pode ser herdado de <type> '<basetypename>' porque ele expande o acesso do <type> base fora do assembly"
ms.date: 07/20/2015
f1_keywords:
- vbc30910
- bc30910
helpviewer_keywords:
- BC30910
ms.assetid: 68fc05c5-5d55-4742-9a3b-ea04312594f4
ms.openlocfilehash: dc979a66c73fdf15a4349a003680156e0ce27ed3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61764355"
---
# <a name="typename-cannot-inherit-from-type-basetypename-because-it-expands-the-access-of-the-base-type-outside-the-assembly"></a><span data-ttu-id="31d2c-102">'\<typename >' não pode herdar de \<tipo > '\<basetypename >' porque ele expande o acesso da base de \<tipo > fora do assembly</span><span class="sxs-lookup"><span data-stu-id="31d2c-102">'\<typename>' cannot inherit from \<type> '\<basetypename>' because it expands the access of the base \<type> outside the assembly</span></span>
<span data-ttu-id="31d2c-103">Uma classe ou interface herda de uma classe base ou interface, mas tem um nível de acesso menos restritivo.</span><span class="sxs-lookup"><span data-stu-id="31d2c-103">A class or interface inherits from a base class or interface but has a less restrictive access level.</span></span>  
  
 <span data-ttu-id="31d2c-104">Por exemplo, uma `Public` interface herda de uma `Friend` interface, ou um `Protected` classe herda de uma `Private` classe.</span><span class="sxs-lookup"><span data-stu-id="31d2c-104">For example, a `Public` interface inherits from a `Friend` interface, or a `Protected` class inherits from a `Private` class.</span></span> <span data-ttu-id="31d2c-105">Isso expõe a classe base ou interface para acesso além do nível desejado.</span><span class="sxs-lookup"><span data-stu-id="31d2c-105">This exposes the base class or interface to access beyond the intended level.</span></span>  
  
 <span data-ttu-id="31d2c-106">**ID do erro:** BC30910</span><span class="sxs-lookup"><span data-stu-id="31d2c-106">**Error ID:** BC30910</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="31d2c-107">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="31d2c-107">To correct this error</span></span>  
  
- <span data-ttu-id="31d2c-108">Altere o nível de acesso da classe derivada ou interface seja pelo menos tão restritivo quanto da classe base ou interface.</span><span class="sxs-lookup"><span data-stu-id="31d2c-108">Change the access level of the derived class or interface to be at least as restrictive as that of the base class or interface.</span></span>  
  
     <span data-ttu-id="31d2c-109">- ou -</span><span class="sxs-lookup"><span data-stu-id="31d2c-109">-or-</span></span>  
  
- <span data-ttu-id="31d2c-110">Se você exigir o nível de acesso menos restritivo, remova o `Inherits` instrução.</span><span class="sxs-lookup"><span data-stu-id="31d2c-110">If you require the less restrictive access level, remove the `Inherits` statement.</span></span> <span data-ttu-id="31d2c-111">Você não pode herdar de uma classe base mais restrito ou interface.</span><span class="sxs-lookup"><span data-stu-id="31d2c-111">You cannot inherit from a more restricted base class or interface.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31d2c-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="31d2c-112">See also</span></span>

- [<span data-ttu-id="31d2c-113">Instrução Class</span><span class="sxs-lookup"><span data-stu-id="31d2c-113">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)
- [<span data-ttu-id="31d2c-114">Instrução Interface</span><span class="sxs-lookup"><span data-stu-id="31d2c-114">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)
- [<span data-ttu-id="31d2c-115">Instrução Inherits</span><span class="sxs-lookup"><span data-stu-id="31d2c-115">Inherits Statement</span></span>](../../../visual-basic/language-reference/statements/inherits-statement.md)
- [<span data-ttu-id="31d2c-116">Níveis de acesso no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="31d2c-116">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
