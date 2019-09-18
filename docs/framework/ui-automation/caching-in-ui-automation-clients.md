---
title: Armazenando em cache em clientes de automação de interface do usuário
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation caching in clients
- caching, UI Automation clients
ms.assetid: 94c15031-4975-43cc-bcd5-c9439ed21c9c
ms.openlocfilehash: bf617279b16f53164209f5ae7605830dabda4c2e
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71043924"
---
# <a name="caching-in-ui-automation-clients"></a>Armazenando em cache em clientes de automação de interface do usuário
> [!NOTE]
> Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]recentes sobre [o, consulte API de automação do Windows: Automação](https://go.microsoft.com/fwlink/?LinkID=156746)da interface do usuário.  
  
 Este tópico apresenta o cache [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] de propriedades e padrões de controle.  
  
 No [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], o Caching significa Pre-busca de dados. Os dados podem então ser acessados sem mais comunicação entre processos. O cache é normalmente usado por aplicativos cliente de automação da interface do usuário para recuperar propriedades e padrões de controle em massa. As informações são recuperadas do cache conforme necessário. O aplicativo atualiza o cache periodicamente, geralmente em resposta a eventos, indicando que algo no [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] foi alterado.  
  
 Os benefícios do cache são mais perceptíveis com controles de Windows Presentation Foundation (WPF) e controles personalizados que têm provedores de automação de interface do usuário do lado do servidor. Há menos benefícios ao acessar provedores do lado do cliente, como os provedores padrão para [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] controles.  
  
 O cache ocorre quando o aplicativo ativa um <xref:System.Windows.Automation.CacheRequest> e, em seguida, usa qualquer método ou propriedade <xref:System.Windows.Automation.AutomationElement>que retorna um; <xref:System.Windows.Automation.AutomationElement.FindFirst%2A>por <xref:System.Windows.Automation.AutomationElement.FindAll%2A>exemplo,,. Os métodos da <xref:System.Windows.Automation.TreeWalker> classe são uma exceção; o Caching só será feito se um <xref:System.Windows.Automation.CacheRequest> for especificado como um parâmetro (por exemplo, <xref:System.Windows.Automation.TreeWalker.GetFirstChild%28System.Windows.Automation.AutomationElement%2CSystem.Windows.Automation.CacheRequest%29?displayProperty=nameWithType>.  
  
 O Caching também ocorre quando você assina um evento enquanto um <xref:System.Windows.Automation.CacheRequest> está ativo. O <xref:System.Windows.Automation.AutomationElement> passado para o manipulador de eventos como a origem de um evento contém as propriedades e os padrões armazenados em cache especificados <xref:System.Windows.Automation.CacheRequest>pelo original. Qualquer alteração feita <xref:System.Windows.Automation.CacheRequest> no depois que você assinar o evento não terá nenhum efeito.  
  
 As [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Propriedades e os padrões de controle de um elemento podem ser armazenados em cache.  
  
<a name="Options_for_Caching"></a>   
## <a name="options-for-caching"></a>Opções de cache  
 O <xref:System.Windows.Automation.CacheRequest> especifica as opções a seguir para o Caching.  
  
<a name="Properties_to_Cache"></a>   
### <a name="properties-to-cache"></a>Propriedades para armazenar em cache  
 Você pode especificar propriedades para cache chamando <xref:System.Windows.Automation.CacheRequest.Add%28System.Windows.Automation.AutomationProperty%29> para cada propriedade antes de ativar a solicitação.  
  
<a name="Control_Patterns_to_Cache"></a>   
### <a name="control-patterns-to-cache"></a>Padrões de controle para cache  
 Você pode especificar padrões de controle para cache chamando <xref:System.Windows.Automation.CacheRequest.Add%28System.Windows.Automation.AutomationPattern%29> para cada padrão antes de ativar a solicitação. Quando um padrão é armazenado em cache, suas propriedades não são armazenadas em cache automaticamente; Você deve especificar as propriedades que deseja armazenar em cache usando <xref:System.Windows.Automation.CacheRequest.Add%2A?displayProperty=nameWithType>.  
  
<a name="Scope_of_the_Caching"></a>   
### <a name="scope-and-filtering-of-caching"></a>Escopo e filtragem de cache  
 Você pode especificar os elementos cujas propriedades e padrões você deseja armazenar em cache definindo a <xref:System.Windows.Automation.CacheRequest.TreeScope%2A?displayProperty=nameWithType> propriedade antes de ativar a solicitação. O escopo é relativo aos elementos que são recuperados enquanto a solicitação está ativa. Por exemplo, se você definir apenas <xref:System.Windows.Automation.TreeScope.Children>e, em seguida, <xref:System.Windows.Automation.AutomationElement>recuperar um, as propriedades e os padrões de filhos desse elemento serão armazenados em cache, mas não os do próprio elemento. Para garantir que o cache seja feito para o próprio elemento recuperado, você deve <xref:System.Windows.Automation.TreeScope.Element> incluir <xref:System.Windows.Automation.CacheRequest.TreeScope%2A> na propriedade. Não é possível definir o escopo como <xref:System.Windows.Automation.TreeScope.Parent> ou. <xref:System.Windows.Automation.TreeScope.Ancestors> No entanto, um elemento pai pode ser armazenado em cache quando um elemento filho é armazenado em cache; consulte Recuperando filhos e pais em cache neste tópico.  
  
 A extensão do cache também é afetada pela <xref:System.Windows.Automation.CacheRequest.TreeFilter%2A?displayProperty=nameWithType> propriedade. Por padrão, o cache é executado somente para elementos que aparecem na exibição de controle da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] árvore. No entanto, você pode alterar essa propriedade para aplicar o cache a todos os elementos ou somente a elementos que aparecem na exibição de conteúdo.  
  
<a name="Strength_of_the_Element_References"></a>   
### <a name="strength-of-the-element-references"></a>Força das referências de elemento  
 Quando você recupera um <xref:System.Windows.Automation.AutomationElement>, por padrão, você tem acesso a todas as propriedades e padrões desse elemento, incluindo aqueles que não foram armazenados em cache. No entanto, para maior eficiência, você pode especificar que a referência ao elemento se refere somente a dados armazenados em cache <xref:System.Windows.Automation.CacheRequest.AutomationElementMode%2A> , definindo a <xref:System.Windows.Automation.CacheRequest> propriedade <xref:System.Windows.Automation.AutomationElementMode.None>de como. Nesse caso, você não tem acesso a nenhuma propriedade não armazenada em cache e padrões de elementos recuperados. Isso significa que você não pode acessar as propriedades <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A> por meio `Current` da propriedade <xref:System.Windows.Automation.AutomationElement> ou de qualquer padrão de controle; nem pode recuperar um padrão usando <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> ou <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A>. Em padrões armazenados em cache, você pode chamar métodos que recuperam Propriedades de matriz <xref:System.Windows.Automation.SelectionPattern.SelectionPatternInformation.GetSelection%2A?displayProperty=nameWithType>, como, mas não qualquer, que executam ações no controle <xref:System.Windows.Automation.InvokePattern.Invoke%2A?displayProperty=nameWithType>, como.  
  
 Um exemplo de um aplicativo que pode não precisar de referências completas a objetos é um leitor de tela, que buscaria <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A> as <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name%2A> Propriedades e dos elementos em uma janela, mas não <xref:System.Windows.Automation.AutomationElement> precisaria dos próprios objetos.  
  
<a name="Activating_the_CacheRequest"></a>   
## <a name="activating-the-cacherequest"></a>Ativando o CacheRequest  
 O cache é executado somente <xref:System.Windows.Automation.AutomationElement> quando os objetos são recuperados enquanto um <xref:System.Windows.Automation.CacheRequest> está ativo para o thread atual. Há duas maneiras de ativar um <xref:System.Windows.Automation.CacheRequest>.  
  
 A maneira usual é chamar <xref:System.Windows.Automation.CacheRequest.Activate%2A>. Esse método retorna um objeto que implementa <xref:System.IDisposable>. A solicitação permanece ativa contanto que o <xref:System.IDisposable> objeto exista. A maneira mais fácil de controlar o tempo de vida do objeto é colocar a chamada dentro de `using` umC#bloco ( `Using` ) ou (Visual Basic). Isso garante que a solicitação será exibida da pilha, mesmo que uma exceção seja gerada.  
  
 Outra maneira, que é útil quando você deseja aninhar solicitações de cache, é chamar <xref:System.Windows.Automation.CacheRequest.Push%2A>. Isso coloca a solicitação em uma pilha e a ativa. A solicitação permanece ativa até ser removida da pilha pelo <xref:System.Windows.Automation.CacheRequest.Pop%2A>. A solicitação se tornará temporariamente inativa se outra solicitação for enviada para a pilha; somente a solicitação superior na pilha está ativa.  
  
<a name="Retrieving_Cached_Properties"></a>   
## <a name="retrieving-cached-properties"></a>Recuperando propriedades armazenadas em cache  
 Você pode recuperar as propriedades armazenadas em cache de um elemento por meio dos métodos e propriedades a seguir.  
  
- <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.Cached%2A>  
  
 Uma exceção será gerada se a propriedade solicitada não estiver no cache.  
  
 <xref:System.Windows.Automation.AutomationElement.Cached%2A>, like <xref:System.Windows.Automation.AutomationElement.Current%2A>, expõe propriedades individuais como membros de uma estrutura. No entanto, você não precisa recuperar essa estrutura; Você pode acessar as propriedades individuais diretamente. Por exemplo, a <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name%2A> propriedade pode ser Obtida de `element.Cached.Name`, onde `element` é um <xref:System.Windows.Automation.AutomationElement>.  
  
<a name="Retrieving_Cached_Control_Patterns"></a>   
## <a name="retrieving-cached-control-patterns"></a>Recuperando padrões de controle armazenados em cache  
 Você pode recuperar os padrões de controle em cache de um elemento por meio dos métodos a seguir.  
  
- <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A>  
  
 Se o padrão não estiver no cache, <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A> o gerará uma exceção e <xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A> retornará. `false`  
  
 Você pode recuperar as propriedades armazenadas em cache de um padrão de controle usando `Cached` a propriedade do objeto Pattern. Você também pode recuperar os valores atuais por meio `Current` da propriedade, mas somente <xref:System.Windows.Automation.AutomationElementMode.None> se não tiver sido especificado <xref:System.Windows.Automation.AutomationElement> quando a foi recuperada. (<xref:System.Windows.Automation.AutomationElementMode.Full> é o valor padrão, e isso permite o acesso aos valores atuais.)  
  
<a name="Retrieving_Cached_Children_and_Parents"></a>   
## <a name="retrieving-cached-children-and-parents"></a>Recuperando filhos e pais armazenados em cache  
 Quando você recupera um <xref:System.Windows.Automation.AutomationElement> e solicita o Caching para filhos desse elemento por meio <xref:System.Windows.Automation.CacheRequest.TreeScope%2A> da propriedade da solicitação, ele é posteriormente possível obter <xref:System.Windows.Automation.AutomationElement.CachedChildren%2A> os elementos filho da Propriedade do elemento que você recuperou.  
  
 Se <xref:System.Windows.Automation.TreeScope.Element> foi incluído no escopo da solicitação de cache, o elemento raiz da solicitação estará posteriormente disponível <xref:System.Windows.Automation.AutomationElement.CachedParent%2A> na propriedade de qualquer um dos elementos filho.  
  
> [!NOTE]
> Você não pode armazenar em cache pais ou ancestrais do elemento raiz da solicitação.  
  
<a name="Updating_the_Cache"></a>   
## <a name="updating-the-cache"></a>Atualizando o cache  
 O cache é válido somente quando nada é alterado no [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]. Seu aplicativo é responsável por atualizar o cache, normalmente em resposta a eventos.  
  
 Se você se inscrever em um evento <xref:System.Windows.Automation.CacheRequest> enquanto um estiver ativo, você <xref:System.Windows.Automation.AutomationElement> Obtém um com um cache atualizado como a origem do evento sempre que seu delegado de manipulador de eventos é chamado. Você também pode atualizar informações armazenadas em cache para um elemento chamando <xref:System.Windows.Automation.AutomationElement.GetUpdatedCache%2A>. Você pode passar o original <xref:System.Windows.Automation.CacheRequest> para atualizar todas as informações que foram anteriormente armazenadas em cache.  
  
 A atualização do cache não altera as propriedades de nenhuma referência <xref:System.Windows.Automation.AutomationElement> existente.  
  
## <a name="see-also"></a>Consulte também

- [Eventos de automação de interface do usuário para clientes](ui-automation-events-for-clients.md)
- [Usar o cache em automação de interface do usuário](use-caching-in-ui-automation.md)
- [Exemplo de FetchTimer](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771456(v=vs.90))
