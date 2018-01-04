---
title: "Como compilar uma caixa de diálogo de interface do usuário padrão usando grade"
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
helpviewer_keywords:
- dialog boxes [WPF], creating
- Grid control [WPF], creating [WPF], dialog box
ms.assetid: d6ac3d51-844b-4d29-96d8-81a696a7b960
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 69dba9b76f823e1779c4555521552b4a423c844c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-build-a-standard-ui-dialog-box-by-using-grid"></a>Como compilar uma caixa de diálogo de interface do usuário padrão usando grade
Este exemplo mostra como criar um padrão [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] caixa de diálogo usando o <xref:System.Windows.Controls.Grid> elemento.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir cria uma caixa de diálogo como a caixa de diálogo **Executar** no sistema operacional [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)].  
  
 O exemplo cria um <xref:System.Windows.Controls.Grid> e usa o <xref:System.Windows.Controls.ColumnDefinition> e <xref:System.Windows.Controls.RowDefinition> classes para definir cinco colunas e quatro linhas.  
  
 O exemplo então adiciona e posiciona um <xref:System.Windows.Controls.Image>, `RunIcon.png`, para representar a imagem que é encontrada na caixa de diálogo. A imagem é colocada na primeira coluna e linha do <xref:System.Windows.Controls.Grid> (canto superior esquerdo).  
  
 Em seguida, o exemplo adiciona um <xref:System.Windows.Controls.TextBlock> elemento para a primeira coluna, que abrange as colunas restantes da primeira linha. Ele adiciona outro <xref:System.Windows.Controls.TextBlock> elemento para a segunda linha na primeira coluna, para representar o **abrir** caixa de texto. Um <xref:System.Windows.Controls.TextBlock> segue, que representa a área de entrada de dados.  
  
 Por fim, o exemplo adiciona três <xref:System.Windows.Controls.Button> elementos para a linha final, que representam o **Okey**, **Cancelar**, e **procurar** eventos.  
  
 [!code-csharp[GridRunDialog#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridRunDialog/CSharp/window1.xaml.cs#1)]
 [!code-vb[GridRunDialog#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GridRunDialog/VisualBasic/grid_vb.vb#1)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Controls.Grid>  
 <xref:System.Windows.GridUnitType>  
 [Visão geral de painéis](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [Tópicos de instruções](../../../../docs/framework/wpf/controls/grid-how-to-topics.md)
