---
title: O tipo subjacente <typename> de Enum não é compatível com CLS
ms.date: 07/20/2015
f1_keywords:
- vbc40032
- bc40032
helpviewer_keywords:
- BC40032
ms.assetid: 32bf1949-fd73-456c-a323-bf1ffe1320ed
ms.openlocfilehash: 42c2398945b97d68161af6fb3c3b69909f4aaf39
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92161511"
---
# <a name="bc40032-underlying-type-typename-of-enum-is-not-cls-compliant"></a><span data-ttu-id="e0a04-102">BC40032: o tipo subjacente \<typename> de enum não tem conformidade com CLS</span><span class="sxs-lookup"><span data-stu-id="e0a04-102">BC40032: Underlying type \<typename> of Enum is not CLS-compliant</span></span>

<span data-ttu-id="e0a04-103">O tipo de dados especificado para essa enumeração não faz parte da [independência de linguagem e dos componentes de Language-Independent](../../../standard/language-independence-and-language-independent-components.md) (CLS).</span><span class="sxs-lookup"><span data-stu-id="e0a04-103">The data type specified for this enumeration is not part of the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS).</span></span> <span data-ttu-id="e0a04-104">Isso não é um erro no seu componente, porque o .NET Framework e Visual Basic oferecem suporte a esse tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="e0a04-104">This is not an error within your component, because the .NET Framework and Visual Basic support this data type.</span></span> <span data-ttu-id="e0a04-105">No entanto, outro componente escrito em código estritamente compatível com CLS pode não dar suporte a esse tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="e0a04-105">However, another component written in strictly CLS-compliant code might not support this data type.</span></span> <span data-ttu-id="e0a04-106">Esse componente pode não ser capaz de interagir com êxito com seu componente.</span><span class="sxs-lookup"><span data-stu-id="e0a04-106">Such a component might not be able to interact successfully with your component.</span></span>

 <span data-ttu-id="e0a04-107">Os tipos de dados a seguir Visual Basic não são compatíveis com CLS:</span><span class="sxs-lookup"><span data-stu-id="e0a04-107">The following Visual Basic data types are not CLS-compliant:</span></span>

- [<span data-ttu-id="e0a04-108">Tipo de Dados SByte</span><span class="sxs-lookup"><span data-stu-id="e0a04-108">SByte Data Type</span></span>](../data-types/sbyte-data-type.md)

- [<span data-ttu-id="e0a04-109">Tipo de Dados UInteger</span><span class="sxs-lookup"><span data-stu-id="e0a04-109">UInteger Data Type</span></span>](../data-types/uinteger-data-type.md)

- [<span data-ttu-id="e0a04-110">Tipo de Dados ULong</span><span class="sxs-lookup"><span data-stu-id="e0a04-110">ULong Data Type</span></span>](../data-types/ulong-data-type.md)

- [<span data-ttu-id="e0a04-111">Tipo de Dados UShort</span><span class="sxs-lookup"><span data-stu-id="e0a04-111">UShort Data Type</span></span>](../data-types/ushort-data-type.md)

 <span data-ttu-id="e0a04-112">Por padrão, esta mensagem é um aviso.</span><span class="sxs-lookup"><span data-stu-id="e0a04-112">By default, this message is a warning.</span></span> <span data-ttu-id="e0a04-113">Para obter mais informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="e0a04-113">For more information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>

 <span data-ttu-id="e0a04-114">**ID do erro:** BC40032</span><span class="sxs-lookup"><span data-stu-id="e0a04-114">**Error ID:** BC40032</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="e0a04-115">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="e0a04-115">To correct this error</span></span>

- <span data-ttu-id="e0a04-116">Se o componente se desassociar apenas com outros componentes .NET Framework, ou não fizer interface com nenhum outro componente, você não precisará alterar nada.</span><span class="sxs-lookup"><span data-stu-id="e0a04-116">If your component interfaces only with other .NET Framework components, or does not interface with any other components, you do not need to change anything.</span></span>

- <span data-ttu-id="e0a04-117">Se você estiver fazendo a interface com um componente não escrito para o .NET Framework, talvez seja possível determinar, por meio de reflexão ou da documentação, se ele dá suporte a esse tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="e0a04-117">If you are interfacing with a component not written for the .NET Framework, you might be able to determine, either through reflection or from documentation, whether it supports this data type.</span></span> <span data-ttu-id="e0a04-118">Se tiver, você não precisará alterar nada.</span><span class="sxs-lookup"><span data-stu-id="e0a04-118">If it does, you do not need to change anything.</span></span>

- <span data-ttu-id="e0a04-119">Se você estiver fazendo a interface com um componente que não oferece suporte a esse tipo de dados, deverá substituí-lo pelo tipo mais próximo em conformidade com CLS.</span><span class="sxs-lookup"><span data-stu-id="e0a04-119">If you are interfacing with a component that does not support this data type, you must replace it with the closest CLS-compliant type.</span></span> <span data-ttu-id="e0a04-120">Por exemplo, no lugar de `UInteger` você pode ser capaz de usar `Integer` se não precisar do intervalo de valores acima de 2.147.483.647.</span><span class="sxs-lookup"><span data-stu-id="e0a04-120">For example, in place of `UInteger` you might be able to use `Integer` if you do not need the value range above 2,147,483,647.</span></span> <span data-ttu-id="e0a04-121">Se você precisar do intervalo estendido, poderá substituir `UInteger` por `Long` .</span><span class="sxs-lookup"><span data-stu-id="e0a04-121">If you do need the extended range, you can replace `UInteger` with `Long`.</span></span>

- <span data-ttu-id="e0a04-122">Se você estiver fazendo a interface com automação ou objetos COM, tenha em mente que alguns tipos têm larguras de dados diferentes das .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e0a04-122">If you are interfacing with Automation or COM objects, keep in mind that some types have different data widths than in the .NET Framework.</span></span> <span data-ttu-id="e0a04-123">Por exemplo, `uint` geralmente é 16 bits em outros ambientes.</span><span class="sxs-lookup"><span data-stu-id="e0a04-123">For example, `uint` is often 16 bits in other environments.</span></span> <span data-ttu-id="e0a04-124">Se você estiver passando um argumento de 16 bits para esse componente, declare-o como `UShort` em vez de `UInteger` em seu código de Visual Basic gerenciado.</span><span class="sxs-lookup"><span data-stu-id="e0a04-124">If you are passing a 16-bit argument to such a component, declare it as `UShort` instead of `UInteger` in your managed Visual Basic code.</span></span>

## <a name="see-also"></a><span data-ttu-id="e0a04-125">Veja também</span><span class="sxs-lookup"><span data-stu-id="e0a04-125">See also</span></span>

- [<span data-ttu-id="e0a04-126">Reflexão (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e0a04-126">Reflection (Visual Basic)</span></span>](../../programming-guide/concepts/reflection.md)
- [<span data-ttu-id="e0a04-127">Reflexão</span><span class="sxs-lookup"><span data-stu-id="e0a04-127">Reflection</span></span>](../../../framework/reflection-and-codedom/reflection.md)
