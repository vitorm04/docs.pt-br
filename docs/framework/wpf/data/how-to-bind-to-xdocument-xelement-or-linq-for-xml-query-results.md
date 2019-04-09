---
title: 'Como: Associar a XDocument, XElement ou LINQ para resultados de consulta XML'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], binding to XDocument
- data binding [WPF], binding to XElement
ms.assetid: 6a629a49-fe1c-465d-b76a-3dcbf4307b64
ms.openlocfilehash: afecb87dcfce1a8c48f1b2108edeae3cfd2aa16f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59209652"
---
# <a name="how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results"></a><span data-ttu-id="97d51-102">Como: Associar a XDocument, XElement ou LINQ para resultados de consulta XML</span><span class="sxs-lookup"><span data-stu-id="97d51-102">How to: Bind to XDocument, XElement, or LINQ for XML Query Results</span></span>
<span data-ttu-id="97d51-103">Este exemplo demonstra como associar dados XML para um <xref:System.Windows.Controls.ItemsControl> usando <xref:System.Xml.Linq.XDocument>.</span><span class="sxs-lookup"><span data-stu-id="97d51-103">This example demonstrates how to bind XML data to an <xref:System.Windows.Controls.ItemsControl> using <xref:System.Xml.Linq.XDocument>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="97d51-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="97d51-104">Example</span></span>  
 <span data-ttu-id="97d51-105">O código XAML a seguir define uma <xref:System.Windows.Controls.ItemsControl> e inclui um modelo de dados para o tipo de dados `Planet` no `http://planetsNS` namespace de XML.</span><span class="sxs-lookup"><span data-stu-id="97d51-105">The following XAML code defines an <xref:System.Windows.Controls.ItemsControl> and includes a data template for data of type `Planet` in the `http://planetsNS` XML namespace.</span></span> <span data-ttu-id="97d51-106">Um tipo de dados XML que ocupa um namespace deve incluir o namespace entre chaves e, se ele aparecer onde uma extensão de marcação XAML pode aparecer, deverá preceder o namespace com uma sequência de escape de chave.</span><span class="sxs-lookup"><span data-stu-id="97d51-106">An XML data type that occupies a namespace must include the namespace in braces, and if it appears where a XAML markup extension could appear, it must precede the namespace with a brace escape sequence.</span></span> <span data-ttu-id="97d51-107">Esse código associa a propriedades dinâmicas que correspondem do <xref:System.Xml.Linq.XContainer.Element%2A> e <xref:System.Xml.Linq.XElement.Attribute%2A> métodos do <xref:System.Xml.Linq.XElement> classe.</span><span class="sxs-lookup"><span data-stu-id="97d51-107">This code binds to dynamic properties that correspond to the <xref:System.Xml.Linq.XContainer.Element%2A> and <xref:System.Xml.Linq.XElement.Attribute%2A> methods of the <xref:System.Xml.Linq.XElement> class.</span></span> <span data-ttu-id="97d51-108">As propriedades dinâmicas permitem que o XAML se associe a propriedades dinâmicas que compartilham os nomes dos métodos.</span><span class="sxs-lookup"><span data-stu-id="97d51-108">Dynamic properties enable XAML to bind to dynamic properties that share the names of methods.</span></span> <span data-ttu-id="97d51-109">Para saber mais, consulte [Propriedades Dinâmicas LINQ to XML](/visualstudio/designers/linq-to-xml-dynamic-properties).</span><span class="sxs-lookup"><span data-stu-id="97d51-109">To learn more, see [LINQ to XML Dynamic Properties](/visualstudio/designers/linq-to-xml-dynamic-properties).</span></span> <span data-ttu-id="97d51-110">Veja como a declaração de namespace padrão para o XML não se aplica aos nomes de atributos.</span><span class="sxs-lookup"><span data-stu-id="97d51-110">Notice how the default namespace declaration for the XML does not apply to attribute names.</span></span>  
  
 [!code-xaml[XLinqExample#StackPanelResources](~/samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml#stackpanelresources)]  
[!code-xaml[XLinqExample#ItemsControl](~/samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml#itemscontrol)]  
  
 <span data-ttu-id="97d51-111">As seguintes chamadas de código em c# <xref:System.Xml.Linq.XDocument.Load%2A> e define o contexto de dados do painel de pilha para todos os subelementos do elemento denominado `SolarSystemPlanets` no `http://planetsNS` namespace de XML.</span><span class="sxs-lookup"><span data-stu-id="97d51-111">The following C# code calls <xref:System.Xml.Linq.XDocument.Load%2A> and sets the stack panel data context to all subelements of the element named `SolarSystemPlanets` in the `http://planetsNS` XML namespace.</span></span>  
  
 [!code-csharp[XLinqExample#LoadDCFromFile](~/samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml.cs#loaddcfromfile)]
 [!code-vb[XLinqExample#LoadDCFromFile](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XLinqExample/visualbasic/window1.xaml.vb#loaddcfromfile)]  
  
 <span data-ttu-id="97d51-112">Dados XML podem ser armazenados como um recurso XAML usando <xref:System.Windows.Data.ObjectDataProvider>.</span><span class="sxs-lookup"><span data-stu-id="97d51-112">XML data can be stored as a XAML resource using <xref:System.Windows.Data.ObjectDataProvider>.</span></span> <span data-ttu-id="97d51-113">Para obter um exemplo completo, consulte [código-fonte L2DBForm.xaml](/visualstudio/designers/l2dbform-xaml-source-code).</span><span class="sxs-lookup"><span data-stu-id="97d51-113">For a complete example, see  [L2DBForm.xaml source code](/visualstudio/designers/l2dbform-xaml-source-code).</span></span> <span data-ttu-id="97d51-114">O exemplo a seguir mostra como o código pode definir o contexto de dados para um recurso de objeto.</span><span class="sxs-lookup"><span data-stu-id="97d51-114">The following sample shows how code can set the data context to an object resource.</span></span>  
  
 [!code-csharp[XLinqExample#LoadDCFromXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml.cs#loaddcfromxaml)]
 [!code-vb[XLinqExample#LoadDCFromXAML](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XLinqExample/visualbasic/window1.xaml.vb#loaddcfromxaml)]  
  
 <span data-ttu-id="97d51-115">As propriedades dinâmicas que mapeiam <xref:System.Xml.Linq.XContainer.Element%2A> e <xref:System.Xml.Linq.XElement.Attribute%2A> proporcionam flexibilidade no XAML.</span><span class="sxs-lookup"><span data-stu-id="97d51-115">The dynamic properties that map to <xref:System.Xml.Linq.XContainer.Element%2A> and <xref:System.Xml.Linq.XElement.Attribute%2A> provide flexibility within XAML.</span></span> <span data-ttu-id="97d51-116">O código também pode se associar aos resultados de um LINQ para consulta XML.</span><span class="sxs-lookup"><span data-stu-id="97d51-116">Your code can also bind to the results of a LINQ for XML query.</span></span> <span data-ttu-id="97d51-117">Este exemplo se associa aos resultados da consulta ordenados por um valor de elemento.</span><span class="sxs-lookup"><span data-stu-id="97d51-117">This example binds to query results ordered by an element value.</span></span>  
  
 [!code-csharp[XLinqExample#BindToResults](~/samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml.cs#bindtoresults)]
 [!code-vb[XLinqExample#BindToResults](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XLinqExample/visualbasic/window1.xaml.vb#bindtoresults)]  
  
## <a name="see-also"></a><span data-ttu-id="97d51-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="97d51-118">See also</span></span>

- [<span data-ttu-id="97d51-119">Visão geral das fontes de associação</span><span class="sxs-lookup"><span data-stu-id="97d51-119">Binding Sources Overview</span></span>](binding-sources-overview.md)
- [<span data-ttu-id="97d51-120">Visão geral da associação de dados do WPF com LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="97d51-120">WPF Data Binding with LINQ to XML Overview</span></span>](/visualstudio/designers/wpf-data-binding-with-linq-to-xml-overview)
- [<span data-ttu-id="97d51-121">Associação de dados de WPF usando o exemplo LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="97d51-121">WPF Data Binding Using LINQ to XML Example</span></span>](/visualstudio/designers/wpf-data-binding-using-linq-to-xml-example)
- [<span data-ttu-id="97d51-122">Propriedades dinâmicas LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="97d51-122">LINQ to XML Dynamic Properties</span></span>](/visualstudio/designers/linq-to-xml-dynamic-properties)
