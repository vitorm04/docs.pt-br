---
title: '&#39;&lt;TypeName&gt; &#39; não pode herdar de &lt;tipo&gt; &#39; &lt;NomeDoTipoBase&gt; &#39; porque ele expande o acesso da base de &lt;tipo&gt; fora do assembly'
ms.date: 07/20/2015
f1_keywords:
- vbc30910
- bc30910
helpviewer_keywords:
- BC30910
ms.assetid: 68fc05c5-5d55-4742-9a3b-ea04312594f4
ms.openlocfilehash: f747b2b24f5fecc22b9e1fbc6ba26b634e9ead2c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33598418"
---
# <a name="39lttypenamegt39-cannot-inherit-from-lttypegt-39ltbasetypenamegt39-because-it-expands-the-access-of-the-base-lttypegt-outside-the-assembly"></a><span data-ttu-id="7e53e-102">&#39;&lt;TypeName&gt; &#39; não pode herdar de &lt;tipo&gt; &#39; &lt;NomeDoTipoBase&gt; &#39; porque ele expande o acesso da base de &lt;tipo&gt; fora do assembly</span><span class="sxs-lookup"><span data-stu-id="7e53e-102">&#39;&lt;typename&gt;&#39; cannot inherit from &lt;type&gt; &#39;&lt;basetypename&gt;&#39; because it expands the access of the base &lt;type&gt; outside the assembly</span></span>
<span data-ttu-id="7e53e-103">Uma classe ou interface herda de uma classe base ou interface, mas tem um nível de acesso menos restritivo.</span><span class="sxs-lookup"><span data-stu-id="7e53e-103">A class or interface inherits from a base class or interface but has a less restrictive access level.</span></span>  
  
 <span data-ttu-id="7e53e-104">Por exemplo, um `Public` interface herda de uma `Friend` interface, ou um `Protected` classe herda de uma `Private` classe.</span><span class="sxs-lookup"><span data-stu-id="7e53e-104">For example, a `Public` interface inherits from a `Friend` interface, or a `Protected` class inherits from a `Private` class.</span></span> <span data-ttu-id="7e53e-105">Isso expõe a classe base ou interface para acesso além do nível desejado.</span><span class="sxs-lookup"><span data-stu-id="7e53e-105">This exposes the base class or interface to access beyond the intended level.</span></span>  
  
 <span data-ttu-id="7e53e-106">**ID do erro:** BC30910</span><span class="sxs-lookup"><span data-stu-id="7e53e-106">**Error ID:** BC30910</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="7e53e-107">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="7e53e-107">To correct this error</span></span>  
  
-   <span data-ttu-id="7e53e-108">Altere o nível de acesso da classe derivada ou interface para que seja pelo menos tão restritivo quanto da classe base ou interface.</span><span class="sxs-lookup"><span data-stu-id="7e53e-108">Change the access level of the derived class or interface to be at least as restrictive as that of the base class or interface.</span></span>  
  
     <span data-ttu-id="7e53e-109">-ou-</span><span class="sxs-lookup"><span data-stu-id="7e53e-109">-or-</span></span>  
  
-   <span data-ttu-id="7e53e-110">Se você precisar que o nível de acesso menos restritivo, remova o `Inherits` instrução.</span><span class="sxs-lookup"><span data-stu-id="7e53e-110">If you require the less restrictive access level, remove the `Inherits` statement.</span></span> <span data-ttu-id="7e53e-111">Você não pode herdar de uma interface ou classe base mais restrito.</span><span class="sxs-lookup"><span data-stu-id="7e53e-111">You cannot inherit from a more restricted base class or interface.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e53e-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7e53e-112">See Also</span></span>  
 [<span data-ttu-id="7e53e-113">Instrução Class</span><span class="sxs-lookup"><span data-stu-id="7e53e-113">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
 [<span data-ttu-id="7e53e-114">Instrução Interface</span><span class="sxs-lookup"><span data-stu-id="7e53e-114">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
 [<span data-ttu-id="7e53e-115">Instrução Inherits</span><span class="sxs-lookup"><span data-stu-id="7e53e-115">Inherits Statement</span></span>](../../../visual-basic/language-reference/statements/inherits-statement.md)  
 [<span data-ttu-id="7e53e-116">Níveis de acesso no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7e53e-116">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
