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
ms.openlocfilehash: c5f729837b9bb52ca7d232ca66b58e283a2bcefc
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053707"
---
# <a name="xxdata-intrinsic-xaml-type"></a><span data-ttu-id="1dde4-102">Tipo intrínseco x:XData (XAML)</span><span class="sxs-lookup"><span data-stu-id="1dde4-102">x:XData Intrinsic XAML Type</span></span>
<span data-ttu-id="1dde4-103">Habilita o posicionamento das ilhas de dados XML em uma produção XAML.</span><span class="sxs-lookup"><span data-stu-id="1dde4-103">Enables placement of XML data islands within a XAML production.</span></span> <span data-ttu-id="1dde4-104">Elementos XML dentro `x:XData` não devem ser tratados por processadores XAML como se eles fossem uma parte do namespace XAML padrão agindo ou qualquer outro namespace XAML.</span><span class="sxs-lookup"><span data-stu-id="1dde4-104">XML elements within `x:XData` should not be treated by XAML processors as if they are a part of the acting default XAML namespace or any other XAML namespace.</span></span> <span data-ttu-id="1dde4-105">`x:XData`pode conter XML bem formado arbitrário.</span><span class="sxs-lookup"><span data-stu-id="1dde4-105">`x:XData` can contain arbitrary well-formed XML.</span></span>  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="1dde4-106">Uso de elemento Object do XAML</span><span class="sxs-lookup"><span data-stu-id="1dde4-106">XAML Object Element Usage</span></span>  
  
```xaml  
<x:XData>  
  <elementDataRoot>  
    [elementData]  
  </elementDataRoot>  
</x:XData>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="1dde4-107">Valores XAML</span><span class="sxs-lookup"><span data-stu-id="1dde4-107">XAML Values</span></span>  
  
|||  
|-|-|  
|`elementDataRoot`|<span data-ttu-id="1dde4-108">O elemento raiz único da ilha de dados embutida.</span><span class="sxs-lookup"><span data-stu-id="1dde4-108">The single root element of the enclosed data island.</span></span> <span data-ttu-id="1dde4-109">Para os consumidores mais eventuales, o XML que não tem uma única raiz é considerado inválido.</span><span class="sxs-lookup"><span data-stu-id="1dde4-109">For most eventual consumers, XML that does not have a single root is considered invalid.</span></span> <span data-ttu-id="1dde4-110">Em particular, uma única raiz é necessária se o `x:XData` se destina como uma fonte de dados XML para WPF ou muitas outras tecnologias que usam fontes XML para vinculação de dados.</span><span class="sxs-lookup"><span data-stu-id="1dde4-110">In particular, a single root is required if the `x:XData` is intended as an XML data source for WPF or many other technologies that use XML sources for data binding.</span></span>|  
|`[elementData]`|<span data-ttu-id="1dde4-111">Opcional.</span><span class="sxs-lookup"><span data-stu-id="1dde4-111">Optional.</span></span> <span data-ttu-id="1dde4-112">XML que representa os dados XML.</span><span class="sxs-lookup"><span data-stu-id="1dde4-112">XML that represents the XML data.</span></span> <span data-ttu-id="1dde4-113">Qualquer número de elementos pode ser contido como dados de elemento e elementos aninhados podem estar contidos em outros elementos; no entanto, as regras gerais do XML se aplicam.</span><span class="sxs-lookup"><span data-stu-id="1dde4-113">Any number of elements can be contained as element data and nested elements can be contained in other elements; however, the general rules of XML apply.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1dde4-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="1dde4-114">Remarks</span></span>  
 <span data-ttu-id="1dde4-115">Os elementos XML dentro de `x:XData` um objeto podem redeclarar todos os namespaces e prefixos possíveis de XMLDOM dentro dos dados.</span><span class="sxs-lookup"><span data-stu-id="1dde4-115">The XML elements within an `x:XData` object can re-declare all possible namespaces and prefixes of the containing XMLDOM within the data.</span></span>  
  
 <span data-ttu-id="1dde4-116">O acesso programático a dados XML `x:XData` e o tipo intrínseco de XAML é possível em .NET Framework serviços <xref:System.Windows.Markup.XData> XAML por meio da classe.</span><span class="sxs-lookup"><span data-stu-id="1dde4-116">Programmatic access to XML data and the `x:XData` intrinsic XAML type is possible in .NET Framework XAML Services through the <xref:System.Windows.Markup.XData> class.</span></span>  
  
## <a name="wpf-usage-notes"></a><span data-ttu-id="1dde4-117">Observações de uso do WPF</span><span class="sxs-lookup"><span data-stu-id="1dde4-117">WPF Usage Notes</span></span>  
 <span data-ttu-id="1dde4-118">O `x:XData` objeto é usado principalmente como um objeto filho de um <xref:System.Windows.Data.XmlDataProvider>ou, como alternativa, como <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> o objeto filho da propriedade (em XAML, normalmente é expresso em sintaxe de elemento de propriedade).</span><span class="sxs-lookup"><span data-stu-id="1dde4-118">The `x:XData` object is primarily used as a child object of an <xref:System.Windows.Data.XmlDataProvider>, or alternatively, as the child object of the <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> property (in XAML, this is typically expressed in property element syntax).</span></span>  
  
 <span data-ttu-id="1dde4-119">Os dados normalmente devem redefinir o namespace XML base dentro da ilha de dados para ser um novo namespace XML padrão (definido como uma cadeia de caracteres vazia).</span><span class="sxs-lookup"><span data-stu-id="1dde4-119">The data should typically redefine the base XML namespace within the data island to be a new default XML namespace (set to an empty string).</span></span> <span data-ttu-id="1dde4-120">Isso é mais fácil para ilhas de dados simples porque <xref:System.Windows.Data.Binding.XPath%2A> as expressões que são usadas para referenciar e associar aos dados podem evitar a inclusão de prefixos.</span><span class="sxs-lookup"><span data-stu-id="1dde4-120">This is easiest for simple data islands because the <xref:System.Windows.Data.Binding.XPath%2A> expressions that are used to reference and bind to the data can avoid inclusion of prefixes.</span></span> <span data-ttu-id="1dde4-121">Ilhas de dados mais complexas podem definir vários prefixos para os dados e usar um prefixo específico para o namespace XML na raiz.</span><span class="sxs-lookup"><span data-stu-id="1dde4-121">More complex data islands might define multiple prefixes for the data and use a specific prefix for the XML namespace at the root.</span></span> <span data-ttu-id="1dde4-122">Nesse caso, todas as <xref:System.Windows.Data.Binding.XPath%2A> referências de expressão devem incluir o prefixo mapeado para namespace apropriado.</span><span class="sxs-lookup"><span data-stu-id="1dde4-122">In this case, all <xref:System.Windows.Data.Binding.XPath%2A> expression references should include the appropriate namespace-mapped prefix.</span></span> <span data-ttu-id="1dde4-123">Para obter mais informações, consulte [Visão geral de vinculação de dados](../wpf/data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="1dde4-123">For more information, see [Data Binding Overview](../wpf/data/data-binding-overview.md).</span></span>  
  
 <span data-ttu-id="1dde4-124">Tecnicamente, `x:XData` pode ser usado como o conteúdo de qualquer Propriedade do tipo <xref:System.Xml.Serialization.IXmlSerializable>.</span><span class="sxs-lookup"><span data-stu-id="1dde4-124">Technically, `x:XData` can be used as the content of any property of type <xref:System.Xml.Serialization.IXmlSerializable>.</span></span> <span data-ttu-id="1dde4-125">No entanto, <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> é a única implementação proeminente.</span><span class="sxs-lookup"><span data-stu-id="1dde4-125">However, <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> is the only prominent implementation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1dde4-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1dde4-126">See also</span></span>

- <xref:System.Windows.Data.XmlDataProvider>
- [<span data-ttu-id="1dde4-127">Visão geral da vinculação de dados</span><span class="sxs-lookup"><span data-stu-id="1dde4-127">Data Binding Overview</span></span>](../wpf/data/data-binding-overview.md)
- [<span data-ttu-id="1dde4-128">Extensão de marcação de associação</span><span class="sxs-lookup"><span data-stu-id="1dde4-128">Binding Markup Extension</span></span>](../wpf/advanced/binding-markup-extension.md)
