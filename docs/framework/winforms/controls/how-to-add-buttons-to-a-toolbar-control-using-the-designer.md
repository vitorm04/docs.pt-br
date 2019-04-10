---
title: 'Como: Adicionar botões a um controle ToolBar usando o designer'
ms.date: 03/30/2017
helpviewer_keywords:
- toolbars [Windows Forms], adding buttons
- ToolBar control [Windows Forms], adding buttons
- ToolBar control [Windows Forms], adding separators
- examples [Windows Forms], toolbars
- ToolBar control [Windows Forms], adding drop-down menus
ms.assetid: d9ce3040-3e21-4e2d-80ae-b430982b2db8
ms.openlocfilehash: 509aa0b03dbbb370384fb83e0d8e5471fc2cb819
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59306179"
---
# <a name="how-to-add-buttons-to-a-toolbar-control-using-the-designer"></a>Como: Adicionar botões a um controle ToolBar usando o designer
> [!NOTE]
>  O controle <xref:System.Windows.Forms.ToolStrip> substitui e adiciona funcionalidade ao controle <xref:System.Windows.Forms.ToolBar>, no entanto, o controle <xref:System.Windows.Forms.ToolBar> é mantido para compatibilidade com versões anteriores e para uso futuro, se desejado.  
  
 Parte integrante do <xref:System.Windows.Forms.ToolBar> controle é os botões que você adicionar a ele. Eles podem ser usados para fornecer acesso fácil aos comandos de menu ou, como alternativa, podem ser colocados em outra área da interface do usuário do seu aplicativo para expor comandos para os usuários que não estão disponíveis na estrutura do menu.  
  
 O procedimento a seguir exige um **aplicativo do Windows** projeto com um formulário que contém um <xref:System.Windows.Forms.ToolBar> controle. Para obter informações sobre como configurar um projeto desse tipo, consulte [como: Criar um projeto de aplicativo do Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) e [como: Adicionar controles ao Windows Forms](how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-add-buttons-at-design-time"></a>Adicionar botões no tempo de design  
  
1. Selecione o <xref:System.Windows.Forms.ToolBar> controle.  
  
2. No **propriedades** janela, clique no <xref:System.Windows.Forms.ToolBar.Buttons%2A> propriedade para selecioná-lo e clique no **reticências** (![captura de tela de VisualStudioEllipsesButton](../media/vbellipsesbutton.png " vbEllipsesButton")) para abrir o **Editor de coleção ToolBarButton**.  
  
3. Use o **Add** e **remover** botões Adicionar e remover botões do <xref:System.Windows.Forms.ToolBar> controle.  
  
4. Configure as propriedades dos botões individuais na janela **Propriedades** que aparece no painel à direita do editor. A tabela a seguir mostra algumas propriedades importantes a considerar.  
  
    |Propriedade|Descrição|  
    |--------------|-----------------|  
    |<xref:System.Windows.Forms.ToolBarButton.DropDownMenu%2A>|Define o menu a ser exibido no botão de barra de ferramentas da lista suspensa. O botão de barra de ferramentas <xref:System.Windows.Forms.ToolBarButton.Style%2A> propriedade deve ser definida como <xref:System.Windows.Forms.ToolBarButtonStyle.DropDownButton>. Esta propriedade usa uma instância do <xref:System.Windows.Forms.ContextMenu> classe como uma referência.|  
    |<xref:System.Windows.Forms.ToolBarButton.PartialPush%2A>|Define se um botão de alternância de barra de ferramentas é parcialmente pressionado. O botão de barra de ferramentas <xref:System.Windows.Forms.ToolBarButton.Style%2A> propriedade deve ser definida como <xref:System.Windows.Forms.ToolBarButtonStyle.ToggleButton>.|  
    |<xref:System.Windows.Forms.ToolBarButton.Pushed%2A>|Define se um botão de alternância da barra de ferramentas está no estado pressionado. O botão de barra de ferramentas <xref:System.Windows.Forms.ToolBarButton.Style%2A> propriedade deve ser definida como <xref:System.Windows.Forms.ToolBarButtonStyle.ToggleButton> ou <xref:System.Windows.Forms.ToolBarButtonStyle.PushButton>.|  
    |<xref:System.Windows.Forms.ToolBarButton.Style%2A>|Define o estilo do botão de barra de ferramentas. Deve ser um dos valores a <xref:System.Windows.Forms.ToolBarButtonStyle> enumeração.|  
    |<xref:System.Windows.Forms.ToolBarButton.Text%2A>|A cadeia de caracteres de texto exibida pelo botão.|  
    |<xref:System.Windows.Forms.ToolBarButton.ToolTipText%2A>|O texto que aparece como uma ToolTip para o botão.|  
  
5. Clique em **OK** para fechar a caixa de diálogo e criar os painéis que você especificou.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.ToolBar>
- [Como: Definir um ícone para um botão de barra de ferramentas](how-to-define-an-icon-for-a-toolbar-button.md)
- [Como: Disparar eventos de menu para botões da barra de ferramentas](how-to-trigger-menu-events-for-toolbar-buttons.md)
- [Visão geral do controle ToolBar](toolbar-control-overview-windows-forms.md)
- [Controle ToolBar](toolbar-control-windows-forms.md)
