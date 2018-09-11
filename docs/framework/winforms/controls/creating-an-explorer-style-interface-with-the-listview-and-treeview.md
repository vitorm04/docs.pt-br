---
title: 'Instruções passo a passo: criando uma interface no estilo do Explorer com os controles ListView e TreeView usando o designer'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Explorer-style applications [Windows Forms], walkthroughs
- TreeView control [Windows Forms], ListView controls used with
- ListView control [Windows Forms], TreeView controls used with
- Explorer-style applications
- TreeView control [Windows Forms], using for explorer-style interface
- ListView control [Windows Forms], explorer style interface
- ListView control [Windows Forms], explorer-style interface
ms.assetid: 9e5e7721-19e2-4890-b273-a43589fe99ff
ms.openlocfilehash: 73d3a0bef1ab075aee8e06f676ef17b853773552
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44267204"
---
# <a name="walkthrough-creating-an-explorer-style-interface-with-the-listview-and-treeview-controls-using-the-designer"></a>Instruções passo a passo: criando uma interface no estilo do Explorer com os controles ListView e TreeView usando o designer
Um dos benefícios do Visual Studio é a capacidade de criar aplicativos dos Windows Forms com aparência profissional em pouco tempo. Um cenário comum é criar uma interface do usuário (UI) com <xref:System.Windows.Forms.ListView> e <xref:System.Windows.Forms.TreeView> controles que se parece com o recurso Windows Explorer dos sistemas de operacionais do Windows. O Windows Explorer exibe uma estrutura hierárquica de arquivos e pastas no computador do usuário.  
  
> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-create-the-form-containing-a-listview-and-treeview-control"></a>Para criar o formulário contendo controles ListView e TreeView  
  
1.  No menu **Arquivo**, aponte para **Novo** e clique em **Projeto**.  
  
2.  Na caixa de diálogo **Novo Projeto**, faça o seguinte:  
  
    1.  Em categorias, escolha **Visual Basic** ou **Visual C#**.  
  
    2.  Na lista de modelos, escolha **Aplicativo dos Windows Forms**.  
  
3.  Clique em **OK**. Um novo projeto dos Windows Forms é criado.  
  
4.  Adicionar um <xref:System.Windows.Forms.SplitContainer> controle ao formulário e defina sua <xref:System.Windows.Forms.SplitContainer.Dock%2A> propriedade <xref:System.Windows.Forms.DockStyle.Fill>.  
  
5.  Adicionar um <xref:System.Windows.Forms.ImageList> chamado `imageList1` ao formulário e use a janela de propriedades para adicionar duas imagens: uma imagem de pasta e uma imagem de documento, nessa ordem.  
  
6.  Adicionar um <xref:System.Windows.Forms.TreeView> controle chamado `treeview1` para o formulário e posicione-a no lado esquerdo do <xref:System.Windows.Forms.SplitContainer> controle. Na janela Propriedades para `treeView1`, faça o seguinte:  
  
    1.  Defina a propriedade <xref:System.Windows.Forms.Control.Dock%2A> como <xref:System.Windows.Forms.DockStyle.Fill>.  
  
    2.  Defina a propriedade <xref:System.Windows.Forms.TreeView.ImageList%2A> como `imagelist1.`  
  
7.  Adicionar um <xref:System.Windows.Forms.ListView> controle chamado `listView1` para o formulário e posicione-o no lado direito do <xref:System.Windows.Forms.SplitContainer> controle. Na janela Propriedades para `listview1`, faça o seguinte:  
  
    1.  Defina a propriedade <xref:System.Windows.Forms.Control.Dock%2A> como <xref:System.Windows.Forms.DockStyle.Fill>.  
  
    2.  Defina a propriedade <xref:System.Windows.Forms.ListView.View%2A> como <xref:System.Windows.Forms.View.Details>.  
  
    3.  Abra o Editor de coleção ColumnHeader clicando nas reticências (![captura de tela VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) na <xref:System.Windows.Forms.ListView.Columns%2A> propriedade **.** Adicione três colunas e defina suas <xref:System.Windows.Forms.ColumnHeader.Text%2A> propriedade para `Name`, `Type`, e `Last Modified`, respectivamente. Clique em **OK** para fechar a caixa de diálogo.  
  
    4.  Defina a propriedade <xref:System.Windows.Forms.ListView.SmallImageList%2A> como `imageList1.`  
  
8.  Implementar o código para preencher o <xref:System.Windows.Forms.TreeView> conosco e subnós. Adicione este código à classe `Form1`.  
  
     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#1)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#1)]  
  
9. Uma vez que o código anterior usa o namespace System.IO, adicione as instruções using ou import adequadas na parte superior do formulário.  
  
     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#4)]  
  
10. Chame o método de configuração da etapa anterior no construtor do formulário ou <xref:System.Windows.Forms.Form.Load> método manipulador de eventos. Adicione este código ao construtor de formulário.  
  
     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#2)]  
  
11. Lidar com o <xref:System.Windows.Forms.TreeView.NodeMouseClick> evento `treeview1` **,** e implementar o código para preencher `listview1` com conteúdo de um nó quando um nó é clicado. Adicione este código à classe `Form1`.  
  
     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#3)]  
  
     Se você estiver usando c#, verifique se você tem o <xref:System.Windows.Forms.TreeView.NodeMouseClick> evento associado com seu método de manipulação de eventos. Adicione este código ao construtor de formulário.  
  
     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#5)]  
  
## <a name="testing-the-application"></a>Testando o aplicativo  
 Agora, é possível testar o formulário para garantir que ele se comporta da forma esperada.  
  
#### <a name="to-test-the-form"></a>Para testar o formulário  
  
-   Pressione F5 para executar o aplicativo.  
  
     Você verá um formulário dividido que contém um <xref:System.Windows.Forms.TreeView> controle que exibe o diretório do projeto no lado esquerdo, e um <xref:System.Windows.Forms.ListView> controle à direita com três colunas. Você pode percorrer os <xref:System.Windows.Forms.TreeView> selecionando nós do diretório e o <xref:System.Windows.Forms.ListView> é preenchido com o conteúdo do diretório selecionado.  
  
## <a name="next-steps"></a>Próximas etapas  
 Esse aplicativo fornece um exemplo de uma maneira de usar <xref:System.Windows.Forms.TreeView> e <xref:System.Windows.Forms.ListView> controla juntos. Para obter mais informações sobre esses controles, consulte os seguintes tópicos:  
  
-   [Como adicionar informações personalizadas a um controle TreeView ou ListView (Windows Forms)](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)  
  
-   [Como Adicionar Recursos de Pesquisa a um Controle ListView](../../../../docs/framework/winforms/controls/how-to-add-search-capabilities-to-a-listview-control.md)  
  
-   [Como anexar um menu de atalho a um nó TreeView](../../../../docs/framework/winforms/controls/how-to-attach-a-shortcut-menu-to-a-treeview-node.md)  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.ListView>  
 <xref:System.Windows.Forms.TreeView>  
 [Controle ListView](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)  
 [Como adicionar e remover nós com o controle TreeView dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)  
 [Como Adicionar e Remover Itens com o Controle ListView dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)  
 [Como adicionar colunas ao controle ListView do Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md)
