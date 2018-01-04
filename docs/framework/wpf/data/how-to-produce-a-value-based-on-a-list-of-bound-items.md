---
title: Como produzir um valor com base em uma lista de itens associados
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
- data binding [WPF], MultiBinding
- Multibinding [WPF]
ms.assetid: b3d06378-b511-4181-95aa-316d60c9229b
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c3987690a1acb180ee22fa02e399accd9c5d481d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-produce-a-value-based-on-a-list-of-bound-items"></a><span data-ttu-id="430d0-102">Como produzir um valor com base em uma lista de itens associados</span><span class="sxs-lookup"><span data-stu-id="430d0-102">How to: Produce a Value Based on a List of Bound Items</span></span>
<span data-ttu-id="430d0-103"><xref:System.Windows.Data.MultiBinding>permite associar uma propriedade de destino da associação a uma lista de propriedades de fonte e, em seguida, aplicar lógica para produzir um valor com as entradas disponíveis.</span><span class="sxs-lookup"><span data-stu-id="430d0-103"><xref:System.Windows.Data.MultiBinding> allows you to bind a binding target property to a list of source properties and then apply logic to produce a value with the given inputs.</span></span> <span data-ttu-id="430d0-104">Este exemplo demonstra como usar <xref:System.Windows.Data.MultiBinding>.</span><span class="sxs-lookup"><span data-stu-id="430d0-104">This example demonstrates how to use <xref:System.Windows.Data.MultiBinding>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="430d0-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="430d0-105">Example</span></span>  
 <span data-ttu-id="430d0-106">No exemplo a seguir, `NameListData` refere-se a uma coleção de objetos de `PersonName`, que são objetos que contêm duas propriedades, `firstName` e `lastName`.</span><span class="sxs-lookup"><span data-stu-id="430d0-106">In the following example, `NameListData` refers to a collection of `PersonName` objects, which are objects that contain two properties, `firstName` and `lastName`.</span></span> <span data-ttu-id="430d0-107">O exemplo a seguir produz um <xref:System.Windows.Controls.TextBlock> que mostra os nomes e sobrenomes de uma pessoa com o sobrenome em primeiro lugar.</span><span class="sxs-lookup"><span data-stu-id="430d0-107">The following example produces a <xref:System.Windows.Controls.TextBlock> that shows the first and last names of a person with the last name first.</span></span>  
  
 [!code-xaml[MultiBinding#Resources1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#resources1)]  
[!code-xaml[MultiBinding#Resources2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#resources2)]  
[!code-xaml[MultiBinding#MultiBindingTextBox2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#multibindingtextbox2)]  
[!code-xaml[MultiBinding#Window](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#window)]  
  
 <span data-ttu-id="430d0-108">Para entender como o formato de sobrenome primeiro é produzido, vamos dar uma olhada na implementação do `NameConverter`:</span><span class="sxs-lookup"><span data-stu-id="430d0-108">To understand how the last-name-first format is produced, let's take a look at the implementation of the `NameConverter`:</span></span>  
  
 [!code-csharp[MultiBinding#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/NameConverter.cs#3)]
 [!code-vb[MultiBinding#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MultiBinding/VisualBasic/NameConverter.vb#3)]  
  
 <span data-ttu-id="430d0-109">`NameConverter` implementa a interface <xref:System.Windows.Data.IMultiValueConverter>.</span><span class="sxs-lookup"><span data-stu-id="430d0-109">`NameConverter` implements the <xref:System.Windows.Data.IMultiValueConverter> interface.</span></span> <span data-ttu-id="430d0-110">O `NameConverter` usa os valores das associações individuais e os armazena na matriz de objetos de valores.</span><span class="sxs-lookup"><span data-stu-id="430d0-110">`NameConverter` takes the values from the individual bindings and stores them in the values object array.</span></span> <span data-ttu-id="430d0-111">A ordem na qual o <xref:System.Windows.Data.Binding> elementos aparecem sob o <xref:System.Windows.Data.MultiBinding> elemento é a ordem em que esses valores são armazenados na matriz.</span><span class="sxs-lookup"><span data-stu-id="430d0-111">The order in which the <xref:System.Windows.Data.Binding> elements appear under the <xref:System.Windows.Data.MultiBinding> element is the order in which those values are stored in the array.</span></span> <span data-ttu-id="430d0-112">O valor da <xref:System.Windows.Data.MultiBinding.ConverterParameter%2A> referenciado pelo argumento do atributo de <xref:System.Windows.Data.MultiBinding.Converter%2A> método, que executa uma troca no parâmetro para determinar como o nome de formato.</span><span class="sxs-lookup"><span data-stu-id="430d0-112">The value of the <xref:System.Windows.Data.MultiBinding.ConverterParameter%2A> attribute is referenced by the parameter argument of the <xref:System.Windows.Data.MultiBinding.Converter%2A> method, which performs a switch on the parameter to determine how to format the name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="430d0-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="430d0-113">See Also</span></span>  
 [<span data-ttu-id="430d0-114">Converter dados associados</span><span class="sxs-lookup"><span data-stu-id="430d0-114">Convert Bound Data</span></span>](../../../../docs/framework/wpf/data/how-to-convert-bound-data.md)  
 [<span data-ttu-id="430d0-115">Visão geral da vinculação de dados</span><span class="sxs-lookup"><span data-stu-id="430d0-115">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="430d0-116">Tópicos de instruções</span><span class="sxs-lookup"><span data-stu-id="430d0-116">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
