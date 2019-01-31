---
title: O tipo de membro '<membername>' não é compatível com CLS
ms.date: 07/20/2015
f1_keywords:
- bc40025
- vbc40025
helpviewer_keywords:
- BC40025
ms.assetid: adbd34bb-43d2-4266-90e7-cd1afaf49b4e
ms.openlocfilehash: 9b23ebca955d961771b194df2c7316cb1b7f4a50
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55254087"
---
# <a name="type-of-member-membername-is-not-cls-compliant"></a><span data-ttu-id="f3042-102">Tipo de membro '\<membername >' não é compatível com CLS</span><span class="sxs-lookup"><span data-stu-id="f3042-102">Type of member '\<membername>' is not CLS-compliant</span></span>
<span data-ttu-id="f3042-103">O tipo de dados especificado para esse membro não é parte do [independência de linguagem e componentes independentes de linguagem](../../../standard/language-independence-and-language-independent-components.md) (CLS).</span><span class="sxs-lookup"><span data-stu-id="f3042-103">The data type specified for this member is not part of the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS).</span></span> <span data-ttu-id="f3042-104">Isso não é um erro no seu componente, porque o [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] e Visual Basic dão suporte a esse tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="f3042-104">This is not an error within your component, because the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] and Visual Basic support this data type.</span></span> <span data-ttu-id="f3042-105">No entanto, outro componente escrito em estritamente código compatível com CLS pode não dar suporte a esse tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="f3042-105">However, another component written in strictly CLS-compliant code might not support this data type.</span></span> <span data-ttu-id="f3042-106">Esse componente não pode ser capaz de interagir com êxito com seu componente.</span><span class="sxs-lookup"><span data-stu-id="f3042-106">Such a component might not be able to interact successfully with your component.</span></span>  
  
 <span data-ttu-id="f3042-107">Os seguintes tipos de dados do Visual Basic não são compatíveis com CLS:</span><span class="sxs-lookup"><span data-stu-id="f3042-107">The following Visual Basic data types are not CLS-compliant:</span></span>  
  
-   [<span data-ttu-id="f3042-108">Tipo de Dados SByte</span><span class="sxs-lookup"><span data-stu-id="f3042-108">SByte Data Type</span></span>](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
-   [<span data-ttu-id="f3042-109">Tipo de Dados UInteger</span><span class="sxs-lookup"><span data-stu-id="f3042-109">UInteger Data Type</span></span>](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
-   [<span data-ttu-id="f3042-110">Tipo de Dados ULong</span><span class="sxs-lookup"><span data-stu-id="f3042-110">ULong Data Type</span></span>](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
-   [<span data-ttu-id="f3042-111">Tipo de Dados UShort</span><span class="sxs-lookup"><span data-stu-id="f3042-111">UShort Data Type</span></span>](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 <span data-ttu-id="f3042-112">Por padrão, esta mensagem é um aviso.</span><span class="sxs-lookup"><span data-stu-id="f3042-112">By default, this message is a warning.</span></span> <span data-ttu-id="f3042-113">Para obter mais informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="f3042-113">For more information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="f3042-114">**ID do erro:** BC40025</span><span class="sxs-lookup"><span data-stu-id="f3042-114">**Error ID:** BC40025</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f3042-115">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="f3042-115">To correct this error</span></span>  
  
-   <span data-ttu-id="f3042-116">Se seu componente interfaces somente com os outros [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] componentes ou não a interface não com todos os outros componentes, você não precisa alterar nada.</span><span class="sxs-lookup"><span data-stu-id="f3042-116">If your component interfaces only with other [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] components, or does not interface with any other components, you do not need to change anything.</span></span>  
  
-   <span data-ttu-id="f3042-117">Se você estiver fazendo interface com um componente não escrito para o [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], você poderá determinar, através de reflexão ou da documentação, se ele dá suporte a esse tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="f3042-117">If you are interfacing with a component not written for the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], you might be able to determine, either through reflection or from documentation, whether it supports this data type.</span></span> <span data-ttu-id="f3042-118">Se isso acontecer, você não precisará alterar nada.</span><span class="sxs-lookup"><span data-stu-id="f3042-118">If it does, you do not need to change anything.</span></span>  
  
-   <span data-ttu-id="f3042-119">Se você estiver fazendo interface com um componente que não oferece suporte a esse tipo de dados, você deve substituí-lo com o tipo compatível com CLS mais próximo.</span><span class="sxs-lookup"><span data-stu-id="f3042-119">If you are interfacing with a component that does not support this data type, you must replace it with the closest CLS-compliant type.</span></span> <span data-ttu-id="f3042-120">Por exemplo, no lugar de `UInteger` talvez você possa usar `Integer` se você não precisar que o intervalo de valores acima de 2.147.483.647.</span><span class="sxs-lookup"><span data-stu-id="f3042-120">For example, in place of `UInteger` you might be able to use `Integer` if you do not need the value range above 2,147,483,647.</span></span> <span data-ttu-id="f3042-121">Se você precisar de intervalo estendido, você pode substituir `UInteger` com `Long`.</span><span class="sxs-lookup"><span data-stu-id="f3042-121">If you do need the extended range, you can replace `UInteger` with `Long`.</span></span>  
  
-   <span data-ttu-id="f3042-122">Se você estiver fazendo interface com objetos de automação ou COM, tenha em mente que alguns tipos têm larguras de dados diferentes que no [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f3042-122">If you are interfacing with Automation or COM objects, keep in mind that some types have different data widths than in the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="f3042-123">Por exemplo, `uint` geralmente é 16 bits em outros ambientes.</span><span class="sxs-lookup"><span data-stu-id="f3042-123">For example, `uint` is often 16 bits in other environments.</span></span> <span data-ttu-id="f3042-124">Se você estiver passando um argumento de 16 bits para tal componente, declare-o como `UShort` em vez de `UInteger` no seu código gerenciado do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="f3042-124">If you are passing a 16-bit argument to such a component, declare it as `UShort` instead of `UInteger` in your managed Visual Basic code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3042-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f3042-125">See also</span></span>
- [<span data-ttu-id="f3042-126">Reflexão</span><span class="sxs-lookup"><span data-stu-id="f3042-126">Reflection</span></span>](../../../framework/reflection-and-codedom/reflection.md)

