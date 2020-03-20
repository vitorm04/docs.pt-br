---
title: WPF e Windows Forms interop
titleSuffix: ''
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms [WPF], interoperability with
- nester interoperation [WPF]
- Windows Forms [WPF], WPF interoperation
- interoperability [WPF], Windows Forms
- hybrid control [WPF interoperability]
ms.assetid: 9e8aa6b6-112c-4579-98d1-c974917df499
ms.openlocfilehash: 76d1e97c92946267aa1217f52c93594fb63d20de
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187158"
---
# <a name="wpf-and-windows-forms-interoperation"></a>Interoperação do WPF e dos Windows Forms
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]e o Windows Forms apresenta duas arquiteturas diferentes para criar interfaces de aplicativos. O <xref:System.Windows.Forms.Integration?displayProperty=nameWithType> namespace fornece classes que permitem cenários comuns de interoperação. As duas classes-chave que implementam capacidades de interoperação são <xref:System.Windows.Forms.Integration.WindowsFormsHost> e <xref:System.Windows.Forms.Integration.ElementHost>. Este tópico descreve quais cenários de interoperação tem suporte e quais cenários não tem suporte.  
  
> [!NOTE]
> Uma consideração especial é fornecida para o cenário de *controle híbrido*. Um controle híbrido tem um controle de uma tecnologia aninhado em um controle da outra tecnologia. Isso também é chamado um *interoperação aninhada*. Um *controle multinível híbrido* tem mais de um nível de aninhamento híbrido de controles. Um exemplo de uma interoperação aninhada multinível [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] é um controle do Windows Forms que contém um controle, que contém outro controle do Windows Forms. Controles híbridos multinível não tem suporte.  

<a name="Windows_Presentation_Foundation_Application_Hosting"></a>
## <a name="hosting-windows-forms-controls-in-wpf"></a>Hospedando controle dos Windows Forms no WPF  
 Os seguintes cenários de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] interoperação são suportados quando um controle hospeda um controle do Windows Forms:  
  
- O [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] controle pode hospedar um ou mais controles do Windows Forms usando XAML.  
  
- Ele pode hospedar um ou mais controles do Windows Forms usando código.  
  
- Ele pode hospedar controles de contêiner do Windows Forms que contenham outros controles do Windows Forms.  
  
- Ele pode hospedar um formulário [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] mestre/detalhe com detalhes de um mestre e formulários do Windows.  
  
- Ele pode hospedar um formulário mestre/detalhe [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] com um mestre e detalhes do Windows Forms.  
  
- Ele pode hospedar um ou mais controles ActiveX.  
  
- Ele pode hospedar um ou mais controles de composição.  
  
- Ele pode hospedar controles híbridos usando [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].  
  
- Ele pode hospedar controles híbridos usando código.  
  
### <a name="layout-support"></a>Suporte de layout  
 A lista a seguir descreve as <xref:System.Windows.Forms.Integration.WindowsFormsHost> limitações conhecidas quando o elemento [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tenta integrar seu controle de Formulários Windows hospedados no sistema de layout.  
  
- Em alguns casos, os controles do Windows Forms não podem ser redimensionados ou podem ser dimensionados apenas para dimensões específicas. Por exemplo, um <xref:System.Windows.Forms.ComboBox> controle do Windows Forms suporta apenas uma única altura, que é definida pelo tamanho da fonte do controle. Em [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] um layout dinâmico, que pressupõe que os <xref:System.Windows.Forms.ComboBox> elementos podem esticar verticalmente, um controle hospedado não se esticará como esperado.  
  
- Os controles do Windows Forms não podem ser girados ou distorcidos. Por exemplo, quando você gira sua interface de usuário em 90 graus, os controles do Windows Forms hospedados manterão sua posição vertical.  
  
- Na maioria dos casos, os controles do Windows Forms não suportam dimensionamento proporcional. Embora as dimensões gerais do controle sejam dimensionadas, os controles filho e os elementos de componentes do controle podem não ser redimensionados conforme o esperado. Essa limitação depende de quão bem cada controle do Windows Forms suporta o dimensionamento.  
  
- Em uma interface do usuário [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], você pode alterar a ordem z dos elementos para controlar o comportamento de sobreposição. Um controle do Windows Forms hospedado é desenhado em um HWND [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] separado, por isso é sempre desenhado em cima de elementos.  
  
- Os controles do Windows Forms suportam o autoscaling com base no tamanho da fonte. Em uma interface do usuário [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], alterar o tamanho da fonte não redimensiona o layout inteiro, embora elementos individuais possam redimensionar dinamicamente.  
  
### <a name="ambient-properties"></a>Propriedades de ambiente  
 Algumas das propriedades [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ambientais dos controles têm equivalentes do Windows Forms. Essas propriedades ambientais são propagadas para os controles do Windows Forms <xref:System.Windows.Forms.Integration.WindowsFormsHost> hospedados e expostas como propriedades públicas no controle. O <xref:System.Windows.Forms.Integration.WindowsFormsHost> controle traduz [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] cada propriedade ambiente em seu equivalente Windows Forms.  
  
 Para mais informações, consulte [Windows Forms e mapeamento de propriedade do WPF](windows-forms-and-wpf-property-mapping.md).  
  
### <a name="behavior"></a>Comportamento  
 A tabela a seguir descreve o comportamento de interoperação.  
  
|Comportamento|Com suporte|Sem suporte|  
|--------------|---------------|-------------------|  
|Transparência|A renderização de controle do Windows Forms suporta transparência. O plano de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fundo do controle pai pode se tornar o plano de fundo dos controles do Windows Forms hospedados.|Alguns controles do Windows Forms não suportam transparência. Por exemplo, <xref:System.Windows.Forms.TextBox> <xref:System.Windows.Forms.ComboBox> os controles e controles não [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]serão transparentes quando hospedados por .|  
|Tabulação|A ordem de guia para controles do Windows Forms hospedados é a mesma de quando esses controles estão hospedados em um aplicativo baseado no Windows Forms.<br /><br /> A tabulação de um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] controle para um controle do Windows Forms com a tecla TAB e as teclas SHIFT+TAB funciona normalmente.<br /><br /> Os controles do Windows <xref:System.Windows.Forms.Control.TabStop%2A> Forms `false` que possuem um valor de propriedade não recebem foco quando o usuário guia através de controles.<br /><br /> - <xref:System.Windows.Forms.Integration.WindowsFormsHost> Cada controle <xref:System.Windows.Forms.Integration.WindowsFormsHost.TabIndex%2A> tem um valor, <xref:System.Windows.Forms.Integration.WindowsFormsHost> que determina quando esse controle receberá foco.<br />- Os controles do Windows <xref:System.Windows.Forms.Integration.WindowsFormsHost> Forms contidos dentro de <xref:System.Windows.Forms.Control.TabIndex%2A> um contêiner seguem a ordem especificada pela propriedade. Fazer tabulação do último índice de tabulação coloca o foco no próximo contorle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], se houver. Se não houver [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] outro controle focalinável, a tabulação retorna ao primeiro controle do Windows Forms na ordem da guia.<br />-   <xref:System.Windows.Forms.Integration.WindowsFormsHost.TabIndex%2A>os valores para <xref:System.Windows.Forms.Integration.WindowsFormsHost> controles dentro do são relativos aos <xref:System.Windows.Forms.Integration.WindowsFormsHost> controles de formulários do Windows irmãos que estão contidos no controle.<br />- A tabulação honra o comportamento específico de controle. Por exemplo, pressionar a <xref:System.Windows.Forms.TextBox> tecla TAB <xref:System.Windows.Forms.TextBoxBase.AcceptsTab%2A> em `true` um controle que tenha um valor de propriedade insere uma guia na caixa de texto em vez de mover o foco.|Não aplicável.|  
|Navegação com teclas de direção|- A navegação com <xref:System.Windows.Forms.Integration.WindowsFormsHost> teclas de seta no controle é a mesma de um controle de contêiner windows forms comum: as teclas SETA PARA CIMA e SETA ESQUERDA selecionam o controle anterior, e as teclas SETA PARA BAIXO e SETA DIREITA selecionam o próximo controle.<br />- As teclas SETA PARA CIMA e SETA ESQUERDA do primeiro controle contido no <xref:System.Windows.Forms.Integration.WindowsFormsHost> controle executam a mesma ação que o atalho do teclado SHIFT+TAB. Se houver um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] controle focalizado, <xref:System.Windows.Forms.Integration.WindowsFormsHost> o foco se move para fora do controle. Esse comportamento difere do <xref:System.Windows.Forms.ContainerControl> comportamento padrão na forma de não haver embrulho até o último controle. Se não houver [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] outro controle focalinável, o foco retorna ao último controle do Windows Forms na ordem da guia.<br />- As teclas SETA PARA BAIXO e SETA DIREITA do último controle contido no <xref:System.Windows.Forms.Integration.WindowsFormsHost> controle executam a mesma ação que a tecla TAB. Se houver um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] controle focalizado, <xref:System.Windows.Forms.Integration.WindowsFormsHost> o foco se move para fora do controle. Esse comportamento difere do <xref:System.Windows.Forms.ContainerControl> comportamento padrão na forma de não haver embrulho ao primeiro controle. Se não houver [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] outro controle focalinável, o foco retorna ao primeiro controle do Windows Forms na ordem da guia.|Não aplicável.|  
|Aceleradores|Aceleradores funcionam como de costume, exceto onde observado na coluna "Sem suporte".|Aceleradores duplicados entre tecnologias não funcionam como aceleradores duplicados comuns. Quando um acelerador é duplicado entre tecnologias, com pelo menos um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] em um controle do Windows Forms e outro em um controle, o controle do Windows Forms sempre recebe o acelerador. O foco não alterna entre os controles quando o acelerador duplicado é pressionado.|  
|Teclas de atalho|Teclas de atalho funcionam como de costume, exceto onde observado na coluna "Sem suporte".|- As teclas de atalho do Windows Forms que são [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] manuseadas na fase de pré-processamento sempre têm precedência sobre as teclas de atalho. Por exemplo, se <xref:System.Windows.Forms.ToolStrip> você tiver um controle com teclas de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] atalho CTRL+S definidas <xref:System.Windows.Forms.ToolStrip> e houver um comando vinculado ao CTRL+S, o manipulador de controle é sempre invocado primeiro, independentemente do foco.<br />- As teclas de atalho <xref:System.Windows.Forms.Control.KeyDown> do Windows Forms [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]que são tratadas pelo evento são processadas por último em . Você pode prevenir esse comportamento substituindo o <xref:System.Windows.Forms.Control.IsInputKey%2A> método do <xref:System.Windows.Forms.Control.PreviewKeyDown> controle do Windows Forms ou manipulando o evento. Retornar `true` do <xref:System.Windows.Forms.Control.IsInputKey%2A> método ou definir o <xref:System.Windows.Forms.PreviewKeyDownEventArgs.IsInputKey%2A?displayProperty=nameWithType> valor `true` da <xref:System.Windows.Forms.Control.PreviewKeyDown> propriedade para o manipulador de eventos.|  
|AcceptsReturn, AcceptsTab e outros comportamentos de controle específicos|Propriedades que alteram o comportamento padrão do teclado funcionam normalmente, assumindo que o controle do Windows Forms substitui o <xref:System.Windows.Forms.Control.IsInputKey%2A> método de retorno `true`.|Os controles do Windows Forms que alteram o comportamento padrão do teclado ao manusear o <xref:System.Windows.Forms.Control.KeyDown> evento são processados por último no controle do host. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Como esses controles são processados por último, eles podem produzir um comportamento inesperado.|  
|Entrar e sair de eventos|Quando o foco não está <xref:System.Windows.Forms.Integration.ElementHost> indo para o controle de contenção, os <xref:System.Windows.Forms.Integration.WindowsFormsHost> eventos Enter and Leave são levantados como de costume quando o foco muda em um único controle.|Os eventos Enter e Leave não são acionados quando ocorrem as seguintes alterações de foco:<br /><br /> - De dentro <xref:System.Windows.Forms.Integration.WindowsFormsHost> para fora de um controle.<br />- De fora <xref:System.Windows.Forms.Integration.WindowsFormsHost> para dentro de um controle.<br />Fora de <xref:System.Windows.Forms.Integration.WindowsFormsHost> um controle.<br />- De um controle do <xref:System.Windows.Forms.Integration.WindowsFormsHost> Windows Forms <xref:System.Windows.Forms.Integration.ElementHost> hospedado em um <xref:System.Windows.Forms.Integration.WindowsFormsHost>controle para um controle hospedado dentro do mesmo .|  
|Multithreading|Todas as variedades de multithreading têm suporte.|Tanto os Formulários do Windows quanto [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] as tecnologias assumem um modelo de concorrência de um único segmento. Durante a depuração, chamadas para objetos do framework de outros segmentos disparará uma exceção para impor essa exigência.|  
|Segurança|Todos os cenários de interoperação requerem confiança total.|Nenhum cenário de interoperação é permitido em confiança parcial.|  
|Acessibilidade|Todos os cenários de acessibilidade tem suporte. Os produtos de tecnologia assistiva funcionam corretamente quando são usados para aplicações híbridas que contêm formulários e [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] controles do Windows.|Não aplicável.|  
|Área de transferência|Todas as operações da área de transferência funcionam como de costume. Isso inclui corte e cola entre [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] formulários do Windows e controles.|Não aplicável.|  
|Recurso do tipo "arrastar e soltar"|Todas as operações do tipo "arrastar e soltar" funcionam como de costume. Isso inclui operações entre [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] formulários do Windows e controles.|Não aplicável.|  
  
<a name="Windows_Forms_Application_Hosting_Windows"></a>
## <a name="hosting-wpf-controls-in-windows-forms"></a>Hospedando Controles de WPF nos Windows Forms  
 Os seguintes cenários de interoperação são [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] suportados quando um controle do Windows Forms hospeda um controle:  
  
- Hospedando um ou mais controles [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] usando código.  
  
- Associar uma folha de propriedades com um ou mais controles [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hospedados.  
  
- Hospedando um ou mais páginas [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] em um formulário.  
  
- Iniciando uma janela [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
- Hospedando um formulário mestre/detalhe [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] com um mestre e detalhes do Windows Forms.  
  
- Hospedando um formulário [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] mestre/detalhe com detalhes de um mestre e formulários do Windows.  
  
- Hospedando controles [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] personalizados.  
  
- Hospedando controles híbridos.  
  
### <a name="ambient-properties"></a>Propriedades de ambiente  
 Algumas das propriedades ambientais dos controles [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] do Windows Forms têm equivalentes. Essas propriedades ambientais são propagadas [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] para os controles hospedados <xref:System.Windows.Forms.Integration.ElementHost> e expostas como propriedades públicas no controle. O <xref:System.Windows.Forms.Integration.ElementHost> controle traduz cada propriedade ambiente [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] do Windows Forms para o seu equivalente.  
  
 Para mais informações, consulte [Windows Forms e mapeamento de propriedade do WPF](windows-forms-and-wpf-property-mapping.md).  
  
### <a name="behavior"></a>Comportamento  
 A tabela a seguir descreve o comportamento de interoperação.  
  
|Comportamento|Com suporte|Sem suporte|  
|--------------|---------------|-------------------|  
|Transparência|[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] renderização de controle dá suporte à transparência. O plano de fundo do controle pai do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Windows Forms pode se tornar o plano de fundo dos controles hospedados.|Não aplicável.|  
|Multithreading|Todas as variedades de multithreading têm suporte.|Tanto os Formulários do Windows quanto [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] as tecnologias assumem um modelo de concorrência de um único segmento. Durante a depuração, chamadas para objetos do framework de outros segmentos disparará uma exceção para impor essa exigência.|  
|Segurança|Todos os cenários de interoperação requerem confiança total.|Nenhum cenário de interoperação é permitido em confiança parcial.|  
|Acessibilidade|Todos os cenários de acessibilidade tem suporte. Os produtos de tecnologia assistiva funcionam corretamente quando são usados para aplicações híbridas que contêm formulários e [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] controles do Windows.|Não aplicável.|  
|Área de transferência|Todas as operações da área de transferência funcionam como de costume. Isso inclui corte e cola entre [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] formulários do Windows e controles.|Não aplicável.|  
|Recurso do tipo "arrastar e soltar"|Todas as operações do tipo "arrastar e soltar" funcionam como de costume. Isso inclui operações entre [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] formulários do Windows e controles.|Não aplicável.|  
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Instruções passo a passo: hospedando um controle dos Windows Forms no WPF](walkthrough-hosting-a-windows-forms-control-in-wpf.md)
- [Instruções passo a passo: hospedando um controle composto dos Windows Forms no WPF](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [Instruções passo a passo: hospedando um controle composto do WPF nos Windows Forms](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [Windows Forms e mapeamento de propriedade do WPF](windows-forms-and-wpf-property-mapping.md)
