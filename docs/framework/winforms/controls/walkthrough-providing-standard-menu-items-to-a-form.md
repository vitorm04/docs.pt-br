---
title: 'Passo a passo: Fornecer itens de menu padrão para um formulário'
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
ms.openlocfilehash: f9e54ecd49fc3bd295f236292715393358bab0b7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59094873"
---
# <a name="walkthrough-providing-standard-menu-items-to-a-form"></a>Passo a passo: Fornecer itens de menu padrão para um formulário
Você pode fornecer um menu padrão para os formulários com o <xref:System.Windows.Forms.MenuStrip> controle.  
  
 Este passo a passo demonstra como usar um <xref:System.Windows.Forms.MenuStrip> controle para criar um menu padrão. O formulário também responde quando um usuário seleciona um item de menu. As seguintes tarefas são ilustradas nesta instrução passo a passo:  
  
-   Criando um projeto do Windows Forms.  
  
-   Criando um menu padrão.  
  
-   Criando um <xref:System.Windows.Forms.StatusStrip> controle.  
  
-   Manipulação da seleção de item de menu.  
  
 Quando tiver terminado, você terá um formulário com um menu padrão que exibe as seleções de item de menu em um <xref:System.Windows.Forms.StatusStrip> controle.  
  
 Para copiar o código deste tópico como uma única listagem, confira [Como: Fornecer itens de Menu padrão para um formulário](how-to-provide-standard-menu-items-to-a-form.md).  
  
> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Para concluir este passo a passo, você precisará de:  
  
-   Permissões suficientes para poder criar e executar projetos de aplicativos dos Windows Forms no computador no qual Visual Studio está instalado.  
  
## <a name="creating-the-project"></a>Criando o Projeto  
 A primeira etapa é criar o projeto e configurar o formulário.  
  
#### <a name="to-create-the-project"></a>Para criar o projeto  
  
1.  Crie um projeto de aplicativo do Windows chamado **StandardMenuForm** (**arquivo** > **novo** > **projeto**  >  **Visual c#** ou **Visual Basic** > **área de trabalho clássica** > **Windows Forms Aplicativo**).  
  
2.  No Designer de Formulários do Windows, selecione o formulário.  
  
## <a name="creating-a-standard-menu"></a>Criando um menu padrão  
 O Designer de formulários do Windows pode preencher automaticamente um <xref:System.Windows.Forms.MenuStrip> controle com itens de menu padrão.  
  
#### <a name="to-create-a-standard-menu"></a>Criar um menu padrão  
  
1.  Dos **caixa de ferramentas**, arraste um <xref:System.Windows.Forms.MenuStrip> controle para seu formulário.  
  
2.  Clique o <xref:System.Windows.Forms.MenuStrip> glifo de smart tag do controle (![glifo de Smart Tag](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) e selecione **inserir itens padrão**.  
  
     O <xref:System.Windows.Forms.MenuStrip> controle é preenchido com os itens de menu padrão.  
  
3.  Clique no item de menu **Arquivo** para ver seus itens de menu padrão e ícones correspondentes.  
  
## <a name="creating-a-statusstrip-control"></a>Criando um controle StatusStrip  
 Use o <xref:System.Windows.Forms.StatusStrip> controle para exibir o status de seus aplicativos dos Windows Forms. No exemplo atual, os itens de menu selecionados pelo usuário são exibidos em um <xref:System.Windows.Forms.StatusStrip> controle.  
  
#### <a name="to-create-a-statusstrip-control"></a>Criar um controle StatusStrip  
  
1.  Dos **caixa de ferramentas**, arraste um <xref:System.Windows.Forms.StatusStrip> controle para seu formulário.  
  
     O <xref:System.Windows.Forms.StatusStrip> controle se encaixa automaticamente na parte inferior do formulário.  
  
2.  Clique o <xref:System.Windows.Forms.StatusStrip> do controle botão de lista suspensa e selecione **StatusLabel** para adicionar um <xref:System.Windows.Forms.ToolStripStatusLabel> o controle para o <xref:System.Windows.Forms.StatusStrip> controle.  
  
## <a name="handling-item-selection"></a>Manipulação da seleção de item  
 Manipular o <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> eventos para responder quando o usuário seleciona um item de menu.  
  
#### <a name="to-handle-item-selection"></a>Manipular a seleção de itens  
  
1.  Clique no item de menu **Arquivo** que você criou na seção Criando um menu padrão.  
  
2.  Na janela **Propriedades**, clique em **Eventos**.  
  
3.  Clique duas vezes o <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> eventos.  
  
     O Designer de formulários do Windows gera um manipulador de eventos para o <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> eventos.  
  
4.  Insira o seguinte código ao manipulador de eventos.  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StandardMenu#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.ToolStrip.StandardMenu#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/VB/Form1.vb#3)]  
  
5.  Inserir a definição de método de utilitário `UpdateStatus` ao formulário.  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StandardMenu#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.StandardMenu#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/VB/Form1.vb#2)]  
  
## <a name="checkpoint"></a>Ponto de verificação  
  
#### <a name="to-test-your-form"></a>Testar o formulário  
  
1.  Pressione F5 para compilar e executar seu formulário.  
  
2.  Clique no item de menu **Arquivo** para abrir o menu.  
  
3.  No menu **Arquivo**, clique em um dos itens para selecioná-lo.  
  
     O <xref:System.Windows.Forms.StatusStrip> controle exibe o item selecionado.  
  
## <a name="next-steps"></a>Próximas etapas  
 Neste passo a passo, você criou um formulário com um menu padrão. Você pode usar o <xref:System.Windows.Forms.ToolStrip> família de controles para muitas outras finalidades:  
  
-   Criar menus de atalho para os controles com <xref:System.Windows.Forms.ContextMenuStrip>. Para obter mais informações, consulte [Visão geral do componente ContextMenu](contextmenu-component-overview-windows-forms.md).  
  
-   Criar um formulário de MDI (interface MDI) de vários documentos com encaixe <xref:System.Windows.Forms.ToolStrip> controles. Para obter mais informações, confira [Passo a passo: Criando um formulário MDI com mesclagem de Menu e controles ToolStrip](walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).  
  
-   Dê sua <xref:System.Windows.Forms.ToolStrip> controla uma aparência profissional. Para obter mais informações, confira [Como: Definir o renderizador ToolStrip para um aplicativo](how-to-set-the-toolstrip-renderer-for-an-application.md).  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.StatusStrip>
- [Controle MenuStrip](menustrip-control-windows-forms.md)
