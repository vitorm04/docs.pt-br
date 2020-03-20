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
ms.openlocfilehash: 91e89dbf36024c31f4afcd9b6d956944baf13576
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174180"
---
# <a name="how-to-make-data-available-for-binding-in-xaml"></a><span data-ttu-id="96671-102">Como disponibilizar dados para associação em XAML</span><span class="sxs-lookup"><span data-stu-id="96671-102">How to: Make Data Available for Binding in XAML</span></span>
<span data-ttu-id="96671-103">Este tópico discute várias maneiras de [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]disponibilizar dados para vinculação, dependendo das necessidades de sua aplicação.</span><span class="sxs-lookup"><span data-stu-id="96671-103">This topic discusses various ways you can make data available for binding in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], depending on the needs of your application.</span></span>  
  
## <a name="example"></a><span data-ttu-id="96671-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="96671-104">Example</span></span>  
 <span data-ttu-id="96671-105">Se você tem um objeto de tempo de execução de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]linguagem comum (CLR) que você gostaria de vincular a `x:Key`partir de , uma maneira que você pode tornar o objeto disponível para vinculação é defini-lo como um recurso e dar-lhe um .</span><span class="sxs-lookup"><span data-stu-id="96671-105">If you have a common language runtime (CLR) object you would like to bind to from [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], one way you can make the object available for binding is to define it as a resource and give it an `x:Key`.</span></span> <span data-ttu-id="96671-106">No exemplo a seguir, temos um objeto `Person` com uma propriedade de cadeia de caracteres denominada `PersonName`.</span><span class="sxs-lookup"><span data-stu-id="96671-106">In the following example, you have a `Person` object with a string property named `PersonName`.</span></span> <span data-ttu-id="96671-107">O `Person` objeto (na linha mostrada `<src>` destacada que contém o `SDKSample`elemento) é definido no namespace chamado .</span><span class="sxs-lookup"><span data-stu-id="96671-107">The `Person` object (in the line shown highlighted that contains the `<src>` element) is defined in the namespace called `SDKSample`.</span></span>  
  
 [!code-xaml[SimpleBinding#Instantiation](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml?highlight=9,37)]  
  
 <span data-ttu-id="96671-108">Em seguida, <xref:System.Windows.Controls.TextBlock> você pode vincular [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]o controle ao objeto, como mostra a linha destacada que contém o `<TextBlock>` elemento.</span><span class="sxs-lookup"><span data-stu-id="96671-108">You can then bind the <xref:System.Windows.Controls.TextBlock> control to the object in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], as the highlighted line that contains the `<TextBlock>` element shows.</span></span>
  
 <span data-ttu-id="96671-109">Alternativamente, você pode <xref:System.Windows.Data.ObjectDataProvider> usar a classe, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="96671-109">Alternatively, you can use the <xref:System.Windows.Data.ObjectDataProvider> class, as in the following example:</span></span>  
  
 [!code-xaml[ObjectDataProvider}](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Page1.xaml?highlight=10-14,42)]  
  
 <span data-ttu-id="96671-110">Você define a vinculação da mesma forma, `<TextBlock>` como a linha destacada que contém o elemento mostra.</span><span class="sxs-lookup"><span data-stu-id="96671-110">You define the binding the same way, as the highlighted line that contains the `<TextBlock>` element shows.</span></span>  
  
 <span data-ttu-id="96671-111">Neste exemplo em particular, o resultado é <xref:System.Windows.Controls.TextBlock> o mesmo: você tem um com o conteúdo `Joe`do texto .</span><span class="sxs-lookup"><span data-stu-id="96671-111">In this particular example, the result is the same: you have a <xref:System.Windows.Controls.TextBlock> with the text content `Joe`.</span></span> <span data-ttu-id="96671-112">No entanto, a <xref:System.Windows.Data.ObjectDataProvider> classe fornece funcionalidades como a capacidade de se vincular ao resultado de um método.</span><span class="sxs-lookup"><span data-stu-id="96671-112">However, the <xref:System.Windows.Data.ObjectDataProvider> class provides functionality such as the ability to bind to the result of a method.</span></span> <span data-ttu-id="96671-113">Você pode optar <xref:System.Windows.Data.ObjectDataProvider> por usar a classe se precisar da funcionalidade que ela fornece.</span><span class="sxs-lookup"><span data-stu-id="96671-113">You can choose to use the <xref:System.Windows.Data.ObjectDataProvider> class if you need the functionality it provides.</span></span>  
  
 <span data-ttu-id="96671-114">No entanto, se estiver associando a um objeto que já foi criado, será necessário definir o `DataContext` no código, como no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="96671-114">However, if you are binding to an object that has already been created, you need to set the `DataContext` in code, as in the following example.</span></span>  
  
 [!code-csharp[ADODataSet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ADODataSet#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ADODataSet/VisualBasic/Window1.xaml.vb#1)]  
  
 <span data-ttu-id="96671-115">Para acessar os dados XML para vincular usando a classe, consulte <xref:System.Windows.Data.XmlDataProvider> [Vincular-se aos dados XML usando um XMLDataProvider e consultas XPath](how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md).</span><span class="sxs-lookup"><span data-stu-id="96671-115">To access XML data for binding using the <xref:System.Windows.Data.XmlDataProvider> class, see [Bind to XML Data Using an XMLDataProvider and XPath Queries](how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md).</span></span> <span data-ttu-id="96671-116">Para acessar os dados XML para vincular usando a <xref:System.Windows.Data.ObjectDataProvider> classe, consulte [Vincular-se a XDocument, XElement ou LINQ para obter resultados de consulta XML](how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md).</span><span class="sxs-lookup"><span data-stu-id="96671-116">To access XML data for binding using the <xref:System.Windows.Data.ObjectDataProvider> class, see [Bind to XDocument, XElement, or LINQ for XML Query Results](how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md).</span></span>  
  
 <span data-ttu-id="96671-117">Para obter informações sobre muitas maneiras que você pode especificar os dados aos quais você está vinculando, consulte [Especificar a Fonte de Vinculação](how-to-specify-the-binding-source.md).</span><span class="sxs-lookup"><span data-stu-id="96671-117">For information about many ways you can specify the data you are binding to, see [Specify the Binding Source](how-to-specify-the-binding-source.md).</span></span> <span data-ttu-id="96671-118">Para obter informações sobre quais tipos de dados você pode vincular ou como implementar seus próprios objetos CLR (Common Language Runtime, tempo de execução de idiomas comuns) para vinculação, consulte [Visão geral de fontes de vinculação](binding-sources-overview.md).</span><span class="sxs-lookup"><span data-stu-id="96671-118">For information about what types of data you can bind to or how to implement your own common language runtime (CLR) objects for binding, see [Binding Sources Overview](binding-sources-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96671-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="96671-119">See also</span></span>

- [<span data-ttu-id="96671-120">Visão geral da vinculação de dados</span><span class="sxs-lookup"><span data-stu-id="96671-120">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="96671-121">Tópicos de como fazer</span><span class="sxs-lookup"><span data-stu-id="96671-121">How-to Topics</span></span>](data-binding-how-to-topics.md)
