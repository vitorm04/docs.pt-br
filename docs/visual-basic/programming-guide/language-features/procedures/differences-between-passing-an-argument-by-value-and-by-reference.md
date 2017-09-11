---
title: "Diferenças entre passar um argumento por valor e por referência (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- ByRef keyword, passing arguments by reference
- Visual Basic code, procedures
- procedures, passing arguments
- ByVal keyword, passing arguments by value
- arguments [Visual Basic], passing by value or by reference
ms.assetid: 5f5c38fe-3e2d-494c-8fff-f4025b55ec93
caps.latest.revision: 14
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
ms.openlocfilehash: 706c64cd316791a748e2b68fe406e34084b04d5a
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="differences-between-passing-an-argument-by-value-and-by-reference-visual-basic"></a><span data-ttu-id="9392a-102">Diferenças entre passar um argumento por valor e por referência (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9392a-102">Differences Between Passing an Argument By Value and By Reference (Visual Basic)</span></span>
<span data-ttu-id="9392a-103">Quando você passar um ou mais argumentos para um procedimento, cada argumento corresponde a um elemento de programação subjacente no código de chamada.</span><span class="sxs-lookup"><span data-stu-id="9392a-103">When you pass one or more arguments to a procedure, each argument corresponds to an underlying programming element in the calling code.</span></span> <span data-ttu-id="9392a-104">Você pode passar o valor desse elemento ou uma referência a ele.</span><span class="sxs-lookup"><span data-stu-id="9392a-104">You can pass either the value of this underlying element, or a reference to it.</span></span> <span data-ttu-id="9392a-105">Isso é conhecido como o *mecanismo de passagem*.</span><span class="sxs-lookup"><span data-stu-id="9392a-105">This is known as the *passing mechanism*.</span></span>  
  
## <a name="passing-by-value"></a><span data-ttu-id="9392a-106">Passagem por valor</span><span class="sxs-lookup"><span data-stu-id="9392a-106">Passing by Value</span></span>  
 <span data-ttu-id="9392a-107">Passar um argumento *pelo valor* especificando o [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) palavra-chave para o parâmetro correspondente na definição do procedimento.</span><span class="sxs-lookup"><span data-stu-id="9392a-107">You pass an argument *by value* by specifying the [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) keyword for the corresponding parameter in the procedure definition.</span></span> <span data-ttu-id="9392a-108">Quando você usa este mecanismo de passagem, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] copia o valor do elemento de programação subjacente em uma variável local no procedimento.</span><span class="sxs-lookup"><span data-stu-id="9392a-108">When you use this passing mechanism, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] copies the value of the underlying programming element into a local variable in the procedure.</span></span> <span data-ttu-id="9392a-109">O código do procedimento não tem nenhum acesso ao elemento subjacente no código de chamada.</span><span class="sxs-lookup"><span data-stu-id="9392a-109">The procedure code does not have any access to the underlying element in the calling code.</span></span>  
  
## <a name="passing-by-reference"></a><span data-ttu-id="9392a-110">Passagem por referência</span><span class="sxs-lookup"><span data-stu-id="9392a-110">Passing by Reference</span></span>  
 <span data-ttu-id="9392a-111">Passar um argumento *por referência* especificando o [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) palavra-chave para o parâmetro correspondente na definição do procedimento.</span><span class="sxs-lookup"><span data-stu-id="9392a-111">You pass an argument *by reference* by specifying the [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) keyword for the corresponding parameter in the procedure definition.</span></span> <span data-ttu-id="9392a-112">Quando você usa este mecanismo de passagem, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] fornece o procedimento uma referência direta ao elemento de programação subjacente no código de chamada.</span><span class="sxs-lookup"><span data-stu-id="9392a-112">When you use this passing mechanism, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] gives the procedure a direct reference to the underlying programming element in the calling code.</span></span>  
  
## <a name="passing-mechanism-and-element-type"></a><span data-ttu-id="9392a-113">Mecanismo de passagem e tipo de elemento</span><span class="sxs-lookup"><span data-stu-id="9392a-113">Passing Mechanism and Element Type</span></span>  
 <span data-ttu-id="9392a-114">A escolha do mecanismo de passagem não é o mesmo que a classificação de tipo do elemento.</span><span class="sxs-lookup"><span data-stu-id="9392a-114">The choice of passing mechanism is not the same as the classification of the underlying element type.</span></span> <span data-ttu-id="9392a-115">Passagem por valor ou referência se refere ao que [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] fornece ao código do procedimento.</span><span class="sxs-lookup"><span data-stu-id="9392a-115">Passing by value or by reference refers to what [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] supplies to the procedure code.</span></span> <span data-ttu-id="9392a-116">Um tipo de valor ou referência se refere a como um elemento de programação é armazenado na memória.</span><span class="sxs-lookup"><span data-stu-id="9392a-116">A value type or reference type refers to how a programming element is stored in memory.</span></span>  
  
 <span data-ttu-id="9392a-117">No entanto, o mecanismo de passagem e o tipo de elemento são inter-relacionados.</span><span class="sxs-lookup"><span data-stu-id="9392a-117">However, the passing mechanism and element type are interrelated.</span></span> <span data-ttu-id="9392a-118">O valor de um tipo de referência é um ponteiro para os dados em outro lugar na memória.</span><span class="sxs-lookup"><span data-stu-id="9392a-118">The value of a reference type is a pointer to the data elsewhere in memory.</span></span> <span data-ttu-id="9392a-119">Isso significa que quando você passa um tipo de referência por valor, o código do procedimento tem um ponteiro para os dados do elemento, mesmo que ele não pode acessar o elemento subjacente.</span><span class="sxs-lookup"><span data-stu-id="9392a-119">This means that when you pass a reference type by value, the procedure code has a pointer to the underlying element's data, even though it cannot access the underlying element itself.</span></span> <span data-ttu-id="9392a-120">Por exemplo, se o elemento é uma variável de matriz, o código do procedimento não tem acesso à variável em si, mas ele pode acessar os membros da matriz.</span><span class="sxs-lookup"><span data-stu-id="9392a-120">For example, if the element is an array variable, the procedure code does not have access to the variable itself, but it can access the array members.</span></span>  
  
## <a name="ability-to-modify"></a><span data-ttu-id="9392a-121">Capacidade de modificar</span><span class="sxs-lookup"><span data-stu-id="9392a-121">Ability to Modify</span></span>  
 <span data-ttu-id="9392a-122">Quando você passa um elemento não modificável como um argumento, o procedimento nunca pode modificá-lo no código de chamada, se é passado `ByVal` ou `ByRef`.</span><span class="sxs-lookup"><span data-stu-id="9392a-122">When you pass a nonmodifiable element as an argument, the procedure can never modify it in the calling code, whether it is passed `ByVal` or `ByRef`.</span></span>  
  
 <span data-ttu-id="9392a-123">Para um elemento modificável, a tabela a seguir resume a interação entre o tipo de elemento e o mecanismo de passagem.</span><span class="sxs-lookup"><span data-stu-id="9392a-123">For a modifiable element, the following table summarizes the interaction between the element type and the passing mechanism.</span></span>  
  
|<span data-ttu-id="9392a-124">Tipo de elemento</span><span class="sxs-lookup"><span data-stu-id="9392a-124">Element type</span></span>|<span data-ttu-id="9392a-125">Passado`ByVal`</span><span class="sxs-lookup"><span data-stu-id="9392a-125">Passed `ByVal`</span></span>|<span data-ttu-id="9392a-126">Passado`ByRef`</span><span class="sxs-lookup"><span data-stu-id="9392a-126">Passed `ByRef`</span></span>|  
|------------------|--------------------|--------------------|  
|<span data-ttu-id="9392a-127">Tipo de valor (contém apenas um valor)</span><span class="sxs-lookup"><span data-stu-id="9392a-127">Value type (contains only a value)</span></span>|<span data-ttu-id="9392a-128">O procedimento não pode alterar a variável ou qualquer um de seus membros.</span><span class="sxs-lookup"><span data-stu-id="9392a-128">The procedure cannot change the variable or any of its members.</span></span>|<span data-ttu-id="9392a-129">O procedimento pode mudar a variável e seus membros.</span><span class="sxs-lookup"><span data-stu-id="9392a-129">The procedure can change the variable and its members.</span></span>|  
|<span data-ttu-id="9392a-130">Tipo de referência (contém um ponteiro para uma instância de classe ou estrutura)</span><span class="sxs-lookup"><span data-stu-id="9392a-130">Reference type (contains a pointer to a class or structure instance)</span></span>|<span data-ttu-id="9392a-131">O procedimento não é possível alterar a variável mas pode mudar membros da instância para qual ele aponta.</span><span class="sxs-lookup"><span data-stu-id="9392a-131">The procedure cannot change the variable but can change members of the instance to which it points.</span></span>|<span data-ttu-id="9392a-132">O procedimento pode alterar a variável e membros da instância para qual ele aponta.</span><span class="sxs-lookup"><span data-stu-id="9392a-132">The procedure can change the variable and members of the instance to which it points.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9392a-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9392a-133">See Also</span></span>  
 <span data-ttu-id="9392a-134">[Procedimentos](./index.md) </span><span class="sxs-lookup"><span data-stu-id="9392a-134">[Procedures](./index.md) </span></span>  
<span data-ttu-id="9392a-135"> [Argumentos e parâmetros de procedimento](./procedure-parameters-and-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="9392a-135"> [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md) </span></span>  
<span data-ttu-id="9392a-136"> [Como: passar argumentos para um procedimento](./how-to-pass-arguments-to-a-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="9392a-136"> [How to: Pass Arguments to a Procedure](./how-to-pass-arguments-to-a-procedure.md) </span></span>  
<span data-ttu-id="9392a-137"> [Passando argumentos por valor e por referência](./passing-arguments-by-value-and-by-reference.md) </span><span class="sxs-lookup"><span data-stu-id="9392a-137"> [Passing Arguments by Value and by Reference](./passing-arguments-by-value-and-by-reference.md) </span></span>  
<span data-ttu-id="9392a-138"> [Diferenças entre argumentos modificável e não modificável](./differences-between-modifiable-and-nonmodifiable-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="9392a-138"> [Differences Between Modifiable and Nonmodifiable Arguments](./differences-between-modifiable-and-nonmodifiable-arguments.md) </span></span>  
<span data-ttu-id="9392a-139"> [Como: alterar o valor de um argumento de procedimento](./how-to-change-the-value-of-a-procedure-argument.md) </span><span class="sxs-lookup"><span data-stu-id="9392a-139"> [How to: Change the Value of a Procedure Argument](./how-to-change-the-value-of-a-procedure-argument.md) </span></span>  
<span data-ttu-id="9392a-140"> [Como: proteger um argumento de procedimento contra alterações de valor](./how-to-protect-a-procedure-argument-against-value-changes.md) </span><span class="sxs-lookup"><span data-stu-id="9392a-140"> [How to: Protect a Procedure Argument Against Value Changes](./how-to-protect-a-procedure-argument-against-value-changes.md) </span></span>  
<span data-ttu-id="9392a-141"> [Como: forçar um argumento a ser passado por valor](./how-to-force-an-argument-to-be-passed-by-value.md) </span><span class="sxs-lookup"><span data-stu-id="9392a-141"> [How to: Force an Argument to Be Passed by Value](./how-to-force-an-argument-to-be-passed-by-value.md) </span></span>  
<span data-ttu-id="9392a-142"> [Passando argumentos por posição e nome](./passing-arguments-by-position-and-by-name.md) </span><span class="sxs-lookup"><span data-stu-id="9392a-142"> [Passing Arguments by Position and by Name](./passing-arguments-by-position-and-by-name.md) </span></span>  
<span data-ttu-id="9392a-143"> [Tipos de Valor e Tipos de Referência](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)</span><span class="sxs-lookup"><span data-stu-id="9392a-143"> [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)</span></span>
