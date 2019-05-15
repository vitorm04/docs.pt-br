---
title: O tipo de membro '<membername>' não é compatível com CLS
ms.date: 07/20/2015
f1_keywords:
- bc40025
- vbc40025
helpviewer_keywords:
- BC40025
ms.assetid: adbd34bb-43d2-4266-90e7-cd1afaf49b4e
ms.openlocfilehash: f6f66617774dccff4450cce42904126acf5c3769
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65590678"
---
# <a name="type-of-member-membername-is-not-cls-compliant"></a><span data-ttu-id="d2417-102">Tipo de membro '\<membername >' não é compatível com CLS</span><span class="sxs-lookup"><span data-stu-id="d2417-102">Type of member '\<membername>' is not CLS-compliant</span></span>
<span data-ttu-id="d2417-103">O tipo de dados especificado para esse membro não é parte do [independência de linguagem e componentes independentes de linguagem](../../../standard/language-independence-and-language-independent-components.md) (CLS).</span><span class="sxs-lookup"><span data-stu-id="d2417-103">The data type specified for this member is not part of the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS).</span></span> <span data-ttu-id="d2417-104">Isso não é um erro no seu componente, porque o .NET Framework e Visual Basic dá suporte a esse tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="d2417-104">This is not an error within your component, because the .NET Framework and Visual Basic support this data type.</span></span> <span data-ttu-id="d2417-105">No entanto, outro componente escrito em estritamente código compatível com CLS pode não dar suporte a esse tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="d2417-105">However, another component written in strictly CLS-compliant code might not support this data type.</span></span> <span data-ttu-id="d2417-106">Esse componente não pode ser capaz de interagir com êxito com seu componente.</span><span class="sxs-lookup"><span data-stu-id="d2417-106">Such a component might not be able to interact successfully with your component.</span></span>  
  
 <span data-ttu-id="d2417-107">Os seguintes tipos de dados do Visual Basic não são compatíveis com CLS:</span><span class="sxs-lookup"><span data-stu-id="d2417-107">The following Visual Basic data types are not CLS-compliant:</span></span>  
  
- [<span data-ttu-id="d2417-108">Tipo de Dados SByte</span><span class="sxs-lookup"><span data-stu-id="d2417-108">SByte Data Type</span></span>](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
- [<span data-ttu-id="d2417-109">Tipo de Dados UInteger</span><span class="sxs-lookup"><span data-stu-id="d2417-109">UInteger Data Type</span></span>](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
- [<span data-ttu-id="d2417-110">Tipo de Dados ULong</span><span class="sxs-lookup"><span data-stu-id="d2417-110">ULong Data Type</span></span>](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
- [<span data-ttu-id="d2417-111">Tipo de Dados UShort</span><span class="sxs-lookup"><span data-stu-id="d2417-111">UShort Data Type</span></span>](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 <span data-ttu-id="d2417-112">Por padrão, esta mensagem é um aviso.</span><span class="sxs-lookup"><span data-stu-id="d2417-112">By default, this message is a warning.</span></span> <span data-ttu-id="d2417-113">Para obter mais informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="d2417-113">For more information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="d2417-114">**ID do erro:** BC40025</span><span class="sxs-lookup"><span data-stu-id="d2417-114">**Error ID:** BC40025</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d2417-115">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="d2417-115">To correct this error</span></span>  
  
- <span data-ttu-id="d2417-116">Se seu componente interage apenas com outros componentes do .NET Framework ou não estabelece uma interface com quaisquer outros componentes, você não precisará alterar nada.</span><span class="sxs-lookup"><span data-stu-id="d2417-116">If your component interfaces only with other .NET Framework components, or does not interface with any other components, you do not need to change anything.</span></span>  
  
- <span data-ttu-id="d2417-117">Se você estiver fazendo interface com um componente não escrito para o .NET Framework, você poderá determinar, por meio de reflexão ou da documentação, se ele dá suporte a esse tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="d2417-117">If you are interfacing with a component not written for the .NET Framework, you might be able to determine, either through reflection or from documentation, whether it supports this data type.</span></span> <span data-ttu-id="d2417-118">Se isso acontecer, você não precisará alterar nada.</span><span class="sxs-lookup"><span data-stu-id="d2417-118">If it does, you do not need to change anything.</span></span>  
  
- <span data-ttu-id="d2417-119">Se você estiver fazendo interface com um componente que não oferece suporte a esse tipo de dados, você deve substituí-lo com o tipo compatível com CLS mais próximo.</span><span class="sxs-lookup"><span data-stu-id="d2417-119">If you are interfacing with a component that does not support this data type, you must replace it with the closest CLS-compliant type.</span></span> <span data-ttu-id="d2417-120">Por exemplo, no lugar de `UInteger` talvez você possa usar `Integer` se você não precisar que o intervalo de valores acima de 2.147.483.647.</span><span class="sxs-lookup"><span data-stu-id="d2417-120">For example, in place of `UInteger` you might be able to use `Integer` if you do not need the value range above 2,147,483,647.</span></span> <span data-ttu-id="d2417-121">Se você precisar de intervalo estendido, você pode substituir `UInteger` com `Long`.</span><span class="sxs-lookup"><span data-stu-id="d2417-121">If you do need the extended range, you can replace `UInteger` with `Long`.</span></span>  
  
- <span data-ttu-id="d2417-122">Se você estiver fazendo interface com objetos de automação ou COM, lembre-se de que alguns tipos têm larguras de dados diferente do que no .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d2417-122">If you are interfacing with Automation or COM objects, keep in mind that some types have different data widths than in the .NET Framework.</span></span> <span data-ttu-id="d2417-123">Por exemplo, `uint` geralmente é 16 bits em outros ambientes.</span><span class="sxs-lookup"><span data-stu-id="d2417-123">For example, `uint` is often 16 bits in other environments.</span></span> <span data-ttu-id="d2417-124">Se você estiver passando um argumento de 16 bits para tal componente, declare-o como `UShort` em vez de `UInteger` no seu código gerenciado do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="d2417-124">If you are passing a 16-bit argument to such a component, declare it as `UShort` instead of `UInteger` in your managed Visual Basic code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2417-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d2417-125">See also</span></span>

- [<span data-ttu-id="d2417-126">Reflexão</span><span class="sxs-lookup"><span data-stu-id="d2417-126">Reflection</span></span>](../../../framework/reflection-and-codedom/reflection.md)
