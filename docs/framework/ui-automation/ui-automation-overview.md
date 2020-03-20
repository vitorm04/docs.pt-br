---
title: Visão geral de automação da interface do usuário
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, overview
- user interface, see UI
- accessibility, UI automation
ms.assetid: 65847654-9994-4a9e-b36d-2dd5d998770b
ms.openlocfilehash: 6f938302967e1b519105769717d326e5042a7bce
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179919"
---
# <a name="ui-automation-overview"></a>Visão geral de automação da interface do usuário
> [!NOTE]
> Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32) (API de Automação do Windows: Automação da Interface do Usuário).  
  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]é a nova estrutura de acessibilidade do Microsoft Windows, disponível em todos os sistemas operacionais que suportam [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)].  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]fornece acesso programático [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] à maioria dos elementos na área de trabalho, permitindo [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] que produtos de [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] tecnologia assistiva, como leitores de tela, forneçam informações sobre os usuários finais e manipulem os por meios diferentes da entrada padrão. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]também permite que scripts de [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]teste automatizados interajam com o .  
  
> [!NOTE]
> [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]não permite a comunicação entre processos iniciados por diferentes usuários através do **Comando Executar como** comando.  
  
 Os aplicativos clientes de automação de interface do usuário podem ser escritos com a garantia de que trabalharão em múltiplas estruturas. O [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] núcleo mascara quaisquer diferenças nos quadros que [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]estão por trás de várias peças de . Por exemplo, `Content` a [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] propriedade de `Caption` um botão, a propriedade `ALT` de um botão Win32 e a <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name%2A>propriedade de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] uma imagem HTML são todas mapeadas para uma única propriedade, na exibição.  
  
A UI Automation oferece funcionalidade completa em sistemas operacionais Windows suportados executando o .NET Framework (veja os requisitos do [sistema .NET Framework](../get-started/system-requirements.md) ou versões do .NET Core a partir do .NET Core 3.0.  
  
 Os provedores de automação de interface do usuário oferecem algum suporte para aplicativos clientes microsoft active accessibility através de um serviço de ponte incorporado.  
  
<a name="Providers_and_Clients"></a>
## <a name="providers-and-clients"></a>Provedores e Clientes  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]tem quatro componentes principais, como mostrado na tabela a seguir.  
  
|Componente|Descrição|  
|---------------|-----------------|  
|API do provedor (UIAutomationProvider.dll e UIAutomationTypes.dll)|Um conjunto de definições de interface que são implementadas [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] por provedores de automação de interface, objetos que fornecem informações sobre elementos e respondem à entrada programática.|  
|API do cliente (UIAutomationClient.dll e UIAutomationTypes.dll)|Um conjunto de tipos para código gerenciado que permite que os [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] aplicativos clientes de automação de interface do usuário obtenham informações sobre o e enviem entradas para controles.|  
|UiAutomationCore.dll|O código subjacente (às [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vezes chamado de núcleo) que lida com a comunicação entre provedores e clientes.|  
|UIAutomationClientsideProviders.dll|Um conjunto de provedores de automação de iu para controles legados padrão. (os[!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] controles têm [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]suporte nativo para .) Esse suporte está disponível automaticamente para aplicativos do cliente.|  
  
 Do ponto de vista do desenvolvedor de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]software, existem duas maneiras de usar: criar suporte para [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] controles personalizados [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] (usando a API do provedor) e criar aplicativos que usam o núcleo para se comunicar com elementos (usando a API do cliente). Dependendo do seu foco, você deve consultar diferentes partes da documentação. Você pode aprender mais sobre os conceitos e obter conhecimento prático de como fazer nas seguintes seções.  
  
|Seção|Assunto|Público|  
|-------------|--------------------|--------------|  
|[Fundamentos de Automação de UI](index.md) (esta seção)|Visão geral dos conceitos.|Todos.|  
|[Provedores de automação de interface de usuário para Código Gerenciado](ui-automation-providers-for-managed-code.md)|Visões gerais e tópicos de como ajudá-lo a usar a API do provedor.|Controle os desenvolvedores.|  
|[Clientes de Automação de Interface de Usuário para Código Gerenciado](ui-automation-clients-for-managed-code.md)|Visões gerais e tópicos de como ajudá-lo a usar a API do cliente.|Desenvolvedores de aplicativos clientes.|  
|[Padrões de controle de automação da interface do usuário](ui-automation-control-patterns.md)|Informações sobre como os padrões de controle devem ser implementados pelos provedores e qual funcionalidade está disponível para os clientes.|Todos.|  
|[Padrão de texto de automação da interface do usuário](ui-automation-text-pattern.md)|Informações sobre como o padrão de controle de texto deve ser implementado pelos provedores e qual funcionalidade está disponível para os clientes.|Todos.|  
|[Tipos de controle de automação de interface do usuário](ui-automation-control-types.md)|Informações sobre as propriedades e padrões de controle suportados por diferentes tipos de controle.|Todos.|  
  
 A tabela [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] a seguir lista os namespaces, os DLLs que os contêm e o público que os usa.  
  
|Namespace|DLLs referenciados|Público|  
|---------------|---------------------|--------------|  
|<xref:System.Windows.Automation>|UIAutomationClientUITipos de automação|Desenvolvedores clientes de automação de ui; usado para <xref:System.Windows.Automation.AutomationElement> encontrar objetos, registrar [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] eventos e trabalhar com padrões de controle.|  
|<xref:System.Windows.Automation.Provider>|Tipos de automação uiAutomationproviderUITipos de automação|Desenvolvedores de provedores de automação [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]de iu de iu para outras estruturas que não .|  
|<xref:System.Windows.Automation.Text>|UIAutomationClientUITipos de automação|Desenvolvedores de provedores de automação [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]de iu de iu para outras estruturas que não; usado para implementar o padrão de controle TextPattern.|  
|<xref:System.Windows.Automation.Peers>|PresentationFramework|Desenvolvedores de provedores [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]de automação de iu de iu para .|  
  
<a name="UI_Automation_Model"></a>
## <a name="ui-automation-model"></a>Modelo de automação de UI  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]expõe cada pedaço [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] dos aplicativos ao <xref:System.Windows.Automation.AutomationElement>cliente como um . Os elementos estão contidos em uma estrutura de árvore, com a área de trabalho como elemento raiz. Os clientes podem filtrar a visão bruta da árvore como uma exibição de controle ou uma exibição de conteúdo. Os aplicativos também podem criar visualizações personalizadas.  
  
 <xref:System.Windows.Automation.AutomationElement>objetos expõem [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] propriedades comuns dos elementos que representam. Uma dessas propriedades é o tipo de controle, que define sua aparência básica e funcionalidade como uma única entidade reconhecível: por exemplo, um botão ou caixa de seleção.  
  
 Além disso, os elementos expõem padrões de controle que fornecem propriedades específicas de seus tipos de controle. Padrões de controle também expõem métodos que permitem aos clientes obter mais informações sobre o elemento e fornecer informações.  
  
> [!NOTE]
> Não há uma correspondência um-para-um entre tipos de controle e padrões de controle. Um padrão de controle pode ser suportado por vários tipos de controle, e um controle pode suportar múltiplos padrões de controle, cada um dos quais expõe diferentes aspectos de seu comportamento. Por exemplo, uma caixa de combinação tem pelo menos dois padrões de controle: um que representa sua capacidade de expansão e colapso, e outro que representa o mecanismo de seleção. Para obter detalhes, consulte [Tipos de Controle de Automação de ICarros](ui-automation-control-types.md).  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]também fornece informações para aplicativos de clientes através de eventos. Ao contrário [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] do WinEvents, os eventos não são baseados em um mecanismo de transmissão. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]os clientes se cadastram [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] para notificações específicas de eventos e podem solicitar que propriedades específicas e informações de padrão de controle sejam passadas para seus manipuladores de eventos. Além disso, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] um evento contém uma referência ao elemento que o levantou. Os provedores podem melhorar o desempenho levantando eventos seletivamente, dependendo se algum cliente está ouvindo.  
  
## <a name="see-also"></a>Confira também

- [Visão geral da árvore de automação de interface do usuário](ui-automation-tree-overview.md)
- [Visão Geral de Padrões de Controle de Automação de Interface de Usuário](ui-automation-control-patterns-overview.md)
- [Visão geral das propriedades de automação da interface do usuário](ui-automation-properties-overview.md)
- [Visão geral sobre eventos de automação de interface do usuário](ui-automation-events-overview.md)
- [Visão geral de segurança da automação de interface do usuário](ui-automation-security-overview.md)
