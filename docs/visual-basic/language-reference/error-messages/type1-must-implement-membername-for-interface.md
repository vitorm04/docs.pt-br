---
title: '&lt;type1&gt;&quot;&lt;typename&gt;&quot;deve implementar&quot;&lt;membername&gt;&quot;para interface&quot;&lt;interfacename&gt;&quot; | Documentos do Microsoft'
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30154
- bc30154
dev_langs:
- VB
helpviewer_keywords:
- BC30154
ms.assetid: 259afdfa-3608-4760-adcb-88ec0da5020d
caps.latest.revision: 9
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
ms.openlocfilehash: 6087f9941d40e6e829c4172c347af23607abf41d
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="lttype1gt39lttypenamegt39-must-implement-39ltmembernamegt39-for-interface-39ltinterfacenamegt39"></a><span data-ttu-id="52065-102">&lt;type1&gt;'&lt;typename&gt;'deve implementar'&lt;membername&gt;'para interface'&lt;interfacename&gt;'</span><span class="sxs-lookup"><span data-stu-id="52065-102">&lt;type1&gt;&#39;&lt;typename&gt;&#39; must implement &#39;&lt;membername&gt;&#39; for interface &#39;&lt;interfacename&gt;&#39;</span></span>
<span data-ttu-id="52065-103">'\<typename >' deve implementar '\<membername >' para interface '\<interfacename >'.</span><span class="sxs-lookup"><span data-stu-id="52065-103">'\<typename>' must implement '\<membername>' for interface '\<interfacename>'.</span></span> <span data-ttu-id="52065-104">Implementação de propriedade deve ter 'ReadOnly' / 'WriteOnly' especificadores.</span><span class="sxs-lookup"><span data-stu-id="52065-104">Implementing property must have matching 'ReadOnly'/'WriteOnly' specifiers.</span></span>  
  
 <span data-ttu-id="52065-105">Uma classe ou estrutura alega implementar uma interface mas não implementa um procedimento, propriedade ou evento definido pela interface.</span><span class="sxs-lookup"><span data-stu-id="52065-105">A class or structure claims to implement an interface but does not implement a procedure, property, or event defined by the interface.</span></span> <span data-ttu-id="52065-106">Cada membro da interface deve ser implementado.</span><span class="sxs-lookup"><span data-stu-id="52065-106">Every member of the interface must be implemented.</span></span>  
  
 <span data-ttu-id="52065-107">**ID do erro:** BC30154</span><span class="sxs-lookup"><span data-stu-id="52065-107">**Error ID:** BC30154</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="52065-108">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="52065-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="52065-109">Declare um membro com o mesmo nome e assinatura, conforme definido na interface.</span><span class="sxs-lookup"><span data-stu-id="52065-109">Declare a member with the same name and signature as defined in the interface.</span></span> <span data-ttu-id="52065-110">Não se esqueça de incluir pelo menos o `End Function`, `End Sub`, ou `End Property` instrução.</span><span class="sxs-lookup"><span data-stu-id="52065-110">Be sure to include at least the `End Function`, `End Sub`, or `End Property` statement.</span></span>  
  
2.  <span data-ttu-id="52065-111">Adicionar uma `Implements` cláusula no final do `Function`, `Sub`, `Property`, ou `Event` instrução.</span><span class="sxs-lookup"><span data-stu-id="52065-111">Add an `Implements` clause to the end of the `Function`, `Sub`, `Property`, or `Event` statement.</span></span> <span data-ttu-id="52065-112">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="52065-112">For example:</span></span>  
  
    ```  
    Public Event ItHappened() Implements IBaseInterface.ItHappened  
    ```  
  
3.  <span data-ttu-id="52065-113">Quando estiver implementando uma propriedade, verifique se `ReadOnly` ou `WriteOnly` é usado da mesma forma como na definição de interface.</span><span class="sxs-lookup"><span data-stu-id="52065-113">When implementing a property, make sure that `ReadOnly` or `WriteOnly` is used in the same way as in the interface definition.</span></span>  
  
4.  <span data-ttu-id="52065-114">Quando estiver implementando uma propriedade, declare `Get` e `Set` procedimentos, conforme apropriado.</span><span class="sxs-lookup"><span data-stu-id="52065-114">When implementing a property, declare `Get` and `Set` procedures, as appropriate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52065-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="52065-115">See Also</span></span>  
 <span data-ttu-id="52065-116">[Instrução Implements](../../../visual-basic/language-reference/statements/implements-statement.md) </span><span class="sxs-lookup"><span data-stu-id="52065-116">[Implements Statement](../../../visual-basic/language-reference/statements/implements-statement.md) </span></span>  
<span data-ttu-id="52065-117"> [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md)</span><span class="sxs-lookup"><span data-stu-id="52065-117"> [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md)</span></span>
