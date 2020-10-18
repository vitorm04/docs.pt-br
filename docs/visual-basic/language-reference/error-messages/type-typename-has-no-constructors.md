---
title: O tipo '<typename>' não tem construtores
ms.date: 07/20/2015
f1_keywords:
- bc30251
- vbc30251
helpviewer_keywords:
- BC30251
ms.assetid: aff3e1df-abe6-4bc0-9abc-a1e70514c561
ms.openlocfilehash: 249bcb7020f26c7c43d560e91ef7a34e4dc64470
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92161173"
---
# <a name="bc30251-type-typename-has-no-constructors"></a><span data-ttu-id="7e6d5-102">BC30251: o tipo ' \<typename> ' não tem construtores</span><span class="sxs-lookup"><span data-stu-id="7e6d5-102">BC30251: Type '\<typename>' has no constructors</span></span>

<span data-ttu-id="7e6d5-103">Um tipo não suporta uma chamada para `Sub New()`.</span><span class="sxs-lookup"><span data-stu-id="7e6d5-103">A type does not support a call to `Sub New()`.</span></span> <span data-ttu-id="7e6d5-104">Uma possível causa é um compilador corrompido ou arquivo binário.</span><span class="sxs-lookup"><span data-stu-id="7e6d5-104">One possible cause is a corrupted compiler or binary file.</span></span>

 <span data-ttu-id="7e6d5-105">**ID do erro:** BC30251</span><span class="sxs-lookup"><span data-stu-id="7e6d5-105">**Error ID:** BC30251</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="7e6d5-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="7e6d5-106">To correct this error</span></span>

1. <span data-ttu-id="7e6d5-107">Se o tipo estiver em um projeto diferente ou em um arquivo referenciado, reinstale o projeto ou arquivo.</span><span class="sxs-lookup"><span data-stu-id="7e6d5-107">If the type is in a different project or in a referenced file, reinstall the project or file.</span></span>

2. <span data-ttu-id="7e6d5-108">Se o tipo estiver no mesmo projeto, recompile o assembly que contém o tipo.</span><span class="sxs-lookup"><span data-stu-id="7e6d5-108">If the type is in the same project, recompile the assembly containing the type.</span></span>

3. <span data-ttu-id="7e6d5-109">Se o erro se repetir, reinstale o compilador Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="7e6d5-109">If the error recurs, reinstall the Visual Basic compiler.</span></span>

4. <span data-ttu-id="7e6d5-110">Se o erro persistir, reúna informações sobre as circunstâncias e notifique o Microsoft Product Support Services.</span><span class="sxs-lookup"><span data-stu-id="7e6d5-110">If the error persists, gather information about the circumstances and notify Microsoft Product Support Services.</span></span>

## <a name="see-also"></a><span data-ttu-id="7e6d5-111">Veja também</span><span class="sxs-lookup"><span data-stu-id="7e6d5-111">See also</span></span>

- [<span data-ttu-id="7e6d5-112">Objetos e classes</span><span class="sxs-lookup"><span data-stu-id="7e6d5-112">Objects and Classes</span></span>](../../programming-guide/language-features/objects-and-classes/index.md)
- [<span data-ttu-id="7e6d5-113">Fale conosco</span><span class="sxs-lookup"><span data-stu-id="7e6d5-113">Talk to Us</span></span>](/visualstudio/ide/feedback-options)
