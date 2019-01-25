---
title: TextPattern Visão geral de objetos inseridos
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, TextPattern class
- embedded objects, accessing
- accessing embedded objects
- embedded objects, UI Automation
ms.assetid: 93fdfbb9-0025-4b72-8ca0-0714adbb70d5
author: Xansky
ms.author: mhopkins
ms.openlocfilehash: 52077103277cdc4d32dfe3e44fcccffeec20295e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54706859"
---
# <a name="textpattern-and-embedded-objects-overview"></a>TextPattern Visão geral de objetos inseridos
> [!NOTE]
>  Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: Automação de interface do usuário](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Esta visão geral descreve como [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] expõe objetos inseridos, ou elementos filho, dentro de um documento de texto ou um contêiner.  
  
 Na [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] um objeto inserido é qualquer elemento que tenha limites não textuais; por exemplo, uma imagem, hiperlink, tabela ou documento digite como uma [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] planilha ou [!INCLUDE[TLA#tla_winmedia](../../../includes/tlasharptla-winmedia-md.md)] arquivo. Isso é diferente da definição padrão, em que um elemento é criado em um aplicativo e incorporado ou vinculado, dentro de outro. Se o objeto pode ser editado em seu aplicativo original é irrelevante no contexto de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].  
  
<a name="Embedded_Objects_and_the_UI_Automation_Tree"></a>   
## <a name="embedded-objects-and-the-ui-automation-tree"></a>Objetos inseridos e a árvore de automação de interface do usuário  
 Objetos inseridos são tratados como elementos individuais dentro da exibição de controle do [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] árvore. Eles são expostos como filhos do contêiner de texto para que eles podem ser acessados através do mesmo modelo como outros controles no [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].  
  
 ![Inserido de tabela com a imagem em um contêiner de texto](../../../docs/framework/ui-automation/media/uia-textpattern-embedded-objects-overview-example1.png "UIA_TextPattern_Embedded_Objects_Overview_Example1")  
Objetos inseridos de exemplo de um contêiner de texto com hiperlink, imagem e tabela  
  
 ![Modo de exibição para o exemplo anterior de conteúdo](../../../docs/framework/ui-automation/media/uia-textpattern-embedded-objects-overview-example2.PNG "UIA_TextPattern_Embedded_Objects_Overview_Example2")  
Exemplo de exibição de conteúdo para uma parte do contêiner de texto anterior  
  
<a name="Expose_Embedded_Objects_Using_TextPattern_and"></a>   
## <a name="expose-embedded-objects-using-textpattern-and-textpatternrange"></a>Expor objetos inseridos usando TextPattern e TextPatternRange  
 Usado em conjunto, o <xref:System.Windows.Automation.TextPattern> classe de padrão de controle e o <xref:System.Windows.Automation.Text.TextPatternRange> classe expõe métodos e propriedades que facilitam a navegação e a consulta de objetos inseridos.  
  
 O conteúdo textual (ou texto interno) de um contêiner de texto e um objeto inserido, como um hiperlink ou célula de tabela, é exposto como um fluxo de texto única e contínua na visualização de controle e exibição de conteúdo a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] de árvore; objeto limites são ignorados. Se um cliente de automação de interface do usuário está recuperando o texto com a finalidade de citar, interpretar ou analisar de alguma maneira, o intervalo de texto deve ser verificado para casos especiais, como uma tabela com textuais conteúdos ou outros objetos inseridos. Isso pode ser feito por meio da chamada <xref:System.Windows.Automation.Text.TextPatternRange.GetChildren%2A> para obter uma <xref:System.Windows.Automation.AutomationElement> para cada embedded objeto e, em seguida, chamar <xref:System.Windows.Automation.TextPattern.RangeFromChild%2A> para obter um intervalo de texto para cada elemento. Isso é feito recursivamente até que todo o conteúdo textual foi recuperado.  
  
 ![Intervalos de texto abrangidos por objetos inseridos. ](../../../docs/framework/ui-automation/media/uia-textpattern-embeddedobjecttextranges.png "UIA_TextPattern_EmbeddedObjectTextRanges")  
Exemplo de um fluxo de texto com objetos inseridos e seus intervalos abrangentes  
  
 Quando for necessário atravessar o conteúdo de um intervalo de texto, uma série de etapas envolvidas nos bastidores para que o <xref:System.Windows.Automation.Text.TextPatternRange.Move%2A> método a ser executado com êxito.  
  
1.  O intervalo de texto é normalizado; ou seja, o intervalo de texto é recolhido em um intervalo de degeneração a <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.Start> ponto de extremidade, o que torna o <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End> supérfluo de ponto de extremidade. Essa etapa é necessária para remover a ambiguidade em situações onde um intervalo de texto abrange <xref:System.Windows.Automation.Text.TextUnit> limites: por exemplo, `{The URL https://www.microsoft.com is embedded in text` onde "{" e "}" é o texto de pontos de extremidade do intervalo.  
  
2.  O intervalo resultante é movido para trás na <xref:System.Windows.Automation.TextPattern.DocumentRange%2A> para o início da solicitada <xref:System.Windows.Automation.Text.TextUnit> limites.  
  
3.  O intervalo é movido para frente ou para trás na <xref:System.Windows.Automation.TextPattern.DocumentRange%2A> pelo número solicitado de <xref:System.Windows.Automation.Text.TextUnit> limites.  
  
4.  O intervalo é expandido de um estado de intervalo de degeneração, em seguida, movendo o <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End> ponto de extremidade por um solicitado <xref:System.Windows.Automation.Text.TextUnit> limites.  
  
 ![Ajustes de intervalo por Move & ExpandToEnclosingUnit](../../../docs/framework/ui-automation/media/uia-textpattern-moveandexpand-examples.png "UIA_TextPattern_MoveAndExpand_Examples")  
Exemplos de como um intervalo de texto é ajustado para Move () e ExpandToEnclosingUnit)  
  
<a name="Common_Scenarios"></a>   
## <a name="common-scenarios"></a>Cenários comuns  
 As seções a seguir apresentam exemplos dos cenários mais comuns que envolvem objetos inseridos.  
  
 Legenda para os exemplos mostrados:  
  
 { = <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.Start>  
  
 } = <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End>  
  
### <a name="hyperlink"></a>Hiperlink  

**Exemplo 1 - um intervalo de texto que contém um hiperlink de texto inserido**
  
`{The URL https://www.microsoft.com is embedded in text}.`
  
|Método chamado|Resultado|  
|-------------------|------------|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetText%2A>|Retorna a cadeia de caracteres `The URL https://www.microsoft.com is embedded in text`.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>|Retorna o mais interno <xref:System.Windows.Automation.AutomationElement> que inclui o intervalo de texto; nesse caso, o <xref:System.Windows.Automation.AutomationElement> que representa o próprio provedor de texto.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetChildren%2A>|Retorna um <xref:System.Windows.Automation.AutomationElement> que representa o controle de hiperlink.|  
|<xref:System.Windows.Automation.TextPattern.RangeFromChild%2A> em que <xref:System.Windows.Automation.AutomationElement> é o objeto retornado pelo anterior `GetChildren` método.|Retorna o intervalo que representa "https://www.microsoft.com".|  
  
 **Exemplo 2 - um intervalo de texto que abrange parcialmente um hiperlink de texto inserido**  
  
 A URL `https://{[www]}` é inserido no texto.  
  
|Método chamado|Resultado|  
|-------------------|------------|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetText%2A>|Retorna a cadeia de caracteres "www".|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>|Retorna o mais interno <xref:System.Windows.Automation.AutomationElement> que inclui o intervalo de texto; nesse caso, o hiperlink de controle.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetChildren%2A>|Retorna `null` , pois o intervalo de texto não abrange toda cadeia de caracteres de URL.|  
  
**Exemplo 3: um intervalo de texto que abrange parcialmente o conteúdo de um contêiner de texto. O contêiner de texto tem um hiperlink de texto inserido não é parte do intervalo de texto.**  
  
`{The URL} [https://www.microsoft.com](https://www.microsoft.com) is embedded in text.`
  
|Método chamado|Resultado|  
|-------------------|------------|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetText%2A>|Retorna a cadeia de caracteres "A URL".|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>|Retorna o mais interno <xref:System.Windows.Automation.AutomationElement> que inclui o intervalo de texto; nesse caso, o <xref:System.Windows.Automation.AutomationElement> que representa o próprio provedor de texto.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.Move%2A> com os parâmetros de (TextUnit, 1).|Move o intervalo de texto para "http", pois o texto do hiperlink é composto de palavras individuais. Nesse caso, o hiperlink não é tratado como um único objeto.<br /><br /> A URL {[http]} é inserida no texto.|  
  
<a name="Image"></a>   
### <a name="image"></a>Image  
 **Exemplo 1 - um intervalo de texto que contém uma imagem inserida**  
  
 {A imagem ![exemplo de imagem inserida](../../../docs/framework/ui-automation/media/uia-textpattern-embedded-objects-overview-imageexample.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample") é inserida em texto}.  
  
|Método chamado|Resultado|  
|-------------------|------------|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetText%2A>|Retorna a cadeia de caracteres "a é inserido no texto". Qualquer texto ALT associado com a imagem não pode ser esperado a serem incluídas no fluxo de texto.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>|Retorna o mais interno <xref:System.Windows.Automation.AutomationElement> que inclui o intervalo de texto; nesse caso, o <xref:System.Windows.Automation.AutomationElement> que representa o próprio provedor de texto.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetChildren%2A>|Retorna um <xref:System.Windows.Automation.AutomationElement> que representa o controle de imagem.|  
|<xref:System.Windows.Automation.TextPattern.RangeFromChild%2A> em que <xref:System.Windows.Automation.AutomationElement> é o objeto retornado pelo anterior <xref:System.Windows.Automation.Text.TextPatternRange.GetChildren%2A> método.|Retorna o intervalo de degeneração que representa "![exemplo de imagem inserida](../../../docs/framework/ui-automation/media/uia-textpattern-embedded-objects-overview-imageexample.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample")".|  
  
 **Exemplo 2 - um intervalo de texto que abrange parcialmente o conteúdo de um contêiner de texto. O contêiner de texto tem uma imagem inserida que não faz parte do intervalo de texto.**  
  
 {A imagem} ![Exemplo de imagem inserida](../../../docs/framework/ui-automation/media/uia-textpattern-embedded-objects-overview-imageexample.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample") é inserido no texto.  
  
|Método chamado|Resultado|  
|-------------------|------------|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetText%2A>|Retorna a cadeia de caracteres "A imagem".|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>|Retorna o mais interno <xref:System.Windows.Automation.AutomationElement> que inclui o intervalo de texto; nesse caso, o <xref:System.Windows.Automation.AutomationElement> que representa o próprio provedor de texto.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.Move%2A> com os parâmetros de (TextUnit, 1).|Move o intervalo de texto para "é". Como apenas objetos inseridos com base em texto são considerados parte do fluxo de texto, a imagem neste exemplo não afeta Move ou seu valor de retorno (1 neste caso).|  
  
<a name="Table"></a>   
### <a name="table"></a>Tabela  
  
### <a name="table-used-for-examples"></a>Tabela usada para obter exemplos  
  
|Célula com imagem|Célula com texto|  
|---------------------|--------------------|  
|![Incorporado a imagem de exemplo](../../../docs/framework/ui-automation/media/uia-textpattern-embedded-objects-overview-imageexample.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample")|X|  
|![Incorporado a imagem de exemplo 2](../../../docs/framework/ui-automation/media/uia-textpattern-embedded-objects-overview-imageexample2.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample2")|S|  
|![Incorporado a imagem de exemplo 3](../../../docs/framework/ui-automation/media/uia-textpattern-embedded-objects-overview-imageexample3.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample3")<br /><br /> Imagem de Z|Z|  
  
 **Exemplo 1: obter o contêiner de texto do conteúdo de uma célula.**  
  
|Método chamado|Resultado|  
|-------------------|------------|  
|<xref:System.Windows.Automation.GridPattern.GetItem%2A> com os parâmetros (0,0)|Retorna o <xref:System.Windows.Automation.AutomationElement> que representa o conteúdo da célula da tabela; nesse caso, o elemento é um controle de texto.|  
|<xref:System.Windows.Automation.TextPattern.RangeFromChild%2A> em que <xref:System.Windows.Automation.AutomationElement> é o objeto retornado pelo anterior `GetItem` método.|Retorna o intervalo que abrange a imagem ![exemplo de imagem inserida](../../../docs/framework/ui-automation/media/uia-textpattern-embedded-objects-overview-imageexample.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample").|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A> para o objeto retornado por anterior `RangeFromChild` método.|Retorna o <xref:System.Windows.Automation.AutomationElement> que representa a célula de tabela; nesse caso, o elemento é um controle de texto que suporta TableItemPattern.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A> para o objeto retornado por anterior `GetEnclosingElement` método.|Retorna o <xref:System.Windows.Automation.AutomationElement> que representa a tabela.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A> para o objeto retornado por anterior `GetEnclosingElement` método.|Retorna o <xref:System.Windows.Automation.AutomationElement> que representa o próprio provedor de texto.|  
  
 **Exemplo 2: obter o conteúdo de texto de uma célula.**  
  
|Método chamado|Resultado|  
|-------------------|------------|  
|<xref:System.Windows.Automation.GridPattern.GetItem%2A> com os parâmetros de (1,1).|Retorna o <xref:System.Windows.Automation.AutomationElement> que representa o conteúdo da célula da tabela; nesse caso, o elemento é um controle de texto.|  
|<xref:System.Windows.Automation.TextPattern.RangeFromChild%2A> em que <xref:System.Windows.Automation.AutomationElement> é o objeto retornado pelo anterior `GetItem` método.|Retorna "Y".|  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Windows.Automation.TextPattern>
- <xref:System.Windows.Automation.Text.TextPatternRange>
- <xref:System.Windows.Automation.Provider.ITextProvider>
- <xref:System.Windows.Automation.Provider.ITextRangeProvider>
- [Acessar objetos inseridos usando automação de interface do usuário](../../../docs/framework/ui-automation/access-embedded-objects-using-ui-automation.md)
- [Expor o conteúdo de uma tabela usando automação de interface do usuário](../../../docs/framework/ui-automation/expose-the-content-of-a-table-using-ui-automation.md)
- [Percorrer texto usando automação de interface do usuário](../../../docs/framework/ui-automation/traverse-text-using-ui-automation.md)
- [Pesquisa de TextPattern e exemplo de seleção](https://msdn.microsoft.com/library/0a3bca57-8b72-489d-a57c-da85b7a22c7f)
