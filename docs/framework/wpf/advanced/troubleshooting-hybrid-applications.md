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
ms.openlocfilehash: 46d8f00f9328e9c0a4df596b709195ae42d651bf
ms.sourcegitcommit: 42ed59871db1f29a32b3d8e7abeb20e6eceeda7c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74960124"
---
# <a name="troubleshooting-hybrid-applications"></a>Solucionando problemas de aplicativos híbridos
<a name="introduction"></a> Este tópico lista alguns problemas comuns que podem ocorrer ao criar aplicativos híbridos que usam tecnologias [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] e [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].  

<a name="overlapping_controls"></a>   
## <a name="overlapping-controls"></a>Sobreposição de controles  
 Controles não podem se sobrepor conforme o esperado. [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] usa um HWND separado para cada controle. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] usa um HWND para todo o conteúdo em uma página. Essa diferença de implementação causa sobreposição de comportamentos inesperados.  
  
 Um controle hospedado [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] em [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sempre aparece na parte superior do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] conteúdo.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] conteúdo hospedado em um controle de <xref:System.Windows.Forms.Integration.ElementHost> aparece na ordem z do controle de <xref:System.Windows.Forms.Integration.ElementHost>. É possível sobrepor <xref:System.Windows.Forms.Integration.ElementHost> controles, mas o conteúdo hospedado [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] não combina ou interage.  
  
<a name="child_property"></a>   
## <a name="child-property"></a>Propriedade Filho  
 As classes <xref:System.Windows.Forms.Integration.WindowsFormsHost> e <xref:System.Windows.Forms.Integration.ElementHost> podem hospedar apenas um único controle ou elemento filho. Para hospedar mais de um controle ou elemento, você deve usar um contêiner como o conteúdo filho. Por exemplo, você pode adicionar [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] botão e controles de caixa de seleção a um controle de <xref:System.Windows.Forms.Panel?displayProperty=nameWithType> e, em seguida, atribuir o painel à propriedade <xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A> de um controle de <xref:System.Windows.Forms.Integration.WindowsFormsHost>. No entanto, você não pode adicionar os controles de botão e caixa de seleção separadamente ao mesmo controle de <xref:System.Windows.Forms.Integration.WindowsFormsHost>.  
  
<a name="scaling"></a>   
## <a name="scaling"></a>Dimensionamento  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] e [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] têm modelos diferentes de dimensionamento. Alguns [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] transformações de colocação em escala são significativas para [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controles, mas não outras. Por exemplo, dimensionar um [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controle para 0 funcionará, mas se você tentar expandir o mesmo controle de volta para um valor diferente de zero, o tamanho do controle permanecerá como 0. Para obter mais informações, consulte [Considerações sobre Layout para o elemento WindowsFormsHost](layout-considerations-for-the-windowsformshost-element.md).  
  
<a name="adapter"></a>   
## <a name="adapter"></a>Personalizado  
 Pode haver confusão ao trabalhar com as classes <xref:System.Windows.Forms.Integration.WindowsFormsHost> e <xref:System.Windows.Forms.Integration.ElementHost>, pois elas incluem um contêiner oculto. As classes <xref:System.Windows.Forms.Integration.WindowsFormsHost> e <xref:System.Windows.Forms.Integration.ElementHost> têm um contêiner oculto, chamado de *adaptador*, que eles usam para hospedar conteúdo. Para o elemento <xref:System.Windows.Forms.Integration.WindowsFormsHost>, o adaptador deriva da classe <xref:System.Windows.Forms.ContainerControl?displayProperty=nameWithType>. Para o controle <xref:System.Windows.Forms.Integration.ElementHost>, o adaptador deriva do elemento <xref:System.Windows.Controls.DockPanel>. Quando você vê referências ao adaptador de outros tópicos de interoperação, esse contêiner é o que está sendo discutido.  
  
<a name="nesting"></a>   
## <a name="nesting"></a>Aninhamento  
 Não há suporte para aninhar um elemento <xref:System.Windows.Forms.Integration.WindowsFormsHost> dentro de um controle de <xref:System.Windows.Forms.Integration.ElementHost>. Também não há suporte para aninhar um controle de <xref:System.Windows.Forms.Integration.ElementHost> dentro de um elemento <xref:System.Windows.Forms.Integration.WindowsFormsHost>.  
  
<a name="focus"></a>   
## <a name="focus"></a>Foco  
 Foco funciona de forma diferente em [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] e [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)], que significa que problemas de foco podem ocorrer em um aplicativo híbrido. Por exemplo, se você tiver foco dentro de um elemento de <xref:System.Windows.Forms.Integration.WindowsFormsHost> e você minimizar e restaurar a página ou mostrar uma caixa de diálogo modal, o foco dentro do elemento <xref:System.Windows.Forms.Integration.WindowsFormsHost> poderá ser perdido. O elemento <xref:System.Windows.Forms.Integration.WindowsFormsHost> ainda tem foco, mas o controle dentro dele pode não.  
  
 Validação de dados também é afetada por foco. A validação funciona em um elemento <xref:System.Windows.Forms.Integration.WindowsFormsHost>, mas não funciona à medida que você faz a sua tabulação para fora do elemento <xref:System.Windows.Forms.Integration.WindowsFormsHost> ou entre dois elementos de <xref:System.Windows.Forms.Integration.WindowsFormsHost> diferentes.  
  
<a name="property_mapping"></a>   
## <a name="property-mapping"></a>Mapeamento de propriedade  
 Alguns mapeamentos de propriedade exigem interpretação extensiva para acabar com implementações diferentes entre as tecnologias [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] e [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]. Mapeamentos de propriedade permitem que seu código reaja a alterações nas fontes, cores e outras propriedades. Em geral, os mapeamentos de propriedade funcionam através da escuta de eventos alterados por *Propriedade* ou em Chamadas Alteradas em *Propriedade* e configurando as propriedades apropriadas no controle filho ou seu adaptador. Para mais informações, consulte [Windows Forms e mapeamento de propriedade do WPF](windows-forms-and-wpf-property-mapping.md).  
  
<a name="layoutrelated_properties_on_hosted_content"></a>   
## <a name="layout-related-properties-on-hosted-content"></a>Propriedades relacionadas ao layout no conteúdo hospedado  
 Quando a propriedade <xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A?displayProperty=nameWithType> ou <xref:System.Windows.Forms.Integration.ElementHost.Child%2A?displayProperty=nameWithType> é atribuída, várias propriedades relacionadas ao layout no conteúdo hospedado são definidas automaticamente. Alterar essas propriedades de conteúdo pode causar comportamentos inesperados de layout.  
  
 Seu conteúdo hospedado está encaixado para preencher o <xref:System.Windows.Forms.Integration.WindowsFormsHost> e <xref:System.Windows.Forms.Integration.ElementHost> pai. Para habilitar esse comportamento de preenchimento, várias propriedades são definidas quando você define a propriedade filho. A tabela a seguir lista quais propriedades de conteúdo são definidas pelas classes <xref:System.Windows.Forms.Integration.ElementHost> e <xref:System.Windows.Forms.Integration.WindowsFormsHost>.  
  
|Classe de host|Propriedades de Conteúdo|  
|----------------|------------------------|  
|<xref:System.Windows.Forms.Integration.ElementHost>|<xref:System.Windows.FrameworkElement.Height%2A><br /><br /> <xref:System.Windows.FrameworkElement.Width%2A><br /><br /> <xref:System.Windows.FrameworkElement.Margin%2A><br /><br /> <xref:System.Windows.FrameworkElement.VerticalAlignment%2A><br /><br /> <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>|  
|<xref:System.Windows.Forms.Integration.WindowsFormsHost>|<xref:System.Windows.Forms.Control.Margin%2A><br /><br /> <xref:System.Windows.Forms.Control.Dock%2A><br /><br /> <xref:System.Windows.Forms.Control.AutoSize%2A><br /><br /> <xref:System.Windows.Forms.Control.Location%2A><br /><br /> <xref:System.Windows.Forms.Control.MaximumSize%2A>|  
  
 Não defina essas propriedades diretamente no conteúdo hospedado. Para obter mais informações, consulte [Considerações sobre Layout para o elemento WindowsFormsHost](layout-considerations-for-the-windowsformshost-element.md).  
  
<a name="navigation_applications"></a>   
## <a name="navigation-applications"></a>Aplicativos de Navegação  
 Aplicativos de navegação não podem manter o estado do usuário. O elemento <xref:System.Windows.Forms.Integration.WindowsFormsHost> recria seus controles quando ele é usado em um aplicativo de navegação. A recriação de controles filho ocorre quando o usuário navega para fora da página que hospeda o elemento <xref:System.Windows.Forms.Integration.WindowsFormsHost> e, em seguida, retorna a ele. Qualquer conteúdo que tenha sido digitado pelo usuário será perdido.  
  
<a name="message_loop_interoperation"></a>   
## <a name="message-loop-interoperation"></a>Interoperação de Loop de mensagem  
 Ao trabalhar com [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] loops de mensagens, as mensagens não podem ser processadas conforme o esperado. O método <xref:System.Windows.Forms.Integration.WindowsFormsHost.EnableWindowsFormsInterop%2A> é chamado pelo Construtor <xref:System.Windows.Forms.Integration.WindowsFormsHost>. Este método adiciona um filtro de mensagem para o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] loop de mensagem. Esse filtro chama o método <xref:System.Windows.Forms.Control.PreProcessMessage%2A?displayProperty=nameWithType> se um <xref:System.Windows.Forms.Control?displayProperty=nameWithType> era o destino da mensagem e traduz/despacha a mensagem.  
  
 Se você mostrar uma <xref:System.Windows.Window> em um loop de mensagem [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] com <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType>, não poderá digitar nada a menos que chame o método <xref:System.Windows.Forms.Integration.ElementHost.EnableModelessKeyboardInterop%2A>. O método <xref:System.Windows.Forms.Integration.ElementHost.EnableModelessKeyboardInterop%2A> usa um <xref:System.Windows.Window> e adiciona um <xref:System.Windows.Forms.IMessageFilter?displayProperty=nameWithType>, que redireciona mensagens relacionadas à chave para o loop de mensagem [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Para obter mais informações, consulte [Windows Forms e Arquitetura de Entrada da Interoperabilidade com WPF](windows-forms-and-wpf-interoperability-input-architecture.md).  
  
<a name="opacity_and_layering"></a>   
## <a name="opacity-and-layering"></a>Opacidade e disposição em camadas  
 A classe <xref:System.Windows.Interop.HwndHost> não dá suporte a camadas. Isso significa que definir a propriedade <xref:System.Windows.UIElement.Opacity%2A> no elemento <xref:System.Windows.Forms.Integration.WindowsFormsHost> não terá efeito e nenhuma mesclagem ocorrerá com outras [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] janelas que tenham <xref:System.Windows.Window.AllowsTransparency%2A> definido como `true`.  
  
<a name="dispose"></a>   
## <a name="dispose"></a>Dispose  
 O não descarte correto das classes pode causar perda de recursos. Em seus aplicativos híbridos, verifique se as classes <xref:System.Windows.Forms.Integration.WindowsFormsHost> e <xref:System.Windows.Forms.Integration.ElementHost> foram descartadas ou se você pode vazar recursos. [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] descarta <xref:System.Windows.Forms.Integration.ElementHost> controles quando seu pai <xref:System.Windows.Forms.Form> não modal é fechado. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] descarta os elementos <xref:System.Windows.Forms.Integration.WindowsFormsHost> quando o aplicativo é desligado. É possível mostrar um elemento <xref:System.Windows.Forms.Integration.WindowsFormsHost> em um <xref:System.Windows.Window> em um loop de mensagem [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]. Nesse caso, seu código pode não receber notificação de que seu aplicativo está sendo desligado.  
  
<a name="enabling_visual_styles"></a>   
## <a name="enabling-visual-styles"></a>Habilitar estilos visuais  
 Os estilos visuais do Microsoft Windows XP em um controle de [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] não podem ser habilitados. O método <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> é chamado no modelo para um aplicativo [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]. Embora esse método não seja chamado por padrão, se você usar o Visual Studio para criar um projeto, obterá os estilos visuais do Microsoft Windows XP para controles, se a versão 6,0 do Comctl32. dll estiver disponível. Você deve chamar o método <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> antes que os identificadores sejam criados no thread. Para obter mais informações, consulte [Como Habilitar Estilos Visuais em um Aplicativo Híbrido](how-to-enable-visual-styles-in-a-hybrid-application.md).  
  
<a name="licensed_controls"></a>   
## <a name="licensed-controls"></a>Controles licenciados  
 Controles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] licenciados que exibem informações de licenciamento em uma caixa de mensagem para o usuário podem causar um comportamento inesperado de um aplicativo híbrido. Alguns controles licenciados mostram uma caixa de diálogo em resposta a lidar com a criação. Por exemplo, um controle licenciado pode informar ao usuário que uma licença é necessária ou se o usuário tem três restantes avaliação usos do controle.  
  
 O elemento <xref:System.Windows.Forms.Integration.WindowsFormsHost> deriva da classe <xref:System.Windows.Interop.HwndHost> e o identificador do controle filho é criado dentro do método <xref:System.Windows.Forms.Integration.WindowsFormsHost.BuildWindowCore%2A>. A classe <xref:System.Windows.Interop.HwndHost> não permite que as mensagens sejam processadas no método <xref:System.Windows.Forms.Integration.WindowsFormsHost.BuildWindowCore%2A>, mas a exibição de uma caixa de diálogo faz com que as mensagens sejam enviadas. Para habilitar esse cenário de licenciamento, chame o método <xref:System.Windows.Forms.Control.CreateControl%2A?displayProperty=nameWithType> no controle antes de atribuí-lo como o filho do elemento <xref:System.Windows.Forms.Integration.WindowsFormsHost>.  
  
<a name="wpf_designer"></a>   
## <a name="wpf-designer"></a>WPF Designer  
 Você pode criar seu conteúdo do WPF usando o designer do WPF para Visual Studio. As seções a seguir listam alguns problemas comuns que podem ocorrer durante a criação de aplicativos híbridos com o designer do WPF.  
  
### <a name="backcolortransparent-is-ignored-at-design-time"></a>BackColorTransparent é ignorado no momento de design  
 A propriedade <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> pode não funcionar conforme o esperado no tempo de design.  
  
 Se um controle WPF não estiver em um pai visível, o tempo de execução do WPF ignorará o valor <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A>. O motivo pelo qual <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> pode ser ignorado é porque <xref:System.Windows.Forms.Integration.ElementHost> objeto é criado em um <xref:System.AppDomain>separado. No entanto, quando você executa o aplicativo, <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> funciona conforme o esperado.  
  
### <a name="design-time-error-list-appears-when-the-obj-folder-is-deleted"></a>Lista de erros do momento de design é exibida quando a pasta obj é excluída  
 Se a pasta obj for excluída, a lista de erros de tempo de Design será exibida.  
  
 Quando você cria usando <xref:System.Windows.Forms.Integration.ElementHost>, o Designer de Formulários do Windows usa arquivos gerados na pasta de depuração ou versão na pasta obj do projeto. Se você excluir esses arquivos, será exibida a lista de erros do momento de design. Para corrigir esse problema, recompile o projeto. Par amais informações, consulte [Erros de tempo de design no Designer de Formulários do Windows](../../winforms/controls/design-time-errors-in-the-windows-forms-designer.md).  
  
<a name="elementhost_and_ime"></a>   
## <a name="elementhost-and-ime"></a>ElementHost e IME  
 Os controles WPF hospedados em um <xref:System.Windows.Forms.Integration.ElementHost> atualmente não dão suporte à propriedade <xref:System.Windows.Forms.Control.ImeMode%2A>. As alterações em <xref:System.Windows.Forms.Control.ImeMode%2A> serão ignoradas pelos controles hospedados.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Interoperabilidade no designer do WPF](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb628658(v=vs.100))
- [Windows Forms e arquitetura de entrada da interoperabilidade do WPF](windows-forms-and-wpf-interoperability-input-architecture.md)
- [Como habilitar estilos visuais em um aplicativo híbrido](how-to-enable-visual-styles-in-a-hybrid-application.md)
- [Considerações sobre o layout do elemento WindowsFormsHost](layout-considerations-for-the-windowsformshost-element.md)
- [Windows Forms e mapeamento de propriedade do WPF](windows-forms-and-wpf-property-mapping.md)
- [Erros de tempo de design no Designer de Formulários do Windows](../../winforms/controls/design-time-errors-in-the-windows-forms-designer.md)
- [Migração e Interoperabilidade](migration-and-interoperability.md)
