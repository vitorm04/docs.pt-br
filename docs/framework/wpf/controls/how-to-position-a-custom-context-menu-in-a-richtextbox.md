---
title: 'Como: Posicionar um menu de contexto personalizado em um RichTextBox'
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
ms.openlocfilehash: f9407f59c3daafd09fa5b84006f33ef2f3ebd31f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61770819"
---
# <a name="how-to-position-a-custom-context-menu-in-a-richtextbox"></a>Como: Posicionar um menu de contexto personalizado em um RichTextBox
Este exemplo mostra como posicionar um menu de contexto personalizado para um <xref:System.Windows.Controls.RichTextBox>.  
  
 Quando você implementa um menu de contexto personalizado para um **RichTextBox**, você é responsável por lidar com o posicionamento do menu de contexto.  Por padrão, um menu de contexto personalizado é aberto no centro do **RichTextBox**.  
  
## <a name="example"></a>Exemplo  
 Para substituir o comportamento de posicionamento padrão, adicione um ouvinte para o <xref:System.Windows.FrameworkContentElement.ContextMenuOpening> eventos.  O exemplo a seguir mostra como fazer isso programaticamente.  
  
 [!code-csharp[RichTextBox_ContextMenu#_AddListener](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBox_ContextMenu/CSharp/app.xaml.cs#_addlistener)]
 [!code-vb[RichTextBox_ContextMenu#_AddListener](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBox_ContextMenu/VisualBasic/app.xaml.vb#_addlistener)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra uma implementação correspondente <xref:System.Windows.FrameworkContentElement.ContextMenuOpening> ouvinte de eventos.  
  
 [!code-csharp[RichTextBox_ContextMenu#_ListenerBody](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBox_ContextMenu/CSharp/app.xaml.cs#_listenerbody)]
 [!code-vb[RichTextBox_ContextMenu#_ListenerBody](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBox_ContextMenu/VisualBasic/app.xaml.vb#_listenerbody)]  
  
## <a name="see-also"></a>Consulte também

- [Visão geral de RichTextBox](richtextbox-overview.md)
- [Visão geral de TextBox](textbox-overview.md)
