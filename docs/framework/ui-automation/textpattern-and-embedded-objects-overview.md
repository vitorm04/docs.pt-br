---
title: TextPattern Visão geral de objetos inseridos
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, TextPattern class
- embedded objects, accessing
- accessing embedded objects
- embedded objects, UI Automation
ms.assetid: 93fdfbb9-0025-4b72-8ca0-0714adbb70d5
ms.openlocfilehash: 635c06a03107b33134b015e2643c5281dd86798b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180009"
---
# <a name="textpattern-and-embedded-objects-overview"></a>TextPattern Visão geral de objetos inseridos
> [!NOTE]
> Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32) (API de Automação do Windows: Automação da Interface do Usuário).  
  
 Esta visão geral [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] descreve como expõe objetos incorporados, ou elementos infantis, dentro de um documento de texto ou contêiner.  
  
 Em [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] um objeto incorporado está qualquer elemento que tenha limites não texual; por exemplo, um tipo de imagem, hiperlink, tabela ou documento, como uma planilha do Microsoft Excel ou um arquivo Microsoft Windows Media. Isso difere da definição padrão, onde um elemento é criado em um aplicativo e incorporado, ou vinculado, dentro de outro. Se o objeto pode ser editado dentro de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]sua aplicação original é irrelevante no contexto de .  
  
<a name="Embedded_Objects_and_the_UI_Automation_Tree"></a>
## <a name="embedded-objects-and-the-ui-automation-tree"></a>Objetos incorporados e a árvore de automação de iue  
 Objetos incorporados são tratados como [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] elementos individuais dentro da visão de controle da árvore. Eles são expostos como crianças do recipiente de texto para que possam ser [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]acessados através do mesmo modelo que outros controles em .  
  
 ![Tabela incorporada com imagem em um recipiente de texto](./media/uia-textpattern-embedded-objects-overview-example1.png "UIA_TextPattern_Embedded_Objects_Overview_Example1")  
Exemplo de um contêiner de texto com objetos incorporados de tabela, imagem e hiperlink  
  
 ![Exibição de conteúdo para o exemplo anterior](./media/uia-textpattern-embedded-objects-overview-example2.PNG "UIA_TextPattern_Embedded_Objects_Overview_Example2")  
Exemplo da exibição de conteúdo para uma parte do recipiente de texto anterior  
  
<a name="Expose_Embedded_Objects_Using_TextPattern_and"></a>
## <a name="expose-embedded-objects-using-textpattern-and-textpatternrange"></a>Expor objetos incorporados usando textpattern e textpatternrange  
 Usado em conjunto, a <xref:System.Windows.Automation.TextPattern> classe <xref:System.Windows.Automation.Text.TextPatternRange> de padrão de controle e a classe expõem métodos e propriedades que facilitam a navegação e a consulta de objetos incorporados.  
  
 O conteúdo textual (ou texto interno) de um recipiente de texto e de um objeto incorporado, como um hiperlink ou uma célula [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] de tabela, é exposto como um único fluxo de texto contínuo na exibição de controle e na visualização de conteúdo da árvore; limites de objetos são ignorados. Se um cliente de Automação de UI estiver recuperando o texto com o propósito de recitar, interpretar ou analisar de alguma forma, o intervalo de texto deve ser verificado para casos especiais, como uma tabela com conteúdo textual ou outros objetos incorporados. Isso pode ser <xref:System.Windows.Automation.Text.TextPatternRange.GetChildren%2A> feito ligando para obter <xref:System.Windows.Automation.AutomationElement> um <xref:System.Windows.Automation.TextPattern.RangeFromChild%2A> para cada objeto incorporado e, em seguida, chamando para obter um intervalo de texto para cada elemento. Isso é feito de forma recursiva até que todo o conteúdo textual tenha sido recuperado.  
  
 ![Os intervalos de texto se estendem por objetos incorporados.](./media/uia-textpattern-embeddedobjecttextranges.png "UIA_TextPattern_EmbeddedObjectTextRanges")  
Exemplo de um fluxo de texto com objetos incorporados e seus intervalos de alcance  
  
 Quando é necessário atravessar o conteúdo de um intervalo de texto, uma série <xref:System.Windows.Automation.Text.TextPatternRange.Move%2A> de passos estão envolvidos nos bastidores para que o método seja executado com sucesso.  
  
1. O intervalo de texto é normalizado; ou seja, o intervalo de texto é <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.Start> colapsado a <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End> uma faixa degenerada no ponto final, o que torna o ponto final supérfluo. Esta etapa é necessária para remover a ambiguidade <xref:System.Windows.Automation.Text.TextUnit> em situações `{The URL https://www.microsoft.com is embedded in text` em que um intervalo de texto abrange limites: por exemplo, onde "{" e "}" são os pontos finais do intervalo de texto.  
  
2. O intervalo resultante é movido <xref:System.Windows.Automation.TextPattern.DocumentRange%2A> para trás no <xref:System.Windows.Automation.Text.TextUnit> início do limite solicitado.  
  
3. O intervalo é movido para <xref:System.Windows.Automation.TextPattern.DocumentRange%2A> frente ou para <xref:System.Windows.Automation.Text.TextUnit> trás pelo número solicitado de limites.  
  
4. O intervalo é então expandido a partir <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End> de um estado <xref:System.Windows.Automation.Text.TextUnit> de degenerado, movendo o ponto final por um limite solicitado.  
  
 ![Ajustes de intervalo por Move & ExpandToEnclosingUnit](./media/uia-textpattern-moveandexpand-examples.png "UIA_TextPattern_MoveAndExpand_Examples")  
Exemplos de como um intervalo de texto é ajustado para Mover() e ExpandToEnclosingUnit()  
  
<a name="Common_Scenarios"></a>
## <a name="common-scenarios"></a>Cenários comuns  
 As seções a seguir apresentam exemplos dos cenários mais comuns que envolvem objetos incorporados.  
  
 Lenda para os exemplos mostrados:  
  
 { =<xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.Start>  
  
 } =<xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End>  
  
### <a name="hyperlink"></a>Hyperlink  

**Exemplo 1 - Um intervalo de texto que contém um hiperlink de texto incorporado**
  
`{The URL https://www.microsoft.com is embedded in text}.`
  
|Método chamado|Result|  
|-------------------|------------|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetText%2A>|Retorna a cadeia de caracteres `The URL https://www.microsoft.com is embedded in text`.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>|Retorna o <xref:System.Windows.Automation.AutomationElement> mais interno que inclui o intervalo de texto; neste caso, <xref:System.Windows.Automation.AutomationElement> o que representa o próprio provedor de texto.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetChildren%2A>|Retorna <xref:System.Windows.Automation.AutomationElement> um representando o controle de hiperlink.|  
|<xref:System.Windows.Automation.TextPattern.RangeFromChild%2A>onde <xref:System.Windows.Automation.AutomationElement> está o objeto devolvido `GetChildren` pelo método anterior.|Retorna o alcance quehttps://www.microsoft.comrepresenta " ".|  
  
 **Exemplo 2 - Um intervalo de texto que abrange parcialmente um hiperlink de texto incorporado**  
  
 A `https://{[www]}` URL está incorporada no texto.  
  
|Método chamado|Result|  
|-------------------|------------|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetText%2A>|Retorna a string "www".|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>|Retorna o <xref:System.Windows.Automation.AutomationElement> mais interno que inclui o intervalo de texto; neste caso, o controle de hiperlink.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetChildren%2A>|Retorna `null` já que o intervalo de texto não abrange toda a seqüência de URL.|  
  
**Exemplo 3 - Um intervalo de texto que abrange parcialmente o conteúdo de um recipiente de texto. O contêiner de texto tem um hiperlink de texto incorporado que não faz parte do intervalo de texto.**  
  
`{The URL} [https://www.microsoft.com](https://www.microsoft.com) is embedded in text.`
  
|Método chamado|Result|  
|-------------------|------------|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetText%2A>|Retorna a string "The URL".|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>|Retorna o <xref:System.Windows.Automation.AutomationElement> mais interno que inclui o intervalo de texto; neste caso, <xref:System.Windows.Automation.AutomationElement> o que representa o próprio provedor de texto.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.Move%2A>com parâmetros de (TextUnit.Word, 1).|Move o intervalo de intervalo de texto para "http" uma vez que o texto do hiperlink é composto por palavras individuais. Neste caso, o hiperlink não é tratado como um único objeto.<br /><br /> O URL {[http]} está incorporado no texto.|  
  
<a name="Image"></a>
### <a name="image"></a>Imagem  
 **Exemplo 1 - Um intervalo de texto que contém uma imagem incorporada**  
  
 {O ![exemplo de imagem incorporada](./media/uia-textpattern-embedded-objects-overview-imageexample.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample") da imagem está incorporado no texto}.  
  
|Método chamado|Result|  
|-------------------|------------|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetText%2A>|Retorna a string "O está embutido no texto". Qualquer texto ALT associado à imagem não pode ser incluído no fluxo de texto.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>|Retorna o <xref:System.Windows.Automation.AutomationElement> mais interno que inclui o intervalo de texto; neste caso, <xref:System.Windows.Automation.AutomationElement> o que representa o próprio provedor de texto.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetChildren%2A>|Retorna <xref:System.Windows.Automation.AutomationElement> um representando o controle de imagem.|  
|<xref:System.Windows.Automation.TextPattern.RangeFromChild%2A>onde <xref:System.Windows.Automation.AutomationElement> está o objeto devolvido <xref:System.Windows.Automation.Text.TextPatternRange.GetChildren%2A> pelo método anterior.|Retorna a faixa degenerada que representa "![Exemplo de Imagem Incorporada](./media/uia-textpattern-embedded-objects-overview-imageexample.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample")".|  
  
 **Exemplo 2 - Um intervalo de texto que abrange parcialmente o conteúdo de um recipiente de texto. O recipiente de texto tem uma imagem incorporada que não faz parte do intervalo de texto.**  
  
 {A imagem} ![O Exemplo de Imagem Incorporado](./media/uia-textpattern-embedded-objects-overview-imageexample.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample") está incorporado no texto.  
  
|Método chamado|Result|  
|-------------------|------------|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetText%2A>|Retorna a seqüência "A imagem".|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>|Retorna o <xref:System.Windows.Automation.AutomationElement> mais interno que inclui o intervalo de texto; neste caso, <xref:System.Windows.Automation.AutomationElement> o que representa o próprio provedor de texto.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.Move%2A>com parâmetros de (TextUnit.Word, 1).|Move o intervalo de intervalo de texto para "é". Como apenas objetos incorporados baseados em texto são considerados parte do fluxo de texto, a imagem neste exemplo não afeta o Move ou seu valor de retorno (1 neste caso).|  
  
<a name="Table"></a>
### <a name="table"></a>Tabela  
  
### <a name="table-used-for-examples"></a>Tabela usada para exemplos  
  
|Célula com Imagem|Célula com Texto|  
|---------------------|--------------------|  
|![Exemplo de imagem incorporado](./media/uia-textpattern-embedded-objects-overview-imageexample.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample")|X|  
|![Exemplo de imagem incorporado 2](./media/uia-textpattern-embedded-objects-overview-imageexample2.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample2")|S|  
|![Exemplo de imagem incorporado 3](./media/uia-textpattern-embedded-objects-overview-imageexample3.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample3")<br /><br /> Imagem para Z|Z|  
  
 **Exemplo 1 - Obtenha o recipiente de texto do conteúdo de uma célula.**  
  
|Método chamado|Result|  
|-------------------|------------|  
|<xref:System.Windows.Automation.GridPattern.GetItem%2A>com parâmetros (0,0)|Retorna <xref:System.Windows.Automation.AutomationElement> o conteúdo representando o conteúdo da célula de tabela; neste caso, o elemento é um controle de texto.|  
|<xref:System.Windows.Automation.TextPattern.RangeFromChild%2A>onde <xref:System.Windows.Automation.AutomationElement> está o objeto devolvido `GetItem` pelo método anterior.|Retorna o intervalo que abrange a imagem ![Exemplo de imagem Incorporada](./media/uia-textpattern-embedded-objects-overview-imageexample.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample").|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>para o objeto devolvido `RangeFromChild` pelo método anterior.|Retorna <xref:System.Windows.Automation.AutomationElement> a representação da célula de tabela; neste caso, o elemento é um controle de texto que suporta TableItemPattern.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>para o objeto devolvido `GetEnclosingElement` pelo método anterior.|Retorna <xref:System.Windows.Automation.AutomationElement> o representando a mesa.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>para o objeto devolvido `GetEnclosingElement` pelo método anterior.|Retorna <xref:System.Windows.Automation.AutomationElement> o que representa o próprio provedor de texto.|  
  
 **Exemplo 2 - Obtenha o conteúdo de texto de uma célula.**  
  
|Método chamado|Result|  
|-------------------|------------|  
|<xref:System.Windows.Automation.GridPattern.GetItem%2A>com parâmetros de (1,1).|Retorna <xref:System.Windows.Automation.AutomationElement> o conteúdo representando o conteúdo da célula de tabela; neste caso, o elemento é um controle de texto.|  
|<xref:System.Windows.Automation.TextPattern.RangeFromChild%2A>onde <xref:System.Windows.Automation.AutomationElement> está o objeto devolvido `GetItem` pelo método anterior.|Retorna "Y".|  
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.Automation.TextPattern>
- <xref:System.Windows.Automation.Text.TextPatternRange>
- <xref:System.Windows.Automation.Provider.ITextProvider>
- <xref:System.Windows.Automation.Provider.ITextRangeProvider>
- [Acessar objetos inseridos usando automação de interface de usuário](access-embedded-objects-using-ui-automation.md)
- [Expor o conteúdo de uma tabela usando automação de interface do usuário](expose-the-content-of-a-table-using-ui-automation.md)
- [Percorrer texto usando automação de interface do usuário](traverse-text-using-ui-automation.md)
- [Amostra de pesquisa e seleção de textpattern](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/FindText)
