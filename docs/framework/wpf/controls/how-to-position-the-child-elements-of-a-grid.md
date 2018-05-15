---
title: Como posicionar os elementos filhos de uma grade
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Grid control [WPF], positioning child elements
ms.assetid: 27b3ba9b-ad32-44e2-bcab-a79d573a463c
ms.openlocfilehash: 62508deee1b10b4a1287360f971b3699e57d4243
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-position-the-child-elements-of-a-grid"></a><span data-ttu-id="71836-102">Como posicionar os elementos filhos de uma grade</span><span class="sxs-lookup"><span data-stu-id="71836-102">How to: Position the Child Elements of a Grid</span></span>
<span data-ttu-id="71836-103">Este exemplo mostra como usar o get e métodos definidos no conjunto de <xref:System.Windows.Controls.Grid> para posicionar elementos filho.</span><span class="sxs-lookup"><span data-stu-id="71836-103">This example shows how to use the get and set methods that are defined on <xref:System.Windows.Controls.Grid> to position child elements.</span></span>  
  
## <a name="example"></a><span data-ttu-id="71836-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="71836-104">Example</span></span>  
 <span data-ttu-id="71836-105">O exemplo a seguir define um pai <xref:System.Windows.Controls.Grid> elemento (`grid1`) que tem três colunas e três linhas.</span><span class="sxs-lookup"><span data-stu-id="71836-105">The following example defines a parent <xref:System.Windows.Controls.Grid> element (`grid1`) that has three columns and three rows.</span></span> <span data-ttu-id="71836-106">Um filho <xref:System.Windows.Shapes.Rectangle> elemento (`rect1`) é adicionado para o <xref:System.Windows.Controls.Grid> na coluna de posição zero, linha zero.</span><span class="sxs-lookup"><span data-stu-id="71836-106">A child <xref:System.Windows.Shapes.Rectangle> element (`rect1`) is added to the <xref:System.Windows.Controls.Grid> in column position zero, row position zero.</span></span> <span data-ttu-id="71836-107"><xref:System.Windows.Controls.Button> elementos representam métodos que podem ser chamados para reposicionar o <xref:System.Windows.Shapes.Rectangle> elemento dentro do <xref:System.Windows.Controls.Grid>.</span><span class="sxs-lookup"><span data-stu-id="71836-107"><xref:System.Windows.Controls.Button> elements represent methods that can be called to reposition the <xref:System.Windows.Shapes.Rectangle> element within the <xref:System.Windows.Controls.Grid>.</span></span> <span data-ttu-id="71836-108">Quando um usuário clica em um botão, o método relacionado é ativado.</span><span class="sxs-lookup"><span data-stu-id="71836-108">When a user clicks a button, the related method is activated.</span></span>  
  
 [!code-xaml[gridGetSetMethods#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridGetSetMethods/CSharp/Window1.xaml#1)]  
  
 <span data-ttu-id="71836-109">O seguinte exemplo de code-behind trata os métodos que o botão <xref:System.Windows.Controls.Primitives.ButtonBase.Click> geram eventos.</span><span class="sxs-lookup"><span data-stu-id="71836-109">The following code-behind example handles the methods that the button <xref:System.Windows.Controls.Primitives.ButtonBase.Click> events raise.</span></span> <span data-ttu-id="71836-110">O exemplo grava essas chamadas de método <xref:System.Windows.Controls.TextBlock> elementos relacionados ao uso obtém métodos para os novos valores de propriedade como cadeias de caracteres de saída.</span><span class="sxs-lookup"><span data-stu-id="71836-110">The example writes these method calls to <xref:System.Windows.Controls.TextBlock> elements that use related get methods to output the new property values as strings.</span></span>  
  
 [!code-csharp[gridGetSetMethods#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridGetSetMethods/CSharp/Window1.xaml.cs#2)]
 [!code-vb[gridGetSetMethods#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/gridGetSetMethods/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="71836-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="71836-111">See Also</span></span>  
 <xref:System.Windows.Controls.Grid>  
 [<span data-ttu-id="71836-112">Visão geral de painéis</span><span class="sxs-lookup"><span data-stu-id="71836-112">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)
