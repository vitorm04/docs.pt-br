---
title: Como implementar um adorno
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
helpviewer_keywords: adorners [WPF], implementing
ms.assetid: 56ae32b6-0599-455c-b52f-2ff97e6f1ec2
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a3f69fee64ea65e8d49cce523c85669993cc6bce
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-implement-an-adorner"></a><span data-ttu-id="6dfe6-102">Como implementar um adorno</span><span class="sxs-lookup"><span data-stu-id="6dfe6-102">How to: Implement an Adorner</span></span>
<span data-ttu-id="6dfe6-103">Este exemplo mostra uma implementação mínima de adorno.</span><span class="sxs-lookup"><span data-stu-id="6dfe6-103">This example shows a minimal adorner implementation.</span></span>  
  
## <a name="notes-for-implementers"></a><span data-ttu-id="6dfe6-104">Observações para implementadores</span><span class="sxs-lookup"><span data-stu-id="6dfe6-104">Notes for Implementers</span></span>  
 <span data-ttu-id="6dfe6-105">É importante observar que adornos não incluem nenhum comportamento de renderização inerente; garantir que um adorno seja renderizado é responsabilidade do implementador do adorno.</span><span class="sxs-lookup"><span data-stu-id="6dfe6-105">It is important to note that adorners do not include any inherent rendering behavior; ensuring that an adorner renders is the responsibility of the adorner implementer.</span></span>   <span data-ttu-id="6dfe6-106">Uma maneira comum de implementar o comportamento de renderização é substituir a <xref:System.Windows.UIElement.OnRender%2A> método e o uso de um ou mais <xref:System.Windows.Media.DrawingContext> objetos para renderizar os visuais do adorno conforme necessário (como mostrado neste exemplo).</span><span class="sxs-lookup"><span data-stu-id="6dfe6-106">A common way of implementing rendering behavior is to override the <xref:System.Windows.UIElement.OnRender%2A> method and use one or more <xref:System.Windows.Media.DrawingContext> objects to render the adorner's visuals as needed (as shown in this example).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6dfe6-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6dfe6-107">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="6dfe6-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="6dfe6-108">Description</span></span>  
 <span data-ttu-id="6dfe6-109">Um adorno personalizado é criado com a implementação de uma classe que herda da <xref:System.Windows.Documents.Adorner> classe.</span><span class="sxs-lookup"><span data-stu-id="6dfe6-109">A custom adorner is created by implementing a class that inherits from the abstract <xref:System.Windows.Documents.Adorner> class.</span></span>  <span data-ttu-id="6dfe6-110">O adorno de exemplo simplesmente adorna os cantos de uma <xref:System.Windows.UIElement> com círculos, substituindo o <xref:System.Windows.UIElement.OnRender%2A> método.</span><span class="sxs-lookup"><span data-stu-id="6dfe6-110">The example adorner simply adorns the corners of a <xref:System.Windows.UIElement> with circles by overriding the <xref:System.Windows.UIElement.OnRender%2A> method.</span></span>  
  
### <a name="code"></a><span data-ttu-id="6dfe6-111">Código</span><span class="sxs-lookup"><span data-stu-id="6dfe6-111">Code</span></span>  
 [!code-csharp[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_simplecircleadornerbody)]
 [!code-vb[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_simplecircleadornerbody)]  
  
## <a name="see-also"></a><span data-ttu-id="6dfe6-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6dfe6-112">See Also</span></span>  
 [<span data-ttu-id="6dfe6-113">Visão geral de adornos</span><span class="sxs-lookup"><span data-stu-id="6dfe6-113">Adorners Overview</span></span>](../../../../docs/framework/wpf/controls/adorners-overview.md)
