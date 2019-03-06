---
title: O namespace ou o tipo especificado em Imports '<qualifiedelementname>' não contém nenhum membro público ou não pode ser localizado
ms.date: 07/20/2015
f1_keywords:
- bc40056
- vbc40056
helpviewer_keywords:
- BC40056
ms.assetid: b59f5754-444f-4378-9272-9678b437e84a
ms.openlocfilehash: 1873c0af7a251afd7754557f5dcb6aed13eb9f11
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57357879"
---
# <a name="namespace-or-type-specified-in-the-imports-qualifiedelementname-doesnt-contain-any-public-member-or-cannot-be-found"></a><span data-ttu-id="1f79d-102">Tipo ou Namespace especificado em Imports'\<qualifiedelementname >' não contém nenhum membro público ou não foi encontrado</span><span class="sxs-lookup"><span data-stu-id="1f79d-102">Namespace or type specified in the Imports '\<qualifiedelementname>' doesn't contain any public member or cannot be found</span></span>

<span data-ttu-id="1f79d-103">Tipo ou Namespace especificado em Imports'\<qualifiedelementname >' não contém nenhum membro público ou não foi encontrado.</span><span class="sxs-lookup"><span data-stu-id="1f79d-103">Namespace or type specified in the Imports '\<qualifiedelementname>' doesn't contain any public member or cannot be found.</span></span> <span data-ttu-id="1f79d-104">Verifique se o namespace ou o tipo é definido e contém pelo menos um membro público.</span><span class="sxs-lookup"><span data-stu-id="1f79d-104">Make sure the namespace or the type is defined and contains at least one public member.</span></span> <span data-ttu-id="1f79d-105">Verifique se que o nome do alias não contém outros aliases.</span><span class="sxs-lookup"><span data-stu-id="1f79d-105">Make sure the alias name doesn't contain other aliases.</span></span>

<span data-ttu-id="1f79d-106">Uma `Imports` declaração especifica um elemento contido que não pode ser encontrado ou não define nenhum `Public` membros.</span><span class="sxs-lookup"><span data-stu-id="1f79d-106">An `Imports` statement specifies a containing element that either cannot be found or does not define any `Public` members.</span></span>

<span data-ttu-id="1f79d-107">Um *que contém o elemento* pode ser um namespace, classe, estrutura, módulo, interface ou enumeração.</span><span class="sxs-lookup"><span data-stu-id="1f79d-107">A *containing element* can be a namespace, class, structure, module, interface, or enumeration.</span></span> <span data-ttu-id="1f79d-108">O elemento contido contém membros, como variáveis, procedimentos ou outros elementos que contém.</span><span class="sxs-lookup"><span data-stu-id="1f79d-108">The containing element contains members, such as variables, procedures, or other containing elements.</span></span>

<span data-ttu-id="1f79d-109">A finalidade de importação é permitir que seu código para acessar membros de namespace ou tipo sem ter que qualificá-los.</span><span class="sxs-lookup"><span data-stu-id="1f79d-109">The purpose of importing is to allow your code to access namespace or type members without having to qualify them.</span></span> <span data-ttu-id="1f79d-110">Seu projeto talvez seja necessário também adicionar uma referência para o namespace ou tipo.</span><span class="sxs-lookup"><span data-stu-id="1f79d-110">Your project might also need to add a reference to the namespace or type.</span></span> <span data-ttu-id="1f79d-111">Para obter mais informações, consulte "Importação de elementos que contém" na [referências a elementos declarados](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span><span class="sxs-lookup"><span data-stu-id="1f79d-111">For more information, see "Importing Containing Elements" in [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>

<span data-ttu-id="1f79d-112">Se o compilador não pode localizar o elemento contido, ele não é possível resolver as referências que usá-lo.</span><span class="sxs-lookup"><span data-stu-id="1f79d-112">If the compiler cannot find the specified containing element, then it cannot resolve references that use it.</span></span> <span data-ttu-id="1f79d-113">Se ele localiza o elemento, mas o elemento não expõe nenhum `Public` membros, então nenhuma referência pode ser bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="1f79d-113">If it finds the element but the element does not expose any `Public` members, then no reference can be successful.</span></span> <span data-ttu-id="1f79d-114">Em ambos os casos não faz sentido para o elemento de importação.</span><span class="sxs-lookup"><span data-stu-id="1f79d-114">In either case it is meaningless to import the element.</span></span>

<span data-ttu-id="1f79d-115">Tenha em mente que se você importar um elemento de recipiente e atribuir um alias de importação para ele, em seguida, é possível usar esse alias de importação para importar de outro elemento.</span><span class="sxs-lookup"><span data-stu-id="1f79d-115">Keep in mind that if you import a containing element and assign an import alias to it, then you cannot use that import alias to import another element.</span></span> <span data-ttu-id="1f79d-116">O código a seguir gera um erro do compilador.</span><span class="sxs-lookup"><span data-stu-id="1f79d-116">The following code generates a compiler error.</span></span>

```vb
Imports winfrm = System.Windows.Forms

' The following statement is INVALID  because it reuses an import alias.

Imports behave = winfrm.Design.Behavior`
```

<span data-ttu-id="1f79d-117">**ID do erro:** BC40056</span><span class="sxs-lookup"><span data-stu-id="1f79d-117">**Error ID:** BC40056</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="1f79d-118">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="1f79d-118">To correct this error</span></span>

1. <span data-ttu-id="1f79d-119">Verifique se o elemento que o contém é acessível a partir de seu projeto.</span><span class="sxs-lookup"><span data-stu-id="1f79d-119">Verify that the containing element is accessible from your project.</span></span>

2. <span data-ttu-id="1f79d-120">Verifique se que a especificação do elemento contido não inclui qualquer alias de importação da importação de outro.</span><span class="sxs-lookup"><span data-stu-id="1f79d-120">Verify that the specification of the containing element does not include any import alias from another import.</span></span>

3. <span data-ttu-id="1f79d-121">Verifique se que o elemento contêiner expõe pelo menos um `Public` membro.</span><span class="sxs-lookup"><span data-stu-id="1f79d-121">Verify that the containing element exposes at least one `Public` member.</span></span>

## <a name="see-also"></a><span data-ttu-id="1f79d-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1f79d-122">See also</span></span>

- [<span data-ttu-id="1f79d-123">Instrução Imports (Tipo e Namespace .NET)</span><span class="sxs-lookup"><span data-stu-id="1f79d-123">Imports Statement (.NET Namespace and Type)</span></span>](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [<span data-ttu-id="1f79d-124">Instrução Namespace</span><span class="sxs-lookup"><span data-stu-id="1f79d-124">Namespace Statement</span></span>](../../../visual-basic/language-reference/statements/namespace-statement.md)
- [<span data-ttu-id="1f79d-125">Público</span><span class="sxs-lookup"><span data-stu-id="1f79d-125">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)
- [<span data-ttu-id="1f79d-126">Namespaces no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1f79d-126">Namespaces in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/namespaces.md)
- [<span data-ttu-id="1f79d-127">Referências a Elementos Declarados</span><span class="sxs-lookup"><span data-stu-id="1f79d-127">References to Declared Elements</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
