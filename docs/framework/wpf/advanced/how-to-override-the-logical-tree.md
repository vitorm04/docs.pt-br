---
title: 'Como: Substituir a árvore lógica'
ms.date: 03/30/2017
helpviewer_keywords:
- overriding the logical tree [WPF]
- logical tree [WPF], overriding
ms.assetid: 0ae4d074-8113-4b06-b4fa-e0f39d4967a6
ms.openlocfilehash: bf3459fff1a90326794d6713dd39c73596b0e960
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61768440"
---
# <a name="how-to-override-the-logical-tree"></a><span data-ttu-id="08313-102">Como: Substituir a árvore lógica</span><span class="sxs-lookup"><span data-stu-id="08313-102">How to: Override the Logical Tree</span></span>
<span data-ttu-id="08313-103">Embora não seja necessário na maioria dos casos, autores de controle avançados tem a opção de substituir a árvore lógica.</span><span class="sxs-lookup"><span data-stu-id="08313-103">Although it is not necessary in most cases, advanced control authors have the option to override the logical tree.</span></span>  
  
## <a name="example"></a><span data-ttu-id="08313-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="08313-104">Example</span></span>  
 <span data-ttu-id="08313-105">Este exemplo descreve como subclasse <xref:System.Windows.Controls.StackPanel> para substituir a árvore lógica, nesse caso, para impor um comportamento que o painel pode ter somente e renderizará somente um único elemento filho.</span><span class="sxs-lookup"><span data-stu-id="08313-105">This example describes how to subclass <xref:System.Windows.Controls.StackPanel> to override the logical tree, in this case to enforce a behavior that the panel may only have and will only render a single child element.</span></span> <span data-ttu-id="08313-106">Isso não é necessariamente um comportamento praticamente desejável, mas é mostrado aqui como um meio de que ilustra o cenário para substituir a árvore lógica normal de um elemento.</span><span class="sxs-lookup"><span data-stu-id="08313-106">This isn't necessarily a practically desirable behavior, but is shown here as a means of illustrating the scenario for overriding an element's normal logical tree.</span></span>  
  
 [!code-csharp[LogicalOverride#SingletonPanel](~/samples/snippets/csharp/VS_Snippets_Wpf/LogicalOverride/CSharp/SDKSampleLibrary/class1.cs#singletonpanel)]  
  
 <span data-ttu-id="08313-107">Para obter mais informações sobre a árvore lógica, consulte [Árvores no WPF](trees-in-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="08313-107">For more information on the logical tree, see [Trees in WPF](trees-in-wpf.md).</span></span>
