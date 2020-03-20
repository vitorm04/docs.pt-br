---
title: Armazenando em cache em clientes de automação de interface do usuário
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation caching in clients
- caching, UI Automation clients
ms.assetid: 94c15031-4975-43cc-bcd5-c9439ed21c9c
ms.openlocfilehash: 186ed77594aadab9e3f49ef30e559e159aee1b60
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180281"
---
# <a name="caching-in-ui-automation-clients"></a>Armazenando em cache em clientes de automação de interface do usuário
> [!NOTE]
> Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32) (API de Automação do Windows: Automação da Interface do Usuário).  
  
 Este tópico introduz cache [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] de propriedades e padrões de controle.  
  
 Em [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], cache significa pré-busca de dados. Os dados podem então ser acessados sem maiorcomunicação entre processos. O cache é normalmente usado por aplicativos clientes de automação de interface do usuário para recuperar propriedades e padrões de controle em massa. As informações são então recuperadas do cache conforme necessário. O aplicativo atualiza o cache periodicamente, geralmente em resposta [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] a eventos que significam que algo no foi alterado.  
  
 Os benefícios do cache são mais perceptíveis com os controles WPF (Windows Presentation Foundation) e controles personalizados que possuem provedores de automação de ui do lado do servidor. Há menos benefícios ao acessar provedores do lado do cliente, como os provedores padrão para controles Win32.  
  
 O cache ocorre quando o <xref:System.Windows.Automation.CacheRequest> aplicativo ativa um e, <xref:System.Windows.Automation.AutomationElement>em seguida, usa qualquer método ou propriedade que devolva um ; por <xref:System.Windows.Automation.AutomationElement.FindFirst%2A>exemplo, <xref:System.Windows.Automation.AutomationElement.FindAll%2A>. Os métodos <xref:System.Windows.Automation.TreeWalker> da classe são uma exceção; o cache só é <xref:System.Windows.Automation.CacheRequest> feito se um for especificado <xref:System.Windows.Automation.TreeWalker.GetFirstChild%28System.Windows.Automation.AutomationElement%2CSystem.Windows.Automation.CacheRequest%29?displayProperty=nameWithType>como parâmetro (por exemplo, .  
  
 O cache também ocorre quando você <xref:System.Windows.Automation.CacheRequest> se inscreve em um evento enquanto um está ativo. O <xref:System.Windows.Automation.AutomationElement> passado para o manipulador de eventos como a fonte de um <xref:System.Windows.Automation.CacheRequest>evento contém as propriedades e padrões armazenados em cache especificados pelo original . Quaisquer alterações <xref:System.Windows.Automation.CacheRequest> feitas no depois de se inscrever no evento não têm efeito.  
  
 As [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] propriedades e padrões de controle de um elemento podem ser armazenados em cache.  
  
<a name="Options_for_Caching"></a>
## <a name="options-for-caching"></a>Opções para Cache  
 O <xref:System.Windows.Automation.CacheRequest> especifica as seguintes opções para cache.  
  
<a name="Properties_to_Cache"></a>
### <a name="properties-to-cache"></a>Propriedades para cache  
 Você pode especificar propriedades <xref:System.Windows.Automation.CacheRequest.Add%28System.Windows.Automation.AutomationProperty%29> para cache, chamando para cada propriedade antes de ativar a solicitação.  
  
<a name="Control_Patterns_to_Cache"></a>
### <a name="control-patterns-to-cache"></a>Padrões de controle para cache  
 Você pode especificar padrões <xref:System.Windows.Automation.CacheRequest.Add%28System.Windows.Automation.AutomationPattern%29> de controle para cache, chamando para cada padrão antes de ativar a solicitação. Quando um padrão é armazenado em cache, suas propriedades não são armazenadas automaticamente em cache; você deve especificar as propriedades <xref:System.Windows.Automation.CacheRequest.Add%2A?displayProperty=nameWithType>que deseja em cache usando .  
  
<a name="Scope_of_the_Caching"></a>
### <a name="scope-and-filtering-of-caching"></a>Escopo e filtragem de cache  
 Você pode especificar os elementos cujas propriedades <xref:System.Windows.Automation.CacheRequest.TreeScope%2A?displayProperty=nameWithType> e padrões você deseja armazenar definindo a propriedade antes de ativar a solicitação. O escopo é relativo aos elementos que são recuperados enquanto a solicitação está ativa. Por exemplo, se <xref:System.Windows.Automation.TreeScope.Children>você definir apenas <xref:System.Windows.Automation.AutomationElement>, e, em seguida, recuperar um , as propriedades e padrões de crianças desse elemento são armazenados em cache, mas não os do elemento em si. Para garantir que o cache seja feito para o <xref:System.Windows.Automation.TreeScope.Element> elemento <xref:System.Windows.Automation.CacheRequest.TreeScope%2A> recuperado em si, você deve incluir na propriedade. Não é possível definir o <xref:System.Windows.Automation.TreeScope.Parent> <xref:System.Windows.Automation.TreeScope.Ancestors>escopo para ou . No entanto, um elemento pai pode ser armazenado em cache quando um elemento filho é armazenado em cache; ver Recuperando crianças e pais armazenados em cache neste tópico.  
  
 A extensão do cache também <xref:System.Windows.Automation.CacheRequest.TreeFilter%2A?displayProperty=nameWithType> é afetada pela propriedade. Por padrão, o cache é realizado apenas para elementos que aparecem na visão de controle da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] árvore. No entanto, você pode alterar esta propriedade para aplicar cache a todos os elementos, ou apenas a elementos que aparecem na exibição de conteúdo.  
  
<a name="Strength_of_the_Element_References"></a>
### <a name="strength-of-the-element-references"></a>Força das Referências do Elemento  
 Quando você <xref:System.Windows.Automation.AutomationElement>recupera um , por padrão, você tem acesso a todas as propriedades e padrões desse elemento, incluindo aqueles que não foram armazenados em cache. No entanto, para maior eficiência, você pode especificar que a referência <xref:System.Windows.Automation.CacheRequest.AutomationElementMode%2A> ao elemento <xref:System.Windows.Automation.CacheRequest> <xref:System.Windows.Automation.AutomationElementMode.None>refere-se apenas a dados armazenados em cache, definindo a propriedade do to . Neste caso, você não tem acesso a quaisquer propriedades e padrões não armazenados em cache de elementos recuperados. Isso significa que você não <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A> pode `Current` acessar <xref:System.Windows.Automation.AutomationElement> quaisquer propriedades através ou propriedade ou qualquer padrão de controle; nem você pode recuperar <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> um <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A>padrão usando ou . Em padrões armazenados em cache, você pode <xref:System.Windows.Automation.SelectionPattern.SelectionPatternInformation.GetSelection%2A?displayProperty=nameWithType>chamar métodos que recuperam propriedades do <xref:System.Windows.Automation.InvokePattern.Invoke%2A?displayProperty=nameWithType>array, como , mas não qualquer um que execute ações no controle, como .  
  
 Um exemplo de um aplicativo que pode não precisar de referências completas <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A> aos objetos é um leitor <xref:System.Windows.Automation.AutomationElement> de tela, que prebuscaria as <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name%2A> propriedades dos elementos em uma janela, mas não precisaria dos objetos em si.  
  
<a name="Activating_the_CacheRequest"></a>
## <a name="activating-the-cacherequest"></a>Ativando o CacheRequest  
 O cache é <xref:System.Windows.Automation.AutomationElement> realizado somente quando <xref:System.Windows.Automation.CacheRequest> os objetos são recuperados enquanto um está ativo para o segmento atual. Há duas maneiras <xref:System.Windows.Automation.CacheRequest>de ativar um .  
  
 A maneira usual <xref:System.Windows.Automation.CacheRequest.Activate%2A>é ligar. Este método retorna um <xref:System.IDisposable>objeto que implementa . A solicitação permanece ativa <xref:System.IDisposable> enquanto o objeto existir. A maneira mais fácil de controlar a vida útil do `using` objeto é `Using` encerrar a chamada dentro de um bloco (C#) ou (Visual Basic). Isso garante que a solicitação seja retirada da pilha mesmo que uma exceção seja levantada.  
  
 Outra forma, que é útil quando você deseja <xref:System.Windows.Automation.CacheRequest.Push%2A>fazer solicitações de cache, é ligar . Isso coloca o pedido em uma pilha e o ativa. A solicitação permanece ativa até que <xref:System.Windows.Automation.CacheRequest.Pop%2A>seja removida da pilha por . A solicitação torna-se temporariamente inativa se outra solicitação for empurrada para a pilha; apenas a solicitação superior na pilha está ativa.  
  
<a name="Retrieving_Cached_Properties"></a>
## <a name="retrieving-cached-properties"></a>Recuperando propriedades armazenadas em cache  
 Você pode recuperar as propriedades armazenadas em cache de um elemento através dos seguintes métodos e propriedades.  
  
- <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.Cached%2A>  
  
 Uma exceção é levantada se a propriedade solicitada não estiver no cache.  
  
 <xref:System.Windows.Automation.AutomationElement.Cached%2A>, <xref:System.Windows.Automation.AutomationElement.Current%2A>como, expõe propriedades individuais como membros de uma estrutura. No entanto, você não precisa recuperar essa estrutura; você pode acessar as propriedades individuais diretamente. Por exemplo, <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name%2A> a propriedade pode `element.Cached.Name`ser `element` obtida <xref:System.Windows.Automation.AutomationElement>a partir de , onde está um .  
  
<a name="Retrieving_Cached_Control_Patterns"></a>
## <a name="retrieving-cached-control-patterns"></a>Recuperando padrões de controle em cache  
 Você pode recuperar os padrões de controle armazenados em cache de um elemento através dos seguintes métodos.  
  
- <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A>  
  
 Se o padrão não estiver <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A> no cache, <xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A> `false`aumenta uma exceção e retorna .  
  
 Você pode recuperar as propriedades armazenadas em `Cached` cache de um padrão de controle usando a propriedade do objeto padrão. Você também pode recuperar os `Current` valores atuais através da propriedade, mas apenas se <xref:System.Windows.Automation.AutomationElementMode.None> não foi especificado quando o <xref:System.Windows.Automation.AutomationElement> foi recuperado. (<xref:System.Windows.Automation.AutomationElementMode.Full> é o valor padrão, e isso permite o acesso aos valores atuais.)  
  
<a name="Retrieving_Cached_Children_and_Parents"></a>
## <a name="retrieving-cached-children-and-parents"></a>Recuperando crianças e pais em cache  
 Quando você <xref:System.Windows.Automation.AutomationElement> recupera um cache e solicita cache <xref:System.Windows.Automation.CacheRequest.TreeScope%2A> para crianças desse elemento através da propriedade da <xref:System.Windows.Automation.AutomationElement.CachedChildren%2A> solicitação, é posteriormente possível obter os elementos da criança da propriedade do elemento que você recuperou.  
  
 Se <xref:System.Windows.Automation.TreeScope.Element> foi incluído no escopo da solicitação de cache, o elemento <xref:System.Windows.Automation.AutomationElement.CachedParent%2A> raiz da solicitação está posteriormente disponível a partir da propriedade de qualquer um dos elementos filho.  
  
> [!NOTE]
> Você não pode cache pais ou ancestrais do elemento raiz da solicitação.  
  
<a name="Updating_the_Cache"></a>
## <a name="updating-the-cache"></a>Atualizando o cache  
 O cache é válido apenas enquanto [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]nada mudar no . Seu aplicativo é responsável por atualizar o cache, normalmente em resposta a eventos.  
  
 Se você se inscrever <xref:System.Windows.Automation.CacheRequest> em um evento <xref:System.Windows.Automation.AutomationElement> enquanto estiver ativo, você obtém um cache atualizado como a fonte do evento sempre que seu delegado manipulador de eventos é chamado. Você também pode atualizar informações armazenadas <xref:System.Windows.Automation.AutomationElement.GetUpdatedCache%2A>em cache para um elemento ligando . Você pode passar <xref:System.Windows.Automation.CacheRequest> no original para atualizar todas as informações que foram armazenadas anteriormente em cache.  
  
 A atualização do cache não altera <xref:System.Windows.Automation.AutomationElement> as propriedades de quaisquer referências existentes.  
  
## <a name="see-also"></a>Confira também

- [Automação de Eventos de Interface de Usuário para Clientes.](ui-automation-events-for-clients.md)
- [Usar armazenamento em cache em automação de interface do usuário](use-caching-in-ui-automation.md)
- [Amostra de FetchTimer](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771456(v=vs.90))
