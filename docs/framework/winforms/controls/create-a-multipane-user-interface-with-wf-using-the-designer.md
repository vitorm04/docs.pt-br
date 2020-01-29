---
title: Criar uma interface do usuário multipainel usando o designer
ms.date: 03/30/2017
helpviewer_keywords:
- user interface [Windows Forms], multipane
- SplitContainer control [Windows Forms], using the designer
- multipane user interface
ms.assetid: c3f9294d-a26c-4198-9242-f237f55f7573
ms.openlocfilehash: 6b41d538f1cd1633cec51c89e27adf3c5b47f9a6
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76737281"
---
# <a name="how-to-create-a-multipane-user-interface-with-windows-forms-using-the-designer"></a>Como criar uma interface de usuário multipainel com os Windows Forms usando o designer
No procedimento a seguir, você vai criar uma interface do usuário com vários painéis semelhante à que é usada no Microsoft Outlook, com uma lista **Pasta**, um painel **Mensagens** e um painel **Visualização**. Essa organização é obtida principalmente por meio de controles de encaixe com o formulário.

 Ao encaixar um controle, você determina a qual borda do contêiner pai um controle é fixado. Portanto, se você definir a propriedade <xref:System.Windows.Forms.SplitContainer.Dock%2A> como <xref:System.Windows.Forms.DockStyle.Right>, a borda direita do controle será encaixada na borda direita de seu controle pai. Além disso, a borda encaixada do controle será redimensionada para corresponder à borda de sua caixa de controles. Para obter mais informações sobre como a propriedade de <xref:System.Windows.Forms.SplitContainer.Dock%2A> funciona, consulte [como: encaixar controles em Windows Forms](how-to-dock-controls-on-windows-forms.md).

 Este procedimento se concentra em organizar o <xref:System.Windows.Forms.SplitContainer> e os outros controles no formulário, não na adição de funcionalidade para fazer com que o aplicativo simule o Microsoft Outlook.

 Para criar essa interface do usuário, coloque todos os controles dentro de um controle de <xref:System.Windows.Forms.SplitContainer>, que contém um controle de <xref:System.Windows.Forms.TreeView> no painel esquerdo. O painel à direita do controle de <xref:System.Windows.Forms.SplitContainer> contém um segundo controle de <xref:System.Windows.Forms.SplitContainer> com um controle de <xref:System.Windows.Forms.ListView> acima de um controle de <xref:System.Windows.Forms.RichTextBox>. Esses <xref:System.Windows.Forms.SplitContainer> controles habilitam o redimensionamento independente dos outros controles no formulário. Você pode adaptar as técnicas neste procedimento para criar interfaces do usuário personalizadas.

## <a name="to-create-an-outlook-style-user-interface-at-design-time"></a>Para criar uma interface do usuário no estilo Outlook no tempo de design

1. Crie um novo projeto de aplicativo do Windows (**arquivo** > **novo** **projeto** de >  > **Visual C#**  ou **Visual Basic** > **área de trabalho clássica** > Windows Forms **aplicativo**).

2. Arraste um controle de <xref:System.Windows.Forms.SplitContainer> da **caixa de ferramentas** para o formulário. Na janela **Propriedades** , defina a propriedade <xref:System.Windows.Forms.SplitContainer.Dock%2A> como <xref:System.Windows.Forms.DockStyle.Fill>.

3. Arraste um controle de <xref:System.Windows.Forms.TreeView> da **caixa de ferramentas** para o painel esquerdo do controle de <xref:System.Windows.Forms.SplitContainer>. Na janela **Propriedades** , defina a propriedade <xref:System.Windows.Forms.SplitContainer.Dock%2A> como <xref:System.Windows.Forms.DockStyle.Left> clicando no painel esquerdo no editor de valor mostrado quando a seta para baixo é clicada.

4. Arraste outro controle de <xref:System.Windows.Forms.SplitContainer> da **caixa de ferramentas**; Coloque-o no painel à direita do controle de <xref:System.Windows.Forms.SplitContainer> que você adicionou ao formulário. Na janela **Propriedades** , defina a propriedade <xref:System.Windows.Forms.SplitContainer.Dock%2A> como <xref:System.Windows.Forms.DockStyle.Fill> e a propriedade <xref:System.Windows.Forms.SplitContainer.Orientation%2A> como <xref:System.Windows.Forms.Orientation.Horizontal>.

5. Arraste um controle de <xref:System.Windows.Forms.ListView> da **caixa de ferramentas** para o painel superior do segundo controle de <xref:System.Windows.Forms.SplitContainer> adicionado ao formulário. Defina a propriedade <xref:System.Windows.Forms.SplitContainer.Dock%2A> do controle de <xref:System.Windows.Forms.ListView> como <xref:System.Windows.Forms.DockStyle.Fill>.

6. Arraste um controle de <xref:System.Windows.Forms.RichTextBox> da **caixa de ferramentas** para o painel inferior do segundo controle de <xref:System.Windows.Forms.SplitContainer>. Defina a propriedade <xref:System.Windows.Forms.SplitContainer.Dock%2A> do controle de <xref:System.Windows.Forms.RichTextBox> como <xref:System.Windows.Forms.DockStyle.Fill>.

     Neste ponto, se você pressionar F5 para executar o aplicativo, o formulário exibirá uma interface do usuário de três partes, semelhante àquela do Microsoft Outlook.

    > [!NOTE]
    > Quando você coloca o ponteiro do mouse sobre qualquer um dos divisores dentro dos controles de <xref:System.Windows.Forms.SplitContainer>, você pode redimensionar as dimensões internas.

Neste ponto no desenvolvimento de aplicativos, você criou uma interface do usuário sofisticada. A próxima etapa é prosseguir com a programação do próprio aplicativo, talvez conectando o controle de <xref:System.Windows.Forms.TreeView> e <xref:System.Windows.Forms.ListView> controles a algum tipo de fonte de dados. Para obter mais informações sobre como conectar controles a dados, consulte [Vinculação de dados e Windows Forms](../data-binding-and-windows-forms.md).

## <a name="see-also"></a>Veja também

- <xref:System.Windows.Forms.SplitContainer>
- [Controle SplitContainer](splitcontainer-control-windows-forms.md)
