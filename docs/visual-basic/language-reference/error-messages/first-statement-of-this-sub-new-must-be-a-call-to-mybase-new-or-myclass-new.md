---
title: A primeira instrução deste ' Sub New ' deve ser uma chamada para 'MyBase.New' ou 'MyClass.New' (nenhum construtor acessível sem parâmetros)
ms.date: 07/20/2015
f1_keywords:
- bc30148
- vbc30148
helpviewer_keywords:
- BC30148
ms.assetid: 4426e8fc-cb39-4eb8-ba95-503cd32fcc89
ms.openlocfilehash: bce8ad10bc201386f34d6623741c7d41a5dec27e
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92163019"
---
# <a name="bc30148-first-statement-of-this-sub-new-must-be-a-call-to-mybasenew-or-myclassnew-no-accessible-constructor-without-parameters"></a><span data-ttu-id="65626-102">BC30148: a primeira instrução deste ' Sub New ' deve ser uma chamada para ' MyBase. New ' ou ' MyClass. New ' (nenhum construtor acessível sem parâmetros)</span><span class="sxs-lookup"><span data-stu-id="65626-102">BC30148: First statement of this 'Sub New' must be a call to 'MyBase.New' or 'MyClass.New' (No Accessible Constructor Without Parameters)</span></span>

<span data-ttu-id="65626-103">A primeira instrução deste "Sub New" deve ser uma chamada para "MyBase. New" ou "MyClass. New" porque a classe base " \<basename> " de " \<derivedname> " não tem um "Sub New" acessível que pode ser chamado sem argumentos.</span><span class="sxs-lookup"><span data-stu-id="65626-103">First statement of this 'Sub New' must be a call to 'MyBase.New' or 'MyClass.New' because base class '\<basename>' of '\<derivedname>' does not have an accessible 'Sub New' that can be called with no arguments.</span></span>

 <span data-ttu-id="65626-104">Em uma classe derivada, cada Construtor deve chamar um construtor de classe base ( `MyBase.New` ).</span><span class="sxs-lookup"><span data-stu-id="65626-104">In a derived class, every constructor must call a base class constructor (`MyBase.New`).</span></span> <span data-ttu-id="65626-105">Se a classe base tiver um construtor sem parâmetros que seja acessível a classes derivadas, o `MyBase.New` poderá ser chamado automaticamente.</span><span class="sxs-lookup"><span data-stu-id="65626-105">If the base class has a constructor with no parameters that is accessible to derived classes, `MyBase.New` can be called automatically.</span></span> <span data-ttu-id="65626-106">Caso contrário, um construtor de classe base deve ser chamado com parâmetros e isso não pode ser feito automaticamente.</span><span class="sxs-lookup"><span data-stu-id="65626-106">If not, a base class constructor must be called with parameters, and this cannot be done automatically.</span></span> <span data-ttu-id="65626-107">Nesse caso, a primeira instrução de cada Construtor de classe derivada deve chamar um construtor com parâmetros na classe base ou chamar outro construtor na classe derivada que faz uma chamada de construtor de classe base.</span><span class="sxs-lookup"><span data-stu-id="65626-107">In this case, the first statement of every derived class constructor must call a parameterized constructor on the base class, or call another constructor in the derived class that makes a base class constructor call.</span></span>

 <span data-ttu-id="65626-108">**ID do erro:** BC30148</span><span class="sxs-lookup"><span data-stu-id="65626-108">**Error ID:** BC30148</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="65626-109">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="65626-109">To correct this error</span></span>

- <span data-ttu-id="65626-110">Chame `MyBase.New` o fornecimento dos parâmetros necessários ou chame um construtor de pares que faça tal chamada.</span><span class="sxs-lookup"><span data-stu-id="65626-110">Either call `MyBase.New` supplying the required parameters, or call a peer constructor that makes such a call.</span></span>

     <span data-ttu-id="65626-111">Por exemplo, se a classe base tiver um construtor declarado como `Public Sub New(ByVal index as Integer)` , a primeira instrução no construtor de classe derivada poderá ser `MyBase.New(100)` .</span><span class="sxs-lookup"><span data-stu-id="65626-111">For example, if the base class has a constructor that's declared as `Public Sub New(ByVal index as Integer)`, the first statement in the derived class constructor might be `MyBase.New(100)`.</span></span>

## <a name="see-also"></a><span data-ttu-id="65626-112">Veja também</span><span class="sxs-lookup"><span data-stu-id="65626-112">See also</span></span>

- [<span data-ttu-id="65626-113">Noções básicas de herança</span><span class="sxs-lookup"><span data-stu-id="65626-113">Inheritance Basics</span></span>](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md)
