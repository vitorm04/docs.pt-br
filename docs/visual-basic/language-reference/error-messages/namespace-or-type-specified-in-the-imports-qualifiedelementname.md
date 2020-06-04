---
title: O namespace ou o tipo especificado em Imports '<qualifiedelementname>' não contém nenhum membro público ou não pode ser localizado
ms.date: 07/20/2015
f1_keywords:
- bc40056
- vbc40056
helpviewer_keywords:
- BC40056
ms.assetid: b59f5754-444f-4378-9272-9678b437e84a
ms.openlocfilehash: 8675d9c3b202200c89e12e7a5f51a19d9e3e0e64
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409459"
---
# <a name="namespace-or-type-specified-in-the-imports-qualifiedelementname-doesnt-contain-any-public-member-or-cannot-be-found"></a><span data-ttu-id="23dd0-102">O namespace ou o tipo especificado em Imports '\<qualifiedelementname>' não contém nenhum membro público ou não pode ser localizado</span><span class="sxs-lookup"><span data-stu-id="23dd0-102">Namespace or type specified in the Imports '\<qualifiedelementname>' doesn't contain any public member or cannot be found</span></span>

<span data-ttu-id="23dd0-103">O namespace ou o tipo especificado em Imports ' \<qualifiedelementname> ' não contém nenhum membro público ou não pode ser encontrado.</span><span class="sxs-lookup"><span data-stu-id="23dd0-103">Namespace or type specified in the Imports '\<qualifiedelementname>' doesn't contain any public member or cannot be found.</span></span> <span data-ttu-id="23dd0-104">Verifique se o namespace ou o tipo está definido e contém pelo menos um membro público.</span><span class="sxs-lookup"><span data-stu-id="23dd0-104">Make sure the namespace or the type is defined and contains at least one public member.</span></span> <span data-ttu-id="23dd0-105">Verifique se o nome do alias não contém outros aliases.</span><span class="sxs-lookup"><span data-stu-id="23dd0-105">Make sure the alias name doesn't contain other aliases.</span></span>

<span data-ttu-id="23dd0-106">Uma `Imports` instrução especifica um elemento contido que não pode ser encontrado ou não define nenhum `Public` membro.</span><span class="sxs-lookup"><span data-stu-id="23dd0-106">An `Imports` statement specifies a containing element that either cannot be found or does not define any `Public` members.</span></span>

<span data-ttu-id="23dd0-107">Um *elemento recipiente* pode ser um namespace, uma classe, uma estrutura, um módulo, uma interface ou uma enumeração.</span><span class="sxs-lookup"><span data-stu-id="23dd0-107">A *containing element* can be a namespace, class, structure, module, interface, or enumeration.</span></span> <span data-ttu-id="23dd0-108">O elemento contentor contém membros, como variáveis, procedimentos ou outros elementos que os contêm.</span><span class="sxs-lookup"><span data-stu-id="23dd0-108">The containing element contains members, such as variables, procedures, or other containing elements.</span></span>

<span data-ttu-id="23dd0-109">A finalidade da importação é permitir que seu código acesse namespace ou membros de tipo sem precisar qualificá-los.</span><span class="sxs-lookup"><span data-stu-id="23dd0-109">The purpose of importing is to allow your code to access namespace or type members without having to qualify them.</span></span> <span data-ttu-id="23dd0-110">Seu projeto também pode precisar adicionar uma referência ao namespace ou ao tipo.</span><span class="sxs-lookup"><span data-stu-id="23dd0-110">Your project might also need to add a reference to the namespace or type.</span></span> <span data-ttu-id="23dd0-111">Para obter mais informações, consulte "importando elementos continentes" em [referências a elementos declarados](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span><span class="sxs-lookup"><span data-stu-id="23dd0-111">For more information, see "Importing Containing Elements" in [References to Declared Elements](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>

<span data-ttu-id="23dd0-112">Se o compilador não encontrar o elemento contido especificado, ele não poderá resolver referências que o utilizam.</span><span class="sxs-lookup"><span data-stu-id="23dd0-112">If the compiler cannot find the specified containing element, then it cannot resolve references that use it.</span></span> <span data-ttu-id="23dd0-113">Se encontrar o elemento, mas o elemento não expor nenhum `Public` membro, nenhuma referência poderá ser bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="23dd0-113">If it finds the element but the element does not expose any `Public` members, then no reference can be successful.</span></span> <span data-ttu-id="23dd0-114">Em ambos os casos, não há sentido para importar o elemento.</span><span class="sxs-lookup"><span data-stu-id="23dd0-114">In either case it is meaningless to import the element.</span></span>

<span data-ttu-id="23dd0-115">Tenha em mente que, se você importar um elemento recipiente e atribuir um alias de importação a ele, não poderá usar esse alias de importação para importar outro elemento.</span><span class="sxs-lookup"><span data-stu-id="23dd0-115">Keep in mind that if you import a containing element and assign an import alias to it, then you cannot use that import alias to import another element.</span></span> <span data-ttu-id="23dd0-116">O código a seguir gera um erro do compilador.</span><span class="sxs-lookup"><span data-stu-id="23dd0-116">The following code generates a compiler error.</span></span>

```vb
Imports winfrm = System.Windows.Forms

' The following statement is INVALID  because it reuses an import alias.

Imports behave = winfrm.Design.Behavior`
```

<span data-ttu-id="23dd0-117">**ID do erro:** BC40056</span><span class="sxs-lookup"><span data-stu-id="23dd0-117">**Error ID:** BC40056</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="23dd0-118">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="23dd0-118">To correct this error</span></span>

1. <span data-ttu-id="23dd0-119">Verifique se o elemento que o contém pode ser acessado do seu projeto.</span><span class="sxs-lookup"><span data-stu-id="23dd0-119">Verify that the containing element is accessible from your project.</span></span>

2. <span data-ttu-id="23dd0-120">Verifique se a especificação do elemento recipiente não inclui nenhum alias de importação de outra importação.</span><span class="sxs-lookup"><span data-stu-id="23dd0-120">Verify that the specification of the containing element does not include any import alias from another import.</span></span>

3. <span data-ttu-id="23dd0-121">Verifique se o elemento que o contém expõe pelo menos um `Public` membro.</span><span class="sxs-lookup"><span data-stu-id="23dd0-121">Verify that the containing element exposes at least one `Public` member.</span></span>

## <a name="see-also"></a><span data-ttu-id="23dd0-122">Confira também</span><span class="sxs-lookup"><span data-stu-id="23dd0-122">See also</span></span>

- [<span data-ttu-id="23dd0-123">Instrução Imports (tipo e namespace .NET)</span><span class="sxs-lookup"><span data-stu-id="23dd0-123">Imports Statement (.NET Namespace and Type)</span></span>](../statements/imports-statement-net-namespace-and-type.md)
- [<span data-ttu-id="23dd0-124">Instrução Namespace</span><span class="sxs-lookup"><span data-stu-id="23dd0-124">Namespace Statement</span></span>](../statements/namespace-statement.md)
- [<span data-ttu-id="23dd0-125">Pública</span><span class="sxs-lookup"><span data-stu-id="23dd0-125">Public</span></span>](../modifiers/public.md)
- [<span data-ttu-id="23dd0-126">Namespaces no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="23dd0-126">Namespaces in Visual Basic</span></span>](../../programming-guide/program-structure/namespaces.md)
- [<span data-ttu-id="23dd0-127">Referências a elementos declarados</span><span class="sxs-lookup"><span data-stu-id="23dd0-127">References to Declared Elements</span></span>](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)
