---
title: Windows Forms e mapeamento de propriedade do WPF
titleSuffix: ''
ms.date: 03/30/2017
helpviewer_keywords:
- property mapping [WPF interoperability]
- Windows Forms [WPF], interoperability with
- Windows Forms [WPF], WPF interoperation
- interoperability [WPF], Windows Forms
- WindowsFormsHost element property mapping [WPF]
ms.assetid: 999d8298-9c04-467d-a453-86e41002057d
ms.openlocfilehash: 45d86ac1b65306c8f404f9cea1e663b67128ebc4
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794069"
---
# <a name="windows-forms-and-wpf-property-mapping"></a>Windows Forms e mapeamento de propriedade do WPF
As tecnologias de Windows Forms e [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] têm dois modelos de propriedade semelhantes, mas diferentes. O *mapeamento de propriedade* dá suporte à interoperação entre as duas arquiteturas e fornece os seguintes recursos:  
  
- Facilita o mapeamento de alterações de propriedades relevantes no ambiente de host para o elemento ou o controle hospedado.  
  
- Fornece tratamento padrão para mapeamento das propriedades mais comumente usadas.  
  
- Permite remoção, substituição ou extensão fácil das propriedades padrão.  
  
- Garante que as alterações de valor da propriedade no host sejam automaticamente detectadas e convertidas no elemento ou controle hospedado.  
  
> [!NOTE]
> Os eventos de alteração de propriedade não são propagados até o controle de hospedagem ou hierarquia de elementos. A conversão de propriedade não é executada se o valor de uma propriedade local não for alterado devido à configuração direta, estilos, herança, vinculação de dados ou outros mecanismos que alterem o valor da propriedade.  
  
 Use a propriedade <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A> no elemento <xref:System.Windows.Forms.Integration.WindowsFormsHost> e a propriedade <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A> no controle <xref:System.Windows.Forms.Integration.ElementHost> para acessar o mapeamento de propriedade.  
  
## <a name="property-mapping-with-the-windowsformshost-element"></a>Mapeamento de propriedades do elemento WindowsFormsHost  
 O elemento <xref:System.Windows.Forms.Integration.WindowsFormsHost> converte as propriedades de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] padrão para seus equivalentes Windows Forms usando a tabela de tradução a seguir.  
  
|Hospedagem do Windows Presentation Foundation|Windows Forms|Comportamento de interoperação|  
|---------------------------------------------|-------------------|-----------------------------|  
|<xref:System.Windows.Controls.Control.Background%2A><br /><br /> (<xref:System.Windows.Media.Brush?displayProperty=nameWithType>)|<xref:System.Windows.Forms.Control.BackColor%2A><br /><br /> (<xref:System.Drawing.Color?displayProperty=nameWithType>)|O elemento <xref:System.Windows.Forms.Integration.WindowsFormsHost> define a propriedade <xref:System.Windows.Forms.Control.BackColor%2A> do controle hospedado e a propriedade <xref:System.Windows.Forms.Control.BackgroundImage%2A> do controle hospedado. O mapeamento é executado usando as seguintes regras:<br /><br /> -Se <xref:System.Windows.Controls.Control.Background%2A> for uma cor sólida, ela será convertida e usada para definir a propriedade <xref:System.Windows.Forms.Control.BackColor%2A> do controle hospedado. A propriedade <xref:System.Windows.Forms.Control.BackColor%2A> não está definida no controle hospedado, pois o controle hospedado pode herdar o valor da propriedade <xref:System.Windows.Forms.Control.BackColor%2A>. **Observação:** o controle hospedado não dá suporte à transparência. Qualquer cor atribuída a <xref:System.Windows.Forms.Control.BackColor%2A> deve ser totalmente opaca, com um valor alfa de 0xFF. <br /><br /> -Se <xref:System.Windows.Controls.Control.Background%2A> não for uma cor sólida, o controle de <xref:System.Windows.Forms.Integration.WindowsFormsHost> criará um bitmap da propriedade <xref:System.Windows.Controls.Control.Background%2A>. O controle de <xref:System.Windows.Forms.Integration.WindowsFormsHost> atribui esse bitmap à propriedade <xref:System.Windows.Forms.Control.BackgroundImage%2A> do controle hospedado. Isso proporciona um efeito que é semelhante à transparência. **Observação:**  Você pode substituir esse comportamento ou remover o mapeamento da propriedade <xref:System.Windows.Controls.Control.Background%2A>.|  
|<xref:System.Windows.FrameworkElement.Cursor%2A>|<xref:System.Windows.Forms.Control.Cursor%2A>|Se o mapeamento padrão não tiver sido reatribuído, <xref:System.Windows.Forms.Integration.WindowsFormsHost> controle atravessará sua hierarquia ancestral até encontrar um ancestral com sua propriedade <xref:System.Windows.FrameworkElement.Cursor%2A> definida. Esse valor é convertido para o próximo cursor de Windows Forms correspondente.<br /><br /> Se o mapeamento padrão para a propriedade <xref:System.Windows.FrameworkElement.ForceCursor%2A> não tiver sido reatribuído, a passagem será interrompida no primeiro ancestral com <xref:System.Windows.FrameworkElement.ForceCursor%2A> definido como `true`.|  
|<xref:System.Windows.FrameworkElement.FlowDirection%2A><br /><br /> (<xref:System.Windows.FlowDirection?displayProperty=nameWithType>)|<xref:System.Windows.Forms.Control.RightToLeft%2A><br /><br /> (<xref:System.Windows.Forms.RightToLeft?displayProperty=nameWithType>)|<xref:System.Windows.FlowDirection.LeftToRight> mapeia para <xref:System.Windows.Forms.RightToLeft.No>.<br /><br /> <xref:System.Windows.FlowDirection.RightToLeft> mapeia para <xref:System.Windows.Forms.RightToLeft.Yes>.<br /><br /> <xref:System.Windows.Forms.RightToLeft.Inherit> não está mapeado.<br /><br /> <xref:System.Windows.FlowDirection.RightToLeft?displayProperty=nameWithType> mapeia para <xref:System.Windows.Forms.RightToLeft.Yes?displayProperty=nameWithType>.|  
|<xref:System.Windows.Controls.Control.FontStyle%2A>|<xref:System.Drawing.Font.Style%2A> no <xref:System.Drawing.Font?displayProperty=nameWithType> do controle hospedado|O conjunto de propriedades [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] é convertido em um <xref:System.Drawing.Font>correspondente. Quando uma dessas propriedades é alterada, um novo <xref:System.Drawing.Font> é criado. Para <xref:System.Windows.FontStyles.Normal%2A>: <xref:System.Drawing.FontStyle.Italic> está desabilitado. Para <xref:System.Windows.FontStyles.Italic%2A> ou <xref:System.Windows.FontStyles.Oblique%2A>: <xref:System.Drawing.FontStyle.Italic> está habilitado.|  
|<xref:System.Windows.Controls.Control.FontWeight%2A>|<xref:System.Drawing.Font.Style%2A> no <xref:System.Drawing.Font?displayProperty=nameWithType> do controle hospedado|O conjunto de propriedades [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] é convertido em um <xref:System.Drawing.Font>correspondente. Quando uma dessas propriedades é alterada, um novo <xref:System.Drawing.Font> é criado. Para <xref:System.Windows.FontWeights.Black%2A>, <xref:System.Windows.FontWeights.Bold%2A>, <xref:System.Windows.FontWeights.DemiBold%2A>, <xref:System.Windows.FontWeights.ExtraBold%2A>, <xref:System.Windows.FontWeights.Heavy%2A>, <xref:System.Windows.FontWeights.Medium%2A>, <xref:System.Windows.FontWeights.SemiBold%2A>ou <xref:System.Windows.FontWeights.UltraBold%2A>: <xref:System.Drawing.FontStyle.Bold> está habilitado. Para <xref:System.Windows.FontWeights.ExtraLight%2A>, <xref:System.Windows.FontWeights.Light%2A>, <xref:System.Windows.FontWeights.Normal%2A>, <xref:System.Windows.FontWeights.Regular%2A>, <xref:System.Windows.FontWeights.Thin%2A>ou <xref:System.Windows.FontWeights.UltraLight%2A>: <xref:System.Drawing.FontStyle.Bold> está desabilitado.|  
|<xref:System.Windows.Controls.Control.FontFamily%2A><br /><br /> <xref:System.Windows.Controls.Control.FontSize%2A><br /><br /> <xref:System.Windows.Controls.Control.FontStretch%2A><br /><br /> <xref:System.Windows.Controls.Control.FontStyle%2A><br /><br /> <xref:System.Windows.Controls.Control.FontWeight%2A>|<xref:System.Windows.Forms.Control.Font%2A><br /><br /> (<xref:System.Drawing.Font?displayProperty=nameWithType>)|O conjunto de propriedades [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] é convertido em um <xref:System.Drawing.Font>correspondente. Quando uma dessas propriedades é alterada, um novo <xref:System.Drawing.Font> é criado. O controle de Windows Forms hospedado redimensiona com base no tamanho da fonte.<br /><br /> O tamanho da fonte em [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] é expresso como um sexto e igual a uma polegada e, em Windows Forms como um Seventy-segundo de uma polegada. A conversão correspondente é:<br /><br /> Tamanho da fonte de Windows Forms = [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tamanho da fonte * 72,0/96,0.|  
|<xref:System.Windows.Controls.Control.Foreground%2A><br /><br /> (<xref:System.Windows.Media.Brush?displayProperty=nameWithType>)|<xref:System.Windows.Forms.Control.ForeColor%2A><br /><br /> (<xref:System.Drawing.Color?displayProperty=nameWithType>)|O mapeamento da propriedade <xref:System.Windows.Controls.Control.Foreground%2A> é executado usando as seguintes regras:<br /><br /> -Se <xref:System.Windows.Controls.Control.Foreground%2A> for um <xref:System.Windows.Media.SolidColorBrush>, use <xref:System.Windows.Media.SolidColorBrush.Color%2A> para <xref:System.Windows.Forms.Control.ForeColor%2A>.<br />-Se <xref:System.Windows.Controls.Control.Foreground%2A> for uma <xref:System.Windows.Media.GradientBrush>, use a cor da <xref:System.Windows.Media.GradientStop> com o menor valor de deslocamento para <xref:System.Windows.Forms.Control.ForeColor%2A>.<br />-Para qualquer outro tipo de <xref:System.Windows.Media.Brush>, deixe <xref:System.Windows.Forms.Control.ForeColor%2A> inalterado. Isso significa que o padrão é usado.|  
|<xref:System.Windows.UIElement.IsEnabled%2A>|<xref:System.Windows.Forms.Control.Enabled%2A>|Quando <xref:System.Windows.UIElement.IsEnabled%2A> é definido, o elemento <xref:System.Windows.Forms.Integration.WindowsFormsHost> define a propriedade <xref:System.Windows.Forms.Control.Enabled%2A> no controle hospedado.|  
|<xref:System.Windows.Controls.Control.Padding%2A>|<xref:System.Windows.Forms.Control.Padding%2A>|Todos os quatro valores da propriedade <xref:System.Windows.Forms.Control.Padding%2A> no controle de Windows Forms hospedado são definidos com o mesmo valor de <xref:System.Windows.Thickness>.<br /><br /> -Valores maiores que <xref:System.Int32.MaxValue> são definidos como <xref:System.Int32.MaxValue>.<br />-Valores menores que <xref:System.Int32.MinValue> são definidos como <xref:System.Int32.MinValue>.|  
|<xref:System.Windows.UIElement.Visibility%2A>|<xref:System.Windows.Forms.Control.Visible%2A>|-   <xref:System.Windows.Visibility.Visible> mapeia para <xref:System.Windows.Forms.Control.Visible%2A> = `true`. O controle de Windows Forms hospedado é visível. Não é recomendável definir explicitamente a propriedade <xref:System.Windows.Forms.Control.Visible%2A> no controle hospedado como `false`.<br />-   <xref:System.Windows.Visibility.Collapsed> mapeia para <xref:System.Windows.Forms.Control.Visible%2A> = `true` ou `false`. O controle de Windows Forms hospedado não é desenhado e sua área é recolhida.<br />-   <xref:System.Windows.Visibility.Hidden>: o controle de Windows Forms hospedado ocupa espaço no layout, mas não está visível. Nesse caso, a propriedade <xref:System.Windows.Forms.Control.Visible%2A> é definida como `true`. Não é recomendável definir explicitamente a propriedade <xref:System.Windows.Forms.Control.Visible%2A> no controle hospedado como `false`.|  
  
 As propriedades anexadas em elementos de contêiner são totalmente suportadas pelo elemento <xref:System.Windows.Forms.Integration.WindowsFormsHost>.  
  
 Para mais informações, consulte [Instruções passo a passo: mapeando propriedades usando o elemento WindowsFormsHost](walkthrough-mapping-properties-using-the-windowsformshost-element.md).  
  
## <a name="updates-to-parent-properties"></a>Atualizações para propriedades pai  
 As alterações na maioria das propriedades pai ocasionam notificações para o controle filho hospedado. A lista a seguir descreve as propriedades que não ocasionam notificações quando seus valores são alterados.  
  
- <xref:System.Windows.Controls.Control.Background%2A>  
  
- <xref:System.Windows.FrameworkElement.Cursor%2A>  
  
- <xref:System.Windows.FrameworkElement.ForceCursor%2A>  
  
- <xref:System.Windows.UIElement.Visibility%2A>  
  
 Por exemplo, se você alterar o valor da propriedade <xref:System.Windows.Controls.Control.Background%2A> do elemento <xref:System.Windows.Forms.Integration.WindowsFormsHost>, a propriedade <xref:System.Windows.Forms.Control.BackColor%2A> do controle hospedado não será alterada.  
  
## <a name="property-mapping-with-the-elementhost-control"></a>Mapeamento de propriedade com o controle ElementHost  
 As propriedades a seguir fornecem notificação de alteração interna. Não chame o método <xref:System.Windows.FrameworkElement.OnPropertyChanged%2A> ao mapear essas propriedades:  
  
- Dimensionamento Automático  
  
- BackColor  
  
- BackgroundImage  
  
- BackgroundImageLayout  
  
- BindingContext  
  
- CausesValidation  
  
- ContextMenu  
  
- ContextMenuStrip  
  
- Cursor  
  
- Encaixar  
  
- Enabled  
  
- Fonte  
  
- ForeColor  
  
- Local  
  
- Margem  
  
- Enchimento  
  
- Pai  
  
- Região  
  
- DaDireitaParaaEsquerda  
  
- Tamanho  
  
- TabIndex  
  
- TabStop  
  
- Texto  
  
- Visível  
  
 O controle de <xref:System.Windows.Forms.Integration.ElementHost> converte Propriedades de Windows Forms padrão para seus equivalentes [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] usando a tabela de tradução a seguir.  
  
 Para mais informações, consulte [Instruções passo a passo: mapeando propriedades usando o controle ElementHost](walkthrough-mapping-properties-using-the-elementhost-control.md).  
  
|Hospedagem dos Windows Forms|Windows Presentation Foundation|Comportamento de interoperação|  
|---------------------------|-------------------------------------|-----------------------------|  
|<xref:System.Windows.Forms.Control.BackColor%2A><br /><br /> (<xref:System.Drawing.Color?displayProperty=nameWithType>)|<xref:System.Windows.Controls.Control.Background%2A><br /><br /> (<xref:System.Windows.Media.Brush?displayProperty=nameWithType>) no elemento hospedado|Definir essa propriedade força um redesenho com um <xref:System.Windows.Media.ImageBrush>. Se a propriedade <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> for definida como `false` (o valor padrão), essa <xref:System.Windows.Media.ImageBrush> será baseada na aparência do controle de <xref:System.Windows.Forms.Integration.ElementHost>, incluindo suas <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.BackgroundImage%2A>, propriedades de <xref:System.Windows.Forms.Control.BackgroundImageLayout%2A> e quaisquer manipuladores de pintura anexados.<br /><br /> Se a propriedade <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> for definida como `true`, a <xref:System.Windows.Media.ImageBrush> será baseada na aparência do pai do controle de <xref:System.Windows.Forms.Integration.ElementHost>, incluindo as propriedades <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.BackgroundImage%2A>, <xref:System.Windows.Forms.Control.BackgroundImageLayout%2A> do pai e os manipuladores de pintura anexados.|  
|<xref:System.Windows.Forms.Control.BackgroundImage%2A><br /><br /> (<xref:System.Drawing.Image?displayProperty=nameWithType>)|<xref:System.Windows.Controls.Control.Background%2A><br /><br /> (<xref:System.Windows.Media.Brush?displayProperty=nameWithType>) no elemento hospedado|Definir essa propriedade causa o mesmo comportamento descrito para o mapeamento de <xref:System.Windows.Forms.Control.BackColor%2A>.|  
|<xref:System.Windows.Forms.Control.BackgroundImageLayout%2A>|<xref:System.Windows.Controls.Control.Background%2A><br /><br /> (<xref:System.Windows.Media.Brush?displayProperty=nameWithType>) no elemento hospedado|Definir essa propriedade causa o mesmo comportamento descrito para o mapeamento de <xref:System.Windows.Forms.Control.BackColor%2A>.|  
|<xref:System.Windows.Forms.Control.Cursor%2A><br /><br /> (<xref:System.Windows.Forms.Cursor?displayProperty=nameWithType>)|<xref:System.Windows.FrameworkElement.Cursor%2A><br /><br /> (<xref:System.Windows.Input.Cursor?displayProperty=nameWithType>)|O cursor padrão Windows Forms é convertido para o cursor de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] padrão correspondente. Se o Windows Forms não for um cursor padrão, o padrão será atribuído.|  
|<xref:System.Windows.Forms.Control.Enabled%2A>|<xref:System.Windows.UIElement.IsEnabled%2A>|Quando <xref:System.Windows.Forms.Control.Enabled%2A> é definido, o controle <xref:System.Windows.Forms.Integration.ElementHost> define a propriedade <xref:System.Windows.UIElement.IsEnabled%2A> no elemento hospedado.|  
|<xref:System.Windows.Forms.Control.Font%2A><br /><br /> (<xref:System.Drawing.Font?displayProperty=nameWithType>)|<xref:System.Windows.Controls.Control.FontFamily%2A><br /><br /> <xref:System.Windows.Controls.Control.FontSize%2A><br /><br /> <xref:System.Windows.Controls.Control.FontStretch%2A><br /><br /> <xref:System.Windows.Controls.Control.FontStyle%2A><br /><br /> <xref:System.Windows.Controls.Control.FontWeight%2A>|O valor de <xref:System.Windows.Forms.Control.Font%2A> é convertido em um conjunto correspondente de propriedades de fonte de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].|  
|<xref:System.Drawing.Font.Bold%2A>|<xref:System.Windows.Controls.Control.FontWeight%2A> no elemento hospedado|Se <xref:System.Drawing.Font.Bold%2A> é `true`, <xref:System.Windows.Controls.Control.FontWeight%2A> é definido como <xref:System.Windows.FontWeights.Bold%2A>.<br /><br /> Se <xref:System.Drawing.Font.Bold%2A> é `false`, <xref:System.Windows.Controls.Control.FontWeight%2A> é definido como <xref:System.Windows.FontWeights.Normal%2A>.|  
|<xref:System.Drawing.Font.Italic%2A>|<xref:System.Windows.Controls.Control.FontStyle%2A> no elemento hospedado|Se <xref:System.Drawing.Font.Italic%2A> é `true`, <xref:System.Windows.Controls.Control.FontStyle%2A> é definido como <xref:System.Windows.FontStyles.Italic%2A>.<br /><br /> Se <xref:System.Drawing.Font.Italic%2A> é `false`, <xref:System.Windows.Controls.Control.FontStyle%2A> é definido como <xref:System.Windows.FontStyles.Normal%2A>.|  
|<xref:System.Drawing.Font.Strikeout%2A>|<xref:System.Windows.TextDecorations> no elemento hospedado|Aplica-se somente ao hospedar um controle de <xref:System.Windows.Controls.TextBlock>.|  
|<xref:System.Drawing.Font.Underline%2A>|<xref:System.Windows.TextDecorations> no elemento hospedado|Aplica-se somente ao hospedar um controle de <xref:System.Windows.Controls.TextBlock>.|  
|<xref:System.Windows.Forms.Control.RightToLeft%2A><br /><br /> (<xref:System.Windows.Forms.RightToLeft?displayProperty=nameWithType>)|<xref:System.Windows.FrameworkElement.FlowDirection%2A><br /><br /> (<xref:System.Windows.FlowDirection>)|<xref:System.Windows.Forms.RightToLeft.No> mapeia para <xref:System.Windows.FlowDirection.LeftToRight>.<br /><br /> <xref:System.Windows.Forms.RightToLeft.Yes> mapeia para <xref:System.Windows.FlowDirection.RightToLeft>.|  
|<xref:System.Windows.Forms.Control.Visible%2A>|<xref:System.Windows.UIElement.Visibility%2A>|O controle <xref:System.Windows.Forms.Integration.ElementHost> define a propriedade <xref:System.Windows.UIElement.Visibility%2A> no elemento hospedado usando as seguintes regras:<br /><br /> -   <xref:System.Windows.Forms.Control.Visible%2A> = `true` mapas para <xref:System.Windows.Visibility.Visible>.<br />-   <xref:System.Windows.Forms.Control.Visible%2A> = `false` mapas para <xref:System.Windows.Visibility.Hidden>.|  
  
## <a name="see-also"></a>Veja também

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Interoperação Win32 e WPF](wpf-and-win32-interoperation.md)
- [Interoperação do WPF e do Windows Forms](wpf-and-windows-forms-interoperation.md)
- [Passo a passo: mapeando propriedades usando o elemento WindowsFormsHost](walkthrough-mapping-properties-using-the-windowsformshost-element.md)
- [Passo a passo: mapeando propriedades usando o controle ElementHost](walkthrough-mapping-properties-using-the-elementhost-control.md)
