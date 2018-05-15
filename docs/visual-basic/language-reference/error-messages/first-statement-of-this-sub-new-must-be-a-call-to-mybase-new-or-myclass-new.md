---
title: A primeira instrução &#39;Sub New&#39; deve ser uma chamada para &#39;MyBase. New&#39; ou &#39;MyClass. New&#39; (nenhum construtor acessível sem parâmetros)
ms.date: 07/20/2015
f1_keywords:
- bc30148
- vbc30148
helpviewer_keywords:
- BC30148
ms.assetid: 4426e8fc-cb39-4eb8-ba95-503cd32fcc89
ms.openlocfilehash: 3b24385932700a4843ae295bc82ef9529cc86b9b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="first-statement-of-this-39sub-new39-must-be-a-call-to-39mybasenew39-or-39myclassnew39-no-accessible-constructor-without-parameters"></a><span data-ttu-id="6acc1-102">A primeira instrução &#39;Sub New&#39; deve ser uma chamada para &#39;MyBase. New&#39; ou &#39;MyClass. New&#39; (nenhum construtor acessível sem parâmetros)</span><span class="sxs-lookup"><span data-stu-id="6acc1-102">First statement of this &#39;Sub New&#39; must be a call to &#39;MyBase.New&#39; or &#39;MyClass.New&#39; (No Accessible Constructor Without Parameters)</span></span>
<span data-ttu-id="6acc1-103">A primeira instrução deste 'Sub New' deve ser uma chamada para 'MyBase. New' ou 'MyClass. New' porque classe base\<nome base >' de '\<derivedname >' não tem um 'Sub New' acessível que pode ser chamado sem argumentos.</span><span class="sxs-lookup"><span data-stu-id="6acc1-103">First statement of this 'Sub New' must be a call to 'MyBase.New' or 'MyClass.New' because base class '\<basename>' of '\<derivedname>' does not have an accessible 'Sub New' that can be called with no arguments.</span></span>  
  
 <span data-ttu-id="6acc1-104">Em uma classe derivada, cada construtor deve chamar um construtor de classe base (`MyBase.New`).</span><span class="sxs-lookup"><span data-stu-id="6acc1-104">In a derived class, every constructor must call a base class constructor (`MyBase.New`).</span></span> <span data-ttu-id="6acc1-105">Se a classe base tem um construtor sem parâmetros que seja acessível a classes derivadas, `MyBase.New` pode ser chamado automaticamente.</span><span class="sxs-lookup"><span data-stu-id="6acc1-105">If the base class has a constructor with no parameters that is accessible to derived classes, `MyBase.New` can be called automatically.</span></span> <span data-ttu-id="6acc1-106">Caso contrário, um construtor de classe base deve ser chamado com parâmetros, e isso não pode ser feito automaticamente.</span><span class="sxs-lookup"><span data-stu-id="6acc1-106">If not, a base class constructor must be called with parameters, and this cannot be done automatically.</span></span> <span data-ttu-id="6acc1-107">Nesse caso, a primeira instrução de cada construtor de classe derivada deve chamar um construtor com parâmetros na classe base ou chamar outro construtor na classe derivada que faz com que um construtor de classe base chamar.</span><span class="sxs-lookup"><span data-stu-id="6acc1-107">In this case, the first statement of every derived class constructor must call a parameterized constructor on the base class, or call another constructor in the derived class that makes a base class constructor call.</span></span>  
  
 <span data-ttu-id="6acc1-108">**ID do erro:** BC30148</span><span class="sxs-lookup"><span data-stu-id="6acc1-108">**Error ID:** BC30148</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="6acc1-109">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="6acc1-109">To correct this error</span></span>  
  
-   <span data-ttu-id="6acc1-110">Chamar `MyBase.New` fornecendo os parâmetros necessários, ou chamar um construtor ponto que faz uma chamada tal.</span><span class="sxs-lookup"><span data-stu-id="6acc1-110">Either call `MyBase.New` supplying the required parameters, or call a peer constructor that makes such a call.</span></span>  
  
     <span data-ttu-id="6acc1-111">Por exemplo, se a classe base tem um construtor que é declarado como `Public Sub New(ByVal index as Integer)`, a primeira instrução em derivada construtor da classe pode ser `MyBase.New(100)`.</span><span class="sxs-lookup"><span data-stu-id="6acc1-111">For example, if the base class has a constructor that’s declared as `Public Sub New(ByVal index as Integer)`, the first statement in the derived class constructor might be `MyBase.New(100)`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6acc1-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6acc1-112">See Also</span></span>  
 [<span data-ttu-id="6acc1-113">Noções Básicas de Herança</span><span class="sxs-lookup"><span data-stu-id="6acc1-113">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
