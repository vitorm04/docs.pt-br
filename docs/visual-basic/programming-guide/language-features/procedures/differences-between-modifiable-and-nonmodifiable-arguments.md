---
title: "Diferenças entre argumentos modificável e não modificável (Visual Basic) | Documentos do Microsoft"
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
- procedures, arguments
- procedure arguments
- arguments [Visual Basic], nonmodifiable
- Visual Basic code, procedures
- arguments [Visual Basic], modifiable
ms.assetid: 87b2df69-e1f7-4657-9caf-b3f48d693428
caps.latest.revision: 16
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
ms.openlocfilehash: bcee3f7efab05d352c839252b4804e4d656384d7
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="differences-between-modifiable-and-nonmodifiable-arguments-visual-basic"></a><span data-ttu-id="9e167-102">Diferenças entre argumentos modificáveis e não modificáveis (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9e167-102">Differences Between Modifiable and Nonmodifiable Arguments (Visual Basic)</span></span>
<span data-ttu-id="9e167-103">Quando você chama um procedimento, você normalmente passa um ou mais argumentos para ele.</span><span class="sxs-lookup"><span data-stu-id="9e167-103">When you call a procedure, you typically pass one or more arguments to it.</span></span> <span data-ttu-id="9e167-104">Cada argumento corresponde a um elemento de programação subjacente.</span><span class="sxs-lookup"><span data-stu-id="9e167-104">Each argument corresponds to an underlying programming element.</span></span> <span data-ttu-id="9e167-105">Os elementos subjacentes e os próprios argumentos podem ser modificáveis ou não modificáveis.</span><span class="sxs-lookup"><span data-stu-id="9e167-105">Both the underlying elements and the arguments themselves can be either modifiable or nonmodifiable.</span></span>  
  
## <a name="modifiable-and-nonmodifiable-elements"></a><span data-ttu-id="9e167-106">Elementos modificáveis e não modificáveis</span><span class="sxs-lookup"><span data-stu-id="9e167-106">Modifiable and Nonmodifiable Elements</span></span>  
 <span data-ttu-id="9e167-107">Um elemento de programação pode ser um *elemento modificável*, que pode ter seu valor alterado, ou um *elemento não modificável*, que tem um valor fixo após ele ter sido criado.</span><span class="sxs-lookup"><span data-stu-id="9e167-107">A programming element can be either a *modifiable element*, which can have its value changed, or a *nonmodifiable element*, which has a fixed value once it has been created.</span></span>  
  
 <span data-ttu-id="9e167-108">A tabela a seguir lista os elementos de programação modificáveis e não modificáveis.</span><span class="sxs-lookup"><span data-stu-id="9e167-108">The following table lists modifiable and nonmodifiable programming elements.</span></span>  
  
|<span data-ttu-id="9e167-109">Elementos modificáveis</span><span class="sxs-lookup"><span data-stu-id="9e167-109">Modifiable elements</span></span>|<span data-ttu-id="9e167-110">Elementos não modificáveis</span><span class="sxs-lookup"><span data-stu-id="9e167-110">Nonmodifiable elements</span></span>|  
|-------------------------|----------------------------|  
|<span data-ttu-id="9e167-111">Variáveis locais (declaradas dentro de procedimentos), incluindo variáveis de objeto, exceto para somente leitura</span><span class="sxs-lookup"><span data-stu-id="9e167-111">Local variables (declared inside procedures), including object variables, except for read-only</span></span>|<span data-ttu-id="9e167-112">Variáveis somente leitura, campos e propriedades</span><span class="sxs-lookup"><span data-stu-id="9e167-112">Read-only variables, fields, and properties</span></span>|  
|<span data-ttu-id="9e167-113">Campos (membro variáveis de módulos, classes e estruturas), exceto para somente leitura</span><span class="sxs-lookup"><span data-stu-id="9e167-113">Fields (member variables of modules, classes, and structures), except for read-only</span></span>|<span data-ttu-id="9e167-114">Literais e constantes</span><span class="sxs-lookup"><span data-stu-id="9e167-114">Constants and literals</span></span>|  
|<span data-ttu-id="9e167-115">Propriedades, exceto para somente leitura</span><span class="sxs-lookup"><span data-stu-id="9e167-115">Properties, except for read-only</span></span>|<span data-ttu-id="9e167-116">Membros de enumeração</span><span class="sxs-lookup"><span data-stu-id="9e167-116">Enumeration members</span></span>|  
|<span data-ttu-id="9e167-117">Elementos de matriz</span><span class="sxs-lookup"><span data-stu-id="9e167-117">Array elements</span></span>|<span data-ttu-id="9e167-118">Expressões (mesmo se seus elementos são modificáveis)</span><span class="sxs-lookup"><span data-stu-id="9e167-118">Expressions (even if their elements are modifiable)</span></span>|  
  
## <a name="modifiable-and-nonmodifiable-arguments"></a><span data-ttu-id="9e167-119">Argumentos modificável e não modificável</span><span class="sxs-lookup"><span data-stu-id="9e167-119">Modifiable and Nonmodifiable Arguments</span></span>  
 <span data-ttu-id="9e167-120">A *argumento modificável* é uma com um elemento subjacente modificável.</span><span class="sxs-lookup"><span data-stu-id="9e167-120">A *modifiable argument* is one with a modifiable underlying element.</span></span> <span data-ttu-id="9e167-121">O código de chamada pode armazenar um novo valor a qualquer momento, e se você passar o argumento [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), o código no procedimento também pode modificar o elemento subjacente no código de chamada.</span><span class="sxs-lookup"><span data-stu-id="9e167-121">The calling code can store a new value at any time, and if you pass the argument [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), the code in the procedure can also modify the underlying element in the calling code.</span></span>  
  
 <span data-ttu-id="9e167-122">A *argumento não modificável* tem um elemento subjacente não modificável ou é passado [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md).</span><span class="sxs-lookup"><span data-stu-id="9e167-122">A *nonmodifiable argument* either has a nonmodifiable underlying element or is passed [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md).</span></span> <span data-ttu-id="9e167-123">O procedimento não pode modificar o elemento subjacente no código de chamada, mesmo se ele for um elemento modificável.</span><span class="sxs-lookup"><span data-stu-id="9e167-123">The procedure cannot modify the underlying element in the calling code, even if it is a modifiable element.</span></span> <span data-ttu-id="9e167-124">Se for um elemento não modificável, o código de chamada não pode modificá-lo.</span><span class="sxs-lookup"><span data-stu-id="9e167-124">If it is a nonmodifiable element, the calling code itself cannot modify it.</span></span>  
  
 <span data-ttu-id="9e167-125">O procedimento chamado pode modificar sua cópia local de um argumento não modificável, mas essa modificação não afeta o elemento subjacente no código de chamada.</span><span class="sxs-lookup"><span data-stu-id="9e167-125">The called procedure might modify its local copy of a nonmodifiable argument, but that modification does not affect the underlying element in the calling code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e167-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9e167-126">See Also</span></span>  
 <span data-ttu-id="9e167-127">[Procedimentos](./index.md) </span><span class="sxs-lookup"><span data-stu-id="9e167-127">[Procedures](./index.md) </span></span>  
<span data-ttu-id="9e167-128"> [Argumentos e parâmetros de procedimento](./procedure-parameters-and-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="9e167-128"> [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md) </span></span>  
<span data-ttu-id="9e167-129"> [Como: passar argumentos para um procedimento](./how-to-pass-arguments-to-a-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="9e167-129"> [How to: Pass Arguments to a Procedure](./how-to-pass-arguments-to-a-procedure.md) </span></span>  
<span data-ttu-id="9e167-130"> [Passando argumentos por valor e por referência](./passing-arguments-by-value-and-by-reference.md) </span><span class="sxs-lookup"><span data-stu-id="9e167-130"> [Passing Arguments by Value and by Reference](./passing-arguments-by-value-and-by-reference.md) </span></span>  
<span data-ttu-id="9e167-131"> [Diferenças entre passar um argumento por valor e por referência](./differences-between-passing-an-argument-by-value-and-by-reference.md) </span><span class="sxs-lookup"><span data-stu-id="9e167-131"> [Differences Between Passing an Argument By Value and By Reference](./differences-between-passing-an-argument-by-value-and-by-reference.md) </span></span>  
<span data-ttu-id="9e167-132"> [Como: alterar o valor de um argumento de procedimento](./how-to-change-the-value-of-a-procedure-argument.md) </span><span class="sxs-lookup"><span data-stu-id="9e167-132"> [How to: Change the Value of a Procedure Argument](./how-to-change-the-value-of-a-procedure-argument.md) </span></span>  
<span data-ttu-id="9e167-133"> [Como: proteger um argumento de procedimento contra alterações de valor](./how-to-protect-a-procedure-argument-against-value-changes.md) </span><span class="sxs-lookup"><span data-stu-id="9e167-133"> [How to: Protect a Procedure Argument Against Value Changes](./how-to-protect-a-procedure-argument-against-value-changes.md) </span></span>  
<span data-ttu-id="9e167-134"> [Como: forçar um argumento a ser passado por valor](./how-to-force-an-argument-to-be-passed-by-value.md) </span><span class="sxs-lookup"><span data-stu-id="9e167-134"> [How to: Force an Argument to Be Passed by Value](./how-to-force-an-argument-to-be-passed-by-value.md) </span></span>  
<span data-ttu-id="9e167-135"> [Passando argumentos por posição e nome](./passing-arguments-by-position-and-by-name.md) </span><span class="sxs-lookup"><span data-stu-id="9e167-135"> [Passing Arguments by Position and by Name](./passing-arguments-by-position-and-by-name.md) </span></span>  
<span data-ttu-id="9e167-136"> [Tipos de Valor e Tipos de Referência](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)</span><span class="sxs-lookup"><span data-stu-id="9e167-136"> [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)</span></span>
