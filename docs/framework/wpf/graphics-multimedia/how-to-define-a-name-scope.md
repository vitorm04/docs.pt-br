---
title: Como definir um escopo de nome
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- name scope [WPF], defining
- Storyboards [WPF], animating in procedural code
- animation [WPF], Storyboards [WPF], in procedural code
ms.assetid: 4f361925-6a08-40dc-8231-a61111c6b28b
ms.openlocfilehash: 689c8187fcf17ef48a73bc5a6fc4928f3be1a078
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33559709"
---
# <a name="how-to-define-a-name-scope"></a><span data-ttu-id="fcbda-102">Como definir um escopo de nome</span><span class="sxs-lookup"><span data-stu-id="fcbda-102">How to: Define a Name Scope</span></span>
<span data-ttu-id="fcbda-103">Para animar com <xref:System.Windows.Media.Animation.Storyboard> no código, você deve criar um <xref:System.Windows.NameScope> e registrar os nomes dos objetos de destino com o elemento que possui esse escopo de nomes.</span><span class="sxs-lookup"><span data-stu-id="fcbda-103">To animate with <xref:System.Windows.Media.Animation.Storyboard> in code, you must create a <xref:System.Windows.NameScope> and register the target objects' names with the element that owns that name scope.</span></span> <span data-ttu-id="fcbda-104">No exemplo a seguir, uma <xref:System.Windows.NameScope> é criado para `myMainPanel`.</span><span class="sxs-lookup"><span data-stu-id="fcbda-104">In the following example, a <xref:System.Windows.NameScope> is created for `myMainPanel`.</span></span> <span data-ttu-id="fcbda-105">Dois botões, `button1` e `button2`, são adicionados ao painel e seus nomes registrados.</span><span class="sxs-lookup"><span data-stu-id="fcbda-105">Two buttons, `button1` and `button2`, are added to the panel, and their names registered.</span></span> <span data-ttu-id="fcbda-106">Várias animações e um <xref:System.Windows.Media.Animation.Storyboard> são criados.</span><span class="sxs-lookup"><span data-stu-id="fcbda-106">Several animations and a <xref:System.Windows.Media.Animation.Storyboard> are created.</span></span> <span data-ttu-id="fcbda-107">O storyboard <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> método é usado para iniciar as animações.</span><span class="sxs-lookup"><span data-stu-id="fcbda-107">The storyboard's <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> method is used to start the animations.</span></span>  
  
 <span data-ttu-id="fcbda-108">Porque `button1`, `button2`, e `myMainPanel` compartilham o mesmo escopo de nomes, qualquer um deles pode ser usado com o <xref:System.Windows.Media.Animation.Storyboard> <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> método para iniciar as animações.</span><span class="sxs-lookup"><span data-stu-id="fcbda-108">Because `button1`, `button2`, and `myMainPanel` all share the same name scope, any one of them can be used with the <xref:System.Windows.Media.Animation.Storyboard> <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> method to start the animations.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fcbda-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="fcbda-109">Example</span></span>  
 [!code-csharp[StoryboardBeginAnimation_procedural_snip#NameScopeExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StoryboardBeginAnimation_procedural_snip/CSharp/ScopeExample.cs#namescopeexample)]
 [!code-vb[StoryboardBeginAnimation_procedural_snip#NameScopeExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StoryboardBeginAnimation_procedural_snip/visualbasic/scopeexample.vb#namescopeexample)]  
  
## <a name="see-also"></a><span data-ttu-id="fcbda-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fcbda-110">See Also</span></span>  
 [<span data-ttu-id="fcbda-111">Animar uma propriedade usando um storyboard</span><span class="sxs-lookup"><span data-stu-id="fcbda-111">Animate a Property by Using a Storyboard</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)  
 [<span data-ttu-id="fcbda-112">Visão geral da animação</span><span class="sxs-lookup"><span data-stu-id="fcbda-112">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
