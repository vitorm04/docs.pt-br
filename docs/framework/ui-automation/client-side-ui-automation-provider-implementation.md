---
title: Implementação de Provedor de Automação de Interface de Usuário do Lado do Cliente
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, client-side provider implementation
- client-side UI Automation provider, implementation
- provider implementation, UI Automation
ms.assetid: 3584c0a1-9cd0-4968-8b63-b06390890ef6
ms.openlocfilehash: e68cf69830aef88f46ff2e288c5aad548db39bdc
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59224450"
---
# <a name="client-side-ui-automation-provider-implementation"></a>Implementação de Provedor de Automação de Interface de Usuário do Lado do Cliente
> [!NOTE]
>  Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: Automação de interface do usuário](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Vários diferente [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] estruturas estão em uso na [!INCLUDE[TLA#tla_ms](../../../includes/tlasharptla-ms-md.md)] sistemas operacionais, inclusive [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)], [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)], e [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]. [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] expõe informações sobre os elementos de interface do usuário para os clientes. No entanto, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] próprio não tem consciência dos diferentes tipos de controles que existem dessas estruturas e as técnicas que são necessários para extrair as informações. Em vez disso, ela deixa essa tarefa para objetos chamados provedores. Um provedor extrai informações de um controle específico e passa essas informações para [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], que então o apresenta ao cliente de maneira consistente.  
  
 Provedores podem existir no lado do servidor ou no lado do cliente. Um provedor do lado do servidor é implementado pelo próprio controle. [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] elementos implementam provedores, assim como podem quaisquer controles de terceiros escritos com [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] em mente.  
  
 No entanto, controles mais antigos, como aqueles no [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] e [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] não diretamente suporte [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]. Esses controles são atendidos em vez disso, por provedores que existem no processo de cliente e obtêm informações sobre controles usando a comunicação entre processos; Por exemplo, ao monitorar as mensagens de e para os controles do windows. Esses provedores do lado do cliente são chamados proxies.  
  
 [!INCLUDE[TLA2#tla_winvista](../../../includes/tla2sharptla-winvista-md.md)] fornece provedores para standard [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] e controles dos Windows Forms. Além disso, um provedor de fallback dá parcial [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] dão suporte a qualquer controle que não é atendido por outro provedor do lado do servidor ou proxy, mas tem um [!INCLUDE[TLA#tla_aa](../../../includes/tlasharptla-aa-md.md)] implementação. Esses provedores são automaticamente carregados e disponível para aplicativos cliente.  
  
 Para obter mais informações sobre o suporte para [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] e controles dos Windows Forms, consulte [suporte de automação da interface do usuário para controles padrão](../../../docs/framework/ui-automation/ui-automation-support-for-standard-controls.md).  
  
 Aplicativos também podem registrar outros provedores do lado do cliente.  
  
<a name="Distributing_Client-Side_Providers"></a>   
## <a name="distributing-client-side-providers"></a>Distribuindo provedores do lado do cliente  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] espera encontrar provedores do lado do cliente em um assembly de código gerenciado. O namespace neste assembly deve ter o mesmo nome que o assembly. Por exemplo, um assembly chamado ContosoProxies.dll conteria o namespace ContosoProxies. Dentro do namespace, crie um <xref:UIAutomationClientsideProviders.UIAutomationClientSideProviders> classe. Na implementação de estática <xref:UIAutomationClientsideProviders.UIAutomationClientSideProviders.ClientSideProviderDescriptionTable> campo, crie uma matriz de <xref:System.Windows.Automation.ClientSideProviderDescription> estruturas que descrevem os provedores.  
  
<a name="Registering_and_Configuring_Client-Side_Providers"></a>   
## <a name="registering-and-configuring-client-side-providers"></a>Registrando e configurando provedores do lado do cliente  
 Provedores do lado do cliente em uma [!INCLUDE[TLA#tla_dll](../../../includes/tlasharptla-dll-md.md)] são carregados chamando <xref:System.Windows.Automation.ClientSettings.RegisterClientSideProviderAssembly%2A>. Nenhuma ação adicional é necessária por um aplicativo cliente para fazer uso dos provedores.  
  
 Provedores implementados no código do cliente são registrados usando <xref:System.Windows.Automation.ClientSettings.RegisterClientSideProviders%2A>. Esse método aceita como um argumento de uma matriz de <xref:System.Windows.Automation.ClientSideProviderDescription> estruturas, cada um deles especifica as propriedades a seguir:  
  
-   Uma função de retorno de chamada que cria o objeto de provedor.  
  
-   O nome da classe dos controles que o provedor servirá.  
  
-   O nome da imagem do aplicativo (normalmente, o nome completo do arquivo executável) que o provedor servirá.  
  
-   Sinalizadores que determinam como o nome da classe é comparado com classes de janela encontradas no aplicativo de destino.  
  
 Os dois últimos parâmetros são opcionais. O cliente pode especificar o nome da imagem do aplicativo de destino quando desejar usar provedores diferentes para diferentes aplicativos. Por exemplo, o cliente pode usar um provedor para um [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] lista de controle de exibição em um aplicativo conhecido que suporta o padrão de exibição de vários e outro para um controle semelhante em outro aplicativo conhecido que não.  
  
## <a name="see-also"></a>Consulte também

- [Criar um Provedor de Automação de Interface de Usuário do Lado do Cliente](../../../docs/framework/ui-automation/create-a-client-side-ui-automation-provider.md)
- [Implementar provedores de automação de interface do usuário em um aplicativo cliente](../../../docs/framework/ui-automation/implement-ui-automation-providers-in-a-client-application.md)
