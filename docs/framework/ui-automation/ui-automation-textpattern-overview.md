---
title: "Visão geral de TextPattern de automação da interface do usuário"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UI Automation, TextPattern class
- TextPattern class
- classes, TextPattern
ms.assetid: 41787927-df1f-4f4a-aba3-641662854fc4
caps.latest.revision: "38"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 56b0774db462c92c6ab0d66ab7158dcc01da0c9e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ui-automation-textpattern-overview"></a>Visão geral de TextPattern de automação da interface do usuário
> [!NOTE]
>  Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746) (API de Automação do Windows: Automação da Interface do Usuário).  
  
 Esta visão geral descreve como usar [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] para expor o conteúdo textual, incluindo atributos de formato e de estilo, dos controles de texto em [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]-as plataformas com suporte. Esses controles incluem, mas não está limitados a, o [!INCLUDE[TLA#tla_winfx](../../../includes/tlasharptla-winfx-md.md)] <xref:System.Windows.Controls.TextBox> e <xref:System.Windows.Controls.RichTextBox> , bem como seus [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] equivalentes.  
  
 Expondo o conteúdo textual de um controle é realizada através do uso do <xref:System.Windows.Automation.TextPattern> padrão de controle, que representa o conteúdo de um recipiente de texto como um fluxo de texto. Por sua vez, <xref:System.Windows.Automation.TextPattern> requer o suporte do <xref:System.Windows.Automation.Text.TextPatternRange> classe para expor os atributos de formato e estilo. <xref:System.Windows.Automation.Text.TextPatternRange>dá suporte a <xref:System.Windows.Automation.TextPattern> por representando contíguas ou várias ramificações intervalos de texto em um recipiente de texto com uma coleção de <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.Start> e <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End> pontos de extremidade. <xref:System.Windows.Automation.Text.TextPatternRange>oferece suporte a funcionalidades como seleção, comparação, recuperação e de passagem.  
  
> [!NOTE]
>  O <xref:System.Windows.Automation.TextPattern> classes não fornecem um meio para inserir ou modificar o texto. No entanto, dependendo do controle, isso pode ser obtido com o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] <xref:System.Windows.Automation.ValuePattern> ou por meio da entrada direta do teclado. Consulte o [TextPattern inserir texto exemplo](http://msdn.microsoft.com/en-us/67353f93-7ee2-42f2-ab76-5c078cf6ca16) para obter um exemplo.  
  
 A funcionalidade descrita nesta visão geral é essencial para fornecedores de tecnologia assistencial e seus usuários finais. Podem usar tecnologias assistenciais [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] para reunir informações de formatação para o usuário de texto completo e fornecer a navegação através de programação e seleção de texto por <xref:System.Windows.Automation.Text.TextUnit> (caractere, palavra, linha ou parágrafo).  
  
<a name="UI_Automation_TextPattern_vs__Cicero"></a>   
## <a name="ui-automation-textpattern-vs-text-services-framework"></a>Vs de TextPattern de automação de interface do usuário. Estrutura de serviços de texto  
 [!INCLUDE[TLA#tla_tsf](../../../includes/tlasharptla-tsf-md.md)]é uma estrutura de sistema simples e escalável que permite serviços em linguagem natural e na área de trabalho e em aplicativos de entrada de texto avançada. Além de fornecer interfaces para aplicativos para expor seu armazenamento de texto também suporta metadados para esse armazenamento de texto.  
  
 No entanto, [!INCLUDE[TLA2#tla_tsf](../../../includes/tla2sharptla-tsf-md.md)] foi projetado para aplicativos que precisam inserir dados de entrada em situações cientes de contexto enquanto <xref:System.Windows.Automation.TextPattern> se destina a fornecer acesso otimizado a um armazenamento de texto para uma solução somente leitura (com a alternativa limitada indicada acima) leitores de tela e dispositivos Braille.  
  
 Em resumo, acessíveis tecnologias que exigem acesso somente leitura a um armazenamento de texto podem usar <xref:System.Windows.Automation.TextPattern>, mas será necessário a funcionalidade mais complexa do [!INCLUDE[TLA2#tla_tsf](../../../includes/tla2sharptla-tsf-md.md)] para entrada ciente de contexto.  
  
<a name="Control_Types"></a>   
## <a name="control-types"></a>Tipos de controle  
  
#### <a name="text"></a>Texto  
 O controle de texto é o elemento básico que representa um trecho de texto na tela.  
  
 Um controle de texto autônomo pode ser usado como um rótulo ou texto estático em um formulário. Controles de texto também podem ser contidos dentro da estrutura de um <xref:System.Windows.Automation.ControlType.ListItem>, <xref:System.Windows.Automation.ControlType.TreeItem> ou <xref:System.Windows.Automation.ControlType.DataItem>.  
  
> [!NOTE]
>  Controles de texto podem não aparecer na exibição de conteúdo de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] árvore (consulte [visão geral de árvore de automação de interface do usuário](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)). Isso ocorre porque os controles de texto geralmente são exibidos por meio da propriedade de nome de outro controle. Por exemplo, o texto que é usado para rotular um controle de edição é exposto por meio da propriedade de nome do controle de edição. Como o controle de edição está na exibição de conteúdo do [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] árvore, não é necessário para o elemento de texto em si esteja no modo de exibição do [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] árvore. Apenas o texto que aparece na exibição de conteúdo é o texto que não é informações redundantes. Isso permite que qualquer tecnologia assistencial filtrar rapidamente somente em pedaços de informações que os usuários precisam.  
  
#### <a name="edit"></a>Editar  
 Controles Edit permitem que um usuário para exibir e editar uma única linha de texto.  
  
> [!NOTE]
>  A única linha de texto pode ser quebrado em determinados cenários de layout.  
  
#### <a name="document"></a>Documento  
 Controles de documento permitem que um usuário navegue e obtenha informações de várias páginas de texto.  
  
<a name="TextPattern_Client_API_s"></a>   
## <a name="textpattern-client-apis"></a>Cliente de TextPattern da API  
  
|||  
|-|-|  
|`System.Windows.Automation.TextPattern Class`|O ponto de entrada para o [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] modelo de texto.<br /><br /> Essa classe também contém os dois <xref:System.Windows.Automation.TextPattern> ouvintes de evento, <xref:System.Windows.Automation.TextPattern.TextSelectionChangedEvent> e <xref:System.Windows.Automation.TextPattern.TextChangedEvent>.|  
|`System.Windows.Automation.Text.TextPatternRange Class`|A representação de um intervalo de texto dentro de um contêiner de texto que dá suporte a <xref:System.Windows.Automation.TextPattern>.<br /><br /> Clientes de automação de interface do usuário devem ter cuidadosos em relação à validade atual de um intervalo de texto criado com <xref:System.Windows.Automation.Text.TextPatternRange>. Se o texto original no controle de texto é totalmente substituído pelo novo texto, o intervalo de texto atual se torna inválido. No entanto, o intervalo de texto ainda pode ter alguma viabilidade se apenas parte do texto original for alterada e o controle de texto subjacente estiver gerenciando seu texto "ponteiro" com âncoras (ou pontos de extremidade) em vez do posicionamento absoluto de caracteres.<br /><br /> Os clientes podem escutar um <xref:System.Windows.Automation.TextPattern.TextChangedEvent> para notificação de alterações para o conteúdo textual estiverem trabalhando com.|  
|`System.Windows.Automation.AutomationTextAttribute Class`|Usado para identificar os atributos de formatação de um intervalo de texto.|  
  
<a name="TextPattern_Provider_API_s"></a>   
## <a name="textpattern-provider-apis"></a>APIs do provedor de TextPattern  
 Elementos de interface do usuário ou controles que dão suporte a <xref:System.Windows.Automation.TextPattern> Implementando o <xref:System.Windows.Automation.Provider.ITextProvider> e <xref:System.Windows.Automation.Provider.ITextRangeProvider> as interfaces, ou modo nativo ou por meio [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] proxies, são capazes de expor informações de atributo detalhadas para qualquer texto que eles contêm em Além de fornecer recursos de navegação robustos.  
  
 Um <xref:System.Windows.Automation.TextPattern> não tem provedor dar suporte a todos os atributos de texto se o controle não tem suporte para algum atributo específico.  
  
 Um <xref:System.Windows.Automation.TextPattern> provedor deve oferecer suporte a <xref:System.Windows.Automation.TextPattern.GetSelection%2A> e <xref:System.Windows.Automation.Text.TextPatternRange.Select%2A> funciona se o controle oferece suporte a seleção de texto ou o posicionamento do cursor de texto (ou cursor do sistema) na área de texto. Se o controle não oferece suporte a essa funcionalidade, em seguida, ele não precisa dar suporte a qualquer um desses métodos. No entanto, o controle deve expor o tipo de seleção de texto, ele oferece suporte ao implementar a <xref:System.Windows.Automation.Provider.ITextProvider.SupportedTextSelection%2A> propriedade.  
  
 Um <xref:System.Windows.Automation.TextPattern> provedor sempre deve oferecer suporte a <xref:System.Windows.Automation.Text.TextUnit> constantes <xref:System.Windows.Automation.Text.TextUnit.Character> e <xref:System.Windows.Automation.Text.TextUnit.Document> , bem como qualquer outro <xref:System.Windows.Automation.Text.TextUnit> constantes é capaz de dar suporte.  
  
> [!NOTE]
>  O provedor pode ignorar o suporte para um determinado <xref:System.Windows.Automation.Text.TextUnit> , adiando para o próximo maior <xref:System.Windows.Automation.Text.TextUnit> suporte na seguinte ordem: <xref:System.Windows.Automation.Text.TextUnit.Character>, <xref:System.Windows.Automation.Text.TextUnit.Format>, <xref:System.Windows.Automation.Text.TextUnit.Word>, <xref:System.Windows.Automation.Text.TextUnit.Line>, <xref:System.Windows.Automation.Text.TextUnit.Paragraph>, <xref:System.Windows.Automation.Text.TextUnit.Page>, e <xref:System.Windows.Automation.Text.TextUnit.Document> .  
  
|||  
|-|-|  
|`ITextProvider Interface`|Expõe métodos, propriedades e atributos que oferecem suporte a <xref:System.Windows.Automation.TextPattern> em aplicativos cliente (consulte <xref:System.Windows.Automation.Provider.ITextProvider>).|  
|`ITextRangeProvider Interface`|Representa um intervalo de texto em um provedor de texto (consulte <xref:System.Windows.Automation.Provider.ITextRangeProvider>).|  
|`System.Windows.Automation.TextPatternIdentifiers Class`|Contém valores que são usados como identificadores para provedores de texto (consulte <xref:System.Windows.Automation.TextPatternIdentifiers>).|  
  
<a name="Security"></a>   
## <a name="security"></a>Segurança  
 O [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] arquitetura foi projetada com base na segurança (consulte [visão geral de segurança de automação de interface do usuário](../../../docs/framework/ui-automation/ui-automation-security-overview.md)). No entanto, as classes TextPattern descritas nesta visão geral exigem algumas considerações de segurança específico.  
  
-   [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]provedores de texto fornecem interfaces de somente leitura e não fornecem a capacidade de alterar o texto existente em um controle.  
  
-   Clientes de automação de interface do usuário só podem usar [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] se eles forem totalmente "confiáveis". Um exemplo disso seria o Logon Desktop protegido, onde somente aplicativos conhecidos e confiáveis podem ser executado.  
  
-   Os desenvolvedores de provedores de automação de interface do usuário devem estar cientes de que todas as informações que escolherem para expor seus controles por meio de [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] é essencialmente público e totalmente acessível por outro código. [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]não faz nenhum esforço para determinar que a integridade de qualquer cliente de automação de interface do usuário e, portanto, o provedor de automação de interface do usuário não deve expor protegidas conteúdas textuais informações confidenciais (como campos de senha).  
  
-   Uma das alterações mais significativas de segurança para [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] é conhecida como "Secure Input" que abrange as tecnologias como menos privilegiado (ou limitadas) contas de usuário (LUA) e isolamento de nível de privilégio da interface do usuário (UIPI).  
  
    -   UIPI impede que um programa controle e/ou monitore outro programa mais de "privilegiado", evitando ataques de mensagem de janela entre processos que falsifiquem a entrada do usuário.  
  
    -   LUA estabelece limites para os privilégios dos aplicativos sendo executados por usuários no grupo de administradores. Aplicativos não necessariamente têm privilégios de administrador, mas em vez disso serão executado com os privilégios mínimos necessários. Como consequência, pode haver algumas restrições impostas em situações LUA. Cadeia de caracteres principalmente truncamento (incluindo strings TextPattern), onde pode ser necessário limitar o tamanho de cadeias de caracteres estão sendo recuperados no nível de administrador de aplicativos para que eles não sejam forçados a alocar memória para o ponto de desabilitar o aplicativo.  
  
<a name="Performance"></a>   
## <a name="performance"></a>Desempenho  
 Como TextPattern se baseia em chamadas entre processos para a maioria de sua funcionalidade, ele não fornece um mecanismo de cache para melhorar o desempenho durante o processamento de conteúdo. Isso é diferente de outros padrões de controle em [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] que podem ser acessados usando o <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A> ou <xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A> métodos.  
  
 É uma tática para melhorar o desempenho, certificando-se de clientes de automação de interface do usuário tentam recuperar blocos de texto usando tamanho moderadamente <xref:System.Windows.Automation.Text.TextPatternRange.GetText%2A>. Por exemplo, chamadas GetText (1) incorrerá em processo cruzado de ocorrências para cada caractere enquanto uma chamada GetText(-1) incorrerá em uma ocorrência de processo cruzado, mas pode ter alta latência dependendo do tamanho do provedor de texto.  
  
<a name="Glossary"></a>   
## <a name="textpattern-terminology"></a>Terminologia de TextPattern  
 **Atributo**  
 Uma característica de formatação de um intervalo de texto (por exemplo, <xref:System.Windows.Automation.TextPattern.IsItalicAttribute> ou <xref:System.Windows.Automation.TextPattern.FontNameAttribute>).  
  
 **Intervalo degenerado**  
 Um intervalo degenerado é um intervalo de texto vazio ou com zero caracteres. Para os fins do padrão de controle TextPattern, o ponto de inserção de texto (ou o cursor do sistema) é considerado um intervalo degenerado. Se nenhum texto estiver selecionado, <xref:System.Windows.Automation.TextPattern.GetSelection%2A> retornaria um intervalo degenerado no ponto de inserção de texto e <xref:System.Windows.Automation.TextPattern.RangeFromPoint%2A> retornaria um intervalo degenerado como seu ponto de extremidade inicial. <xref:System.Windows.Automation.TextPattern.RangeFromChild%2A>e <xref:System.Windows.Automation.TextPattern.GetVisibleRanges%2A> podem retornar intervalos degenerados quando o provedor de texto não é possível localizar nenhum intervalo de texto que correspondem à condição especificada. Esse intervalo degenerado pode ser usado como um ponto de extremidade inicial no provedor de texto. <xref:System.Windows.Automation.Text.TextPatternRange.FindText%2A>e <xref:System.Windows.Automation.Text.TextPatternRange.FindAttribute%2A> retornam uma referência nula (`Nothing` em [!INCLUDE[TLA2#tla_visualbnet](../../../includes/tla2sharptla-visualbnet-md.md)]) para evitar confusão com um intervalo descoberto degenerado.  
  
 **Objeto inserido**  
 Há dois tipos de objetos incorporados no [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] modelo de texto. Eles consistem em elementos de conteúdo baseado em texto, como hiperlinks ou tabelas e elementos de controle, como imagens e botões. Para obter mais informações, consulte [acesso incorporado objetos usando automação de IU](../../../docs/framework/ui-automation/access-embedded-objects-using-ui-automation.md).  
  
 **Ponto de extremidade**  
 Absoluto <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.Start> ou <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End> ponto de um intervalo de texto dentro de um contêiner de texto.  
  
 ![TextPatternRangeEndpoints &#40; início e término &#41;. ] (../../../docs/framework/ui-automation/media/uia-textpattern-endpoints.PNG "UIA_TextPattern_Endpoints")  
O exemplo a seguir ilustra um conjunto de pontos inicial e final.  
  
 **TextRange**  
 Uma representação de um intervalo de texto, com os pontos inicial e final, em um contêiner de texto, incluindo todos os respectivos atributos e funcionalidade.  
  
 <xref:System.Windows.Automation.Text.TextUnit>  
 Uma unidade predefinida de texto (caractere, palavra, linha ou parágrafo) usado para navegar pelos segmentos lógicos de um intervalo de texto.  
  
## <a name="see-also"></a>Consulte também  
 [Padrões de controle de automação de interface do usuário para clientes](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [Visão geral de padrões de controle de automação da interface do usuário](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [Visão geral de árvore de automação de interface do usuário](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [Usar o cache em automação de interface do usuário](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)  
 [Suporte a padrões de controle em um provedor de automação de interface do usuário](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [Mapeamento de padrão de controle para clientes de automação de interface do usuário](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md)  
 [Estrutura de serviços de texto](http://msdn.microsoft.com/library/default.asp?url=/library/tsf/tsf/text_services_framework.asp)
