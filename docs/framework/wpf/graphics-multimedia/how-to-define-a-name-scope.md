---
title: 'Como: Definir um escopo de nome'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- name scope [WPF], defining
- Storyboards [WPF], animating in procedural code
- animation [WPF], Storyboards [WPF], in procedural code
ms.assetid: 4f361925-6a08-40dc-8231-a61111c6b28b
ms.openlocfilehash: 656c1e9af11697cd4a1253bdab673887765976a6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54674460"
---
# <a name="how-to-define-a-name-scope"></a><span data-ttu-id="af20f-102">Como: Definir um escopo de nome</span><span class="sxs-lookup"><span data-stu-id="af20f-102">How to: Define a Name Scope</span></span>
<span data-ttu-id="af20f-103">Para animar com <xref:System.Windows.Media.Animation.Storyboard> no código, você deve criar um <xref:System.Windows.NameScope> e registrar os nomes de objetos de destino com o elemento que possui esse escopo de nome.</span><span class="sxs-lookup"><span data-stu-id="af20f-103">To animate with <xref:System.Windows.Media.Animation.Storyboard> in code, you must create a <xref:System.Windows.NameScope> and register the target objects' names with the element that owns that name scope.</span></span> <span data-ttu-id="af20f-104">No exemplo a seguir, uma <xref:System.Windows.NameScope> é criado para `myMainPanel`.</span><span class="sxs-lookup"><span data-stu-id="af20f-104">In the following example, a <xref:System.Windows.NameScope> is created for `myMainPanel`.</span></span> <span data-ttu-id="af20f-105">Dois botões, `button1` e `button2`, são adicionados ao painel e os nomes registrados.</span><span class="sxs-lookup"><span data-stu-id="af20f-105">Two buttons, `button1` and `button2`, are added to the panel, and their names registered.</span></span> <span data-ttu-id="af20f-106">Várias animações e um <xref:System.Windows.Media.Animation.Storyboard> são criados.</span><span class="sxs-lookup"><span data-stu-id="af20f-106">Several animations and a <xref:System.Windows.Media.Animation.Storyboard> are created.</span></span> <span data-ttu-id="af20f-107">O storyboard <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> método é usado para iniciar as animações.</span><span class="sxs-lookup"><span data-stu-id="af20f-107">The storyboard's <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> method is used to start the animations.</span></span>  
  
 <span data-ttu-id="af20f-108">Porque `button1`, `button2`, e `myMainPanel` compartilham o mesmo escopo de nome, qualquer um deles pode ser usado com o <xref:System.Windows.Media.Animation.Storyboard> <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> método para iniciar as animações.</span><span class="sxs-lookup"><span data-stu-id="af20f-108">Because `button1`, `button2`, and `myMainPanel` all share the same name scope, any one of them can be used with the <xref:System.Windows.Media.Animation.Storyboard> <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> method to start the animations.</span></span>  
  
## <a name="example"></a><span data-ttu-id="af20f-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="af20f-109">Example</span></span>  
 [!code-csharp[StoryboardBeginAnimation_procedural_snip#NameScopeExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StoryboardBeginAnimation_procedural_snip/CSharp/ScopeExample.cs#namescopeexample)]
 [!code-vb[StoryboardBeginAnimation_procedural_snip#NameScopeExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StoryboardBeginAnimation_procedural_snip/visualbasic/scopeexample.vb#namescopeexample)]  
  
## <a name="see-also"></a><span data-ttu-id="af20f-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="af20f-110">See also</span></span>
- [<span data-ttu-id="af20f-111">Animar uma propriedade usando um storyboard</span><span class="sxs-lookup"><span data-stu-id="af20f-111">Animate a Property by Using a Storyboard</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)
- [<span data-ttu-id="af20f-112">Visão geral da animação</span><span class="sxs-lookup"><span data-stu-id="af20f-112">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
