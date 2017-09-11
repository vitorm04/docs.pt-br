---
title: "Tipo de membro &quot;&lt;membername&gt;&quot; não é compatível com CLS | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc40025
- vbc40025
dev_langs:
- VB
helpviewer_keywords:
- BC40025
ms.assetid: adbd34bb-43d2-4266-90e7-cd1afaf49b4e
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
ms.openlocfilehash: ab4d0936603ae133bd7def4341f29d5fcdf7188b
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="type-of-member-39ltmembernamegt39-is-not-cls-compliant"></a><span data-ttu-id="e9f7e-102">Tipo de membro '&lt;membername&gt;' não é compatível com CLS</span><span class="sxs-lookup"><span data-stu-id="e9f7e-102">Type of member &#39;&lt;membername&gt;&#39; is not CLS-compliant</span></span>
<span data-ttu-id="e9f7e-103">O tipo de dados especificado para este membro não é parte do [independência da linguagem e componentes independentes de linguagem](https://msdn.microsoft.com/library/12a7a7h3) (CLS).</span><span class="sxs-lookup"><span data-stu-id="e9f7e-103">The data type specified for this member is not part of the [Language Independence and Language-Independent Components](https://msdn.microsoft.com/library/12a7a7h3) (CLS).</span></span> <span data-ttu-id="e9f7e-104">Isso não é um erro no seu componente, pois o [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] e [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] suporte para este tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="e9f7e-104">This is not an error within your component, because the [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] and [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] support this data type.</span></span> <span data-ttu-id="e9f7e-105">No entanto, outro componente escrito em estritamente código compatível com CLS pode não oferecer suporte a esse tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="e9f7e-105">However, another component written in strictly CLS-compliant code might not support this data type.</span></span> <span data-ttu-id="e9f7e-106">Esse componente não poderá interagir com êxito com seu componente.</span><span class="sxs-lookup"><span data-stu-id="e9f7e-106">Such a component might not be able to interact successfully with your component.</span></span>  
  
 <span data-ttu-id="e9f7e-107">O seguinte [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] tipos de dados não são compatíveis com CLS:</span><span class="sxs-lookup"><span data-stu-id="e9f7e-107">The following [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] data types are not CLS-compliant:</span></span>  
  
-   [<span data-ttu-id="e9f7e-108">Tipo de Dados SByte</span><span class="sxs-lookup"><span data-stu-id="e9f7e-108">SByte Data Type</span></span>](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
-   [<span data-ttu-id="e9f7e-109">Tipo de Dados UInteger</span><span class="sxs-lookup"><span data-stu-id="e9f7e-109">UInteger Data Type</span></span>](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
-   [<span data-ttu-id="e9f7e-110">Tipo de Dados ULong</span><span class="sxs-lookup"><span data-stu-id="e9f7e-110">ULong Data Type</span></span>](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
-   [<span data-ttu-id="e9f7e-111">Tipo de Dados UShort</span><span class="sxs-lookup"><span data-stu-id="e9f7e-111">UShort Data Type</span></span>](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 <span data-ttu-id="e9f7e-112">Por padrão, esta mensagem é um aviso.</span><span class="sxs-lookup"><span data-stu-id="e9f7e-112">By default, this message is a warning.</span></span> <span data-ttu-id="e9f7e-113">Para obter mais informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="e9f7e-113">For more information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="e9f7e-114">**ID do erro:** BC40025</span><span class="sxs-lookup"><span data-stu-id="e9f7e-114">**Error ID:** BC40025</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e9f7e-115">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="e9f7e-115">To correct this error</span></span>  
  
-   <span data-ttu-id="e9f7e-116">Se seu componente interfaces somente com outras [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] componentes ou não não interface com quaisquer outros componentes, você não precisa alterar nada.</span><span class="sxs-lookup"><span data-stu-id="e9f7e-116">If your component interfaces only with other [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] components, or does not interface with any other components, you do not need to change anything.</span></span>  
  
-   <span data-ttu-id="e9f7e-117">Se você estiver fazendo interface com um componente não gravado para o [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)], você poderá determinar, através de reflexão ou da documentação, se ele suporta esse tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="e9f7e-117">If you are interfacing with a component not written for the [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)], you might be able to determine, either through reflection or from documentation, whether it supports this data type.</span></span> <span data-ttu-id="e9f7e-118">Se isso acontecer, você não precisa alterar nada.</span><span class="sxs-lookup"><span data-stu-id="e9f7e-118">If it does, you do not need to change anything.</span></span>  
  
-   <span data-ttu-id="e9f7e-119">Se você estiver fazendo interface com um componente que não oferece suporte a esse tipo de dados, você deve substituí-lo com o tipo compatível com CLS mais próximo.</span><span class="sxs-lookup"><span data-stu-id="e9f7e-119">If you are interfacing with a component that does not support this data type, you must replace it with the closest CLS-compliant type.</span></span> <span data-ttu-id="e9f7e-120">Por exemplo, no lugar de `UInteger` você poderá usar `Integer` se você não precisar do intervalo de valor acima de 2.147.483.647.</span><span class="sxs-lookup"><span data-stu-id="e9f7e-120">For example, in place of `UInteger` you might be able to use `Integer` if you do not need the value range above 2,147,483,647.</span></span> <span data-ttu-id="e9f7e-121">Se você precisar de intervalo estendido, você pode substituir `UInteger` com `Long`.</span><span class="sxs-lookup"><span data-stu-id="e9f7e-121">If you do need the extended range, you can replace `UInteger` with `Long`.</span></span>  
  
-   <span data-ttu-id="e9f7e-122">Se você estiver fazendo interface com objetos de automação ou COM, tenha em mente que alguns tipos têm larguras de dados diferentes que o [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)].</span><span class="sxs-lookup"><span data-stu-id="e9f7e-122">If you are interfacing with Automation or COM objects, keep in mind that some types have different data widths than in the [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)].</span></span> <span data-ttu-id="e9f7e-123">Por exemplo, `uint` é geralmente 16 bits em outros ambientes.</span><span class="sxs-lookup"><span data-stu-id="e9f7e-123">For example, `uint` is often 16 bits in other environments.</span></span> <span data-ttu-id="e9f7e-124">Se você estiver passando um argumento de 16 bits para tal um componente, declare-o como `UShort` em vez de `UInteger` em gerenciado [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] código.</span><span class="sxs-lookup"><span data-stu-id="e9f7e-124">If you are passing a 16-bit argument to such a component, declare it as `UShort` instead of `UInteger` in your managed [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9f7e-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e9f7e-125">See Also</span></span>  
 <span data-ttu-id="e9f7e-126">[Reflexão](http://msdn.microsoft.com/library/d1a58e7f-fb39-4d50-bf84-e3b8f9bf9775) </span><span class="sxs-lookup"><span data-stu-id="e9f7e-126">[Reflection](http://msdn.microsoft.com/library/d1a58e7f-fb39-4d50-bf84-e3b8f9bf9775) </span></span>  
<span data-ttu-id="e9f7e-127"> [\<PAVE em > escrevendo código compatível com CLS](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)</span><span class="sxs-lookup"><span data-stu-id="e9f7e-127"> [\<PAVE OVER> Writing CLS-Compliant Code](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)</span></span>
