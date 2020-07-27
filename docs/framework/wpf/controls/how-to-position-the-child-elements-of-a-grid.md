---
title: Como posicionar os elementos filhos de uma grade
description: Saiba como usar os métodos get e set que são definidos em uma grade de Windows Presentation Foundation para posicionar elementos filho.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Grid control [WPF], positioning child elements
ms.assetid: 27b3ba9b-ad32-44e2-bcab-a79d573a463c
ms.openlocfilehash: 926d223097dd21dd0292c9523903b4be8aba8ba9
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87167392"
---
# <a name="how-to-position-the-child-elements-of-a-grid"></a><span data-ttu-id="53e96-103">Como posicionar os elementos filhos de uma grade</span><span class="sxs-lookup"><span data-stu-id="53e96-103">How to: Position the Child Elements of a Grid</span></span>
<span data-ttu-id="53e96-104">Este exemplo mostra como usar os métodos get e set que são definidos no <xref:System.Windows.Controls.Grid> para posicionar elementos filho.</span><span class="sxs-lookup"><span data-stu-id="53e96-104">This example shows how to use the get and set methods that are defined on <xref:System.Windows.Controls.Grid> to position child elements.</span></span>  
  
## <a name="example"></a><span data-ttu-id="53e96-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="53e96-105">Example</span></span>  
 <span data-ttu-id="53e96-106">O exemplo a seguir define um <xref:System.Windows.Controls.Grid> elemento pai ( `grid1` ) que tem três colunas e três linhas.</span><span class="sxs-lookup"><span data-stu-id="53e96-106">The following example defines a parent <xref:System.Windows.Controls.Grid> element (`grid1`) that has three columns and three rows.</span></span> <span data-ttu-id="53e96-107">Um <xref:System.Windows.Shapes.Rectangle> elemento filho ( `rect1` ) é adicionado ao <xref:System.Windows.Controls.Grid> na coluna posição zero, posição de linha zero.</span><span class="sxs-lookup"><span data-stu-id="53e96-107">A child <xref:System.Windows.Shapes.Rectangle> element (`rect1`) is added to the <xref:System.Windows.Controls.Grid> in column position zero, row position zero.</span></span> <span data-ttu-id="53e96-108"><xref:System.Windows.Controls.Button>os elementos representam métodos que podem ser chamados para reposicionar o <xref:System.Windows.Shapes.Rectangle> elemento dentro do <xref:System.Windows.Controls.Grid> .</span><span class="sxs-lookup"><span data-stu-id="53e96-108"><xref:System.Windows.Controls.Button> elements represent methods that can be called to reposition the <xref:System.Windows.Shapes.Rectangle> element within the <xref:System.Windows.Controls.Grid>.</span></span> <span data-ttu-id="53e96-109">Quando um usuário clica em um botão, o método relacionado é ativado.</span><span class="sxs-lookup"><span data-stu-id="53e96-109">When a user clicks a button, the related method is activated.</span></span>  
  
 [!code-xaml[gridGetSetMethods](~/samples/snippets/csharp/VS_Snippets_Wpf/gridGetSetMethods/CSharp/Window1.xaml)]  
  
 <span data-ttu-id="53e96-110">O exemplo code-behind a seguir manipula os métodos que os <xref:System.Windows.Controls.Primitives.ButtonBase.Click> eventos de botão geram.</span><span class="sxs-lookup"><span data-stu-id="53e96-110">The following code-behind example handles the methods that the button <xref:System.Windows.Controls.Primitives.ButtonBase.Click> events raise.</span></span> <span data-ttu-id="53e96-111">O exemplo grava essas chamadas de método em <xref:System.Windows.Controls.TextBlock> elementos que usam os métodos get relacionados para gerar os novos valores de propriedade como cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="53e96-111">The example writes these method calls to <xref:System.Windows.Controls.TextBlock> elements that use related get methods to output the new property values as strings.</span></span>  
  
 [!code-csharp[gridGetSetMethods#2](~/samples/snippets/csharp/VS_Snippets_Wpf/gridGetSetMethods/CSharp/Window1.xaml.cs#2)]
 [!code-vb[gridGetSetMethods#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/gridGetSetMethods/VisualBasic/Window1.xaml.vb#2)]  
 <span data-ttu-id="53e96-112">Este é o resultado concluído!</span><span class="sxs-lookup"><span data-stu-id="53e96-112">Here is the finished result!</span></span>

 ![uma captura de tela representa uma interface do usuário do WPF com duas colunas, o lado direito tem uma grade 3 x 3 e a esquerda tem botões para mover um retângulo colorido entre as colunas e as linhas da grade](././media/grid-methods-sample.png)
  
## <a name="see-also"></a><span data-ttu-id="53e96-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="53e96-114">See also</span></span>

- <xref:System.Windows.Controls.Grid>
- [<span data-ttu-id="53e96-115">Visão geral de painéis</span><span class="sxs-lookup"><span data-stu-id="53e96-115">Panels Overview</span></span>](panels-overview.md)
