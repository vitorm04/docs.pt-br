---
title: Visão geral do controle ToolBar (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- ToolBar
helpviewer_keywords:
- toolbars [Windows Forms], about toolbars
- ToolBar control [Windows Forms], about ToolBar controls
ms.assetid: d426b203-0216-4dbe-b834-1641e50a9c29
ms.openlocfilehash: 42c3d9c681da9ca87125a274fa12af623269bd70
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54745237"
---
# <a name="toolbar-control-overview-windows-forms"></a>Visão geral do controle ToolBar (Windows Forms)
> [!NOTE]
>  O controle <xref:System.Windows.Forms.ToolStrip> substitui e adiciona funcionalidade ao controle <xref:System.Windows.Forms.ToolBar>, no entanto, o controle <xref:System.Windows.Forms.ToolBar> é mantido para compatibilidade com versões anteriores e para uso futuro, se desejado.  
  
 O controle <xref:System.Windows.Forms.ToolBar> dos Windows Forms é usado em formulários como uma barra de controle que exibe uma linha de menus suspensos e botões de bitmap que ativam comandos. Portanto, clicar em um botão de barra de ferramentas pode ser equivalente a escolher um comando de menu. Os botões podem ser configurados para parecerem e se comportarem como botões de pressão, menus suspensos ou separadores. Normalmente, uma barra de ferramentas contém botões e menus que correspondem aos itens na estrutura do menu do aplicativo, fornecendo acesso rápido às funções e comandos do aplicativo usados com mais frequência.  
  
## <a name="working-with-the-toolbar-control"></a>Trabalhando com o controle ToolBar  
 Um <xref:System.Windows.Forms.ToolBar> controle é geralmente "encaixado" na parte superior da sua janela pai, mas também pode ser encaixada de qualquer lado da janela. Uma barra de ferramentas pode exibir dicas de ferramenta quando o usuário apontar o ponteiro do mouse para um botão de barra de ferramentas. Uma ToolTip é uma pequena janela pop-up que descreve resumidamente a finalidade do botão ou do menu. Para exibir dicas de ferramentas, o <xref:System.Windows.Forms.ToolBar.ShowToolTips%2A> propriedade deve ser definida como `true`.  
  
> [!NOTE]
>  Alguns aplicativos apresentam controles muito semelhantes à barra de ferramentas que têm a capacidade de “flutuar” acima da janela do aplicativo e ser reposicionado. O controle ToolBar do Windows Forms não é capaz de realizar essas ações.  
  
 Quando o <xref:System.Windows.Forms.ToolBar.Appearance%2A> estiver definida como <xref:System.Windows.Forms.ToolBarAppearance>, os botões de barra de ferramentas aparecem em relevo e tridimensionais. Você pode definir as <xref:System.Windows.Forms.ToolBar.Appearance%2A> propriedade da barra de ferramentas para <xref:System.Windows.Forms.ToolBarAppearance> para dar uma aparência plana a barra de ferramentas e seus botões. Quando o ponteiro do mouse passa sobre um botão plano, a aparência do botão muda para tridimensional. Botões de barra de ferramentas podem ser divididos em grupos lógicos usando separadores. Um separador é um botão de barra de ferramentas com o <xref:System.Windows.Forms.ToolBarButton.Style%2A> propriedade definida como <xref:System.Windows.Forms.ToolBarButtonStyle>. Ele aparece como um espaço vazio na barra de ferramentas. Quando a barra de ferramentas tem uma aparência plana, os separadores de botões aparecem como linhas em vez de espaços entre os botões.  
  
 O <xref:System.Windows.Forms.ToolBar> controle permite que você crie barras de ferramentas adicionando <xref:System.Windows.Forms.Button> objetos para um <xref:System.Windows.Forms.ToolBar.Buttons%2A> coleção. Você pode usar o Editor de coleção para adicionar botões a um <xref:System.Windows.Forms.ToolBar> controle; cada <xref:System.Windows.Forms.Button> objeto deve ter texto ou uma imagem atribuídos, embora seja possível atribuir ambos. A imagem é fornecida por um componente [ImageList](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md) associado. Em tempo de execução, você pode adicionar ou remover botões do <xref:System.Windows.Forms.ToolBar.ToolBarButtonCollection> usando o <xref:System.Windows.Forms.ToolBar.ToolBarButtonCollection.Add%2A> e <xref:System.Windows.Forms.ToolBar.ToolBarButtonCollection.Remove%2A> métodos. Para programar os botões de uma <xref:System.Windows.Forms.ToolBar>, adicione código para o <xref:System.Windows.Forms.ToolBar.ButtonClick> eventos da <xref:System.Windows.Forms.ToolBar>, usando o <xref:System.Windows.Forms.ToolBarButtonClickEventArgs.Button%2A> propriedade do <xref:System.Windows.Forms.ToolBarButtonClickEventArgs> classe para determinar qual botão foi clicado.  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Windows.Forms.ToolBar>
- [Controle de barra de ferramentas](../../../../docs/framework/winforms/controls/toolbar-control-windows-forms.md)
- [Como: Adicionar botões a um controle de barra de ferramentas](../../../../docs/framework/winforms/controls/how-to-add-buttons-to-a-toolbar-control.md)
- [Como: Definir um ícone para um botão de barra de ferramentas](../../../../docs/framework/winforms/controls/how-to-define-an-icon-for-a-toolbar-button.md)
- [Como: Disparar eventos de Menu para botões da barra de ferramentas](../../../../docs/framework/winforms/controls/how-to-trigger-menu-events-for-toolbar-buttons.md)
