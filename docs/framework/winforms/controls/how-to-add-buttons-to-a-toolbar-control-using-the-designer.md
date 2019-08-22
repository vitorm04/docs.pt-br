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
ms.openlocfilehash: 4d7a49633599aabc96153e4793e50c1a4d6d092d
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666217"
---
# <a name="how-to-add-buttons-to-a-toolbar-control-using-the-designer"></a>Como: Adicionar botões a um controle ToolBar usando o designer

> [!NOTE]
> O controle <xref:System.Windows.Forms.ToolStrip> substitui e adiciona funcionalidade ao controle <xref:System.Windows.Forms.ToolBar>, no entanto, o controle <xref:System.Windows.Forms.ToolBar> é mantido para compatibilidade com versões anteriores e para uso futuro, se desejado.

Uma parte integral do <xref:System.Windows.Forms.ToolBar> controle são os botões que você adiciona a ele. Eles podem ser usados para fornecer acesso fácil aos comandos de menu ou, como alternativa, podem ser colocados em outra área da interface do usuário do seu aplicativo para expor comandos para os usuários que não estão disponíveis na estrutura do menu.

O procedimento a seguir requer um projeto de **aplicativo do Windows** com um <xref:System.Windows.Forms.ToolBar> formulário que contém um controle. Para obter informações sobre como configurar esse projeto, consulte [como: Crie um projeto](/visualstudio/ide/step-1-create-a-windows-forms-application-project) de aplicativo Windows Forms [e como: Adicione controles a Windows Forms](how-to-add-controls-to-windows-forms.md).

### <a name="to-add-buttons-at-design-time"></a>Adicionar botões no tempo de design

1. Selecione o controle <xref:System.Windows.Forms.ToolBar>.

2. Na janela **Propriedades** , clique na <xref:System.Windows.Forms.ToolBar.Buttons%2A> propriedade para selecioná-la e clique nas **reticências** (![o botão de reticências (...) no botão janela Propriedades do Visual Studio.](./media/visual-studio-ellipsis-button.png)) para abrir o **ToolBarButton Editor de coleção**.

3. Use os botões **Adicionar** e **remover** para adicionar e remover <xref:System.Windows.Forms.ToolBar> botões do controle.

4. Configure as propriedades dos botões individuais na janela **Propriedades** que aparece no painel à direita do editor. A tabela a seguir mostra algumas propriedades importantes a considerar.

    |Propriedade|Descrição|
    |--------------|-----------------|
    |<xref:System.Windows.Forms.ToolBarButton.DropDownMenu%2A>|Define o menu a ser exibido no botão de barra de ferramentas da lista suspensa. A propriedade do <xref:System.Windows.Forms.ToolBarButton.Style%2A> botão da barra de ferramentas deve <xref:System.Windows.Forms.ToolBarButtonStyle.DropDownButton>ser definida como. Essa propriedade usa uma instância da <xref:System.Windows.Forms.ContextMenu> classe como uma referência.|
    |<xref:System.Windows.Forms.ToolBarButton.PartialPush%2A>|Define se um botão de alternância de barra de ferramentas é parcialmente pressionado. A propriedade do <xref:System.Windows.Forms.ToolBarButton.Style%2A> botão da barra de ferramentas deve <xref:System.Windows.Forms.ToolBarButtonStyle.ToggleButton>ser definida como.|
    |<xref:System.Windows.Forms.ToolBarButton.Pushed%2A>|Define se um botão de alternância da barra de ferramentas está no estado pressionado. A propriedade do <xref:System.Windows.Forms.ToolBarButton.Style%2A> botão da barra de ferramentas deve ser <xref:System.Windows.Forms.ToolBarButtonStyle.PushButton>definida como <xref:System.Windows.Forms.ToolBarButtonStyle.ToggleButton> ou.|
    |<xref:System.Windows.Forms.ToolBarButton.Style%2A>|Define o estilo do botão de barra de ferramentas. Deve ser um dos valores na <xref:System.Windows.Forms.ToolBarButtonStyle> enumeração.|
    |<xref:System.Windows.Forms.ToolBarButton.Text%2A>|A cadeia de caracteres de texto exibida pelo botão.|
    |<xref:System.Windows.Forms.ToolBarButton.ToolTipText%2A>|O texto que aparece como uma ToolTip para o botão.|

5. Clique em **OK** para fechar a caixa de diálogo e criar os painéis que você especificou.

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.ToolBar>
- [Como: Definir um ícone para um botão da barra de ferramentas](how-to-define-an-icon-for-a-toolbar-button.md)
- [Como: Eventos do menu disparar para botões da barra de ferramentas](how-to-trigger-menu-events-for-toolbar-buttons.md)
- [Visão geral do controle de barra de ferramentas](toolbar-control-overview-windows-forms.md)
- [Controle de barra de ferramentas](toolbar-control-windows-forms.md)
