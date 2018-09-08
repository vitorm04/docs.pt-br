---
title: Visão geral de TextPattern de automação da interface do usuário
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, TextPattern class
- TextPattern class
- classes, TextPattern
ms.assetid: 41787927-df1f-4f4a-aba3-641662854fc4
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 522caed7e8006157f99e65e99bf52743871444ad
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44195628"
---
# <a name="ui-automation-textpattern-overview"></a>Visão geral de TextPattern de automação da interface do usuário
> [!NOTE]
>  Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746) (API de Automação do Windows: Automação da Interface do Usuário).  
  
 Esta visão geral descreve como usar [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] para expor o conteúdo textual, incluindo atributos de formato e estilo de controles de texto em [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]-plataformas com suporte. Esses controles incluem, mas não estão limitados a, o Microsoft .NET Framework <xref:System.Windows.Controls.TextBox> e <xref:System.Windows.Controls.RichTextBox> , bem como seus [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] equivalentes.  
  
 Expondo o conteúdo textual de um controle é feito por meio do uso do <xref:System.Windows.Automation.TextPattern> padrão de controle, que representa o conteúdo de um contêiner de texto como um fluxo de texto. Por sua vez, <xref:System.Windows.Automation.TextPattern> requer o suporte do <xref:System.Windows.Automation.Text.TextPatternRange> classe para expor os atributos de formato e estilo. <xref:System.Windows.Automation.Text.TextPatternRange> dá suporte a <xref:System.Windows.Automation.TextPattern> representando contíguas ou múltiplos disjuntos texto em um contêiner de texto com uma coleção de <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.Start> e <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End> pontos de extremidade. <xref:System.Windows.Automation.Text.TextPatternRange> dá suporte à funcionalidade, como seleção, comparação, recuperação e passagem.  
  
> [!NOTE]
>  O <xref:System.Windows.Automation.TextPattern> classes não fornecem um meio para inserir ou modificar o texto. No entanto, dependendo do controle, isso pode ser feito pelo [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] <xref:System.Windows.Automation.ValuePattern> ou por meio de entrada direta do teclado. Consulte a [TextPattern inserir texto exemplo](https://msdn.microsoft.com/library/67353f93-7ee2-42f2-ab76-5c078cf6ca16) para obter um exemplo.  
  
 A funcionalidade descrita nesta visão geral é vital para fornecedores de tecnologia assistencial e seus usuários finais. Tecnologias assistenciais podem usar [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] para coletar informações de formatação para o usuário de texto completo e fornecer navegação programática e seleção de texto por <xref:System.Windows.Automation.Text.TextUnit> (caractere, palavra, linha ou parágrafo).  
  
<a name="UI_Automation_TextPattern_vs__Cicero"></a>   
## <a name="ui-automation-textpattern-vs-text-services-framework"></a>TextPattern de automação de interface do usuário vs. Estrutura de serviços de texto  
 [!INCLUDE[TLA#tla_tsf](../../../includes/tlasharptla-tsf-md.md)] é uma estrutura de sistema simples e escalonável que permite que os serviços de linguagem natural e na área de trabalho e em aplicativos de entrada de texto avançada. Além de fornecer interfaces para aplicativos para expor seu repositório de texto também suporta metadados para esse armazenamento de texto.  
  
 No entanto, [!INCLUDE[TLA2#tla_tsf](../../../includes/tla2sharptla-tsf-md.md)] foi projetado para aplicativos que precisam para inserir dados de entrada em cenários sensíveis ao contexto enquanto <xref:System.Windows.Automation.TextPattern> é uma solução somente leitura (com a alternativa limitada indicada acima) deve fornecer acesso otimizado a um armazenamento de texto para leitores de tela e dispositivos de Braille.  
  
 Em resumo, as tecnologias acessíveis que exigem acesso somente leitura a um armazenamento de texto podem usar <xref:System.Windows.Automation.TextPattern>, mas será necessário a funcionalidade mais complexa do [!INCLUDE[TLA2#tla_tsf](../../../includes/tla2sharptla-tsf-md.md)] para entrada de reconhecimento de contexto.  
  
<a name="Control_Types"></a>   
## <a name="control-types"></a>Tipos de controle  
  
#### <a name="text"></a>Texto  
 O controle de texto é o elemento básico que representa uma parte do texto na tela.  
  
 Um controle de texto autônomo pode ser usado como um rótulo ou texto estático em um formulário. Controles de texto também podem estar contidos dentro da estrutura de um <xref:System.Windows.Automation.ControlType.ListItem>, <xref:System.Windows.Automation.ControlType.TreeItem> ou <xref:System.Windows.Automation.ControlType.DataItem>.  
  
> [!NOTE]
>  Controles de texto podem não aparecer na exibição de conteúdo a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] árvore (veja [visão geral da árvore de automação de interface do usuário](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)). Isso ocorre porque os controles de texto geralmente são exibidos por meio da propriedade de nome de outro controle. Por exemplo, o texto que é usado para rotular um controle de edição é exposto por meio da propriedade de nome do controle de edição. Porque o controle de edição está em exibição de conteúdo a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] árvore, não é necessário para o elemento de texto em si esteja nesse modo de exibição do [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] árvore. Apenas o texto que aparece na exibição de conteúdo é texto que não é informações redundantes. Isso permite que qualquer tecnologia assistencial para rapidamente filtrar somente as partes de informações que os usuários precisam.  
  
#### <a name="edit"></a>Editar  
 Controles Edit permitem que um usuário para exibir e editar uma única linha de texto.  
  
> [!NOTE]
>  A única linha de texto pode ser quebrado em determinados cenários de layout.  
  
#### <a name="document"></a>Documento  
 Controles de documento permitem que um usuário navegue e obtenha informações de várias páginas de texto.  
  
<a name="TextPattern_Client_API_s"></a>   
## <a name="textpattern-client-apis"></a>TextPattern cliente da API  
  
|||  
|-|-|  
|`System.Windows.Automation.TextPattern Class`|O ponto de entrada para o [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] modelo de texto.<br /><br /> Essa classe também contém os dois <xref:System.Windows.Automation.TextPattern> ouvintes de eventos <xref:System.Windows.Automation.TextPattern.TextSelectionChangedEvent> e <xref:System.Windows.Automation.TextPattern.TextChangedEvent>.|  
|`System.Windows.Automation.Text.TextPatternRange Class`|A representação de um intervalo de texto dentro de um contêiner de texto que dá suporte a <xref:System.Windows.Automation.TextPattern>.<br /><br /> Clientes de automação de interface do usuário devem ter cuidadosos sobre a validade atual de um intervalo de texto criado usando <xref:System.Windows.Automation.Text.TextPatternRange>. Se o texto original no controle de texto for completamente substituído pelo novo texto, o intervalo de texto atual se tornará inválido. No entanto, o intervalo de texto pode ainda ter alguma viabilidade se apenas parte do texto original for alterada e o controle de texto subjacente está gerenciando seu texto "ponteiro" com âncoras (ou pontos de extremidade) em vez de usar posicionamento absoluto de caracteres.<br /><br /> Os clientes podem escutar um <xref:System.Windows.Automation.TextPattern.TextChangedEvent> para notificação de todas as alterações feitas no conteúdo textual que trabalham com.|  
|`System.Windows.Automation.AutomationTextAttribute Class`|Usado para identificar os atributos de formatação de um intervalo de texto.|  
  
<a name="TextPattern_Provider_API_s"></a>   
## <a name="textpattern-provider-apis"></a>APIs do provedor de TextPattern  
 Elementos de interface do usuário ou controles que dão suporte ao <xref:System.Windows.Automation.TextPattern> Implementando o <xref:System.Windows.Automation.Provider.ITextProvider> e <xref:System.Windows.Automation.Provider.ITextRangeProvider> interfaces, modo nativo ou, ou por meio das [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] proxies, são capazes de expor informações detalhadas de atributo para qualquer texto que eles contêm em Além de fornecer recursos de navegação robustos.  
  
 Um <xref:System.Windows.Automation.TextPattern> não tem provedor dar suporte a todos os atributos de texto se o controle não tem suporte para todos os atributos específicos.  
  
 Um <xref:System.Windows.Automation.TextPattern> provedor deve oferecer suporte a <xref:System.Windows.Automation.TextPattern.GetSelection%2A> e <xref:System.Windows.Automation.Text.TextPatternRange.Select%2A> funciona se o controle dá suporte à seleção de texto ou o posicionamento do cursor de texto (ou o cursor do sistema) dentro da área de texto. Se o controle não der suporte a essa funcionalidade, em seguida, ele não precisa dar suporte a qualquer um desses métodos. No entanto, o controle deve expor o tipo de seleção de texto, ele oferece suporte ao implementar o <xref:System.Windows.Automation.Provider.ITextProvider.SupportedTextSelection%2A> propriedade.  
  
 Um <xref:System.Windows.Automation.TextPattern> provedor sempre deve oferecer suporte a <xref:System.Windows.Automation.Text.TextUnit> constantes <xref:System.Windows.Automation.Text.TextUnit.Character> e <xref:System.Windows.Automation.Text.TextUnit.Document> , bem como qualquer outro <xref:System.Windows.Automation.Text.TextUnit> constantes é capaz de dar suporte.  
  
> [!NOTE]
>  O provedor pode ignorar o suporte para um determinado <xref:System.Windows.Automation.Text.TextUnit> adiando para a próxima maior <xref:System.Windows.Automation.Text.TextUnit> tem suporte na seguinte ordem: <xref:System.Windows.Automation.Text.TextUnit.Character>, <xref:System.Windows.Automation.Text.TextUnit.Format>, <xref:System.Windows.Automation.Text.TextUnit.Word>, <xref:System.Windows.Automation.Text.TextUnit.Line>, <xref:System.Windows.Automation.Text.TextUnit.Paragraph>, <xref:System.Windows.Automation.Text.TextUnit.Page>, e <xref:System.Windows.Automation.Text.TextUnit.Document> .  
  
|||  
|-|-|  
|`ITextProvider Interface`|Expõe métodos, propriedades e atributos que oferecem suporte a <xref:System.Windows.Automation.TextPattern> em aplicativos cliente (consulte <xref:System.Windows.Automation.Provider.ITextProvider>).|  
|`ITextRangeProvider Interface`|Representa um intervalo de texto em um provedor de texto (consulte <xref:System.Windows.Automation.Provider.ITextRangeProvider>).|  
|`System.Windows.Automation.TextPatternIdentifiers Class`|Contém valores que são usados como identificadores para provedores de texto (consulte <xref:System.Windows.Automation.TextPatternIdentifiers>).|  
  
<a name="Security"></a>   
## <a name="security"></a>Segurança  
 O [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] arquitetura foi projetada tendo em mente a segurança (consulte [visão geral de segurança de automação de interface do usuário](../../../docs/framework/ui-automation/ui-automation-security-overview.md)). No entanto, as classes TextPattern descritas nesta visão geral exigem algumas considerações de segurança específicos.  
  
-   [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] provedores de texto fornecem interfaces somente leitura e não fornecem a capacidade de alterar o texto existente em um controle.  
  
-   Clientes de automação de interface do usuário só podem usar [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] se eles forem totalmente "confiáveis". Um exemplo disso seria o Logon Desktop protegido, onde podem ser executado somente aplicativos conhecidos e confiáveis.  
  
-   Os desenvolvedores de provedores de automação de interface do usuário devem estar cientes de que todas as informações que eles optar por expor em seus controles por meio de [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] é, essencialmente, público e totalmente acessível por outro código. [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] não faz nenhum esforço para determinar que a confiabilidade de qualquer cliente de automação de interface do usuário e, portanto, o provedor de automação de interface do usuário não deve expor protegidas conteúdas textuais informações confidenciais (como campos de senha).  
  
-   Uma das alterações mais significativas de segurança para [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] é amplamente conhecido como "Proteger entrada" que abrange as tecnologias, como com privilégios mínimos (ou limitadas) contas de usuário (LUA) e o isolamento de nível de privilégio da interface do usuário (UIPI).  
  
    -   UIPI impede que um programa controlando e/ou monitoramento de outro programa "privilegiado" more, impedindo ataques de mensagem de janela de processo cruzado que imitam a entrada do usuário.  
  
    -   LUA define limites para os privilégios dos aplicativos sendo executados por usuários no grupo de administradores. Aplicativos não necessariamente têm privilégios de administrador, mas em vez disso, serão executado com os privilégios mínimos necessários. Como consequência, pode haver algumas restrições impostas em cenários LUA. Cadeia de caracteres mais notavelmente truncamento (incluindo strings TextPattern), onde pode ser necessário limitar o tamanho de cadeias de caracteres que está sendo recuperado do aplicativos de nível de administrador para que eles não sejam forçados a alocar memória para o ponto de desabilitar o aplicativo.  
  
<a name="Performance"></a>   
## <a name="performance"></a>Desempenho  
 Como TextPattern se baseia em chamadas de processo cruzado para a maioria das suas funcionalidades, ele não fornece um mecanismo de cache para melhorar o desempenho durante o processamento de conteúdo. Isso é diferente de outros padrões de controle em [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] que podem ser acessados usando o <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A> ou <xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A> métodos.  
  
 Uma tática para melhorar o desempenho é assegurar que os clientes de automação de interface do usuário de tentam recuperar blocos de texto por meio de tamanho moderado <xref:System.Windows.Automation.Text.TextPatternRange.GetText%2A>. Por exemplo, chamadas GetText (1) incorrerá ocorrências de processo cruzado para cada caractere, enquanto uma chamada de GetText(-1) incorrerá em um acerto de processo cruzado, mas pode ter alta latência, dependendo do tamanho do provedor de texto.  
  
<a name="Glossary"></a>   
## <a name="textpattern-terminology"></a>Terminologia de TextPattern  
 **Atributo**  
 Uma característica de formatação de um intervalo de texto (por exemplo, <xref:System.Windows.Automation.TextPattern.IsItalicAttribute> ou <xref:System.Windows.Automation.TextPattern.FontNameAttribute>).  
  
 **Intervalo de degeneração**  
 Um intervalo de degeneração é um intervalo de texto vazio ou zero caractere. Para os fins do padrão de controle TextPattern, o ponto de inserção de texto (ou o cursor do sistema) é considerado um intervalo de degeneração. Se nenhum texto estiver selecionado, <xref:System.Windows.Automation.TextPattern.GetSelection%2A> retornaria um intervalo de degeneração no ponto de inserção de texto e <xref:System.Windows.Automation.TextPattern.RangeFromPoint%2A> retornaria um intervalo degenerado como seu ponto de extremidade inicial. <xref:System.Windows.Automation.TextPattern.RangeFromChild%2A> e <xref:System.Windows.Automation.TextPattern.GetVisibleRanges%2A> podem retornar intervalos degenerados quando o provedor de texto não é possível localizar nenhum intervalo de texto que correspondem à condição fornecida. Esse intervalo de degeneração pode ser usado como um ponto de extremidade inicial no provedor de texto. <xref:System.Windows.Automation.Text.TextPatternRange.FindText%2A> e <xref:System.Windows.Automation.Text.TextPatternRange.FindAttribute%2A> retornar uma referência nula (`Nothing` no Microsoft Visual Basic .NET) para evitar confusão com um intervalo descoberto em comparação com um intervalo de degeneração.  
  
 **Objeto incorporado**  
 Há dois tipos de objetos incorporados no [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] modelo de texto. Eles consistem em elementos de conteúdo baseado em texto, como tabelas ou hiperlinks e elementos de controle, como imagens e botões. Para obter mais informações, consulte [acesso Embedded objetos usando automação de IU](../../../docs/framework/ui-automation/access-embedded-objects-using-ui-automation.md).  
  
 **Ponto de extremidade**  
 Absoluta <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.Start> ou <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End> ponto de um intervalo de texto dentro de um contêiner de texto.  
  
 ![TextPatternRangeEndpoints &#40;iniciar e terminar&#41;. ](../../../docs/framework/ui-automation/media/uia-textpattern-endpoints.PNG "UIA_TextPattern_Endpoints")  
O exemplo a seguir ilustra um conjunto de pontos iniciais e finais.  
  
 **TextRange**  
 Uma representação de um intervalo de texto, com pontos inicial e final, em um contêiner de texto, incluindo funcionalidades e todos os respectivos atributos.  
  
 <xref:System.Windows.Automation.Text.TextUnit>  
 Uma unidade predefinida de texto (caractere, palavra, linha ou parágrafo) usado para navegar pelos segmentos lógicos de um intervalo de texto.  
  
## <a name="see-also"></a>Consulte também  
 [Padrões de controle de automação de interface do usuário para clientes](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [Visão geral de padrões de controle de automação da interface do usuário](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [Visão geral de árvore de automação de interface do usuário](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [Usar o cache em automação de interface do usuário](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)  
 [Suporte a padrões de controle em um provedor de automação de interface do usuário](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [Mapeamento de padrão de controle para clientes de automação de interface do usuário](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md)  
 [Estrutura de serviços de texto](https://msdn.microsoft.com/library/default.asp?url=/library/tsf/tsf/text_services_framework.asp)
