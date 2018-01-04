---
title: "Instruções passo a passo: criando um formulário MDI com mesclagem de menu e controles ToolStrip"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b170c3e3311dbbfb070a66107bd4f22407647bae
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls"></a>Instruções passo a passo: criando um formulário MDI com mesclagem de menu e controles ToolStrip
O <xref:System.Windows.Forms?displayProperty=nameWithType> namespace oferece suporte para vários aplicativos de interface (MDI) do documento e o <xref:System.Windows.Forms.MenuStrip> controle oferece suporte a mesclagem de menu. Formulários MDI também podem <xref:System.Windows.Forms.ToolStrip> controles.  
  
 Este passo a passo demonstra como usar <xref:System.Windows.Forms.ToolStripPanel> controles com um formulário MDI. O formulário também dá suporte à mesclagem com menus filho. As seguintes tarefas são ilustradas nesta explicação passo a passo:  
  
-   Criando um projeto do Windows Forms.  
  
-   Criando o menu principal do formulário. O nome real do menu variará.  
  
-   Adicionando o <xref:System.Windows.Forms.ToolStripPanel> o controle para o **caixa de ferramentas**.  
  
-   Criando um formulário filho.  
  
-   Organizando <xref:System.Windows.Forms.ToolStripPanel> controles por ordem z.  
  
 Quando você terminar, você terá um formulário MDI que dá suporte à mesclagem de menu e movable <xref:System.Windows.Forms.ToolStrip> controles.  
  
 Para copiar o código neste tópico como uma única lista, consulte [Como criar um formulário MDI com mesclagem de menu e controles ToolStrip](../../../../docs/framework/winforms/controls/how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).  
  
> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Para concluir este passo a passo, você precisará de:  
  
-   Permissões suficientes para poder criar e executar projetos de Aplicativo do Windows Forms no computador no qual [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] está instalado.  
  
## <a name="creating-the-project"></a>Criando o Projeto  
 A primeira etapa é criar o projeto e configurar o formulário.  
  
#### <a name="to-create-the-project"></a>Para criar o projeto  
  
1.  Criar um projeto de aplicativos do Windows chamado **MdiForm**.  
  
     Para obter mais informações, consulte [Como criar um projeto de aplicativos do Windows](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
2.  No Designer de Formulários do Windows, selecione o formulário.  
  
3.  Na janela Propriedades, defina o valor da <xref:System.Windows.Forms.Form.IsMdiContainer%2A> para `true`.  
  
## <a name="creating-the-main-menu"></a>Criando o menu principal  
 O formulário MDI pai contém o menu principal. O menu principal tem um item de menu chamado **Janela**. Com o item de menu **Janela**, você pode criar formulários filho. Os itens de menu de formulários filho são mesclados no menu principal.  
  
#### <a name="to-create-the-main-menu"></a>Como criar o menu principal  
  
1.  Do **caixa de ferramentas**, arraste um <xref:System.Windows.Forms.MenuStrip> controle para o formulário.  
  
2.  Adicionar um <xref:System.Windows.Forms.ToolStripMenuItem> para o <xref:System.Windows.Forms.MenuStrip> controlar e nomeie-o **janela**.  
  
3.  Selecione o <xref:System.Windows.Forms.MenuStrip> controle.  
  
4.  Na janela Propriedades, defina o valor da <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> propriedade `ToolStripMenuItem1`.  
  
5.  Adicione um subitem no item de menu **Janela** e nomeie o subitem como **Novo**.  
  
6.  Na janela Propriedades, clique em **Eventos**.  
  
7.  Clique duas vezes o <xref:System.Windows.Forms.ToolStripItem.Click> evento.  
  
     O Designer de formulários do Windows gera um manipulador de eventos para o <xref:System.Windows.Forms.ToolStripItem.Click> evento.  
  
8.  Insira o seguinte código ao manipulador de eventos.  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.MdiForm#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.MdiForm#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/VB/Form1.vb#2)]  
  
## <a name="adding-the-toolstrippanel-control-to-the-toolbox"></a>Adicionando o controle ToolStripPanel à caixa de ferramentas  
 Quando você usa <xref:System.Windows.Forms.MenuStrip> controles com um formulário MDI deve ter o <xref:System.Windows.Forms.ToolStripPanel> controle. Você deve adicionar o <xref:System.Windows.Forms.ToolStripPanel> o controle para o **caixa de ferramentas** para criar o formulário MDI no Designer de formulários do Windows.  
  
#### <a name="to-add-the-toolstrippanel-control-to-the-toolbox"></a>Como adicionar o controle ToolStripPanel à caixa de ferramentas  
  
1.  Abra a **caixa de ferramentas** e, em seguida, clique na guia **Todos os Windows Forms** para mostrar os controles dos Windows Forms disponíveis.  
  
2.  Clique com o botão direito do mouse para abrir o menu de atalho e selecione **Escolher Itens**.  
  
3.  Na caixa de diálogo **Escolher Itens da Caixa de Ferramentas**, role para baixo a coluna **Nome** até encontrar **ToolStripPanel**.  
  
4.  Marque a caixa de seleção por **ToolStripPanel**e, em seguida, clique em **OK**.  
  
     O <xref:System.Windows.Forms.ToolStripPanel> controle aparece no **caixa de ferramentas**.  
  
## <a name="creating-a-child-form"></a>Criando um formulário filho  
 Neste procedimento, você definirá uma classe de formulário filho separada que tem seu próprio <xref:System.Windows.Forms.MenuStrip> controle. Os itens de menu para esse formulário são mesclados com as do formulário pai.  
  
#### <a name="to-define-a-child-form"></a>Como definir um formulário filho  
  
1.  Adicione um novo formulário chamado `ChildForm` ao projeto.  
  
     Para obter mais informações, consulte [Como adicionar o Windows Forms a um projeto](http://msdn.microsoft.com/en-us/3d7bb25f-fd90-47cf-9378-fa0d764686c1).  
  
2.  Do **caixa de ferramentas**, arraste um <xref:System.Windows.Forms.MenuStrip> controle para o formulário filho.  
  
3.  Clique o <xref:System.Windows.Forms.MenuStrip> glifo de marca inteligente do controle (![marca inteligente](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) e, em seguida, selecione **editar itens**.  
  
4.  No **Editor de coleção de itens** caixa de diálogo caixa, adicione uma nova <xref:System.Windows.Forms.ToolStripMenuItem> chamado **ChildMenuItem** ao menu filho.  
  
     Para obter mais informações, consulte [Editor de Coleção dos Itens ToolStrip](http://msdn.microsoft.com/en-us/e681f3ab-94ba-4b2b-ac64-1dfad46caa25).  
  
## <a name="testing-the-form"></a>Testando o formulário  
  
#### <a name="to-test-your-form"></a>Como testar o formulário  
  
1.  Pressione F5 para compilar e executar seu formulário.  
  
2.  Clique no item de menu **Janela** para abrir o menu e, em seguida, clique em **Novo**.  
  
     Um novo formulário filho é criado na área de cliente do MDI do formulário. O menu do formulário filho será mesclado com o menu principal.  
  
3.  Feche o formulário filho.  
  
     O menu do formulário filho será removido do menu principal.  
  
4.  Clique em **Novo** várias vezes.  
  
     Os formulários filho automaticamente são listados na l**janela** porque o item de menu a <xref:System.Windows.Forms.MenuStrip> do controle <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> propriedade é atribuída.  
  
## <a name="adding-toolstrip-support"></a>Adicionando suporte ToolStrip  
 Neste procedimento, você adicionará quatro <xref:System.Windows.Forms.ToolStrip> controles ao formulário pai MDI. Cada <xref:System.Windows.Forms.ToolStrip> controle é adicionado dentro de um <xref:System.Windows.Forms.ToolStripPanel> controle, que é encaixado na borda da forma.  
  
#### <a name="to-add-toolstrip-controls-to-the-mdi-parent-form"></a>Como adicionar controles ToolStrip ao formulário pai do MDI  
  
1.  Do **caixa de ferramentas**, arraste um <xref:System.Windows.Forms.ToolStripPanel> controle para o formulário.  
  
2.  Com o <xref:System.Windows.Forms.ToolStripPanel> controle selecionado, clique duas vezes o <xref:System.Windows.Forms.ToolStrip> controlar o **caixa de ferramentas**.  
  
     Um <xref:System.Windows.Forms.ToolStrip> controle é criado no <xref:System.Windows.Forms.ToolStripPanel> controle.  
  
3.  Selecione o <xref:System.Windows.Forms.ToolStripPanel> controle.  
  
4.  Na janela Propriedades, altere o valor do controle <xref:System.Windows.Forms.Control.Dock%2A> propriedade <xref:System.Windows.Forms.DockStyle.Left>.  
  
     O <xref:System.Windows.Forms.ToolStripPanel> controlar módulos de ancoragem para o lado esquerdo do formulário, sob o menu principal. A área do cliente MDI é redimensionada para ajustar o <xref:System.Windows.Forms.ToolStripPanel> controle.  
  
5.  Repita as etapas de 1 a 4.  
  
     Encaixar o novo <xref:System.Windows.Forms.ToolStripPanel> controle para a parte superior do formulário.  
  
     O <xref:System.Windows.Forms.ToolStripPanel> controle está encaixado sob o menu principal, mas à direita do primeiro <xref:System.Windows.Forms.ToolStripPanel> controle. Esta etapa ilustra a importância de ordem z no posicionamento corretamente <xref:System.Windows.Forms.ToolStripPanel> controles.  
  
6.  Repita as etapas 1 a 4 para duas mais <xref:System.Windows.Forms.ToolStripPanel> controles.  
  
     Encaixar o novo <xref:System.Windows.Forms.ToolStripPanel> controles à direita e inferior do formulário.  
  
## <a name="arranging-toolstrippanel-controls-by-z-order"></a>Organizando controles ToolStripPanel pela ordem Z  
 A posição de um encaixada <xref:System.Windows.Forms.ToolStripPanel> controle do formulário MDI é determinada pela posição do controle na ordem z. Você pode facilmente organizar a ordem z dos controles na janela de estrutura de tópicos do documento.  
  
#### <a name="to-arrange-toolstrippanel-controls-by-z-order"></a>Como organizar controles ToolStripPanel pela ordem Z  
  
1.  No menu **Exibir**, clique em **Outras janelas** e clique em **Estrutura de Tópicos do Documento**.  
  
     A organização dos seus <xref:System.Windows.Forms.ToolStripPanel> controles do procedimento anterior é o padrão. Isso ocorre porque a ordem z não está correta. Use a janela de estrutura de tópicos do documento para alterar a ordem z de controles.  
  
2.  Na janela de estrutura de tópicos do documento, selecione **ToolStripPanel4**.  
  
3.  Clique no botão de seta para baixo repetidamente, até **ToolStripPanel4** estar na parte inferior da lista.  
  
     O controle **ToolStripPanel4** é encaixado na parte inferior do formulário, sob outros controles.  
  
4.  Selecione **ToolStripPanel2**.  
  
5.  Clique no botão de seta para baixo uma vez para posicionar o controle em terceiro lugar na lista.  
  
     O controle **ToolStripPanel2** é encaixado à parte superior do formulário, abaixo do menu principal e acima de outros controles.  
  
6.  Selecione vários controles da janela **Estrutura de Tópicos do Documento** e mova-os em diferentes posições na ordem z. Observe o efeito da ordem z no posicionamento de controles encaixados. Use CTRL-Z ou **Desfazer** no menu **Editar** para desfazer as alterações.  
  
## <a name="checkpoint"></a>Ponto de verificação  
  
#### <a name="to-test-your-form"></a>Testar o formulário  
  
1.  Pressione F5 para compilar e executar seu formulário.  
  
2.  Clique a alça de um <xref:System.Windows.Forms.ToolStrip> controlar e arraste o controle para posições diferentes no formulário.  
  
     Você pode arrastar um <xref:System.Windows.Forms.ToolStrip> controle de um <xref:System.Windows.Forms.ToolStripPanel> controle para outro.  
  
## <a name="next-steps"></a>Próximas etapas  
 Neste passo a passo, você criou um formulário de pai MDI com <xref:System.Windows.Forms.ToolStrip> mesclagem de menu e controles. Você pode usar o <xref:System.Windows.Forms.ToolStrip> família de controles para muitas outras finalidades:  
  
-   Criar menus de atalho para os controles com <xref:System.Windows.Forms.ContextMenuStrip>. Para obter mais informações, consulte [Visão geral do componente ContextMenu](../../../../docs/framework/winforms/controls/contextmenu-component-overview-windows-forms.md).  
  
-   Foi criado um formulário com um menu padrão preenchido automaticamente. Para mais informações, consulte [Instruções passo a passo: fornecendo itens de menu padrão para um formulário](../../../../docs/framework/winforms/controls/walkthrough-providing-standard-menu-items-to-a-form.md).  
  
-   Dê sua <xref:System.Windows.Forms.ToolStrip> controla uma aparência profissional. Para obter mais informações, consulte [Como definir o renderizador ToolStrip para um aplicativo](../../../../docs/framework/winforms/controls/how-to-set-the-toolstrip-renderer-for-an-application.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.StatusStrip>  
 [Como criar formulários pai MDI](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)  
 [Como criar formulários filho MDI](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md)  
 [Como inserir um MenuStrip um menu suspenso do MDI](../../../../docs/framework/winforms/controls/how-to-insert-a-menustrip-into-an-mdi-drop-down-menu-windows-forms.md)  
 [Controle ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)
