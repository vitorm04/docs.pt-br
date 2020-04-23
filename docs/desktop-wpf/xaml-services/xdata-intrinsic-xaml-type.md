---
title: Tipo intrínseco x:XData (XAML)
ms.date: 03/30/2017
f1_keywords:
- x:XData
- XData
- xXData
helpviewer_keywords:
- XAML [XAML Services], x:XData directive element
- XData in XAML [XAML Services]
- x:XData XAML directive element [XAML Services]
ms.assetid: 7ce209c2-621b-4977-b643-565f7e663534
ms.openlocfilehash: b7f0954158988db107feb4a6c51ba81d5db11dcb
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071538"
---
# <a name="xxdata-intrinsic-xaml-type"></a><span data-ttu-id="8157f-102">Tipo intrínseco x:XData (XAML)</span><span class="sxs-lookup"><span data-stu-id="8157f-102">x:XData Intrinsic XAML Type</span></span>
<span data-ttu-id="8157f-103">Permite a colocação de ilhas de dados XML dentro de uma produção XAML.</span><span class="sxs-lookup"><span data-stu-id="8157f-103">Enables placement of XML data islands within a XAML production.</span></span> <span data-ttu-id="8157f-104">Os elementos `x:XData` XML dentro não devem ser tratados por processadores XAML como se fossem parte do namespace xaml padrão de ação ou qualquer outro espaço de nome XAML.</span><span class="sxs-lookup"><span data-stu-id="8157f-104">XML elements within `x:XData` should not be treated by XAML processors as if they are a part of the acting default XAML namespace or any other XAML namespace.</span></span> <span data-ttu-id="8157f-105">`x:XData`pode conter XML arbitrário bem formado.</span><span class="sxs-lookup"><span data-stu-id="8157f-105">`x:XData` can contain arbitrary well-formed XML.</span></span>

## <a name="xaml-object-element-usage"></a><span data-ttu-id="8157f-106">Uso de elemento Object do XAML</span><span class="sxs-lookup"><span data-stu-id="8157f-106">XAML Object Element Usage</span></span>

```xaml
<x:XData>
  <elementDataRoot>
    [elementData]
  </elementDataRoot>
</x:XData>
```

## <a name="xaml-values"></a><span data-ttu-id="8157f-107">Valores XAML</span><span class="sxs-lookup"><span data-stu-id="8157f-107">XAML Values</span></span>

|||
|-|-|
|`elementDataRoot`|<span data-ttu-id="8157f-108">O único elemento raiz da ilha de dados fechado.</span><span class="sxs-lookup"><span data-stu-id="8157f-108">The single root element of the enclosed data island.</span></span> <span data-ttu-id="8157f-109">Para a maioria dos consumidores eventuais, XML que não tem uma única raiz é considerado inválido.</span><span class="sxs-lookup"><span data-stu-id="8157f-109">For most eventual consumers, XML that does not have a single root is considered invalid.</span></span> <span data-ttu-id="8157f-110">Em particular, uma única raiz `x:XData` é necessária se a destinação como uma fonte de dados XML para WPF ou muitas outras tecnologias que usam fontes XML para vinculação de dados.</span><span class="sxs-lookup"><span data-stu-id="8157f-110">In particular, a single root is required if the `x:XData` is intended as an XML data source for WPF or many other technologies that use XML sources for data binding.</span></span>|
|`[elementData]`|<span data-ttu-id="8157f-111">Opcional.</span><span class="sxs-lookup"><span data-stu-id="8157f-111">Optional.</span></span> <span data-ttu-id="8157f-112">XML que representa os dados XML.</span><span class="sxs-lookup"><span data-stu-id="8157f-112">XML that represents the XML data.</span></span> <span data-ttu-id="8157f-113">Qualquer número de elementos pode ser contido como dados de elementos e elementos aninhados podem ser contidos em outros elementos; no entanto, as regras gerais do XML se aplicam.</span><span class="sxs-lookup"><span data-stu-id="8157f-113">Any number of elements can be contained as element data and nested elements can be contained in other elements; however, the general rules of XML apply.</span></span>|

## <a name="remarks"></a><span data-ttu-id="8157f-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="8157f-114">Remarks</span></span>

<span data-ttu-id="8157f-115">Os elementos XML dentro de um `x:XData` objeto podem redeclarar todos os espaços de nome e prefixos possíveis do XMLDOM contendo dentro dos dados.</span><span class="sxs-lookup"><span data-stu-id="8157f-115">The XML elements within an `x:XData` object can re-declare all possible namespaces and prefixes of the containing XMLDOM within the data.</span></span>

<span data-ttu-id="8157f-116">O acesso programático aos `x:XData` dados XML e ao tipo XAML intrínseco <xref:System.Windows.Markup.XData> é possível em Serviços .NET XAML através da classe.</span><span class="sxs-lookup"><span data-stu-id="8157f-116">Programmatic access to XML data and the `x:XData` intrinsic XAML type is possible in .NET XAML Services through the <xref:System.Windows.Markup.XData> class.</span></span>

## <a name="wpf-usage-notes"></a><span data-ttu-id="8157f-117">Notas de uso do WPF</span><span class="sxs-lookup"><span data-stu-id="8157f-117">WPF Usage Notes</span></span>

<span data-ttu-id="8157f-118">O `x:XData` objeto é usado principalmente como <xref:System.Windows.Data.XmlDataProvider>objeto infantil de um , ou <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> alternativamente, como objeto filho da propriedade (em XAML, isso é tipicamente expresso em sintaxe de elemento de propriedade).</span><span class="sxs-lookup"><span data-stu-id="8157f-118">The `x:XData` object is primarily used as a child object of an <xref:System.Windows.Data.XmlDataProvider>, or alternatively, as the child object of the <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> property (in XAML, this is typically expressed in property element syntax).</span></span>

<span data-ttu-id="8157f-119">Os dados devem normalmente redefinir o namespace xml base dentro da ilha de dados para ser um novo namespace XML padrão (definido como uma seqüência de string vazia).</span><span class="sxs-lookup"><span data-stu-id="8157f-119">The data should typically redefine the base XML namespace within the data island to be a new default XML namespace (set to an empty string).</span></span> <span data-ttu-id="8157f-120">Isso é mais fácil para <xref:System.Windows.Data.Binding.XPath%2A> ilhas de dados simples porque as expressões que são usadas para referenciar e vincular aos dados podem evitar a inclusão de prefixos.</span><span class="sxs-lookup"><span data-stu-id="8157f-120">This is easiest for simple data islands because the <xref:System.Windows.Data.Binding.XPath%2A> expressions that are used to reference and bind to the data can avoid inclusion of prefixes.</span></span> <span data-ttu-id="8157f-121">Ilhas de dados mais complexas podem definir vários prefixos para os dados e usar um prefixo específico para o namespace XML na raiz.</span><span class="sxs-lookup"><span data-stu-id="8157f-121">More complex data islands might define multiple prefixes for the data and use a specific prefix for the XML namespace at the root.</span></span> <span data-ttu-id="8157f-122">Neste caso, <xref:System.Windows.Data.Binding.XPath%2A> todas as referências de expressão devem incluir o prefixo mapeado pelo namespace apropriado.</span><span class="sxs-lookup"><span data-stu-id="8157f-122">In this case, all <xref:System.Windows.Data.Binding.XPath%2A> expression references should include the appropriate namespace-mapped prefix.</span></span> <span data-ttu-id="8157f-123">Para obter mais informações, consulte [Visão geral de vinculação de dados](../data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="8157f-123">For more information, see [Data Binding Overview](../data/data-binding-overview.md).</span></span>

<span data-ttu-id="8157f-124">Tecnicamente, `x:XData` pode ser usado como o <xref:System.Xml.Serialization.IXmlSerializable>conteúdo de qualquer propriedade do tipo.</span><span class="sxs-lookup"><span data-stu-id="8157f-124">Technically, `x:XData` can be used as the content of any property of type <xref:System.Xml.Serialization.IXmlSerializable>.</span></span> <span data-ttu-id="8157f-125">No <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> entanto, é a única implementação proeminente.</span><span class="sxs-lookup"><span data-stu-id="8157f-125">However, <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> is the only prominent implementation.</span></span>

## <a name="see-also"></a><span data-ttu-id="8157f-126">Confira também</span><span class="sxs-lookup"><span data-stu-id="8157f-126">See also</span></span>

- <xref:System.Windows.Data.XmlDataProvider>
- [<span data-ttu-id="8157f-127">Visão geral da vinculação de dados</span><span class="sxs-lookup"><span data-stu-id="8157f-127">Data Binding Overview</span></span>](../data/data-binding-overview.md)
- [<span data-ttu-id="8157f-128">Extensão de marcação de associação</span><span class="sxs-lookup"><span data-stu-id="8157f-128">Binding Markup Extension</span></span>](../../framework/wpf/advanced/binding-markup-extension.md)
