---
title: "Extensão de marcação x:Null"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- NullExtension
- x:NullExtension
- x:Null
- Null
- xNull
helpviewer_keywords:
- Null markup extension in XAML [XAML Services]
- x:Null markup extension [XAML Services]
- XAML [XAML Services], x:Null markup extension
ms.assetid: 2e3ccc21-4996-481d-91b5-3910d8b3bfa3
caps.latest.revision: "20"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: a60d74bdf3343d02eaf912ac7700f36a649f659c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="xnull-markup-extension"></a><span data-ttu-id="2578e-102">Extensão de marcação x:Null</span><span class="sxs-lookup"><span data-stu-id="2578e-102">x:Null Markup Extension</span></span>
<span data-ttu-id="2578e-103">Especifica `null` como um valor para um membro XAML.</span><span class="sxs-lookup"><span data-stu-id="2578e-103">Specifies `null` as a value for a XAML member.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="2578e-104">Uso do Atributo XAML</span><span class="sxs-lookup"><span data-stu-id="2578e-104">XAML Attribute Usage</span></span>  
  
```xaml  
<object property="{x:Null}" .../>  
```  
  
## <a name="remarks"></a><span data-ttu-id="2578e-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="2578e-105">Remarks</span></span>  
 <span data-ttu-id="2578e-106">A palavra-chave para uma referência nula em [!INCLUDE[TLA#tla_cshrp](../../../includes/tlasharptla-cshrp-md.md)] e [!INCLUDE[TLA#tla_cpp](../../../includes/tlasharptla-cpp-md.md)] é nulo.</span><span class="sxs-lookup"><span data-stu-id="2578e-106">The keyword for a null reference in [!INCLUDE[TLA#tla_cshrp](../../../includes/tlasharptla-cshrp-md.md)] and [!INCLUDE[TLA#tla_cpp](../../../includes/tlasharptla-cpp-md.md)] is null.</span></span> <span data-ttu-id="2578e-107">O [!INCLUDE[TLA#tla_visualb](../../../includes/tlasharptla-visualb-md.md)] palavra-chave para uma referência nula é `Nothing`, mas você sempre usar `{x:Null}` como o uso XAML independentemente qual idioma de lógica você associar o XAML.</span><span class="sxs-lookup"><span data-stu-id="2578e-107">The [!INCLUDE[TLA#tla_visualb](../../../includes/tlasharptla-visualb-md.md)] keyword for a null reference is `Nothing`, but you always use `{x:Null}` as the XAML usage regardless which code-behind language you associate with the XAML.</span></span>  
  
 <span data-ttu-id="2578e-108">O `x:Null` extensão de marcação não possui propriedades configuráveis.</span><span class="sxs-lookup"><span data-stu-id="2578e-108">The `x:Null` markup extension has no settable properties.</span></span>  
  
 <span data-ttu-id="2578e-109">Um uso nulo costuma está associado a exposição de membro XAML de um CLR <xref:System.Nullable%601> valor.</span><span class="sxs-lookup"><span data-stu-id="2578e-109">A null usage is often associated with the XAML member exposure of a CLR <xref:System.Nullable%601> value.</span></span>  
  
 <span data-ttu-id="2578e-110">O `x:Null` extensão de marcação, como todas as extensões de marcação XAML, usa as chaves (`{,}`) para escapar o tratamento de valores de atributo para ser diferente de literais ou referências de manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="2578e-110">The `x:Null` markup extension, like all XAML markup extensions, uses the braces (`{,}`) for escaping the handling of attribute values to be other than literals or event-handler references.</span></span> <span data-ttu-id="2578e-111">Sintaxe de atributo é a sintaxe mais frequentemente usada com essa extensão de marcação.</span><span class="sxs-lookup"><span data-stu-id="2578e-111">Attribute syntax is the syntax most frequently used with this markup extension.</span></span> <span data-ttu-id="2578e-112">Uma sintaxe de elemento de objeto `<x:Null />` é tecnicamente possível, mas raramente é usada, pois o `x:Null` extensão de marcação não tem parâmetros posicionais ou argumentos de construção.</span><span class="sxs-lookup"><span data-stu-id="2578e-112">An object element syntax `<x:Null />` is technically possible, but is rarely used because the `x:Null` markup extension has no positional parameters or construction arguments.</span></span>  
  
 <span data-ttu-id="2578e-113">Para obter informações sobre extensões de marcação, consulte [extensões de marcação e WPF XAML](../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="2578e-113">For information about markup extensions, see [Markup Extensions and WPF XAML](../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).</span></span>  
  
 <span data-ttu-id="2578e-114">Em serviços de XAML do .NET Framework, o tratamento para esta extensão de marcação é definida pelo <xref:System.Windows.Markup.NullExtension> classe.</span><span class="sxs-lookup"><span data-stu-id="2578e-114">In .NET Framework XAML Services, the handling for this markup extension is defined by the <xref:System.Windows.Markup.NullExtension> class.</span></span>  
  
## <a name="wpf-usage-notes"></a><span data-ttu-id="2578e-115">Observações de uso do WPF</span><span class="sxs-lookup"><span data-stu-id="2578e-115">WPF Usage Notes</span></span>  
 <span data-ttu-id="2578e-116">Observe que `null` não é necessariamente o valor inicial para uma propriedade de dependência de tipo de referência.</span><span class="sxs-lookup"><span data-stu-id="2578e-116">Note that `null` is not necessarily the initial unset value for a reference-type dependency property.</span></span> <span data-ttu-id="2578e-117">O valor padrão inicial pode variar para cada propriedade de dependência e pode ser com base nos metadados de propriedade específica.</span><span class="sxs-lookup"><span data-stu-id="2578e-117">The initial default value can vary for each dependency property and can be based on property-specific metadata.</span></span> <span data-ttu-id="2578e-118">Muitas propriedades de dependência não aceitam `null` como um valor, por meio de marcação ou código devido a suas implementações de retorno de chamada de validação.</span><span class="sxs-lookup"><span data-stu-id="2578e-118">Many dependency properties do not accept `null` as a value, either through markup or code because of their validation callback implementations.</span></span> <span data-ttu-id="2578e-119">Para obter mais informações sobre propriedades de dependência, consulte [visão geral de propriedades de dependência](../../../docs/framework/wpf/advanced/dependency-properties-overview.md).</span><span class="sxs-lookup"><span data-stu-id="2578e-119">For more information about dependency properties, see [Dependency Properties Overview](../../../docs/framework/wpf/advanced/dependency-properties-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2578e-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2578e-120">See Also</span></span>  
 <xref:System.Windows.DependencyProperty.UnsetValue>  
 [<span data-ttu-id="2578e-121">Visão geral de XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="2578e-121">XAML Overview (WPF)</span></span>](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [<span data-ttu-id="2578e-122">Extensões de marcação e XAML WPF</span><span class="sxs-lookup"><span data-stu-id="2578e-122">Markup Extensions and WPF XAML</span></span>](../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
