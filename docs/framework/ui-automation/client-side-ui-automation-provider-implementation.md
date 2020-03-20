---
title: Implementação de Provedor de Automação de Interface de Usuário do Lado do Cliente
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, client-side provider implementation
- client-side UI Automation provider, implementation
- provider implementation, UI Automation
ms.assetid: 3584c0a1-9cd0-4968-8b63-b06390890ef6
ms.openlocfilehash: 50d7921f1c63580248b562864f9c1f398d41c9bc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180253"
---
# <a name="client-side-ui-automation-provider-implementation"></a>Implementação de Provedor de Automação de Interface de Usuário do Lado do Cliente
> [!NOTE]
> Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32) (API de Automação do Windows: Automação da Interface do Usuário).  
  
 Várias [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] estruturas diferentes estão em uso nos sistemas operacionais da [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]Microsoft, incluindo Win32, Windows Forms e . [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]expõe informações sobre elementos de Interface do Usuário aos clientes. No [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] entanto, não se conscientiza dos diferentes tipos de controles existentes nesses quadros e das técnicas necessárias para extrair informações deles. Em vez disso, deixa essa tarefa para objetos chamados provedores. Um provedor extrai informações de um controle [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]específico e entrega essas informações para , que então as apresenta ao cliente de forma consistente.  
  
 Os provedores podem existir no lado do servidor ou no lado do cliente. Um provedor do lado do servidor é implementado pelo próprio controle. [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]elementos implementam provedores, assim como [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] quaisquer controles de terceiros escritos com em mente.  
  
 No entanto, controles mais antigos, como os do [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Win32 e do Windows Forms, não suportam diretamente . Esses controles são atendidos em vez de provedores que existem no processo do cliente e obtêm informações sobre controles usando comunicação entre processos; por exemplo, monitorando mensagens do Windows de e para os controles. Esses provedores do lado do cliente às vezes são chamados de proxies.  
  
 O Windows Vista fornece aos provedores os controles padrão Win32 e Windows Forms. Além disso, um provedor [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] de recuo dá suporte parcial a qualquer controle que não seja atendido por outro provedor ou proxy do lado do servidor, mas que tenha uma implementação de Acessibilidade Ativa do Microsoft. Todos esses provedores são carregados automaticamente e disponíveis para aplicativos clientes.  
  
 Para obter mais informações sobre o suporte aos controles Win32 e Windows Forms, consulte [suporte à automação de iu para controles padrão](ui-automation-support-for-standard-controls.md).  
  
 Os aplicativos também podem registrar outros provedores do lado do cliente.  
  
<a name="Distributing_Client-Side_Providers"></a>
## <a name="distributing-client-side-providers"></a>Distribuindo provedores do lado do cliente  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]espera encontrar provedores do lado do cliente em um conjunto de código gerenciado. O namespace nesta assembléia deve ter o mesmo nome da assembléia. Por exemplo, um conjunto chamado ContosoProxies.dll conteria o espaço de nome ContosoProxies. Dentro do namespace, <xref:UIAutomationClientsideProviders.UIAutomationClientSideProviders> crie uma classe. Na implementação do <xref:UIAutomationClientsideProviders.UIAutomationClientSideProviders.ClientSideProviderDescriptionTable> campo estático, <xref:System.Windows.Automation.ClientSideProviderDescription> crie uma matriz de estruturas descrevendo os provedores.  
  
<a name="Registering_and_Configuring_Client-Side_Providers"></a>
## <a name="registering-and-configuring-client-side-providers"></a>Registrando e configurando provedores do lado do cliente  
 Os provedores do lado do cliente em uma biblioteca <xref:System.Windows.Automation.ClientSettings.RegisterClientSideProviderAssembly%2A>de link dinâmico (DLL) são carregados por chamada . Nenhuma ação adicional é necessária por um aplicativo cliente para fazer uso dos provedores.  
  
 Os provedores implementados no próprio código <xref:System.Windows.Automation.ClientSettings.RegisterClientSideProviders%2A>do cliente são registrados usando . Este método toma como argumento <xref:System.Windows.Automation.ClientSideProviderDescription> uma matriz de estruturas, cada uma das quais especifica as seguintes propriedades:  
  
- Uma função de retorno de chamada que cria o objeto do provedor.  
  
- O nome da classe dos controles que o provedor servirá.  
  
- O nome da imagem do aplicativo (geralmente o nome completo do arquivo executável) que o provedor irá servir.  
  
- Sinalizadores que regem como o nome da classe é compatível com as classes de janela encontradas no aplicativo de destino.  
  
 Os dois últimos parâmetros são opcionais. O cliente pode especificar o nome da imagem do aplicativo de destino quando quiser usar diferentes provedores para diferentes aplicativos. Por exemplo, o cliente pode usar um provedor para um controle de exibição de lista Win32 em um aplicativo conhecido que suporta o padrão De exibição múltipla e outro para um controle semelhante em outro aplicativo conhecido que não o faça.  
  
## <a name="see-also"></a>Confira também

- [Criar um Provedor de Automação de Interface de Usuário do Lado do Cliente](create-a-client-side-ui-automation-provider.md)
- [Implementar provedores de automação de interface do usuário em um aplicativo cliente](implement-ui-automation-providers-in-a-client-application.md)
