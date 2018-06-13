---
title: Como criar uma associação simples
ms.date: 03/30/2017
helpviewer_keywords:
- simple binding [WPF], creating
- data binding [WPF], creating simple bindings
- binding data [WPF], creating
ms.assetid: 69b80f72-6259-44cb-8294-5bdcebca1e08
ms.openlocfilehash: 8910dd3ec6c9f72f9d8fb64cd33912f0d4318e5f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33555004"
---
# <a name="how-to-create-a-simple-binding"></a><span data-ttu-id="084e2-102">Como criar uma associação simples</span><span class="sxs-lookup"><span data-stu-id="084e2-102">How to: Create a Simple Binding</span></span>
<span data-ttu-id="084e2-103">Este exemplo mostra como criar um simples <xref:System.Windows.Data.Binding>.</span><span class="sxs-lookup"><span data-stu-id="084e2-103">This example shows you how to create a simple <xref:System.Windows.Data.Binding>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="084e2-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="084e2-104">Example</span></span>  
 <span data-ttu-id="084e2-105">Neste exemplo, você tem uma `Person` objeto com uma propriedade de cadeia de caracteres denominada `PersonName`.</span><span class="sxs-lookup"><span data-stu-id="084e2-105">In this example, you have a `Person` object with a string property named `PersonName`.</span></span> <span data-ttu-id="084e2-106">O objeto `Person` é definido no namespace chamado `SDKSample`.</span><span class="sxs-lookup"><span data-stu-id="084e2-106">The `Person` object is defined in the namespace called `SDKSample`.</span></span>  
  
 <span data-ttu-id="084e2-107">A linha realçada que contém o `<src>` elemento no exemplo a seguir cria uma instância de `Person` do objeto com um `PersonName` valor da propriedade `Joe`.</span><span class="sxs-lookup"><span data-stu-id="084e2-107">The highlighted line that contains the `<src>` element in the following example instantiates the `Person` object with a `PersonName` property value of `Joe`.</span></span> <span data-ttu-id="084e2-108">Isso é feito o `Resources` seção e atribuído um `x:Key`.</span><span class="sxs-lookup"><span data-stu-id="084e2-108">This is done in the `Resources` section and assigned an `x:Key`.</span></span>  
  
 [!code-xaml[SimpleBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml?highlight=9,37)]  
  
 <span data-ttu-id="084e2-109">A linha realçada que contém o `<TextBlock>` elemento, em seguida, associa a <xref:System.Windows.Controls.TextBlock> o controle para o `PersonName` propriedade.</span><span class="sxs-lookup"><span data-stu-id="084e2-109">The highlighted line that contains the `<TextBlock>` element then binds the <xref:System.Windows.Controls.TextBlock> control to the `PersonName` property.</span></span> <span data-ttu-id="084e2-110">Como resultado, o <xref:System.Windows.Controls.TextBlock> é exibida com o valor "Joe".</span><span class="sxs-lookup"><span data-stu-id="084e2-110">As a result, the <xref:System.Windows.Controls.TextBlock> appears with the value "Joe".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="084e2-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="084e2-111">See Also</span></span>  
 [<span data-ttu-id="084e2-112">Visão geral da vinculação de dados</span><span class="sxs-lookup"><span data-stu-id="084e2-112">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="084e2-113">Tópicos de instruções</span><span class="sxs-lookup"><span data-stu-id="084e2-113">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
