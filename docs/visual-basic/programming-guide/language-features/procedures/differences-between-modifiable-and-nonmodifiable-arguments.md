---
title: Diferenças entre argumentos modificáveis e não modificáveis (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedure arguments
- arguments [Visual Basic], nonmodifiable
- Visual Basic code, procedures
- arguments [Visual Basic], modifiable
ms.assetid: 87b2df69-e1f7-4657-9caf-b3f48d693428
ms.openlocfilehash: a880ae8c13eebd5d9d325468098e058f58d3fa71
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58826659"
---
# <a name="differences-between-modifiable-and-nonmodifiable-arguments-visual-basic"></a><span data-ttu-id="b9e9d-102">Diferenças entre argumentos modificáveis e não modificáveis (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b9e9d-102">Differences Between Modifiable and Nonmodifiable Arguments (Visual Basic)</span></span>
<span data-ttu-id="b9e9d-103">Quando você chama um procedimento, você normalmente passa um ou mais argumentos para ele.</span><span class="sxs-lookup"><span data-stu-id="b9e9d-103">When you call a procedure, you typically pass one or more arguments to it.</span></span> <span data-ttu-id="b9e9d-104">Cada argumento corresponde a um elemento de programação subjacente.</span><span class="sxs-lookup"><span data-stu-id="b9e9d-104">Each argument corresponds to an underlying programming element.</span></span> <span data-ttu-id="b9e9d-105">Os elementos subjacentes e os próprios argumentos podem ser modificável ou não modificável.</span><span class="sxs-lookup"><span data-stu-id="b9e9d-105">Both the underlying elements and the arguments themselves can be either modifiable or nonmodifiable.</span></span>  
  
## <a name="modifiable-and-nonmodifiable-elements"></a><span data-ttu-id="b9e9d-106">Elementos modificável e</span><span class="sxs-lookup"><span data-stu-id="b9e9d-106">Modifiable and Nonmodifiable Elements</span></span>  
 <span data-ttu-id="b9e9d-107">Um elemento de programação pode ser um *elemento modificável*, que pode ter seu valor alterado, ou um *elemento não modificável*, que tem um valor fixo quando ele tiver sido criado.</span><span class="sxs-lookup"><span data-stu-id="b9e9d-107">A programming element can be either a *modifiable element*, which can have its value changed, or a *nonmodifiable element*, which has a fixed value once it has been created.</span></span>  
  
 <span data-ttu-id="b9e9d-108">A tabela a seguir lista os elementos de programação modificáveis e não modificáveis.</span><span class="sxs-lookup"><span data-stu-id="b9e9d-108">The following table lists modifiable and nonmodifiable programming elements.</span></span>  
  
|<span data-ttu-id="b9e9d-109">Elementos modificáveis</span><span class="sxs-lookup"><span data-stu-id="b9e9d-109">Modifiable elements</span></span>|<span data-ttu-id="b9e9d-110">Elementos não modificáveis</span><span class="sxs-lookup"><span data-stu-id="b9e9d-110">Nonmodifiable elements</span></span>|  
|-------------------------|----------------------------|  
|<span data-ttu-id="b9e9d-111">Variáveis locais (declaradas dentro de procedimentos), incluindo variáveis de objeto, exceto para somente leitura</span><span class="sxs-lookup"><span data-stu-id="b9e9d-111">Local variables (declared inside procedures), including object variables, except for read-only</span></span>|<span data-ttu-id="b9e9d-112">Propriedades, campos e variáveis somente leitura</span><span class="sxs-lookup"><span data-stu-id="b9e9d-112">Read-only variables, fields, and properties</span></span>|  
|<span data-ttu-id="b9e9d-113">Campos (variáveis de membro de módulos, classes e estruturas), exceto para somente leitura</span><span class="sxs-lookup"><span data-stu-id="b9e9d-113">Fields (member variables of modules, classes, and structures), except for read-only</span></span>|<span data-ttu-id="b9e9d-114">Literais e constantes</span><span class="sxs-lookup"><span data-stu-id="b9e9d-114">Constants and literals</span></span>|  
|<span data-ttu-id="b9e9d-115">Propriedades, exceto para somente leitura</span><span class="sxs-lookup"><span data-stu-id="b9e9d-115">Properties, except for read-only</span></span>|<span data-ttu-id="b9e9d-116">Membros de enumeração</span><span class="sxs-lookup"><span data-stu-id="b9e9d-116">Enumeration members</span></span>|  
|<span data-ttu-id="b9e9d-117">Elementos de matriz</span><span class="sxs-lookup"><span data-stu-id="b9e9d-117">Array elements</span></span>|<span data-ttu-id="b9e9d-118">Expressões (mesmo se seus elementos são modificáveis)</span><span class="sxs-lookup"><span data-stu-id="b9e9d-118">Expressions (even if their elements are modifiable)</span></span>|  
  
## <a name="modifiable-and-nonmodifiable-arguments"></a><span data-ttu-id="b9e9d-119">Argumentos modificáveis e</span><span class="sxs-lookup"><span data-stu-id="b9e9d-119">Modifiable and Nonmodifiable Arguments</span></span>  
 <span data-ttu-id="b9e9d-120">Um *argumento modificável* é aquele com um elemento subjacente modificável.</span><span class="sxs-lookup"><span data-stu-id="b9e9d-120">A *modifiable argument* is one with a modifiable underlying element.</span></span> <span data-ttu-id="b9e9d-121">O código de chamada pode armazenar um novo valor a qualquer momento, e se você passar o argumento [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), o código no procedimento também pode modificar o elemento subjacente no código de chamada.</span><span class="sxs-lookup"><span data-stu-id="b9e9d-121">The calling code can store a new value at any time, and if you pass the argument [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), the code in the procedure can also modify the underlying element in the calling code.</span></span>  
  
 <span data-ttu-id="b9e9d-122">Um *argumento não modificável* tem um elemento subjacente não modificável ou é passado [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md).</span><span class="sxs-lookup"><span data-stu-id="b9e9d-122">A *nonmodifiable argument* either has a nonmodifiable underlying element or is passed [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md).</span></span> <span data-ttu-id="b9e9d-123">O procedimento não pode modificar o elemento subjacente no código de chamada, mesmo se for um elemento modificável.</span><span class="sxs-lookup"><span data-stu-id="b9e9d-123">The procedure cannot modify the underlying element in the calling code, even if it is a modifiable element.</span></span> <span data-ttu-id="b9e9d-124">Se for um elemento não modificável, o código de chamada em si não é possível modificá-lo.</span><span class="sxs-lookup"><span data-stu-id="b9e9d-124">If it is a nonmodifiable element, the calling code itself cannot modify it.</span></span>  
  
 <span data-ttu-id="b9e9d-125">O procedimento chamado pode modificar sua cópia local de um argumento não modificável, mas essa modificação não afeta o elemento subjacente no código de chamada.</span><span class="sxs-lookup"><span data-stu-id="b9e9d-125">The called procedure might modify its local copy of a nonmodifiable argument, but that modification does not affect the underlying element in the calling code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9e9d-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b9e9d-126">See also</span></span>

- [<span data-ttu-id="b9e9d-127">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="b9e9d-127">Procedures</span></span>](./index.md)
- [<span data-ttu-id="b9e9d-128">Parâmetros e Argumentos de Procedimento</span><span class="sxs-lookup"><span data-stu-id="b9e9d-128">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="b9e9d-129">Como: Passar argumentos para um procedimento</span><span class="sxs-lookup"><span data-stu-id="b9e9d-129">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)
- [<span data-ttu-id="b9e9d-130">Passando Argumentos por Valor e por Referência</span><span class="sxs-lookup"><span data-stu-id="b9e9d-130">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="b9e9d-131">Diferenças entre passar um argumento por valor e por referência</span><span class="sxs-lookup"><span data-stu-id="b9e9d-131">Differences Between Passing an Argument By Value and By Reference</span></span>](./differences-between-passing-an-argument-by-value-and-by-reference.md)
- [<span data-ttu-id="b9e9d-132">Como: Altere o valor de um argumento de procedimento</span><span class="sxs-lookup"><span data-stu-id="b9e9d-132">How to: Change the Value of a Procedure Argument</span></span>](./how-to-change-the-value-of-a-procedure-argument.md)
- [<span data-ttu-id="b9e9d-133">Como: Proteger um argumento de procedimento contra alterações de valor</span><span class="sxs-lookup"><span data-stu-id="b9e9d-133">How to: Protect a Procedure Argument Against Value Changes</span></span>](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [<span data-ttu-id="b9e9d-134">Como: Forçar um argumento a ser passado por valor</span><span class="sxs-lookup"><span data-stu-id="b9e9d-134">How to: Force an Argument to Be Passed by Value</span></span>](./how-to-force-an-argument-to-be-passed-by-value.md)
- [<span data-ttu-id="b9e9d-135">Passando Argumentos por Posição e Nome</span><span class="sxs-lookup"><span data-stu-id="b9e9d-135">Passing Arguments by Position and by Name</span></span>](./passing-arguments-by-position-and-by-name.md)
- [<span data-ttu-id="b9e9d-136">Tipos de Valor e Tipos de Referência</span><span class="sxs-lookup"><span data-stu-id="b9e9d-136">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
