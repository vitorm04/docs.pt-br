---
title: 'Instruções passo a passo: fornecendo itens de menu padrão para um formulário'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- menu items [Windows Forms], standard
- toolbars [Windows Forms], walkthroughs
- StatusStrip control [Windows Forms]
- ToolStrip control [Windows Forms]
ms.assetid: dac37d98-589e-4d6d-9673-6437e8943122
caps.latest.revision: 7
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 00988266804207e85bc715342f888fd29348066e
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2018
---
# <a name="walkthrough-providing-standard-menu-items-to-a-form"></a>Instruções passo a passo: fornecendo itens de menu padrão para um formulário
Você pode fornecer um menu padrão para seus formulários com o <xref:System.Windows.Forms.MenuStrip> controle.  
  
 Este passo a passo demonstra como usar um <xref:System.Windows.Forms.MenuStrip> controle para criar um menu padrão. O formulário também responde quando um usuário seleciona um item de menu. As seguintes tarefas são ilustradas nesta instrução passo a passo:  
  
-   Criando um projeto do Windows Forms.  
  
-   Criando um menu padrão.  
  
-   Criando um <xref:System.Windows.Forms.StatusStrip> controle.  
  
-   Manipulação da seleção de item de menu.  
  
 Quando você terminar, você terá um formulário com um menu padrão que exibe as seleções de item de menu em um <xref:System.Windows.Forms.StatusStrip> controle.  
  
 Para copiar o código deste tópico como uma única lista, consulte [Como fornecer itens de menu padrão para um formulário](../../../../docs/framework/winforms/controls/how-to-provide-standard-menu-items-to-a-form.md).  
  
> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Para concluir este passo a passo, você precisará de:  
  
-   Permissões suficientes para poder criar e executar projetos de aplicativos dos Windows Forms no computador no qual Visual Studio está instalado.  
  
## <a name="creating-the-project"></a>Criando o Projeto  
 A primeira etapa é criar o projeto e configurar o formulário.  
  
#### <a name="to-create-the-project"></a>Para criar o projeto  
  
1.  Criar um projeto de aplicativos do Windows chamado **StandardMenuForm**.  
  
     Para obter mais informações, consulte [Como criar um projeto de aplicativos do Windows](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
2.  No Designer de Formulários do Windows, selecione o formulário.  
  
## <a name="creating-a-standard-menu"></a>Criando um menu padrão  
 O Designer de formulários do Windows pode preencher automaticamente uma <xref:System.Windows.Forms.MenuStrip> controle com itens de menu padrão.  
  
#### <a name="to-create-a-standard-menu"></a>Criar um menu padrão  
  
1.  Do **caixa de ferramentas**, arraste um <xref:System.Windows.Forms.MenuStrip> controle no formulário.  
  
2.  Clique o <xref:System.Windows.Forms.MenuStrip> glifo de marca inteligente do controle (![marca inteligente](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) e selecione **inserir itens padrão**.  
  
     O <xref:System.Windows.Forms.MenuStrip> controle é preenchido com os itens de menu padrão.  
  
3.  Clique no item de menu **Arquivo** para ver seus itens de menu padrão e ícones correspondentes.  
  
## <a name="creating-a-statusstrip-control"></a>Criando um controle StatusStrip  
 Use o <xref:System.Windows.Forms.StatusStrip> controle para exibir o status de seus aplicativos de formulários do Windows. No exemplo atual, os itens de menu selecionados pelo usuário são exibidos em um <xref:System.Windows.Forms.StatusStrip> controle.  
  
#### <a name="to-create-a-statusstrip-control"></a>Criar um controle StatusStrip  
  
1.  Do **caixa de ferramentas**, arraste um <xref:System.Windows.Forms.StatusStrip> controle no formulário.  
  
     O <xref:System.Windows.Forms.StatusStrip> controle encaixa automaticamente para a parte inferior do formulário.  
  
2.  Clique o <xref:System.Windows.Forms.StatusStrip> do controle de botão suspenso e selecione **StatusLabel** para adicionar um <xref:System.Windows.Forms.ToolStripStatusLabel> o controle para o <xref:System.Windows.Forms.StatusStrip> controle.  
  
## <a name="handling-item-selection"></a>Manipulação da seleção de item  
 Manipular o <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> evento para responder quando o usuário seleciona um item de menu.  
  
#### <a name="to-handle-item-selection"></a>Manipular a seleção de itens  
  
1.  Clique no item de menu **Arquivo** que você criou na seção Criando um menu padrão.  
  
2.  Na janela **Propriedades**, clique em **Eventos**.  
  
3.  Clique duas vezes o <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> evento.  
  
     O Designer de formulários do Windows gera um manipulador de eventos para o <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> evento.  
  
4.  Insira o seguinte código ao manipulador de eventos.  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StandardMenu#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.ToolStrip.StandardMenu#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/VB/Form1.vb#3)]  
  
5.  Inserir a definição de método de utilitário `UpdateStatus` ao formulário.  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StandardMenu#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.StandardMenu#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/VB/Form1.vb#2)]  
  
## <a name="checkpoint"></a>Ponto de verificação  
  
#### <a name="to-test-your-form"></a>Testar o formulário  
  
1.  Pressione F5 para compilar e executar seu formulário.  
  
2.  Clique no item de menu **Arquivo** para abrir o menu.  
  
3.  No menu **Arquivo**, clique em um dos itens para selecioná-lo.  
  
     O <xref:System.Windows.Forms.StatusStrip> controle exibe o item selecionado.  
  
## <a name="next-steps"></a>Próximas etapas  
 Neste passo a passo, você criou um formulário com um menu padrão. Você pode usar o <xref:System.Windows.Forms.ToolStrip> família de controles para muitas outras finalidades:  
  
-   Criar menus de atalho para os controles com <xref:System.Windows.Forms.ContextMenuStrip>. Para obter mais informações, consulte [Visão geral do componente ContextMenu](../../../../docs/framework/winforms/controls/contextmenu-component-overview-windows-forms.md).  
  
-   Criar um formulário de interface MDI vários documentos com encaixe <xref:System.Windows.Forms.ToolStrip> controles. Para obter mais informações, consulte [Instruções passo a passo: criando um formulário MDI com mesclagem de menu e controles ToolStrip](../../../../docs/framework/winforms/controls/walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).  
  
-   Dê sua <xref:System.Windows.Forms.ToolStrip> controla uma aparência profissional. Para obter mais informações, consulte [Como definir o renderizador ToolStrip para um aplicativo](../../../../docs/framework/winforms/controls/how-to-set-the-toolstrip-renderer-for-an-application.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.StatusStrip>  
 [Controle MenuStrip](../../../../docs/framework/winforms/controls/menustrip-control-windows-forms.md)
