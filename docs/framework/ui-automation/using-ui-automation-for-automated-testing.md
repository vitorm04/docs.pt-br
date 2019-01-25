---
title: Usando automação de interface do usuário para testes automatizados
ms.date: 03/30/2017
helpviewer_keywords:
- automated testing
- testing, UI Automation
- UI Automation, automated testing
ms.assetid: 3a0435c0-a791-4ad7-ba92-a4c1d1231fde
author: Xansky
ms.author: mhopkins
ms.openlocfilehash: 023c85591ba484e0b8f97a8ef71a4f65a2f05ffb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54691782"
---
# <a name="using-ui-automation-for-automated-testing"></a>Usando automação de interface do usuário para testes automatizados
> [!NOTE]
>  Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>. Para obter as informações mais recentes sobre [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: Automação de interface do usuário](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Esta visão geral descreve como [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] pode ser útil como uma estrutura para o acesso programático em cenários de teste automatizado.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Fornece um modelo de objeto unificada que permite que todos os [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] estruturas para expor funcionalidades complexas e avançadas de uma maneira acessível e facilmente automatizada.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] foi desenvolvido como um sucessor [!INCLUDE[TLA#tla_aa](../../../includes/tlasharptla-aa-md.md)]. [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] uma estrutura existente foi projetada para fornecer uma solução para tornar acessíveis os controles e aplicativos. [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] não foi projetado com a automação de teste em mente, mesmo que ela evoluiu e essa função devido aos requisitos de acessibilidade e automação muito semelhantes. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], além de fornecer soluções mais refinadas para acessibilidade, também projetado especificamente para fornecer funcionalidades robustas para testes automatizados. Por exemplo, [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] se baseia em uma única interface para expor informações sobre a interface do usuário e para coletar as informações necessárias para produtos AT; [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] separa os dois modelos.  
  
 Um provedor e do cliente são necessários para implementar [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] para que possa ser útil como uma ferramenta de teste automatizado. Provedores de automação de interface do usuário são aplicativos como o Microsoft Word, Excel, e outros aplicativos de terceiros ou controles com base no [!INCLUDE[TLA#tla_win](../../../includes/tlasharptla-win-md.md)] sistema operacional. Clientes de automação de interface do usuário incluem aplicativos de tecnologia assistencial e scripts de teste automatizados.  
  
> [!NOTE]
>  A intenção desta visão geral é apresentar os recursos novos e aprimorados para testes automatizados de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]. Esta visão geral não se destina a fornecer informações sobre acessibilidade recursos e não abordará acessibilidade diferente de onde for necessário.  
  
<a name="Using_UI_Automation_During_Development"></a>   
## <a name="ui-automation-in-a-provider"></a>Automação de interface do usuário em um provedor  
 Para um [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] ser automatizada, um desenvolvedor de um aplicativo ou controle deve examinar o que podem executar ações de um usuário final no [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] usando a interação do teclado e mouse padrão do objeto.  
  
 Uma vez principais ações tiveram sido identificadas, correspondente [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] padrões de controle (ou seja, os padrões de controle que espelham a funcionalidade e o comportamento do [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elemento) deve ser implementado no controle. Por exemplo, a interação do usuário com um controle de caixa de combinação (como a caixa de diálogo Executar) normalmente envolve expandir e recolher a caixa de combinação para ocultar ou exibir uma lista de itens, selecionando um item da lista ou adicionando um novo valor por meio de entrada do teclado.  
  
> [!NOTE]
>  Com outros modelos de acessibilidade, os desenvolvedores devem coletar informações diretamente de outros controles, menus ou botões individuais. Infelizmente, cada tipo de controle é fornecido em dezenas de pequenas variações. Em outras palavras, mesmo que dez variações de um botão de ação podem todos funcionam da mesma forma e realizam a mesma função, elas devem todas ser tratadas como controles exclusivos. Não há nenhuma maneira de saber que esses controles são funcionalmente equivalentes. Padrões de controle foram desenvolvidos para representar esses comportamentos comuns de controle. Para obter mais informações, consulte [visão geral de padrões de controle de automação da interface do usuário](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).  
  
<a name="Implementing_UI_Automation"></a>   
### <a name="implementing-ui-automation"></a>Implementando a automação de interface do usuário  
 Como mencionado anteriormente, sem o modelo unificado fornecido pelo [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], ferramentas de teste e os desenvolvedores precisam conhecer informações específicas da estrutura para expor propriedades e os comportamentos dos controles no framework. Como pode haver vários diferentes estruturas de interface do usuário presentes em qualquer momento em que os sistemas operacionais Windows, incluindo [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)], [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)], e o Windows Presentation Foundation (WPF), ele pode ser uma tarefa árdua para testar vários aplicativos com controles que parecem semelhantes. Por exemplo, a tabela a seguir descreve os nomes de propriedade específicas do framework necessários para recuperar o nome (ou texto) associado a um controle de botão e mostra a única equivalente [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] propriedade.  
  
|Tipo de controle de automação de interface do usuário|Estrutura de interface do usuário|Propriedade específica do Framework|Propriedade de automação de interface do usuário|  
|--------------------------------|------------------|---------------------------------|----------------------------|  
|Botão|Windows Presentation Foundation|Conteúdo|NameProperty|  
|Botão|Win32|Legenda|NameProperty|  
|Image|HTML|alt|NameProperty|  
  
 Provedores de automação de interface do usuário serão responsáveis por mapear as propriedades específicas da estrutura de seus controles para o equivalente [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] propriedades.  
  
 Informações sobre como implementar [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] em um provedor pode ser encontrado em [provedores de automação de interface do usuário para código gerenciado](../../../docs/framework/ui-automation/ui-automation-providers-for-managed-code.md). Informações sobre como implementar padrões de controle estão disponíveis em [UI Automation Control Patterns](../../../docs/framework/ui-automation/ui-automation-control-patterns.md) e [UI Automation Text Pattern](../../../docs/framework/ui-automation/ui-automation-text-pattern.md).  
  
<a name="Testing_with_UI_Automation"></a>   
## <a name="ui-automation-in-a-client"></a>Automação de interface do usuário em um cliente  
 O objetivo de muitos cenários e ferramentas de teste automatizado é a manipulação consistente e reproduzível da interface do usuário. Isso pode envolver a controles específicos até a gravação e reprodução de scripts de teste que iterar por meio de uma série de ações genéricas em um grupo de controles de teste de unidade.  
  
 Uma complicação que surge de aplicativos automatizados é a dificuldade de sincronizar um teste com um destino dinâmico. Por exemplo, um controle de caixa de listagem, por exemplo, um contido no Gerenciador de tarefas do Windows, que exibe uma lista de aplicativos em execução no momento. Como os itens na caixa de listagem são atualizados dinamicamente fora do controle do aplicativo de teste, a tentativa de repetir a seleção de um item específico na caixa de listagem com qualquer consistência é impossível. Problemas semelhantes também podem ocorrer durante a tentativa de repetir as alterações de foco simples em um [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] que está fora do controle do aplicativo de teste.  
  
<a name="Programmatic_Access"></a>   
### <a name="programmatic-access"></a>Acesso programático  
 Acesso programático fornece a capacidade de imitar, por meio de código, qualquer interação e experiência expostos por tradicional mouse e teclado de entrada. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] permite acesso programático por meio de cinco componentes:  
  
-   O [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] facilita a navegação através da estrutura de árvore a [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]. A árvore é criada da coleção de HWNDs. Para obter mais informações, consulte [visão geral da árvore de automação de interface do usuário](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
  
-   Elementos de automação são componentes individuais no [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]. Eles geralmente podem ser mais granulares do que um hWnd. Para obter mais informações, consulte [visão geral de tipos de controle de automação da interface do usuário](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md).  
  
-   Propriedades de automação fornecem informações específicas sobre [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elementos. Para obter mais informações, consulte [visão geral das propriedades de automação de interface do usuário](../../../docs/framework/ui-automation/ui-automation-properties-overview.md).  
  
-   Padrões de controle definem um aspecto específico da funcionalidade de um controle; ele podem consistir de método, propriedade, evento e informações de estrutura. Para obter mais informações, consulte [visão geral de padrões de controle de automação da interface do usuário](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).  
  
-   Eventos de automação fornecem informações e notificações de eventos. Para obter mais informações, consulte [visão geral de eventos de automação de interface do usuário](../../../docs/framework/ui-automation/ui-automation-events-overview.md).  
  
<a name="Key_properties_critical_to_test_automation"></a>   
### <a name="key-properties-for-test-automation"></a>Propriedades de chave para a automação de teste  
 A capacidade de identificar com exclusividade e posteriormente localizar qualquer controle dentro de [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] fornece a base para aplicativos de testes automatizados operar em que [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]. Há vários [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] propriedades usadas por clientes e provedores que ajudam a isso.  
  
#### <a name="automationid"></a>AutomationID  
 Identifica exclusivamente um elemento de automação de seus irmãos. <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> não é localizado, diferentemente de uma propriedade, como <xref:System.Windows.Automation.AutomationElement.NameProperty> que normalmente é localizada se um produto é fornecido em vários idiomas. Ver [usar a propriedade AutomationID](../../../docs/framework/ui-automation/use-the-automationid-property.md).  
  
> [!NOTE]
>  <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> não garante uma identidade exclusiva em toda a árvore de automação. Por exemplo, um aplicativo pode conter um controle de menu com vários itens de menu de nível superior que, por sua vez, têm vários itens de menu filho. Esses itens de menu secundária podem ser identificados por um esquema genérico, como "Item1, Item 2, Item3, etc.", permitindo identificadores duplicados para os filhos entre itens de menu de nível superior.  
  
#### <a name="controltype"></a>ControlType  
 Identifica o tipo de controle representado por um elemento de automação. Informações significativas podem ser inferidas de dados de conhecimento do tipo de controle. Ver [visão geral de tipos de controle de automação de interface do usuário](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md).  
  
#### <a name="nameproperty"></a>NameProperty  
 Isso é uma cadeia de caracteres de texto que identifica ou explica um controle. <xref:System.Windows.Automation.AutomationElement.NameProperty> deve ser usada com cuidado, pois ele pode ser localizado. Ver [visão geral das propriedades de automação de interface do usuário](../../../docs/framework/ui-automation/ui-automation-properties-overview.md).  
  
<a name="Steps_Required_To_Automate_the_UI_in_a_Test_Application"></a>   
### <a name="implementing-ui-automation-in-a-test-application"></a>Implementação de automação de interface do usuário em um aplicativo de teste  
  
|||  
|-|-|  
|Adicione as referências de automação de interface do usuário.|O [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] dll do necessário para clientes de automação de interface do usuário estão listados aqui.<br /><br /> -UIAutomationClient. dll fornece acesso para o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] APIs do lado do cliente.<br />-UIAutomationClientSideProvider. dll fornece a capacidade de automatizar [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] controles. Ver [suporte de automação de interface do usuário para controles padrão](../../../docs/framework/ui-automation/ui-automation-support-for-standard-controls.md).<br />-UIAutomationTypes. dll fornece acesso para os tipos específicos definidos em [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].|  
|Adicionar o <xref:System.Windows.Automation> namespace.|Este namespace contém tudo o que os clientes de automação de interface do usuário precisam usar os recursos do [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , exceto a manipulação de texto.|  
|Adicionar o <xref:System.Windows.Automation.Text> namespace.|Este namespace contém tudo o que uma necessidade dos clientes de automação de interface do usuário para usar os recursos do [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] manipulação de texto.|  
|Localizar os controles de interesse|Scripts de teste automatizados localizam os elementos de automação de interface do usuário que representam os controles de interesse dentro da árvore de automação.<br /><br /> Há várias maneiras de obter elementos de automação de interface do usuário com o código.<br /><br /> -Consulte o [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] usando um <xref:System.Windows.Automation.Condition> instrução. Normalmente, é onde a neutralidade de idioma <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> é usado. **Observação:**  Uma <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> pode ser obtida usando uma ferramenta como Inspect.exe é capaz de relacionar a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] propriedades de um controle. <br /><br /> – Use o <xref:System.Windows.Automation.TreeWalker> classe para percorrer toda a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] árvore ou um subconjunto dele.<br />-Rastreie o foco.<br />-Use o hWnd do controle.<br />-Use o local da tela, como o local do cursor do mouse.<br /><br /> Consulte [obtendo elementos de automação de interface do usuário](../../../docs/framework/ui-automation/obtaining-ui-automation-elements.md)|  
|Obter padrões de controle|Padrões de controle expõem comportamentos comuns para controles funcionalmente semelhantes.<br /><br /> Depois de localizar os controles que exigem teste, scripts de teste automatizados obter os padrões de controle de interesse de um desses elementos de automação de interface do usuário. Por exemplo, o <xref:System.Windows.Automation.InvokePattern> padrão de controle para a funcionalidade típica de botão ou o <xref:System.Windows.Automation.WindowPattern> padrão de controle para a funcionalidade de janela.<br /><br /> Ver [visão geral de padrões de controle de automação de interface do usuário](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).|  
|Automatizar a interface do usuário|Scripts de teste automatizados podem agora controlar qualquer [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] de interesse de um [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] framework usando as informações e funcionalidade exposta pelo [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] padrões de controle.|  
  
<a name="Supporting_tools"></a>   
## <a name="related-tools-and-technologies"></a>Ferramentas e tecnologias relacionadas  
 Há uma série de ferramentas relacionadas e tecnologias que oferecem suporte a testes automatizados com [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].  
  
-   Inspect.exe é um [!INCLUDE[TLA#tla_gui](../../../includes/tlasharptla-gui-md.md)] aplicativo que pode ser usado para reunir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] informações para o cliente e o provedor de desenvolvimento e depuração. Inspect.exe está incluído no [!INCLUDE[TLA#tla_winfxsdk](../../../includes/tlasharptla-winfxsdk-md.md)].  
  
-   Expõe o MSAABridge [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] informações para [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] clientes. O principal objetivo da ponte [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] à [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] é permitir que o existente [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] os clientes a capacidade de interagir com qualquer estrutura que implementou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].  
  
<a name="Security"></a>   
## <a name="security"></a>Segurança  
 Para obter informações de segurança, consulte [visão geral de segurança de automação de interface do usuário](../../../docs/framework/ui-automation/ui-automation-security-overview.md).  
  
## <a name="see-also"></a>Consulte também
- [UI Automation Fundamentals](../../../docs/framework/ui-automation/index.md) (Fundamentos da Automação da Interface do Usuário)
