---
title: "&quot;&lt;typename&gt;&quot; não pode herdar de &lt;tipo&gt; &quot;&lt;NomeDoTipoBase&gt;&quot; porque ele expande o acesso da base de &lt;tipo&gt; fora do assembly | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30910
- bc30910
dev_langs:
- VB
helpviewer_keywords:
- BC30910
ms.assetid: 68fc05c5-5d55-4742-9a3b-ea04312594f4
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 126dfb9c3e3793505c47a40bb8862a2d70aff980
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="39lttypenamegt39-cannot-inherit-from-lttypegt-39ltbasetypenamegt39-because-it-expands-the-access-of-the-base-lttypegt-outside-the-assembly"></a><span data-ttu-id="47b9a-102">'&lt;typename&gt;' não pode herdar de &lt;tipo&gt; '&lt;NomeDoTipoBase&gt;' porque ele expande o acesso da base de &lt;tipo&gt; fora do assembly</span><span class="sxs-lookup"><span data-stu-id="47b9a-102">&#39;&lt;typename&gt;&#39; cannot inherit from &lt;type&gt; &#39;&lt;basetypename&gt;&#39; because it expands the access of the base &lt;type&gt; outside the assembly</span></span>
<span data-ttu-id="47b9a-103">Uma classe ou interface herda de uma classe base ou interface, mas tem um nível de acesso menos restritivo.</span><span class="sxs-lookup"><span data-stu-id="47b9a-103">A class or interface inherits from a base class or interface but has a less restrictive access level.</span></span>  
  
 <span data-ttu-id="47b9a-104">Por exemplo, um `Public` interface herda de uma `Friend` interface, ou um `Protected` classe herda de uma `Private` classe.</span><span class="sxs-lookup"><span data-stu-id="47b9a-104">For example, a `Public` interface inherits from a `Friend` interface, or a `Protected` class inherits from a `Private` class.</span></span> <span data-ttu-id="47b9a-105">Isso expõe a classe base ou interface para acesso além do nível desejado.</span><span class="sxs-lookup"><span data-stu-id="47b9a-105">This exposes the base class or interface to access beyond the intended level.</span></span>  
  
 <span data-ttu-id="47b9a-106">**ID do erro:** BC30910</span><span class="sxs-lookup"><span data-stu-id="47b9a-106">**Error ID:** BC30910</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="47b9a-107">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="47b9a-107">To correct this error</span></span>  
  
-   <span data-ttu-id="47b9a-108">Altere o nível de acesso da classe derivada ou interface seja pelo menos tão restritivo quanto da classe base ou interface.</span><span class="sxs-lookup"><span data-stu-id="47b9a-108">Change the access level of the derived class or interface to be at least as restrictive as that of the base class or interface.</span></span>  
  
     <span data-ttu-id="47b9a-109">-ou-</span><span class="sxs-lookup"><span data-stu-id="47b9a-109">-or-</span></span>  
  
-   <span data-ttu-id="47b9a-110">Se você exigir o nível de acesso menos restritivo, remova o `Inherits` instrução.</span><span class="sxs-lookup"><span data-stu-id="47b9a-110">If you require the less restrictive access level, remove the `Inherits` statement.</span></span> <span data-ttu-id="47b9a-111">Você não pode herdar de uma interface ou classe base mais restrito.</span><span class="sxs-lookup"><span data-stu-id="47b9a-111">You cannot inherit from a more restricted base class or interface.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47b9a-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="47b9a-112">See Also</span></span>  
 <span data-ttu-id="47b9a-113">[Instrução Class](../../../visual-basic/language-reference/statements/class-statement.md) </span><span class="sxs-lookup"><span data-stu-id="47b9a-113">[Class Statement](../../../visual-basic/language-reference/statements/class-statement.md) </span></span>  
<span data-ttu-id="47b9a-114"> [Instrução interface](../../../visual-basic/language-reference/statements/interface-statement.md) </span><span class="sxs-lookup"><span data-stu-id="47b9a-114"> [Interface Statement](../../../visual-basic/language-reference/statements/interface-statement.md) </span></span>  
<span data-ttu-id="47b9a-115"> [Instrução Inherits](../../../visual-basic/language-reference/statements/inherits-statement.md) </span><span class="sxs-lookup"><span data-stu-id="47b9a-115"> [Inherits Statement](../../../visual-basic/language-reference/statements/inherits-statement.md) </span></span>  
<span data-ttu-id="47b9a-116"> [Níveis de acesso no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)</span><span class="sxs-lookup"><span data-stu-id="47b9a-116"> [Access Levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)</span></span>
