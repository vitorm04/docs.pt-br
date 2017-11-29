---
title: "Considerações sobre o layout do elemento WindowsFormsHost"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms [WPF], interoperability with
- Windows Forms [WPF], WPF interoperation
- interoperability [WPF], Windows Forms
- WindowsFormsHost element layout considerations [WPF]
- dynamic layout [WPF interoperability]
- device-independent pixels
ms.assetid: 3c574597-bbde-440f-95cc-01371f1a5d9d
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d21077e6012f8e48a1418f67e8f0d156d82003c3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="layout-considerations-for-the-windowsformshost-element"></a>Considerações sobre o layout do elemento WindowsFormsHost
Este tópico descreve como o <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento interage com o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sistema de layout.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] e [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] dão suporte diferente, mas similar, lógico para dimensionamento e posicionamento de elementos em um formulário ou página. Quando você cria uma interface do usuário híbrida (IU) que hospeda [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controles em [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], o <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento integra os dois esquemas de layout.  
  
## <a name="differences-in-layout-between-wpf-and-windows-forms"></a>Diferenças de Layout entre WPF e Windows Forms  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] usa layout independente de resolução. Todas as dimensões de layout [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] são especificadas usando *pixels independentes de dispositivo*. Um pixel independente de dispositivo é um sobre noventa e seis avos de polegada em tamanho e independente de resolução, assim, você obtém resultados semelhantes independentemente de se está processando um monitor de 72 dpi ou uma impressora 19.200 dpi.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] também é baseado no *layout dinâmico*. Isso significa que um elemento de interface do usuário se organiza em um formulário ou página de acordo com seu conteúdo, seu contêiner de layout pai e o tamanho de tela disponível. O layout dinâmico facilita a localização ao ajustar automaticamente o tamanho e a posição dos elementos da interface do usuário quando as cadeias de caracteres que eles contêm alteram de comprimento.  
  
 O layout em [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] é dependente de dispositivo e mais provável de ser estático. Normalmente, os controles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] são posicionados absolutamente em um formulário usando dimensões especificadas em pixels de hardware. No entanto, [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] dá suporte a alguns recursos de layout dinâmico, como resumido na tabela a seguir.  
  
|Recurso de layout|Descrição|  
|--------------------|-----------------|  
|Dimensionamento automático|Alguns controles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] se redimensionam para exibir seu conteúdo adequadamente. Para obter mais informações, consulte [Visão Geral da Propriedade AutoSize](../../../../docs/framework/winforms/controls/autosize-property-overview.md).|  
|Ancoragem e encaixe|Os controles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] dão suporte ao posicionamento e ao dimensionamento com base no contêiner pai. Para obter mais informações, consulte <xref:System.Windows.Forms.Control.Anchor%2A?displayProperty=nameWithType> e <xref:System.Windows.Forms.Control.Dock%2A?displayProperty=nameWithType>.|  
|Dimensionamento automático|Os controles contêiner se redimensionam e redimensionam seus filhos com base na resolução do dispositivo de saída ou o tamanho, em pixels, da fonte padrão do contêiner. Para obter mais informações, consulte [Dimensionamento automático nos Windows Forms](../../../../docs/framework/winforms/automatic-scaling-in-windows-forms.md).|  
|Contêineres de layout|O <xref:System.Windows.Forms.FlowLayoutPanel> e <xref:System.Windows.Forms.TableLayoutPanel> controles organizam seus controles filho e dimensionam a mesmos acordo com seu conteúdo.|  
  
## <a name="layout-limitations"></a>Limitações de layout  
 Em geral, controles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] não podem ser dimensionados e transformados, na medida do possível, em [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. A lista a seguir descreve as limitações conhecidas quando o <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento tenta integrar seu [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controle para o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sistema de layout.  
  
-   Em alguns casos, os controles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] não podem ser redimensionados ou podem ser dimensionados somente para dimensões específicas. Por exemplo, um [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.ComboBox> controle oferece suporte a apenas uma única altura, que é definida pelo tamanho da fonte do controle. Em um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layout dinâmico, onde os elementos podem alongar verticalmente, hospedado <xref:System.Windows.Forms.ComboBox> controle não será ampliado conforme o esperado.  
  
-   Os controles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] não podem ser girados ou inclinados. O <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento gera o <xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError> evento se você aplicar uma transformação de distorção ou rotação. Se você não tratar o <xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError> evento, um <xref:System.InvalidOperationException> é gerado.  
  
-   Na maioria dos casos, os controles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] não dão suporte ao dimensionamento proporcional. Embora as dimensões gerais do controle sejam dimensionadas, os controles filho e os elementos de componentes do controle podem não ser redimensionados conforme o esperado. Essa limitação depende de quanto cada controle [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] dá suporte ao dimensionamento. Além disso, não é possível dimensionar controles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] para um tamanho de 0 pixel.  
  
-   Os controles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] dão suporte ao dimensionamento automático, no qual o formulário redimensionará automaticamente si mesmo e seus controles com base no tamanho da fonte. Em uma interface do usuário [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], alterar o tamanho da fonte não redimensiona o layout inteiro, embora elementos individuais possam redimensionar dinamicamente.  
  
### <a name="z-order"></a>Ordem z  
 Em uma interface do usuário [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], você pode alterar a ordem z dos elementos para controlar o comportamento de sobreposição. Um controle [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] hospedado é desenhado em uma HWND separada, portanto, é sempre desenhado na parte superior dos elementos [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 Hospedado [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controle também é desenhado na parte superior de qualquer <xref:System.Windows.Documents.Adorner> elementos.  
  
## <a name="layout-behavior"></a>Comportamento de layout  
 As seções a seguir descrevem aspectos específicos do comportamento de layout ao hospedar controles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] em [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
### <a name="scaling-unit-conversion-and-device-independence"></a>Dimensionamento, conversão de unidade e independência de dispositivo  
 Sempre que o <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento executa operações envolvendo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] e [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] dimensões, dois sistemas de coordenadas envolvidas: pixels independentes de dispositivo para [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] e pixels de hardware para [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]. Portanto, você deve aplicar a unidade apropriada e conversões de dimensionamento para atingir um layout consistente.  
  
 Conversão entre os sistemas de coordenadas depende da resolução do dispositivo atual e de qualquer layout ou transformações de renderização aplicadas para o <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento ou a seus ancestrais.  
  
 Se o dispositivo de saída for de 96 dpi e nenhuma escala foi aplicada para o <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento, um pixel independente de dispositivo é igual a um pixel de hardware.  
  
 Todos os outros casos requerem o dimensionamento do sistema de coordenadas. O controle hospedado não é redimensionado. Em vez disso, o <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento tenta redimensionar o controle hospedado e todos os seus controles filhos. Porque [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] não suporte completo a escala, o <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento pode ser expandido para o grau suportado pelos controles específicos.  
  
 Substituir o <xref:System.Windows.Forms.Integration.WindowsFormsHost.ScaleChild%2A> método para fornecer o comportamento de dimensionamento personalizado hospedado [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] controle.  
  
 Além de dimensionar, o <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento trata casos de arredondamento e de estouro conforme descrito na tabela a seguir.  
  
|Tipo de conversão|Descrição|  
|----------------------|-----------------|  
|Arredondamento|As dimensões em pixels independentes de dispositivo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] são especificadas como `double` e as dimensões de pixel de hardware [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] são especificadas como `int`. Em casos onde `double`-dimensões com base são convertidos em `int`-dimensões, o <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento usa arredondamento padrão para que os valores fracionários menores do que 0,5 são arredondados para baixo para 0.|  
|Estouro|Quando o <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento converte de `double` valores `int` valores, o estouro é possível. Valores maiores que <xref:System.Int32.MaxValue> são definidos como <xref:System.Int32.MaxValue>.|  
  
### <a name="layout-related-properties"></a>Propriedades relacionadas ao layout  
 Propriedades que controlam o comportamento de layout em [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controles e [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elementos são mapeados corretamente pelo <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento. Para mais informações, consulte [Windows Forms e mapeamento de propriedade do WPF](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-property-mapping.md).  
  
### <a name="layout-changes-in-the-hosted-control"></a>Alterações de layout no controle hospedado  
 As alterações de layout no controle [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] hospedado são propagadas para [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] para disparar atualizações de layout. O <xref:System.Windows.UIElement.InvalidateMeasure%2A> método <xref:System.Windows.Forms.Integration.WindowsFormsHost> garante que as alterações de layout no controle hospedado invalidar o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] mecanismo de layout para executar.  
  
### <a name="continuously-sized-windows-forms-controls"></a>Controles dos Windows Forms dimensionados continuamente  
 Os controles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] que dão suporte ao dimensionamento contínuo interagem totalmente com o sistema de layout [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. O <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento usa o <xref:System.Windows.FrameworkElement.MeasureOverride%2A> e <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> métodos como de costume para dimensionar e organizar hospedado [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controle.  
  
### <a name="sizing-algorithm"></a>Algoritmo de dimensionamento  
 O <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento usa o procedimento a seguir para dimensionar o controle hospedado:  
  
1.  O <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento substitui o <xref:System.Windows.FrameworkElement.MeasureOverride%2A> e <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> métodos.  
  
2.  Para determinar o tamanho do controle hospedado, o <xref:System.Windows.FrameworkElement.MeasureOverride%2A> método chama o controle hospedado <xref:System.Windows.Forms.Control.GetPreferredSize%2A> método com uma restrição convertida da restrição de passado para o <xref:System.Windows.FrameworkElement.MeasureOverride%2A> método.  
  
3.  O <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> método tenta configurar o controle hospedado a restrição de determinado tamanho.  
  
4.  Se o controle hospedado <xref:System.Windows.Forms.Control.Size%2A> propriedade corresponde a restrição especificada, o controle hospedado é dimensionado para a restrição.  
  
 Se o <xref:System.Windows.Forms.Control.Size%2A> propriedade não coincide com a restrição especificada, o controle hospedado não dá suporte a dimensionamento contínuo. Por exemplo, o <xref:System.Windows.Forms.MonthCalendar> controle permite apenas tamanhos discretos. Os tamanhos permitidos para este controle consistem em números inteiros (representando o número de meses) para altura e largura. Em casos como esse, o <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento se comporta da seguinte maneira:  
  
-   Se o <xref:System.Windows.Forms.Control.Size%2A> propriedade retorna um tamanho maior do que a restrição especificada, o <xref:System.Windows.Forms.Integration.WindowsFormsHost> elemento corta o controle hospedado. Altura e largura são tratadas separadamente, portanto, o controle hospedado pode ser recortado em qualquer direção.  
  
-   Se o <xref:System.Windows.Forms.Control.Size%2A> propriedade retorna um tamanho menor do que a restrição especificada, <xref:System.Windows.Forms.Integration.WindowsFormsHost> aceita este valor de tamanho e retorna o valor para o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sistema de layout.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [Passo a passo: organizando controles do Windows Forms no WPF](../../../../docs/framework/wpf/advanced/walkthrough-arranging-windows-forms-controls-in-wpf.md)  
 [Organizar janelas controles de formulários no exemplo do WPF](http://go.microsoft.com/fwlink/?LinkID=159971)  
 [Windows Forms e mapeamento de propriedade do WPF](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-property-mapping.md)  
 [Migração e interoperabilidade](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)
