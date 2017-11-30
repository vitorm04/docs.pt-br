---
title: Windows Forms e mapeamento de propriedade do WPF
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- property mapping [WPF interoperability]
- Windows Forms [WPF], interoperability with
- Windows Forms [WPF], WPF interoperation
- interoperability [WPF], Windows Forms
- WindowsFormsHost element property mapping [WPF]
ms.assetid: 999d8298-9c04-467d-a453-86e41002057d
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1a0af1015747e2f27b19c2cac2c896dd60214264
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="windows-forms-and-wpf-property-mapping"></a>Windows Forms e mapeamento de propriedade do WPF
As tecnologias [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] e [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] têm dois modelos de propriedade semelhantes, mas diferentes. O *mapeamento de propriedade* dá suporte à interoperação entre as duas arquiteturas e fornece os seguintes recursos:  
  
-   Facilita o mapeamento de alterações de propriedades relevantes no ambiente de host para o elemento ou o controle hospedado.  
  
-   Fornece tratamento padrão para mapeamento das propriedades mais comumente usadas.  
  
-   Permite remoção, substituição ou extensão fácil das propriedades padrão.  
  
-   Garante que as alterações de valor da propriedade no host sejam automaticamente detectadas e convertidas no elemento ou controle hospedado.  
  
> [!NOTE]
>  Os eventos de alteração de propriedade não são propagados até o controle de hospedagem ou hierarquia de elementos. A conversão de propriedade não é executada se o valor de uma propriedade local não for alterado devido à configuração direta, estilos, herança, vinculação de dados ou outros mecanismos que alterem o valor da propriedade.  
  
 Use o <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A> propriedade no <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento e o <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A> propriedade <xref:System.Windows.Forms.Integration.ElementHost> controle para acessar o mapeamento de propriedade.  
  
## <a name="property-mapping-with-the-windowsformshost-element"></a>Mapeamento de propriedades do elemento WindowsFormsHost  
 O <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento converte padrão [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] propriedades para seus [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] equivalentes usando a seguinte tabela de conversão.  
  
|Hospedagem do Windows Presentation Foundation|Windows Forms|Comportamento de interoperação|  
|---------------------------------------------|-------------------|-----------------------------|  
|<xref:System.Windows.Controls.Control.Background%2A><br /><br /> (<xref:System.Windows.Media.Brush?displayProperty=nameWithType>)|<xref:System.Windows.Forms.Control.BackColor%2A><br /><br /> (<xref:System.Drawing.Color?displayProperty=nameWithType>)|O <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento define o <xref:System.Windows.Forms.Control.BackColor%2A> propriedade do controle hospedado e a <xref:System.Windows.Forms.Control.BackgroundImage%2A> propriedade do controle hospedado. O mapeamento é executado usando as seguintes regras:<br /><br /> -Se <xref:System.Windows.Controls.Control.Background%2A> é uma cor sólida, ele é convertido e usado para definir o <xref:System.Windows.Forms.Control.BackColor%2A> propriedade do controle hospedado. O <xref:System.Windows.Forms.Control.BackColor%2A> propriedade não está definida no controle hospedado, porque o controle hospedado pode herdar o valor da <xref:System.Windows.Forms.Control.BackColor%2A> propriedade. **Observação:** o controle hospedado não dá suporte à transparência. Qualquer cor atribuída a <xref:System.Windows.Forms.Control.BackColor%2A> deve ser totalmente opaca, com um valor alfa de 0xFF. <br /><br /> -Se <xref:System.Windows.Controls.Control.Background%2A> não é uma cor sólida, o <xref:System.Windows.Forms.Integration.WindowsFormsHost> controle cria um bitmap a partir de <xref:System.Windows.Controls.Control.Background%2A> propriedade. O <xref:System.Windows.Forms.Integration.WindowsFormsHost> controle atribui esse bitmap para o <xref:System.Windows.Forms.Control.BackgroundImage%2A> propriedade do controle hospedado. Isso proporciona um efeito que é semelhante à transparência. **Observação:** você pode substituir esse comportamento ou você pode remover o <xref:System.Windows.Controls.Control.Background%2A> mapeamento de propriedade.|  
|<xref:System.Windows.FrameworkElement.Cursor%2A>|<xref:System.Windows.Forms.Control.Cursor%2A>|Se o mapeamento padrão não foi reatribuído, <xref:System.Windows.Forms.Integration.WindowsFormsHost> controle percorre a hierarquia de seu predecessor até encontrar um ancestral com seu <xref:System.Windows.FrameworkElement.Cursor%2A> conjunto de propriedades. Esse valor é convertido para o cursor [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] mais próximo correspondente.<br /><br /> Se o mapeamento padrão para o <xref:System.Windows.FrameworkElement.ForceCursor%2A> propriedade não foi reatribuída, passagem para sobre o primeiro predecessor com <xref:System.Windows.FrameworkElement.ForceCursor%2A> definido como `true`.|  
|<xref:System.Windows.FrameworkElement.FlowDirection%2A><br /><br /> (<xref:System.Windows.FlowDirection?displayProperty=nameWithType>)|<xref:System.Windows.Forms.Control.RightToLeft%2A><br /><br /> (<xref:System.Windows.Forms.RightToLeft?displayProperty=nameWithType>)|<xref:System.Windows.FlowDirection.LeftToRight>mapeia para <xref:System.Windows.Forms.RightToLeft.No>.<br /><br /> <xref:System.Windows.FlowDirection.RightToLeft>mapeia para <xref:System.Windows.Forms.RightToLeft.Yes>.<br /><br /> <xref:System.Windows.Forms.RightToLeft.Inherit>não é mapeado.<br /><br /> <xref:System.Windows.FlowDirection.RightToLeft?displayProperty=nameWithType>mapeia para <xref:System.Windows.Forms.RightToLeft.Yes?displayProperty=nameWithType>.|  
|<xref:System.Windows.Controls.Control.FontStyle%2A>|<xref:System.Drawing.Font.Style%2A>o controle hospedado<xref:System.Drawing.Font?displayProperty=nameWithType>|O conjunto de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] propriedades é convertida em um correspondente <xref:System.Drawing.Font>. Quando uma dessas propriedades for alterada, um novo <xref:System.Drawing.Font> é criado. Para <xref:System.Windows.FontStyles.Normal%2A>: <xref:System.Drawing.FontStyle.Italic> está desabilitado. Para <xref:System.Windows.FontStyles.Italic%2A> ou <xref:System.Windows.FontStyles.Oblique%2A>: <xref:System.Drawing.FontStyle.Italic> está habilitado.|  
|<xref:System.Windows.Controls.Control.FontWeight%2A>|<xref:System.Drawing.Font.Style%2A>o controle hospedado<xref:System.Drawing.Font?displayProperty=nameWithType>|O conjunto de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] propriedades é convertida em um correspondente <xref:System.Drawing.Font>. Quando uma dessas propriedades for alterada, um novo <xref:System.Drawing.Font> é criado. Para <xref:System.Windows.FontWeights.Black%2A>, <xref:System.Windows.FontWeights.Bold%2A>, <xref:System.Windows.FontWeights.DemiBold%2A>, <xref:System.Windows.FontWeights.ExtraBold%2A>, <xref:System.Windows.FontWeights.Heavy%2A>, <xref:System.Windows.FontWeights.Medium%2A>, <xref:System.Windows.FontWeights.SemiBold%2A>, ou <xref:System.Windows.FontWeights.UltraBold%2A>: <xref:System.Drawing.FontStyle.Bold> está habilitado. Para <xref:System.Windows.FontWeights.ExtraLight%2A>, <xref:System.Windows.FontWeights.Light%2A>, <xref:System.Windows.FontWeights.Normal%2A>, <xref:System.Windows.FontWeights.Regular%2A>, <xref:System.Windows.FontWeights.Thin%2A>, ou <xref:System.Windows.FontWeights.UltraLight%2A>: <xref:System.Drawing.FontStyle.Bold> está desabilitado.|  
|<xref:System.Windows.Controls.Control.FontFamily%2A><br /><br /> <xref:System.Windows.Controls.Control.FontSize%2A><br /><br /> <xref:System.Windows.Controls.Control.FontStretch%2A><br /><br /> <xref:System.Windows.Controls.Control.FontStyle%2A><br /><br /> <xref:System.Windows.Controls.Control.FontWeight%2A>|<xref:System.Windows.Forms.Control.Font%2A><br /><br /> (<xref:System.Drawing.Font?displayProperty=nameWithType>)|O conjunto de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] propriedades é convertida em um correspondente <xref:System.Drawing.Font>. Quando uma dessas propriedades for alterada, um novo <xref:System.Drawing.Font> é criado. O controle [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] hospedado será redimensionado com base no tamanho da fonte.<br /><br /> O tamanho da fonte em [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] é expresso como um sobre noventa e seis avos de uma polegada e em [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] como um sobre setenta e dois avos de uma polegada. A conversão correspondente é:<br /><br /> [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] tamanho da fonte = [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tamanho da fonte * 72/96.|  
|<xref:System.Windows.Controls.Control.Foreground%2A><br /><br /> (<xref:System.Windows.Media.Brush?displayProperty=nameWithType>)|<xref:System.Windows.Forms.Control.ForeColor%2A><br /><br /> (<xref:System.Drawing.Color?displayProperty=nameWithType>)|O <xref:System.Windows.Controls.Control.Foreground%2A> mapeamento de propriedade é feito usando as seguintes regras:<br /><br /> -Se <xref:System.Windows.Controls.Control.Foreground%2A> é um <xref:System.Windows.Media.SolidColorBrush>, use <xref:System.Windows.Media.SolidColorBrush.Color%2A> para <xref:System.Windows.Forms.Control.ForeColor%2A>.<br />-Se <xref:System.Windows.Controls.Control.Foreground%2A> é um <xref:System.Windows.Media.GradientBrush>, use a cor de <xref:System.Windows.Media.GradientStop> com o menor valor de deslocamento para <xref:System.Windows.Forms.Control.ForeColor%2A>.<br />-Para qualquer outro <xref:System.Windows.Media.Brush> digite, deixe <xref:System.Windows.Forms.Control.ForeColor%2A> inalterado. Isso significa que o padrão é usado.|  
|<xref:System.Windows.UIElement.IsEnabled%2A>|<xref:System.Windows.Forms.Control.Enabled%2A>|Quando <xref:System.Windows.UIElement.IsEnabled%2A> for definida, <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento define o <xref:System.Windows.Forms.Control.Enabled%2A> propriedade no controle hospedado.|  
|<xref:System.Windows.Controls.Control.Padding%2A>|<xref:System.Windows.Forms.Control.Padding%2A>|Todos os quatro valores da <xref:System.Windows.Forms.Control.Padding%2A> propriedade hospedado [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controle são definidos para o mesmo <xref:System.Windows.Thickness> valor.<br /><br /> -Os valores maiores que <xref:System.Int32.MaxValue> são definidos como <xref:System.Int32.MaxValue>.<br />-Valores inferiores <xref:System.Int32.MinValue> são definidos como <xref:System.Int32.MinValue>.|  
|<xref:System.Windows.UIElement.Visibility%2A>|<xref:System.Windows.Forms.Control.Visible%2A>|-   <xref:System.Windows.Visibility.Visible>mapeia para <xref:System.Windows.Forms.Control.Visible%2A>  =  `true`. O controle [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] hospedado é visível. Definir explicitamente o <xref:System.Windows.Forms.Control.Visible%2A> propriedade no controle hospedado para `false` não é recomendado.<br />-   <xref:System.Windows.Visibility.Collapsed>mapeia para <xref:System.Windows.Forms.Control.Visible%2A>  =  `true` ou `false`. O controle [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] hospedado não é desenhado e sua área é recolhida.<br />-   <xref:System.Windows.Visibility.Hidden>: O hospedado [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ocupam espaço no layout do controle, mas não está visível. Nesse caso, o <xref:System.Windows.Forms.Control.Visible%2A> está definida como `true`. Definir explicitamente o <xref:System.Windows.Forms.Control.Visible%2A> propriedade no controle hospedado para `false` não é recomendado.|  
  
 Propriedades anexadas em elementos de contêiner têm suporte total a <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento.  
  
 Para mais informações, consulte [Instruções passo a passo: mapeando propriedades usando o elemento WindowsFormsHost](../../../../docs/framework/wpf/advanced/walkthrough-mapping-properties-using-the-windowsformshost-element.md).  
  
## <a name="updates-to-parent-properties"></a>Atualizações para propriedades pai  
 As alterações na maioria das propriedades pai ocasionam notificações para o controle filho hospedado. A lista a seguir descreve as propriedades que não ocasionam notificações quando seus valores são alterados.  
  
-   <xref:System.Windows.Controls.Control.Background%2A>  
  
-   <xref:System.Windows.FrameworkElement.Cursor%2A>  
  
-   <xref:System.Windows.FrameworkElement.ForceCursor%2A>  
  
-   <xref:System.Windows.UIElement.Visibility%2A>  
  
 Por exemplo, se você alterar o valor da <xref:System.Windows.Controls.Control.Background%2A> propriedade o <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento, o <xref:System.Windows.Forms.Control.BackColor%2A> não altera a propriedade do controle hospedado.  
  
## <a name="property-mapping-with-the-elementhost-control"></a>Mapeamento de propriedade com o controle ElementHost  
 As propriedades a seguir fornecem notificação de alteração interna. Não chame o <xref:System.Windows.FrameworkElement.OnPropertyChanged%2A> método quando você está mapeando essas propriedades:  
  
-   AutoSize  
  
-   BackColor  
  
-   BackgroundImage  
  
-   BackgroundImageLayout  
  
-   BindingContext  
  
-   CausesValidation  
  
-   ContextMenu  
  
-   ContextMenuStrip  
  
-   Cursor  
  
-   Encaixar  
  
-   Habilitada  
  
-   Fonte  
  
-   ForeColor  
  
-   Local  
  
-   Margem  
  
-   Enchimento  
  
-   Pai  
  
-   Região  
  
-   DaDireitaParaaEsquerda  
  
-   Tamanho  
  
-   TabIndex  
  
-   TabStop  
  
-   Texto  
  
-   Visível  
  
 O <xref:System.Windows.Forms.Integration.ElementHost> controle converte padrão [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] propriedades para seus [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] equivalentes usando a seguinte tabela de conversão.  
  
 Para mais informações, consulte [Instruções passo a passo: mapeando propriedades usando o controle ElementHost](../../../../docs/framework/wpf/advanced/walkthrough-mapping-properties-using-the-elementhost-control.md).  
  
|Hospedagem dos Windows Forms|Windows Presentation Foundation|Comportamento de interoperação|  
|---------------------------|-------------------------------------|-----------------------------|  
|<xref:System.Windows.Forms.Control.BackColor%2A><br /><br /> (<xref:System.Drawing.Color?displayProperty=nameWithType>)|<xref:System.Windows.Controls.Control.Background%2A><br /><br /> (<xref:System.Windows.Media.Brush?displayProperty=nameWithType>) no elemento hospedado|A definição dessa propriedade força um redesenho com um <xref:System.Windows.Media.ImageBrush>. Se o <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> está definida como `false` (o valor padrão), isso <xref:System.Windows.Media.ImageBrush> baseia-se na aparência do <xref:System.Windows.Forms.Integration.ElementHost> controlar, incluindo seu <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.BackgroundImage%2A>, <xref:System.Windows.Forms.Control.BackgroundImageLayout%2A> propriedades e qualquer pintura anexados manipuladores.<br /><br /> Se o <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> está definida como `true`, o <xref:System.Windows.Media.ImageBrush> baseia-se na aparência do <xref:System.Windows.Forms.Integration.ElementHost> pai do controle, incluindo o pai <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.BackgroundImage%2A>, <xref:System.Windows.Forms.Control.BackgroundImageLayout%2A> propriedades e qualquer pintura anexados manipuladores.|  
|<xref:System.Windows.Forms.Control.BackgroundImage%2A><br /><br /> (<xref:System.Drawing.Image?displayProperty=nameWithType>)|<xref:System.Windows.Controls.Control.Background%2A><br /><br /> (<xref:System.Windows.Media.Brush?displayProperty=nameWithType>) no elemento hospedado|A definição dessa propriedade faz com que o mesmo comportamento descrito para o <xref:System.Windows.Forms.Control.BackColor%2A> mapeamento.|  
|<xref:System.Windows.Forms.Control.BackgroundImageLayout%2A>|<xref:System.Windows.Controls.Control.Background%2A><br /><br /> (<xref:System.Windows.Media.Brush?displayProperty=nameWithType>) no elemento hospedado|A definição dessa propriedade faz com que o mesmo comportamento descrito para o <xref:System.Windows.Forms.Control.BackColor%2A> mapeamento.|  
|<xref:System.Windows.Forms.Control.Cursor%2A><br /><br /> (<xref:System.Windows.Forms.Cursor?displayProperty=nameWithType>)|<xref:System.Windows.FrameworkElement.Cursor%2A><br /><br /> (<xref:System.Windows.Input.Cursor?displayProperty=nameWithType>)|O cursor [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] padrão é convertido para os respectivos cursores [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] padrão. Se o [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] não for um cursor padrão, o padrão será designado.|  
|<xref:System.Windows.Forms.Control.Enabled%2A>|<xref:System.Windows.UIElement.IsEnabled%2A>|Quando <xref:System.Windows.Forms.Control.Enabled%2A> for definida, o <xref:System.Windows.Forms.Integration.ElementHost> conjuntos de controles de <xref:System.Windows.UIElement.IsEnabled%2A> propriedade no elemento hospedado.|  
|<xref:System.Windows.Forms.Control.Font%2A><br /><br /> (<xref:System.Drawing.Font?displayProperty=nameWithType>)|<xref:System.Windows.Controls.Control.FontFamily%2A><br /><br /> <xref:System.Windows.Controls.Control.FontSize%2A><br /><br /> <xref:System.Windows.Controls.Control.FontStretch%2A><br /><br /> <xref:System.Windows.Controls.Control.FontStyle%2A><br /><br /> <xref:System.Windows.Controls.Control.FontWeight%2A>|O <xref:System.Windows.Forms.Control.Font%2A> valor é convertido em um conjunto correspondente de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] propriedades de fonte.|  
|<xref:System.Drawing.Font.Bold%2A>|<xref:System.Windows.Controls.Control.FontWeight%2A>no elemento hospedado|Se <xref:System.Drawing.Font.Bold%2A> é `true`, <xref:System.Windows.Controls.Control.FontWeight%2A> é definido como <xref:System.Windows.FontWeights.Bold%2A>.<br /><br /> Se <xref:System.Drawing.Font.Bold%2A> é `false`, <xref:System.Windows.Controls.Control.FontWeight%2A> é definido como <xref:System.Windows.FontWeights.Normal%2A>.|  
|<xref:System.Drawing.Font.Italic%2A>|<xref:System.Windows.Controls.Control.FontStyle%2A>no elemento hospedado|Se <xref:System.Drawing.Font.Italic%2A> é `true`, <xref:System.Windows.Controls.Control.FontStyle%2A> é definido como <xref:System.Windows.FontStyles.Italic%2A>.<br /><br /> Se <xref:System.Drawing.Font.Italic%2A> é `false`, <xref:System.Windows.Controls.Control.FontStyle%2A> é definido como <xref:System.Windows.FontStyles.Normal%2A>.|  
|<xref:System.Drawing.Font.Strikeout%2A>|<xref:System.Windows.TextDecorations>no elemento hospedado|Aplica-se somente ao hospedar um <xref:System.Windows.Controls.TextBlock> controle.|  
|<xref:System.Drawing.Font.Underline%2A>|<xref:System.Windows.TextDecorations>no elemento hospedado|Aplica-se somente ao hospedar um <xref:System.Windows.Controls.TextBlock> controle.|  
|<xref:System.Windows.Forms.Control.RightToLeft%2A><br /><br /> (<xref:System.Windows.Forms.RightToLeft?displayProperty=nameWithType>)|<xref:System.Windows.FrameworkElement.FlowDirection%2A><br /><br /> (<xref:System.Windows.FlowDirection>)|<xref:System.Windows.Forms.RightToLeft.No>mapeia para <xref:System.Windows.FlowDirection.LeftToRight>.<br /><br /> <xref:System.Windows.Forms.RightToLeft.Yes>mapeia para <xref:System.Windows.FlowDirection.RightToLeft>.|  
|<xref:System.Windows.Forms.Control.Visible%2A>|<xref:System.Windows.UIElement.Visibility%2A>|O <xref:System.Windows.Forms.Integration.ElementHost> conjuntos de controles de <xref:System.Windows.UIElement.Visibility%2A> propriedade no elemento hospedado usando as seguintes regras:<br /><br /> -   <xref:System.Windows.Forms.Control.Visible%2A> = `true`mapeia para <xref:System.Windows.Visibility.Visible>.<br />-   <xref:System.Windows.Forms.Control.Visible%2A> = `false`mapeia para <xref:System.Windows.Visibility.Hidden>.|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [Interoperação do WPF e do Win32](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md)  
 [Interoperação do WPF e do Windows Forms](../../../../docs/framework/wpf/advanced/wpf-and-windows-forms-interoperation.md)  
 [Passo a passo: mapeando propriedades usando o elemento WindowsFormsHost](../../../../docs/framework/wpf/advanced/walkthrough-mapping-properties-using-the-windowsformshost-element.md)  
 [Instruções passo a passo: mapeando propriedades usando o controle ElementHost](../../../../docs/framework/wpf/advanced/walkthrough-mapping-properties-using-the-elementhost-control.md)
