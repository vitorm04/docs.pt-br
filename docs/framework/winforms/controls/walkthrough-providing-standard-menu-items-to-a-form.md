---
title: 'Instruções passo a passo: fornecendo itens de menu padrão para um formulário'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- menu items [Windows Forms], standard
- toolbars [Windows Forms], walkthroughs
- StatusStrip control [Windows Forms]
- ToolStrip control [Windows Forms]
ms.assetid: dac37d98-589e-4d6d-9673-6437e8943122
ms.openlocfilehash: ee80aad445c00bb4b98b49c80495fa512150bcef
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628768"
---
# <a name="walkthrough-providing-standard-menu-items-to-a-form"></a>Instruções passo a passo: fornecendo itens de menu padrão para um formulário

Você pode fornecer um menu padrão para seus formulários com o controle <xref:System.Windows.Forms.MenuStrip>.

Este tutorial demonstra como usar um controle de <xref:System.Windows.Forms.MenuStrip> para criar um menu padrão. O formulário também responde quando um usuário seleciona um item de menu. As seguintes tarefas são ilustradas nesta instrução passo a passo:

- Criando um projeto do Windows Forms.

- Criando um menu padrão.

- Criar um controle de <xref:System.Windows.Forms.StatusStrip>.

- Manipulação da seleção de item de menu.

Quando terminar, você terá um formulário com um menu padrão que exibe as seleções do item de menu em um controle de <xref:System.Windows.Forms.StatusStrip>.

Para copiar o código deste tópico como uma única lista, consulte [Como fornecer itens de menu padrão para um formulário](how-to-provide-standard-menu-items-to-a-form.md).

## <a name="prerequisites"></a>Prerequisites

Você precisará do Visual Studio para concluir este passo a passos.

## <a name="create-the-project"></a>Criar o projeto

1. No Visual Studio, crie um projeto de aplicativo do Windows chamado **StandardMenuForm** (**arquivo** > **novo** > **projeto** > **Visual C#**  ou **Visual Basic** > **área de trabalho clássica** > Windows Forms **aplicativo**).

2. No Designer de Formulários do Windows, selecione o formulário.

## <a name="create-a-standard-menu"></a>Criar um menu padrão

O Designer de Formulários do Windows pode preencher automaticamente um controle de <xref:System.Windows.Forms.MenuStrip> com itens de menu padrão.

1. Na **caixa de ferramentas**, arraste um controle de <xref:System.Windows.Forms.MenuStrip> para o formulário.

2. Clique no glifo ações do designer do controle de <xref:System.Windows.Forms.MenuStrip> (![seta preta pequena](./media/designer-actions-glyph.gif)) e selecione **Inserir itens padrão**.

     O controle de <xref:System.Windows.Forms.MenuStrip> é preenchido com os itens de menu padrão.

3. Clique no item de menu **Arquivo** para ver seus itens de menu padrão e ícones correspondentes.

## <a name="create-a-statusstrip-control"></a>Criar um controle StatusStrip

Use o controle <xref:System.Windows.Forms.StatusStrip> para exibir o status de seus aplicativos Windows Forms. No exemplo atual, os itens de menu selecionados pelo usuário são exibidos em um controle de <xref:System.Windows.Forms.StatusStrip>.

1. Na **caixa de ferramentas**, arraste um controle de <xref:System.Windows.Forms.StatusStrip> para o formulário.

     O controle de <xref:System.Windows.Forms.StatusStrip> se encaixa automaticamente na parte inferior do formulário.

2. Clique no botão suspenso do controle de <xref:System.Windows.Forms.StatusStrip> e selecione **StatusLabel** para adicionar um controle de <xref:System.Windows.Forms.ToolStripStatusLabel> ao controle de <xref:System.Windows.Forms.StatusStrip>.

## <a name="handle-item-selection"></a>Processar seleção de item

Manipule o evento <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> para responder quando o usuário seleciona um item de menu.

1. Clique no item de menu **Arquivo** que você criou na seção Criando um menu padrão.

2. Na janela **Propriedades**, clique em **Eventos**.

3. Clique duas vezes no evento <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked>.

     O Designer de Formulários do Windows gera um manipulador de eventos para o evento <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked>.

4. Insira o seguinte código ao manipulador de eventos.

     [!code-csharp[System.Windows.Forms.ToolStrip.StandardMenu#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.ToolStrip.StandardMenu#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/VB/Form1.vb#3)]

5. Inserir a definição de método de utilitário `UpdateStatus` ao formulário.

     [!code-csharp[System.Windows.Forms.ToolStrip.StandardMenu#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.StandardMenu#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/VB/Form1.vb#2)]

## <a name="checkpoint--test-your-form"></a>Ponto de verificação-testar seu formulário

1. Pressione **F5** para compilar e executar o formulário.

2. Clique no item de menu **Arquivo** para abrir o menu.

3. No menu **Arquivo**, clique em um dos itens para selecioná-lo.

     O controle de <xref:System.Windows.Forms.StatusStrip> exibe o item selecionado.

## <a name="next-steps"></a>Próximas etapas

Neste passo a passo, você criou um formulário com um menu padrão. Você pode usar a família de controles de <xref:System.Windows.Forms.ToolStrip> para muitas outras finalidades:

- Crie menus de atalho para seus controles com <xref:System.Windows.Forms.ContextMenuStrip>. Para obter mais informações, consulte [Visão geral do componente ContextMenu](contextmenu-component-overview-windows-forms.md).

- Crie um formulário MDI (interface de vários documentos) com controles de <xref:System.Windows.Forms.ToolStrip> de encaixe. Para obter mais informações, consulte [Instruções passo a passo: criando um formulário MDI com mesclagem de menu e controles ToolStrip](walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).

- Dê ao seu <xref:System.Windows.Forms.ToolStrip> controles uma aparência profissional. Para obter mais informações, consulte [Como definir o renderizador ToolStrip para um aplicativo](how-to-set-the-toolstrip-renderer-for-an-application.md).

## <a name="see-also"></a>Confira também

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.StatusStrip>
- [Controle MenuStrip](menustrip-control-windows-forms.md)
