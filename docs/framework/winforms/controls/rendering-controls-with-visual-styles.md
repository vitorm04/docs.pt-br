---
title: Renderizando controles com estilos visuais
ms.date: 03/30/2017
helpviewer_keywords:
- professional appearance [Windows Forms], rendering Windows Forms controls
- themes [Windows Forms], XP visual styles in Window Forms
- custom controls [Windows Forms], rendering
- custom controls [Windows Forms], painting
- visual themes [Windows Forms], rendering Windows Forms controls
- user controls [Windows Forms], painting
- visual styles [Windows Forms], rendering Windows Forms controls
ms.assetid: a5b178ba-610e-46c4-a6c0-509c0886a744
ms.openlocfilehash: 32bcbab585c39be4a72150bf49820d4a16f1691f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968245"
---
# <a name="rendering-controls-with-visual-styles"></a>Renderizando controles com estilos visuais
O .NET Framework fornece suporte para controles de renderização e outros elementos da interface do usuário do Windows usando estilos visuais em sistemas operacionais que dão suporte a eles. Este tópico discute os vários níveis de suporte no .NET Framework para processamento de controles e outros elementos de interface do usuário com o estilo visual atual do sistema operacional.  
  
## <a name="rendering-classes-for-common-controls"></a>Classes de renderização para controles comuns  
 Renderizar um controle refere-se a desenhar a interface do usuário de um controle. O <xref:System.Windows.Forms?displayProperty=nameWithType> namespace fornece a <xref:System.Windows.Forms.ControlPaint> classe para renderizar alguns controles de Windows Forms comuns. No entanto, essa classe desenha controles no estilo clássico do Windows, o que pode dificultar a manutenção de uma experiência de interface do usuário consistente ao desenhar controles personalizados em aplicativos com os estilos visuais habilitados.  
  
 O .NET Framework 2,0 inclui classes no <xref:System.Windows.Forms?displayProperty=nameWithType> namespace que processam as partes e os Estados de controles comuns com estilos visuais. Cada uma dessas classes inclui métodos `static` para desenhar o controle ou partes do controle em um estado específico com o estilo visual atual do sistema operacional.  
  
 Algumas dessas classes foram projetadas para desenhar o controle relacionado independentemente de estilos visuais estarem disponíveis. Se os estilos visuais estiverem habilitados, os membros da classe desenharão o controle relacionado com estilos visuais. Se os estilos visuais estiverem desabilitados, os membros da classe desenharão o controle no estilo clássico do Windows. Essas classes incluem:  
  
- <xref:System.Windows.Forms.ButtonRenderer>  
  
- <xref:System.Windows.Forms.CheckBoxRenderer>  
  
- <xref:System.Windows.Forms.GroupBoxRenderer>  
  
- <xref:System.Windows.Forms.RadioButtonRenderer>  
  
 Outras classes só podem desenhar o controle relacionado quando os estilos visuais estiverem disponíveis e seus membros lançarão uma exceção se os estilos visuais estiverem desabilitados. Essas classes incluem:  
  
- <xref:System.Windows.Forms.ComboBoxRenderer>  
  
- <xref:System.Windows.Forms.ProgressBarRenderer>  
  
- <xref:System.Windows.Forms.ScrollBarRenderer>  
  
- <xref:System.Windows.Forms.TabRenderer>  
  
- <xref:System.Windows.Forms.TextBoxRenderer>  
  
- <xref:System.Windows.Forms.TrackBarRenderer>  
  
 Para obter mais informações sobre como usar essas classes para desenhar um controle [, consulte Como: Use uma classe](how-to-use-a-control-rendering-class.md)de renderização de controle.  
  
## <a name="visual-style-element-and-rendering-classes"></a>Elemento de estilo visual e classes de renderização  
 O <xref:System.Windows.Forms.VisualStyles?displayProperty=nameWithType> namespace inclui classes que podem ser usadas para desenhar e obter informações sobre qualquer controle ou elemento de interface do usuário com suporte em estilos visuais. Os controles com suporte incluem controles comuns que têm uma classe de <xref:System.Windows.Forms?displayProperty=nameWithType> renderização no namespace (consulte a seção anterior), bem como outros controles, como controles de guia e controles Rebar. Outros elementos de interface do usuário com suporte incluem as partes do menu **Iniciar**, a barra de tarefas e a área não cliente do Windows.  
  
 As classes principais do <xref:System.Windows.Forms.VisualStyles?displayProperty=nameWithType> namespace são <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> e <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer>. <xref:System.Windows.Forms.VisualStyles.VisualStyleElement>é uma classe base para identificar qualquer elemento de controle ou de interface do usuário com suporte dos estilos visuais. <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> Além disso <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> , o <xref:System.Windows.Forms.VisualStyles?displayProperty=nameWithType> namespace inclui muitas classes aninhadas de <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> com `static` propriedades que retornam um para cada Estado de um controle, parte de controle ou outro elemento de interface do usuário com suporte no Visual estilos.  
  
 <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer>fornece os métodos que desenham e obtêm <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> informações sobre cada um definido pelo estilo visual atual do sistema operacional. Informações que podem ser recuperadas sobre um elemento incluem seu tamanho padrão, o tipo de tela de fundo e definições de cores. <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer>encapsula a funcionalidade da API de estilos visuais (UxTheme) da parte do shell do Windows do SDK da plataforma Windows. Para obter mais informações, consulte [habilitando estilos visuais](/windows/desktop/controls/cookbook-overview).  
  
 Para obter mais informações sobre <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> como <xref:System.Windows.Forms.VisualStyles.VisualStyleElement>usar o [e o, consulte Como: Renderizar um elemento](how-to-render-a-visual-style-element.md)de estilo visual.  
  
## <a name="enabling-visual-styles"></a>Habilitar estilos visuais  
 Para Habilitar estilos visuais para um aplicativo escrito para o .NET Framework versão 1,0, os programadores devem incluir um manifesto do aplicativo que especifica que o ComCtl32. dll versão 6 ou posterior será usado para desenhar controles. Aplicativos criados com o .NET Framework versão 1,1 ou posterior podem usar o <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> método <xref:System.Windows.Forms.Application> da classe.  
  
## <a name="checking-for-visual-styles-support"></a>Verificando se há suporte para estilos visuais  
 A <xref:System.Windows.Forms.Application.RenderWithVisualStyles%2A> propriedade<xref:System.Windows.Forms.Application> da classe indica se o aplicativo atual está desenhando controles com estilos visuais. Ao pintar um controle personalizado, você pode verificar o valor de <xref:System.Windows.Forms.Application.RenderWithVisualStyles%2A> para determinar se você deve renderizar seu controle com ou sem estilos visuais. A tabela a seguir lista as quatro condições que devem existir <xref:System.Windows.Forms.Application.RenderWithVisualStyles%2A> para que `true`o seja retornado.  
  
|Condição|Observações|  
|---------------|-----------|  
|O sistema operacional dá suporte a estilos visuais.|Para verificar essa condição separadamente, use a <xref:System.Windows.Forms.VisualStyles.VisualStyleInformation.IsSupportedByOS%2A> propriedade <xref:System.Windows.Forms.VisualStyles.VisualStyleInformation> da classe.|  
|O usuário habilitou estilos visuais no sistema operacional.|Para verificar essa condição separadamente, use a <xref:System.Windows.Forms.VisualStyles.VisualStyleInformation.IsEnabledByUser%2A> propriedade <xref:System.Windows.Forms.VisualStyles.VisualStyleInformation> da classe.|  
|Os estilos visuais estão habilitados no aplicativo.|Os estilos visuais podem ser habilitados em um aplicativo chamando <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> o método ou usando um manifesto do aplicativo que especifica que o Comctl32. dll versão 6 ou posterior será usado para desenhar controles.|  
|Os estilos visuais estão sendo usados para desenhar a área de cliente das janelas de aplicativos.|Para verificar essa condição separadamente, use a <xref:System.Windows.Forms.Application.VisualStyleState%2A> propriedade <xref:System.Windows.Forms.Application> da classe e verifique se ela tem o valor <xref:System.Windows.Forms.VisualStyles.VisualStyleState.ClientAreaEnabled?displayProperty=nameWithType> ou <xref:System.Windows.Forms.VisualStyles.VisualStyleState.ClientAndNonClientAreasEnabled?displayProperty=nameWithType>.|  
  
 Para determinar quando um usuário habilita ou desabilita estilos visuais, ou alterna de um estilo visual para outro, verifique o <xref:Microsoft.Win32.UserPreferenceCategory.VisualStyle?displayProperty=nameWithType> valor nos manipuladores para os <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanging?displayProperty=nameWithType> eventos ou <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged?displayProperty=nameWithType> .  
  
> [!IMPORTANT]
> Se você quiser usar <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> o para renderizar um controle ou elemento de interface de usuário quando o usuário habilitar ou alternar estilos visuais, certifique-se de fazer isso ao manipular o <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanging> <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> evento em vez do evento. Uma exceção será gerada se você usar a <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> classe ao manipular. <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanging>  
  
## <a name="see-also"></a>Consulte também

- [Pintura e renderização de controle personalizado](custom-control-painting-and-rendering.md)
