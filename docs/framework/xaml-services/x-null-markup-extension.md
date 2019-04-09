---
title: Extensão de marcação x:Null
ms.date: 03/30/2017
f1_keywords:
- NullExtension
- x:NullExtension
- x:Null
- "Null"
- xNull
helpviewer_keywords:
- Null markup extension in XAML [XAML Services]
- x:Null markup extension [XAML Services]
- XAML [XAML Services], x:Null markup extension
ms.assetid: 2e3ccc21-4996-481d-91b5-3910d8b3bfa3
ms.openlocfilehash: e46d8561b62d9137d4fed4df447338a97fc0577b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59100802"
---
# <a name="xnull-markup-extension"></a><span data-ttu-id="94856-102">Extensão de marcação x:Null</span><span class="sxs-lookup"><span data-stu-id="94856-102">x:Null Markup Extension</span></span>
<span data-ttu-id="94856-103">Especifica `null` como um valor para um membro XAML.</span><span class="sxs-lookup"><span data-stu-id="94856-103">Specifies `null` as a value for a XAML member.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="94856-104">Uso do Atributo XAML</span><span class="sxs-lookup"><span data-stu-id="94856-104">XAML Attribute Usage</span></span>  
  
```xaml  
<object property="{x:Null}" .../>  
```  
  
## <a name="remarks"></a><span data-ttu-id="94856-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="94856-105">Remarks</span></span>  
 <span data-ttu-id="94856-106">A palavra-chave para uma referência nula no C# e [!INCLUDE[TLA#tla_cpp](../../../includes/tlasharptla-cpp-md.md)] é nulo.</span><span class="sxs-lookup"><span data-stu-id="94856-106">The keyword for a null reference in C# and [!INCLUDE[TLA#tla_cpp](../../../includes/tlasharptla-cpp-md.md)] is null.</span></span> <span data-ttu-id="94856-107">É a palavra-chave do Microsoft Visual Basic para uma referência nula `Nothing`, mas você sempre usar `{x:Null}` como o uso XAML independentemente qual idioma de lógica que você associar com o XAML.</span><span class="sxs-lookup"><span data-stu-id="94856-107">The Microsoft Visual Basic keyword for a null reference is `Nothing`, but you always use `{x:Null}` as the XAML usage regardless which code-behind language you associate with the XAML.</span></span>  
  
 <span data-ttu-id="94856-108">O `x:Null` extensão de marcação não possui propriedades configuráveis.</span><span class="sxs-lookup"><span data-stu-id="94856-108">The `x:Null` markup extension has no settable properties.</span></span>  
  
 <span data-ttu-id="94856-109">Um uso nulo geralmente está associado com a exposição de membro XAML de um CLR <xref:System.Nullable%601> valor.</span><span class="sxs-lookup"><span data-stu-id="94856-109">A null usage is often associated with the XAML member exposure of a CLR <xref:System.Nullable%601> value.</span></span>  
  
 <span data-ttu-id="94856-110">O `x:Null` extensão de marcação, como todas as extensões de marcação XAML, usa as chaves (`{,}`) para escapar o tratamento de valores de atributo para ser diferente de literais ou referências de manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="94856-110">The `x:Null` markup extension, like all XAML markup extensions, uses the braces (`{,}`) for escaping the handling of attribute values to be other than literals or event-handler references.</span></span> <span data-ttu-id="94856-111">Sintaxe de atributo é a sintaxe mais frequentemente usada com essa extensão de marcação.</span><span class="sxs-lookup"><span data-stu-id="94856-111">Attribute syntax is the syntax most frequently used with this markup extension.</span></span> <span data-ttu-id="94856-112">Uma sintaxe de elemento de objeto `<x:Null />` é tecnicamente possível, mas raramente é usado porque o `x:Null` extensão de marcação não tem parâmetros posicionais ou argumentos de construção.</span><span class="sxs-lookup"><span data-stu-id="94856-112">An object element syntax `<x:Null />` is technically possible, but is rarely used because the `x:Null` markup extension has no positional parameters or construction arguments.</span></span>  
  
 <span data-ttu-id="94856-113">Para obter informações sobre extensões de marcação, consulte [extensões de marcação e XAML WPF](../wpf/advanced/markup-extensions-and-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="94856-113">For information about markup extensions, see [Markup Extensions and WPF XAML](../wpf/advanced/markup-extensions-and-wpf-xaml.md).</span></span>  
  
 <span data-ttu-id="94856-114">Nos serviços de XAML do .NET Framework, o tratamento para essa extensão de marcação é definido pelo <xref:System.Windows.Markup.NullExtension> classe.</span><span class="sxs-lookup"><span data-stu-id="94856-114">In .NET Framework XAML Services, the handling for this markup extension is defined by the <xref:System.Windows.Markup.NullExtension> class.</span></span>  
  
## <a name="wpf-usage-notes"></a><span data-ttu-id="94856-115">Notas de uso do WPF</span><span class="sxs-lookup"><span data-stu-id="94856-115">WPF Usage Notes</span></span>  
 <span data-ttu-id="94856-116">Observe que `null` não é necessariamente o valor inicial para uma propriedade de dependência do tipo de referência.</span><span class="sxs-lookup"><span data-stu-id="94856-116">Note that `null` is not necessarily the initial unset value for a reference-type dependency property.</span></span> <span data-ttu-id="94856-117">O valor padrão inicial pode variar para cada propriedade de dependência e pode ser com base nos metadados de propriedade específica.</span><span class="sxs-lookup"><span data-stu-id="94856-117">The initial default value can vary for each dependency property and can be based on property-specific metadata.</span></span> <span data-ttu-id="94856-118">Muitas propriedades de dependência não aceitam `null` como um valor, por meio de marcação ou código devido a suas implementações de retorno de chamada de validação.</span><span class="sxs-lookup"><span data-stu-id="94856-118">Many dependency properties do not accept `null` as a value, either through markup or code because of their validation callback implementations.</span></span> <span data-ttu-id="94856-119">Para obter mais informações sobre propriedades de dependência, consulte [visão geral das propriedades de dependência](../wpf/advanced/dependency-properties-overview.md).</span><span class="sxs-lookup"><span data-stu-id="94856-119">For more information about dependency properties, see [Dependency Properties Overview](../wpf/advanced/dependency-properties-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94856-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="94856-120">See also</span></span>

- <xref:System.Windows.DependencyProperty.UnsetValue>
- [<span data-ttu-id="94856-121">Visão geral de XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="94856-121">XAML Overview (WPF)</span></span>](../wpf/advanced/xaml-overview-wpf.md)
- [<span data-ttu-id="94856-122">Extensões de marcação e XAML WPF</span><span class="sxs-lookup"><span data-stu-id="94856-122">Markup Extensions and WPF XAML</span></span>](../wpf/advanced/markup-extensions-and-wpf-xaml.md)
