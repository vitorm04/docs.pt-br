---
title: Como controlar a disponibilidade de uma variável
ms.date: 07/20/2015
helpviewer_keywords:
- access levels, declared elements
- Private keyword [Visual Basic], accessing variables
- access levels, variables
- Public keyword [Visual Basic], accessing variables
- Friend keyword [Visual Basic], accessing variables
- variables [Visual Basic], access level
- declared elements [Visual Basic], access level
- Protected keyword [Visual Basic], accessing variables
ms.assetid: eaf4f073-7922-43ce-ae1e-90ff376ae947
ms.openlocfilehash: 886b57909cf6ba25dbaceea5c5f06eb4e3ba6f1f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345387"
---
# <a name="how-to-control-the-availability-of-a-variable-visual-basic"></a><span data-ttu-id="a1dcd-102">Como controlar a disponibilidade de uma variável (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a1dcd-102">How to: Control the Availability of a Variable (Visual Basic)</span></span>
<span data-ttu-id="a1dcd-103">You control the availability of a variable by specifying its *access level*.</span><span class="sxs-lookup"><span data-stu-id="a1dcd-103">You control the availability of a variable by specifying its *access level*.</span></span> <span data-ttu-id="a1dcd-104">The access level determines what code has permission to read or write to the variable.</span><span class="sxs-lookup"><span data-stu-id="a1dcd-104">The access level determines what code has permission to read or write to the variable.</span></span>  
  
- <span data-ttu-id="a1dcd-105">*Member variables* (defined at module level and outside any procedure) default to public access, which means any code that can see them can access them.</span><span class="sxs-lookup"><span data-stu-id="a1dcd-105">*Member variables* (defined at module level and outside any procedure) default to public access, which means any code that can see them can access them.</span></span> <span data-ttu-id="a1dcd-106">You can change this by specifying an access modifier.</span><span class="sxs-lookup"><span data-stu-id="a1dcd-106">You can change this by specifying an access modifier.</span></span>  
  
- <span data-ttu-id="a1dcd-107">*Local variables* (defined inside a procedure) nominally have public access, although only code within their procedure can access them.</span><span class="sxs-lookup"><span data-stu-id="a1dcd-107">*Local variables* (defined inside a procedure) nominally have public access, although only code within their procedure can access them.</span></span> <span data-ttu-id="a1dcd-108">You cannot change the access level of a local variable, but you can change the access level of the procedure that contains it.</span><span class="sxs-lookup"><span data-stu-id="a1dcd-108">You cannot change the access level of a local variable, but you can change the access level of the procedure that contains it.</span></span>  
  
 <span data-ttu-id="a1dcd-109">For more information, see [Access levels in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="a1dcd-109">For more information, see [Access levels in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
## <a name="private-and-public-access"></a><span data-ttu-id="a1dcd-110">Private and Public Access</span><span class="sxs-lookup"><span data-stu-id="a1dcd-110">Private and Public Access</span></span>  
  
#### <a name="to-make-a-variable-accessible-only-from-within-its-module-class-or-structure"></a><span data-ttu-id="a1dcd-111">To make a variable accessible only from within its module, class, or structure</span><span class="sxs-lookup"><span data-stu-id="a1dcd-111">To make a variable accessible only from within its module, class, or structure</span></span>  
  
1. <span data-ttu-id="a1dcd-112">Place the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) for the variable inside the module, class, or structure, but outside any procedure.</span><span class="sxs-lookup"><span data-stu-id="a1dcd-112">Place the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) for the variable inside the module, class, or structure, but outside any procedure.</span></span>  
  
2. <span data-ttu-id="a1dcd-113">Include the [Private](../../../../visual-basic/language-reference/modifiers/private.md) keyword in the `Dim` statement.</span><span class="sxs-lookup"><span data-stu-id="a1dcd-113">Include the [Private](../../../../visual-basic/language-reference/modifiers/private.md) keyword in the `Dim` statement.</span></span>  
  
     <span data-ttu-id="a1dcd-114">You can read or write to the variable from anywhere within the module, class, or structure, but not from outside it.</span><span class="sxs-lookup"><span data-stu-id="a1dcd-114">You can read or write to the variable from anywhere within the module, class, or structure, but not from outside it.</span></span>  
  
#### <a name="to-make-a-variable-accessible-from-any-code-that-can-see-it"></a><span data-ttu-id="a1dcd-115">To make a variable accessible from any code that can see it</span><span class="sxs-lookup"><span data-stu-id="a1dcd-115">To make a variable accessible from any code that can see it</span></span>  
  
1. <span data-ttu-id="a1dcd-116">For a member variable, place the `Dim` statement for the variable inside a module, class, or structure, but outside any procedure.</span><span class="sxs-lookup"><span data-stu-id="a1dcd-116">For a member variable, place the `Dim` statement for the variable inside a module, class, or structure, but outside any procedure.</span></span>  
  
2. <span data-ttu-id="a1dcd-117">Include the [Public](../../../../visual-basic/language-reference/modifiers/public.md) keyword in the `Dim` statement.</span><span class="sxs-lookup"><span data-stu-id="a1dcd-117">Include the [Public](../../../../visual-basic/language-reference/modifiers/public.md) keyword in the `Dim` statement.</span></span>  
  
     <span data-ttu-id="a1dcd-118">You can read or write to the variable from any code that interoperates with your assembly.</span><span class="sxs-lookup"><span data-stu-id="a1dcd-118">You can read or write to the variable from any code that interoperates with your assembly.</span></span>  
  
 <span data-ttu-id="a1dcd-119">\- ou -</span><span class="sxs-lookup"><span data-stu-id="a1dcd-119">-or-</span></span>  
  
1. <span data-ttu-id="a1dcd-120">For a local variable, place the `Dim` statement for the variable inside a procedure.</span><span class="sxs-lookup"><span data-stu-id="a1dcd-120">For a local variable, place the `Dim` statement for the variable inside a procedure.</span></span>  
  
2. <span data-ttu-id="a1dcd-121">Do not include the `Public` keyword in the `Dim` statement.</span><span class="sxs-lookup"><span data-stu-id="a1dcd-121">Do not include the `Public` keyword in the `Dim` statement.</span></span>  
  
     <span data-ttu-id="a1dcd-122">You can read or write to the variable from anywhere within the procedure, but not from outside it.</span><span class="sxs-lookup"><span data-stu-id="a1dcd-122">You can read or write to the variable from anywhere within the procedure, but not from outside it.</span></span>  
  
## <a name="protected-and-friend-access"></a><span data-ttu-id="a1dcd-123">Protected and Friend Access</span><span class="sxs-lookup"><span data-stu-id="a1dcd-123">Protected and Friend Access</span></span>  
 <span data-ttu-id="a1dcd-124">You can limit the access level of a variable to its class and any derived classes, or to its assembly.</span><span class="sxs-lookup"><span data-stu-id="a1dcd-124">You can limit the access level of a variable to its class and any derived classes, or to its assembly.</span></span> <span data-ttu-id="a1dcd-125">You can also specify the union of these limitations, which allows access from code in any derived class or in any other place in the same assembly.</span><span class="sxs-lookup"><span data-stu-id="a1dcd-125">You can also specify the union of these limitations, which allows access from code in any derived class or in any other place in the same assembly.</span></span> <span data-ttu-id="a1dcd-126">You specify this union by combining the `Protected` and `Friend` keywords in the same declaration.</span><span class="sxs-lookup"><span data-stu-id="a1dcd-126">You specify this union by combining the `Protected` and `Friend` keywords in the same declaration.</span></span>  
  
#### <a name="to-make-a-variable-accessible-only-from-within-its-class-and-any-derived-classes"></a><span data-ttu-id="a1dcd-127">To make a variable accessible only from within its class and any derived classes</span><span class="sxs-lookup"><span data-stu-id="a1dcd-127">To make a variable accessible only from within its class and any derived classes</span></span>  
  
1. <span data-ttu-id="a1dcd-128">Place the `Dim` statement for the variable inside a class, but outside any procedure.</span><span class="sxs-lookup"><span data-stu-id="a1dcd-128">Place the `Dim` statement for the variable inside a class, but outside any procedure.</span></span>  
  
2. <span data-ttu-id="a1dcd-129">Include the [Protected](../../../../visual-basic/language-reference/modifiers/protected.md) keyword in the `Dim` statement.</span><span class="sxs-lookup"><span data-stu-id="a1dcd-129">Include the [Protected](../../../../visual-basic/language-reference/modifiers/protected.md) keyword in the `Dim` statement.</span></span>  
  
     <span data-ttu-id="a1dcd-130">You can read or write to the variable from anywhere within the class, as well as from within any class derived from it, but not from outside any class in the derivation chain.</span><span class="sxs-lookup"><span data-stu-id="a1dcd-130">You can read or write to the variable from anywhere within the class, as well as from within any class derived from it, but not from outside any class in the derivation chain.</span></span>  
  
#### <a name="to-make-a-variable-accessible-only-from-within-the-same-assembly"></a><span data-ttu-id="a1dcd-131">To make a variable accessible only from within the same assembly</span><span class="sxs-lookup"><span data-stu-id="a1dcd-131">To make a variable accessible only from within the same assembly</span></span>  
  
1. <span data-ttu-id="a1dcd-132">Place the `Dim` statement for the variable inside a module, class, or structure, but outside any procedure.</span><span class="sxs-lookup"><span data-stu-id="a1dcd-132">Place the `Dim` statement for the variable inside a module, class, or structure, but outside any procedure.</span></span>  
  
2. <span data-ttu-id="a1dcd-133">Include the [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) keyword in the `Dim` statement.</span><span class="sxs-lookup"><span data-stu-id="a1dcd-133">Include the [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) keyword in the `Dim` statement.</span></span>  
  
     <span data-ttu-id="a1dcd-134">You can read or write to the variable from anywhere within the module, class, or structure, as well as from any code in the same assembly, but not from outside the assembly.</span><span class="sxs-lookup"><span data-stu-id="a1dcd-134">You can read or write to the variable from anywhere within the module, class, or structure, as well as from any code in the same assembly, but not from outside the assembly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a1dcd-135">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a1dcd-135">Example</span></span>  
 <span data-ttu-id="a1dcd-136">The following example shows declarations of variables with `Public`, `Protected`, `Friend`, `Protected Friend`, and `Private` access levels.</span><span class="sxs-lookup"><span data-stu-id="a1dcd-136">The following example shows declarations of variables with `Public`, `Protected`, `Friend`, `Protected Friend`, and `Private` access levels.</span></span> <span data-ttu-id="a1dcd-137">Note that when the `Dim` statement specifies an access level, you do not need to include the `Dim` keyword.</span><span class="sxs-lookup"><span data-stu-id="a1dcd-137">Note that when the `Dim` statement specifies an access level, you do not need to include the `Dim` keyword.</span></span>  
  
```vb  
Public Class classForEverybody  
Protected Class classForMyHeirs  
Friend stringForThisProject As String  
Protected Friend stringForProjectAndHeirs As String  
Private numberForMeOnly As Integer  
```  
  
## <a name="net-framework-security"></a><span data-ttu-id="a1dcd-138">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="a1dcd-138">.NET Framework Security</span></span>  
 <span data-ttu-id="a1dcd-139">The more restrictive the access level of a variable, the smaller the chances that malicious code can make improper use of it.</span><span class="sxs-lookup"><span data-stu-id="a1dcd-139">The more restrictive the access level of a variable, the smaller the chances that malicious code can make improper use of it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1dcd-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a1dcd-140">See also</span></span>

- [<span data-ttu-id="a1dcd-141">Access levels in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a1dcd-141">Access levels in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="a1dcd-142">Instrução Dim</span><span class="sxs-lookup"><span data-stu-id="a1dcd-142">Dim Statement</span></span>](../../../../visual-basic/language-reference/statements/dim-statement.md)
- [<span data-ttu-id="a1dcd-143">Público</span><span class="sxs-lookup"><span data-stu-id="a1dcd-143">Public</span></span>](../../../../visual-basic/language-reference/modifiers/public.md)
- [<span data-ttu-id="a1dcd-144">Protegido</span><span class="sxs-lookup"><span data-stu-id="a1dcd-144">Protected</span></span>](../../../../visual-basic/language-reference/modifiers/protected.md)
- [<span data-ttu-id="a1dcd-145">Friend</span><span class="sxs-lookup"><span data-stu-id="a1dcd-145">Friend</span></span>](../../../../visual-basic/language-reference/modifiers/friend.md)
- [<span data-ttu-id="a1dcd-146">Privado</span><span class="sxs-lookup"><span data-stu-id="a1dcd-146">Private</span></span>](../../../../visual-basic/language-reference/modifiers/private.md)
