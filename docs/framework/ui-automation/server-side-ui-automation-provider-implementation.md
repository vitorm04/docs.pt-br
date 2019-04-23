---
title: Implementação do provedor de automação de interface do usuário no lado do servidor
ms.date: 03/30/2017
helpviewer_keywords:
- server-side UI Automation provider implementation
- UI Automation, server-side provider implementation
- provider implementation, UI Automation
ms.assetid: 6acc6d08-bd67-4e2e-915c-9c1d34eb86fe
ms.openlocfilehash: 3b3e69d1c52b98822a4cf3b75de74466e1dc68f0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59320041"
---
# <a name="server-side-ui-automation-provider-implementation"></a>Implementação do provedor de automação de interface do usuário no lado do servidor
> [!NOTE]
>  Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: Automação de interface do usuário](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Esta seção descreve como implementar um provedor de automação de interface do usuário do lado do servidor para um controle personalizado.  
  
 A implementação para elementos do Windows Presentation Foundation (WPF) e não-[!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] elementos (como aqueles projetado para [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)]) é fundamentalmente diferente. [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] elementos oferecem suporte para [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] por meio de uma classe derivada de <xref:System.Windows.Automation.Peers.AutomationPeer>. Não -[!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] elementos oferecem suporte por meio de implementações de interfaces de provedor.  
  
<a name="Security_Considerations"></a>   
## <a name="security-considerations"></a>Considerações sobre segurança  
 Provedores devem ser escritos para que eles podem trabalhar em um ambiente de confiança parcial. Porque UIAutomationClient. dll não está configurado para ser executado em confiança parcial, seu código de provedor não deve referenciar o assembly. Se isso acontecer, o código pode executar em um ambiente de confiança total, mas, em seguida, falhar em um ambiente de confiança parcial.  
  
 Em particular, não use campos de classes em UIAutomationClient. dll, como aqueles em <xref:System.Windows.Automation.AutomationElement>. Em vez disso, use os campos equivalentes de classes em UIAutomationTypes. dll, tais como <xref:System.Windows.Automation.AutomationElementIdentifiers>.  
  
<a name="Provider_Implementation_by_WPF_Elements"></a>   
## <a name="provider-implementation-by-windows-presentation-foundation-elements"></a>Implementação de provedor por elementos do Windows Presentation Foundation  
 Para obter mais informações sobre esse tópico, consulte [automação de interface do usuário de um controle personalizado do WPF](../../../docs/framework/wpf/controls/ui-automation-of-a-wpf-custom-control.md).  
  
<a name="Provider_Implementation_by_non_WPF_Elements"></a>   
## <a name="provider-implementation-by-non-wpf-elements"></a>Implementação de provedor por elementos não - WPF  
 Controles personalizados que não fazem parte da [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] framework, mas que são escritos em código gerenciado (com mais frequência essas são [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] controles), dão suporte para [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ao implementar interfaces. Cada elemento deve implementar pelo menos uma das interfaces listadas na primeira tabela na próxima seção. Além disso, se o elemento dá suporte a um ou mais padrões de controle, ele deve implementar a interface adequada para cada padrão de controle.  
  
 Seu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] projeto provedor deve referenciar os seguintes assemblies:  
  
-   UIAutomationProviders.dll  
  
-   UIAutomationTypes.dll  
  
-   WindowsBase.dll  

<a name="Provider_Interfaces"></a>   
### <a name="provider-interfaces"></a>Interfaces de provedor  
 Cada [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] provedor deve implementar uma das seguintes interfaces.  
  
|Interface|Descrição|  
|---------------|-----------------|  
|<xref:System.Windows.Automation.Provider.IRawElementProviderSimple>|Fornece funcionalidade para um controle simples hospedado em uma janela, incluindo suporte para padrões de controle e propriedades.|  
|<xref:System.Windows.Automation.Provider.IRawElementProviderFragment>|Herda de <xref:System.Windows.Automation.Provider.IRawElementProviderSimple>. Adiciona a funcionalidade para um elemento em um controle complexo, incluindo navegação dentro do fragmento, definindo o foco e retornar o retângulo delimitador do elemento.|  
|<xref:System.Windows.Automation.Provider.IRawElementProviderFragmentRoot>|Herda de <xref:System.Windows.Automation.Provider.IRawElementProviderFragment>. Adiciona a funcionalidade para o elemento raiz em um controle complexo, incluindo localizar um elemento filho nas coordenadas especificadas e definindo o estado de foco para todo o controle.|  
  
 As seguintes interfaces oferecem funcionalidade adicional, mas não são necessárias a serem implementados.  
  
|Interface|Descrição|  
|---------------|-----------------|  
|<xref:System.Windows.Automation.Provider.IRawElementProviderAdviseEvents>|Permite que o provedor controlar solicitações para eventos.|  
|<xref:System.Windows.Automation.Provider.IRawElementProviderHwndOverride>|Permite o reposicionamento de elementos baseados em janela dentro do [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] árvore de um fragmento.|  
  
 Todas as outras interfaces no <xref:System.Windows.Automation.Provider> namespace são para suporte ao padrão de controle.  
  
<a name="Requirements_for_Non_WPF_Providers"></a>   
### <a name="requirements-for-non-wpf-providers"></a>Requisitos para provedores não-WPF  
 Para se comunicar com [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], seu controle deve implementar as seguintes áreas principais de funcionalidade:  
  
|Funcionalidade|Implementação|  
|-------------------|--------------------|  
|Exponha a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|Em resposta a uma mensagem WM_GETOBJECT enviada para a janela de controle, retornar o objeto que implementa <xref:System.Windows.Automation.Provider.IRawElementProviderSimple> (ou uma interface derivada). Para fragmentos, isso deve ser o provedor para a raiz do fragmento.|  
|Fornecer valores de propriedade|Implemente <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPropertyValue%2A> para fornecer ou substituir valores.|  
|Habilitar o cliente para interagir com o controle|Implementar interfaces que oferecem suporte a padrões de controle, como <xref:System.Windows.Automation.Provider.IInvokeProvider>. Retornar esses provedores de padrão em sua implementação de <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A>.|  
|Gerar eventos|Chame um dos métodos estáticos de <xref:System.Windows.Automation.Provider.AutomationInteropProvider> para acionar um evento que um cliente pode escutar.|  
|Habilitar a navegação e foco dentro de um fragmento|Implemente <xref:System.Windows.Automation.Provider.IRawElementProviderFragment> para cada elemento dentro do fragmento. (Necessário para elementos que não fazem parte de um fragmento.)|  
|Habilite foco e localização de um elemento filho em um fragmento.|Implementar <xref:System.Windows.Automation.Provider.IRawElementProviderFragmentRoot>. (Não necessariamente para elementos que são não raízes de fragmentos.)|  
  
<a name="Property_Values_in_Non_WPF_Providers"></a>   
### <a name="property-values-in-non-wpf-providers"></a>Valores de propriedade em provedores não-WPF  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] provedores para controles personalizados devem oferecer suporte a determinadas propriedades que podem ser usadas pelo sistema de automação, bem como por aplicativos cliente. Para elementos que são hospedados em janelas (HWNDs) [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] pode recuperar algumas propriedades do provedor de janela padrão, mas deve obter outras do provedor personalizado.  
  
 Provedores de controles baseados em HWND geralmente não precisa fornecer as seguintes propriedades (identificadas pelos valores de campo):  
  
-   <xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>  
  
-   <xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>  
  
-   <xref:System.Windows.Automation.AutomationElementIdentifiers.ProcessIdProperty>  
  
-   <xref:System.Windows.Automation.AutomationElementIdentifiers.ClassNameProperty>  
  
-   <xref:System.Windows.Automation.AutomationElementIdentifiers.HasKeyboardFocusProperty>  
  
-   <xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>  
  
-   <xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>  
  
-   <xref:System.Windows.Automation.AutomationElementIdentifiers.IsPasswordProperty>  
  
-   <xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>  
  
-   <xref:System.Windows.Automation.AutomationElementIdentifiers.RuntimeIdProperty>  
  
> [!NOTE]
>  O <xref:System.Windows.Automation.AutomationElementIdentifiers.RuntimeIdProperty> de um elemento simples ou fragmento raiz hospedado em uma janela é obtido da janela; no entanto, os elementos de fragmento abaixo da raiz (por exemplo, itens de lista em uma caixa de listagem) devem fornecer seus próprios identificadores. Para obter mais informações, consulte <xref:System.Windows.Automation.Provider.IRawElementProviderFragment.GetRuntimeId%2A>.  
>   
>  O <xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty> deve ser retornado para provedores hospedados em um [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] controle. Nesse caso, o provedor de janela padrão talvez não é possível recuperar o valor correto.  
>   
>  O <xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty> é geralmente fornecido pelo provedor de host. Por exemplo, se um controle personalizado é derivado de <xref:System.Windows.Forms.Control>, o nome é derivado do `Text` propriedade do controle.  
  
 Por exemplo de código, consulte [retornar propriedades de um provedor de automação de interface do usuário](../../../docs/framework/ui-automation/return-properties-from-a-ui-automation-provider.md).  
  
<a name="Events_in_Non_WPF_Providers"></a>   
### <a name="events-in-non-wpf-providers"></a>Eventos em provedores não-WPF  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] provedores devem disparar eventos para notificar aplicativos de cliente de alterações no estado da interface do usuário. Os métodos a seguir são usados para gerar eventos.  
  
|Método|Descrição|  
|------------|-----------------|  
|<xref:System.Windows.Automation.Provider.AutomationInteropProvider.RaiseAutomationEvent%2A>|Gera vários eventos, incluindo eventos disparados por padrões de controle.|  
|<xref:System.Windows.Automation.Provider.AutomationInteropProvider.RaiseAutomationPropertyChangedEvent%2A>|Gera um evento quando uma propriedade [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] foi alterada.|  
|<xref:System.Windows.Automation.Provider.AutomationInteropProvider.RaiseStructureChangedEvent%2A>|Gera um evento quando a estrutura do [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] árvore tiver sido alterado; por exemplo, pela remoção ou adição de um elemento.|  
  
 A finalidade de um evento é notificar o cliente de algo que ocorrem na [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)], se a atividade é disparada pelo [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] próprio sistema. Por exemplo, o evento identificado por <xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent> deve ser acionado sempre que o controle é invocado, através de entrada direta do usuário ou aplicativo que chama o cliente <xref:System.Windows.Automation.InvokePattern.Invoke%2A>.  
  
 Para otimizar o desempenho, um provedor seletivamente pode gerar eventos, ou não gerar nenhuma eventos em todos os se nenhum aplicativo cliente está registrado para recebê-los. Os métodos a seguir são usados para otimização.  
  
|Método|Descrição|  
|------------|-----------------|  
|<xref:System.Windows.Automation.Provider.AutomationInteropProvider.ClientsAreListening%2A>|Essa propriedade estática que especifica se todos os aplicativos cliente se inscreveu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] eventos.|  
|<xref:System.Windows.Automation.Provider.IRawElementProviderAdviseEvents>|A implementação do provedor dessa interface em uma raiz de fragmento permite que ele ser notificado quando os clientes se registrar e cancelar o registro de manipuladores de eventos para eventos no fragmento.|  
  
<a name="Non_WPF_Provider_Navigation"></a>   
### <a name="non-wpf-provider-navigation"></a>Navegação de provedor de não-WPF  
 Provedores de controles simples, como um botão personalizado hospedado em uma janela (HWND) não precisam oferecer suporte à navegação dentro do [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] árvore. Navegação de e para o elemento é manipulada pelo provedor padrão para a janela de host, que é especificada na implementação de <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.HostRawElementProvider%2A>. Quando você implementa um provedor para um controle personalizado complexo, no entanto, você deve oferecer suporte à navegação entre o nó raiz do fragmento e seus descendentes e entre nós irmãos.  
  
> [!NOTE]
>  Elementos de um fragmento que não seja o raiz devem retornar um `null` referenciar de <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.HostRawElementProvider%2A>, porque eles não são hospedados diretamente em uma janela, e nenhum provedor padrão pode dar suporte a navegação de e -los.  
  
 A estrutura do fragmento é determinada pela sua implementação de <xref:System.Windows.Automation.Provider.IRawElementProviderFragment.Navigate%2A>. Para cada direção possível de cada fragmento, esse método retorna o objeto de provedor para o elemento nessa direção. Não se houver nenhum elemento nessa direção, o método retorna um `null` referência.  
  
 A raiz do fragmento dá suporte à navegação somente aos elementos filho. Por exemplo, uma caixa de listagem retorna o primeiro item na lista quando a direção é <xref:System.Windows.Automation.Provider.NavigateDirection.FirstChild>e o último item quando a direção é <xref:System.Windows.Automation.Provider.NavigateDirection.LastChild>. A raiz do fragmento não oferece suporte a navegação para um pai ou irmãos; Isso é manipulado pelo provedor de janela de host.  
  
 Elementos de um fragmento que não são a raiz devem oferecer suporte à navegação para o pai e todos os irmãos e filhos que eles tenham.  
  
<a name="Non_WPF_Provider_Reparenting"></a>   
### <a name="non-wpf-provider-reparenting"></a>Provedor de não-WPF Reassociando  
 Janelas pop-up são janelas de nível superior, na verdade e, portanto, por padrão, são exibidos no [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] árvore como filhos da área de trabalho. Em muitos casos, no entanto, janelas pop-up são logicamente filhos de um outro controle. Por exemplo, a lista suspensa de uma caixa de combinação é logicamente um filho da caixa de combinação. Da mesma forma, uma janela de menu pop-up é logicamente um filho do menu. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] fornece suporte para reassociar janelas pop-up para que eles apareçam como filhos do controle associado.  
  
 Para reassociar uma janela pop-up:  
  
1. Crie um provedor para a janela pop-up. Isso requer que a classe da janela pop-up é conhecida de antemão.  
  
2. Implemente todas as propriedades e padrões como de costume para essa janela pop-up, como se fosse um controle em si mesmo.  
  
3. Implemente a <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.HostRawElementProvider%2A> propriedade para que ele retorne o valor obtido de <xref:System.Windows.Automation.Provider.AutomationInteropProvider.HostProviderFromHandle%2A>, onde o parâmetro é o identificador de janela da janela pop-up.  
  
4. Implemente <xref:System.Windows.Automation.Provider.IRawElementProviderFragment.Navigate%2A> para a janela pop-up e seu pai para que a navegação é tratada corretamente do pai lógico para os filhos lógicos e entre irmãos.  
  
 Quando [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] encontrar uma janela pop-up, ele reconhece que a navegação está sendo substituída do padrão e pula a janela pop-up quando ele é encontrado como um filho da área de trabalho. Em vez disso, o nó será alcançável através do fragmento.  
  
 Mudança de pai não é adequada para casos em que um controle pode hospedar uma janela de qualquer classe. Por exemplo, um rebar pode hospedar qualquer tipo de HWND suas faixas. Para tratar desses casos, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] suporta uma forma alternativa de realocação de HWND, conforme descrito na próxima seção.  
  
<a name="Non_WPF_Provider_Repositioning"></a>   
### <a name="non-wpf-provider-repositioning"></a>Provedor de não-WPF reposicionamento  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] fragmentos podem conter dois ou mais elementos, cada um contido em uma janela (HWND). Porque cada HWND tem seu próprio provedor padrão que considera o HWND para ser um filho de um HWND que contém, o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] árvore, por padrão, mostrará os HWNDs no fragmento como filhos da janela pai. Na maioria dos casos isso é o comportamento desejável, mas às vezes, ele pode gerar confusão porque ele não coincide com a estrutura lógica do [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)].  
  
 Um bom exemplo disso é um controle rebar. Um rebar contém faixas, por sua vez, cada um deles pode conter um controle baseado em HWND como uma barra de ferramentas, uma caixa de edição ou uma caixa de combinação. O provedor de janela padrão para o HWND de rebar vê o HWNDs do controle de faixa como filhos, e o provedor do rebar vê as faixas como filhos. Porque o provedor do HWND e o provedor de rebar estão trabalhando juntos e combinando seus filhos, as faixas e os controles baseados em HWND aparecem como filhos do rebar. Logicamente, no entanto, apenas as faixas devem aparecer como filhos do rebar, e cada provedor de banda deve ser combinado com o provedor HWND padrão para o controle que ele contém.  
  
 Para fazer isso, o provedor do fragmento raiz para o rebar expõe um conjunto de filhos que representam as faixas. Cada faixa tem um único provedor que pode expor propriedades e padrões. Em sua implementação de <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.HostRawElementProvider%2A>, o provedor de faixa retorna o provedor de janela padrão para o controle HWND, que obtém chamando <xref:System.Windows.Automation.Provider.AutomationInteropProvider.HostProviderFromHandle%2A>, passando o identificador de janela do controle. Por fim, o provedor do fragmento raiz para o rebar implementa o <xref:System.Windows.Automation.Provider.IRawElementProviderHwndOverride> interface e em sua implementação de <xref:System.Windows.Automation.Provider.IRawElementProviderHwndOverride.GetOverrideProviderForHwnd%2A> retorna o provedor de banda apropriado para o controle no HWND especificado.  
  
## <a name="see-also"></a>Consulte também

- [Visão geral dos provedores de automação de interface do usuário](../../../docs/framework/ui-automation/ui-automation-providers-overview.md)
- [Expor um provedor de automação de interface do usuário do lado do servidor](../../../docs/framework/ui-automation/expose-a-server-side-ui-automation-provider.md)
- [Retornar as propriedades de um provedor de automação de interface do usuário](../../../docs/framework/ui-automation/return-properties-from-a-ui-automation-provider.md)
- [Disparar eventos de um provedor de automação de interface do usuário](../../../docs/framework/ui-automation/raise-events-from-a-ui-automation-provider.md)
- [Habilitar navegação de um provedor de fragmento de automação de interface do usuário](../../../docs/framework/ui-automation/enable-navigation-in-a-ui-automation-fragment-provider.md)
- [Suporte a padrões de controle em um provedor de automação de interface do usuário](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)
