---
title: Visão geral do controle ToolBar
ms.date: 03/30/2017
f1_keywords:
- ToolBar
helpviewer_keywords:
- toolbars [Windows Forms], about toolbars
- ToolBar control [Windows Forms], about ToolBar controls
ms.assetid: d426b203-0216-4dbe-b834-1641e50a9c29
ms.openlocfilehash: f364e052258703331496f8103b48953a90aa3a9b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76735490"
---
# <a name="toolbar-control-overview-windows-forms"></a>Visão geral do controle ToolBar (Windows Forms)
> [!NOTE]
> O controle <xref:System.Windows.Forms.ToolStrip> substitui e adiciona funcionalidade ao controle <xref:System.Windows.Forms.ToolBar>, no entanto, o controle <xref:System.Windows.Forms.ToolBar> é mantido para compatibilidade com versões anteriores e para uso futuro, se desejado.  
  
 O controle <xref:System.Windows.Forms.ToolBar> dos Windows Forms é usado em formulários como uma barra de controle que exibe uma linha de menus suspensos e botões de bitmap que ativam comandos. Portanto, clicar em um botão de barra de ferramentas pode ser equivalente a escolher um comando de menu. Os botões podem ser configurados para parecerem e se comportarem como botões de pressão, menus suspensos ou separadores. Normalmente, uma barra de ferramentas contém botões e menus que correspondem aos itens na estrutura do menu do aplicativo, fornecendo acesso rápido às funções e comandos do aplicativo usados com mais frequência.  
  
## <a name="working-with-the-toolbar-control"></a>Trabalhando com o controle ToolBar  
 Um controle de <xref:System.Windows.Forms.ToolBar> geralmente é "encaixado" ao longo da parte superior de sua janela pai, mas também pode ser encaixado em qualquer lado da janela. Uma barra de ferramentas pode exibir dicas de ferramenta quando o usuário apontar o ponteiro do mouse para um botão de barra de ferramentas. Uma ToolTip é uma pequena janela pop-up que descreve resumidamente a finalidade do botão ou do menu. Para exibir dicas de ferramentas, a propriedade <xref:System.Windows.Forms.ToolBar.ShowToolTips%2A> deve ser definida como `true`.  
  
> [!NOTE]
> Alguns aplicativos apresentam controles muito semelhantes à barra de ferramentas que têm a capacidade de “flutuar” acima da janela do aplicativo e ser reposicionado. O controle ToolBar do Windows Forms não é capaz de realizar essas ações.  
  
 Quando a propriedade <xref:System.Windows.Forms.ToolBar.Appearance%2A> é definida como <xref:System.Windows.Forms.ToolBarAppearance>, os botões da barra de ferramentas são gerados e tridimensionais. Você pode definir a propriedade <xref:System.Windows.Forms.ToolBar.Appearance%2A> da barra de ferramentas como <xref:System.Windows.Forms.ToolBarAppearance> para dar à barra de ferramentas e a seus botões uma aparência plana. Quando o ponteiro do mouse passa sobre um botão plano, a aparência do botão muda para tridimensional. Botões de barra de ferramentas podem ser divididos em grupos lógicos usando separadores. Um separador é um botão da barra de ferramentas com a propriedade <xref:System.Windows.Forms.ToolBarButton.Style%2A> definida como <xref:System.Windows.Forms.ToolBarButtonStyle>. Ele aparece como um espaço vazio na barra de ferramentas. Quando a barra de ferramentas tem uma aparência plana, os separadores de botões aparecem como linhas em vez de espaços entre os botões.  
  
 O controle de <xref:System.Windows.Forms.ToolBar> permite que você crie barras de ferramentas adicionando <xref:System.Windows.Forms.Button> objetos a uma coleção de <xref:System.Windows.Forms.ToolBar.Buttons%2A>. Você pode usar o editor de coleção para adicionar botões a um controle de <xref:System.Windows.Forms.ToolBar>; cada objeto de <xref:System.Windows.Forms.Button> deve ter texto ou uma imagem atribuída, embora você possa atribuir ambos. A imagem é fornecida por um componente [ImageList](imagelist-component-windows-forms.md) associado. Em tempo de execução, você pode adicionar ou remover botões da <xref:System.Windows.Forms.ToolBar.ToolBarButtonCollection> usando os métodos <xref:System.Windows.Forms.ToolBar.ToolBarButtonCollection.Add%2A> e <xref:System.Windows.Forms.ToolBar.ToolBarButtonCollection.Remove%2A>. Para programar os botões de um <xref:System.Windows.Forms.ToolBar>, adicione o código aos eventos <xref:System.Windows.Forms.ToolBar.ButtonClick> do <xref:System.Windows.Forms.ToolBar>, usando a propriedade <xref:System.Windows.Forms.ToolBarButtonClickEventArgs.Button%2A> da classe <xref:System.Windows.Forms.ToolBarButtonClickEventArgs> para determinar qual botão foi clicado.  
  
## <a name="see-also"></a>Veja também

- <xref:System.Windows.Forms.ToolBar>
- [Controle de barra de ferramentas](toolbar-control-windows-forms.md)
- [Como adicionar botões a um controle de barra de ferramentas](how-to-add-buttons-to-a-toolbar-control.md)
- [Como definir um ícone para um botão de barra de ferramentas](how-to-define-an-icon-for-a-toolbar-button.md)
- [Como disparar eventos de menu para botões da barra de ferramentas](how-to-trigger-menu-events-for-toolbar-buttons.md)
