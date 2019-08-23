---
title: Visão geral de automação da interface do usuário
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, overview
- user interface, see UI
- accessibility, UI automation
ms.assetid: 65847654-9994-4a9e-b36d-2dd5d998770b
ms.openlocfilehash: af4abf060e9a8606f69a94f27ecd76487a2ff51c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69914598"
---
# <a name="ui-automation-overview"></a>Visão geral de automação da interface do usuário
> [!NOTE]
> Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]recentes sobre [o, consulte API de automação do Windows: Automação](https://go.microsoft.com/fwlink/?LinkID=156746)da interface do usuário.  
  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]é a nova estrutura de acessibilidade [!INCLUDE[TLA#tla_win](../../../includes/tlasharptla-win-md.md)]para, disponível em todos os sistemas operacionais [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]que dão suporte ao.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]fornece acesso programático à [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] maioria dos elementos na área de trabalho, permitindo que os produtos de tecnologia assistencial, como leitores [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] de tela, forneçam informações sobre [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] os usuários finais e manipulem o por meio de entrada padrão. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]também permite que os scripts de teste automatizados [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]interajam com o.  
  
> [!NOTE]
> [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]o não permite a comunicação entre os processos iniciados por usuários diferentes por meio do comando **Executar como** .  
  
 Os aplicativos cliente de automação da interface do usuário podem ser escritos com a garantia de que funcionarão em várias estruturas. O [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] núcleo mascara quaisquer diferenças nas estruturas que se basear em várias partes [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]do. Por exemplo, a `Content` propriedade de um [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] botão, a `Caption` propriedade de um [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] botão e a `ALT` propriedade de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] uma imagem HTML são mapeadas para uma única propriedade, <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name%2A>, na exibição.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]fornece funcionalidade completa no [!INCLUDE[TLA#tla_longhorn](../../../includes/tlasharptla-longhorn-md.md)], [!INCLUDE[TLA#tla_winxp](../../../includes/tlasharptla-winxp-md.md)]e [!INCLUDE[TLA2#tla_winnetsvrfam](../../../includes/tla2sharptla-winnetsvrfam-md.md)].  
  
 Os provedores de automação da interface do usuário oferecem algum suporte para aplicativos cliente do Microsoft Acessibilidade Ativa, por meio de um serviço de ponte interno.  
  
<a name="Providers_and_Clients"></a>   
## <a name="providers-and-clients"></a>Provedores e clientes  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]tem quatro componentes principais, conforme mostrado na tabela a seguir.  
  
|Componente|Descrição|  
|---------------|-----------------|  
|API do provedor (UIAutomationProvider. dll e UIAutomationTypes. dll)|Um conjunto de definições de interface que são implementadas por provedores de automação de interface do usuário [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] , objetos que fornecem informações sobre elementos e respondem a entradas programáticas.|  
|API de cliente (UIAutomationClient. dll e UIAutomationTypes. dll)|Um conjunto de tipos para código gerenciado que permite que aplicativos cliente de automação da interface do usuário [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] obtenham informações sobre o e enviem entrada para controles.|  
|UiAutomationCore. dll|O código subjacente (às vezes chamado [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] de núcleo) que lida com a comunicação entre os provedores e os clientes.|  
|UIAutomationClientsideProviders.dll|Um conjunto de provedores de automação de interface do usuário para controles herdados padrão. ([!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] controles têm suporte nativo para [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].) Esse suporte está automaticamente disponível para aplicativos cliente.|  
  
 Da perspectiva do desenvolvedor do software, há duas maneiras de usar [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]: para criar suporte para controles personalizados (usando a API do provedor) e criar aplicativos que usam o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] núcleo para se comunicar com [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elementos (usando a API do cliente). Dependendo do seu foco, você deve consultar diferentes partes da documentação. Você pode saber mais sobre os conceitos e obter conhecimento prático nas seções a seguir.  
  
|Seção|Assunto|Público-alvo|  
|-------------|--------------------|--------------|  
|[Conceitos básicos de automação da interface do usuário](../../../docs/framework/ui-automation/index.md) (esta seção)|Visões gerais amplas dos conceitos.|Os.|  
|[UI Automation Providers for Managed Code](../../../docs/framework/ui-automation/ui-automation-providers-for-managed-code.md) (Provedores da Automação da Interface do Usuário para código gerenciado)|Visões gerais e tópicos de instruções para ajudá-lo a usar a API do provedor.|Desenvolvedores de controle.|  
|[UI Automation Clients for Managed Code](../../../docs/framework/ui-automation/ui-automation-clients-for-managed-code.md) (Clientes da Automação da Interface do Usuário para código gerenciado)|Visões gerais e tópicos de instruções para ajudá-lo a usar a API do cliente.|Desenvolvedores de aplicativos cliente.|  
|[UI Automation Control Patterns](../../../docs/framework/ui-automation/ui-automation-control-patterns.md) (Padrões de controle da Automação da Interface do Usuário)|Informações sobre como os padrões de controle devem ser implementados pelos provedores e qual funcionalidade está disponível para os clientes.|Os.|  
|[UI Automation Text Pattern](../../../docs/framework/ui-automation/ui-automation-text-pattern.md) (Padrão de texto da Automação da Interface do Usuário)|Informações sobre como o padrão de controle de texto deve ser implementado por provedores e qual funcionalidade está disponível para os clientes.|Os.|  
|[UI Automation Control Types](../../../docs/framework/ui-automation/ui-automation-control-types.md) (Tipos de controle da Automação da Interface do Usuário)|Informações sobre as propriedades e padrões de controle com suporte de diferentes tipos de controle.|Os.|  
  
 A tabela a seguir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] lista os namespaces, as DLLs que os contêm e o público-alvo que os utiliza.  
  
|Namespace|DLLs referenciadas|Público-alvo|  
|---------------|---------------------|--------------|  
|<xref:System.Windows.Automation>|UIAutomationClientUIAutomationTypes|Desenvolvedores de cliente de automação da interface do usuário; usado para localizar <xref:System.Windows.Automation.AutomationElement> objetos, registrar para [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] eventos e trabalhar com [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] padrões de controle.|  
|<xref:System.Windows.Automation.Provider>|UIAutomationProviderUIAutomationTypes|Desenvolvedores de provedores de automação de interface do usuário para [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]estruturas diferentes de.|  
|<xref:System.Windows.Automation.Text>|UIAutomationClientUIAutomationTypes|Desenvolvedores de provedores de automação de interface do usuário para [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]estruturas diferentes de; usados para implementar o padrão de controle TextPattern.|  
|<xref:System.Windows.Automation.Peers>|PresentationFramework|Desenvolvedores de provedores de automação de [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]interface do usuário para o.|  
  
<a name="UI_Automation_Model"></a>   
## <a name="ui-automation-model"></a>Modelo de automação da interface do usuário  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]expõe cada parte do [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] para aplicativos cliente como um. <xref:System.Windows.Automation.AutomationElement> Os elementos estão contidos em uma estrutura de árvore, com a área de trabalho como o elemento raiz. Os clientes podem filtrar a exibição bruta da árvore como uma exibição de controle ou de conteúdo. Os aplicativos também podem criar exibições personalizadas.  
  
 <xref:System.Windows.Automation.AutomationElement>os [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] objetos expõem as propriedades comuns dos elementos que representam. Uma dessas propriedades é o tipo de controle, que define sua aparência e funcionalidade básicas como uma única entidade reconhecível: por exemplo, um botão ou caixa de seleção.  
  
 Além disso, os elementos expõem padrões de controle que fornecem propriedades específicas para seus tipos de controle. Os padrões de controle também expõem métodos que permitem que os clientes obtenham mais informações sobre o elemento e forneçam entrada.  
  
> [!NOTE]
> Não há uma correspondência um-para-um entre tipos de controle e padrões de controle. Um padrão de controle pode ser suportado por vários tipos de controle, e um controle pode dar suporte a vários padrões de controle, cada um dos quais expõe diferentes aspectos de seu comportamento. Por exemplo, uma caixa de combinação tem pelo menos dois padrões de controle: um que representa sua capacidade de expandir e recolher e outro que representa o mecanismo de seleção. Para obter informações específicas, consulte [tipos de controle de automação da interface do usuário](../../../docs/framework/ui-automation/ui-automation-control-types.md).  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]também fornece informações para aplicativos cliente por meio de eventos. Ao [!INCLUDE[TLA2#tla_winevents](../../../includes/tla2sharptla-winevents-md.md)]contrário [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] de, os eventos não são baseados em um mecanismo de difusão. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Os clientes se registram para notificações de eventos específicas e [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] podem solicitar que propriedades específicas e informações de padrão de controle sejam passadas para seus manipuladores de eventos. Além disso, um [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] evento contém uma referência ao elemento que o gerou. Os provedores podem melhorar o desempenho gerando eventos de forma seletiva, dependendo se algum cliente está ouvindo.  
  
## <a name="see-also"></a>Consulte também

- [Visão geral de árvore de automação de interface do usuário](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [Visão geral de padrões de controle de automação da interface do usuário](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [Visão geral de propriedades de automação de interface do usuário](../../../docs/framework/ui-automation/ui-automation-properties-overview.md)
- [Visão geral sobre eventos de automação de interface do usuário](../../../docs/framework/ui-automation/ui-automation-events-overview.md)
- [Visão geral de segurança de automação de interface do usuário](../../../docs/framework/ui-automation/ui-automation-security-overview.md)
