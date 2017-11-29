---
title: "Como especificar a origem da associação"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- binding data [WPF], binding sources
- data binding [WPF], binding source
- binding sources [WPF]
ms.assetid: 55d47757-2648-4a52-987f-b767953f168c
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 05f77e8939b9b81a9e3861df6a44bc3585a0a504
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-specify-the-binding-source"></a><span data-ttu-id="d0d69-102">Como especificar a origem da associação</span><span class="sxs-lookup"><span data-stu-id="d0d69-102">How to: Specify the Binding Source</span></span>
<span data-ttu-id="d0d69-103">Na associação de dados, o objeto da origem de associação refere-se àquele cujos dados você deseja obter.</span><span class="sxs-lookup"><span data-stu-id="d0d69-103">In data binding, the binding source object refers to the object you obtain your data from.</span></span> <span data-ttu-id="d0d69-104">Este tópico descreve as diferentes maneiras de especificar a origem da associação.</span><span class="sxs-lookup"><span data-stu-id="d0d69-104">This topic describes the different ways of specifying the binding source.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d0d69-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d0d69-105">Example</span></span>  
 <span data-ttu-id="d0d69-106">Se você estiver associando várias propriedades a uma fonte comum, será recomendável usar a propriedade `DataContext`, que fornece uma maneira conveniente para estabelecer um escopo dentro do qual todas as propriedades associadas a dados herdarão uma fonte comum.</span><span class="sxs-lookup"><span data-stu-id="d0d69-106">If you are binding several properties to a common source, you want to use the `DataContext` property, which provides a convenient way to establish a scope within which all data-bound properties inherit a common source.</span></span>  
  
 <span data-ttu-id="d0d69-107">No exemplo a seguir, o contexto de dados é estabelecido no elemento raiz do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d0d69-107">In the following example, the data context is established on the root element of the application.</span></span> <span data-ttu-id="d0d69-108">Isso permite que todos os elementos filho herdem esse contexto de dados.</span><span class="sxs-lookup"><span data-stu-id="d0d69-108">This allows all child elements to inherit that data context.</span></span> <span data-ttu-id="d0d69-109">Os dados para a associação provêm de uma classe personalizada de dados, `NetIncome`, referenciada diretamente por meio de um mapeamento e com a chave de recurso de `incomeDataSource` concedida.</span><span class="sxs-lookup"><span data-stu-id="d0d69-109">Data for the binding comes from a custom data class, `NetIncome`, referenced directly through a mapping and given the resource key of `incomeDataSource`.</span></span>  
  
 [!code-xaml[DirectionalBinding#DataContext1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#datacontext1)]  
[!code-xaml[DirectionalBinding#DataContext2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#datacontext2)]  
  
 <span data-ttu-id="d0d69-110">O exemplo a seguir mostra a definição da classe `NetIncome`.</span><span class="sxs-lookup"><span data-stu-id="d0d69-110">The following example shows the definition of the `NetIncome` class.</span></span>  
  
 [!code-csharp[DirectionalBinding#DataObject](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/billsdata.cs#dataobject)]
 [!code-vb[DirectionalBinding#DataObject](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DirectionalBinding/VisualBasic/NetIncome.vb#dataobject)]  
  
> [!NOTE]
>  <span data-ttu-id="d0d69-111">O exemplo acima instancia o objeto na marcação e o utiliza como um recurso.</span><span class="sxs-lookup"><span data-stu-id="d0d69-111">The above example instantiates the object in markup and uses it as a resource.</span></span> <span data-ttu-id="d0d69-112">Se você deseja associar a um objeto já instanciado no código, é necessário definir a propriedade `DataContext` com programação.</span><span class="sxs-lookup"><span data-stu-id="d0d69-112">If you want to bind to an object that has already been instantiated in code, you need to set the `DataContext` property programmatically.</span></span> <span data-ttu-id="d0d69-113">Por exemplo, consulte [Disponibilizar dados para associação em XAML](../../../../docs/framework/wpf/data/how-to-make-data-available-for-binding-in-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="d0d69-113">For an example, see [Make Data Available for Binding in XAML](../../../../docs/framework/wpf/data/how-to-make-data-available-for-binding-in-xaml.md).</span></span>  
  
 <span data-ttu-id="d0d69-114">Como alternativa, se quiser especificar a fonte em suas associações individuais explicitamente, você terá as opções a seguir.</span><span class="sxs-lookup"><span data-stu-id="d0d69-114">Alternatively, if you want to specify the source on your individual bindings explicitly, you have the following options.</span></span> <span data-ttu-id="d0d69-115">Eles têm precedência sobre o contexto de dados herdado.</span><span class="sxs-lookup"><span data-stu-id="d0d69-115">These take precedence over the inherited data context.</span></span>  
  
|<span data-ttu-id="d0d69-116">Propriedade</span><span class="sxs-lookup"><span data-stu-id="d0d69-116">Property</span></span>|<span data-ttu-id="d0d69-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="d0d69-117">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.Windows.Data.Binding.Source%2A>|<span data-ttu-id="d0d69-118">Você pode usar essa propriedade para definir a fonte para uma instância de um objeto.</span><span class="sxs-lookup"><span data-stu-id="d0d69-118">You use this property to set the source to an instance of an object.</span></span> <span data-ttu-id="d0d69-119">Se você não precisar da funcionalidade de estabelecer um escopo no qual diversas propriedades herdam o mesmo contexto de dados, você pode usar o <xref:System.Windows.Data.Binding.Source%2A> propriedade em vez do `DataContext` propriedade.</span><span class="sxs-lookup"><span data-stu-id="d0d69-119">If you do not need the functionality of establishing a scope in which several properties inherit the same data context, you can use the <xref:System.Windows.Data.Binding.Source%2A> property instead of the `DataContext` property.</span></span> <span data-ttu-id="d0d69-120">Para obter mais informações, consulte <xref:System.Windows.Data.Binding.Source%2A>.</span><span class="sxs-lookup"><span data-stu-id="d0d69-120">For more information, see <xref:System.Windows.Data.Binding.Source%2A>.</span></span>|  
|<xref:System.Windows.Data.Binding.RelativeSource%2A>|<span data-ttu-id="d0d69-121">Isso é útil quando você deseja especificar a fonte com relação a onde está o seu destino de associação.</span><span class="sxs-lookup"><span data-stu-id="d0d69-121">This is useful when you want to specify the source relative to where your binding target is.</span></span> <span data-ttu-id="d0d69-122">Alguns cenários comuns em que você pode usar essa propriedade é quando você deseja associar uma propriedade do seu elemento a outra propriedade do mesmo elemento ou caso esteja definindo uma associação em um estilo ou um modelo.</span><span class="sxs-lookup"><span data-stu-id="d0d69-122">Some common scenarios where you may use this property is when you want to bind one property of your element to another property of the same element or if you are defining a binding in a style or a template.</span></span> <span data-ttu-id="d0d69-123">Para obter mais informações, consulte <xref:System.Windows.Data.Binding.RelativeSource%2A>.</span><span class="sxs-lookup"><span data-stu-id="d0d69-123">For more information, see <xref:System.Windows.Data.Binding.RelativeSource%2A>.</span></span>|  
|<xref:System.Windows.Data.Binding.ElementName%2A>|<span data-ttu-id="d0d69-124">Especifique uma cadeia de caracteres que representa o elemento ao qual você deseja associar.</span><span class="sxs-lookup"><span data-stu-id="d0d69-124">You specify a string that represents the element you want to bind to.</span></span> <span data-ttu-id="d0d69-125">Isso é útil quando você deseja associar à propriedade de outro elemento em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d0d69-125">This is useful when you want to bind to the property of another element on your application.</span></span> <span data-ttu-id="d0d69-126">Por exemplo, se você quiser usar um <xref:System.Windows.Controls.Slider> para controlar a altura do controle de outro em seu aplicativo, ou se você deseja vincular a <xref:System.Windows.Controls.ContentControl.Content%2A> de seu controle o <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> propriedade do seu <xref:System.Windows.Controls.ListBox> controle.</span><span class="sxs-lookup"><span data-stu-id="d0d69-126">For example, if you want to use a <xref:System.Windows.Controls.Slider> to control the height of another control in your application, or if you want to bind the <xref:System.Windows.Controls.ContentControl.Content%2A> of your control to the <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> property of your <xref:System.Windows.Controls.ListBox> control.</span></span> <span data-ttu-id="d0d69-127">Para obter mais informações, consulte <xref:System.Windows.Data.Binding.ElementName%2A>.</span><span class="sxs-lookup"><span data-stu-id="d0d69-127">For more information, see <xref:System.Windows.Data.Binding.ElementName%2A>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d0d69-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d0d69-128">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.DataContext%2A?displayProperty=nameWithType>  
 <xref:System.Windows.FrameworkContentElement.DataContext%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="d0d69-129">Herança do valor da propriedade</span><span class="sxs-lookup"><span data-stu-id="d0d69-129">Property Value Inheritance</span></span>](../../../../docs/framework/wpf/advanced/property-value-inheritance.md)  
 [<span data-ttu-id="d0d69-130">Visão geral da vinculação de dados</span><span class="sxs-lookup"><span data-stu-id="d0d69-130">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="d0d69-131">Visão geral das declarações de associação</span><span class="sxs-lookup"><span data-stu-id="d0d69-131">Binding Declarations Overview</span></span>](../../../../docs/framework/wpf/data/binding-declarations-overview.md)  
 [<span data-ttu-id="d0d69-132">Tópicos explicativos</span><span class="sxs-lookup"><span data-stu-id="d0d69-132">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
