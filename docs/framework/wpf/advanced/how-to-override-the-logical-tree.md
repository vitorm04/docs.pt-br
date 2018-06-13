---
title: Como substituir a árvore lógica
ms.date: 03/30/2017
helpviewer_keywords:
- overriding the logical tree [WPF]
- logical tree [WPF], overriding
ms.assetid: 0ae4d074-8113-4b06-b4fa-e0f39d4967a6
ms.openlocfilehash: 0c7269b9ea052019e2e4f6def23b063903cbb5e1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33542884"
---
# <a name="how-to-override-the-logical-tree"></a><span data-ttu-id="a3208-102">Como substituir a árvore lógica</span><span class="sxs-lookup"><span data-stu-id="a3208-102">How to: Override the Logical Tree</span></span>
<span data-ttu-id="a3208-103">Embora não seja necessário na maioria dos casos, autores de controle avançados têm a opção de substituir a árvore lógica.</span><span class="sxs-lookup"><span data-stu-id="a3208-103">Although it is not necessary in most cases, advanced control authors have the option to override the logical tree.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a3208-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a3208-104">Example</span></span>  
 <span data-ttu-id="a3208-105">Este exemplo descreve como subclasse <xref:System.Windows.Controls.StackPanel> para substituir a árvore lógica, nesse caso, para impor um comportamento que o painel somente pode ter e processará apenas um único elemento filho.</span><span class="sxs-lookup"><span data-stu-id="a3208-105">This example describes how to subclass <xref:System.Windows.Controls.StackPanel> to override the logical tree, in this case to enforce a behavior that the panel may only have and will only render a single child element.</span></span> <span data-ttu-id="a3208-106">Isso não é necessariamente um comportamento praticamente desejável, mas é mostrado aqui como um meio de que ilustra o cenário para substituir a árvore lógica normal de um elemento.</span><span class="sxs-lookup"><span data-stu-id="a3208-106">This isn't necessarily a practically desirable behavior, but is shown here as a means of illustrating the scenario for overriding an element's normal logical tree.</span></span>  
  
 [!code-csharp[LogicalOverride#SingletonPanel](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LogicalOverride/CSharp/SDKSampleLibrary/class1.cs#singletonpanel)]  
  
 <span data-ttu-id="a3208-107">Para obter mais informações sobre a árvore lógica, consulte [Árvores no WPF](../../../../docs/framework/wpf/advanced/trees-in-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="a3208-107">For more information on the logical tree, see [Trees in WPF](../../../../docs/framework/wpf/advanced/trees-in-wpf.md).</span></span>
