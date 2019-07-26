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
ms.openlocfilehash: 7dbea2c7d4010d8defc572dbdc14a0dfd6d7601e
ms.sourcegitcommit: 4b9c2d893b45d47048c6598b4182ba87759b1b59
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/25/2019
ms.locfileid: "68484717"
---
# <a name="xnull-markup-extension"></a><span data-ttu-id="96a29-102">Extensão de marcação x:Null</span><span class="sxs-lookup"><span data-stu-id="96a29-102">x:Null Markup Extension</span></span>
<span data-ttu-id="96a29-103">Especifica `null` como um valor para um membro XAML.</span><span class="sxs-lookup"><span data-stu-id="96a29-103">Specifies `null` as a value for a XAML member.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="96a29-104">Uso do Atributo XAML</span><span class="sxs-lookup"><span data-stu-id="96a29-104">XAML Attribute Usage</span></span>  
  
```xaml  
<object property="{x:Null}" .../>  
```  
  
## <a name="remarks"></a><span data-ttu-id="96a29-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="96a29-105">Remarks</span></span>  
 <span data-ttu-id="96a29-106">A palavra-chave para uma referência C# nula C++ em e é nula.</span><span class="sxs-lookup"><span data-stu-id="96a29-106">The keyword for a null reference in C# and C++ is null.</span></span> <span data-ttu-id="96a29-107">A palavra-chave Microsoft Visual Basic para uma referência `Nothing`nula é, mas você `{x:Null}` sempre usa como o uso do XAML, independentemente do idioma code-behind que você associar ao XAML.</span><span class="sxs-lookup"><span data-stu-id="96a29-107">The Microsoft Visual Basic keyword for a null reference is `Nothing`, but you always use `{x:Null}` as the XAML usage regardless which code-behind language you associate with the XAML.</span></span>  
  
 <span data-ttu-id="96a29-108">A `x:Null` extensão de marcação não tem nenhuma propriedade configurável.</span><span class="sxs-lookup"><span data-stu-id="96a29-108">The `x:Null` markup extension has no settable properties.</span></span>  
  
 <span data-ttu-id="96a29-109">Um uso nulo geralmente é associado à exposição de membro XAML de um valor <xref:System.Nullable%601> CLR.</span><span class="sxs-lookup"><span data-stu-id="96a29-109">A null usage is often associated with the XAML member exposure of a CLR <xref:System.Nullable%601> value.</span></span>  
  
 <span data-ttu-id="96a29-110">A `x:Null` extensão de marcação, como todas as extensões de marcação XAML, usa as`{,}`chaves () para escapar a manipulação de valores de atributo para que sejam diferentes de literais ou referências de manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="96a29-110">The `x:Null` markup extension, like all XAML markup extensions, uses the braces (`{,}`) for escaping the handling of attribute values to be other than literals or event-handler references.</span></span> <span data-ttu-id="96a29-111">A sintaxe de atributo é a sintaxe usada com mais frequência com essa extensão de marcação.</span><span class="sxs-lookup"><span data-stu-id="96a29-111">Attribute syntax is the syntax most frequently used with this markup extension.</span></span> <span data-ttu-id="96a29-112">Uma sintaxe `<x:Null />` de elemento de objeto é tecnicamente possível, mas raramente é usada `x:Null` porque a extensão de marcação não tem parâmetros posicionais ou argumentos de construção.</span><span class="sxs-lookup"><span data-stu-id="96a29-112">An object element syntax `<x:Null />` is technically possible, but is rarely used because the `x:Null` markup extension has no positional parameters or construction arguments.</span></span>  
  
 <span data-ttu-id="96a29-113">Para obter informações sobre extensões de marcação, consulte [extensões de marcação e WPF XAML](../wpf/advanced/markup-extensions-and-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="96a29-113">For information about markup extensions, see [Markup Extensions and WPF XAML](../wpf/advanced/markup-extensions-and-wpf-xaml.md).</span></span>  
  
 <span data-ttu-id="96a29-114">Em .NET Framework serviços XAML, o tratamento para essa extensão de marcação é definido pela <xref:System.Windows.Markup.NullExtension> classe.</span><span class="sxs-lookup"><span data-stu-id="96a29-114">In .NET Framework XAML Services, the handling for this markup extension is defined by the <xref:System.Windows.Markup.NullExtension> class.</span></span>  
  
## <a name="wpf-usage-notes"></a><span data-ttu-id="96a29-115">Observações de uso do WPF</span><span class="sxs-lookup"><span data-stu-id="96a29-115">WPF Usage Notes</span></span>  
 <span data-ttu-id="96a29-116">Observe que `null` não é necessariamente o valor inicial de redefinição para uma propriedade de dependência de tipo de referência.</span><span class="sxs-lookup"><span data-stu-id="96a29-116">Note that `null` is not necessarily the initial unset value for a reference-type dependency property.</span></span> <span data-ttu-id="96a29-117">O valor padrão inicial pode variar para cada propriedade de dependência e pode ser baseado em metadados específicos da propriedade.</span><span class="sxs-lookup"><span data-stu-id="96a29-117">The initial default value can vary for each dependency property and can be based on property-specific metadata.</span></span> <span data-ttu-id="96a29-118">Muitas propriedades de dependência não são `null` aceitas como um valor, seja por meio de marcação ou código, devido a suas implementações de retorno de chamada de validação.</span><span class="sxs-lookup"><span data-stu-id="96a29-118">Many dependency properties do not accept `null` as a value, either through markup or code because of their validation callback implementations.</span></span> <span data-ttu-id="96a29-119">Para obter mais informações sobre propriedades de dependência, consulte [visão geral das propriedades de dependência](../wpf/advanced/dependency-properties-overview.md).</span><span class="sxs-lookup"><span data-stu-id="96a29-119">For more information about dependency properties, see [Dependency Properties Overview](../wpf/advanced/dependency-properties-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96a29-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="96a29-120">See also</span></span>

- <xref:System.Windows.DependencyProperty.UnsetValue>
- [<span data-ttu-id="96a29-121">Visão geral de XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="96a29-121">XAML Overview (WPF)</span></span>](../wpf/advanced/xaml-overview-wpf.md)
- [<span data-ttu-id="96a29-122">Extensões de marcação e XAML do WPF</span><span class="sxs-lookup"><span data-stu-id="96a29-122">Markup Extensions and WPF XAML</span></span>](../wpf/advanced/markup-extensions-and-wpf-xaml.md)
