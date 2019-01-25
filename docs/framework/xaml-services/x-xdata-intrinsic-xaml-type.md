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
ms.openlocfilehash: 8b951b33242fa7e17a02133adb8fed4ce638e51e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54498041"
---
# <a name="xxdata-intrinsic-xaml-type"></a><span data-ttu-id="b6a46-102">Tipo intrínseco x:XData (XAML)</span><span class="sxs-lookup"><span data-stu-id="b6a46-102">x:XData Intrinsic XAML Type</span></span>
<span data-ttu-id="b6a46-103">Habilita o posicionamento de ilhas de dados XML dentro de uma produção de XAML.</span><span class="sxs-lookup"><span data-stu-id="b6a46-103">Enables placement of XML data islands within a XAML production.</span></span> <span data-ttu-id="b6a46-104">Elementos XML em `x:XData` não deve ser tratada pelos processadores XAML, como se eles são uma parte do namespace XAML padrão atuando ou qualquer outro namespace XAML.</span><span class="sxs-lookup"><span data-stu-id="b6a46-104">XML elements within `x:XData` should not be treated by XAML processors as if they are a part of the acting default XAML namespace or any other XAML namespace.</span></span> <span data-ttu-id="b6a46-105">`x:XData` pode conter XML bem formado arbitrário.</span><span class="sxs-lookup"><span data-stu-id="b6a46-105">`x:XData` can contain arbitrary well-formed XML.</span></span>  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="b6a46-106">Uso de elemento Object do XAML</span><span class="sxs-lookup"><span data-stu-id="b6a46-106">XAML Object Element Usage</span></span>  
  
```  
<x:XData>  
  <elementDataRoot>  
    [elementData]  
  </elementDataRoot>  
</x:XData>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="b6a46-107">Valores XAML</span><span class="sxs-lookup"><span data-stu-id="b6a46-107">XAML Values</span></span>  
  
|||  
|-|-|  
|`elementDataRoot`|<span data-ttu-id="b6a46-108">O elemento de raiz única da ilha de dados incluídos.</span><span class="sxs-lookup"><span data-stu-id="b6a46-108">The single root element of the enclosed data island.</span></span> <span data-ttu-id="b6a46-109">Para a maioria dos consumidores eventual, XML que não tem uma única raiz é considerado inválido.</span><span class="sxs-lookup"><span data-stu-id="b6a46-109">For most eventual consumers, XML that does not have a single root is considered invalid.</span></span> <span data-ttu-id="b6a46-110">Em particular, uma única raiz será necessária se o `x:XData` destina-se como uma fonte de dados XML para o WPF ou muitas outras tecnologias que usam fontes de XML para vinculação de dados.</span><span class="sxs-lookup"><span data-stu-id="b6a46-110">In particular, a single root is required if the `x:XData` is intended as an XML data source for WPF or many other technologies that use XML sources for data binding.</span></span>|  
|`[elementData]`|<span data-ttu-id="b6a46-111">Opcional.</span><span class="sxs-lookup"><span data-stu-id="b6a46-111">Optional.</span></span> <span data-ttu-id="b6a46-112">XML que representa os dados XML.</span><span class="sxs-lookup"><span data-stu-id="b6a46-112">XML that represents the XML data.</span></span> <span data-ttu-id="b6a46-113">Qualquer número de elementos pode estar contido como dados de elemento e elementos aninhados podem estar contidos em outros elementos; No entanto, se aplicam as regras gerais de XML.</span><span class="sxs-lookup"><span data-stu-id="b6a46-113">Any number of elements can be contained as element data and nested elements can be contained in other elements; however, the general rules of XML apply.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b6a46-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="b6a46-114">Remarks</span></span>  
 <span data-ttu-id="b6a46-115">Os elementos XML dentro de um `x:XData` objeto pode declarar novamente todos os possíveis namespaces e prefixos do XMLDOM recipiente dentro dos dados.</span><span class="sxs-lookup"><span data-stu-id="b6a46-115">The XML elements within an `x:XData` object can re-declare all possible namespaces and prefixes of the containing XMLDOM within the data.</span></span>  
  
 <span data-ttu-id="b6a46-116">Acesso programático aos dados XML e o `x:XData` tipo intrínseco do XAML é possível em serviços de XAML do .NET Framework por meio de <xref:System.Windows.Markup.XData> classe.</span><span class="sxs-lookup"><span data-stu-id="b6a46-116">Programmatic access to XML data and the `x:XData` intrinsic XAML type is possible in .NET Framework XAML Services through the <xref:System.Windows.Markup.XData> class.</span></span>  
  
## <a name="wpf-usage-notes"></a><span data-ttu-id="b6a46-117">Notas de uso do WPF</span><span class="sxs-lookup"><span data-stu-id="b6a46-117">WPF Usage Notes</span></span>  
 <span data-ttu-id="b6a46-118">O `x:XData` objeto é usado principalmente como um objeto filho de um <xref:System.Windows.Data.XmlDataProvider>, ou como alternativa, como o objeto filho do <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> propriedade (no XAML, isso é normalmente expressa na sintaxe de elemento de propriedade).</span><span class="sxs-lookup"><span data-stu-id="b6a46-118">The `x:XData` object is primarily used as a child object of an <xref:System.Windows.Data.XmlDataProvider>, or alternatively, as the child object of the <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> property (in XAML, this is typically expressed in property element syntax).</span></span>  
  
 <span data-ttu-id="b6a46-119">Os dados normalmente devem redefinir o namespace XML base dentro da ilha de dados para ser um novo namespace XML padrão (definido como uma cadeia de caracteres vazia).</span><span class="sxs-lookup"><span data-stu-id="b6a46-119">The data should typically redefine the base XML namespace within the data island to be a new default XML namespace (set to an empty string).</span></span> <span data-ttu-id="b6a46-120">Isso é mais fácil para ilhas de dados simples, porque o <xref:System.Windows.Data.Binding.XPath%2A> expressões que são usadas para referenciar e associar aos dados podem evitar a inclusão de prefixos.</span><span class="sxs-lookup"><span data-stu-id="b6a46-120">This is easiest for simple data islands because the <xref:System.Windows.Data.Binding.XPath%2A> expressions that are used to reference and bind to the data can avoid inclusion of prefixes.</span></span> <span data-ttu-id="b6a46-121">Ilhas de dados mais complexas podem definir vários prefixos para os dados e usar um prefixo específico para o namespace XML na raiz.</span><span class="sxs-lookup"><span data-stu-id="b6a46-121">More complex data islands might define multiple prefixes for the data and use a specific prefix for the XML namespace at the root.</span></span> <span data-ttu-id="b6a46-122">Nesse caso, todos os <xref:System.Windows.Data.Binding.XPath%2A> referências de expressão devem incluir o prefixo de namespace mapeado apropriado.</span><span class="sxs-lookup"><span data-stu-id="b6a46-122">In this case, all <xref:System.Windows.Data.Binding.XPath%2A> expression references should include the appropriate namespace-mapped prefix.</span></span> <span data-ttu-id="b6a46-123">Para obter mais informações, consulte [Visão geral de vinculação de dados](../../../docs/framework/wpf/data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="b6a46-123">For more information, see [Data Binding Overview](../../../docs/framework/wpf/data/data-binding-overview.md).</span></span>  
  
 <span data-ttu-id="b6a46-124">Tecnicamente, `x:XData` pode ser usado como o conteúdo de qualquer propriedade do tipo <xref:System.Xml.Serialization.IXmlSerializable>.</span><span class="sxs-lookup"><span data-stu-id="b6a46-124">Technically, `x:XData` can be used as the content of any property of type <xref:System.Xml.Serialization.IXmlSerializable>.</span></span> <span data-ttu-id="b6a46-125">No entanto, <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> é a implementação apenas proeminente.</span><span class="sxs-lookup"><span data-stu-id="b6a46-125">However, <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> is the only prominent implementation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6a46-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b6a46-126">See also</span></span>
- <xref:System.Windows.Data.XmlDataProvider>
- [<span data-ttu-id="b6a46-127">Visão geral da vinculação de dados</span><span class="sxs-lookup"><span data-stu-id="b6a46-127">Data Binding Overview</span></span>](../../../docs/framework/wpf/data/data-binding-overview.md)
- [<span data-ttu-id="b6a46-128">Extensão de marcação de associação</span><span class="sxs-lookup"><span data-stu-id="b6a46-128">Binding Markup Extension</span></span>](../../../docs/framework/wpf/advanced/binding-markup-extension.md)
