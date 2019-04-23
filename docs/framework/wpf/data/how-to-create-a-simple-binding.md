---
title: 'Como: Criar uma associação simples'
ms.date: 03/30/2017
helpviewer_keywords:
- simple binding [WPF], creating
- data binding [WPF], creating simple bindings
- binding data [WPF], creating
ms.assetid: 69b80f72-6259-44cb-8294-5bdcebca1e08
ms.openlocfilehash: d617c8b97aa679398ed2d061a652f5164f1e499b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59094379"
---
# <a name="how-to-create-a-simple-binding"></a><span data-ttu-id="eed00-102">Como: Criar uma associação simples</span><span class="sxs-lookup"><span data-stu-id="eed00-102">How to: Create a Simple Binding</span></span>
<span data-ttu-id="eed00-103">Este exemplo mostra como criar um simples <xref:System.Windows.Data.Binding>.</span><span class="sxs-lookup"><span data-stu-id="eed00-103">This example shows you how to create a simple <xref:System.Windows.Data.Binding>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eed00-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="eed00-104">Example</span></span>  
 <span data-ttu-id="eed00-105">Neste exemplo, você tem um `Person` objeto com uma propriedade de cadeia de caracteres denominada `PersonName`.</span><span class="sxs-lookup"><span data-stu-id="eed00-105">In this example, you have a `Person` object with a string property named `PersonName`.</span></span> <span data-ttu-id="eed00-106">O objeto `Person` é definido no namespace chamado `SDKSample`.</span><span class="sxs-lookup"><span data-stu-id="eed00-106">The `Person` object is defined in the namespace called `SDKSample`.</span></span>  
  
 <span data-ttu-id="eed00-107">A linha realçada que contém o `<src>` elemento no exemplo a seguir cria uma instância de `Person` do objeto com um `PersonName` valor da propriedade `Joe`.</span><span class="sxs-lookup"><span data-stu-id="eed00-107">The highlighted line that contains the `<src>` element in the following example instantiates the `Person` object with a `PersonName` property value of `Joe`.</span></span> <span data-ttu-id="eed00-108">Isso é feito na `Resources` seção e atribuído um `x:Key`.</span><span class="sxs-lookup"><span data-stu-id="eed00-108">This is done in the `Resources` section and assigned an `x:Key`.</span></span>  
  
 [!code-xaml[SimpleBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml?highlight=9,37)]  
  
 <span data-ttu-id="eed00-109">A linha realçada que contém o `<TextBlock>` , em seguida, associa um elemento de <xref:System.Windows.Controls.TextBlock> o controle para o `PersonName` propriedade.</span><span class="sxs-lookup"><span data-stu-id="eed00-109">The highlighted line that contains the `<TextBlock>` element then binds the <xref:System.Windows.Controls.TextBlock> control to the `PersonName` property.</span></span> <span data-ttu-id="eed00-110">Como resultado, o <xref:System.Windows.Controls.TextBlock> aparece com o valor "Joe".</span><span class="sxs-lookup"><span data-stu-id="eed00-110">As a result, the <xref:System.Windows.Controls.TextBlock> appears with the value "Joe".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eed00-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="eed00-111">See also</span></span>

- [<span data-ttu-id="eed00-112">Visão geral da vinculação de dados</span><span class="sxs-lookup"><span data-stu-id="eed00-112">Data Binding Overview</span></span>](data-binding-overview.md)
- [<span data-ttu-id="eed00-113">Tópicos de instruções</span><span class="sxs-lookup"><span data-stu-id="eed00-113">How-to Topics</span></span>](data-binding-how-to-topics.md)
