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
manager: markl
ms.openlocfilehash: ab732ffedfbe05b1b246d8d8eef1c374e223eb39
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33401174"
---
# <a name="textpattern-and-embedded-objects-overview"></a>TextPattern Visão geral de objetos inseridos
> [!NOTE]
>  Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746) (API de Automação do Windows: Automação da Interface do Usuário).  
  
 Esta visão geral descreve como [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] expõe objetos inseridos, ou elementos filho, dentro de um documento de texto ou contêiner.  
  
 Em [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] um objeto inserido é qualquer elemento que tenha limites não textuais; por exemplo, uma imagem, o hiperlink, a tabela ou o documento digite como uma [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] planilha ou [!INCLUDE[TLA#tla_winmedia](../../../includes/tlasharptla-winmedia-md.md)] arquivo. Isso é diferente da definição padrão, onde um elemento é criado em um aplicativo e incorporado ou vinculado, dentro de outro. Se o objeto pode ser editado em seu aplicativo original é irrelevante no contexto de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].  
  
<a name="Embedded_Objects_and_the_UI_Automation_Tree"></a>   
## <a name="embedded-objects-and-the-ui-automation-tree"></a>Objetos inseridos e a árvore de automação de interface do usuário  
 Objetos inseridos são tratados como elementos individuais na exibição de controle de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] árvore. Eles são expostos como filhos do recipiente de texto para que eles possam ser acessados através do mesmo modelo como outros controles em [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].  
  
 ![Incorporado a tabela com a imagem em um contêiner de texto](../../../docs/framework/ui-automation/media/uia-textpattern-embedded-objects-overview-example1.png "UIA_TextPattern_Embedded_Objects_Overview_Example1")  
Objetos inseridos de exemplo de um recipiente de texto com hiperlink, imagem e tabela  
  
 ![Modo de exibição para o exemplo anterior de conteúdo](../../../docs/framework/ui-automation/media/uia-textpattern-embedded-objects-overview-example2.PNG "UIA_TextPattern_Embedded_Objects_Overview_Example2")  
Exemplo de exibição de conteúdo de uma parte do recipiente de texto anterior  
  
<a name="Expose_Embedded_Objects_Using_TextPattern_and"></a>   
## <a name="expose-embedded-objects-using-textpattern-and-textpatternrange"></a>Expor objetos inseridos usando TextPattern e TextPatternRange  
 Usado em conjunto, o <xref:System.Windows.Automation.TextPattern> classe padrão de controle e o <xref:System.Windows.Automation.Text.TextPatternRange> classe expõe métodos e propriedades que facilitam a navegação e a consulta de objetos inseridos.  
  
 O conteúdo textual (ou texto interno) de um recipiente de texto e um objeto inserido, como um hiperlink ou célula de tabela, é exposto como um fluxo de texto único e contínuo em visualização de controle e exibição de conteúdo de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] árvore; objeto limites são ignorados. Se um cliente de automação de interface do usuário estiver recuperando o texto com a finalidade de citar, interpretar, ou analisar de alguma maneira, o intervalo de texto deve ser verificado para casos especiais, como uma tabela com textuais conteúdos ou outros objetos inseridos. Isso pode ser conseguido chamando <xref:System.Windows.Automation.Text.TextPatternRange.GetChildren%2A> para obter um <xref:System.Windows.Automation.AutomationElement> cada Embedded objeto e, em seguida, chamar <xref:System.Windows.Automation.TextPattern.RangeFromChild%2A> para obter um intervalo de texto para cada elemento. Isso é feito de forma recursiva até que todo o conteúdo textual tiver sido recuperado.  
  
 ![Intervalos de texto abrangidos por objetos inseridos. ] (../../../docs/framework/ui-automation/media/uia-textpattern-embeddedobjecttextranges.png "UIA_TextPattern_EmbeddedObjectTextRanges")  
Exemplo de um fluxo de texto com objetos inseridos e seus intervalos abrangentes  
  
 Quando for necessário atravessar o conteúdo de um intervalo de texto, uma série de etapas envolvidas em segundo plano para que o <xref:System.Windows.Automation.Text.TextPatternRange.Move%2A> método seja executado com êxito.  
  
1.  O intervalo de texto é normalizado; ou seja, o intervalo de texto é recolhido para um intervalo degenerado no <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.Start> ponto de extremidade, o que torna o <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End> supérfluo de ponto de extremidade. Essa etapa é necessária para remover ambiguidade em situações nas quais um intervalo de texto abrange <xref:System.Windows.Automation.Text.TextUnit> limites: por exemplo, "{a U} RL [ http://www.microsoft.com ](http://www.microsoft.com) é inserido no texto" onde "{" e "}" é pontos de extremidade do intervalo de texto.  
  
2.  O intervalo resultante é movido para trás no <xref:System.Windows.Automation.TextPattern.DocumentRange%2A> para o início da solicitados <xref:System.Windows.Automation.Text.TextUnit> limite.  
  
3.  O intervalo é movido para frente ou para trás no <xref:System.Windows.Automation.TextPattern.DocumentRange%2A> pelo número solicitado de <xref:System.Windows.Automation.Text.TextUnit> limites.  
  
4.  O intervalo é expandido de um estado de intervalo degenerado movendo o <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End> ponto de extremidade por solicitado <xref:System.Windows.Automation.Text.TextUnit> limite.  
  
 ![Ajustes de intervalo por Move & ExpandToEnclosingUnit](../../../docs/framework/ui-automation/media/uia-textpattern-moveandexpand-examples.png "UIA_TextPattern_MoveAndExpand_Examples")  
Exemplos de como um intervalo de texto é ajustado para Move () e ExpandToEnclosingUnit)  
  
<a name="Common_Scenarios"></a>   
## <a name="common-scenarios"></a>Cenários comuns  
 As seções a seguir apresentam exemplos dos cenários mais comuns que envolvem objetos inseridos.  
  
 Legenda para os exemplos mostrados:  
  
 { = <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.Start>  
  
 } = <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End>  
  
<a name="Hyperlink"></a>   
### <a name="hyperlink"></a>Hiperlink  
 **Exemplo 1 - um intervalo de texto que contém um hiperlink de texto inserido**  
  
 {A URL [ http://www.microsoft.com ](http://www.microsoft.com) é inserida em texto}.  
  
|Método chamado|Resultado|  
|-------------------|------------|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetText%2A>|Retorna a cadeia de caracteres "a URL http://www.microsoft.com é inserido no texto".|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>|Retorna o mais interno <xref:System.Windows.Automation.AutomationElement> que inclui o intervalo de texto; nesse caso, o <xref:System.Windows.Automation.AutomationElement> que representa o provedor de texto.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetChildren%2A>|Retorna um <xref:System.Windows.Automation.AutomationElement> que representa o controle de hiperlink.|  
|<xref:System.Windows.Automation.TextPattern.RangeFromChild%2A> onde <xref:System.Windows.Automation.AutomationElement> é o objeto retornado por anterior `GetChildren` método.|Retorna o intervalo que representa "http://www.microsoft.com".|  
  
 **Exemplo 2 - um intervalo de texto que abrange parcialmente um hiperlink de texto inserido**  
  
 Http://{[www URL]} é inserida em texto.  
  
|Método chamado|Resultado|  
|-------------------|------------|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetText%2A>|Retorna a cadeia de caracteres "www".|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>|Retorna o mais interno <xref:System.Windows.Automation.AutomationElement> que inclui o intervalo de texto; nesse caso, o hiperlink de controle.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetChildren%2A>|Retorna `null` desde que o intervalo de texto não abrange a cadeia de caracteres de URL inteira.|  
  
 **Exemplo 3 - um intervalo de texto que abrange parcialmente o conteúdo de um recipiente de texto. O contêiner de texto tem um hiperlink de texto inserido que não faz parte do intervalo de texto.**  
  
 {URL} [ http://www.microsoft.com ](http://www.microsoft.com) é inserida em texto.  
  
|Método chamado|Resultado|  
|-------------------|------------|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetText%2A>|Retorna a cadeia de caracteres "A URL".|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>|Retorna o mais interno <xref:System.Windows.Automation.AutomationElement> que inclui o intervalo de texto; nesse caso, o <xref:System.Windows.Automation.AutomationElement> que representa o provedor de texto.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.Move%2A> com parâmetros de (TextUnit, 1).|Move o intervalo de texto para "http", desde que o texto do hiperlink é composto de palavras individuais. Nesse caso, o hiperlink não é tratado como um único objeto.<br /><br /> A URL {[http]} é inserida em texto.|  
  
<a name="Image"></a>   
### <a name="image"></a>Image  
 **Exemplo 1 - um intervalo de texto que contém uma imagem inserida**  
  
 {A imagem ![exemplo de imagem inserida](../../../docs/framework/ui-automation/media/uia-textpattern-embedded-objects-overview-imageexample.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample") é inserida em texto}.  
  
|Método chamado|Resultado|  
|-------------------|------------|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetText%2A>|Retorna a cadeia de caracteres "a é inserida em texto". Qualquer texto alternativo associado com a imagem não pode ser esperado a serem incluídos no fluxo de texto.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>|Retorna o mais interno <xref:System.Windows.Automation.AutomationElement> que inclui o intervalo de texto; nesse caso, o <xref:System.Windows.Automation.AutomationElement> que representa o provedor de texto.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetChildren%2A>|Retorna um <xref:System.Windows.Automation.AutomationElement> que representa o controle de imagem.|  
|<xref:System.Windows.Automation.TextPattern.RangeFromChild%2A> onde <xref:System.Windows.Automation.AutomationElement> é o objeto retornado por anterior <xref:System.Windows.Automation.Text.TextPatternRange.GetChildren%2A> método.|Retorna o intervalo degenerado representando "![exemplo de imagem inserida](../../../docs/framework/ui-automation/media/uia-textpattern-embedded-objects-overview-imageexample.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample")".|  
  
 **Exemplo 2 - um intervalo de texto que abrange parcialmente o conteúdo de um recipiente de texto. O contêiner de texto tem uma imagem inserida que não faz parte do intervalo de texto.**  
  
 {A imagem} ![Exemplo de imagem inserida](../../../docs/framework/ui-automation/media/uia-textpattern-embedded-objects-overview-imageexample.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample") é inserida em texto.  
  
|Método chamado|Resultado|  
|-------------------|------------|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetText%2A>|Retorna a cadeia de caracteres "A imagem".|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>|Retorna o mais interno <xref:System.Windows.Automation.AutomationElement> que inclui o intervalo de texto; nesse caso, o <xref:System.Windows.Automation.AutomationElement> que representa o provedor de texto.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.Move%2A> com parâmetros de (TextUnit, 1).|Move o intervalo de texto para "é". Como apenas objetos inseridos com base em texto são considerados parte do fluxo de texto, a imagem neste exemplo não afeta Move ou seu valor de retorno (1 neste caso).|  
  
<a name="Table"></a>   
### <a name="table"></a>Tabela  
  
### <a name="table-used-for-examples"></a>Tabela usada para exemplos  
  
|Célula com imagem|Célula com texto|  
|---------------------|--------------------|  
|![Inserido imagem exemplo](../../../docs/framework/ui-automation/media/uia-textpattern-embedded-objects-overview-imageexample.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample")|X|  
|![Inserido imagem exemplo 2](../../../docs/framework/ui-automation/media/uia-textpattern-embedded-objects-overview-imageexample2.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample2")|S|  
|![Inserido imagem exemplo 3](../../../docs/framework/ui-automation/media/uia-textpattern-embedded-objects-overview-imageexample3.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample3")<br /><br /> Imagem para Z|Z|  
  
 **Exemplo 1: obter o contêiner de texto do conteúdo de uma célula.**  
  
|Método chamado|Resultado|  
|-------------------|------------|  
|<xref:System.Windows.Automation.GridPattern.GetItem%2A> com os parâmetros (0,0)|Retorna o <xref:System.Windows.Automation.AutomationElement> que representa o conteúdo da célula da tabela; nesse caso, o elemento é um controle de texto.|  
|<xref:System.Windows.Automation.TextPattern.RangeFromChild%2A> onde <xref:System.Windows.Automation.AutomationElement> é o objeto retornado por anterior `GetItem` método.|Retorna o intervalo que abrange a imagem ![exemplo de imagem inserida](../../../docs/framework/ui-automation/media/uia-textpattern-embedded-objects-overview-imageexample.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample").|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A> para o objeto retornado por anterior `RangeFromChild` método.|Retorna o <xref:System.Windows.Automation.AutomationElement> que representa a célula de tabela; nesse caso, o elemento é um controle de texto que suporta TableItemPattern.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A> para o objeto retornado por anterior `GetEnclosingElement` método.|Retorna o <xref:System.Windows.Automation.AutomationElement> que representa a tabela.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A> para o objeto retornado por anterior `GetEnclosingElement` método.|Retorna o <xref:System.Windows.Automation.AutomationElement> que representa o provedor de texto.|  
  
 **Exemplo 2: obter o conteúdo do texto de uma célula.**  
  
|Método chamado|Resultado|  
|-------------------|------------|  
|<xref:System.Windows.Automation.GridPattern.GetItem%2A> com parâmetros de (1,1).|Retorna o <xref:System.Windows.Automation.AutomationElement> que representa o conteúdo da célula da tabela; nesse caso, o elemento é um controle de texto.|  
|<xref:System.Windows.Automation.TextPattern.RangeFromChild%2A> onde <xref:System.Windows.Automation.AutomationElement> é o objeto retornado por anterior `GetItem` método.|Retorna "Y".|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Automation.TextPattern>  
 <xref:System.Windows.Automation.Text.TextPatternRange>  
 <xref:System.Windows.Automation.Provider.ITextProvider>  
 <xref:System.Windows.Automation.Provider.ITextRangeProvider>  
 [Acessar objetos inseridos usando automação de interface do usuário](../../../docs/framework/ui-automation/access-embedded-objects-using-ui-automation.md)  
 [Expor o conteúdo de uma tabela usando automação de interface do usuário](../../../docs/framework/ui-automation/expose-the-content-of-a-table-using-ui-automation.md)  
 [Percorrer texto usando automação de interface do usuário](../../../docs/framework/ui-automation/traverse-text-using-ui-automation.md)  
 [Exemplo de seleção e pesquisa de TextPattern](http://msdn.microsoft.com/library/0a3bca57-8b72-489d-a57c-da85b7a22c7f)
