---
title: Como limpar associações
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- bindings [WPF], clearing
- clearing bindings [WPF]
- data binding [WPF], clearing bindings
ms.assetid: 73962a93-32a9-4bcd-9240-bcfbb239093a
ms.openlocfilehash: 66f7eb0209d23660b9c7351ca793f509b2f4bb8d
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458870"
---
# <a name="how-to-clear-bindings"></a><span data-ttu-id="859ce-102">Como limpar associações</span><span class="sxs-lookup"><span data-stu-id="859ce-102">How to: Clear Bindings</span></span>
<span data-ttu-id="859ce-103">Este exemplo mostra como limpar associações de um objeto.</span><span class="sxs-lookup"><span data-stu-id="859ce-103">This example shows how to clear bindings from an object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="859ce-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="859ce-104">Example</span></span>  
 <span data-ttu-id="859ce-105">Para limpar uma associação de uma propriedade individual em um objeto, chame <xref:System.Windows.Data.BindingOperations.ClearBinding%2A> conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="859ce-105">To clear a binding from an individual property on an object, call <xref:System.Windows.Data.BindingOperations.ClearBinding%2A> as shown in the following example.</span></span> <span data-ttu-id="859ce-106">O exemplo a seguir remove a associação da <xref:System.Windows.Controls.TextBlock.TextProperty> de *MyText*, um objeto <xref:System.Windows.Controls.TextBlock>.</span><span class="sxs-lookup"><span data-stu-id="859ce-106">The following example removes the binding from the <xref:System.Windows.Controls.TextBlock.TextProperty> of *mytext*, a <xref:System.Windows.Controls.TextBlock> object.</span></span>  
  
 [!code-csharp[CodeOnlyBinding#ClearBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#clearbinding)]
 [!code-vb[CodeOnlyBinding#ClearBinding](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#clearbinding)]  
  
 <span data-ttu-id="859ce-107">Limpar a associação remove a associação de forma que o valor da propriedade de dependência seja alterado para o que fosse feito sem a associação.</span><span class="sxs-lookup"><span data-stu-id="859ce-107">Clearing the binding removes the binding so that the value of the dependency property is changed to whatever it would have been without the binding.</span></span> <span data-ttu-id="859ce-108">Esse valor pode ser um valor padrão, um valor herdado ou um valor de uma associação de modelo de dados.</span><span class="sxs-lookup"><span data-stu-id="859ce-108">This value could be a default value, an inherited value, or a value from a data template binding.</span></span>  
  
 <span data-ttu-id="859ce-109">Para limpar associações de todas as propriedades possíveis em um objeto, use <xref:System.Windows.Data.BindingOperations.ClearAllBindings%2A>.</span><span class="sxs-lookup"><span data-stu-id="859ce-109">To clear bindings from all possible properties on an object, use <xref:System.Windows.Data.BindingOperations.ClearAllBindings%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="859ce-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="859ce-110">See also</span></span>

- <xref:System.Windows.Data.BindingOperations>
- [<span data-ttu-id="859ce-111">Visão geral da vinculação de dados</span><span class="sxs-lookup"><span data-stu-id="859ce-111">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="859ce-112">Tópicos explicativos</span><span class="sxs-lookup"><span data-stu-id="859ce-112">How-to Topics</span></span>](data-binding-how-to-topics.md)
