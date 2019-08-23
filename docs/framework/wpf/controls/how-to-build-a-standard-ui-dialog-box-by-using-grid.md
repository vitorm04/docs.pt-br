---
title: 'Como: Criar uma caixa de diálogo de interface do usuário padrão usando grade'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dialog boxes [WPF], creating
- Grid control [WPF], creating [WPF], dialog box
ms.assetid: d6ac3d51-844b-4d29-96d8-81a696a7b960
ms.openlocfilehash: 68c9653e616388374aad2ad33ac7dab68446241d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923413"
---
# <a name="how-to-build-a-standard-ui-dialog-box-by-using-grid"></a>Como: Criar uma caixa de diálogo de interface do usuário padrão usando grade
Este exemplo mostra como criar uma caixa de [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] diálogo padrão usando o <xref:System.Windows.Controls.Grid> elemento.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir cria uma caixa de diálogo como a caixa de diálogo **executar** no sistema operacional Windows.  
  
 O exemplo cria um <xref:System.Windows.Controls.Grid> e usa as <xref:System.Windows.Controls.ColumnDefinition> classes <xref:System.Windows.Controls.RowDefinition> e para definir cinco colunas e quatro linhas.  
  
 Em seguida, o exemplo adiciona e <xref:System.Windows.Controls.Image>posiciona `RunIcon.png`um,, para representar a imagem que é encontrada na caixa de diálogo. A imagem é colocada na primeira coluna e linha do <xref:System.Windows.Controls.Grid> (canto superior esquerdo).  
  
 Em seguida, o exemplo adiciona <xref:System.Windows.Controls.TextBlock> um elemento à primeira coluna, que abrange as colunas restantes da primeira linha. Ele adiciona outro <xref:System.Windows.Controls.TextBlock> elemento à segunda linha na primeira coluna, para representar a caixa de texto **aberta** . A <xref:System.Windows.Controls.TextBlock> seguir, que representa a área de entrada de dados.  
  
 Por fim, o exemplo adiciona <xref:System.Windows.Controls.Button> três elementos à linha final, que representam os eventos **OK**, **Cancelar**e **procurar** .  
  
 [!code-csharp[GridRunDialog#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GridRunDialog/CSharp/window1.xaml.cs#1)]
 [!code-vb[GridRunDialog#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GridRunDialog/VisualBasic/grid_vb.vb#1)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Controls.Grid>
- <xref:System.Windows.GridUnitType>
- [Visão geral de painéis](panels-overview.md)
- [Tópicos de instruções](grid-how-to-topics.md)
