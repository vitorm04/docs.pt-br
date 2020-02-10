---
title: Considerações sobre o layout do elemento WindowsFormsHost
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms [WPF], interoperability with
- Windows Forms [WPF], WPF interoperation
- interoperability [WPF], Windows Forms
- WindowsFormsHost element layout considerations [WPF]
- dynamic layout [WPF interoperability]
- device-independent pixels
ms.assetid: 3c574597-bbde-440f-95cc-01371f1a5d9d
ms.openlocfilehash: 89ed57a787b93a1326b4accd3bb1bc5ff9a825fd
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77095145"
---
# <a name="layout-considerations-for-the-windowsformshost-element"></a>Considerações sobre o layout do elemento WindowsFormsHost
Este tópico descreve como o elemento <xref:System.Windows.Forms.Integration.WindowsFormsHost> interage com o sistema de layout de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] e Windows Forms dão suporte à lógica diferente, mas semelhante, para dimensionar e posicionar elementos em um formulário ou página. Quando você cria uma interface do usuário híbrida (IU) que hospeda controles de Windows Forms no [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], o elemento <xref:System.Windows.Forms.Integration.WindowsFormsHost> integra os dois esquemas de layout.  
  
## <a name="differences-in-layout-between-wpf-and-windows-forms"></a>Diferenças de Layout entre WPF e Windows Forms  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] usa layout independente de resolução. Todas as dimensões de layout [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] são especificadas usando *pixels independentes de dispositivo*. Um pixel independente de dispositivo é um sobre noventa e seis avos de polegada em tamanho e independente de resolução, assim, você obtém resultados semelhantes independentemente de se está processando um monitor de 72 dpi ou uma impressora 19.200 dpi.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] também é baseado no *layout dinâmico*. Isso significa que um elemento de interface do usuário se organiza em um formulário ou página de acordo com seu conteúdo, seu contêiner de layout pai e o tamanho de tela disponível. O layout dinâmico facilita a localização ao ajustar automaticamente o tamanho e a posição dos elementos da interface do usuário quando as cadeias de caracteres que eles contêm alteram de comprimento.  
  
 O layout em Windows Forms depende do dispositivo e tem mais probabilidade de ser estático. Normalmente, os controles de Windows Forms são posicionados absolutamente em um formulário usando dimensões especificadas em pixels de hardware. No entanto, o Windows Forms oferece suporte a alguns recursos de layout dinâmico, conforme resumido na tabela a seguir.  
  
|Recurso de layout|DESCRIÇÃO|  
|--------------------|-----------------|  
|Dimensionamento automático|Alguns controles de Windows Forms se redimensionam para exibir seu conteúdo corretamente. Para obter mais informações, consulte [Visão Geral da Propriedade AutoSize](../../winforms/controls/autosize-property-overview.md).|  
|Ancoragem e encaixe|Os controles de Windows Forms dão suporte ao posicionamento e dimensionamento com base no contêiner pai. Para obter mais informações, consulte <xref:System.Windows.Forms.Control.Anchor%2A?displayProperty=nameWithType> e <xref:System.Windows.Forms.Control.Dock%2A?displayProperty=nameWithType>.|  
|Dimensionamento automático|Os controles contêiner se redimensionam e redimensionam seus filhos com base na resolução do dispositivo de saída ou o tamanho, em pixels, da fonte padrão do contêiner. Para obter mais informações, consulte [Dimensionamento automático nos Windows Forms](../../winforms/automatic-scaling-in-windows-forms.md).|  
|Contêineres de layout|Os controles <xref:System.Windows.Forms.FlowLayoutPanel> e <xref:System.Windows.Forms.TableLayoutPanel> organizam seus controles filho e se dimensionam de acordo com seu conteúdo.|  
  
## <a name="layout-limitations"></a>Limitações de layout  
 Em geral, os controles de Windows Forms não podem ser dimensionados e transformados na extensão possível no [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. A lista a seguir descreve as limitações conhecidas quando o elemento <xref:System.Windows.Forms.Integration.WindowsFormsHost> tenta integrar seu controle de Windows Forms hospedado ao sistema de layout de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
- Em alguns casos, os controles de Windows Forms não podem ser redimensionados ou podem ser dimensionados apenas para dimensões específicas. Por exemplo, um controle de <xref:System.Windows.Forms.ComboBox> Windows Forms dá suporte a apenas uma única altura, que é definida pelo tamanho da fonte do controle. Em um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layout dinâmico em que os elementos podem ser ampliados verticalmente, um controle de <xref:System.Windows.Forms.ComboBox> hospedado não será ampliado conforme o esperado.  
  
- Os controles de Windows Forms não podem ser girados ou distorcidos. O elemento <xref:System.Windows.Forms.Integration.WindowsFormsHost> gera o evento <xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError> se você aplicar uma transformação distorção ou rotação. Se você não tratar o evento <xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError>, um <xref:System.InvalidOperationException> será gerado.  
  
- Na maioria dos casos, os controles de Windows Forms não dão suporte ao dimensionamento proporcional. Embora as dimensões gerais do controle sejam dimensionadas, os controles filho e os elementos de componentes do controle podem não ser redimensionados conforme o esperado. Essa limitação depende de quão bem cada controle de Windows Forms dá suporte ao dimensionamento. Além disso, você não pode dimensionar Windows Forms controles até um tamanho de 0 pixels.  
  
- Os controles de Windows Forms dão suporte ao dimensionamento automático, no qual o formulário será redimensionado automaticamente e seus controles com base no tamanho da fonte. Em uma interface do usuário [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], alterar o tamanho da fonte não redimensiona o layout inteiro, embora elementos individuais possam redimensionar dinamicamente.  
  
### <a name="z-order"></a>Ordem z  
 Em uma interface do usuário [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], você pode alterar a ordem z dos elementos para controlar o comportamento de sobreposição. Um controle de Windows Forms hospedado é desenhado em um HWND separado, portanto, ele sempre é desenhado sobre os elementos [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 Um controle de Windows Forms hospedado também é desenhado sobre qualquer elemento de <xref:System.Windows.Documents.Adorner>.  
  
## <a name="layout-behavior"></a>Comportamento de layout  
 As seções a seguir descrevem aspectos específicos do comportamento de layout ao hospedar Windows Forms controles no [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
### <a name="scaling-unit-conversion-and-device-independence"></a>Dimensionamento, conversão de unidade e independência de dispositivo  
 Sempre que o elemento <xref:System.Windows.Forms.Integration.WindowsFormsHost> executa operações que envolvem [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] e Windows Forms dimensões, dois sistemas de coordenadas são envolvidos: pixels independentes de dispositivo para [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] e pixels de hardware para Windows Forms. Portanto, você deve aplicar a unidade apropriada e conversões de dimensionamento para atingir um layout consistente.  
  
 A conversão entre os sistemas de coordenadas depende da resolução atual do dispositivo e de todas as transformações de layout ou de renderização aplicadas ao elemento <xref:System.Windows.Forms.Integration.WindowsFormsHost> ou a seus ancestrais.  
  
 Se o dispositivo de saída for 96 dpi e nenhum dimensionamento for aplicado ao elemento <xref:System.Windows.Forms.Integration.WindowsFormsHost>, um pixel independente do dispositivo será igual a um pixel de hardware.  
  
 Todos os outros casos requerem o dimensionamento do sistema de coordenadas. O controle hospedado não é redimensionado. Em vez disso, o elemento <xref:System.Windows.Forms.Integration.WindowsFormsHost> tenta dimensionar o controle hospedado e todos os seus controles filho. Como Windows Forms não dá suporte total ao dimensionamento, o elemento <xref:System.Windows.Forms.Integration.WindowsFormsHost> é dimensionado para o grau suportado por controles específicos.  
  
 Substitua o método <xref:System.Windows.Forms.Integration.WindowsFormsHost.ScaleChild%2A> para fornecer o comportamento de dimensionamento personalizado para o controle de Windows Forms hospedado.  
  
 Além do dimensionamento, o elemento <xref:System.Windows.Forms.Integration.WindowsFormsHost> manipula casos de arredondamento e de estouro, conforme descrito na tabela a seguir.  
  
|Tipo de conversão|DESCRIÇÃO|  
|----------------------|-----------------|  
|Rounding|[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] as dimensões de pixel independentes de dispositivo são especificadas como `double`e Windows Forms as dimensões de pixel de hardware são especificadas como `int`. Nos casos em que as dimensões baseadas em `double`são convertidas em dimensões baseadas em `int`, o elemento <xref:System.Windows.Forms.Integration.WindowsFormsHost> usa o arredondamento padrão, para que os valores fracionários menores que 0,5 sejam arredondados para baixo para 0.|  
|Estouro|Quando o elemento <xref:System.Windows.Forms.Integration.WindowsFormsHost> converte de valores de `double` em valores `int`, o estouro é possível. Valores maiores que <xref:System.Int32.MaxValue> são definidos como <xref:System.Int32.MaxValue>.|  
  
### <a name="layout-related-properties"></a>Propriedades relacionadas ao layout  
 As propriedades que controlam o comportamento de layout em Windows Forms controles e [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elementos são mapeadas adequadamente pelo elemento <xref:System.Windows.Forms.Integration.WindowsFormsHost>. Para mais informações, consulte [Windows Forms e mapeamento de propriedade do WPF](windows-forms-and-wpf-property-mapping.md).  
  
### <a name="layout-changes-in-the-hosted-control"></a>Alterações de layout no controle hospedado  
 As alterações de layout no controle de Windows Forms hospedado são propagadas para [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] para disparar atualizações de layout. O método <xref:System.Windows.UIElement.InvalidateMeasure%2A> em <xref:System.Windows.Forms.Integration.WindowsFormsHost> garante que as alterações de layout no controle hospedado façam com que o mecanismo de layout de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] seja executado.  
  
### <a name="continuously-sized-windows-forms-controls"></a>Controles dos Windows Forms dimensionados continuamente  
 Windows Forms controles que dão suporte ao dimensionamento contínuo totalmente interagem com o sistema de layout de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. O elemento <xref:System.Windows.Forms.Integration.WindowsFormsHost> usa os métodos <xref:System.Windows.FrameworkElement.MeasureOverride%2A> e <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> normalmente para dimensionar e organizar o controle Windows Forms hospedado.  
  
### <a name="sizing-algorithm"></a>Algoritmo de dimensionamento  
 O elemento <xref:System.Windows.Forms.Integration.WindowsFormsHost> usa o procedimento a seguir para dimensionar o controle hospedado:  
  
1. O elemento <xref:System.Windows.Forms.Integration.WindowsFormsHost> substitui os métodos <xref:System.Windows.FrameworkElement.MeasureOverride%2A> e <xref:System.Windows.FrameworkElement.ArrangeOverride%2A>.  
  
2. Para determinar o tamanho do controle hospedado, o método <xref:System.Windows.FrameworkElement.MeasureOverride%2A> chama o método <xref:System.Windows.Forms.Control.GetPreferredSize%2A> do controle hospedado com uma restrição convertida da restrição passada para o método <xref:System.Windows.FrameworkElement.MeasureOverride%2A>.  
  
3. O método <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> tenta definir o controle hospedado para a restrição de tamanho fornecida.  
  
4. Se a propriedade de <xref:System.Windows.Forms.Control.Size%2A> do controle hospedado corresponder à restrição especificada, o controle hospedado será dimensionado para a restrição.  
  
 Se a propriedade <xref:System.Windows.Forms.Control.Size%2A> não corresponder à restrição especificada, o controle hospedado não oferecerá suporte ao dimensionamento contínuo. Por exemplo, o controle de <xref:System.Windows.Forms.MonthCalendar> permite apenas tamanhos discretos. Os tamanhos permitidos para este controle consistem em números inteiros (representando o número de meses) para altura e largura. Em casos como esse, o elemento <xref:System.Windows.Forms.Integration.WindowsFormsHost> se comporta da seguinte maneira:  
  
- Se a propriedade <xref:System.Windows.Forms.Control.Size%2A> retornar um tamanho maior do que a restrição especificada, o elemento <xref:System.Windows.Forms.Integration.WindowsFormsHost> cortará o controle hospedado. Altura e largura são tratadas separadamente, portanto, o controle hospedado pode ser recortado em qualquer direção.  
  
- Se a propriedade <xref:System.Windows.Forms.Control.Size%2A> retornar um tamanho menor do que a restrição especificada, <xref:System.Windows.Forms.Integration.WindowsFormsHost> aceitará esse valor de tamanho e retornará o valor para o sistema de layout de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Passo a passo: organizando controles do Windows Forms no WPF](walkthrough-arranging-windows-forms-controls-in-wpf.md)
- [Organizando Windows Forms controles no WPF de exemplo](https://github.com/microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/WpfLayoutHostingWfWithXaml)
- [Windows Forms e mapeamento de propriedade do WPF](windows-forms-and-wpf-property-mapping.md)
- [Migração e interoperabilidade](migration-and-interoperability.md)
