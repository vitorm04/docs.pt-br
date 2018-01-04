---
title: Como posicionar os elementos filhos de uma grade
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
helpviewer_keywords: Grid control [WPF], positioning child elements
ms.assetid: 27b3ba9b-ad32-44e2-bcab-a79d573a463c
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0ca385e1aee10fb10ac3e912999aec3a11d03ab4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-position-the-child-elements-of-a-grid"></a>Como posicionar os elementos filhos de uma grade
Este exemplo mostra como usar o get e métodos definidos no conjunto de <xref:System.Windows.Controls.Grid> para posicionar elementos filho.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir define um pai <xref:System.Windows.Controls.Grid> elemento (`grid1`) que tem três colunas e três linhas. Um filho <xref:System.Windows.Shapes.Rectangle> elemento (`rect1`) é adicionado para o <xref:System.Windows.Controls.Grid> na coluna de posição zero, linha zero. <xref:System.Windows.Controls.Button>elementos representam métodos que podem ser chamados para reposicionar o <xref:System.Windows.Shapes.Rectangle> elemento dentro do <xref:System.Windows.Controls.Grid>. Quando um usuário clica em um botão, o método relacionado é ativado.  
  
 [!code-xaml[gridGetSetMethods#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridGetSetMethods/CSharp/Window1.xaml#1)]  
  
 O seguinte exemplo de code-behind trata os métodos que o botão <xref:System.Windows.Controls.Primitives.ButtonBase.Click> geram eventos. O exemplo grava essas chamadas de método <xref:System.Windows.Controls.TextBlock> elementos relacionados ao uso obtém métodos para os novos valores de propriedade como cadeias de caracteres de saída.  
  
 [!code-csharp[gridGetSetMethods#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridGetSetMethods/CSharp/Window1.xaml.cs#2)]
 [!code-vb[gridGetSetMethods#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/gridGetSetMethods/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Controls.Grid>  
 [Visão geral de painéis](../../../../docs/framework/wpf/controls/panels-overview.md)
