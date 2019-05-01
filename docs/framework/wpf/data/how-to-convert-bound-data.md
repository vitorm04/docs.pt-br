---
title: 'Como: Converter dados associados'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- converting [WPF], bound data
- data binding [WPF], converting bound data
- binding data [WPF], converting bound data
ms.assetid: b00aaa19-c6df-4c3b-a9fd-88a0b488df2b
ms.openlocfilehash: 40699bec1c6cd775f7f8495b7a49eda15fb2ed83
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62020927"
---
# <a name="how-to-convert-bound-data"></a><span data-ttu-id="b5a30-102">Como: Converter dados associados</span><span class="sxs-lookup"><span data-stu-id="b5a30-102">How to: Convert Bound Data</span></span>
<span data-ttu-id="b5a30-103">Este exemplo mostra como aplicar a conversão a dados que são usados em associações.</span><span class="sxs-lookup"><span data-stu-id="b5a30-103">This example shows how to apply conversion to data that is used in bindings.</span></span>  
  
 <span data-ttu-id="b5a30-104">Para converter dados durante a associação, você deve criar uma classe que implementa o <xref:System.Windows.Data.IValueConverter> interface, que inclui o <xref:System.Windows.Data.IValueConverter.Convert%2A> e <xref:System.Windows.Data.IValueConverter.ConvertBack%2A> métodos.</span><span class="sxs-lookup"><span data-stu-id="b5a30-104">To convert data during binding, you must create a class that implements the <xref:System.Windows.Data.IValueConverter> interface, which includes the <xref:System.Windows.Data.IValueConverter.Convert%2A> and <xref:System.Windows.Data.IValueConverter.ConvertBack%2A> methods.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b5a30-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b5a30-105">Example</span></span>  
 <span data-ttu-id="b5a30-106">O exemplo a seguir mostra a implementação de um conversor de data que converte o valor passado de modo que mostre apenas o ano, mês e dia.</span><span class="sxs-lookup"><span data-stu-id="b5a30-106">The following example shows the implementation of a date converter that converts the date value passed in so that it only shows the year, the month, and the day.</span></span> <span data-ttu-id="b5a30-107">Ao implementar o <xref:System.Windows.Data.IValueConverter> interface, é uma boa prática decorar a implementação com um <xref:System.Windows.Data.ValueConversionAttribute> das ferramentas de atributo para indicar ao desenvolvimento os tipos de dados envolvidos na conversão, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="b5a30-107">When implementing the <xref:System.Windows.Data.IValueConverter> interface, it is a good practice to decorate the implementation with a <xref:System.Windows.Data.ValueConversionAttribute> attribute to indicate to development tools the data types involved in the conversion, as in the following example:</span></span>  
  
 [!code-csharp[DataBindingLab#18](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DateConverter.cs#18)]
 [!code-vb[DataBindingLab#18](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/DateConverter.vb#18)]  
  
 <span data-ttu-id="b5a30-108">Depois de criar um conversor, você pode adicioná-lo como um recurso em seu arquivo [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b5a30-108">Once you have created a converter, you can add it as a resource in your [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file.</span></span> <span data-ttu-id="b5a30-109">No exemplo a seguir, o *src* mapeia para o namespace no qual *DateConverter* está definido.</span><span class="sxs-lookup"><span data-stu-id="b5a30-109">In the following example, *src* maps to the namespace in which *DateConverter* is defined.</span></span>  
  
 [!code-xaml[DataBindingLab#15](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DataBindingLabApp.xaml#15)]  
  
 <span data-ttu-id="b5a30-110">Finalmente, você pode usar o conversor em sua associação usando a sintaxe a seguir.</span><span class="sxs-lookup"><span data-stu-id="b5a30-110">Finally, you can use the converter in your binding using the following syntax.</span></span> <span data-ttu-id="b5a30-111">No exemplo a seguir, o conteúdo de texto a <xref:System.Windows.Controls.TextBlock> está associado a *StartDate*, que é uma propriedade de uma fonte de dados externa.</span><span class="sxs-lookup"><span data-stu-id="b5a30-111">In the following example, the text content of the <xref:System.Windows.Controls.TextBlock> is bound to *StartDate*, which is a property of an external data source.</span></span>  
  
 [!code-xaml[DataBindingLab#17](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DataBindingLabApp.xaml#17)]  
  
 <span data-ttu-id="b5a30-112">Os recursos de estilo referenciados no exemplo acima são definidos em uma seção de recursos não mostrada neste tópico.</span><span class="sxs-lookup"><span data-stu-id="b5a30-112">The style resources referenced in the above example are defined in a resource section not shown in this topic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5a30-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b5a30-113">See also</span></span>

- [<span data-ttu-id="b5a30-114">Implementar a validação de associação</span><span class="sxs-lookup"><span data-stu-id="b5a30-114">Implement Binding Validation</span></span>](how-to-implement-binding-validation.md)
- [<span data-ttu-id="b5a30-115">Visão geral da vinculação de dados</span><span class="sxs-lookup"><span data-stu-id="b5a30-115">Data Binding Overview</span></span>](data-binding-overview.md)
- [<span data-ttu-id="b5a30-116">Tópicos de instruções</span><span class="sxs-lookup"><span data-stu-id="b5a30-116">How-to Topics</span></span>](data-binding-how-to-topics.md)
