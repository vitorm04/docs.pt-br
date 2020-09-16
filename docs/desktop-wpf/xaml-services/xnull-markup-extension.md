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
ms.openlocfilehash: f4971d61d11ec14eaeac2d2f202353e4921b9325
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90549438"
---
# <a name="xnull-markup-extension"></a><span data-ttu-id="22769-102">Extensão de marcação x:Null</span><span class="sxs-lookup"><span data-stu-id="22769-102">x:Null Markup Extension</span></span>

<span data-ttu-id="22769-103">Especifica `null` como um valor para um membro XAML.</span><span class="sxs-lookup"><span data-stu-id="22769-103">Specifies `null` as a value for a XAML member.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="22769-104">Uso do Atributo XAML</span><span class="sxs-lookup"><span data-stu-id="22769-104">XAML Attribute Usage</span></span>

```xaml
<object property="{x:Null}" .../>
```

## <a name="remarks"></a><span data-ttu-id="22769-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="22769-105">Remarks</span></span>

<span data-ttu-id="22769-106">A palavra-chave para uma referência nula em C# e C++ é nula.</span><span class="sxs-lookup"><span data-stu-id="22769-106">The keyword for a null reference in C# and C++ is null.</span></span> <span data-ttu-id="22769-107">A palavra-chave Microsoft Visual Basic para uma referência nula é `Nothing` , mas você sempre usa `{x:Null}` como o uso do XAML, independentemente do idioma code-behind que você associar ao XAML.</span><span class="sxs-lookup"><span data-stu-id="22769-107">The Microsoft Visual Basic keyword for a null reference is `Nothing`, but you always use `{x:Null}` as the XAML usage regardless which code-behind language you associate with the XAML.</span></span>

<span data-ttu-id="22769-108">A `x:Null` extensão de marcação não tem nenhuma propriedade configurável.</span><span class="sxs-lookup"><span data-stu-id="22769-108">The `x:Null` markup extension has no settable properties.</span></span>

<span data-ttu-id="22769-109">Um uso nulo geralmente é associado à exposição de membro XAML de um <xref:System.Nullable%601> valor CLR.</span><span class="sxs-lookup"><span data-stu-id="22769-109">A null usage is often associated with the XAML member exposure of a CLR <xref:System.Nullable%601> value.</span></span>

<span data-ttu-id="22769-110">A `x:Null` extensão de marcação, como todas as extensões de marcação XAML, usa as chaves ( `{,}` ) para escapar a manipulação de valores de atributo para que sejam diferentes de literais ou referências de manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="22769-110">The `x:Null` markup extension, like all XAML markup extensions, uses the braces (`{,}`) for escaping the handling of attribute values to be other than literals or event-handler references.</span></span> <span data-ttu-id="22769-111">A sintaxe de atributo é a sintaxe usada com mais frequência com essa extensão de marcação.</span><span class="sxs-lookup"><span data-stu-id="22769-111">Attribute syntax is the syntax most frequently used with this markup extension.</span></span> <span data-ttu-id="22769-112">Uma sintaxe de elemento de objeto `<x:Null />` é tecnicamente possível, mas raramente é usada porque a `x:Null` extensão de marcação não tem parâmetros posicionais ou argumentos de construção.</span><span class="sxs-lookup"><span data-stu-id="22769-112">An object element syntax `<x:Null />` is technically possible, but is rarely used because the `x:Null` markup extension has no positional parameters or construction arguments.</span></span>

<span data-ttu-id="22769-113">Para obter informações sobre extensões de marcação, consulte [extensões de marcação e WPF XAML](/dotnet/desktop/wpf/advanced/markup-extensions-and-wpf-xaml).</span><span class="sxs-lookup"><span data-stu-id="22769-113">For information about markup extensions, see [Markup Extensions and WPF XAML](/dotnet/desktop/wpf/advanced/markup-extensions-and-wpf-xaml).</span></span>

<span data-ttu-id="22769-114">Nos serviços XAML do .NET, o tratamento para essa extensão de marcação é definido pela <xref:System.Windows.Markup.NullExtension> classe.</span><span class="sxs-lookup"><span data-stu-id="22769-114">In .NET XAML Services, the handling for this markup extension is defined by the <xref:System.Windows.Markup.NullExtension> class.</span></span>

## <a name="wpf-usage-notes"></a><span data-ttu-id="22769-115">Notas de uso do WPF</span><span class="sxs-lookup"><span data-stu-id="22769-115">WPF Usage Notes</span></span>

<span data-ttu-id="22769-116">Observe que `null` não é necessariamente o valor inicial de redefinição para uma propriedade de dependência de tipo de referência.</span><span class="sxs-lookup"><span data-stu-id="22769-116">Note that `null` is not necessarily the initial unset value for a reference-type dependency property.</span></span> <span data-ttu-id="22769-117">O valor padrão inicial pode variar para cada propriedade de dependência e pode ser baseado em metadados específicos da propriedade.</span><span class="sxs-lookup"><span data-stu-id="22769-117">The initial default value can vary for each dependency property and can be based on property-specific metadata.</span></span> <span data-ttu-id="22769-118">Muitas propriedades de dependência não são aceitas `null` como um valor, seja por meio de marcação ou código, devido a suas implementações de retorno de chamada de validação.</span><span class="sxs-lookup"><span data-stu-id="22769-118">Many dependency properties do not accept `null` as a value, either through markup or code because of their validation callback implementations.</span></span> <span data-ttu-id="22769-119">Para obter mais informações sobre propriedades de dependência, consulte [visão geral das propriedades de dependência](/dotnet/desktop/wpf/advanced/dependency-properties-overview).</span><span class="sxs-lookup"><span data-stu-id="22769-119">For more information about dependency properties, see [Dependency Properties Overview](/dotnet/desktop/wpf/advanced/dependency-properties-overview).</span></span>

## <a name="see-also"></a><span data-ttu-id="22769-120">Confira também</span><span class="sxs-lookup"><span data-stu-id="22769-120">See also</span></span>

- <xref:System.Windows.DependencyProperty.UnsetValue>
- [<span data-ttu-id="22769-121">Visão geral de XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="22769-121">XAML Overview (WPF)</span></span>](../fundamentals/xaml.md)
- [<span data-ttu-id="22769-122">Extensões de marcação e XAML WPF</span><span class="sxs-lookup"><span data-stu-id="22769-122">Markup Extensions and WPF XAML</span></span>](/dotnet/desktop/wpf/advanced/markup-extensions-and-wpf-xaml)
