---
title: Como posicionar os elementos filhos de uma grade
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Grid control [WPF], positioning child elements
ms.assetid: 27b3ba9b-ad32-44e2-bcab-a79d573a463c
ms.openlocfilehash: 44268c32732a9409ea30f028adaa8a2631a06c5c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186713"
---
# <a name="how-to-position-the-child-elements-of-a-grid"></a><span data-ttu-id="e9c1a-102">Como posicionar os elementos filhos de uma grade</span><span class="sxs-lookup"><span data-stu-id="e9c1a-102">How to: Position the Child Elements of a Grid</span></span>
<span data-ttu-id="e9c1a-103">Este exemplo mostra como usar os métodos get <xref:System.Windows.Controls.Grid> and set que são definidos para posicionar elementos da criança.</span><span class="sxs-lookup"><span data-stu-id="e9c1a-103">This example shows how to use the get and set methods that are defined on <xref:System.Windows.Controls.Grid> to position child elements.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e9c1a-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e9c1a-104">Example</span></span>  
 <span data-ttu-id="e9c1a-105">O exemplo a seguir <xref:System.Windows.Controls.Grid> define`grid1`um elemento pai ( ) que tem três colunas e três linhas.</span><span class="sxs-lookup"><span data-stu-id="e9c1a-105">The following example defines a parent <xref:System.Windows.Controls.Grid> element (`grid1`) that has three columns and three rows.</span></span> <span data-ttu-id="e9c1a-106">Um <xref:System.Windows.Shapes.Rectangle> elemento`rect1`filho ( ) <xref:System.Windows.Controls.Grid> é adicionado à posição da coluna zero, posição zero da linha.</span><span class="sxs-lookup"><span data-stu-id="e9c1a-106">A child <xref:System.Windows.Shapes.Rectangle> element (`rect1`) is added to the <xref:System.Windows.Controls.Grid> in column position zero, row position zero.</span></span> <span data-ttu-id="e9c1a-107"><xref:System.Windows.Controls.Button>elementos representam métodos que podem <xref:System.Windows.Shapes.Rectangle> ser chamados <xref:System.Windows.Controls.Grid>a reposicionar o elemento dentro do .</span><span class="sxs-lookup"><span data-stu-id="e9c1a-107"><xref:System.Windows.Controls.Button> elements represent methods that can be called to reposition the <xref:System.Windows.Shapes.Rectangle> element within the <xref:System.Windows.Controls.Grid>.</span></span> <span data-ttu-id="e9c1a-108">Quando um usuário clica em um botão, o método relacionado é ativado.</span><span class="sxs-lookup"><span data-stu-id="e9c1a-108">When a user clicks a button, the related method is activated.</span></span>  
  
 [!code-xaml[gridGetSetMethods](~/samples/snippets/csharp/VS_Snippets_Wpf/gridGetSetMethods/CSharp/Window1.xaml)]  
  
 <span data-ttu-id="e9c1a-109">O exemplo de código por trás a <xref:System.Windows.Controls.Primitives.ButtonBase.Click> seguir lida com os métodos que os eventos do botão aumentam.</span><span class="sxs-lookup"><span data-stu-id="e9c1a-109">The following code-behind example handles the methods that the button <xref:System.Windows.Controls.Primitives.ButtonBase.Click> events raise.</span></span> <span data-ttu-id="e9c1a-110">O exemplo escreve essas <xref:System.Windows.Controls.TextBlock> chamadas de método para elementos que usam métodos de obter relacionados para produzir os novos valores de propriedade como strings.</span><span class="sxs-lookup"><span data-stu-id="e9c1a-110">The example writes these method calls to <xref:System.Windows.Controls.TextBlock> elements that use related get methods to output the new property values as strings.</span></span>  
  
 [!code-csharp[gridGetSetMethods#2](~/samples/snippets/csharp/VS_Snippets_Wpf/gridGetSetMethods/CSharp/Window1.xaml.cs#2)]
 [!code-vb[gridGetSetMethods#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/gridGetSetMethods/VisualBasic/Window1.xaml.vb#2)]  
 <span data-ttu-id="e9c1a-111">Aqui está o resultado final!</span><span class="sxs-lookup"><span data-stu-id="e9c1a-111">Here is the finished result!</span></span>

 ![uma captura de tela mostra uma interface de usuário WPF com duas colunas, o lado direito tem uma grade 3 x 3 e a esquerda tem botões para mover um retângulo colorido entre as colunas e linhas da grade](././media/grid-methods-sample.png)
  
## <a name="see-also"></a><span data-ttu-id="e9c1a-113">Confira também</span><span class="sxs-lookup"><span data-stu-id="e9c1a-113">See also</span></span>

- <xref:System.Windows.Controls.Grid>
- [<span data-ttu-id="e9c1a-114">Visão geral de painéis</span><span class="sxs-lookup"><span data-stu-id="e9c1a-114">Panels Overview</span></span>](panels-overview.md)
