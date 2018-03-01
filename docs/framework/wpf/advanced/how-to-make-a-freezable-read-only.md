---
title: "Como tornar um congelável somente leitura"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Freezable objects [WPF], making read-only
ms.assetid: 6c544b7d-d3c9-4736-aa90-4b8728234ccb
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: aa6d3f7109e8258dff0a07556bc8572f6071c961
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-make-a-freezable-read-only"></a><span data-ttu-id="f1370-102">Como tornar um congelável somente leitura</span><span class="sxs-lookup"><span data-stu-id="f1370-102">How to: Make a Freezable Read-Only</span></span>
<span data-ttu-id="f1370-103">Este exemplo mostra como fazer uma <xref:System.Windows.Freezable> somente leitura chamando seu <xref:System.Windows.Freezable.Freeze%2A> método.</span><span class="sxs-lookup"><span data-stu-id="f1370-103">This example shows how to make a <xref:System.Windows.Freezable> read-only by calling its <xref:System.Windows.Freezable.Freeze%2A> method.</span></span>  
  
 <span data-ttu-id="f1370-104">Não é possível congelar uma <xref:System.Windows.Freezable> objeto se qualquer uma das seguintes condições for `true` sobre o objeto:</span><span class="sxs-lookup"><span data-stu-id="f1370-104">You cannot freeze a <xref:System.Windows.Freezable> object if any one of the following conditions is `true` about the object:</span></span>  
  
-   <span data-ttu-id="f1370-105">Ele tem propriedades animadas ou associadas a dados.</span><span class="sxs-lookup"><span data-stu-id="f1370-105">It has animated or data bound properties.</span></span>  
  
-   <span data-ttu-id="f1370-106">Ela tem propriedades que são definidas por um recurso dinâmico.</span><span class="sxs-lookup"><span data-stu-id="f1370-106">It has properties that are set by a dynamic resource.</span></span> <span data-ttu-id="f1370-107">Para obter mais informações sobre recursos dinâmicos, consulte o [recursos XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md).</span><span class="sxs-lookup"><span data-stu-id="f1370-107">For more information about dynamic resources, see the [XAML Resources](../../../../docs/framework/wpf/advanced/xaml-resources.md).</span></span>  
  
-   <span data-ttu-id="f1370-108">Ele contém <xref:System.Windows.Freezable> subobjetos não podem ser congelados.</span><span class="sxs-lookup"><span data-stu-id="f1370-108">It contains <xref:System.Windows.Freezable> sub-objects that cannot be frozen.</span></span>  
  
 <span data-ttu-id="f1370-109">Se essas condições forem `false` para sua <xref:System.Windows.Freezable> objeto e você não pretende modificá-lo, considere congelamento para obter benefícios de desempenho.</span><span class="sxs-lookup"><span data-stu-id="f1370-109">If these conditions are `false` for your <xref:System.Windows.Freezable> object and you do not intend to modify it, consider freezing it to gain performance benefits.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f1370-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f1370-110">Example</span></span>  
 <span data-ttu-id="f1370-111">O exemplo a seguir congela um <xref:System.Windows.Media.SolidColorBrush>, que é um tipo de <xref:System.Windows.Freezable> objeto.</span><span class="sxs-lookup"><span data-stu-id="f1370-111">The following example freezes a <xref:System.Windows.Media.SolidColorBrush>, which is a type of <xref:System.Windows.Freezable> object.</span></span>  
  
 [!code-csharp[freezablesample_procedural#FreezeExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#freezeexample1)]
 [!code-vb[freezablesample_procedural#FreezeExample1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#freezeexample1)]  
  
 <span data-ttu-id="f1370-112">Para obter mais informações sobre <xref:System.Windows.Freezable> objetos, consulte o [visão geral de objetos Freezable](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).</span><span class="sxs-lookup"><span data-stu-id="f1370-112">For more information about <xref:System.Windows.Freezable> objects, see the [Freezable Objects Overview](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1370-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f1370-113">See Also</span></span>  
 <xref:System.Windows.Freezable>  
 <xref:System.Windows.Freezable.CanFreeze%2A>  
 <xref:System.Windows.Freezable.Freeze%2A>  
 [<span data-ttu-id="f1370-114">Visão geral de objetos congeláveis</span><span class="sxs-lookup"><span data-stu-id="f1370-114">Freezable Objects Overview</span></span>](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)  
 [<span data-ttu-id="f1370-115">Tópicos de instruções</span><span class="sxs-lookup"><span data-stu-id="f1370-115">How-to Topics</span></span>](../../../../docs/framework/wpf/advanced/base-elements-how-to-topics.md)
