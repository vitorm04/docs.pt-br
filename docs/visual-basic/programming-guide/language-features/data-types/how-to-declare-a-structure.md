---
title: Como declarar uma estrutura
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], structures
- structure statements [Visual Basic]
- statements [Visual Basic], structure
- structures [Visual Basic], declaring
ms.assetid: d5e98381-eb81-47d4-af83-48cc534a2572
ms.openlocfilehash: 41d2d03064dea703909218de56feb863526c220b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350004"
---
# <a name="how-to-declare-a-structure-visual-basic"></a><span data-ttu-id="7063a-102">Como declarar uma estrutura (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7063a-102">How to: Declare a Structure (Visual Basic)</span></span>
<span data-ttu-id="7063a-103">You begin a structure declaration with the [Structure Statement](../../../../visual-basic/language-reference/statements/structure-statement.md), and you end it with the `End Structure` statement.</span><span class="sxs-lookup"><span data-stu-id="7063a-103">You begin a structure declaration with the [Structure Statement](../../../../visual-basic/language-reference/statements/structure-statement.md), and you end it with the `End Structure` statement.</span></span> <span data-ttu-id="7063a-104">Between these two statements you must declare at least one *element*.</span><span class="sxs-lookup"><span data-stu-id="7063a-104">Between these two statements you must declare at least one *element*.</span></span> <span data-ttu-id="7063a-105">The elements can be of any data type, but at least one must be either a nonshared variable or a nonshared, noncustom event.</span><span class="sxs-lookup"><span data-stu-id="7063a-105">The elements can be of any data type, but at least one must be either a nonshared variable or a nonshared, noncustom event.</span></span>  
  
 <span data-ttu-id="7063a-106">You cannot initialize any of the structure elements in the structure declaration.</span><span class="sxs-lookup"><span data-stu-id="7063a-106">You cannot initialize any of the structure elements in the structure declaration.</span></span> <span data-ttu-id="7063a-107">When you declare a variable to be of a structure type, you assign values to the elements by accessing them through the variable.</span><span class="sxs-lookup"><span data-stu-id="7063a-107">When you declare a variable to be of a structure type, you assign values to the elements by accessing them through the variable.</span></span>  
  
 <span data-ttu-id="7063a-108">For a discussion of the differences between structures and classes, see [Structures and Classes](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md).</span><span class="sxs-lookup"><span data-stu-id="7063a-108">For a discussion of the differences between structures and classes, see [Structures and Classes](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md).</span></span>  
  
 <span data-ttu-id="7063a-109">For demonstration purposes, consider a situation where you want to keep track of an employee's name, telephone extension, and salary.</span><span class="sxs-lookup"><span data-stu-id="7063a-109">For demonstration purposes, consider a situation where you want to keep track of an employee's name, telephone extension, and salary.</span></span> <span data-ttu-id="7063a-110">A structure allows you to do this in a single variable.</span><span class="sxs-lookup"><span data-stu-id="7063a-110">A structure allows you to do this in a single variable.</span></span>  
  
### <a name="to-declare-a-structure"></a><span data-ttu-id="7063a-111">To declare a structure</span><span class="sxs-lookup"><span data-stu-id="7063a-111">To declare a structure</span></span>  
  
1. <span data-ttu-id="7063a-112">Create the beginning and ending statements for the structure.</span><span class="sxs-lookup"><span data-stu-id="7063a-112">Create the beginning and ending statements for the structure.</span></span>  
  
     <span data-ttu-id="7063a-113">You can specify the access level of a structure using the [Public](../../../../visual-basic/language-reference/modifiers/public.md), [Protected](../../../../visual-basic/language-reference/modifiers/protected.md), [Friend](../../../../visual-basic/language-reference/modifiers/friend.md), or [Private](../../../../visual-basic/language-reference/modifiers/private.md) keyword, or you can let it default to `Public`.</span><span class="sxs-lookup"><span data-stu-id="7063a-113">You can specify the access level of a structure using the [Public](../../../../visual-basic/language-reference/modifiers/public.md), [Protected](../../../../visual-basic/language-reference/modifiers/protected.md), [Friend](../../../../visual-basic/language-reference/modifiers/friend.md), or [Private](../../../../visual-basic/language-reference/modifiers/private.md) keyword, or you can let it default to `Public`.</span></span>  
  
    ```vb  
    Private Structure employee  
    End Structure  
    ```  
  
2. <span data-ttu-id="7063a-114">Add elements to the body of the structure.</span><span class="sxs-lookup"><span data-stu-id="7063a-114">Add elements to the body of the structure.</span></span>  
  
     <span data-ttu-id="7063a-115">A structure must have at least one element.</span><span class="sxs-lookup"><span data-stu-id="7063a-115">A structure must have at least one element.</span></span> <span data-ttu-id="7063a-116">You must declare every element and specify an access level for it.</span><span class="sxs-lookup"><span data-stu-id="7063a-116">You must declare every element and specify an access level for it.</span></span> <span data-ttu-id="7063a-117">If you use the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) without any keywords, the accessibility defaults to `Public`.</span><span class="sxs-lookup"><span data-stu-id="7063a-117">If you use the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) without any keywords, the accessibility defaults to `Public`.</span></span>  
  
    ```vb  
    Private Structure employee  
        Public givenName As String  
        Public familyName As String  
        Public phoneExtension As Long  
        Private salary As Decimal  
        Public Sub giveRaise(raise As Double)  
            salary *= raise  
        End Sub  
        Public Event salaryReviewTime()  
    End Structure  
    ```  
  
     <span data-ttu-id="7063a-118">The `salary` field in the preceding example is `Private`, which means it is inaccessible outside the structure, even from the containing class.</span><span class="sxs-lookup"><span data-stu-id="7063a-118">The `salary` field in the preceding example is `Private`, which means it is inaccessible outside the structure, even from the containing class.</span></span> <span data-ttu-id="7063a-119">However, the `giveRaise` procedure is `Public`, so it can be called from outside the structure.</span><span class="sxs-lookup"><span data-stu-id="7063a-119">However, the `giveRaise` procedure is `Public`, so it can be called from outside the structure.</span></span> <span data-ttu-id="7063a-120">Similarly, you can raise the `salaryReviewTime` event from outside the structure.</span><span class="sxs-lookup"><span data-stu-id="7063a-120">Similarly, you can raise the `salaryReviewTime` event from outside the structure.</span></span>  
  
     <span data-ttu-id="7063a-121">In addition to variables, `Sub` procedures, and events, you can also define constants, `Function` procedures, and properties in a structure.</span><span class="sxs-lookup"><span data-stu-id="7063a-121">In addition to variables, `Sub` procedures, and events, you can also define constants, `Function` procedures, and properties in a structure.</span></span> <span data-ttu-id="7063a-122">You can designate at most one property as the *default property*, provided it takes at least one argument.</span><span class="sxs-lookup"><span data-stu-id="7063a-122">You can designate at most one property as the *default property*, provided it takes at least one argument.</span></span> <span data-ttu-id="7063a-123">You can handle an event with a [Shared](../../../../visual-basic/language-reference/modifiers/shared.md)`Sub` procedure.</span><span class="sxs-lookup"><span data-stu-id="7063a-123">You can handle an event with a [Shared](../../../../visual-basic/language-reference/modifiers/shared.md)`Sub` procedure.</span></span> <span data-ttu-id="7063a-124">For more information, see [How to: Declare and Call a Default Property in Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md).</span><span class="sxs-lookup"><span data-stu-id="7063a-124">For more information, see [How to: Declare and Call a Default Property in Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7063a-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7063a-125">See also</span></span>

- [<span data-ttu-id="7063a-126">Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="7063a-126">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [<span data-ttu-id="7063a-127">Tipos de Dados Elementares</span><span class="sxs-lookup"><span data-stu-id="7063a-127">Elementary Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [<span data-ttu-id="7063a-128">Tipos de Dados Compostos</span><span class="sxs-lookup"><span data-stu-id="7063a-128">Composite Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)
- [<span data-ttu-id="7063a-129">Tipos de Valor e Tipos de Referência</span><span class="sxs-lookup"><span data-stu-id="7063a-129">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [<span data-ttu-id="7063a-130">Estruturas</span><span class="sxs-lookup"><span data-stu-id="7063a-130">Structures</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="7063a-131">Solução de problemas de Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="7063a-131">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [<span data-ttu-id="7063a-132">Variáveis de Estrutura</span><span class="sxs-lookup"><span data-stu-id="7063a-132">Structure Variables</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structure-variables.md)
- [<span data-ttu-id="7063a-133">Estruturas e Outros Elementos de Programação</span><span class="sxs-lookup"><span data-stu-id="7063a-133">Structures and Other Programming Elements</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md)
- [<span data-ttu-id="7063a-134">Estruturas e Classes</span><span class="sxs-lookup"><span data-stu-id="7063a-134">Structures and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)
- [<span data-ttu-id="7063a-135">Tipo de Dados Definido pelo Usuário</span><span class="sxs-lookup"><span data-stu-id="7063a-135">User-Defined Data Type</span></span>](../../../../visual-basic/language-reference/data-types/user-defined-data-type.md)
