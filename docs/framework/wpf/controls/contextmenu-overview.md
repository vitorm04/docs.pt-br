---
title: Visão geral de ContextMenu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], ContextMenu
- ContextMenu controls [WPF], about ContextMenu controls
ms.assetid: 16909c42-799a-4561-91e0-7d69dcfeea91
ms.openlocfilehash: 4d2d8db0f614b5240705146dbe91432b96b46dd6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185911"
---
# <a name="contextmenu-overview"></a>Visão geral de ContextMenu
A <xref:System.Windows.Controls.ContextMenu> classe representa o elemento que expõe a funcionalidade <xref:System.Windows.Controls.Menu>usando um contexto específico . Normalmente, um usuário <xref:System.Windows.Controls.ContextMenu> expõe [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] o no botão do mouse com o botão direito do mouse. Este tópico introduz <xref:System.Windows.Controls.ContextMenu> o elemento e fornece exemplos [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] de como usá-lo dentro e código.  

<a name="contextmenu_control"></a>
## <a name="contextmenu-control"></a>Controle ContextMenu  
 A <xref:System.Windows.Controls.ContextMenu> está ligado a um controle específico. O <xref:System.Windows.Controls.ContextMenu> elemento permite que você apresente aos usuários uma lista de itens que especificam comandos <xref:System.Windows.Controls.Button>ou opções que estão associadas a um determinado controle, por exemplo, a . Os usuários clicam com o botão direito do mouse no controle para exibir o menu. Normalmente, clicar <xref:System.Windows.Controls.MenuItem> em um abre um submenu ou faz com que um aplicativo realize um comando.  
  
<a name="creating_contextmenus"></a>
## <a name="creating-contextmenus"></a>Criando ContextMenus  
 Os exemplos a seguir mostram <xref:System.Windows.Controls.ContextMenu> como criar um com submenus. Os <xref:System.Windows.Controls.ContextMenu> controles estão ligados aos controles de botão.  
  
 [!code-xaml[ContextMenu#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ContextMenu/CSharp/Pane1.xaml#1)]  
  
 [!code-csharp[ContextMenu#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ContextMenu/CSharp/Pane1.xaml.cs#2)]
 [!code-vb[ContextMenu#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ContextMenu/VisualBasic/Pane1.xaml.vb#2)]  
  
<a name="applying_styles_to_contextmenu"></a>
## <a name="applying-styles-to-a-contextmenu"></a>Aplicando estilos a um ContextMenu  
 Usando um <xref:System.Windows.Style>controle, você pode mudar drasticamente <xref:System.Windows.Controls.ContextMenu> a aparência e o comportamento de um sem escrever um controle personalizado. Além de definir propriedades visuais, você também pode aplicar estilos a partes de um controle. Por exemplo, você pode alterar o comportamento de partes do controle usando propriedades, ou <xref:System.Windows.Controls.ContextMenu>pode adicionar partes ou alterar o layout de. Os exemplos a seguir mostram várias maneiras de adicionar estilos aos <xref:System.Windows.Controls.ContextMenu> controles.  
  
 O primeiro exemplo define um estilo chamado `SimpleSysResources`, que mostra como usar as configurações atuais do sistema no seu estilo. O exemplo <xref:System.Windows.SystemColors.MenuHighlightBrushKey%2A> atribui <xref:System.Windows.Controls.Control.Background%2A> como <xref:System.Windows.SystemColors.MenuTextBrushKey%2A> a <xref:System.Windows.Controls.Control.Foreground%2A> cor e <xref:System.Windows.Controls.ContextMenu>como a cor do .  
  
```xaml  
<Style x:Key="SimpleSysResources" TargetType="{x:Type MenuItem}">  
  <Setter Property = "Background" Value=
    "{DynamicResource {x:Static SystemColors.MenuHighlightBrushKey}}"/>  
  <Setter Property = "Foreground" Value=
    "{DynamicResource {x:Static SystemColors.MenuTextBrushKey}}"/>  
</Style>  
```  
  
 O exemplo a <xref:System.Windows.Trigger> seguir usa o <xref:System.Windows.Controls.Menu> elemento para alterar a aparência <xref:System.Windows.Controls.ContextMenu>de um em resposta a eventos que são levantados no . Quando um usuário move o mouse sobre <xref:System.Windows.Controls.ContextMenu> o menu, a aparência dos itens muda.  
  
```xaml  
<Style x:Key="Triggers" TargetType="{x:Type MenuItem}">  
  <Style.Triggers>  
    <Trigger Property="MenuItem.IsMouseOver" Value="true">  
      <Setter Property = "FontSize" Value="16"/>  
      <Setter Property = "FontStyle" Value="Italic"/>  
      <Setter Property = "Foreground" Value="Red"/>  
    </Trigger>  
  </Style.Triggers>  
</Style>  
```  
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.Controls.ContextMenu>
- <xref:System.Windows.Style>
- <xref:System.Windows.Controls.Menu>
- <xref:System.Windows.Controls.MenuItem>
- [ContextMenu](contextmenu.md)
- [Estilos e modelos de ContextMenu](contextmenu-styles-and-templates.md)
- [Exemplo da galeria de controles de WPF](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/ControlsAndLayout)
