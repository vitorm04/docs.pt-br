---
title: 'Como: Definir um ícone para um botão de barra de ferramentas usando o Designer'
ms.date: 03/30/2017
helpviewer_keywords:
- toolbars [Windows Forms], adding icons to buttons
- examples [Windows Forms], toolbars
- images [Windows Forms], toolbar buttons
- buttons [Windows Forms], images
- icons [Windows Forms], toolbar buttons
- ToolBar control [Windows Forms], adding icons to buttons
ms.assetid: d848f38e-67f2-49d4-8e88-01c845c06c02
ms.openlocfilehash: 49e93f12bebbf409e6b3a06634556b9103c85f44
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666198"
---
# <a name="how-to-define-an-icon-for-a-toolbar-button-using-the-designer"></a>Como: Definir um ícone para um botão de barra de ferramentas usando o Designer

> [!NOTE]
> O controle <xref:System.Windows.Forms.ToolStrip> substitui e adiciona funcionalidade ao controle <xref:System.Windows.Forms.ToolBar>, no entanto, o controle <xref:System.Windows.Forms.ToolBar> é mantido para compatibilidade com versões anteriores e para uso futuro, se desejado.

<xref:System.Windows.Forms.ToolBar>os botões podem exibir ícones dentro deles para facilitar a identificação pelos usuários. Isso é obtido por meio da <xref:System.Windows.Forms.ImageList> <xref:System.Windows.Forms.ToolBar> adição de imagens ao componente e sua associação ao controle.

O procedimento a seguir requer um projeto de **aplicativo do Windows** com um <xref:System.Windows.Forms.ToolBar> formulário que contém <xref:System.Windows.Forms.ImageList> um controle e um componente. Para obter informações sobre como configurar esse projeto, consulte [como: Crie um projeto](/visualstudio/ide/step-1-create-a-windows-forms-application-project) de aplicativo Windows Forms [e como: Adicione controles a Windows Forms](how-to-add-controls-to-windows-forms.md).

### <a name="to-set-an-icon-for-a-toolbar-button-at-design-time"></a>Para definir um ícone para um botão de barra de ferramentas em tempo de design

1. Adicione imagens ao <xref:System.Windows.Forms.ImageList> componente. Para obter mais informações, confira [Como: Adicione ou remova imagens ImageList com o designer](how-to-add-or-remove-imagelist-images-with-the-designer.md).

2. Selecione o <xref:System.Windows.Forms.ToolBar> controle no formulário.

3. Na janela **Propriedades** , defina a <xref:System.Windows.Forms.ToolBar> Propriedade do <xref:System.Windows.Forms.ToolBar.ImageList%2A> controle para o <xref:System.Windows.Forms.ImageList> componente.

4. Clique na <xref:System.Windows.Forms.ToolBar> Propriedade do <xref:System.Windows.Forms.ToolBar.Buttons%2A> controle para selecioná-la e clique nas reticências![(o botão de reticências (...) no botão janela Propriedades do](./media/visual-studio-ellipsis-button.png)Visual Studio.) para abrir o **Editor de coleção ToolBarButton**.

5. Use o botão **Adicionar** para adicionar botões ao <xref:System.Windows.Forms.ToolBar> controle.

6. Na janela **Propriedades** que aparece no painel no lado direito do **Editor de coleção ToolBarButton**, defina a <xref:System.Windows.Forms.ToolBarButton.ImageIndex%2A> propriedade de cada botão da barra de ferramentas como um dos valores na lista, que é desenhado a partir das imagens que você adicionou ao <xref:System.Windows.Forms.ImageList> do componente.

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.ToolBar>
- [Como: Eventos do menu disparar para botões da barra de ferramentas](how-to-trigger-menu-events-for-toolbar-buttons.md)
- [Controle de barra de ferramentas](toolbar-control-windows-forms.md)
- [Componente ImageList](imagelist-component-windows-forms.md)
