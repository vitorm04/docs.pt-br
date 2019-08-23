---
title: Interoperação do WPF e dos Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms [WPF], interoperability with
- nester interoperation [WPF]
- Windows Forms [WPF], WPF interoperation
- interoperability [WPF], Windows Forms
- hybrid control [WPF interoperability]
ms.assetid: 9e8aa6b6-112c-4579-98d1-c974917df499
ms.openlocfilehash: 0326f283cb271d1578e94b648e423c6f88c579f0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917395"
---
# <a name="wpf-and-windows-forms-interoperation"></a>Interoperação do WPF e dos Windows Forms
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] e [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] apresentam duas diferentes arquiteturas para criação de interfaces de aplicativo. O <xref:System.Windows.Forms.Integration?displayProperty=nameWithType> namespace fornece classes que habilitam cenários comuns de interoperação. As duas classes principais que implementam recursos de interoperação <xref:System.Windows.Forms.Integration.ElementHost>são <xref:System.Windows.Forms.Integration.WindowsFormsHost> e. Este tópico descreve quais cenários de interoperação tem suporte e quais cenários não tem suporte.  
  
> [!NOTE]
> Uma consideração especial é fornecida para o cenário de *controle híbrido*. Um controle híbrido tem um controle de uma tecnologia aninhado em um controle da outra tecnologia. Isso também é chamado um *interoperação aninhada*. Um *controle multinível híbrido* tem mais de um nível de aninhamento híbrido de controles. Um exemplo de interoperação multinível aninhada é um [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controle que contém um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] controle, que contém outro [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controle. Controles híbridos multinível não tem suporte.  

<a name="Windows_Presentation_Foundation_Application_Hosting"></a>   
## <a name="hosting-windows-forms-controls-in-wpf"></a>Hospedando controle dos Windows Forms no WPF  
 Os cenários de interoperação a seguir têm suporte [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] quando um controle hospeda um controle de Windows Forms:  
  
- O controle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pode hospedar um ou mais [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controles usando do XAML.  
  
- Ele pode hospedar um ou mais [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controles usando código.  
  
- Ele pode hospedar [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controles de contêiner que contêm outros [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controles.  
  
- Ele pode hospedar um formulário mestre/detalhes com um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] mestre e [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] detalhes.  
  
- Ele pode hospedar um formulário mestre/detalhes com um [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] mestre e [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] detalhes.  
  
- Ele pode hospedar um ou mais controles ActiveX.  
  
- Ele pode hospedar um ou mais controles de composição.  
  
- Ele pode hospedar controles híbridos usando [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].  
  
- Ele pode hospedar controles híbridos usando código.  
  
### <a name="layout-support"></a>Suporte de layout  
 A lista a seguir descreve as limitações conhecidas quando <xref:System.Windows.Forms.Integration.WindowsFormsHost> o elemento tenta integrar seu controle [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] hospedado ao sistema [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de layout.  
  
- Em alguns casos, os controles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] não podem ser redimensionados ou podem ser dimensionados somente para dimensões específicas. Por exemplo, um [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.ComboBox> controle dá suporte a apenas uma única altura, que é definida pelo tamanho da fonte do controle. Em um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layout dinâmico, que assume que os elementos podem ser ampliados verticalmente <xref:System.Windows.Forms.ComboBox> , um controle hospedado não será ampliado conforme o esperado.  
  
- Os controles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] não podem ser girados ou inclinados. Por exemplo, quando você rotaciona sua interface do usuário em 90 graus, os controles hospedados [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] manterão sua posição vertical.  
  
- Na maioria dos casos, os controles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] não dão suporte ao dimensionamento proporcional. Embora as dimensões gerais do controle sejam dimensionadas, os controles filho e os elementos de componentes do controle podem não ser redimensionados conforme o esperado. Essa limitação depende de quanto cada controle [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] dá suporte ao dimensionamento.  
  
- Em uma interface do usuário [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], você pode alterar a ordem z dos elementos para controlar o comportamento de sobreposição. Um controle [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] hospedado é desenhado em uma HWND separada, portanto, é sempre desenhado na parte superior dos elementos [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
- [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controles oferecem suporte a dimensionamento automático com base no tamanho da fonte. Em uma interface do usuário [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], alterar o tamanho da fonte não redimensiona o layout inteiro, embora elementos individuais possam redimensionar dinamicamente.  
  
### <a name="ambient-properties"></a>Propriedades de ambiente  
 Algumas das propriedades de ambiente dos controles [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] têm [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] equivalentes. Essas propriedades de ambiente são propagadas para [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] os controles hospedados e expostas <xref:System.Windows.Forms.Integration.WindowsFormsHost> como propriedades públicas no controle. O <xref:System.Windows.Forms.Integration.WindowsFormsHost> controle traduz cada [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] propriedade de ambiente em seu [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] equivalente.  
  
 Para mais informações, consulte [Windows Forms e mapeamento de propriedade do WPF](windows-forms-and-wpf-property-mapping.md).  
  
### <a name="behavior"></a>Comportamento  
 A tabela a seguir descreve o comportamento de interoperação.  
  
|Comportamento|Com suporte|Sem suporte|  
|--------------|---------------|-------------------|  
|Transparência|[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] renderização de controle dá suporte à transparência. A tela de fundo do controle pai [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pode se tornar a tela de fundo de controles hospedados [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].|Alguns [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controles não dão suporte a transparência. Por exemplo, os <xref:System.Windows.Forms.TextBox> controles <xref:System.Windows.Forms.ComboBox> e não serão transparentes quando hospedados pelo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].|  
|Tabulação|Ordem de tabulação para controles hospedados [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] é igual a quando esses controles são hospedados em um aplicativo baseado em [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].<br /><br /> Tabulação de um controle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] para um controle [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] com a tecla TAB e teclas SHIFT + TAB funciona da maneira habitual.<br /><br /> [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]controles que têm um <xref:System.Windows.Forms.Control.TabStop%2A> valor de propriedade `false` de não recebem o foco quando o usuário faz a tabulação através de controles.<br /><br /> -Cada <xref:System.Windows.Forms.Integration.WindowsFormsHost> controle tem um <xref:System.Windows.Forms.Integration.WindowsFormsHost.TabIndex%2A> valor, que determina quando esse <xref:System.Windows.Forms.Integration.WindowsFormsHost> controle receberá o foco.<br />-   [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]controles que estão contidos dentro de <xref:System.Windows.Forms.Integration.WindowsFormsHost> um contêiner seguem a ordem especificada <xref:System.Windows.Forms.Control.TabIndex%2A> pela propriedade. Fazer tabulação do último índice de tabulação coloca o foco no próximo contorle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], se houver. Se nenhum outro controle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de foco existir, a tabulação retornará para o primeiro [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controle na ordem de tabulação.<br />-   <xref:System.Windows.Forms.Integration.WindowsFormsHost.TabIndex%2A>os valores para controles dentro <xref:System.Windows.Forms.Integration.WindowsFormsHost> de são relativos aos [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controles irmãos contidos no <xref:System.Windows.Forms.Integration.WindowsFormsHost> controle.<br />- A tabulação honra o comportamento específico de controle. Por exemplo, pressionar a tecla Tab em um <xref:System.Windows.Forms.TextBox> controle que tem um <xref:System.Windows.Forms.TextBoxBase.AcceptsTab%2A> valor de propriedade `true` de entra em uma guia na caixa de texto em vez de mover o foco.|Não aplicável.|  
|Navegação com teclas de direção|-A navegação com as teclas de <xref:System.Windows.Forms.Integration.WindowsFormsHost> direção no controle é a mesma que em [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] um controle de contêiner comum: As teclas seta para cima e seta para a esquerda selecionam o controle anterior e as teclas seta para baixo e seta para a direita selecionam o próximo controle.<br />-As teclas de seta para cima e seta para a esquerda do primeiro controle contido no <xref:System.Windows.Forms.Integration.WindowsFormsHost> controle executam a mesma ação que o atalho de teclado Shift + Tab. Se houver um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] controle focado, o foco se moverá <xref:System.Windows.Forms.Integration.WindowsFormsHost> para fora do controle. Esse comportamento difere do comportamento padrão <xref:System.Windows.Forms.ContainerControl> no caso de não haver nenhum encapsulamento para o último controle. Se nenhum outro controle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] com foco existir, a tabulação retornará para o último controle [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] na ordem de tabulação.<br />-As teclas de seta para baixo e de seta para a direita do último controle contido <xref:System.Windows.Forms.Integration.WindowsFormsHost> no controle executam a mesma ação que a tecla Tab. Se houver um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] controle focado, o foco se moverá <xref:System.Windows.Forms.Integration.WindowsFormsHost> para fora do controle. Esse comportamento difere do comportamento padrão <xref:System.Windows.Forms.ContainerControl> no caso de não haver nenhum encapsulamento para o primeiro controle. Se nenhum outro controle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] com foco existir, o foco retorna para o último controle [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] na ordem de tabulação.|Não aplicável.|  
|Aceleradores|Aceleradores funcionam como de costume, exceto onde observado na coluna "Sem suporte".|Aceleradores duplicados entre tecnologias não funcionam como aceleradores duplicados comuns. Quando um acelerador é duplicado entre tecnologias, com, pelo menos, um em um controle de [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] e o outro em um controle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], o controle [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] sempre recebe o acelerador. O foco não alterna entre os controles quando o acelerador duplicado é pressionado.|  
|Teclas de atalho|Teclas de atalho funcionam como de costume, exceto onde observado na coluna "Sem suporte".|-   [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] teclas de atalho que são tratadas no estágio de pré-processamento sempre têm precedência sobre [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] teclas de atalho. Por exemplo, se você tiver um <xref:System.Windows.Forms.ToolStrip> controle com as teclas de atalho CTRL + s definidas e houver um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] comando associado a CTRL + s, o <xref:System.Windows.Forms.ToolStrip> manipulador de controle será sempre invocado primeiro, independentemente do foco.<br />-   [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]as teclas de atalho que são manipuladas pelo <xref:System.Windows.Forms.Control.KeyDown> evento são processadas por último em. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Você pode evitar esse comportamento substituindo o [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] método do <xref:System.Windows.Forms.Control.IsInputKey%2A> controle ou manipulando <xref:System.Windows.Forms.Control.PreviewKeyDown> o evento. Retorne `true` <xref:System.Windows.Forms.PreviewKeyDownEventArgs.IsInputKey%2A?displayProperty=nameWithType> `true` <xref:System.Windows.Forms.Control.PreviewKeyDown> do método ou defina o valor da propriedade como em seu manipulador de eventos. <xref:System.Windows.Forms.Control.IsInputKey%2A>|  
|AcceptsReturn, AcceptsTab e outros comportamentos de controle específicos|As propriedades que alteram o comportamento padrão do teclado funcionam como de costume [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] , supondo <xref:System.Windows.Forms.Control.IsInputKey%2A> que o controle `true`substitua o método a ser retornado.|[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]os controles que alteram o comportamento de teclado <xref:System.Windows.Forms.Control.KeyDown> padrão manipulando o evento são processados por último no controle de host. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Como esses controles são processados por último, eles podem produzir um comportamento inesperado.|  
|Entrar e sair de eventos|Quando o foco não vai para o controle <xref:System.Windows.Forms.Integration.ElementHost> recipiente, os eventos Enter e Leave são gerados como de costume quando o foco é alterado <xref:System.Windows.Forms.Integration.WindowsFormsHost> em um único controle.|Os eventos Enter e Leave não são acionados quando ocorrem as seguintes alterações de foco:<br /><br /> -De dentro para fora de <xref:System.Windows.Forms.Integration.WindowsFormsHost> um controle.<br />-De fora para dentro de <xref:System.Windows.Forms.Integration.WindowsFormsHost> um controle.<br />-Fora de <xref:System.Windows.Forms.Integration.WindowsFormsHost> um controle.<br />-De um [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controle hospedado em um <xref:System.Windows.Forms.Integration.WindowsFormsHost> controle para um <xref:System.Windows.Forms.Integration.ElementHost> controle hospedado dentro do mesmo <xref:System.Windows.Forms.Integration.WindowsFormsHost>.|  
|Multithreading|Todas as variedades de multithreading têm suporte.|As tecnologias [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] e [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] supõem um modelo de simultaneidade de segmento único. Durante a depuração, chamadas para objetos do framework de outros segmentos disparará uma exceção para impor essa exigência.|  
|Segurança|Todos os cenários de interoperação requerem confiança total.|Nenhum cenário de interoperação é permitido em confiança parcial.|  
|Acessibilidade|Todos os cenários de acessibilidade tem suporte. Produtos de tecnologia assistencial funcionam corretamente quando eles são usados para aplicativos híbridos que contêm os controles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] e [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].|Não aplicável.|  
|Área de Transferência|Todas as operações da área de transferência funcionam como de costume. Isso inclui recorte e colagem entre os controles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] e [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].|Não aplicável.|  
|Recurso do tipo "arrastar e soltar"|Todas as operações do tipo "arrastar e soltar" funcionam como de costume. Isso inclui operações entre os controles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] e [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].|Não aplicável.|  
  
<a name="Windows_Forms_Application_Hosting_Windows"></a>   
## <a name="hosting-wpf-controls-in-windows-forms"></a>Hospedando Controles de WPF nos Windows Forms  
 Os cenários de interoperação a seguir têm suporte quando um controle de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Windows Forms hospeda um controle:  
  
- Hospedando um ou mais controles [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] usando código.  
  
- Associar uma folha de propriedades com um ou mais controles [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hospedados.  
  
- Hospedando um ou mais páginas [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] em um formulário.  
  
- Iniciando uma janela [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
- Hospedando um formulário mestre/detalhes com um [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] mestre e [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] detalhes.  
  
- Hospedando um formulário mestre/detalhes com um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] mestre e [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] detalhes.  
  
- Hospedando controles [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] personalizados.  
  
- Hospedando controles híbridos.  
  
### <a name="ambient-properties"></a>Propriedades de ambiente  
 Algumas das propriedades de ambiente dos controles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] têm [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] equivalentes. Essas propriedades de ambiente são propagadas para [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] os controles hospedados e expostas <xref:System.Windows.Forms.Integration.ElementHost> como propriedades públicas no controle. O <xref:System.Windows.Forms.Integration.ElementHost> controle traduz cada [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] propriedade de ambiente para seu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] equivalente.  
  
 Para mais informações, consulte [Windows Forms e mapeamento de propriedade do WPF](windows-forms-and-wpf-property-mapping.md).  
  
### <a name="behavior"></a>Comportamento  
 A tabela a seguir descreve o comportamento de interoperação.  
  
|Comportamento|Com suporte|Sem suporte|  
|--------------|---------------|-------------------|  
|Transparência|[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] renderização de controle dá suporte à transparência. A tela de fundo do controle pai [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] pode se tornar a tela de fundo de controles hospedados [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].|Não aplicável.|  
|Multithreading|Todas as variedades de multithreading têm suporte.|As tecnologias [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] e [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] supõem um modelo de simultaneidade de segmento único. Durante a depuração, chamadas para objetos do framework de outros segmentos disparará uma exceção para impor essa exigência.|  
|Segurança|Todos os cenários de interoperação requerem confiança total.|Nenhum cenário de interoperação é permitido em confiança parcial.|  
|Acessibilidade|Todos os cenários de acessibilidade tem suporte. Produtos de tecnologia assistencial funcionam corretamente quando eles são usados para aplicativos híbridos que contêm os controles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] e [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].|Não aplicável.|  
|Área de Transferência|Todas as operações da área de transferência funcionam como de costume. Isso inclui recorte e colagem entre os controles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] e [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].|Não aplicável.|  
|Recurso do tipo "arrastar e soltar"|Todas as operações do tipo "arrastar e soltar" funcionam como de costume. Isso inclui operações entre os controles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] e [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].|Não aplicável.|  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Passo a passo: Hospedando um controle de Windows Forms no WPF](walkthrough-hosting-a-windows-forms-control-in-wpf.md)
- [Passo a passo: Hospedando um controle composto Windows Forms no WPF](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [Passo a passo: Hospedando um controle composto do WPF no Windows Forms](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [Windows Forms e mapeamento de propriedade do WPF](windows-forms-and-wpf-property-mapping.md)
