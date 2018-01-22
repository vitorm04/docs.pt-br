---
title: "Como criar uma interface de usuário multipainel com os Windows Forms usando o designer"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- user interface [Windows Forms], multipane
- SplitContainer control [Windows Forms], using the designer
- multipane user interface
ms.assetid: c3f9294d-a26c-4198-9242-f237f55f7573
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1752691b3cc6809f1a5da54a01e81de2d4037d19
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-create-a-multipane-user-interface-with-windows-forms-using-the-designer"></a>Como criar uma interface de usuário multipainel com os Windows Forms usando o designer
No procedimento a seguir, você vai criar uma interface do usuário com vários painéis semelhante à que é usada no Microsoft Outlook, com uma lista **Pasta**, um painel **Mensagens** e um painel **Visualização**. Essa organização é obtida principalmente por meio de controles de encaixe com o formulário.  
  
 Ao encaixar um controle, você determina a qual borda do contêiner pai um controle é fixado. Portanto, se você definir o <xref:System.Windows.Forms.SplitContainer.Dock%2A> propriedade <xref:System.Windows.Forms.DockStyle.Right>, a borda direita do controle será encaixada à direita do controle pai. Além disso, a borda encaixada do controle será redimensionada para corresponder à borda de sua caixa de controles. Para obter mais informações sobre como o <xref:System.Windows.Forms.SplitContainer.Dock%2A> propriedade funciona, consulte [como: encaixar controles nos Windows Forms](../../../../docs/framework/winforms/controls/how-to-dock-controls-on-windows-forms.md).  
  
 Este procedimento se concentra na organização a <xref:System.Windows.Forms.SplitContainer> e outros controles no formulário, não na adição de funcionalidade para tornar o aplicativo imitar o Microsoft Outlook.  
  
 Para criar essa interface do usuário, você coloca todos os controles dentro de um <xref:System.Windows.Forms.SplitContainer> controle, que contém um <xref:System.Windows.Forms.TreeView> controle no painel esquerdo. O painel direito do <xref:System.Windows.Forms.SplitContainer> controle contém um segundo <xref:System.Windows.Forms.SplitContainer> controlar com um <xref:System.Windows.Forms.ListView> controle acima um <xref:System.Windows.Forms.RichTextBox> controle. Essas <xref:System.Windows.Forms.SplitContainer> controles permitem redimensionar independente dos outros controles no formulário. Você pode adaptar as técnicas neste procedimento para criar interfaces do usuário personalizadas.  
  
> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-create-an-outlook-style-user-interface-at-design-time"></a>Para criar uma interface do usuário no estilo Outlook no tempo de design  
  
1.  Crie um novo projeto de aplicativos do Windows. Para obter detalhes, consulte [Como criar um projeto de aplicativo do Windows](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
2.  Arraste um <xref:System.Windows.Forms.SplitContainer> controlar do **caixa de ferramentas** ao formulário. No **propriedades** janela, defina o <xref:System.Windows.Forms.SplitContainer.Dock%2A> propriedade <xref:System.Windows.Forms.DockStyle.Fill>.  
  
3.  Arraste um <xref:System.Windows.Forms.TreeView> controlar do **caixa de ferramentas** no painel esquerdo do <xref:System.Windows.Forms.SplitContainer> controle. No **propriedades** janela, defina o <xref:System.Windows.Forms.SplitContainer.Dock%2A> propriedade <xref:System.Windows.Forms.DockStyle.Left> clicando o painel à esquerda no editor de valor mostrado quando clica na seta para baixo.  
  
4.  Arraste outro <xref:System.Windows.Forms.SplitContainer> controlar do **caixa de ferramentas**; colocá-lo no painel direito do <xref:System.Windows.Forms.SplitContainer> controle adicionado ao formulário. No **propriedades** janela, defina o <xref:System.Windows.Forms.SplitContainer.Dock%2A> propriedade <xref:System.Windows.Forms.DockStyle.Fill> e o <xref:System.Windows.Forms.SplitContainer.Orientation%2A> propriedade <xref:System.Windows.Forms.Orientation.Horizontal>.  
  
5.  Arraste um <xref:System.Windows.Forms.ListView> controlar do **caixa de ferramentas** no painel superior do segundo <xref:System.Windows.Forms.SplitContainer> controle adicionado ao formulário. Definir o <xref:System.Windows.Forms.SplitContainer.Dock%2A> propriedade do <xref:System.Windows.Forms.ListView> controle <xref:System.Windows.Forms.DockStyle.Fill>.  
  
6.  Arraste um <xref:System.Windows.Forms.RichTextBox> controlar do **caixa de ferramentas** no painel inferior da segunda <xref:System.Windows.Forms.SplitContainer> controle. Definir o <xref:System.Windows.Forms.SplitContainer.Dock%2A> propriedade do <xref:System.Windows.Forms.RichTextBox> controle <xref:System.Windows.Forms.DockStyle.Fill>.  
  
     Neste ponto, se você pressionar F5 para executar o aplicativo, o formulário exibirá uma interface do usuário de três partes, semelhante àquela do Microsoft Outlook.  
  
    > [!NOTE]
    >  Quando você colocar o ponteiro do mouse sobre qualquer uma das divisores dentro de <xref:System.Windows.Forms.SplitContainer> controles, você pode redimensionar as dimensões internas.  
  
     Neste ponto no desenvolvimento de aplicativos, você criou uma interface do usuário sofisticada. A próxima etapa é prosseguir com a programação de aplicativo em si, talvez conectando-se a <xref:System.Windows.Forms.TreeView> controle e <xref:System.Windows.Forms.ListView> controles para algum tipo de fonte de dados. Para obter mais informações sobre como conectar controles a dados, consulte [Vinculação de dados e Windows Forms](../../../../docs/framework/winforms/data-binding-and-windows-forms.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.SplitContainer>  
 [Controle SplitContainer](../../../../docs/framework/winforms/controls/splitcontainer-control-windows-forms.md)
