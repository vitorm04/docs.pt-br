---
title: "'<typename>' não pode ser herdado de <type> '<basetypename>' porque ele expande o acesso do <type> base fora do assembly"
ms.date: 07/20/2015
f1_keywords:
- vbc30910
- bc30910
helpviewer_keywords:
- BC30910
ms.assetid: 68fc05c5-5d55-4742-9a3b-ea04312594f4
ms.openlocfilehash: 5adb5a74c220c7b2f95ac7370040a7fa2bd34299
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90872064"
---
# <a name="typename-cannot-inherit-from-type-basetypename-because-it-expands-the-access-of-the-base-type-outside-the-assembly"></a><span data-ttu-id="5c83a-102">'\<typename>' não pode ser herdado de \<type> '\<basetypename>' porque ele expande o acesso do \<type> base fora do assembly</span><span class="sxs-lookup"><span data-stu-id="5c83a-102">'\<typename>' cannot inherit from \<type> '\<basetypename>' because it expands the access of the base \<type> outside the assembly</span></span>

<span data-ttu-id="5c83a-103">Uma classe ou interface herda de uma classe base ou interface, mas tem um nível de acesso menos restritivo.</span><span class="sxs-lookup"><span data-stu-id="5c83a-103">A class or interface inherits from a base class or interface but has a less restrictive access level.</span></span>  
  
 <span data-ttu-id="5c83a-104">Por exemplo, uma `Public` interface herda de uma `Friend` interface ou uma `Protected` classe herda de uma `Private` classe.</span><span class="sxs-lookup"><span data-stu-id="5c83a-104">For example, a `Public` interface inherits from a `Friend` interface, or a `Protected` class inherits from a `Private` class.</span></span> <span data-ttu-id="5c83a-105">Isso expõe a classe base ou a interface para acessar além do nível pretendido.</span><span class="sxs-lookup"><span data-stu-id="5c83a-105">This exposes the base class or interface to access beyond the intended level.</span></span>  
  
 <span data-ttu-id="5c83a-106">**ID do erro:** BC30910</span><span class="sxs-lookup"><span data-stu-id="5c83a-106">**Error ID:** BC30910</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="5c83a-107">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="5c83a-107">To correct this error</span></span>  
  
- <span data-ttu-id="5c83a-108">Altere o nível de acesso da classe derivada ou da interface para que seja pelo menos tão restritiva quanto a classe base ou interface.</span><span class="sxs-lookup"><span data-stu-id="5c83a-108">Change the access level of the derived class or interface to be at least as restrictive as that of the base class or interface.</span></span>  
  
     <span data-ttu-id="5c83a-109">- ou -</span><span class="sxs-lookup"><span data-stu-id="5c83a-109">-or-</span></span>  
  
- <span data-ttu-id="5c83a-110">Se você precisar do nível de acesso menos restritivo, remova a `Inherits` instrução.</span><span class="sxs-lookup"><span data-stu-id="5c83a-110">If you require the less restrictive access level, remove the `Inherits` statement.</span></span> <span data-ttu-id="5c83a-111">Não é possível herdar de uma classe base ou interface mais restrita.</span><span class="sxs-lookup"><span data-stu-id="5c83a-111">You cannot inherit from a more restricted base class or interface.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c83a-112">Confira também</span><span class="sxs-lookup"><span data-stu-id="5c83a-112">See also</span></span>

- [<span data-ttu-id="5c83a-113">Instrução Class</span><span class="sxs-lookup"><span data-stu-id="5c83a-113">Class Statement</span></span>](../statements/class-statement.md)
- [<span data-ttu-id="5c83a-114">Instrução Interface</span><span class="sxs-lookup"><span data-stu-id="5c83a-114">Interface Statement</span></span>](../statements/interface-statement.md)
- [<span data-ttu-id="5c83a-115">Instrução Inherits</span><span class="sxs-lookup"><span data-stu-id="5c83a-115">Inherits Statement</span></span>](../statements/inherits-statement.md)
- [<span data-ttu-id="5c83a-116">Níveis de acesso no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5c83a-116">Access levels in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/access-levels.md)
