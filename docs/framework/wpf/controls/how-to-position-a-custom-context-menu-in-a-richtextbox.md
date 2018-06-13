---
title: Como posicionar um menu contextual em um RichTextBox
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom context menus [WPF], positioning
- positioning custom context menus [WPF]
- RichTextBox control [WPF], positioning custom context menus
- context menus [WPF], positioning
ms.assetid: bf77c930-a546-4573-9a56-9af345ba189a
ms.openlocfilehash: bde28cdb87bdaef3198d1efd3059fed3d0ae0ce2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33553840"
---
# <a name="how-to-position-a-custom-context-menu-in-a-richtextbox"></a>Como posicionar um menu contextual em um RichTextBox
Este exemplo mostra como posicionar um menu de contexto para um <xref:System.Windows.Controls.RichTextBox>.  
  
 Quando você implementa um menu de contexto para um **RichTextBox**, você é responsável por lidar com o posicionamento do menu de contexto.  Por padrão, um menu de contexto é aberto no centro do **RichTextBox**.  
  
## <a name="example"></a>Exemplo  
 Para substituir o comportamento de posicionamento padrão, adicione um ouvinte para o <xref:System.Windows.FrameworkContentElement.ContextMenuOpening> evento.  O exemplo a seguir mostra como fazer isso programaticamente.  
  
 [!code-csharp[RichTextBox_ContextMenu#_AddListener](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBox_ContextMenu/CSharp/app.xaml.cs#_addlistener)]
 [!code-vb[RichTextBox_ContextMenu#_AddListener](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBox_ContextMenu/VisualBasic/app.xaml.vb#_addlistener)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra uma implementação correspondente <xref:System.Windows.FrameworkContentElement.ContextMenuOpening> ouvinte de evento.  
  
 [!code-csharp[RichTextBox_ContextMenu#_ListenerBody](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBox_ContextMenu/CSharp/app.xaml.cs#_listenerbody)]
 [!code-vb[RichTextBox_ContextMenu#_ListenerBody](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBox_ContextMenu/VisualBasic/app.xaml.vb#_listenerbody)]  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral de RichTextBox](../../../../docs/framework/wpf/controls/richtextbox-overview.md)  
 [Visão geral de TextBox](../../../../docs/framework/wpf/controls/textbox-overview.md)
