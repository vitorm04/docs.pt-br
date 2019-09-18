---
title: Visão geral de TextPattern de automação da interface do usuário
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, TextPattern class
- TextPattern class
- classes, TextPattern
ms.assetid: 41787927-df1f-4f4a-aba3-641662854fc4
ms.openlocfilehash: defabb90c8aed19fda663d9b360545fc399acaec
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71040531"
---
# <a name="ui-automation-textpattern-overview"></a>Visão geral de TextPattern de automação da interface do usuário

> [!NOTE]
> Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]recentes sobre [o, consulte API de automação do Windows: Automação](https://go.microsoft.com/fwlink/?LinkID=156746)da interface do usuário.

Esta visão geral descreve como usar [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] o para expor o conteúdo textual, incluindo atributos de formato e estilo, de controles [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]de texto em plataformas com suporte. Esses controles incluem, entre outros, a estrutura <xref:System.Windows.Controls.TextBox> de Microsoft .net e <xref:System.Windows.Controls.RichTextBox> também seus [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] equivalentes.

Expor o conteúdo textual de um controle é realizado por meio do uso do padrão <xref:System.Windows.Automation.TextPattern> de controle, que representa o conteúdo de um contêiner de texto como um fluxo de texto. Por sua vez <xref:System.Windows.Automation.TextPattern> , o requer o suporte <xref:System.Windows.Automation.Text.TextPatternRange> da classe para expor atributos de formato e estilo. <xref:System.Windows.Automation.Text.TextPatternRange>Dá <xref:System.Windows.Automation.TextPattern> suporte ao representação de trechos de texto contíguos ou múltiplos, disjunçãos em um contêiner de <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.Start> texto <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End> com uma coleção de pontos de extremidade e. <xref:System.Windows.Automation.Text.TextPatternRange>oferece suporte a funcionalidades como seleção, comparação, recuperação e passagem.

> [!NOTE]
> As <xref:System.Windows.Automation.TextPattern> classes não fornecem um meio para inserir ou modificar texto. No entanto, dependendo do controle, isso pode ser realizado pelo ou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] por meio de entrada de <xref:System.Windows.Automation.ValuePattern> teclado direta. Consulte o [exemplo inserir texto de TextPattern](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/InsertText) para obter um exemplo.

A funcionalidade descrita nesta visão geral é vital para fornecedores de tecnologia assistencial e seus usuários finais. Tecnologias assistenciais podem ser [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] usadas para reunir informações completas de formatação de texto para o usuário e fornecer navegação programática e seleção <xref:System.Windows.Automation.Text.TextUnit> de texto por (caractere, palavra, linha ou parágrafo).

<a name="UI_Automation_TextPattern_vs__Cicero"></a>

## <a name="ui-automation-textpattern-vs-text-services-framework"></a>TextPattern da automação da interface do usuário vs. Estrutura de serviços de texto

[!INCLUDE[TLA#tla_tsf](../../../includes/tlasharptla-tsf-md.md)]o é uma estrutura de sistema simples e escalonável que permite serviços de linguagem natural e entrada de texto avançada na área de trabalho e em aplicativos. Além de fornecer interfaces para que os aplicativos exponham seu armazenamento de texto, ele também dá suporte a metadados para esse armazenamento de texto.

No entanto, [!INCLUDE[TLA2#tla_tsf](../../../includes/tla2sharptla-tsf-md.md)] o foi projetado para aplicativos que precisam injetar entrada em cenários com <xref:System.Windows.Automation.TextPattern> reconhecimento de contexto, enquanto que é uma solução somente leitura (com a solução alternativa limitada mencionada acima), destinada a fornecer acesso otimizado a um armazenamento de texto para leitores de tela e dispositivos Braille.

Em suma, tecnologias acessíveis que exigem acesso somente leitura a um armazenamento de texto podem usar <xref:System.Windows.Automation.TextPattern>, mas precisarão da funcionalidade mais complexa do [!INCLUDE[TLA2#tla_tsf](../../../includes/tla2sharptla-tsf-md.md)] para a entrada com reconhecimento de contexto.

<a name="Control_Types"></a>

## <a name="control-types"></a>Tipos de controle

### <a name="text"></a>Texto

O controle texto é o elemento básico que representa uma parte do texto na tela.

Um controle de texto autônomo pode ser usado como um rótulo ou texto estático em um formulário. Os controles de texto também podem estar contidos na estrutura de <xref:System.Windows.Automation.ControlType.ListItem>um <xref:System.Windows.Automation.ControlType.TreeItem> , <xref:System.Windows.Automation.ControlType.DataItem>ou.

> [!NOTE]
> Os controles de texto podem não aparecer na exibição de conteúdo [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] da árvore (consulte [visão geral da árvore de automação da interface do usuário](ui-automation-tree-overview.md)). Isso ocorre porque os controles de texto geralmente são exibidos por meio da propriedade Name de outro controle. Por exemplo, o texto usado para rotular um controle de edição é exposto por meio da propriedade Name do controle de edição. Como o controle de edição está na exibição de conteúdo da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] árvore, não é necessário que o próprio elemento de texto esteja nessa exibição [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] da árvore. O único texto que aparece na exibição de conteúdo é texto que não é informações redundantes. Isso permite que qualquer tecnologia assistencial filtre rapidamente apenas as informações de que seus usuários precisam.

### <a name="edit"></a>Editar

Os controles de edição permitem que um usuário exiba e edite uma única linha de texto.

> [!NOTE]
> A linha única de texto pode ser encapsulada em determinados cenários de layout.

### <a name="document"></a>Documento

Os controles de documento permitem que um usuário navegue e obtenha informações de várias páginas de texto.

<a name="TextPattern_Client_API_s"></a>

## <a name="textpattern-client-apis"></a>APIs de cliente TextPattern

|||
|-|-|
|`System.Windows.Automation.TextPattern Class`|O ponto de entrada para [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] o modelo de texto.<br /><br /> Essa classe também contém os dois <xref:System.Windows.Automation.TextPattern> ouvintes <xref:System.Windows.Automation.TextPattern.TextSelectionChangedEvent> de eventos e <xref:System.Windows.Automation.TextPattern.TextChangedEvent>.|
|`System.Windows.Automation.Text.TextPatternRange Class`|A representação de um intervalo de texto dentro de um contêiner de texto <xref:System.Windows.Automation.TextPattern>que dá suporte a.<br /><br /> Os clientes de automação da interface do usuário devem ter cuidado com a validade atual de <xref:System.Windows.Automation.Text.TextPatternRange>um intervalo de texto criado usando o. Se o texto original no controle de texto for completamente substituído pelo novo texto, o intervalo de texto atual se tornará inválido. No entanto, o intervalo de texto ainda pode ter alguma viabilidade se apenas parte do texto original for alterada e o controle de texto subjacente estiver gerenciando seu texto "ponteiro" com âncoras (ou pontos de extremidade) em vez de com o posicionamento de caracteres absoluto.<br /><br /> Os clientes podem escutar uma <xref:System.Windows.Automation.TextPattern.TextChangedEvent> notificação de qualquer alteração no conteúdo textual com a qual estão trabalhando.|
|`System.Windows.Automation.AutomationTextAttribute Class`|Usado para identificar os atributos de formatação de um intervalo de texto.|

<a name="TextPattern_Provider_API_s"></a>

## <a name="textpattern-provider-apis"></a>APIs do provedor de TextPattern

Elementos de interface do usuário ou <xref:System.Windows.Automation.TextPattern> controles que dão <xref:System.Windows.Automation.Provider.ITextProvider> suporte <xref:System.Windows.Automation.Provider.ITextRangeProvider> ao implementar as interfaces e, de [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] forma nativa ou por meio de proxies, são capazes de expor informações de atributo detalhadas para qualquer texto que eles contenham adição ao fornecimento de recursos de navegação robustos.

Um <xref:System.Windows.Automation.TextPattern> provedor não precisará dar suporte a todos os atributos de texto se o controle não tiver suporte para nenhum atributo específico.

Um <xref:System.Windows.Automation.TextPattern> provedor deve <xref:System.Windows.Automation.TextPattern.GetSelection%2A> dar suporte às <xref:System.Windows.Automation.Text.TextPatternRange.Select%2A> funções e se o controle oferecer suporte à seleção de texto ou ao posicionamento do cursor de texto (ou do cursor do sistema) na área de texto. Se o controle não oferecer suporte a essa funcionalidade, ele não precisará oferecer suporte a nenhum desses métodos. No entanto, o controle deve expor o tipo de seleção de texto compatível com <xref:System.Windows.Automation.Provider.ITextProvider.SupportedTextSelection%2A> a implementação da propriedade.

Um <xref:System.Windows.Automation.TextPattern> provedor deve sempre dar suporte <xref:System.Windows.Automation.Text.TextUnit> às <xref:System.Windows.Automation.Text.TextUnit.Character> constantes <xref:System.Windows.Automation.Text.TextUnit.Document> e também a qualquer outra <xref:System.Windows.Automation.Text.TextUnit> constante com suporte.

> [!NOTE]
> O provedor pode ignorar o suporte para um <xref:System.Windows.Automation.Text.TextUnit> específico, desferindo-se <xref:System.Windows.Automation.Text.TextUnit> ao próximo maior suporte na <xref:System.Windows.Automation.Text.TextUnit.Word>seguinte <xref:System.Windows.Automation.Text.TextUnit.Character> <xref:System.Windows.Automation.Text.TextUnit.Line>ordem <xref:System.Windows.Automation.Text.TextUnit.Format> <xref:System.Windows.Automation.Text.TextUnit.Paragraph>:, <xref:System.Windows.Automation.Text.TextUnit.Page>,,,, <xref:System.Windows.Automation.Text.TextUnit.Document> e .

|||
|-|-|
|`ITextProvider Interface`|Expõe métodos, propriedades e atributos que dão <xref:System.Windows.Automation.TextPattern> suporte a aplicativos cliente ( <xref:System.Windows.Automation.Provider.ITextProvider>consulte).|
|`ITextRangeProvider Interface`|Representa um intervalo de texto em um provedor de texto ( <xref:System.Windows.Automation.Provider.ITextRangeProvider>consulte).|
|`System.Windows.Automation.TextPatternIdentifiers Class`|Contém valores que são usados como identificadores para provedores de texto ( <xref:System.Windows.Automation.TextPatternIdentifiers>consulte).|

<a name="Security"></a>

## <a name="security"></a>Segurança

A [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] arquitetura foi projetada tendo em mente a segurança (consulte [visão geral da segurança de automação da interface do usuário](ui-automation-security-overview.md)). No entanto, as classes de TextPattern descritas nesta visão geral exigem algumas considerações de segurança específicas.

- [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]os provedores de texto fornecem interfaces somente leitura e não fornecem a capacidade de alterar o texto existente em um controle.

- Os clientes de automação da interface [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] do usuário só poderão usar se forem totalmente "confiáveis". Um exemplo disso seria a área de trabalho de logon protegida, onde somente aplicativos conhecidos e confiáveis podem ser executados.

- Os desenvolvedores de provedores de automação de interface do usuário devem estar cientes de que todas as informações que [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] eles optam por serem expostas em seus controles por meio do são essencialmente públicas e totalmente acessíveis por outro código. [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]Não faz nenhum esforço para determinar a confiabilidade de qualquer cliente de automação de interface do usuário e, portanto, o provedor de automação de interface do usuário não deve expor conteúdo protegido ou informações textuais confidenciais (como campos de senha).

- Uma das alterações mais significativas na segurança do [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] é amplamente conhecida como "entrada segura", que abrange tecnologias como contas de usuário menos privilegiadas (ou limitadas) e UIPI (isolamento de nível de privilégio de interface do usuário).

  - O UIPI impede que um programa controle e/ou monitore outro programa "privilegiado", impedindo ataques de mensagem de janela de processo cruzado que falsificam a entrada do usuário.

  - O LUA define os limites dos privilégios dos aplicativos que estão sendo executados pelos usuários no grupo Administradores. Os aplicativos não terão necessariamente privilégios de administrador, mas, em vez disso, serão executados com os privilégios mínimos necessários. Como consequência, pode haver algumas restrições impostas em cenários de LUA. Mais notavelmente o truncamento de cadeia de caracteres (incluindo cadeias de TextPattern), em que pode ser necessário limitar o tamanho das cadeias que estão sendo recuperadas de aplicativos de nível de administrador para que não sejam forçadas a alocar memória até o ponto de desabilitar o aplicativo.

<a name="Performance"></a>

## <a name="performance"></a>Desempenho

Como TextPattern se baseia em chamadas entre processos para a maior parte de sua funcionalidade, ele não fornece um mecanismo de cache para melhorar o desempenho ao processar o conteúdo. Isso é diferente de outros padrões de [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] controle no que podem ser acessados usando os <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A> métodos ou <xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A> .

Uma tática para melhorar o desempenho é garantindo que os clientes de automação da interface do usuário tentem recuperar blocos de <xref:System.Windows.Automation.Text.TextPatternRange.GetText%2A>texto de tamanho moderado usando. Por exemplo, as chamadas de gettext (1) incorrerão em ocorrências entre processos para cada caractere, enquanto uma chamada gettext (-1) incorrerá em uma ocorrência de processo cruzado, mas poderá ter alta latência dependendo do tamanho do provedor de texto.

<a name="Glossary"></a>

## <a name="textpattern-terminology"></a>Terminologia de TextPattern

**Attribute**\
Uma característica de formatação de um intervalo de texto (por <xref:System.Windows.Automation.TextPattern.IsItalicAttribute> exemplo <xref:System.Windows.Automation.TextPattern.FontNameAttribute>, ou).

**Intervalo de degeneração**\
Um intervalo de degeneração é um intervalo de texto vazio ou com zero caracteres. Para os fins do padrão de controle TextPattern, o ponto de inserção de texto (ou o cursor do sistema) é considerado um intervalo de degeneramento. Se nenhum texto for selecionado, <xref:System.Windows.Automation.TextPattern.GetSelection%2A> retornará um intervalo de degeneração no ponto de inserção de texto <xref:System.Windows.Automation.TextPattern.RangeFromPoint%2A> e retornará um intervalo de degeneração como seu ponto de extremidade inicial. <xref:System.Windows.Automation.TextPattern.RangeFromChild%2A>e <xref:System.Windows.Automation.TextPattern.GetVisibleRanges%2A> pode retornar intervalos de degeneração quando o provedor de texto não encontrar nenhum intervalo de texto que corresponda à condição especificada. Esse intervalo de degeneração pode ser usado como um ponto de extremidade inicial dentro do provedor de texto. <xref:System.Windows.Automation.Text.TextPatternRange.FindText%2A>e <xref:System.Windows.Automation.Text.TextPatternRange.FindAttribute%2A> retorne uma referência nula`Nothing` (no Microsoft Visual Basic .net) para evitar confusão com um intervalo descoberto em vez de um intervalo de degeneramento.

**Objeto inserido**\
Há dois tipos de objetos inseridos no modelo [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] de texto. Eles consistem em elementos de conteúdo baseados em texto, como hiperlinks ou tabelas, e elementos de controle, como imagens e botões. Para obter informações mais detalhadas, consulte [acessar objetos inseridos usando a automação da interface do usuário](access-embedded-objects-using-ui-automation.md).

**Extremidade**\
A parte <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.Start> absoluta <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End> ou o ponto de um intervalo de texto dentro de um contêiner de texto.

![TextPatternRangeEndpoints &#40;iniciar e encerrar&#41;.](./media/uia-textpattern-endpoints.PNG "UIA_TextPattern_Endpoints") O seguinte ilustra um conjunto de pontos inicial e final.

**TextRange**\
Uma representação de um intervalo de texto, com pontos inicial e final, em um contêiner de texto, incluindo todos os atributos e funcionalidades associados.

<xref:System.Windows.Automation.Text.TextUnit>\
Uma unidade de texto predefinida (caractere, palavra, linha ou parágrafo) usada para navegar por segmentos lógicos de um intervalo de texto.

## <a name="see-also"></a>Consulte também

- [Padrões de controle de automação de interface do usuário para clientes](ui-automation-control-patterns-for-clients.md)
- [Visão geral de padrões de controle de automação da interface do usuário](ui-automation-control-patterns-overview.md)
- [Visão geral de árvore de automação de interface do usuário](ui-automation-tree-overview.md)
- [Usar o cache em automação de interface do usuário](use-caching-in-ui-automation.md)
- [Suporte a padrões de controle em um provedor de automação de interface do usuário](support-control-patterns-in-a-ui-automation-provider.md)
- [Mapeamento de padrão de controle para clientes de automação de interface do usuário](control-pattern-mapping-for-ui-automation-clients.md)
- [Estrutura de serviços de texto](/windows/desktop/api/_tsf/)
