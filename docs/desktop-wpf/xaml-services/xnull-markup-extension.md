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
ms.openlocfilehash: b83e893f951c15eca69fbb6b002369dd723ca469
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071426"
---
# <a name="xnull-markup-extension"></a><span data-ttu-id="a4d2f-102">Extensão de marcação x:Null</span><span class="sxs-lookup"><span data-stu-id="a4d2f-102">x:Null Markup Extension</span></span>

<span data-ttu-id="a4d2f-103">Especifica `null` como um valor para um membro XAML.</span><span class="sxs-lookup"><span data-stu-id="a4d2f-103">Specifies `null` as a value for a XAML member.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="a4d2f-104">Uso do Atributo XAML</span><span class="sxs-lookup"><span data-stu-id="a4d2f-104">XAML Attribute Usage</span></span>

```xaml
<object property="{x:Null}" .../>
```

## <a name="remarks"></a><span data-ttu-id="a4d2f-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="a4d2f-105">Remarks</span></span>

<span data-ttu-id="a4d2f-106">A palavra-chave para uma referência nula em C# e C++ é nula.</span><span class="sxs-lookup"><span data-stu-id="a4d2f-106">The keyword for a null reference in C# and C++ is null.</span></span> <span data-ttu-id="a4d2f-107">A palavra-chave Microsoft Visual Basic `Nothing`para uma `{x:Null}` referência nula é , mas você sempre usa como o uso XAML, independentemente de qual linguagem de código atrás você associa com o XAML.</span><span class="sxs-lookup"><span data-stu-id="a4d2f-107">The Microsoft Visual Basic keyword for a null reference is `Nothing`, but you always use `{x:Null}` as the XAML usage regardless which code-behind language you associate with the XAML.</span></span>

<span data-ttu-id="a4d2f-108">A `x:Null` extensão de marcação não tem propriedades definidas.</span><span class="sxs-lookup"><span data-stu-id="a4d2f-108">The `x:Null` markup extension has no settable properties.</span></span>

<span data-ttu-id="a4d2f-109">Um uso nulo é frequentemente associado com a <xref:System.Nullable%601> exposição do membro XAML de um valor CLR.</span><span class="sxs-lookup"><span data-stu-id="a4d2f-109">A null usage is often associated with the XAML member exposure of a CLR <xref:System.Nullable%601> value.</span></span>

<span data-ttu-id="a4d2f-110">A `x:Null` extensão de marcação, como todas as extensões`{,}`de marcação XAML, usa as chaves ( ) para escapar do manuseio de valores de atributo suscitados por literais ou referências de manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="a4d2f-110">The `x:Null` markup extension, like all XAML markup extensions, uses the braces (`{,}`) for escaping the handling of attribute values to be other than literals or event-handler references.</span></span> <span data-ttu-id="a4d2f-111">Sintaxe de atributo é a sintaxe mais usada com esta extensão de marcação.</span><span class="sxs-lookup"><span data-stu-id="a4d2f-111">Attribute syntax is the syntax most frequently used with this markup extension.</span></span> <span data-ttu-id="a4d2f-112">Uma sintaxe `<x:Null />` de elemento de objeto é `x:Null` tecnicamente possível, mas raramente é usada porque a extensão de marcação não tem parâmetros posicionais ou argumentos de construção.</span><span class="sxs-lookup"><span data-stu-id="a4d2f-112">An object element syntax `<x:Null />` is technically possible, but is rarely used because the `x:Null` markup extension has no positional parameters or construction arguments.</span></span>

<span data-ttu-id="a4d2f-113">Para obter informações sobre extensões de marcação, consulte [Extensões de marcação e WPF XAML](../../framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="a4d2f-113">For information about markup extensions, see [Markup Extensions and WPF XAML](../../framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).</span></span>

<span data-ttu-id="a4d2f-114">Nos Serviços XAML .NET, o manuseio desta extensão de marcação é definido pela <xref:System.Windows.Markup.NullExtension> classe.</span><span class="sxs-lookup"><span data-stu-id="a4d2f-114">In .NET XAML Services, the handling for this markup extension is defined by the <xref:System.Windows.Markup.NullExtension> class.</span></span>

## <a name="wpf-usage-notes"></a><span data-ttu-id="a4d2f-115">Notas de uso do WPF</span><span class="sxs-lookup"><span data-stu-id="a4d2f-115">WPF Usage Notes</span></span>

<span data-ttu-id="a4d2f-116">Observe `null` que não é necessariamente o valor inicial não definido para uma propriedade de dependência de tipo de referência.</span><span class="sxs-lookup"><span data-stu-id="a4d2f-116">Note that `null` is not necessarily the initial unset value for a reference-type dependency property.</span></span> <span data-ttu-id="a4d2f-117">O valor padrão inicial pode variar para cada propriedade de dependência e pode ser baseado em metadados específicos da propriedade.</span><span class="sxs-lookup"><span data-stu-id="a4d2f-117">The initial default value can vary for each dependency property and can be based on property-specific metadata.</span></span> <span data-ttu-id="a4d2f-118">Muitas propriedades de dependência `null` não aceitam como valor, seja através de marcação ou código por causa de suas implementações de chamada de validação.</span><span class="sxs-lookup"><span data-stu-id="a4d2f-118">Many dependency properties do not accept `null` as a value, either through markup or code because of their validation callback implementations.</span></span> <span data-ttu-id="a4d2f-119">Para obter mais informações sobre propriedades de dependência, consulte [Visão geral das propriedades de dependência](../../framework/wpf/advanced/dependency-properties-overview.md).</span><span class="sxs-lookup"><span data-stu-id="a4d2f-119">For more information about dependency properties, see [Dependency Properties Overview](../../framework/wpf/advanced/dependency-properties-overview.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a4d2f-120">Confira também</span><span class="sxs-lookup"><span data-stu-id="a4d2f-120">See also</span></span>

- <xref:System.Windows.DependencyProperty.UnsetValue>
- [<span data-ttu-id="a4d2f-121">Visão geral de XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="a4d2f-121">XAML Overview (WPF)</span></span>](../fundamentals/xaml.md)
- [<span data-ttu-id="a4d2f-122">Extensões de marcação e XAML WPF</span><span class="sxs-lookup"><span data-stu-id="a4d2f-122">Markup Extensions and WPF XAML</span></span>](../../framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
