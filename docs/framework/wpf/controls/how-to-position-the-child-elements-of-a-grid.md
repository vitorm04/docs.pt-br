---
title: 'Como: Posicionar os elementos filho de uma grade'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Grid control [WPF], positioning child elements
ms.assetid: 27b3ba9b-ad32-44e2-bcab-a79d573a463c
ms.openlocfilehash: c508f45c1ea3d0925503d6fe5600498a0558d5ad
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59202983"
---
# <a name="how-to-position-the-child-elements-of-a-grid"></a>Como: Posicionar os elementos filho de uma grade
Este exemplo mostra como usar o get e definir métodos que são definidos no <xref:System.Windows.Controls.Grid> para posicionar elementos filho.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir define um pai <xref:System.Windows.Controls.Grid> elemento (`grid1`) que tem três colunas e três linhas. Um filho <xref:System.Windows.Shapes.Rectangle> elemento (`rect1`) é adicionado para o <xref:System.Windows.Controls.Grid> na coluna de posição zero, linha zero. <xref:System.Windows.Controls.Button> elementos representam métodos que podem ser chamados para reposicionar a <xref:System.Windows.Shapes.Rectangle> elemento dentro do <xref:System.Windows.Controls.Grid>. Quando um usuário clica em um botão, o método relacionado é ativado.  
  
 [!code-xaml[gridGetSetMethods](~/samples/snippets/csharp/VS_Snippets_Wpf/gridGetSetMethods/CSharp/Window1.xaml)]  
  
 O exemplo de code-behind a seguir trata os métodos que o botão <xref:System.Windows.Controls.Primitives.ButtonBase.Click> geram eventos. O exemplo grava essas chamadas de método <xref:System.Windows.Controls.TextBlock> métodos para os novos valores de propriedade como cadeias de caracteres de saída de get de elementos relacionados ao uso.  
  
 [!code-csharp[gridGetSetMethods#2](~/samples/snippets/csharp/VS_Snippets_Wpf/gridGetSetMethods/CSharp/Window1.xaml.cs#2)]
 [!code-vb[gridGetSetMethods#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/gridGetSetMethods/VisualBasic/Window1.xaml.vb#2)]  
 Aqui está o resultado finalizado!
 
 ![uma captura de tela mostra uma interface de usuário do WPF com duas colunas, à direita tem uma grade de 3x3 e à esquerda tem botões para mover um retângulo colorido entre as colunas e linhas de grade](././media/grid-methods-sample.png) 
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Controls.Grid>
- [Visão geral de painéis](panels-overview.md)
