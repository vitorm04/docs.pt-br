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
# <a name="how-to-position-the-child-elements-of-a-grid"></a>Como posicionar os elementos filhos de uma grade
Este exemplo mostra como usar os métodos get <xref:System.Windows.Controls.Grid> and set que são definidos para posicionar elementos da criança.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir <xref:System.Windows.Controls.Grid> define`grid1`um elemento pai ( ) que tem três colunas e três linhas. Um <xref:System.Windows.Shapes.Rectangle> elemento`rect1`filho ( ) <xref:System.Windows.Controls.Grid> é adicionado à posição da coluna zero, posição zero da linha. <xref:System.Windows.Controls.Button>elementos representam métodos que podem <xref:System.Windows.Shapes.Rectangle> ser chamados <xref:System.Windows.Controls.Grid>a reposicionar o elemento dentro do . Quando um usuário clica em um botão, o método relacionado é ativado.  
  
 [!code-xaml[gridGetSetMethods](~/samples/snippets/csharp/VS_Snippets_Wpf/gridGetSetMethods/CSharp/Window1.xaml)]  
  
 O exemplo de código por trás a <xref:System.Windows.Controls.Primitives.ButtonBase.Click> seguir lida com os métodos que os eventos do botão aumentam. O exemplo escreve essas <xref:System.Windows.Controls.TextBlock> chamadas de método para elementos que usam métodos de obter relacionados para produzir os novos valores de propriedade como strings.  
  
 [!code-csharp[gridGetSetMethods#2](~/samples/snippets/csharp/VS_Snippets_Wpf/gridGetSetMethods/CSharp/Window1.xaml.cs#2)]
 [!code-vb[gridGetSetMethods#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/gridGetSetMethods/VisualBasic/Window1.xaml.vb#2)]  
 Aqui está o resultado final!

 ![uma captura de tela mostra uma interface de usuário WPF com duas colunas, o lado direito tem uma grade 3 x 3 e a esquerda tem botões para mover um retângulo colorido entre as colunas e linhas da grade](././media/grid-methods-sample.png)
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.Controls.Grid>
- [Visão geral de painéis](panels-overview.md)
