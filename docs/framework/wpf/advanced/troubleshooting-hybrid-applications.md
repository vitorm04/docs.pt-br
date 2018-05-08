---
title: Solucionando problemas de aplicativos híbridos
ms.date: 03/30/2017
helpviewer_keywords:
- overlapping controls [WPF]
- Windows Forms [WPF], interoperability with
- Windows Forms [WPF], WPF interoperation
- interoperability [WPF], Windows Forms
- hybrid applications [WPF interoperability]
- message loops [WPF]
ms.assetid: f440c23f-fa5d-4d5a-852f-ba61150e6405
ms.openlocfilehash: 878761c030d4950e53ee24b76f7e29101584143a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="troubleshooting-hybrid-applications"></a>Solucionando problemas de aplicativos híbridos
<a name="introduction"></a> Este tópico lista alguns problemas comuns que podem ocorrer ao criar aplicativos híbridos que usam tecnologias [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] e [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].  
  

  
<a name="overlapping_controls"></a>   
## <a name="overlapping-controls"></a>Sobreposição de controles  
 Controles não podem se sobrepor conforme o esperado. [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] usa um HWND separado para cada controle. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] usa um HWND para todo o conteúdo em uma página. Essa diferença de implementação causa sobreposição de comportamentos inesperados.  
  
 Um controle hospedado [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] em [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sempre aparece na parte superior do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] conteúdo.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] conteúdo hospedado em um <xref:System.Windows.Forms.Integration.ElementHost> controle aparece na ordem z do <xref:System.Windows.Forms.Integration.ElementHost> controle. É possível sobrepor <xref:System.Windows.Forms.Integration.ElementHost> controles, mas hospedado [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] conteúdo não combinar ou interagir.  
  
<a name="child_property"></a>   
## <a name="child-property"></a>Propriedade Filho  
 O <xref:System.Windows.Forms.Integration.WindowsFormsHost> e <xref:System.Windows.Forms.Integration.ElementHost> classes podem hospedar apenas um controle filho único ou um elemento. Para hospedar mais de um controle ou elemento, você deve usar um contêiner como o conteúdo filho. Por exemplo, você pode adicionar [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controles de botão e a caixa de seleção para um <xref:System.Windows.Forms.Panel?displayProperty=nameWithType> controle e, em seguida, atribua o painel para um <xref:System.Windows.Forms.Integration.WindowsFormsHost> do controle <xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A> propriedade. No entanto, você não pode adicionar os controles de botão e a caixa de seleção separadamente para o mesmo <xref:System.Windows.Forms.Integration.WindowsFormsHost> controle.  
  
<a name="scaling"></a>   
## <a name="scaling"></a>Dimensionamento  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] e [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] têm modelos diferentes de dimensionamento. Alguns [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] transformações de colocação em escala são significativas para [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controles, mas não outras. Por exemplo, dimensionar um [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controle para 0 funcionará, mas se você tentar expandir o mesmo controle de volta para um valor diferente de zero, o tamanho do controle permanecerá como 0. Para obter mais informações, consulte [Considerações sobre Layout para o elemento WindowsFormsHost](../../../../docs/framework/wpf/advanced/layout-considerations-for-the-windowsformshost-element.md).  
  
<a name="adapter"></a>   
## <a name="adapter"></a>Adaptador  
 Pode haver confusão ao trabalhar o <xref:System.Windows.Forms.Integration.WindowsFormsHost> e <xref:System.Windows.Forms.Integration.ElementHost> classes, porque eles incluem um contêiner oculto. Tanto o <xref:System.Windows.Forms.Integration.WindowsFormsHost> e <xref:System.Windows.Forms.Integration.ElementHost> classes têm um contêiner oculto, chamado um *adaptador*, que eles usam para hospedar conteúdo. Para o <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento, o adaptador deriva o <xref:System.Windows.Forms.ContainerControl?displayProperty=nameWithType> classe. Para o <xref:System.Windows.Forms.Integration.ElementHost> controle, o adaptador deriva o <xref:System.Windows.Controls.DockPanel> elemento. Quando você vê referências ao adaptador de outros tópicos de interoperação, esse contêiner é o que está sendo discutido.  
  
<a name="nesting"></a>   
## <a name="nesting"></a>Aninhamento  
 Aninhando um <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento dentro de um <xref:System.Windows.Forms.Integration.ElementHost> não há suporte para o controle. Aninhando um <xref:System.Windows.Forms.Integration.ElementHost> controle dentro de um <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento também não tem suporte.  
  
<a name="focus"></a>   
## <a name="focus"></a>Foco  
 Foco funciona de forma diferente em [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] e [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)], que significa que problemas de foco podem ocorrer em um aplicativo híbrido. Por exemplo, se você tem o foco dentro de um <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento e você a minimizar e restaurar a página ou mostrar uma caixa de diálogo modal, foco dentro de <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento poderão ser perdido. O <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento ainda tem foco, mas o controle dentro dele não pode.  
  
 Validação de dados também é afetada por foco. Validação funciona em uma <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento, mas ele não funciona conforme o guia do <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento, ou entre dois diferentes <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementos.  
  
<a name="property_mapping"></a>   
## <a name="property-mapping"></a>Mapeamento de propriedade  
 Alguns mapeamentos de propriedade exigem interpretação extensiva para acabar com implementações diferentes entre as tecnologias [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] e [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]. Mapeamentos de propriedade permitem que seu código reaja a alterações nas fontes, cores e outras propriedades. Em geral, os mapeamentos de propriedade funcionam através da escuta de eventos alterados por *Propriedade* ou em Chamadas Alteradas em *Propriedade* e configurando as propriedades apropriadas no controle filho ou seu adaptador. Para mais informações, consulte [Windows Forms e mapeamento de propriedade do WPF](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-property-mapping.md).  
  
<a name="layoutrelated_properties_on_hosted_content"></a>   
## <a name="layout-related-properties-on-hosted-content"></a>Propriedades relacionadas ao layout no conteúdo hospedado  
 Quando o <xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A?displayProperty=nameWithType> ou <xref:System.Windows.Forms.Integration.ElementHost.Child%2A?displayProperty=nameWithType> é atribuída a propriedade, várias propriedades relacionadas ao layout do conteúdo hospedado são definidas automaticamente. Alterar essas propriedades de conteúdo pode causar comportamentos inesperados de layout.  
  
 O conteúdo hospedado é encaixado para preencher o <xref:System.Windows.Forms.Integration.WindowsFormsHost> e <xref:System.Windows.Forms.Integration.ElementHost> pai. Para habilitar esse comportamento de preenchimento, várias propriedades são definidas quando você define a propriedade filho. A tabela a seguir lista quais propriedades de conteúdo são definidas pelo <xref:System.Windows.Forms.Integration.ElementHost> e <xref:System.Windows.Forms.Integration.WindowsFormsHost> classes.  
  
|Classe de host|Propriedades de Conteúdo|  
|----------------|------------------------|  
|<xref:System.Windows.Forms.Integration.ElementHost>|<xref:System.Windows.FrameworkElement.Height%2A><br /><br /> <xref:System.Windows.FrameworkElement.Width%2A><br /><br /> <xref:System.Windows.FrameworkElement.Margin%2A><br /><br /> <xref:System.Windows.FrameworkElement.VerticalAlignment%2A><br /><br /> <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>|  
|<xref:System.Windows.Forms.Integration.WindowsFormsHost>|<xref:System.Windows.Forms.Control.Margin%2A><br /><br /> <xref:System.Windows.Forms.Control.Dock%2A><br /><br /> <xref:System.Windows.Forms.Control.AutoSize%2A><br /><br /> <xref:System.Windows.Forms.Control.Location%2A><br /><br /> <xref:System.Windows.Forms.Control.MaximumSize%2A>|  
  
 Não defina essas propriedades diretamente no conteúdo hospedado. Para obter mais informações, consulte [Considerações sobre Layout para o elemento WindowsFormsHost](../../../../docs/framework/wpf/advanced/layout-considerations-for-the-windowsformshost-element.md).  
  
<a name="navigation_applications"></a>   
## <a name="navigation-applications"></a>Aplicativos de Navegação  
 Aplicativos de navegação não podem manter o estado do usuário. O <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento recria seus controles quando ele é usado em um aplicativo de navegação. Recriar controles filho ocorre quando o usuário navega para fora a hospedagem de página a <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento e, em seguida, retorna a ele. Qualquer conteúdo que tenha sido digitado pelo usuário será perdido.  
  
<a name="message_loop_interoperation"></a>   
## <a name="message-loop-interoperation"></a>Interoperação de Loop de mensagem  
 Ao trabalhar com [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] loops de mensagens, as mensagens não podem ser processadas conforme o esperado. O <xref:System.Windows.Forms.Integration.WindowsFormsHost.EnableWindowsFormsInterop%2A> método é chamado pelo <xref:System.Windows.Forms.Integration.WindowsFormsHost> construtor. Este método adiciona um filtro de mensagem para o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] loop de mensagem. Esse filtro chama o <xref:System.Windows.Forms.Control.PreProcessMessage%2A?displayProperty=nameWithType> método se um <xref:System.Windows.Forms.Control?displayProperty=nameWithType> era o destino da mensagem e converte/expede a mensagem.  
  
 Se você mostrar um <xref:System.Windows.Window> em uma [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] loop de mensagem com <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType>, é possível inserir nada, a menos que você chamar o <xref:System.Windows.Forms.Integration.ElementHost.EnableModelessKeyboardInterop%2A> método. O <xref:System.Windows.Forms.Integration.ElementHost.EnableModelessKeyboardInterop%2A> leva um <xref:System.Windows.Window> e adiciona um <xref:System.Windows.Forms.IMessageFilter?displayProperty=nameWithType>, que redireciona as mensagens relacionadas à chave para o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] loop de mensagem. Para obter mais informações, consulte [Windows Forms e Arquitetura de Entrada da Interoperabilidade com WPF](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-interoperability-input-architecture.md).  
  
<a name="opacity_and_layering"></a>   
## <a name="opacity-and-layering"></a>Opacidade e disposição em camadas  
 O <xref:System.Windows.Interop.HwndHost> classe não oferece suporte a camadas. Isso significa que essa configuração de <xref:System.Windows.UIElement.Opacity%2A> propriedade no <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento não tem nenhum efeito e nenhuma combinação ocorrerá com outros [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] windows que têm <xref:System.Windows.Window.AllowsTransparency%2A> definido como `true`.  
  
<a name="dispose"></a>   
## <a name="dispose"></a>Dispose  
 O não descarte correto das classes pode causar perda de recursos. Em seus aplicativos, verifique se o <xref:System.Windows.Forms.Integration.WindowsFormsHost> e <xref:System.Windows.Forms.Integration.ElementHost> classes são descartadas, ou você pode deixar vazar recursos. [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] descarta <xref:System.Windows.Forms.Integration.ElementHost> controla quando seu não modal <xref:System.Windows.Forms.Form> pai for fechada. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] descarta <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementos quando seu aplicativo é desligado. É possível mostrar uma <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento em um <xref:System.Windows.Window> em um [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] loop de mensagem. Nesse caso, seu código pode não receber notificação de que seu aplicativo está sendo desligado.  
  
<a name="enabling_visual_styles"></a>   
## <a name="enabling-visual-styles"></a>Habilitar estilos visuais  
 [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)] estilos visuais em um [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controle não pode ser habilitado. O <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> método é chamado no modelo para um [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] aplicativo. Embora esse método não é chamado por padrão, se você usar [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] para criar um projeto, você obterá [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)] estilos visuais para controles, se a versão 6.0 do Comctl32.dll está disponível. Você deve chamar o <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> método antes de identificadores são criados no thread. Para obter mais informações, consulte [Como Habilitar Estilos Visuais em um Aplicativo Híbrido](../../../../docs/framework/wpf/advanced/how-to-enable-visual-styles-in-a-hybrid-application.md).  
  
<a name="licensed_controls"></a>   
## <a name="licensed-controls"></a>Controles licenciados  
 Controles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] licenciados que exibem informações de licenciamento em uma caixa de mensagem para o usuário podem causar um comportamento inesperado de um aplicativo híbrido. Alguns controles licenciados mostram uma caixa de diálogo em resposta a lidar com a criação. Por exemplo, um controle licenciado pode informar ao usuário que uma licença é necessária ou se o usuário tem três restantes avaliação usos do controle.  
  
 O <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento deriva o <xref:System.Windows.Interop.HwndHost> classe e o identificador do controle filho é criada dentro a <xref:System.Windows.Forms.Integration.WindowsFormsHost.BuildWindowCore%2A> método. O <xref:System.Windows.Interop.HwndHost> classe não permite que mensagens sejam processadas no <xref:System.Windows.Forms.Integration.WindowsFormsHost.BuildWindowCore%2A> método mas exibindo uma caixa de diálogo faz com que as mensagens sejam enviadas. Para habilitar esse cenário de licenciamento, chame o <xref:System.Windows.Forms.Control.CreateControl%2A?displayProperty=nameWithType> método no controle antes de atribuí-lo como o <xref:System.Windows.Forms.Integration.WindowsFormsHost> filho do elemento.  
  
<a name="wpf_designer"></a>   
## <a name="wpf-designer"></a>WPF Designer  
 Você pode criar seu conteúdo WPF usando o [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)]. As seções a seguir listam alguns problemas comuns que podem ocorrer ao criar aplicativos híbridos com o [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].  
  
### <a name="backcolortransparent-is-ignored-at-design-time"></a>BackColorTransparent é ignorado no momento de design  
 O <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> propriedade pode não funcionar conforme o esperado em tempo de design.  
  
 Se um controle WPF não estiver em um pai visível, o tempo de execução do WPF ignora o <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> valor. O motivo que <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> poderá ser ignorada é porque <xref:System.Windows.Forms.Integration.ElementHost> objeto é criado em uma função <xref:System.AppDomain>. No entanto, quando você executa o aplicativo, <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> funcionam como esperado.  
  
### <a name="design-time-error-list-appears-when-the-obj-folder-is-deleted"></a>Lista de erros do momento de design é exibida quando a pasta obj é excluída  
 Se a pasta obj for excluída, a lista de erros de tempo de Design será exibida.  
  
 Quando você cria usando <xref:System.Windows.Forms.Integration.ElementHost>, o Designer de formulários do Windows usa os arquivos gerados na pasta Debug ou Release dentro da pasta de obj do seu projeto. Se você excluir esses arquivos, será exibida a lista de erros do momento de design. Para corrigir esse problema, recompile o projeto. Par amais informações, consulte [Erros de tempo de design no Designer de Formulários do Windows](../../../../docs/framework/winforms/controls/design-time-errors-in-the-windows-forms-designer.md).  
  
<a name="elementhost_and_ime"></a>   
## <a name="elementhost-and-ime"></a>ElementHost e IME  
 Controles do WPF hospedado em um <xref:System.Windows.Forms.Integration.ElementHost> atualmente não dão suporte a <xref:System.Windows.Forms.Control.ImeMode%2A> propriedade. Altera para <xref:System.Windows.Forms.Control.ImeMode%2A> será ignorado pelos controles hospedados.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [Interoperabilidade no WPF Designer](http://msdn.microsoft.com/library/2cb7c1ca-2a75-463b-8801-fba81e2b7042)  
 [Windows Forms e arquitetura de entrada da interoperabilidade do WPF](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-interoperability-input-architecture.md)  
 [Como habilitar estilos visuais em um aplicativo híbrido](../../../../docs/framework/wpf/advanced/how-to-enable-visual-styles-in-a-hybrid-application.md)  
 [Considerações sobre o layout do elemento WindowsFormsHost](../../../../docs/framework/wpf/advanced/layout-considerations-for-the-windowsformshost-element.md)  
 [Windows Forms e mapeamento de propriedade do WPF](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-property-mapping.md)  
 [Erros de tempo de design no Designer de Formulários do Windows](../../../../docs/framework/winforms/controls/design-time-errors-in-the-windows-forms-designer.md)  
 [Migração e interoperabilidade](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)
