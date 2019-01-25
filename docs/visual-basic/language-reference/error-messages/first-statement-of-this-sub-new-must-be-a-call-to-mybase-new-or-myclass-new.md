---
title: A primeira instrução &#39;Sub New&#39; deve ser uma chamada para &#39;MyBase. New&#39; ou &#39;MyClass. New&#39; (nenhum construtor acessível sem parâmetros)
ms.date: 07/20/2015
f1_keywords:
- bc30148
- vbc30148
helpviewer_keywords:
- BC30148
ms.assetid: 4426e8fc-cb39-4eb8-ba95-503cd32fcc89
ms.openlocfilehash: 75832ae88908094c1cb74ce04ad84c0d2ae91e68
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54728889"
---
# <a name="first-statement-of-this-39sub-new39-must-be-a-call-to-39mybasenew39-or-39myclassnew39-no-accessible-constructor-without-parameters"></a><span data-ttu-id="f76a0-102">A primeira instrução &#39;Sub New&#39; deve ser uma chamada para &#39;MyBase. New&#39; ou &#39;MyClass. New&#39; (nenhum construtor acessível sem parâmetros)</span><span class="sxs-lookup"><span data-stu-id="f76a0-102">First statement of this &#39;Sub New&#39; must be a call to &#39;MyBase.New&#39; or &#39;MyClass.New&#39; (No Accessible Constructor Without Parameters)</span></span>
<span data-ttu-id="f76a0-103">A primeira instrução deste 'Sub New' deve ser uma chamada para 'MyBase. New' ou 'MyClass. New' porque classe base\<basename >' de '\<derivedname >' não tem um 'Sub New' acessível que pode ser chamado sem argumentos.</span><span class="sxs-lookup"><span data-stu-id="f76a0-103">First statement of this 'Sub New' must be a call to 'MyBase.New' or 'MyClass.New' because base class '\<basename>' of '\<derivedname>' does not have an accessible 'Sub New' that can be called with no arguments.</span></span>  
  
 <span data-ttu-id="f76a0-104">Em uma classe derivada, cada construtor deve chamar um construtor de classe base (`MyBase.New`).</span><span class="sxs-lookup"><span data-stu-id="f76a0-104">In a derived class, every constructor must call a base class constructor (`MyBase.New`).</span></span> <span data-ttu-id="f76a0-105">Se a classe base tem um construtor sem parâmetros acessível a classes derivadas, `MyBase.New` pode ser chamado automaticamente.</span><span class="sxs-lookup"><span data-stu-id="f76a0-105">If the base class has a constructor with no parameters that is accessible to derived classes, `MyBase.New` can be called automatically.</span></span> <span data-ttu-id="f76a0-106">Caso contrário, um construtor de classe base deve ser chamado com parâmetros, e isso não pode ser feito automaticamente.</span><span class="sxs-lookup"><span data-stu-id="f76a0-106">If not, a base class constructor must be called with parameters, and this cannot be done automatically.</span></span> <span data-ttu-id="f76a0-107">Nesse caso, a primeira instrução de cada construtor de classe derivada deve chamar um construtor parametrizado na classe base ou chamar outro construtor na classe derivada que faz um construtor de classe base chamada.</span><span class="sxs-lookup"><span data-stu-id="f76a0-107">In this case, the first statement of every derived class constructor must call a parameterized constructor on the base class, or call another constructor in the derived class that makes a base class constructor call.</span></span>  
  
 <span data-ttu-id="f76a0-108">**ID do erro:** BC30148</span><span class="sxs-lookup"><span data-stu-id="f76a0-108">**Error ID:** BC30148</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f76a0-109">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="f76a0-109">To correct this error</span></span>  
  
-   <span data-ttu-id="f76a0-110">Chamar `MyBase.New` fornecendo os parâmetros necessários ou chamar um construtor de mesmo nível que torna essa chamada.</span><span class="sxs-lookup"><span data-stu-id="f76a0-110">Either call `MyBase.New` supplying the required parameters, or call a peer constructor that makes such a call.</span></span>  
  
     <span data-ttu-id="f76a0-111">Por exemplo, se a classe base tem um construtor que é declarado como `Public Sub New(ByVal index as Integer)`, a primeira instrução em derivado construtor de classe pode ser `MyBase.New(100)`.</span><span class="sxs-lookup"><span data-stu-id="f76a0-111">For example, if the base class has a constructor that’s declared as `Public Sub New(ByVal index as Integer)`, the first statement in the derived class constructor might be `MyBase.New(100)`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f76a0-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f76a0-112">See also</span></span>
- [<span data-ttu-id="f76a0-113">Noções Básicas de Herança</span><span class="sxs-lookup"><span data-stu-id="f76a0-113">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
