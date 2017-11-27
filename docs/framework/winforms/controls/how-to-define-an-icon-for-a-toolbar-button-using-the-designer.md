---
title: "Como definir um ícone para um botão ToolBar usando o designer"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- toolbars [Windows Forms], adding icons to buttons
- examples [Windows Forms], toolbars
- images [Windows Forms], toolbar buttons
- buttons [Windows Forms], images
- icons [Windows Forms], toolbar buttons
- ToolBar control [Windows Forms], adding icons to buttons
ms.assetid: d848f38e-67f2-49d4-8e88-01c845c06c02
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1d8bdad3aa17c964871c0d35f6e33b8098f2c649
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-define-an-icon-for-a-toolbar-button-using-the-designer"></a>Como definir um ícone para um botão ToolBar usando o designer
> [!NOTE]
>  O controle <xref:System.Windows.Forms.ToolStrip> substitui e adiciona funcionalidade ao controle <xref:System.Windows.Forms.ToolBar>, no entanto, o controle <xref:System.Windows.Forms.ToolBar> é mantido para compatibilidade com versões anteriores e para uso futuro, se desejado.  
  
 <xref:System.Windows.Forms.ToolBar>botões são capazes de exibir ícones dentro delas para facilitar a identificação pelos usuários. Isso é conseguido por meio da adição de imagens para o <xref:System.Windows.Forms.ImageList> componente e associá-lo com o <xref:System.Windows.Forms.ToolBar> controle.  
  
 O procedimento a seguir requer um **aplicativo do Windows** projeto com um formulário que contém um <xref:System.Windows.Forms.ToolBar> controle e um <xref:System.Windows.Forms.ImageList> componente. Para obter informações sobre como configurar um projeto desse tipo, consulte [Como Criar um Projeto de Aplicativo do Windows](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa) e [Como Adicionar Controles ao Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-set-an-icon-for-a-toolbar-button-at-design-time"></a>Para definir um ícone para um botão de barra de ferramentas em tempo de design  
  
1.  Adicionar imagens para o <xref:System.Windows.Forms.ImageList> componente. Para obter mais informações, consulte [Como adicionar ou remover imagens ImageList com o designer](../../../../docs/framework/winforms/controls/how-to-add-or-remove-imagelist-images-with-the-designer.md).  
  
2.  Selecione o <xref:System.Windows.Forms.ToolBar> controle do formulário.  
  
3.  No **propriedades** janela, defina o <xref:System.Windows.Forms.ToolBar> do controle <xref:System.Windows.Forms.ToolBar.ImageList%2A> propriedade para o <xref:System.Windows.Forms.ImageList> componente.  
  
4.  Clique o <xref:System.Windows.Forms.ToolBar> do controle <xref:System.Windows.Forms.ToolBar.Buttons%2A> propriedade para selecioná-lo e, em seguida, clique nas reticências (![de tela de VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) para abrir o **Editor de coleção de ToolBarButton**.  
  
5.  Use o **adicionar** botão para adicionar os botões para o <xref:System.Windows.Forms.ToolBar> controle.  
  
6.  No **propriedades** que aparece no painel no lado direito da janela de **ToolBarButton Collection Editor**, defina o <xref:System.Windows.Forms.ToolBarButton.ImageIndex%2A> propriedade de cada botão da barra de ferramentas para um dos valores na lista, que é desenhada de imagens adicionadas para o <xref:System.Windows.Forms.ImageList> componente.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.ToolBar>  
 [Como disparar eventos de menu para botões da barra de ferramentas](../../../../docs/framework/winforms/controls/how-to-trigger-menu-events-for-toolbar-buttons.md)  
 [Controle de barra de ferramentas](../../../../docs/framework/winforms/controls/toolbar-control-windows-forms.md)  
 [Componente ImageList](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md)
