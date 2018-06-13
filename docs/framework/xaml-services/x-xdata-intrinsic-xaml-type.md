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
ms.openlocfilehash: 3a16379fd6104342529723bf6d0bc9fb4762cf92
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33565357"
---
# <a name="xxdata-intrinsic-xaml-type"></a><span data-ttu-id="af494-102">Tipo intrínseco x:XData (XAML)</span><span class="sxs-lookup"><span data-stu-id="af494-102">x:XData Intrinsic XAML Type</span></span>
<span data-ttu-id="af494-103">Habilita o posicionamento de ilhas de dados dentro de uma produção XAML.</span><span class="sxs-lookup"><span data-stu-id="af494-103">Enables placement of XML data islands within a XAML production.</span></span> <span data-ttu-id="af494-104">Elementos XML no `x:XData` não devem ser tratados por processadores XAML, como se fossem uma parte da ação padrão do namespace XAML ou qualquer outro namespace XAML.</span><span class="sxs-lookup"><span data-stu-id="af494-104">XML elements within `x:XData` should not be treated by XAML processors as if they are a part of the acting default XAML namespace or any other XAML namespace.</span></span> <span data-ttu-id="af494-105">`x:XData` pode conter XML bem formado arbitrário.</span><span class="sxs-lookup"><span data-stu-id="af494-105">`x:XData` can contain arbitrary well-formed XML.</span></span>  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="af494-106">Uso de elemento Object do XAML</span><span class="sxs-lookup"><span data-stu-id="af494-106">XAML Object Element Usage</span></span>  
  
```  
<x:XData>  
  <elementDataRoot>  
    [elementData]  
  </elementDataRoot>  
</x:XData>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="af494-107">Valores XAML</span><span class="sxs-lookup"><span data-stu-id="af494-107">XAML Values</span></span>  
  
|||  
|-|-|  
|`elementDataRoot`|<span data-ttu-id="af494-108">O elemento raiz único da ilha de dados incluídos.</span><span class="sxs-lookup"><span data-stu-id="af494-108">The single root element of the enclosed data island.</span></span> <span data-ttu-id="af494-109">Para a maioria dos consumidores eventual, XML que não tem uma única raiz é considerado inválido.</span><span class="sxs-lookup"><span data-stu-id="af494-109">For most eventual consumers, XML that does not have a single root is considered invalid.</span></span> <span data-ttu-id="af494-110">Em particular, uma única raiz é necessária se o `x:XData` destina-se como uma fonte de dados XML para WPF ou muitas outras tecnologias que usam fontes de XML para associação de dados.</span><span class="sxs-lookup"><span data-stu-id="af494-110">In particular, a single root is required if the `x:XData` is intended as an XML data source for WPF or many other technologies that use XML sources for data binding.</span></span>|  
|`[elementData]`|<span data-ttu-id="af494-111">Opcional.</span><span class="sxs-lookup"><span data-stu-id="af494-111">Optional.</span></span> <span data-ttu-id="af494-112">XML que representa os dados XML.</span><span class="sxs-lookup"><span data-stu-id="af494-112">XML that represents the XML data.</span></span> <span data-ttu-id="af494-113">Qualquer número de elementos pode ser contido como dados de elemento e elementos aninhados podem estar contidos em outros elementos; No entanto, se aplicam às regras gerais do XML.</span><span class="sxs-lookup"><span data-stu-id="af494-113">Any number of elements can be contained as element data and nested elements can be contained in other elements; however, the general rules of XML apply.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="af494-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="af494-114">Remarks</span></span>  
 <span data-ttu-id="af494-115">Os elementos de uma `x:XData` objeto pode declarar novamente todos os possíveis namespaces e prefixos do recipiente XMLDOM dentro dos dados.</span><span class="sxs-lookup"><span data-stu-id="af494-115">The XML elements within an `x:XData` object can re-declare all possible namespaces and prefixes of the containing XMLDOM within the data.</span></span>  
  
 <span data-ttu-id="af494-116">Acesso programático aos dados XML e o `x:XData` tipo intrínseco do XAML é possível em serviços XAML do .NET Framework por meio de <xref:System.Windows.Markup.XData> classe.</span><span class="sxs-lookup"><span data-stu-id="af494-116">Programmatic access to XML data and the `x:XData` intrinsic XAML type is possible in .NET Framework XAML Services through the <xref:System.Windows.Markup.XData> class.</span></span>  
  
## <a name="wpf-usage-notes"></a><span data-ttu-id="af494-117">Observações de uso do WPF</span><span class="sxs-lookup"><span data-stu-id="af494-117">WPF Usage Notes</span></span>  
 <span data-ttu-id="af494-118">O `x:XData` objeto é usado principalmente como um objeto filho de um <xref:System.Windows.Data.XmlDataProvider>, ou como alternativa, como o objeto filho do <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> propriedade (em XAML, isso é geralmente expresso na sintaxe de elemento de propriedade).</span><span class="sxs-lookup"><span data-stu-id="af494-118">The `x:XData` object is primarily used as a child object of an <xref:System.Windows.Data.XmlDataProvider>, or alternatively, as the child object of the <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> property (in XAML, this is typically expressed in property element syntax).</span></span>  
  
 <span data-ttu-id="af494-119">Os dados normalmente devem redefinir o namespace XML base dentro da ilha de dados para um novo namespace de XML padrão (definido como uma cadeia de caracteres vazia).</span><span class="sxs-lookup"><span data-stu-id="af494-119">The data should typically redefine the base XML namespace within the data island to be a new default XML namespace (set to an empty string).</span></span> <span data-ttu-id="af494-120">Isso é mais fácil para ilhas de dados simples, porque o <xref:System.Windows.Data.Binding.XPath%2A> expressões que são usadas para referenciar e associar os dados podem evitar a inclusão de prefixos.</span><span class="sxs-lookup"><span data-stu-id="af494-120">This is easiest for simple data islands because the <xref:System.Windows.Data.Binding.XPath%2A> expressions that are used to reference and bind to the data can avoid inclusion of prefixes.</span></span> <span data-ttu-id="af494-121">Ilhas de dados mais complexas podem definir vários prefixos para os dados e usar um prefixo específico para o namespace XML na raiz.</span><span class="sxs-lookup"><span data-stu-id="af494-121">More complex data islands might define multiple prefixes for the data and use a specific prefix for the XML namespace at the root.</span></span> <span data-ttu-id="af494-122">Nesse caso, todos os <xref:System.Windows.Data.Binding.XPath%2A> referências de expressão devem incluir o prefixo mapeado em namespace apropriado.</span><span class="sxs-lookup"><span data-stu-id="af494-122">In this case, all <xref:System.Windows.Data.Binding.XPath%2A> expression references should include the appropriate namespace-mapped prefix.</span></span> <span data-ttu-id="af494-123">Para obter mais informações, consulte [Visão geral de vinculação de dados](../../../docs/framework/wpf/data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="af494-123">For more information, see [Data Binding Overview](../../../docs/framework/wpf/data/data-binding-overview.md).</span></span>  
  
 <span data-ttu-id="af494-124">Tecnicamente, `x:XData` pode ser usado como o conteúdo de qualquer propriedade do tipo <xref:System.Xml.Serialization.IXmlSerializable>.</span><span class="sxs-lookup"><span data-stu-id="af494-124">Technically, `x:XData` can be used as the content of any property of type <xref:System.Xml.Serialization.IXmlSerializable>.</span></span> <span data-ttu-id="af494-125">No entanto, <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> é a implementação somente destacada.</span><span class="sxs-lookup"><span data-stu-id="af494-125">However, <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> is the only prominent implementation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af494-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="af494-126">See Also</span></span>  
 <xref:System.Windows.Data.XmlDataProvider>  
 [<span data-ttu-id="af494-127">Visão geral da vinculação de dados</span><span class="sxs-lookup"><span data-stu-id="af494-127">Data Binding Overview</span></span>](../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="af494-128">Extensão de marcação de associação</span><span class="sxs-lookup"><span data-stu-id="af494-128">Binding Markup Extension</span></span>](../../../docs/framework/wpf/advanced/binding-markup-extension.md)
