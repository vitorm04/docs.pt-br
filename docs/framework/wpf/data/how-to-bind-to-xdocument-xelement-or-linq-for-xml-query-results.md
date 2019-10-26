---
title: Como associar a XDocument, XElement ou LINQ para resultados de consulta XML
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], binding to XDocument
- data binding [WPF], binding to XElement
ms.assetid: 6a629a49-fe1c-465d-b76a-3dcbf4307b64
ms.openlocfilehash: 070f67f30613d4522a48e08fd1c208fbe5887525
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920117"
---
# <a name="how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results"></a><span data-ttu-id="1c0a3-102">Como associar a XDocument, XElement ou LINQ para resultados de consulta XML</span><span class="sxs-lookup"><span data-stu-id="1c0a3-102">How to: Bind to XDocument, XElement, or LINQ for XML Query Results</span></span>

<span data-ttu-id="1c0a3-103">Este exemplo demonstra como associar dados XML a um <xref:System.Windows.Controls.ItemsControl> usando <xref:System.Xml.Linq.XDocument>.</span><span class="sxs-lookup"><span data-stu-id="1c0a3-103">This example demonstrates how to bind XML data to an <xref:System.Windows.Controls.ItemsControl> using <xref:System.Xml.Linq.XDocument>.</span></span>

## <a name="example"></a><span data-ttu-id="1c0a3-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1c0a3-104">Example</span></span>

<span data-ttu-id="1c0a3-105">O código XAML a seguir define um <xref:System.Windows.Controls.ItemsControl> e inclui um modelo de dados para dados do tipo `Planet` no namespace XML `http://planetsNS`.</span><span class="sxs-lookup"><span data-stu-id="1c0a3-105">The following XAML code defines an <xref:System.Windows.Controls.ItemsControl> and includes a data template for data of type `Planet` in the `http://planetsNS` XML namespace.</span></span> <span data-ttu-id="1c0a3-106">Um tipo de dados XML que ocupa um namespace deve incluir o namespace entre chaves e, se ele aparecer onde uma extensão de marcação XAML pode aparecer, deverá preceder o namespace com uma sequência de escape de chave.</span><span class="sxs-lookup"><span data-stu-id="1c0a3-106">An XML data type that occupies a namespace must include the namespace in braces, and if it appears where a XAML markup extension could appear, it must precede the namespace with a brace escape sequence.</span></span> <span data-ttu-id="1c0a3-107">Esse código é associado a propriedades dinâmicas que correspondem aos métodos <xref:System.Xml.Linq.XContainer.Element%2A> e <xref:System.Xml.Linq.XElement.Attribute%2A> da classe <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="1c0a3-107">This code binds to dynamic properties that correspond to the <xref:System.Xml.Linq.XContainer.Element%2A> and <xref:System.Xml.Linq.XElement.Attribute%2A> methods of the <xref:System.Xml.Linq.XElement> class.</span></span> <span data-ttu-id="1c0a3-108">As propriedades dinâmicas permitem que o XAML se associe a propriedades dinâmicas que compartilham os nomes dos métodos.</span><span class="sxs-lookup"><span data-stu-id="1c0a3-108">Dynamic properties enable XAML to bind to dynamic properties that share the names of methods.</span></span> <span data-ttu-id="1c0a3-109">Para saber mais, confira [LINQ to XML propriedades dinâmicas](linq-to-xml-dynamic-properties.md).</span><span class="sxs-lookup"><span data-stu-id="1c0a3-109">To learn more, see [LINQ to XML dynamic properties](linq-to-xml-dynamic-properties.md).</span></span> <span data-ttu-id="1c0a3-110">Veja como a declaração de namespace padrão para o XML não se aplica aos nomes de atributos.</span><span class="sxs-lookup"><span data-stu-id="1c0a3-110">Notice how the default namespace declaration for the XML does not apply to attribute names.</span></span>

[!code-xaml[XLinqExample#StackPanelResources](~/samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml#stackpanelresources)]
[!code-xaml[XLinqExample#ItemsControl](~/samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml#itemscontrol)]

<span data-ttu-id="1c0a3-111">O código C# a seguir chama<xref:System.Xml.Linq.XDocument.Load%2A>e define o contexto de dados do painel de pilha para todos os subelementos do elemento nomeado`SolarSystemPlanets`no namespace XML`http://planetsNS`.</span><span class="sxs-lookup"><span data-stu-id="1c0a3-111">The following C# code calls <xref:System.Xml.Linq.XDocument.Load%2A> and sets the stack panel data context to all subelements of the element named `SolarSystemPlanets` in the `http://planetsNS` XML namespace.</span></span>

[!code-csharp[XLinqExample#LoadDCFromFile](~/samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml.cs#loaddcfromfile)]
[!code-vb[XLinqExample#LoadDCFromFile](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XLinqExample/visualbasic/window1.xaml.vb#loaddcfromfile)]

<span data-ttu-id="1c0a3-112">Os dados XML podem ser armazenados como um recurso XAML usando <xref:System.Windows.Data.ObjectDataProvider>.</span><span class="sxs-lookup"><span data-stu-id="1c0a3-112">XML data can be stored as a XAML resource using <xref:System.Windows.Data.ObjectDataProvider>.</span></span> <span data-ttu-id="1c0a3-113">Para obter um exemplo completo, consulte [código-fonte L2DBForm. XAML](l2dbform-xaml-source-code.md).</span><span class="sxs-lookup"><span data-stu-id="1c0a3-113">For a complete example, see  [L2DBForm.xaml source code](l2dbform-xaml-source-code.md).</span></span> <span data-ttu-id="1c0a3-114">O exemplo a seguir mostra como o código pode definir o contexto de dados para um recurso de objeto.</span><span class="sxs-lookup"><span data-stu-id="1c0a3-114">The following sample shows how code can set the data context to an object resource.</span></span>

[!code-csharp[XLinqExample#LoadDCFromXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml.cs#loaddcfromxaml)]
[!code-vb[XLinqExample#LoadDCFromXAML](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XLinqExample/visualbasic/window1.xaml.vb#loaddcfromxaml)]

<span data-ttu-id="1c0a3-115">As propriedades dinâmicas que são mapeadas para <xref:System.Xml.Linq.XContainer.Element%2A> e <xref:System.Xml.Linq.XElement.Attribute%2A> fornecem flexibilidade no XAML.</span><span class="sxs-lookup"><span data-stu-id="1c0a3-115">The dynamic properties that map to <xref:System.Xml.Linq.XContainer.Element%2A> and <xref:System.Xml.Linq.XElement.Attribute%2A> provide flexibility within XAML.</span></span> <span data-ttu-id="1c0a3-116">O código também pode se associar aos resultados de um LINQ para consulta XML.</span><span class="sxs-lookup"><span data-stu-id="1c0a3-116">Your code can also bind to the results of a LINQ for XML query.</span></span> <span data-ttu-id="1c0a3-117">Este exemplo se associa aos resultados da consulta ordenados por um valor de elemento.</span><span class="sxs-lookup"><span data-stu-id="1c0a3-117">This example binds to query results ordered by an element value.</span></span>

[!code-csharp[XLinqExample#BindToResults](~/samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml.cs#bindtoresults)]
[!code-vb[XLinqExample#BindToResults](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XLinqExample/visualbasic/window1.xaml.vb#bindtoresults)]

## <a name="see-also"></a><span data-ttu-id="1c0a3-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1c0a3-118">See also</span></span>

- [<span data-ttu-id="1c0a3-119">Visão geral das origens da associação</span><span class="sxs-lookup"><span data-stu-id="1c0a3-119">Binding Sources Overview</span></span>](binding-sources-overview.md)
- [<span data-ttu-id="1c0a3-120">Visão geral da vinculação de dados do WPF com LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="1c0a3-120">WPF Data Binding with LINQ to XML Overview</span></span>](wpf-data-binding-with-linq-to-xml-overview.md)
- [<span data-ttu-id="1c0a3-121">Vinculação de dados de WPF usando o exemplo LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="1c0a3-121">WPF Data Binding Using LINQ to XML Example</span></span>](linq-to-xml-data-binding-sample.md)
- [<span data-ttu-id="1c0a3-122">Propriedades dinâmicas LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="1c0a3-122">LINQ to XML Dynamic Properties</span></span>](linq-to-xml-dynamic-properties.md)
