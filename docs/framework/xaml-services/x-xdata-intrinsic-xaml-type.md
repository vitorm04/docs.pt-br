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
ms.openlocfilehash: 8496e7c87cf7e6eea996ca7af4f288b7495c7661
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459906"
---
# <a name="xxdata-intrinsic-xaml-type"></a><span data-ttu-id="e8ebb-102">Tipo intrínseco x:XData (XAML)</span><span class="sxs-lookup"><span data-stu-id="e8ebb-102">x:XData Intrinsic XAML Type</span></span>
<span data-ttu-id="e8ebb-103">Habilita o posicionamento das ilhas de dados XML em uma produção XAML.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-103">Enables placement of XML data islands within a XAML production.</span></span> <span data-ttu-id="e8ebb-104">Elementos XML dentro de `x:XData` não devem ser tratados por processadores XAML como se eles fossem uma parte do namespace XAML padrão atuante ou qualquer outro namespace XAML.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-104">XML elements within `x:XData` should not be treated by XAML processors as if they are a part of the acting default XAML namespace or any other XAML namespace.</span></span> <span data-ttu-id="e8ebb-105">`x:XData` pode conter XML bem formado arbitrário.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-105">`x:XData` can contain arbitrary well-formed XML.</span></span>  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="e8ebb-106">Uso de elemento Object do XAML</span><span class="sxs-lookup"><span data-stu-id="e8ebb-106">XAML Object Element Usage</span></span>  
  
```xaml  
<x:XData>  
  <elementDataRoot>  
    [elementData]  
  </elementDataRoot>  
</x:XData>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="e8ebb-107">Valores XAML</span><span class="sxs-lookup"><span data-stu-id="e8ebb-107">XAML Values</span></span>  
  
|||  
|-|-|  
|`elementDataRoot`|<span data-ttu-id="e8ebb-108">O elemento raiz único da ilha de dados embutida.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-108">The single root element of the enclosed data island.</span></span> <span data-ttu-id="e8ebb-109">Para os consumidores mais eventuales, o XML que não tem uma única raiz é considerado inválido.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-109">For most eventual consumers, XML that does not have a single root is considered invalid.</span></span> <span data-ttu-id="e8ebb-110">Em particular, uma única raiz será necessária se a `x:XData` for destinada como uma fonte de dados XML para WPF ou muitas outras tecnologias que usam fontes XML para vinculação de dados.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-110">In particular, a single root is required if the `x:XData` is intended as an XML data source for WPF or many other technologies that use XML sources for data binding.</span></span>|  
|`[elementData]`|<span data-ttu-id="e8ebb-111">Opcional.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-111">Optional.</span></span> <span data-ttu-id="e8ebb-112">XML que representa os dados XML.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-112">XML that represents the XML data.</span></span> <span data-ttu-id="e8ebb-113">Qualquer número de elementos pode ser contido como dados de elemento e elementos aninhados podem estar contidos em outros elementos; no entanto, as regras gerais do XML se aplicam.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-113">Any number of elements can be contained as element data and nested elements can be contained in other elements; however, the general rules of XML apply.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e8ebb-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="e8ebb-114">Remarks</span></span>  
 <span data-ttu-id="e8ebb-115">Os elementos XML dentro de um objeto `x:XData` podem redeclarar todos os namespaces e prefixos possíveis de XMLDOM dentro dos dados.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-115">The XML elements within an `x:XData` object can re-declare all possible namespaces and prefixes of the containing XMLDOM within the data.</span></span>  
  
 <span data-ttu-id="e8ebb-116">O acesso programático a dados XML e o tipo de XAML intrínseco `x:XData` é possível em .NET Framework serviços XAML por meio da classe <xref:System.Windows.Markup.XData>.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-116">Programmatic access to XML data and the `x:XData` intrinsic XAML type is possible in .NET Framework XAML Services through the <xref:System.Windows.Markup.XData> class.</span></span>  
  
## <a name="wpf-usage-notes"></a><span data-ttu-id="e8ebb-117">Observações de uso do WPF</span><span class="sxs-lookup"><span data-stu-id="e8ebb-117">WPF Usage Notes</span></span>  
 <span data-ttu-id="e8ebb-118">O objeto `x:XData` é usado principalmente como um objeto filho de um <xref:System.Windows.Data.XmlDataProvider>ou, como alternativa, como o objeto filho da propriedade <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> (em XAML, isso normalmente é expresso em sintaxe de elemento de propriedade).</span><span class="sxs-lookup"><span data-stu-id="e8ebb-118">The `x:XData` object is primarily used as a child object of an <xref:System.Windows.Data.XmlDataProvider>, or alternatively, as the child object of the <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> property (in XAML, this is typically expressed in property element syntax).</span></span>  
  
 <span data-ttu-id="e8ebb-119">Os dados normalmente devem redefinir o namespace XML base dentro da ilha de dados para ser um novo namespace XML padrão (definido como uma cadeia de caracteres vazia).</span><span class="sxs-lookup"><span data-stu-id="e8ebb-119">The data should typically redefine the base XML namespace within the data island to be a new default XML namespace (set to an empty string).</span></span> <span data-ttu-id="e8ebb-120">Isso é mais fácil para ilhas de dados simples porque as expressões de <xref:System.Windows.Data.Binding.XPath%2A> que são usadas para referenciar e associar aos dados podem evitar a inclusão de prefixos.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-120">This is easiest for simple data islands because the <xref:System.Windows.Data.Binding.XPath%2A> expressions that are used to reference and bind to the data can avoid inclusion of prefixes.</span></span> <span data-ttu-id="e8ebb-121">Ilhas de dados mais complexas podem definir vários prefixos para os dados e usar um prefixo específico para o namespace XML na raiz.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-121">More complex data islands might define multiple prefixes for the data and use a specific prefix for the XML namespace at the root.</span></span> <span data-ttu-id="e8ebb-122">Nesse caso, todas as referências de expressão de <xref:System.Windows.Data.Binding.XPath%2A> devem incluir o prefixo mapeado para namespace apropriado.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-122">In this case, all <xref:System.Windows.Data.Binding.XPath%2A> expression references should include the appropriate namespace-mapped prefix.</span></span> <span data-ttu-id="e8ebb-123">Para obter mais informações, consulte [Visão geral de vinculação de dados](../../desktop-wpf/data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="e8ebb-123">For more information, see [Data Binding Overview](../../desktop-wpf/data/data-binding-overview.md).</span></span>  
  
 <span data-ttu-id="e8ebb-124">Tecnicamente, `x:XData` pode ser usada como o conteúdo de qualquer Propriedade do tipo <xref:System.Xml.Serialization.IXmlSerializable>.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-124">Technically, `x:XData` can be used as the content of any property of type <xref:System.Xml.Serialization.IXmlSerializable>.</span></span> <span data-ttu-id="e8ebb-125">No entanto, <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> é a única implementação proeminente.</span><span class="sxs-lookup"><span data-stu-id="e8ebb-125">However, <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> is the only prominent implementation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8ebb-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e8ebb-126">See also</span></span>

- <xref:System.Windows.Data.XmlDataProvider>
- [<span data-ttu-id="e8ebb-127">Visão geral da vinculação de dados</span><span class="sxs-lookup"><span data-stu-id="e8ebb-127">Data Binding Overview</span></span>](../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="e8ebb-128">Extensão de marcação de associação</span><span class="sxs-lookup"><span data-stu-id="e8ebb-128">Binding Markup Extension</span></span>](../wpf/advanced/binding-markup-extension.md)
