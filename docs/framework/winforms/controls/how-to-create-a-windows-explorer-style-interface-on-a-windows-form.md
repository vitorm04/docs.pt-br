---
title: Como criar uma interface no estilo do Windows Explorer em Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Explorer [Windows Forms], creating with Windows Forms
- SplitContainer control [Windows Forms], Explorer-style interface
- forms [Windows Forms], Windows Explorer type
ms.assetid: 9a3d5f4f-5dda-4350-9ad5-57ce5976dc47
ms.openlocfilehash: 2d5b79244d867ea4b6134413d42710b2eadc871e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-windows-explorerstyle-interface-on-a-windows-form"></a>Como criar uma interface no estilo do Windows Explorer em Windows Forms
O Windows Explorer é uma opção de interface do usuário comum para aplicativos devido à sua familiaridade pronta.  
  
 O Windows Explorer é, essencialmente, um <xref:System.Windows.Forms.TreeView> controle e um <xref:System.Windows.Forms.ListView> controle em painéis separados. Os painéis são redimensionáveis por um divisor. Essa disposição de controles é muito eficiente para exibir e procurar informações.  
  
 As etapas a seguir mostram como organizar controles em um formato semelhante ao Windows Explorer. Elas não mostram como adicionar a funcionalidade de localização de arquivos do aplicativo Windows Explorer.  
  
> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-create-a-windows-explorer-style-windows-form"></a>Para criar um Windows Form no estilo do Windows Explorer  
  
1.  Crie um novo projeto de aplicativos do Windows. Para obter detalhes, consulte [Como criar um projeto de aplicativo do Windows](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
2.  Na **Caixa de Ferramentas**:  
  
    1.  Arraste um <xref:System.Windows.Forms.SplitContainer> controle no formulário.  
  
    2.  Arraste um <xref:System.Windows.Forms.TreeView> controlar em **SplitterPanel1** (o painel do <xref:System.Windows.Forms.SplitContainer> controle marcado **Panel1**).  
  
    3.  Arraste um <xref:System.Windows.Forms.ListView> controlar em **SplitterPanel2** (o painel do <xref:System.Windows.Forms.SplitContainer> controle marcado **Panel2**).  
  
3.  Selecione os três controles pressionando a tecla CTRL e clicando neles. Quando você seleciona o <xref:System.Windows.Forms.SplitContainer> de controle, clique na barra de divisão, em vez dos painéis.  
  
    > [!NOTE]
    >  Não use o comando **Selecionar Tudo** no menu **Editar**. Se você fizer isso, a propriedade necessária na próxima etapa não aparecerá na janela **Propriedades**.  
  
4.  No **propriedades** janela, defina o <xref:System.Windows.Forms.SplitContainer.Dock%2A> propriedade <xref:System.Windows.Forms.DockStyle.Fill>.  
  
5.  Pressione F5 para executar o aplicativo.  
  
     O formulário exibe uma interface do usuário de duas partes, semelhante à do Windows Explorer.  
  
    > [!NOTE]
    >  Quando você arrasta o divisor, os painéis são redimensionados.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.SplitContainer>  
 [Como criar uma interface do usuário multipainel com o Windows Forms](../../../../docs/framework/winforms/controls/how-to-create-a-multipane-user-interface-with-windows-forms.md)  
 [Como definir o comportamento de redimensionamento e posicionamento em uma janela dividida](../../../../docs/framework/winforms/controls/how-to-define-resize-and-positioning-behavior-in-a-split-window.md)  
 [Como dividir uma janela horizontalmente](../../../../docs/framework/winforms/controls/how-to-split-a-window-horizontally.md)  
 [Controle SplitContainer](../../../../docs/framework/winforms/controls/splitcontainer-control-windows-forms.md)
