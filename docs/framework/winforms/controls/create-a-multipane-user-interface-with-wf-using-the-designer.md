---
title: Como criar uma interface de usuário multipainel com os Windows Forms usando o designer
ms.date: 03/30/2017
helpviewer_keywords:
- user interface [Windows Forms], multipane
- SplitContainer control [Windows Forms], using the designer
- multipane user interface
ms.assetid: c3f9294d-a26c-4198-9242-f237f55f7573
ms.openlocfilehash: 9c8cab952fd9d0c58380a308dd360dcedb2ea8f1
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47071261"
---
# <a name="how-to-create-a-multipane-user-interface-with-windows-forms-using-the-designer"></a>Como criar uma interface de usuário multipainel com os Windows Forms usando o designer
No procedimento a seguir, você vai criar uma interface do usuário com vários painéis semelhante à que é usada no Microsoft Outlook, com uma lista **Pasta**, um painel **Mensagens** e um painel **Visualização**. Essa organização é obtida principalmente por meio de controles de encaixe com o formulário.  
  
 Ao encaixar um controle, você determina a qual borda do contêiner pai um controle é fixado. Portanto, se você definir a <xref:System.Windows.Forms.SplitContainer.Dock%2A> propriedade para <xref:System.Windows.Forms.DockStyle.Right>, a borda direita do controle será encaixada na borda direita do controle pai. Além disso, a borda encaixada do controle será redimensionada para corresponder à borda de sua caixa de controles. Para obter mais informações sobre como o <xref:System.Windows.Forms.SplitContainer.Dock%2A> propriedade funciona, consulte [como: encaixar controles nos Windows Forms](../../../../docs/framework/winforms/controls/how-to-dock-controls-on-windows-forms.md).  
  
 Este procedimento se concentra em Organizando o <xref:System.Windows.Forms.SplitContainer> e os outros controles no formulário, não na adição de funcionalidade para fazer com que o aplicativo simular o Microsoft Outlook.  
  
 Para criar essa interface do usuário, você coloca todos os controles dentro de um <xref:System.Windows.Forms.SplitContainer> controle, que contém um <xref:System.Windows.Forms.TreeView> controle no painel esquerdo. O painel à direita do <xref:System.Windows.Forms.SplitContainer> controle contiver um segundo <xref:System.Windows.Forms.SplitContainer> controlar com um <xref:System.Windows.Forms.ListView> controle acima uma <xref:System.Windows.Forms.RichTextBox> controle. Eles <xref:System.Windows.Forms.SplitContainer> controles permitem que um redimensionamento independente dos outros controles no formulário. Você pode adaptar as técnicas neste procedimento para criar interfaces do usuário personalizadas.  
  
> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-create-an-outlook-style-user-interface-at-design-time"></a>Para criar uma interface do usuário no estilo Outlook no tempo de design  
  
1.  Criar um novo projeto de aplicativo do Windows (**arquivo** > **New** > **projeto** > **Visual C#** ou **Visual Basic** > **área de trabalho clássica** > **aplicativo de formulários do Windows**).  
  
2.  Arraste uma <xref:System.Windows.Forms.SplitContainer> controlar do **caixa de ferramentas** ao formulário. No **propriedades** janela, defina as <xref:System.Windows.Forms.SplitContainer.Dock%2A> propriedade <xref:System.Windows.Forms.DockStyle.Fill>.  
  
3.  Arraste uma <xref:System.Windows.Forms.TreeView> controlar do **caixa de ferramentas** para o painel esquerdo do <xref:System.Windows.Forms.SplitContainer> controle. No **propriedades** janela, defina o <xref:System.Windows.Forms.SplitContainer.Dock%2A> propriedade <xref:System.Windows.Forms.DockStyle.Left> clicando no painel esquerdo no editor de valor mostrado quando a seta para baixo é clicada.  
  
4.  Arraste outro <xref:System.Windows.Forms.SplitContainer> controlar do **caixa de ferramentas**; coloque-o no painel direito do <xref:System.Windows.Forms.SplitContainer> controle adicionado ao seu formulário. No **propriedades** janela, defina o <xref:System.Windows.Forms.SplitContainer.Dock%2A> propriedade a ser <xref:System.Windows.Forms.DockStyle.Fill> e o <xref:System.Windows.Forms.SplitContainer.Orientation%2A> propriedade <xref:System.Windows.Forms.Orientation.Horizontal>.  
  
5.  Arraste uma <xref:System.Windows.Forms.ListView> controlar do **caixa de ferramentas** para o painel superior do segundo <xref:System.Windows.Forms.SplitContainer> controle adicionado ao seu formulário. Defina a <xref:System.Windows.Forms.SplitContainer.Dock%2A> propriedade do <xref:System.Windows.Forms.ListView> o controle para <xref:System.Windows.Forms.DockStyle.Fill>.  
  
6.  Arraste uma <xref:System.Windows.Forms.RichTextBox> controlar do **caixa de ferramentas** para o painel inferior do segundo <xref:System.Windows.Forms.SplitContainer> controle. Defina a <xref:System.Windows.Forms.SplitContainer.Dock%2A> propriedade do <xref:System.Windows.Forms.RichTextBox> o controle para <xref:System.Windows.Forms.DockStyle.Fill>.  
  
     Neste ponto, se você pressionar F5 para executar o aplicativo, o formulário exibirá uma interface do usuário de três partes, semelhante àquela do Microsoft Outlook.  
  
    > [!NOTE]
    >  Quando você colocar o ponteiro do mouse sobre qualquer um dos divisores dentro de <xref:System.Windows.Forms.SplitContainer> controles, você pode redimensionar as dimensões internas.  
  
     Neste ponto no desenvolvimento de aplicativos, você criou uma interface do usuário sofisticada. A próxima etapa é prosseguir com a programação do aplicativo em si, talvez conectando-se a <xref:System.Windows.Forms.TreeView> controle e <xref:System.Windows.Forms.ListView> controles para algum tipo de fonte de dados. Para obter mais informações sobre como conectar controles a dados, consulte [Vinculação de dados e Windows Forms](../../../../docs/framework/winforms/data-binding-and-windows-forms.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.SplitContainer>  
 [Controle SplitContainer](../../../../docs/framework/winforms/controls/splitcontainer-control-windows-forms.md)
