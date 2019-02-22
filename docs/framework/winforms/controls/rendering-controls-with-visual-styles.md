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
ms.openlocfilehash: 9ee357e343c5e060393359f0666886bef6b87b50
ms.sourcegitcommit: 2b986afe4ce9e13bbeec929c9737757eb61de60e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56664348"
---
# <a name="rendering-controls-with-visual-styles"></a>Renderizando controles com estilos visuais
O [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] dá suporte à renderização de controles e outros elementos da interface do usuário do Windows usando estilos visuais em sistemas operacionais que dão suporte a eles. Este tópico discute os vários níveis de suporte no [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] para renderizar controles e outros elementos da interface do usuário com o estilo visual atual do sistema operacional.  
  
## <a name="rendering-classes-for-common-controls"></a>Classes de renderização para controles comuns  
 Renderizar um controle refere-se a desenhar a interface do usuário de um controle. O <xref:System.Windows.Forms?displayProperty=nameWithType> namespace fornece o <xref:System.Windows.Forms.ControlPaint> classe para alguns comuns de renderização controles de formulários do Windows. No entanto, essa classe desenha controles no estilo clássico do Windows, o que pode dificultar a manutenção de uma experiência de interface do usuário consistente ao desenhar controles personalizados em aplicativos com os estilos visuais habilitados.  
  
 O [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)] inclui classes de <xref:System.Windows.Forms?displayProperty=nameWithType> namespace que renderizam as partes e estados dos controles comuns com estilos visuais. Cada uma dessas classes inclui métodos `static` para desenhar o controle ou partes do controle em um estado específico com o estilo visual atual do sistema operacional.  
  
 Algumas dessas classes foram projetadas para desenhar o controle relacionado independentemente de estilos visuais estarem disponíveis. Se os estilos visuais estiverem habilitados, os membros da classe desenharão o controle relacionado com estilos visuais. Se os estilos visuais estiverem desabilitados, os membros da classe desenharão o controle no estilo clássico do Windows. Essas classes incluem:  
  
-   <xref:System.Windows.Forms.ButtonRenderer>  
  
-   <xref:System.Windows.Forms.CheckBoxRenderer>  
  
-   <xref:System.Windows.Forms.GroupBoxRenderer>  
  
-   <xref:System.Windows.Forms.RadioButtonRenderer>  
  
 Outras classes só podem desenhar o controle relacionado quando os estilos visuais estiverem disponíveis e seus membros lançarão uma exceção se os estilos visuais estiverem desabilitados. Essas classes incluem:  
  
-   <xref:System.Windows.Forms.ComboBoxRenderer>  
  
-   <xref:System.Windows.Forms.ProgressBarRenderer>  
  
-   <xref:System.Windows.Forms.ScrollBarRenderer>  
  
-   <xref:System.Windows.Forms.TabRenderer>  
  
-   <xref:System.Windows.Forms.TextBoxRenderer>  
  
-   <xref:System.Windows.Forms.TrackBarRenderer>  
  
 Para obter mais informações sobre como usar essas classes para desenhar um controle, consulte [como: Usar um classe de renderização do controle](../../../../docs/framework/winforms/controls/how-to-use-a-control-rendering-class.md).  
  
## <a name="visual-style-element-and-rendering-classes"></a>Elemento de estilo visual e classes de renderização  
 O <xref:System.Windows.Forms.VisualStyles?displayProperty=nameWithType> namespace inclui classes que podem ser usadas para desenhar e obter informações sobre qualquer controle ou elemento de interface do usuário que é compatível com estilos visuais. Controles com suporte incluem controles comuns que têm uma classe de renderização no <xref:System.Windows.Forms?displayProperty=nameWithType> namespace (consulte a seção anterior), bem como outros controles, como controles de guia e controles rebar. Outros elementos de interface do usuário com suporte incluem as partes do menu **Iniciar**, a barra de tarefas e a área não cliente do Windows.  
  
 As principais classes de <xref:System.Windows.Forms.VisualStyles?displayProperty=nameWithType> são do namespace <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> e <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer>. <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> é uma classe de base para identificar qualquer elemento de interface de usuário ou controle compatível com estilos visuais. Além <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> em si, o <xref:System.Windows.Forms.VisualStyles?displayProperty=nameWithType> namespace inclui muitas classes aninhadas de <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> com `static` propriedades que retornam um <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> para cada estado de um controle, parte do controle ou outro elemento de interface do usuário com suporte pelo visual estilos.  
  
 <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> fornece os métodos que desenhar e obtém informações sobre cada <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> definido pelo estilo visual atual do sistema operacional. Informações que podem ser recuperadas sobre um elemento incluem seu tamanho padrão, o tipo de tela de fundo e definições de cores. <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> encapsula a funcionalidade dos estilos visuais (UxTheme) API da parte do Shell do Windows do Windows Platform SDK. Para obter mais informações, consulte [habilitando estilos visuais](/windows/desktop/controls/cookbook-overview).  
  
 Para obter mais informações sobre como usar <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> e <xref:System.Windows.Forms.VisualStyles.VisualStyleElement>, consulte [como: Renderizar um elemento de estilo Visual](../../../../docs/framework/winforms/controls/how-to-render-a-visual-style-element.md).  
  
## <a name="enabling-visual-styles"></a>Habilitar estilos visuais  
 Para habilitar os estilos visuais para um aplicativo escrito para o [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] versão 1.0, os programadores devem incluir um manifesto do aplicativo que especifique que o ComCtl32.dll versão 6 ou posterior será usado para desenhar controles. Aplicativos criados com o [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] versão 1.1 ou posterior pode usar o <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> método da <xref:System.Windows.Forms.Application> classe.  
  
## <a name="checking-for-visual-styles-support"></a>Verificando se há suporte para estilos visuais  
 O <xref:System.Windows.Forms.Application.RenderWithVisualStyles%2A> propriedade do <xref:System.Windows.Forms.Application> classe indica se o aplicativo atual está desenhando controles com estilos visuais. Ao pintar um controle personalizado, você pode verificar o valor de <xref:System.Windows.Forms.Application.RenderWithVisualStyles%2A> para determinar se deve renderizar o controle com ou sem estilos visuais. A tabela a seguir lista as quatro condições que devem existir para <xref:System.Windows.Forms.Application.RenderWithVisualStyles%2A> para retornar `true`.  
  
|Condição|Observações|  
|---------------|-----------|  
|O sistema operacional dá suporte a estilos visuais.|Para verificar essa condição separadamente, use o <xref:System.Windows.Forms.VisualStyles.VisualStyleInformation.IsSupportedByOS%2A> propriedade do <xref:System.Windows.Forms.VisualStyles.VisualStyleInformation> classe.|  
|O usuário habilitou estilos visuais no sistema operacional.|Para verificar essa condição separadamente, use o <xref:System.Windows.Forms.VisualStyles.VisualStyleInformation.IsEnabledByUser%2A> propriedade do <xref:System.Windows.Forms.VisualStyles.VisualStyleInformation> classe.|  
|Os estilos visuais estão habilitados no aplicativo.|Estilos visuais podem ser habilitados em um aplicativo chamando o <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> método ou usando um aplicativo de manifesto que especifique que ComCtl32.dll versão 6 ou posterior será usado para desenhar controles.|  
|Os estilos visuais estão sendo usados para desenhar a área de cliente das janelas de aplicativos.|Para verificar essa condição separadamente, use o <xref:System.Windows.Forms.Application.VisualStyleState%2A> propriedade do <xref:System.Windows.Forms.Application> classe e verificar se ele tem o valor <xref:System.Windows.Forms.VisualStyles.VisualStyleState.ClientAreaEnabled?displayProperty=nameWithType> ou <xref:System.Windows.Forms.VisualStyles.VisualStyleState.ClientAndNonClientAreasEnabled?displayProperty=nameWithType>.|  
  
 Para determinar quando um usuário habilita ou desabilita os estilos visuais ou alterna de um estilo visual para outra, verifique para o <xref:Microsoft.Win32.UserPreferenceCategory.VisualStyle?displayProperty=nameWithType> valor nos manipuladores para o <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanging?displayProperty=nameWithType> ou <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged?displayProperty=nameWithType> eventos.  
  
> [!IMPORTANT]
>  Se você quiser usar <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> para renderizar um controle ou elemento de interface do usuário quando o usuário ativa ou alterna os estilos visuais, certifique-se de que você faça isso ao lidar com o <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> eventos em vez do <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanging> eventos. Uma exceção será gerada se você usar o <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> quando a manipulação de classe <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanging>.  
  
## <a name="see-also"></a>Consulte também
- [Pintura e renderização de controle personalizado](../../../../docs/framework/winforms/controls/custom-control-painting-and-rendering.md)
