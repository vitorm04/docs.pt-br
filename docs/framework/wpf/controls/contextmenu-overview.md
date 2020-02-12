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
ms.openlocfilehash: b973d47711632f4c0fe56f042545598272c79d2d
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77124358"
---
# <a name="contextmenu-overview"></a>Visão geral de ContextMenu
A classe <xref:System.Windows.Controls.ContextMenu> representa o elemento que expõe a funcionalidade usando um <xref:System.Windows.Controls.Menu>específico de contexto. Normalmente, um usuário expõe a <xref:System.Windows.Controls.ContextMenu> no [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] clicando com o botão do mouse com o mouse. Este tópico apresenta o elemento <xref:System.Windows.Controls.ContextMenu> e fornece exemplos de como usá-lo em [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] e código.  

<a name="contextmenu_control"></a>   
## <a name="contextmenu-control"></a>Controle ContextMenu  
 Uma <xref:System.Windows.Controls.ContextMenu> é anexada a um controle específico. O elemento <xref:System.Windows.Controls.ContextMenu> permite que você apresente aos usuários uma lista de itens que especificam comandos ou opções associadas a um controle específico, por exemplo, um <xref:System.Windows.Controls.Button>. Os usuários clicam com o botão direito do mouse no controle para exibir o menu. Normalmente, clicar em um <xref:System.Windows.Controls.MenuItem> abre um submenu ou faz com que um aplicativo execute um comando.  
  
<a name="creating_contextmenus"></a>   
## <a name="creating-contextmenus"></a>Criando ContextMenus  
 Os exemplos a seguir mostram como criar um <xref:System.Windows.Controls.ContextMenu> com submenus. Os controles de <xref:System.Windows.Controls.ContextMenu> são anexados a controles de botão.  
  
 [!code-xaml[ContextMenu#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ContextMenu/CSharp/Pane1.xaml#1)]  
  
 [!code-csharp[ContextMenu#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ContextMenu/CSharp/Pane1.xaml.cs#2)]
 [!code-vb[ContextMenu#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ContextMenu/VisualBasic/Pane1.xaml.vb#2)]  
  
<a name="applying_styles_to_contextmenu"></a>   
## <a name="applying-styles-to-a-contextmenu"></a>Aplicando estilos a um ContextMenu  
 Usando um <xref:System.Windows.Style>de controle, você pode alterar drasticamente a aparência e o comportamento de um <xref:System.Windows.Controls.ContextMenu> sem escrever um controle personalizado. Além de definir propriedades visuais, você também pode aplicar estilos a partes de um controle. Por exemplo, você pode alterar o comportamento de partes do controle usando propriedades, ou pode adicionar partes ou alterar o layout de um <xref:System.Windows.Controls.ContextMenu>. Os exemplos a seguir mostram várias maneiras de adicionar estilos a <xref:System.Windows.Controls.ContextMenu> controles.  
  
 O primeiro exemplo define um estilo chamado `SimpleSysResources`, que mostra como usar as configurações atuais do sistema no seu estilo. O exemplo atribui <xref:System.Windows.SystemColors.MenuHighlightBrushKey%2A> como a cor <xref:System.Windows.Controls.Control.Background%2A> e <xref:System.Windows.SystemColors.MenuTextBrushKey%2A> como a cor <xref:System.Windows.Controls.Control.Foreground%2A> do <xref:System.Windows.Controls.ContextMenu>.  
  
```xaml  
<Style x:Key="SimpleSysResources" TargetType="{x:Type MenuItem}">  
  <Setter Property = "Background" Value=   
    "{DynamicResource {x:Static SystemColors.MenuHighlightBrushKey}}"/>  
  <Setter Property = "Foreground" Value=   
    "{DynamicResource {x:Static SystemColors.MenuTextBrushKey}}"/>  
</Style>  
```  
  
 O exemplo a seguir usa o elemento <xref:System.Windows.Trigger> para alterar a aparência de uma <xref:System.Windows.Controls.Menu> em resposta a eventos que são gerados no <xref:System.Windows.Controls.ContextMenu>. Quando um usuário move o mouse sobre o menu, a aparência da <xref:System.Windows.Controls.ContextMenu> itens é alterada.  
  
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
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Controls.ContextMenu>
- <xref:System.Windows.Style>
- <xref:System.Windows.Controls.Menu>
- <xref:System.Windows.Controls.MenuItem>
- [ContextMenu](contextmenu.md)
- [Estilos e modelos de ContextMenu](contextmenu-styles-and-templates.md)
- [Exemplo da galeria de controles de WPF](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/ControlsAndLayout)
