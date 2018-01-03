---
title: "O tipo subjacente &lt;typename&gt; de Enum não é compatível com CLS"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc40032
- bc40032
helpviewer_keywords: BC40032
ms.assetid: 32bf1949-fd73-456c-a323-bf1ffe1320ed
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e054f8d992154f66ab1d48a477a7e04900aa5b4d
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/21/2017
---
# <a name="underlying-type-lttypenamegt-of-enum-is-not-cls-compliant"></a><span data-ttu-id="b3919-102">O tipo subjacente &lt;typename&gt; de Enum não é compatível com CLS</span><span class="sxs-lookup"><span data-stu-id="b3919-102">Underlying type &lt;typename&gt; of Enum is not CLS-compliant</span></span>
<span data-ttu-id="b3919-103">O tipo de dados especificado para essa enumeração não é parte do [independência da linguagem e componentes independentes da linguagem](../../../standard/language-independence-and-language-independent-components.md) (CLS).</span><span class="sxs-lookup"><span data-stu-id="b3919-103">The data type specified for this enumeration is not part of the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS).</span></span> <span data-ttu-id="b3919-104">Isso não é um erro no seu componente, porque o [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] e [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] suporte para esse tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="b3919-104">This is not an error within your component, because the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] and [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] support this data type.</span></span> <span data-ttu-id="b3919-105">No entanto, outro componente escrito em estritamente código compatível com CLS não pode oferecer suporte a esse tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="b3919-105">However, another component written in strictly CLS-compliant code might not support this data type.</span></span> <span data-ttu-id="b3919-106">Esse componente não poderá interagir com êxito com seu componente.</span><span class="sxs-lookup"><span data-stu-id="b3919-106">Such a component might not be able to interact successfully with your component.</span></span>  
  
 <span data-ttu-id="b3919-107">O seguinte [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] tipos de dados não são compatíveis com CLS:</span><span class="sxs-lookup"><span data-stu-id="b3919-107">The following [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] data types are not CLS-compliant:</span></span>  
  
-   [<span data-ttu-id="b3919-108">Tipo de Dados SByte</span><span class="sxs-lookup"><span data-stu-id="b3919-108">SByte Data Type</span></span>](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
-   [<span data-ttu-id="b3919-109">Tipo de Dados UInteger</span><span class="sxs-lookup"><span data-stu-id="b3919-109">UInteger Data Type</span></span>](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
-   [<span data-ttu-id="b3919-110">Tipo de Dados ULong</span><span class="sxs-lookup"><span data-stu-id="b3919-110">ULong Data Type</span></span>](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
-   [<span data-ttu-id="b3919-111">Tipo de Dados UShort</span><span class="sxs-lookup"><span data-stu-id="b3919-111">UShort Data Type</span></span>](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 <span data-ttu-id="b3919-112">Por padrão, esta mensagem é um aviso.</span><span class="sxs-lookup"><span data-stu-id="b3919-112">By default, this message is a warning.</span></span> <span data-ttu-id="b3919-113">Para obter mais informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="b3919-113">For more information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="b3919-114">**ID do erro:** BC40032</span><span class="sxs-lookup"><span data-stu-id="b3919-114">**Error ID:** BC40032</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b3919-115">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="b3919-115">To correct this error</span></span>  
  
-   <span data-ttu-id="b3919-116">Se o seu componente interfaces somente com outras [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] componentes ou não não interface com outros componentes, você não precisa alterar nada.</span><span class="sxs-lookup"><span data-stu-id="b3919-116">If your component interfaces only with other [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] components, or does not interface with any other components, you do not need to change anything.</span></span>  
  
-   <span data-ttu-id="b3919-117">Se você estiver fazendo interface com um componente não gravado para o [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], você poderá determinar, através de reflexão ou da documentação, se ele dá suporte a esse tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="b3919-117">If you are interfacing with a component not written for the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], you might be able to determine, either through reflection or from documentation, whether it supports this data type.</span></span> <span data-ttu-id="b3919-118">Em caso afirmativo, você não precisa alterar nada.</span><span class="sxs-lookup"><span data-stu-id="b3919-118">If it does, you do not need to change anything.</span></span>  
  
-   <span data-ttu-id="b3919-119">Se você estiver fazendo interface com um componente que não oferece suporte a esse tipo de dados, você deve substituí-lo com o tipo compatível com CLS mais próximo.</span><span class="sxs-lookup"><span data-stu-id="b3919-119">If you are interfacing with a component that does not support this data type, you must replace it with the closest CLS-compliant type.</span></span> <span data-ttu-id="b3919-120">Por exemplo, no lugar de `UInteger` você poderá usar `Integer` se você não precisar que o intervalo de valores acima de 2.147.483.647.</span><span class="sxs-lookup"><span data-stu-id="b3919-120">For example, in place of `UInteger` you might be able to use `Integer` if you do not need the value range above 2,147,483,647.</span></span> <span data-ttu-id="b3919-121">Se você precisar de intervalo estendido, você pode substituir `UInteger` com `Long`.</span><span class="sxs-lookup"><span data-stu-id="b3919-121">If you do need the extended range, you can replace `UInteger` with `Long`.</span></span>  
  
-   <span data-ttu-id="b3919-122">Se você estiver fazendo interface com objetos de automação ou COM, tenha em mente que alguns tipos têm larguras de dados diferentes do que no [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b3919-122">If you are interfacing with Automation or COM objects, keep in mind that some types have different data widths than in the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="b3919-123">Por exemplo, `uint` é geralmente 16 bits em outros ambientes.</span><span class="sxs-lookup"><span data-stu-id="b3919-123">For example, `uint` is often 16 bits in other environments.</span></span> <span data-ttu-id="b3919-124">Se você estiver passando um argumento de 16 bits para tal componente, declare-o como `UShort` em vez de `UInteger` em gerenciado [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] código.</span><span class="sxs-lookup"><span data-stu-id="b3919-124">If you are passing a 16-bit argument to such a component, declare it as `UShort` instead of `UInteger` in your managed [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3919-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b3919-125">See Also</span></span>  
 [<span data-ttu-id="b3919-126">Reflexão (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b3919-126">Reflection (Visual Basic)</span></span>](../../programming-guide/concepts/reflection.md)  
 [<span data-ttu-id="b3919-127">Reflexão</span><span class="sxs-lookup"><span data-stu-id="b3919-127">Reflection</span></span>](../../../framework/reflection-and-codedom/reflection.md)  
 
