---
title: Controle ToolBar (Windows Forms)
ms.date: 03/30/2017
helpviewer_keywords:
- toolbars [Windows Forms]
- ToolBar control [Windows Forms]
ms.assetid: 6b40e9ce-6a7a-4784-bfc9-7f1d36b7462e
ms.openlocfilehash: 3f0a1b6a7f83753ccae1a129528ed320a2613122
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62009534"
---
# <a name="toolbar-control-windows-forms"></a>Controle ToolBar (Windows Forms)
> [!NOTE]
>  O controle <xref:System.Windows.Forms.ToolStrip> substitui e adiciona funcionalidade ao controle `ToolBar`, no entanto, o controle `ToolBar` é mantido para compatibilidade com versões anteriores e para uso futuro, se desejado.  
  
 O controle `ToolBar` dos Windows Forms é usado em formulários como uma barra de controle que exibe uma linha de menus suspensos e botões de bitmap que ativam comandos. Portanto, clicar em um botão de barra de ferramentas é equivalente a escolher um comando de menu. Os botões podem ser configurados para parecer e se comportar como botões de push, menus suspensos ou separadores. Normalmente, uma barra de ferramentas contém botões e menus que correspondem aos itens na estrutura do menu do aplicativo, fornecendo acesso rápido a funções e comandos usados com mais frequência do aplicativo.  
  
> [!NOTE]
>  O `ToolBar` do controle <xref:System.Windows.Forms.ToolBarButton.DropDownMenu%2A> propriedade usa uma instância do <xref:System.Windows.Forms.ContextMenu> classe como uma referência. Considere cuidadosamente a referência passada ao implementar esse tipo de botão em barras de ferramentas em seu aplicativo, como a propriedade aceitará qualquer objeto que herda o <xref:System.Windows.Forms.Menu> classe.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Visão geral do controle de barra de ferramentas](toolbar-control-overview-windows-forms.md)  
 Apresenta os conceitos gerais do controle `ToolBar`, o que permite a criação de barras de ferramentas personalizadas com que seus usuários podem trabalhar.  
  
 [Como: Adicionar botões a um controle de barra de ferramentas](how-to-add-buttons-to-a-toolbar-control.md)  
 Descreve como adicionar botões a um controle `ToolBar`.  
  
 [Como: Definir um ícone para um botão de barra de ferramentas](how-to-define-an-icon-for-a-toolbar-button.md)  
 Descreve como exibir ícones nos botões de um controle `ToolBar`.  
  
 [Como: Disparar eventos de Menu para botões da barra de ferramentas](how-to-trigger-menu-events-for-toolbar-buttons.md)  
 Fornece instruções sobre como escrever o código para interpretar em qual botão o usuário clica em um controle `ToolBar`.  
  
 Consulte também [como: Definir um ícone para um botão de barra de ferramentas usando o Designer](how-to-define-an-icon-for-a-toolbar-button-using-the-designer.md), [como: Adicionar botões a um controle de barra de ferramentas usando o Designer](how-to-add-buttons-to-a-toolbar-control-using-the-designer.md).  
  
## <a name="reference"></a>Referência  
 Classe <xref:System.Windows.Forms.ToolBar>  
 Fornece informações de referência sobre a classe e seus membros.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Controles a serem usados nos Windows Forms](controls-to-use-on-windows-forms.md)  
 Fornece uma lista completa dos controles dos Windows Forms, com links para informações sobre seu uso.  
  
 [Controle ToolStrip](toolstrip-control-windows-forms.md)  
 Descreve as barras de ferramentas que podem hospedar menus, controles e controles de usuário em aplicativos dos Windows Forms.
