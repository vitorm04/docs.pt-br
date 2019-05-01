---
title: 'Como: Disponibilizar dados para associação em XAML'
ms.date: 01/29/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], making data available for binding
- binding data [WPF], making data available for
ms.assetid: 7103c2e8-0e31-4a13-bf12-ca382221a8d5
ms.openlocfilehash: 2d51f06da31482c46b04d1eb86172c3eda246c20
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62010300"
---
# <a name="how-to-make-data-available-for-binding-in-xaml"></a><span data-ttu-id="b7544-102">Como: Disponibilizar dados para associação em XAML</span><span class="sxs-lookup"><span data-stu-id="b7544-102">How to: Make Data Available for Binding in XAML</span></span>
<span data-ttu-id="b7544-103">Este tópico discute várias maneiras que você pode tornar dados disponíveis para associação em [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], dependendo das necessidades do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b7544-103">This topic discusses various ways you can make data available for binding in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], depending on the needs of your application.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b7544-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b7544-104">Example</span></span>  
 <span data-ttu-id="b7544-105">Se você tiver um objeto [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] que deseja associar de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], uma maneira de disponibilizar o objeto para associação será defini-lo como um recurso e conceder um `x:Key` a ele.</span><span class="sxs-lookup"><span data-stu-id="b7544-105">If you have a [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] object you would like to bind to from [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], one way you can make the object available for binding is to define it as a resource and give it an `x:Key`.</span></span> <span data-ttu-id="b7544-106">No exemplo a seguir, temos um objeto `Person` com uma propriedade de cadeia de caracteres denominada `PersonName`.</span><span class="sxs-lookup"><span data-stu-id="b7544-106">In the following example, you have a `Person` object with a string property named `PersonName`.</span></span> <span data-ttu-id="b7544-107">O `Person` objeto (na linha mostrada realçada que contém o `<src>` elemento) é definido no namespace chamado `SDKSample`.</span><span class="sxs-lookup"><span data-stu-id="b7544-107">The `Person` object (in the line shown highlighted that contains the `<src>` element) is defined in the namespace called `SDKSample`.</span></span>  
  
 [!code-xaml[SimpleBinding#Instantiation](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml?highlight=9,37)]  
  
 <span data-ttu-id="b7544-108">Em seguida, você pode associar o <xref:System.Windows.Controls.TextBlock> controle para o objeto no [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], como a linha destacada, que contém o `<TextBlock>` mostra do elemento.</span><span class="sxs-lookup"><span data-stu-id="b7544-108">You can then bind the <xref:System.Windows.Controls.TextBlock> control to the object in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], as the highlighted line that contains the `<TextBlock>` element shows.</span></span> 
  
 <span data-ttu-id="b7544-109">Como alternativa, você pode usar o <xref:System.Windows.Data.ObjectDataProvider> classe, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="b7544-109">Alternatively, you can use the <xref:System.Windows.Data.ObjectDataProvider> class, as in the following example:</span></span>  
  
 [!code-xaml[ObjectDataProvider}](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Page1.xaml?highlight=10-14,42)]  
  
 <span data-ttu-id="b7544-110">Definir a associação da mesma forma, como a linha realçada que contém o `<TextBlock>` mostra do elemento.</span><span class="sxs-lookup"><span data-stu-id="b7544-110">You define the binding the same way, as the highlighted line that contains the `<TextBlock>` element shows.</span></span>  
  
 <span data-ttu-id="b7544-111">Nesse exemplo específico, o resultado é o mesmo: você tem um <xref:System.Windows.Controls.TextBlock> com o conteúdo de texto `Joe`.</span><span class="sxs-lookup"><span data-stu-id="b7544-111">In this particular example, the result is the same: you have a <xref:System.Windows.Controls.TextBlock> with the text content `Joe`.</span></span> <span data-ttu-id="b7544-112">No entanto, o <xref:System.Windows.Data.ObjectDataProvider> classe fornece funcionalidades como a capacidade de associar ao resultado de um método.</span><span class="sxs-lookup"><span data-stu-id="b7544-112">However, the <xref:System.Windows.Data.ObjectDataProvider> class provides functionality such as the ability to bind to the result of a method.</span></span> <span data-ttu-id="b7544-113">Você pode optar por usar o <xref:System.Windows.Data.ObjectDataProvider> classe se você precisar da funcionalidade que ele fornece.</span><span class="sxs-lookup"><span data-stu-id="b7544-113">You can choose to use the <xref:System.Windows.Data.ObjectDataProvider> class if you need the functionality it provides.</span></span>  
  
 <span data-ttu-id="b7544-114">No entanto, se estiver associando a um objeto que já foi criado, será necessário definir o `DataContext` no código, como no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="b7544-114">However, if you are binding to an object that has already been created, you need to set the `DataContext` in code, as in the following example.</span></span>  
  
 [!code-csharp[ADODataSet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ADODataSet#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ADODataSet/VisualBasic/Window1.xaml.vb#1)]  
  
 <span data-ttu-id="b7544-115">Para acessar [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] dados para associação usando o <xref:System.Windows.Data.XmlDataProvider> classe, consulte [associar a dados XML usando um XMLDataProvider e consultas XPath](how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md).</span><span class="sxs-lookup"><span data-stu-id="b7544-115">To access [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data for binding using the <xref:System.Windows.Data.XmlDataProvider> class, see [Bind to XML Data Using an XMLDataProvider and XPath Queries](how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md).</span></span> <span data-ttu-id="b7544-116">Para acessar [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] dados para associação usando o <xref:System.Windows.Data.ObjectDataProvider> classe, consulte [associar a XDocument, XElement ou LINQ para resultados de consulta XML](how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md).</span><span class="sxs-lookup"><span data-stu-id="b7544-116">To access [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data for binding using the <xref:System.Windows.Data.ObjectDataProvider> class, see [Bind to XDocument, XElement, or LINQ for XML Query Results](how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md).</span></span>  
  
 <span data-ttu-id="b7544-117">Para obter informações sobre várias maneiras que você pode especificar os dados que você está associando a, consulte [especificar a origem da associação](how-to-specify-the-binding-source.md).</span><span class="sxs-lookup"><span data-stu-id="b7544-117">For information about many ways you can specify the data you are binding to, see [Specify the Binding Source](how-to-specify-the-binding-source.md).</span></span> <span data-ttu-id="b7544-118">Para obter informações sobre a quais tipos de dados é possível associar ou como implementar seus próprios objetos [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] para associação, consulte [Visão geral de fontes de associação](binding-sources-overview.md).</span><span class="sxs-lookup"><span data-stu-id="b7544-118">For information about what types of data you can bind to or how to implement your own [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] objects for binding, see [Binding Sources Overview](binding-sources-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7544-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b7544-119">See also</span></span>

- [<span data-ttu-id="b7544-120">Visão geral da vinculação de dados</span><span class="sxs-lookup"><span data-stu-id="b7544-120">Data Binding Overview</span></span>](data-binding-overview.md)
- [<span data-ttu-id="b7544-121">Tópicos de instruções</span><span class="sxs-lookup"><span data-stu-id="b7544-121">How-to Topics</span></span>](data-binding-how-to-topics.md)
