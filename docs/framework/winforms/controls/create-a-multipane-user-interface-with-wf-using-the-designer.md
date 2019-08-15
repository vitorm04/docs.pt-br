---
title: 'Como: Criar uma interface do usuário com vários painéis com o Windows Forms usando o designer'
ms.date: 03/30/2017
helpviewer_keywords:
- user interface [Windows Forms], multipane
- SplitContainer control [Windows Forms], using the designer
- multipane user interface
ms.assetid: c3f9294d-a26c-4198-9242-f237f55f7573
ms.openlocfilehash: f96124f7d97e733b1f0e2559320ce2e09ba5ff21
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039956"
---
# <a name="how-to-create-a-multipane-user-interface-with-windows-forms-using-the-designer"></a>Como: Criar uma interface do usuário com vários painéis com o Windows Forms usando o designer
No procedimento a seguir, você vai criar uma interface do usuário com vários painéis semelhante à que é usada no Microsoft Outlook, com uma lista **Pasta**, um painel **Mensagens** e um painel **Visualização**. Essa organização é obtida principalmente por meio de controles de encaixe com o formulário.

 Ao encaixar um controle, você determina a qual borda do contêiner pai um controle é fixado. Portanto, se você definir a <xref:System.Windows.Forms.SplitContainer.Dock%2A> Propriedade como <xref:System.Windows.Forms.DockStyle.Right>, a borda direita do controle será encaixada na borda direita de seu controle pai. Além disso, a borda encaixada do controle será redimensionada para corresponder à borda de sua caixa de controles. Para obter mais informações sobre como <xref:System.Windows.Forms.SplitContainer.Dock%2A> a propriedade funciona, [consulte Como: Encaixar controles](how-to-dock-controls-on-windows-forms.md)em Windows Forms.

 Este procedimento se concentra em organizar o <xref:System.Windows.Forms.SplitContainer> e os outros controles no formulário, não na adição de funcionalidade para fazer com que o aplicativo simule o Microsoft Outlook.

 Para criar essa interface do usuário, coloque todos os controles dentro de <xref:System.Windows.Forms.SplitContainer> um controle, que contém <xref:System.Windows.Forms.TreeView> um controle no painel esquerdo. O painel à direita <xref:System.Windows.Forms.SplitContainer> do controle contém um segundo <xref:System.Windows.Forms.SplitContainer> controle com um <xref:System.Windows.Forms.ListView> controle acima de um <xref:System.Windows.Forms.RichTextBox> controle. Esses <xref:System.Windows.Forms.SplitContainer> controles habilitam o redimensionamento independente dos outros controles no formulário. Você pode adaptar as técnicas neste procedimento para criar interfaces do usuário personalizadas.

## <a name="to-create-an-outlook-style-user-interface-at-design-time"></a>Para criar uma interface do usuário no estilo Outlook no tempo de design

1. Criar um novo projeto de aplicativo do Windows (**arquivo** > **novo** > **projeto** > **Visual C#**  ou **Visual Basic** > **área de trabalho clássica**  >  **Windows Forms aplicativo**).

2. Arraste um <xref:System.Windows.Forms.SplitContainer> controle da **caixa de ferramentas** para o formulário. Na janela **Propriedades** , defina a <xref:System.Windows.Forms.SplitContainer.Dock%2A> Propriedade como <xref:System.Windows.Forms.DockStyle.Fill>.

3. Arraste um <xref:System.Windows.Forms.TreeView> controle da **caixa de ferramentas** para o painel esquerdo do <xref:System.Windows.Forms.SplitContainer> controle. Na janela **Propriedades** , defina a <xref:System.Windows.Forms.SplitContainer.Dock%2A> Propriedade como <xref:System.Windows.Forms.DockStyle.Left> clicando no painel esquerdo no editor de valor mostrado quando a seta para baixo for clicada.

4. Arraste outro <xref:System.Windows.Forms.SplitContainer> controle da **caixa de ferramentas**; Coloque-o no painel à direita do <xref:System.Windows.Forms.SplitContainer> controle adicionado ao formulário. Na janela **Propriedades** , defina a <xref:System.Windows.Forms.SplitContainer.Dock%2A> Propriedade como <xref:System.Windows.Forms.DockStyle.Fill> e a <xref:System.Windows.Forms.SplitContainer.Orientation%2A> Propriedade como <xref:System.Windows.Forms.Orientation.Horizontal>.

5. Arraste um <xref:System.Windows.Forms.ListView> controle da **caixa de ferramentas** para o painel superior do segundo <xref:System.Windows.Forms.SplitContainer> controle adicionado ao formulário. Defina a <xref:System.Windows.Forms.SplitContainer.Dock%2A> propriedade <xref:System.Windows.Forms.ListView> do controle como <xref:System.Windows.Forms.DockStyle.Fill>.

6. Arraste um <xref:System.Windows.Forms.RichTextBox> controle da **caixa de ferramentas** para o painel inferior do segundo <xref:System.Windows.Forms.SplitContainer> controle. Defina a <xref:System.Windows.Forms.SplitContainer.Dock%2A> propriedade <xref:System.Windows.Forms.RichTextBox> do controle como <xref:System.Windows.Forms.DockStyle.Fill>.

     Neste ponto, se você pressionar F5 para executar o aplicativo, o formulário exibirá uma interface do usuário de três partes, semelhante àquela do Microsoft Outlook.

    > [!NOTE]
    >  Quando você coloca o ponteiro do mouse sobre qualquer um dos divisores <xref:System.Windows.Forms.SplitContainer> dentro dos controles, você pode redimensionar as dimensões internas.

Neste ponto no desenvolvimento de aplicativos, você criou uma interface do usuário sofisticada. A próxima etapa é prosseguir com a programação do próprio aplicativo, talvez conectando o controle e <xref:System.Windows.Forms.TreeView> <xref:System.Windows.Forms.ListView> os controles a algum tipo de fonte de dados. Para obter mais informações sobre como conectar controles a dados, consulte [Vinculação de dados e Windows Forms](../data-binding-and-windows-forms.md).

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.SplitContainer>
- [Controle SplitContainer](splitcontainer-control-windows-forms.md)
