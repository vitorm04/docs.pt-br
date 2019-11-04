---
title: Como disponibilizar dados para associação em XAML
ms.date: 01/29/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], making data available for binding
- binding data [WPF], making data available for
ms.assetid: 7103c2e8-0e31-4a13-bf12-ca382221a8d5
ms.openlocfilehash: 2bfd9809a6ad487a7e706366dc6bce8fe951c940
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459754"
---
# <a name="how-to-make-data-available-for-binding-in-xaml"></a><span data-ttu-id="5ae70-102">Como disponibilizar dados para associação em XAML</span><span class="sxs-lookup"><span data-stu-id="5ae70-102">How to: Make Data Available for Binding in XAML</span></span>
<span data-ttu-id="5ae70-103">Este tópico discute várias maneiras de disponibilizar dados para associação em [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], dependendo das necessidades do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5ae70-103">This topic discusses various ways you can make data available for binding in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], depending on the needs of your application.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5ae70-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5ae70-104">Example</span></span>  
 <span data-ttu-id="5ae70-105">Se você tiver um objeto Common Language Runtime (CLR) ao qual deseja associar-se [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], uma maneira de tornar o objeto disponível para associação é defini-lo como um recurso e fornecê-lo a um `x:Key`.</span><span class="sxs-lookup"><span data-stu-id="5ae70-105">If you have a common language runtime (CLR) object you would like to bind to from [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], one way you can make the object available for binding is to define it as a resource and give it an `x:Key`.</span></span> <span data-ttu-id="5ae70-106">No exemplo a seguir, temos um objeto `Person` com uma propriedade de cadeia de caracteres denominada `PersonName`.</span><span class="sxs-lookup"><span data-stu-id="5ae70-106">In the following example, you have a `Person` object with a string property named `PersonName`.</span></span> <span data-ttu-id="5ae70-107">O objeto `Person` (na linha mostrado realçado que contém o elemento `<src>`) é definido no namespace chamado `SDKSample`.</span><span class="sxs-lookup"><span data-stu-id="5ae70-107">The `Person` object (in the line shown highlighted that contains the `<src>` element) is defined in the namespace called `SDKSample`.</span></span>  
  
 [!code-xaml[SimpleBinding#Instantiation](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml?highlight=9,37)]  
  
 <span data-ttu-id="5ae70-108">Em seguida, você pode associar o controle de <xref:System.Windows.Controls.TextBlock> ao objeto em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], como a linha realçada que contém o elemento `<TextBlock>` mostra.</span><span class="sxs-lookup"><span data-stu-id="5ae70-108">You can then bind the <xref:System.Windows.Controls.TextBlock> control to the object in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], as the highlighted line that contains the `<TextBlock>` element shows.</span></span> 
  
 <span data-ttu-id="5ae70-109">Como alternativa, você pode usar a classe <xref:System.Windows.Data.ObjectDataProvider>, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="5ae70-109">Alternatively, you can use the <xref:System.Windows.Data.ObjectDataProvider> class, as in the following example:</span></span>  
  
 [!code-xaml[ObjectDataProvider}](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Page1.xaml?highlight=10-14,42)]  
  
 <span data-ttu-id="5ae70-110">Você define a associação da mesma maneira, como a linha realçada que contém o elemento `<TextBlock>` mostra.</span><span class="sxs-lookup"><span data-stu-id="5ae70-110">You define the binding the same way, as the highlighted line that contains the `<TextBlock>` element shows.</span></span>  
  
 <span data-ttu-id="5ae70-111">Neste exemplo específico, o resultado é o mesmo: você tem um <xref:System.Windows.Controls.TextBlock> com o conteúdo de texto `Joe`.</span><span class="sxs-lookup"><span data-stu-id="5ae70-111">In this particular example, the result is the same: you have a <xref:System.Windows.Controls.TextBlock> with the text content `Joe`.</span></span> <span data-ttu-id="5ae70-112">No entanto, a classe <xref:System.Windows.Data.ObjectDataProvider> fornece funcionalidade como a capacidade de associar ao resultado de um método.</span><span class="sxs-lookup"><span data-stu-id="5ae70-112">However, the <xref:System.Windows.Data.ObjectDataProvider> class provides functionality such as the ability to bind to the result of a method.</span></span> <span data-ttu-id="5ae70-113">Você pode optar por usar a classe <xref:System.Windows.Data.ObjectDataProvider> se precisar da funcionalidade que ela fornece.</span><span class="sxs-lookup"><span data-stu-id="5ae70-113">You can choose to use the <xref:System.Windows.Data.ObjectDataProvider> class if you need the functionality it provides.</span></span>  
  
 <span data-ttu-id="5ae70-114">No entanto, se estiver associando a um objeto que já foi criado, será necessário definir o `DataContext` no código, como no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="5ae70-114">However, if you are binding to an object that has already been created, you need to set the `DataContext` in code, as in the following example.</span></span>  
  
 [!code-csharp[ADODataSet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ADODataSet#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ADODataSet/VisualBasic/Window1.xaml.vb#1)]  
  
 <span data-ttu-id="5ae70-115">Para acessar dados de [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] para associação usando a classe <xref:System.Windows.Data.XmlDataProvider>, consulte [associar dados XML usando um XmlDataProvider e consultas XPath](how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md).</span><span class="sxs-lookup"><span data-stu-id="5ae70-115">To access [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data for binding using the <xref:System.Windows.Data.XmlDataProvider> class, see [Bind to XML Data Using an XMLDataProvider and XPath Queries](how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md).</span></span> <span data-ttu-id="5ae70-116">Para acessar dados de [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] para associação usando a classe <xref:System.Windows.Data.ObjectDataProvider>, consulte [associar a resultados de consulta de XDocument, XElement ou LINQ for XML](how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md).</span><span class="sxs-lookup"><span data-stu-id="5ae70-116">To access [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data for binding using the <xref:System.Windows.Data.ObjectDataProvider> class, see [Bind to XDocument, XElement, or LINQ for XML Query Results](how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md).</span></span>  
  
 <span data-ttu-id="5ae70-117">Para obter informações sobre várias maneiras que você pode especificar os dados aos quais você está ligando, consulte [especificar a origem da Associação](how-to-specify-the-binding-source.md).</span><span class="sxs-lookup"><span data-stu-id="5ae70-117">For information about many ways you can specify the data you are binding to, see [Specify the Binding Source](how-to-specify-the-binding-source.md).</span></span> <span data-ttu-id="5ae70-118">Para obter informações sobre quais tipos de dados você pode associar ou como implementar seus próprios objetos Common Language Runtime (CLR) para associação, consulte [visão geral de fontes de associação](binding-sources-overview.md).</span><span class="sxs-lookup"><span data-stu-id="5ae70-118">For information about what types of data you can bind to or how to implement your own common language runtime (CLR) objects for binding, see [Binding Sources Overview](binding-sources-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ae70-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5ae70-119">See also</span></span>

- [<span data-ttu-id="5ae70-120">Visão geral da vinculação de dados</span><span class="sxs-lookup"><span data-stu-id="5ae70-120">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="5ae70-121">Tópicos explicativos</span><span class="sxs-lookup"><span data-stu-id="5ae70-121">How-to Topics</span></span>](data-binding-how-to-topics.md)
