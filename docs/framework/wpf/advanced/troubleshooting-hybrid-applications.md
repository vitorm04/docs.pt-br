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
ms.openlocfilehash: b85a607d2e44d6253359a81118f90e6ee05d2d3f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187320"
---
# <a name="troubleshooting-hybrid-applications"></a>Solucionando problemas de aplicativos híbridos
<a name="introduction"></a>Este tópico lista alguns problemas comuns que podem [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ocorrer ao criar aplicativos híbridos, que usam tecnologias do Windows Forms.  

<a name="overlapping_controls"></a>
## <a name="overlapping-controls"></a>Sobreposição de controles  
 Controles não podem se sobrepor conforme o esperado. O Windows Forms usa um HWND separado para cada controle. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] usa um HWND para todo o conteúdo em uma página. Essa diferença de implementação causa sobreposição de comportamentos inesperados.  
  
 Um controle do Windows [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Forms hospedado sempre [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aparece em cima do conteúdo.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]conteúdo hospedado em <xref:System.Windows.Forms.Integration.ElementHost> um controle aparece na <xref:System.Windows.Forms.Integration.ElementHost> ordem z do controle. É possível sobrepor <xref:System.Windows.Forms.Integration.ElementHost> controles, mas [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] o conteúdo hospedado não combina ou interage.  
  
<a name="child_property"></a>
## <a name="child-property"></a>Propriedade Filho  
 As <xref:System.Windows.Forms.Integration.WindowsFormsHost> <xref:System.Windows.Forms.Integration.ElementHost> aulas e podem hospedar apenas um único controle ou elemento de criança. Para hospedar mais de um controle ou elemento, você deve usar um contêiner como o conteúdo filho. Por exemplo, você pode adicionar o botão Windows <xref:System.Windows.Forms.Panel?displayProperty=nameWithType> Forms e os controles da <xref:System.Windows.Forms.Integration.WindowsFormsHost> caixa <xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A> de seleção a um controle e, em seguida, atribuir o painel à propriedade de um controle. No entanto, não é possível adicionar os controles <xref:System.Windows.Forms.Integration.WindowsFormsHost> de botão e caixa de seleção separadamente ao mesmo controle.  
  
<a name="scaling"></a>
## <a name="scaling"></a>Scaling  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]e os Formulários windows têm modelos de escala diferentes. Algumas [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] transformações de dimensionamento são significativas para os controles do Windows Forms, mas outras não. Por exemplo, dimensionar um controle do Windows Forms para 0 funcionará, mas se você tentar dimensionar o mesmo controle de volta para um valor não-zero, o tamanho do controle permanecerá 0. Para obter mais informações, consulte [Considerações sobre Layout para o elemento WindowsFormsHost](layout-considerations-for-the-windowsformshost-element.md).  
  
<a name="adapter"></a>
## <a name="adapter"></a>Adaptador  
 Pode haver confusão <xref:System.Windows.Forms.Integration.WindowsFormsHost> ao <xref:System.Windows.Forms.Integration.ElementHost> trabalhar nas aulas, porque eles incluem um recipiente escondido. Tanto <xref:System.Windows.Forms.Integration.WindowsFormsHost> as <xref:System.Windows.Forms.Integration.ElementHost> classes quanto as classes têm um recipiente oculto, chamado *adaptador,* que eles usam para hospedar conteúdo. Para <xref:System.Windows.Forms.Integration.WindowsFormsHost> o elemento, o adaptador <xref:System.Windows.Forms.ContainerControl?displayProperty=nameWithType> deriva da classe. Para <xref:System.Windows.Forms.Integration.ElementHost> o controle, o adaptador <xref:System.Windows.Controls.DockPanel> deriva do elemento. Quando você vê referências ao adaptador de outros tópicos de interoperação, esse contêiner é o que está sendo discutido.  
  
<a name="nesting"></a>
## <a name="nesting"></a>Aninhamento  
 Não é <xref:System.Windows.Forms.Integration.WindowsFormsHost> suportado <xref:System.Windows.Forms.Integration.ElementHost> um elemento dentro de um controle. Aninhar <xref:System.Windows.Forms.Integration.ElementHost> um <xref:System.Windows.Forms.Integration.WindowsFormsHost> controle dentro de um elemento também não é suportado.  
  
<a name="focus"></a>
## <a name="focus"></a>Focus  
 O foco funciona [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de forma diferente e os Formulários do Windows, o que significa que problemas de foco podem ocorrer em um aplicativo híbrido. Por exemplo, se você <xref:System.Windows.Forms.Integration.WindowsFormsHost> tiver foco dentro de um elemento e minimizar e restaurar a <xref:System.Windows.Forms.Integration.WindowsFormsHost> página ou mostrar uma caixa de diálogo modal, o foco dentro do elemento pode ser perdido. O <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento ainda tem foco, mas o controle dentro dele pode não.  
  
 Validação de dados também é afetada por foco. A validação <xref:System.Windows.Forms.Integration.WindowsFormsHost> funciona em um elemento, mas não <xref:System.Windows.Forms.Integration.WindowsFormsHost> funciona como você <xref:System.Windows.Forms.Integration.WindowsFormsHost> guia fora do elemento, ou entre dois elementos diferentes.  
  
<a name="property_mapping"></a>
## <a name="property-mapping"></a>Mapeamento de propriedade  
 Alguns mapeamentos de propriedades requerem uma interpretação [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] extensiva para fazer uma ponte entre as tecnologias Windows Forms e Windows. Mapeamentos de propriedade permitem que seu código reaja a alterações nas fontes, cores e outras propriedades. Em geral, os mapeamentos de propriedade funcionam através da escuta de eventos alterados por *Propriedade* ou em Chamadas Alteradas em *Propriedade* e configurando as propriedades apropriadas no controle filho ou seu adaptador. Para mais informações, consulte [Windows Forms e mapeamento de propriedade do WPF](windows-forms-and-wpf-property-mapping.md).  
  
<a name="layoutrelated_properties_on_hosted_content"></a>
## <a name="layout-related-properties-on-hosted-content"></a>Propriedades relacionadas ao layout no conteúdo hospedado  
 Quando <xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A?displayProperty=nameWithType> a <xref:System.Windows.Forms.Integration.ElementHost.Child%2A?displayProperty=nameWithType> propriedade ou propriedade é atribuída, várias propriedades relacionadas ao layout no conteúdo hospedado são definidas automaticamente. Alterar essas propriedades de conteúdo pode causar comportamentos inesperados de layout.  
  
 Seu conteúdo hospedado está ancorado <xref:System.Windows.Forms.Integration.WindowsFormsHost> para <xref:System.Windows.Forms.Integration.ElementHost> preencher o e pai. Para habilitar esse comportamento de preenchimento, várias propriedades são definidas quando você define a propriedade filho. A tabela a seguir lista quais <xref:System.Windows.Forms.Integration.ElementHost> <xref:System.Windows.Forms.Integration.WindowsFormsHost> propriedades de conteúdo são definidas pelas classes e classes.  
  
|Classe de host|Propriedades de Conteúdo|  
|----------------|------------------------|  
|<xref:System.Windows.Forms.Integration.ElementHost>|<xref:System.Windows.FrameworkElement.Height%2A><br /><br /> <xref:System.Windows.FrameworkElement.Width%2A><br /><br /> <xref:System.Windows.FrameworkElement.Margin%2A><br /><br /> <xref:System.Windows.FrameworkElement.VerticalAlignment%2A><br /><br /> <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>|  
|<xref:System.Windows.Forms.Integration.WindowsFormsHost>|<xref:System.Windows.Forms.Control.Margin%2A><br /><br /> <xref:System.Windows.Forms.Control.Dock%2A><br /><br /> <xref:System.Windows.Forms.Control.AutoSize%2A><br /><br /> <xref:System.Windows.Forms.Control.Location%2A><br /><br /> <xref:System.Windows.Forms.Control.MaximumSize%2A>|  
  
 Não defina essas propriedades diretamente no conteúdo hospedado. Para obter mais informações, consulte [Considerações sobre Layout para o elemento WindowsFormsHost](layout-considerations-for-the-windowsformshost-element.md).  
  
<a name="navigation_applications"></a>
## <a name="navigation-applications"></a>Aplicativos de Navegação  
 Aplicativos de navegação não podem manter o estado do usuário. O <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento recria seus controles quando é usado em um aplicativo de navegação. A recriação dos controles de criança ocorre quando <xref:System.Windows.Forms.Integration.WindowsFormsHost> o usuário navega para longe da página que hospeda o elemento e, em seguida, retorna a ele. Qualquer conteúdo que tenha sido digitado pelo usuário será perdido.  
  
<a name="message_loop_interoperation"></a>
## <a name="message-loop-interoperation"></a>Interoperação de Loop de mensagem  
 Ao trabalhar com loops de mensagens do Windows Forms, as mensagens podem não ser processadas como esperado. O <xref:System.Windows.Forms.Integration.WindowsFormsHost.EnableWindowsFormsInterop%2A> método é <xref:System.Windows.Forms.Integration.WindowsFormsHost> chamado pelo construtor. Este método adiciona um filtro de mensagem para o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] loop de mensagem. Este filtro <xref:System.Windows.Forms.Control.PreProcessMessage%2A?displayProperty=nameWithType> chama o <xref:System.Windows.Forms.Control?displayProperty=nameWithType> método se um era o alvo da mensagem e traduze/despacha a mensagem.  
  
 Se você <xref:System.Windows.Window> mostrar um loop de <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType>mensagem do Windows Forms <xref:System.Windows.Forms.Integration.ElementHost.EnableModelessKeyboardInterop%2A> com , você não poderá digitar nada a menos que você chame o método. O <xref:System.Windows.Forms.Integration.ElementHost.EnableModelessKeyboardInterop%2A> método <xref:System.Windows.Window> pega a <xref:System.Windows.Forms.IMessageFilter?displayProperty=nameWithType>e adiciona um , que [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] redireciona mensagens relacionadas a chaves para o loop de mensagem. Para obter mais informações, consulte [Windows Forms e Arquitetura de Entrada da Interoperabilidade com WPF](windows-forms-and-wpf-interoperability-input-architecture.md).  
  
<a name="opacity_and_layering"></a>
## <a name="opacity-and-layering"></a>Opacidade e disposição em camadas  
 A <xref:System.Windows.Interop.HwndHost> classe não suporta camadas. Isso significa que <xref:System.Windows.UIElement.Opacity%2A> a <xref:System.Windows.Forms.Integration.WindowsFormsHost> configuração da propriedade no elemento não [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tem efeito, e nenhuma mistura ocorrerá com outras janelas que foram <xref:System.Windows.Window.AllowsTransparency%2A> definidas como `true`.  
  
<a name="dispose"></a>
## <a name="dispose"></a>Dispose  
 O não descarte correto das classes pode causar perda de recursos. Em suas aplicações híbridas, <xref:System.Windows.Forms.Integration.WindowsFormsHost> certifique-se de que as classes e e <xref:System.Windows.Forms.Integration.ElementHost> as classes estão descartadas, ou você pode vazar recursos. O Windows <xref:System.Windows.Forms.Integration.ElementHost> Forms elimina os controles <xref:System.Windows.Forms.Form> quando seu pai não modal fecha. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]elimina <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementos quando seu aplicativo é desligado. É possível mostrar <xref:System.Windows.Forms.Integration.WindowsFormsHost> um elemento <xref:System.Windows.Window> em um loop de mensagem do Windows Forms. Nesse caso, seu código pode não receber notificação de que seu aplicativo está sendo desligado.  
  
<a name="enabling_visual_styles"></a>
## <a name="enabling-visual-styles"></a>Habilitar estilos visuais  
 Os estilos visuais do Microsoft Windows XP em um controle do Windows Forms podem não estar ativados. O <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> método é chamado no modelo para um aplicativo Windows Forms. Embora este método não seja chamado por padrão, se você usar o Visual Studio para criar um projeto, você obterá estilos visuais do Microsoft Windows XP para controles, se a versão 6.0 do Comctl32.dll estiver disponível. Você deve <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> chamar o método antes que as alças sejam criadas no segmento. Para obter mais informações, consulte [Como Habilitar Estilos Visuais em um Aplicativo Híbrido](how-to-enable-visual-styles-in-a-hybrid-application.md).  
  
<a name="licensed_controls"></a>
## <a name="licensed-controls"></a>Controles licenciados  
 Controles licenciados do Windows Forms que exibem informações de licenciamento em uma caixa de mensagem para o usuário podem causar comportamento inesperado para um aplicativo híbrido. Alguns controles licenciados mostram uma caixa de diálogo em resposta a lidar com a criação. Por exemplo, um controle licenciado pode informar ao usuário que uma licença é necessária ou se o usuário tem três restantes avaliação usos do controle.  
  
 O <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento deriva <xref:System.Windows.Interop.HwndHost> da classe, e a alça do controle <xref:System.Windows.Forms.Integration.WindowsFormsHost.BuildWindowCore%2A> da criança é criada dentro do método. A <xref:System.Windows.Interop.HwndHost> classe não permite que mensagens <xref:System.Windows.Forms.Integration.WindowsFormsHost.BuildWindowCore%2A> sejam processadas no método, mas exibir uma caixa de diálogo faz com que mensagens sejam enviadas. Para habilitar esse cenário <xref:System.Windows.Forms.Control.CreateControl%2A?displayProperty=nameWithType> de licenciamento, chame o <xref:System.Windows.Forms.Integration.WindowsFormsHost> método no controle antes de atribuí-lo como filho do elemento.  
  
<a name="wpf_designer"></a>
## <a name="wpf-designer"></a>WPF Designer  
 Você pode projetar seu conteúdo WPF usando o WPF Designer for Visual Studio. As seções a seguir listam alguns problemas comuns que podem ocorrer ao criar aplicativos híbridos com o WPF Designer.  
  
### <a name="backcolortransparent-is-ignored-at-design-time"></a>BackColorTransparent é ignorado no momento de design  
 A <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> propriedade pode não funcionar como esperado na hora do projeto.  
  
 Se um controle WPF não estiver em um pai visível, o tempo de execução do WPF ignorará o <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> valor. A razão <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> pela qual isso <xref:System.Windows.Forms.Integration.ElementHost> pode ser ignorado <xref:System.AppDomain>é porque o objeto é criado em um separado . No entanto, quando <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> você executa o aplicativo, funciona como esperado.  
  
### <a name="design-time-error-list-appears-when-the-obj-folder-is-deleted"></a>Lista de erros do momento de design é exibida quando a pasta obj é excluída  
 Se a pasta obj for excluída, a lista de erros de tempo de Design será exibida.  
  
 Quando você <xref:System.Windows.Forms.Integration.ElementHost>projeta o uso, o Windows Forms Designer usa arquivos gerados na pasta Debug ou Release dentro da pasta obj do seu projeto. Se você excluir esses arquivos, será exibida a lista de erros do momento de design. Para corrigir esse problema, recompile o projeto. Par amais informações, consulte [Erros de tempo de design no Designer de Formulários do Windows](../../winforms/controls/design-time-errors-in-the-windows-forms-designer.md).  
  
<a name="elementhost_and_ime"></a>
## <a name="elementhost-and-ime"></a>ElementHost e IME  
 Os controles WPF hospedados em um <xref:System.Windows.Forms.Integration.ElementHost> <xref:System.Windows.Forms.Control.ImeMode%2A> atualmente não suportam a propriedade. As <xref:System.Windows.Forms.Control.ImeMode%2A> alterações serão ignoradas pelos controles hospedados.  
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Interoperabilidade no WPF Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb628658(v=vs.100))
- [Windows Forms e arquitetura de entrada da interoperabilidade do WPF](windows-forms-and-wpf-interoperability-input-architecture.md)
- [Como habilitar estilos visuais em um aplicativo híbrido](how-to-enable-visual-styles-in-a-hybrid-application.md)
- [Considerações sobre o layout do elemento WindowsFormsHost](layout-considerations-for-the-windowsformshost-element.md)
- [Windows Forms e mapeamento de propriedade do WPF](windows-forms-and-wpf-property-mapping.md)
- [Erros de tempo de design no Designer de Formulários do Windows](../../winforms/controls/design-time-errors-in-the-windows-forms-designer.md)
- [Migração e Interoperabilidade](migration-and-interoperability.md)
