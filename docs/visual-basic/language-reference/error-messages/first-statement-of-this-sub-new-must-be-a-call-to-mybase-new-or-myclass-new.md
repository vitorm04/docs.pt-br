---
title: A primeira instrução deste ' Sub New ' deve ser uma chamada para 'MyBase.New' ou 'MyClass.New' (nenhum construtor acessível sem parâmetros)
ms.date: 07/20/2015
f1_keywords:
- bc30148
- vbc30148
helpviewer_keywords:
- BC30148
ms.assetid: 4426e8fc-cb39-4eb8-ba95-503cd32fcc89
ms.openlocfilehash: d29d7609f8f3f38eadda9a9c763f3ba8e6b99e61
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57365081"
---
# <a name="first-statement-of-this-sub-new-must-be-a-call-to-mybasenew-or-myclassnew-no-accessible-constructor-without-parameters"></a><span data-ttu-id="7fc80-102">A primeira instrução deste ' Sub New ' deve ser uma chamada para 'MyBase.New' ou 'MyClass.New' (nenhum construtor acessível sem parâmetros)</span><span class="sxs-lookup"><span data-stu-id="7fc80-102">First statement of this 'Sub New' must be a call to 'MyBase.New' or 'MyClass.New' (No Accessible Constructor Without Parameters)</span></span>
<span data-ttu-id="7fc80-103">A primeira instrução deste 'Sub New' deve ser uma chamada para 'MyBase. New' ou 'MyClass. New' porque classe base\<basename >' de '\<derivedname >' não tem um 'Sub New' acessível que pode ser chamado sem argumentos.</span><span class="sxs-lookup"><span data-stu-id="7fc80-103">First statement of this 'Sub New' must be a call to 'MyBase.New' or 'MyClass.New' because base class '\<basename>' of '\<derivedname>' does not have an accessible 'Sub New' that can be called with no arguments.</span></span>  
  
 <span data-ttu-id="7fc80-104">Em uma classe derivada, cada construtor deve chamar um construtor de classe base (`MyBase.New`).</span><span class="sxs-lookup"><span data-stu-id="7fc80-104">In a derived class, every constructor must call a base class constructor (`MyBase.New`).</span></span> <span data-ttu-id="7fc80-105">Se a classe base tem um construtor sem parâmetros acessível a classes derivadas, `MyBase.New` pode ser chamado automaticamente.</span><span class="sxs-lookup"><span data-stu-id="7fc80-105">If the base class has a constructor with no parameters that is accessible to derived classes, `MyBase.New` can be called automatically.</span></span> <span data-ttu-id="7fc80-106">Caso contrário, um construtor de classe base deve ser chamado com parâmetros, e isso não pode ser feito automaticamente.</span><span class="sxs-lookup"><span data-stu-id="7fc80-106">If not, a base class constructor must be called with parameters, and this cannot be done automatically.</span></span> <span data-ttu-id="7fc80-107">Nesse caso, a primeira instrução de cada construtor de classe derivada deve chamar um construtor parametrizado na classe base ou chamar outro construtor na classe derivada que faz um construtor de classe base chamada.</span><span class="sxs-lookup"><span data-stu-id="7fc80-107">In this case, the first statement of every derived class constructor must call a parameterized constructor on the base class, or call another constructor in the derived class that makes a base class constructor call.</span></span>  
  
 <span data-ttu-id="7fc80-108">**ID do erro:** BC30148</span><span class="sxs-lookup"><span data-stu-id="7fc80-108">**Error ID:** BC30148</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="7fc80-109">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="7fc80-109">To correct this error</span></span>  
  
-   <span data-ttu-id="7fc80-110">Chamar `MyBase.New` fornecendo os parâmetros necessários ou chamar um construtor de mesmo nível que torna essa chamada.</span><span class="sxs-lookup"><span data-stu-id="7fc80-110">Either call `MyBase.New` supplying the required parameters, or call a peer constructor that makes such a call.</span></span>  
  
     <span data-ttu-id="7fc80-111">Por exemplo, se a classe base tem um construtor que é declarado como `Public Sub New(ByVal index as Integer)`, a primeira instrução em derivado construtor de classe pode ser `MyBase.New(100)`.</span><span class="sxs-lookup"><span data-stu-id="7fc80-111">For example, if the base class has a constructor that’s declared as `Public Sub New(ByVal index as Integer)`, the first statement in the derived class constructor might be `MyBase.New(100)`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7fc80-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7fc80-112">See also</span></span>
- [<span data-ttu-id="7fc80-113">Noções Básicas de Herança</span><span class="sxs-lookup"><span data-stu-id="7fc80-113">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
