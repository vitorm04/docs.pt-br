---
title: 'Como: Alterar o FlowDirection de conteúdo de forma programática'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- FlowDirection property [WPF], changing programmatically
- documents [WPF], changing FlowDirection property programmatically
ms.assetid: 02f5a8ba-f8c0-4e5a-84b9-4c5bf12922a2
ms.openlocfilehash: ec159ed0efce8b5514788331e8715a55e7a8a638
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57359322"
---
# <a name="how-to-change-the-flowdirection-of-content-programmatically"></a>Como: Alterar o FlowDirection de conteúdo de forma programática
Este exemplo mostra como alterar programaticamente o <xref:System.Windows.FrameworkElement.FlowDirection%2A> propriedade de um <xref:System.Windows.Controls.FlowDocumentReader>.  
  
## <a name="example"></a>Exemplo  
 Duas <xref:System.Windows.Controls.Button> elementos são criados, cada um representando um dos possíveis valores da <xref:System.Windows.FlowDirection>. Quando um botão é clicado, o valor da propriedade associada é aplicado ao conteúdo de um <xref:System.Windows.Controls.FlowDocumentReader> chamado `tf1`.  O valor da propriedade também é escrito para uma <xref:System.Windows.Controls.TextBlock> chamado `txt1`.  
  
 [!code-xaml[FlowDirectionSnippets#_FlowDirectionXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDirectionSnippets/CSharp/Window1.xaml#_flowdirectionxaml)]  
  
## <a name="example"></a>Exemplo  
 Os eventos associados com os cliques de botão definidos acima são tratados em um C# arquivo code-behind.  
  
 [!code-csharp[FlowDirectionSnippets#_FlowDirection](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDirectionSnippets/CSharp/Window1.xaml.cs#_flowdirection)]
 [!code-vb[FlowDirectionSnippets#_FlowDirection](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDirectionSnippets/VisualBasic/Window1.xaml.vb#_flowdirection)]
