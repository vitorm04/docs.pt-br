---
title: WPF e Windows Forms Interop
titleSuffix: ''
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms [WPF], interoperability with
- nester interoperation [WPF]
- Windows Forms [WPF], WPF interoperation
- interoperability [WPF], Windows Forms
- hybrid control [WPF interoperability]
ms.assetid: 9e8aa6b6-112c-4579-98d1-c974917df499
ms.openlocfilehash: 2dc2ea10ce8f723a0ee34c4774253e1357ba6afa
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76735123"
---
# <a name="wpf-and-windows-forms-interoperation"></a>Interoperação do WPF e dos Windows Forms
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] e [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] apresentam duas diferentes arquiteturas para criação de interfaces de aplicativo. O namespace <xref:System.Windows.Forms.Integration?displayProperty=nameWithType> fornece classes que habilitam cenários comuns de interoperação. As duas classes principais que implementam recursos de interoperação são <xref:System.Windows.Forms.Integration.WindowsFormsHost> e <xref:System.Windows.Forms.Integration.ElementHost>. Este tópico descreve quais cenários de interoperação tem suporte e quais cenários não tem suporte.  
  
> [!NOTE]
> Uma consideração especial é fornecida para o cenário de *controle híbrido*. Um controle híbrido tem um controle de uma tecnologia aninhado em um controle da outra tecnologia. Isso também é chamado um *interoperação aninhada*. Um *controle multinível híbrido* tem mais de um nível de aninhamento híbrido de controles. Um exemplo de interoperação multinível aninhada é um [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controle que contém um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] controle, que contém outro [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controle. Controles híbridos multinível não tem suporte.  

<a name="Windows_Presentation_Foundation_Application_Hosting"></a>   
## <a name="hosting-windows-forms-controls-in-wpf"></a>Hospedando controle dos Windows Forms no WPF  
 Os cenários de interoperação a seguir têm suporte quando um controle de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hospeda um controle de Windows Forms:  
  
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
 A lista a seguir descreve as limitações conhecidas quando o elemento <xref:System.Windows.Forms.Integration.WindowsFormsHost> tenta integrar seu controle de [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] hospedado ao sistema de layout de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
- Em alguns casos, os controles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] não podem ser redimensionados ou podem ser dimensionados somente para dimensões específicas. Por exemplo, um controle de <xref:System.Windows.Forms.ComboBox> [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] dá suporte a apenas uma única altura, que é definida pelo tamanho da fonte do controle. Em um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] layout dinâmico, que assume que os elementos podem ser ampliados verticalmente, um controle de <xref:System.Windows.Forms.ComboBox> hospedado não será ampliado conforme o esperado.  
  
- Os controles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] não podem ser girados ou inclinados. Por exemplo, quando você rotaciona sua interface do usuário em 90 graus, os controles hospedados [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] manterão sua posição vertical.  
  
- Na maioria dos casos, os controles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] não dão suporte ao dimensionamento proporcional. Embora as dimensões gerais do controle sejam dimensionadas, os controles filho e os elementos de componentes do controle podem não ser redimensionados conforme o esperado. Essa limitação depende de quanto cada controle [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] dá suporte ao dimensionamento.  
  
- Em uma interface do usuário [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], você pode alterar a ordem z dos elementos para controlar o comportamento de sobreposição. Um controle [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] hospedado é desenhado em uma HWND separada, portanto, é sempre desenhado na parte superior dos elementos [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
- [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controles oferecem suporte a dimensionamento automático com base no tamanho da fonte. Em uma interface do usuário [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], alterar o tamanho da fonte não redimensiona o layout inteiro, embora elementos individuais possam redimensionar dinamicamente.  
  
### <a name="ambient-properties"></a>Propriedades de ambiente  
 Algumas das propriedades de ambiente dos controles [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] têm [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] equivalentes. Essas propriedades de ambiente são propagadas para os controles de [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] hospedados e expostas como propriedades públicas no controle de <xref:System.Windows.Forms.Integration.WindowsFormsHost>. O controle de <xref:System.Windows.Forms.Integration.WindowsFormsHost> converte cada propriedade de ambiente [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] em sua [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] equivalente.  
  
 Para mais informações, consulte [Windows Forms e mapeamento de propriedade do WPF](windows-forms-and-wpf-property-mapping.md).  
  
### <a name="behavior"></a>Comportamento  
 A tabela a seguir descreve o comportamento de interoperação.  
  
|Comportamento|Com suporte|Sem suporte|  
|--------------|---------------|-------------------|  
|Transparência|[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] renderização de controle dá suporte à transparência. A tela de fundo do controle pai [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pode se tornar a tela de fundo de controles hospedados [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].|Alguns [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controles não dão suporte a transparência. Por exemplo, os controles <xref:System.Windows.Forms.TextBox> e <xref:System.Windows.Forms.ComboBox> não serão transparentes quando hospedados por [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].|  
|Tabulação|Ordem de tabulação para controles hospedados [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] é igual a quando esses controles são hospedados em um aplicativo baseado em [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].<br /><br /> Tabulação de um controle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] para um controle [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] com a tecla TAB e teclas SHIFT + TAB funciona da maneira habitual.<br /><br /> [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controles que têm um valor de propriedade <xref:System.Windows.Forms.Control.TabStop%2A> de `false` não recebem o foco quando o usuário faz a Tabulação pelos controles.<br /><br /> -Cada controle de <xref:System.Windows.Forms.Integration.WindowsFormsHost> tem um valor de <xref:System.Windows.Forms.Integration.WindowsFormsHost.TabIndex%2A>, que determina quando o controle de <xref:System.Windows.Forms.Integration.WindowsFormsHost> receberá o foco.<br />-   [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controles contidos dentro de um contêiner de <xref:System.Windows.Forms.Integration.WindowsFormsHost> seguem a ordem especificada pela propriedade <xref:System.Windows.Forms.Control.TabIndex%2A>. Fazer tabulação do último índice de tabulação coloca o foco no próximo contorle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], se houver. Se nenhum outro controle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de foco existir, a tabulação retornará para o primeiro [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controle na ordem de tabulação.<br />-   valores de <xref:System.Windows.Forms.Integration.WindowsFormsHost.TabIndex%2A> para controles dentro da <xref:System.Windows.Forms.Integration.WindowsFormsHost> são relativos aos controles de [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] irmãos contidos no controle <xref:System.Windows.Forms.Integration.WindowsFormsHost>.<br />- A tabulação honra o comportamento específico de controle. Por exemplo, pressionar a tecla TAB em um controle <xref:System.Windows.Forms.TextBox> que tem um valor de propriedade <xref:System.Windows.Forms.TextBoxBase.AcceptsTab%2A> de `true` insere uma guia na caixa de texto em vez de mover o foco.|{1&gt;Não aplicável.&lt;1}|  
|Navegação com teclas de direção|-A navegação com as teclas de direção no controle de <xref:System.Windows.Forms.Integration.WindowsFormsHost> é a mesma que em um controle de contêiner de [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] comum: as teclas seta para cima e seta para a esquerda selecionam o controle anterior e as teclas seta para baixo e seta para a direita selecionam o próximo controle.<br />-As teclas de seta para cima e seta para a esquerda do primeiro controle contido no controle de <xref:System.Windows.Forms.Integration.WindowsFormsHost> executam a mesma ação que o atalho de teclado SHIFT + TAB. Se houver um controle de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] com foco, o foco se moverá para fora do controle de <xref:System.Windows.Forms.Integration.WindowsFormsHost>. Esse comportamento é diferente do comportamento de <xref:System.Windows.Forms.ContainerControl> padrão, pois não ocorre nenhum encapsulamento para o último controle. Se nenhum outro controle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] com foco existir, a tabulação retornará para o último controle [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] na ordem de tabulação.<br />-As teclas de seta para baixo e de seta para a direita do último controle contido no controle de <xref:System.Windows.Forms.Integration.WindowsFormsHost> executam a mesma ação que a tecla TAB. Se houver um controle de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] com foco, o foco se moverá para fora do controle de <xref:System.Windows.Forms.Integration.WindowsFormsHost>. Esse comportamento é diferente do comportamento de <xref:System.Windows.Forms.ContainerControl> padrão, pois não ocorre nenhum encapsulamento para o primeiro controle. Se nenhum outro controle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] com foco existir, o foco retorna para o último controle [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] na ordem de tabulação.|{1&gt;Não aplicável.&lt;1}|  
|Aceleradores|Aceleradores funcionam como de costume, exceto onde observado na coluna "Sem suporte".|Aceleradores duplicados entre tecnologias não funcionam como aceleradores duplicados comuns. Quando um acelerador é duplicado entre tecnologias, com, pelo menos, um em um controle de [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] e o outro em um controle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], o controle [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] sempre recebe o acelerador. O foco não alterna entre os controles quando o acelerador duplicado é pressionado.|  
|Teclas de atalho|Teclas de atalho funcionam como de costume, exceto onde observado na coluna "Sem suporte".|-   [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] teclas de atalho que são tratadas no estágio de pré-processamento sempre têm precedência sobre [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] teclas de atalho. Por exemplo, se você tiver um controle de <xref:System.Windows.Forms.ToolStrip> com as teclas de atalho CTRL + S definidas e houver um comando [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] associado a CTRL + S, o manipulador de controle de <xref:System.Windows.Forms.ToolStrip> será sempre invocado primeiro, independentemente do foco.<br />-   [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] teclas de atalho que são manipuladas pelo evento <xref:System.Windows.Forms.Control.KeyDown> são processadas por último no [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Você pode evitar esse comportamento substituindo o método <xref:System.Windows.Forms.Control.IsInputKey%2A> do controle de [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ou manipulando o evento <xref:System.Windows.Forms.Control.PreviewKeyDown>. Retorne `true` do método <xref:System.Windows.Forms.Control.IsInputKey%2A> ou defina o valor da propriedade <xref:System.Windows.Forms.PreviewKeyDownEventArgs.IsInputKey%2A?displayProperty=nameWithType> como `true` no manipulador de eventos <xref:System.Windows.Forms.Control.PreviewKeyDown>.|  
|AcceptsReturn, AcceptsTab e outros comportamentos de controle específicos|As propriedades que alteram o comportamento padrão do teclado funcionam como de costume, supondo que o controle de [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] substitua o método <xref:System.Windows.Forms.Control.IsInputKey%2A> para retornar `true`.|[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controles que alteram o comportamento de teclado padrão manipulando o evento <xref:System.Windows.Forms.Control.KeyDown> são processados por último no controle de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] do host. Como esses controles são processados por último, eles podem produzir um comportamento inesperado.|  
|Entrar e sair de eventos|Quando o foco não vai para o controle de <xref:System.Windows.Forms.Integration.ElementHost> que o contém, os eventos Enter e Leave são gerados como de costume quando o foco é alterado em um único controle de <xref:System.Windows.Forms.Integration.WindowsFormsHost>.|Os eventos Enter e Leave não são acionados quando ocorrem as seguintes alterações de foco:<br /><br /> -De dentro para fora de um controle de <xref:System.Windows.Forms.Integration.WindowsFormsHost>.<br />-De fora para dentro de um controle de <xref:System.Windows.Forms.Integration.WindowsFormsHost>.<br />-Fora de um controle de <xref:System.Windows.Forms.Integration.WindowsFormsHost>.<br />-De um controle de [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] hospedado em um controle de <xref:System.Windows.Forms.Integration.WindowsFormsHost> para um controle de <xref:System.Windows.Forms.Integration.ElementHost> hospedado dentro do mesmo <xref:System.Windows.Forms.Integration.WindowsFormsHost>.|  
|Multithreading|Todas as variedades de multithreading têm suporte.|As tecnologias [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] e [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] supõem um modelo de simultaneidade de segmento único. Durante a depuração, chamadas para objetos do framework de outros segmentos disparará uma exceção para impor essa exigência.|  
|Segurança|Todos os cenários de interoperação requerem confiança total.|Nenhum cenário de interoperação é permitido em confiança parcial.|  
|Acessibilidade|Todos os cenários de acessibilidade tem suporte. Produtos de tecnologia assistencial funcionam corretamente quando eles são usados para aplicativos híbridos que contêm os controles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] e [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].|{1&gt;Não aplicável.&lt;1}|  
|Área de Transferência|Todas as operações da área de transferência funcionam como de costume. Isso inclui recorte e colagem entre os controles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] e [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].|{1&gt;Não aplicável.&lt;1}|  
|Recurso do tipo "arrastar e soltar"|Todas as operações do tipo "arrastar e soltar" funcionam como de costume. Isso inclui operações entre os controles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] e [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].|{1&gt;Não aplicável.&lt;1}|  
  
<a name="Windows_Forms_Application_Hosting_Windows"></a>   
## <a name="hosting-wpf-controls-in-windows-forms"></a>Hospedando Controles de WPF nos Windows Forms  
 Os cenários de interoperação a seguir têm suporte quando um controle de Windows Forms hospeda um controle de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]:  
  
- Hospedando um ou mais controles [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] usando código.  
  
- Associar uma folha de propriedades com um ou mais controles [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hospedados.  
  
- Hospedando um ou mais páginas [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] em um formulário.  
  
- Iniciando uma janela [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
- Hospedando um formulário mestre/detalhes com um [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] mestre e [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] detalhes.  
  
- Hospedando um formulário mestre/detalhes com um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] mestre e [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] detalhes.  
  
- Hospedando controles [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] personalizados.  
  
- Hospedando controles híbridos.  
  
### <a name="ambient-properties"></a>Propriedades de ambiente  
 Algumas das propriedades de ambiente dos controles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] têm [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] equivalentes. Essas propriedades de ambiente são propagadas para os controles de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hospedados e expostas como propriedades públicas no controle de <xref:System.Windows.Forms.Integration.ElementHost>. O controle de <xref:System.Windows.Forms.Integration.ElementHost> converte cada propriedade de ambiente [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] para seu equivalente [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 Para mais informações, consulte [Windows Forms e mapeamento de propriedade do WPF](windows-forms-and-wpf-property-mapping.md).  
  
### <a name="behavior"></a>Comportamento  
 A tabela a seguir descreve o comportamento de interoperação.  
  
|Comportamento|Com suporte|Sem suporte|  
|--------------|---------------|-------------------|  
|Transparência|[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] renderização de controle dá suporte à transparência. A tela de fundo do controle pai [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] pode se tornar a tela de fundo de controles hospedados [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].|{1&gt;Não aplicável.&lt;1}|  
|Multithreading|Todas as variedades de multithreading têm suporte.|As tecnologias [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] e [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] supõem um modelo de simultaneidade de segmento único. Durante a depuração, chamadas para objetos do framework de outros segmentos disparará uma exceção para impor essa exigência.|  
|Segurança|Todos os cenários de interoperação requerem confiança total.|Nenhum cenário de interoperação é permitido em confiança parcial.|  
|Acessibilidade|Todos os cenários de acessibilidade tem suporte. Produtos de tecnologia assistencial funcionam corretamente quando eles são usados para aplicativos híbridos que contêm os controles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] e [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].|{1&gt;Não aplicável.&lt;1}|  
|Área de Transferência|Todas as operações da área de transferência funcionam como de costume. Isso inclui recorte e colagem entre os controles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] e [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].|{1&gt;Não aplicável.&lt;1}|  
|Recurso do tipo "arrastar e soltar"|Todas as operações do tipo "arrastar e soltar" funcionam como de costume. Isso inclui operações entre os controles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] e [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].|{1&gt;Não aplicável.&lt;1}|  
  
## <a name="see-also"></a>Veja também

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Passo a passo: hospedando um controle do Windows Forms no WPF](walkthrough-hosting-a-windows-forms-control-in-wpf.md)
- [Passo a passo: hospedando um controle composto do Windows Forms no WPF](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [Passo a passo: hospedando um controle composto do WPF no Windows Forms](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [Windows Forms e mapeamento de propriedade do WPF](windows-forms-and-wpf-property-mapping.md)
