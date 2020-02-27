---
title: 'Instruções passo a passo: criando um formulário MDI com mesclagem de menu e controles ToolStrip'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toolbars [Windows Forms]
- ToolStripPanel control [Windows Forms]
- MDI [Windows Forms], creating forms
- multiple document interface forms
- MDI forms
- ToolStrip control [Windows Forms]
- MDI forms [Windows Forms], creating
- MDI forms [Windows Forms], walkthroughs
ms.assetid: fbab4221-74af-42d0-bbf4-3c97f7b2e544
ms.openlocfilehash: e0343b98cb71521b35418e70550a93e0bfe20fa8
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628781"
---
# <a name="walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls"></a>Instruções passo a passo: criando um formulário MDI com mesclagem de menu e controles ToolStrip

O namespace <xref:System.Windows.Forms?displayProperty=nameWithType> dá suporte a aplicativos de interface de vários documentos (MDI) e o controle de <xref:System.Windows.Forms.MenuStrip> dá suporte à mesclagem de menus. Os formulários MDI também podem <xref:System.Windows.Forms.ToolStrip> controles.

Este tutorial demonstra como usar <xref:System.Windows.Forms.ToolStripPanel> controles com um formulário MDI. O formulário também dá suporte à mesclagem com menus filho. As seguintes tarefas são ilustradas nesta instrução passo a passo:

- Criando um projeto do Windows Forms.

- Criando o menu principal do formulário. O nome real do menu variará.

- Adicionar o controle de <xref:System.Windows.Forms.ToolStripPanel> à **caixa de ferramentas**.

- Criando um formulário filho.

- Organizando os controles de <xref:System.Windows.Forms.ToolStripPanel> por ordem z.

Quando terminar, você terá um formulário MDI que dá suporte à mesclagem de menus e aos controles de <xref:System.Windows.Forms.ToolStrip> móvel.

Para copiar o código neste tópico como uma única lista, consulte [Como criar um formulário MDI com mesclagem de menu e controles ToolStrip](how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).

## <a name="prerequisites"></a>Prerequisites

Você precisará do Visual Studio para concluir este passo a passos.

## <a name="create-the-project"></a>Criar o projeto

1. No Visual Studio, crie um projeto de aplicativo do Windows chamado **MDIForm** (**File** > **New** > **Project** >  **C# Visual** ou **Visual Basic** > **Classic desktop** > **aplicativo Windows Forms**).

2. No Designer de Formulários do Windows, selecione o formulário.

3. Na janela Propriedades, defina o valor da <xref:System.Windows.Forms.Form.IsMdiContainer%2A> como `true`.

## <a name="create-the-main-menu"></a>Criar o menu principal

O formulário MDI pai contém o menu principal. O menu principal tem um item de menu chamado **Janela**. Com o item de menu **Janela**, você pode criar formulários filho. Os itens de menu de formulários filho são mesclados no menu principal.

1. Na **caixa de ferramentas**, arraste um controle de <xref:System.Windows.Forms.MenuStrip> para o formulário.

2. Adicione um <xref:System.Windows.Forms.ToolStripMenuItem> ao controle de <xref:System.Windows.Forms.MenuStrip> e nomeie-o como **janela**.

3. Selecione o controle <xref:System.Windows.Forms.MenuStrip>.

4. Na janela Propriedades, defina o valor da propriedade <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> como `ToolStripMenuItem1`.

5. Adicione um subitem no item de menu **Janela** e nomeie o subitem como **Novo**.

6. Na janela Propriedades, clique em **Eventos**.

7. Clique duas vezes no evento <xref:System.Windows.Forms.ToolStripItem.Click>.

     O Designer de Formulários do Windows gera um manipulador de eventos para o evento <xref:System.Windows.Forms.ToolStripItem.Click>.

8. Insira o seguinte código ao manipulador de eventos.

     [!code-csharp[System.Windows.Forms.ToolStrip.MdiForm#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.MdiForm#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/VB/Form1.vb#2)]

## <a name="add-the-toolstrippanel-control-to-the-toolbox"></a>Adicionar o controle ToolStripPanel à caixa de ferramentas

Quando você usa controles de <xref:System.Windows.Forms.MenuStrip> com um formulário MDI, você deve ter o controle <xref:System.Windows.Forms.ToolStripPanel>. Você deve adicionar o controle de <xref:System.Windows.Forms.ToolStripPanel> à **caixa de ferramentas** para criar seu formulário MDI no designer de formulários do Windows.

1. Abra a **caixa de ferramentas** e, em seguida, clique na guia **Todos os Windows Forms** para mostrar os controles dos Windows Forms disponíveis.

2. Clique com o botão direito do mouse para abrir o menu de atalho e selecione **Escolher Itens**.

3. Na caixa de diálogo **Escolher Itens da Caixa de Ferramentas**, role para baixo a coluna **Nome** até encontrar **ToolStripPanel**.

4. Marque a caixa de seleção por **ToolStripPanel**e, em seguida, clique em **OK**.

     O controle <xref:System.Windows.Forms.ToolStripPanel> aparece na **caixa de ferramentas**.

## <a name="create-a-child-form"></a>Criar um formulário filho

Neste procedimento, você definirá uma classe de formulário filho separada que tem seu próprio controle de <xref:System.Windows.Forms.MenuStrip>. Os itens de menu para esse formulário são mesclados com as do formulário pai.

1. Adicione um novo formulário chamado `ChildForm` ao projeto.

     Para obter mais informações, consulte [Como adicionar o Windows Forms a um projeto](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/y2xxdce3(v=vs.100)).

2. Na **caixa de ferramentas**, arraste um controle de <xref:System.Windows.Forms.MenuStrip> para o formulário filho.

3. Clique no glifo ações do designer do controle de <xref:System.Windows.Forms.MenuStrip> (![seta preta pequena](./media/designer-actions-glyph.gif)) e, em seguida, selecione **Editar itens**.

4. Na caixa de diálogo **Editor de coleção de itens** , adicione um novo <xref:System.Windows.Forms.ToolStripMenuItem> chamado **ChildMenuItem** ao menu filho.

     Para obter mais informações, consulte [Editor de Coleção dos Itens ToolStrip](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233643(v=vs.100)).

## <a name="test-the-form"></a>Testar o formulário

1. Pressione **F5** para compilar e executar o formulário.

2. Clique no item de menu **Janela** para abrir o menu e, em seguida, clique em **Novo**.

     Um novo formulário filho é criado na área de cliente do MDI do formulário. O menu do formulário filho será mesclado com o menu principal.

3. Feche o formulário filho.

     O menu do formulário filho será removido do menu principal.

4. Clique em **Novo** várias vezes.

     Os formulários filho são listados automaticamente no item de menu **janela** porque a propriedade <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> do controle de <xref:System.Windows.Forms.MenuStrip> é atribuída.

## <a name="add-toolstrip-support"></a>Adicionar suporte a ToolStrip

Neste procedimento, você adicionará quatro controles <xref:System.Windows.Forms.ToolStrip> ao formulário pai MDI. Cada controle de <xref:System.Windows.Forms.ToolStrip> é adicionado dentro de um controle de <xref:System.Windows.Forms.ToolStripPanel>, que é encaixado na borda do formulário.

1. Na **caixa de ferramentas**, arraste um controle de <xref:System.Windows.Forms.ToolStripPanel> para o formulário.

2. Com o controle de <xref:System.Windows.Forms.ToolStripPanel> selecionado, clique duas vezes no controle de <xref:System.Windows.Forms.ToolStrip> na **caixa de ferramentas**.

     Um controle de <xref:System.Windows.Forms.ToolStrip> é criado no controle de <xref:System.Windows.Forms.ToolStripPanel>.

3. Selecione o controle <xref:System.Windows.Forms.ToolStripPanel>.

4. No janela Propriedades, altere o valor da propriedade <xref:System.Windows.Forms.Control.Dock%2A> do controle para <xref:System.Windows.Forms.DockStyle.Left>.

     O controle de <xref:System.Windows.Forms.ToolStripPanel> se encaixa no lado esquerdo do formulário, abaixo do menu principal. A área do cliente MDI é redimensionada para se ajustar ao controle de <xref:System.Windows.Forms.ToolStripPanel>.

5. Repita as etapas de 1 a 4.

     Encaixe o novo controle de <xref:System.Windows.Forms.ToolStripPanel> na parte superior do formulário.

     O controle de <xref:System.Windows.Forms.ToolStripPanel> é encaixado sob o menu principal, mas à direita do primeiro controle <xref:System.Windows.Forms.ToolStripPanel>. Esta etapa ilustra a importância da ordem z no posicionamento correto de <xref:System.Windows.Forms.ToolStripPanel> controles.

6. Repita as etapas de 1 a 4 para mais dois controles de <xref:System.Windows.Forms.ToolStripPanel>.

     Encaixe os novos controles de <xref:System.Windows.Forms.ToolStripPanel> à direita e à parte inferior do formulário.

## <a name="arrange-toolstrippanel-controls-by-z-order"></a>Organizar os controles ToolStripPanel por ordem Z

A posição de um controle de <xref:System.Windows.Forms.ToolStripPanel> encaixado em seu formulário MDI é determinada pela posição do controle na ordem z. Você pode facilmente organizar a ordem z dos controles na janela de estrutura de tópicos do documento.

1. No menu **Exibir**, clique em **Outras janelas** e clique em **Estrutura de Tópicos do Documento**.

     A organização dos controles de <xref:System.Windows.Forms.ToolStripPanel> do procedimento anterior não é padrão. Isso ocorre porque a ordem z não está correta. Use a janela de estrutura de tópicos do documento para alterar a ordem z de controles.

2. Na janela de estrutura de tópicos do documento, selecione **ToolStripPanel4**.

3. Clique no botão de seta para baixo repetidamente, até **ToolStripPanel4** estar na parte inferior da lista.

     O controle **ToolStripPanel4** é encaixado na parte inferior do formulário, sob outros controles.

4. Selecione **ToolStripPanel2**.

5. Clique no botão de seta para baixo uma vez para posicionar o controle em terceiro lugar na lista.

     O controle **ToolStripPanel2** é encaixado à parte superior do formulário, abaixo do menu principal e acima de outros controles.

6. Selecione vários controles da janela **Estrutura de Tópicos do Documento** e mova-os em diferentes posições na ordem z. Observe o efeito da ordem z no posicionamento de controles encaixados. Use CTRL-Z ou **Desfazer** no menu **Editar** para desfazer as alterações.

## <a name="checkpoint---test-your-form"></a>Ponto de verificação-testar seu formulário

1. Pressione **F5** para compilar e executar o formulário.

2. Clique na alça de um controle de <xref:System.Windows.Forms.ToolStrip> e arraste o controle para posições diferentes no formulário.

     Você pode arrastar um controle de <xref:System.Windows.Forms.ToolStrip> de um controle de <xref:System.Windows.Forms.ToolStripPanel> para outro.

## <a name="next-steps"></a>Próximas etapas

Neste tutorial, você criou um formulário pai MDI com controles <xref:System.Windows.Forms.ToolStrip> e mesclagem de menu. Você pode usar a família de controles de <xref:System.Windows.Forms.ToolStrip> para muitas outras finalidades:

- Crie menus de atalho para seus controles com <xref:System.Windows.Forms.ContextMenuStrip>. Para obter mais informações, consulte [Visão geral do componente ContextMenu](contextmenu-component-overview-windows-forms.md).

- Foi criado um formulário com um menu padrão preenchido automaticamente. Para mais informações, consulte [Instruções passo a passo: fornecendo itens de menu padrão para um formulário](walkthrough-providing-standard-menu-items-to-a-form.md).

- Dê ao seu <xref:System.Windows.Forms.ToolStrip> controles uma aparência profissional. Para obter mais informações, consulte [Como definir o renderizador ToolStrip para um aplicativo](how-to-set-the-toolstrip-renderer-for-an-application.md).

## <a name="see-also"></a>Confira também

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.StatusStrip>
- [Como criar formulários pai MDI](../advanced/how-to-create-mdi-parent-forms.md)
- [Como criar formulários filho MDI](../advanced/how-to-create-mdi-child-forms.md)
- [Como inserir um MenuStrip um menu suspenso do MDI](how-to-insert-a-menustrip-into-an-mdi-drop-down-menu-windows-forms.md)
- [Controle ToolStrip](toolstrip-control-windows-forms.md)
