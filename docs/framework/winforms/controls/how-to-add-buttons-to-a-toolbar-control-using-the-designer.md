---
title: "Como adicionar botões a um controle ToolBar usando o designer"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- toolbars [Windows Forms], adding buttons
- ToolBar control [Windows Forms], adding buttons
- ToolBar control [Windows Forms], adding separators
- examples [Windows Forms], toolbars
- ToolBar control [Windows Forms], adding drop-down menus
ms.assetid: d9ce3040-3e21-4e2d-80ae-b430982b2db8
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5339d946f771b7ba187813dd67860aaa63a21eb3
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-add-buttons-to-a-toolbar-control-using-the-designer"></a>Como adicionar botões a um controle ToolBar usando o designer
> [!NOTE]
>  O controle <xref:System.Windows.Forms.ToolStrip> substitui e adiciona funcionalidade ao controle <xref:System.Windows.Forms.ToolBar>, no entanto, o controle <xref:System.Windows.Forms.ToolBar> é mantido para compatibilidade com versões anteriores e para uso futuro, se desejado.  
  
 Parte integrante do <xref:System.Windows.Forms.ToolBar> controle é os botões que você adicionar a ele. Eles podem ser usados para fornecer acesso fácil aos comandos de menu ou, como alternativa, podem ser colocados em outra área da interface do usuário do seu aplicativo para expor comandos para os usuários que não estão disponíveis na estrutura do menu.  
  
 O procedimento a seguir requer um **aplicativo do Windows** projeto com um formulário que contém um <xref:System.Windows.Forms.ToolBar> controle. Para obter informações sobre como configurar um projeto desse tipo, consulte [Como criar um projeto de aplicativos do Windows](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) e [Como adicionar controles ao Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-add-buttons-at-design-time"></a>Adicionar botões no tempo de design  
  
1.  Selecione o <xref:System.Windows.Forms.ToolBar> controle.  
  
2.  No **propriedades** janela, clique no <xref:System.Windows.Forms.ToolBar.Buttons%2A> propriedade para selecioná-la e clique no **reticências** (![de tela de VisualStudioEllipsesButton] (../../../../docs/framework/winforms/media/vbellipsesbutton.png " vbEllipsesButton")) para abrir o **Editor de coleção de ToolBarButton**.  
  
3.  Use o **adicionar** e **remover** botões para adicionar e remover botões do <xref:System.Windows.Forms.ToolBar> controle.  
  
4.  Configure as propriedades dos botões individuais na janela **Propriedades** que aparece no painel à direita do editor. A tabela a seguir mostra algumas propriedades importantes a considerar.  
  
    |Propriedade|Descrição|  
    |--------------|-----------------|  
    |<xref:System.Windows.Forms.ToolBarButton.DropDownMenu%2A>|Define o menu a ser exibido no botão de barra de ferramentas da lista suspensa. O botão de barra de ferramentas <xref:System.Windows.Forms.ToolBarButton.Style%2A> propriedade deve ser definida como <xref:System.Windows.Forms.ToolBarButtonStyle.DropDownButton>. Essa propriedade tem uma instância do <xref:System.Windows.Forms.ContextMenu> classe como uma referência.|  
    |<xref:System.Windows.Forms.ToolBarButton.PartialPush%2A>|Define se um botão de alternância de barra de ferramentas é parcialmente pressionado. O botão de barra de ferramentas <xref:System.Windows.Forms.ToolBarButton.Style%2A> propriedade deve ser definida como <xref:System.Windows.Forms.ToolBarButtonStyle.ToggleButton>.|  
    |<xref:System.Windows.Forms.ToolBarButton.Pushed%2A>|Define se um botão de alternância da barra de ferramentas está no estado pressionado. O botão de barra de ferramentas <xref:System.Windows.Forms.ToolBarButton.Style%2A> propriedade deve ser definida como <xref:System.Windows.Forms.ToolBarButtonStyle.ToggleButton> ou <xref:System.Windows.Forms.ToolBarButtonStyle.PushButton>.|  
    |<xref:System.Windows.Forms.ToolBarButton.Style%2A>|Define o estilo do botão de barra de ferramentas. Deve ser um dos valores a <xref:System.Windows.Forms.ToolBarButtonStyle> enumeração.|  
    |<xref:System.Windows.Forms.ToolBarButton.Text%2A>|A cadeia de caracteres de texto exibida pelo botão.|  
    |<xref:System.Windows.Forms.ToolBarButton.ToolTipText%2A>|O texto que aparece como uma ToolTip para o botão.|  
  
5.  Clique em **OK** para fechar a caixa de diálogo e criar os painéis que você especificou.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.ToolBar>  
 [Como definir um ícone para um botão de barra de ferramentas](../../../../docs/framework/winforms/controls/how-to-define-an-icon-for-a-toolbar-button.md)  
 [Como disparar eventos de menu para botões da barra de ferramentas](../../../../docs/framework/winforms/controls/how-to-trigger-menu-events-for-toolbar-buttons.md)  
 [Visão geral do controle de barra de ferramentas](../../../../docs/framework/winforms/controls/toolbar-control-overview-windows-forms.md)  
 [Controle de barra de ferramentas](../../../../docs/framework/winforms/controls/toolbar-control-windows-forms.md)
