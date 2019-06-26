---
title: Serviços de hospedagem
ms.date: 03/30/2017
helpviewer_keywords:
- hosting services [WCF]
ms.assetid: 192be927-6be2-4fda-98f0-e513c4881acc
ms.openlocfilehash: db7ca2690fc7b76d3e843a4ed51ef356890ab9eb
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/26/2019
ms.locfileid: "67402406"
---
# <a name="hosting-services"></a>Serviços de hospedagem
Para se tornar ativo, um serviço deve ser hospedado dentro de um ambiente de tempo de execução que cria e controla seu contexto e o tempo de vida. Serviços Windows Communication Foundation (WCF) são projetados para funcionar em qualquer processo do Windows que dá suporte a código gerenciado.  
  
 O WCF fornece um modelo de programação unificado para a criação de aplicativos orientados a serviço. Esse modelo de programação permanece consistente e é independente do ambiente de tempo de execução no qual o serviço é implantado. Na prática, isso significa que o código para seus serviços parece muito mesmo que a opção de hospedagem.  
  
 Eles hospedando as opções variam de em execução dentro de um aplicativo de console para ambientes de servidor, como um Windows serviço em execução dentro de um processo de trabalho gerenciadas pelo Internet Information Services (IIS) ou pelo serviço de ativação de processos para Windows (WAS). Os desenvolvedores escolher o ambiente de hospedagem que satisfaz os requisitos de implantação do serviço. Esses requisitos podem derivar da plataforma na qual o aplicativo é implantado, o transporte em que ele deve enviar e receber mensagens, ou no tipo de reciclagem de processo e outro gerenciamento de processo necessários para garantir a disponibilidade adequada ou em alguns outros requisitos de gerenciamento ou a confiabilidade. A próxima seção fornece informações e diretrizes sobre as opções de hospedagem.  
  
## <a name="hosting-options"></a>Hospedando opções  
  
#### <a name="self-hosting-in-a-managed-application"></a>Hospedagem interna em um aplicativo gerenciado  
 Serviços WCF podem ser hospedados em qualquer aplicativo gerenciado. Isso é a opção mais flexível porque requer que a infra-estrutura mínimos para implantar. Você incorporar o código para o serviço dentro do código de aplicativo gerenciado e, em seguida, cria e abre uma instância da <xref:System.ServiceModel.ServiceHost> para disponibilizar o serviço. Para obter mais informações, confira [Como: Hospedar um serviço WCF em um aplicativo gerenciado](../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md).  
  
 Essa opção permite que os dois cenários comuns: Serviços do WCF em execução dentro de aplicativos de console e aplicativos cliente avançados, como aqueles baseados em Windows Presentation Foundation (WPF) ou Windows Forms (WinForms). Hospedar um serviço WCF dentro de um aplicativo de console é geralmente útil durante a fase de desenvolvimento do aplicativo. Isso os torna fácil de depurar, fácil de obter as informações de rastreamento para descobrir o que está acontecendo dentro do aplicativo e fácil de mover-se copiando-os para novos locais. Essa opção de hospedagem também facilita para os aplicativos cliente avançados, como aplicativos WPF e WinForms, para se comunicar com o mundo exterior. Por exemplo, um cliente de colaboração ponto a ponto que usa o WPF para sua interface do usuário e também hospeda um serviço WCF que permite que outros clientes para conectá-lo e compartilhar informações.  
  
#### <a name="managed-windows-services"></a>Serviços do Windows gerenciado  
 Essa opção de hospedagem consiste em registrar o domínio do aplicativo (AppDomain) que hospeda um serviço do WCF como um serviço gerenciado do Windows (anteriormente conhecido como serviço NT), para que o tempo de vida do processo do serviço é controlado pelo Gerenciador de controle de serviços (SCM) para Serviços do Windows. Como a opção de hospedagem interna, esse tipo de ambiente de hospedagem requer que algum código de hospedagem é escrito como parte do aplicativo. O serviço é implementado como um serviço do Windows e como um serviço WCF, fazendo com que ela herde os <xref:System.ServiceProcess.ServiceBase> de classe, bem como de um WCF de interface de contrato de serviço. O <xref:System.ServiceModel.ServiceHost> , em seguida, é criado e aberto dentro de um substituída <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> método e fechadas dentro um substituído <xref:System.ServiceProcess.ServiceBase.OnStop> método. Uma classe de instalador que herda de <xref:System.Configuration.Install.Installer> também devem ser implementados para permitir que o programa seja instalado como um serviço do Windows pela ferramenta Installutil.exe. Para obter mais informações, confira [Como: Hospedar um serviço WCF em um serviço Windows gerenciado](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-a-managed-windows-service.md). O cenário habilitado pela opção de hospedagem de serviço gerenciado do Windows é que uma longa serviço do WCF hospedado fora do IIS em um ambiente seguro que não está mensagem-ativado. O tempo de vida do serviço é controlado pelo sistema operacional. Essa opção de hospedagem está disponível em todas as versões do Windows.  
  
#### <a name="internet-information-services-iis"></a>Serviços de Informações da Internet (IIS)  
 Opção de hospedagem do IIS é integrado com o ASP.NET e usa os recursos que oferecem essas tecnologias, como desligamento ocioso, reciclagem do processo, o monitoramento de integridade do processo e ativação baseada em mensagem. Sobre o [!INCLUDE[wxp](../../../includes/wxp-md.md)] e [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] sistemas operacionais, isso é a solução preferencial para hospedar aplicativos de serviço Web que devem ser altamente disponível e altamente escalonável. O IIS também oferece a capacidade de gerenciamento integrada que os clientes esperam de um produto de servidor de classe empresarial. Essa opção de hospedando requer que o IIS esteja configurado corretamente, mas não requer que nenhum código de hospedagem seja escrito como parte do aplicativo. Para obter mais informações sobre como configurar o IIS de hospedagem para um serviço WCF, consulte [como: Hospedar um serviço WCF no IIS](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).  
  
 Observe que os serviços hospedados no IIS só podem usar o transporte HTTP. Sua implementação no IIS 5.1 introduziu algumas limitações em [!INCLUDE[wxp](../../../includes/wxp-md.md)]. A ativação baseada em mensagem fornecida para um serviço WCF pelo IIS 5.1 no [!INCLUDE[wxp](../../../includes/wxp-md.md)] bloqueia qualquer outro serviço WCF auto-hospedado no mesmo computador que usa a porta 80 para se comunicar. Serviços WCF podem ser executados no mesmo processo de trabalho/Pool AppDomain/aplicativo como outros aplicativos quando hospedado pelo IIS 6.0 em [!INCLUDE[ws2003](../../../includes/ws2003-md.md)]. Mas como o WCF e o IIS 6.0 usam a pilha HTTP do modo kernel (http. sys), o IIS 6.0 podem compartilhar a porta 80 com outros serviços do WCF auto-hospedado em execução no mesmo computador, ao contrário do IIS 5.1.  
  
#### <a name="windows-process-activation-service-was"></a>Serviço de Ativação de Processos do Windows (WAS)  
 Windows Process Activation Service (WAS) é o novo mecanismo de ativação de processo para o [!INCLUDE[lserver](../../../includes/lserver-md.md)] que também está disponível em [!INCLUDE[wv](../../../includes/wv-md.md)]. Ele retém o modelo de processo do IIS 6.0 familiar (pools de aplicativos e ativação de processo baseado em mensagem) e hospedagem de recursos (como proteção rápida contra falha, o monitoramento de integridade e reciclagem), mas ele remove a dependência do HTTP a ativação arquitetura. [!INCLUDE[iisver](../../../includes/iisver-md.md)] usa o WAS para realizar a ativação baseada em mensagem sobre HTTP. Componentes adicionais do WCF também se conecte ao WAS para fornecer a ativação baseada em mensagem sobre os outros protocolos que o WCF oferece suporte, como TCP, MSMQ e pipes nomeados. Isso permite que aplicativos que usam protocolos de comunicação para usar os recursos do IIS, como reciclagem de processos, rápidos não proteção e o sistema de configuração comuns que são disponíveis somente para aplicativos baseados em HTTP.  
  
 Essa opção de hospedagem requer que foi configurado corretamente, mas ele não exige que você escrever qualquer código de hospedagem como parte do aplicativo. Para obter mais informações sobre como configurar ESTIVESSE hospedando, consulte [como: Hospedar um serviço WCF no WAS](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md).  
  
## <a name="choosing-a-hosting-environment"></a>Escolhendo um ambiente de hospedagem  
 A tabela a seguir resume alguns dos principais benefícios e cenários associados a cada uma das opções de hospedagem.  
  
|Ambiente de hospedagem|Cenários comuns|Principais benefícios e limitações|  
|-------------------------|----------------------|----------------------------------|  
|Aplicativo gerenciado ("auto-hospedado")|– Usados durante o desenvolvimento de aplicativos de console.<br />-Rich WinForm e WPF aplicativos cliente que acessam serviços.|-Flexível.<br />-Fácil de implantar.<br />-Não uma solução empresarial para os serviços.|  
|Serviços do Windows (anteriormente conhecido como serviços NT)|-Um serviço WCF de longa execução hospedado fora do IIS.|-Serviço processo tempo de vida controlado pelo sistema operacional, mensagem de não ativada.<br />-Suporte para todas as versões do Windows.<br />-Proteger o ambiente.|  
|IIS 5.1, IIS 6.0|-Executando um serviço WCF lado a lado com o conteúdo ASP.NET na Internet usando o protocolo HTTP.|-Reciclagem de processo.<br />-Desligamento ocioso.<br />-Monitoramento de integridade de processo.<br />-Ativação baseada em mensagem.<br />-Apenas para HTTP.|  
|Serviço de Ativação de Processos do Windows (WAS)|-Execução de um serviço WCF sem instalar o IIS na Internet usando diversos protocolos de transporte.|-O IIS não é necessário.<br />-Reciclagem de processo.<br />-Desligamento ocioso.<br />-Monitoramento de integridade de processo.<br />-Ativação baseada em mensagem.<br />-Funciona com HTTP, TCP, pipes nomeados e MSMQ.|  
|IIS 7.0|-Executando um serviço WCF com conteúdo ASP.NET.<br />-Execução de um serviço WCF na Internet usando diversos protocolos de transporte.|-FORAM benefícios.<br />-Integrado com o conteúdo do ASP.NET e IIS.|  
  
 A escolha de um ambiente de hospedagem depende da versão do Windows na qual ele é implantado, os transportes que ele necessita para enviar mensagens e o tipo de processo e a reciclagem de domínio de aplicativo requer. A tabela a seguir resume os dados relacionados a esses requisitos.  
  
|Ambiente de hospedagem|Disponibilidade de plataforma|Transportes com suporte|Processo e a reciclagem do AppDomain|  
|-------------------------|---------------------------|--------------------------|-------------------------------------|  
|Aplicativos gerenciados ("auto-hospedado")|[!INCLUDE[wxp](../../../includes/wxp-md.md)], [!INCLUDE[ws2003](../../../includes/ws2003-md.md)], [!INCLUDE[wv](../../../includes/wv-md.md)],<br /><br /> [!INCLUDE[lserver](../../../includes/lserver-md.md)]|HTTP,<br /><br /> net.tcp,<br /><br /> NET. pipe,<br /><br /> net.msmq|Não|  
|Serviços do Windows (anteriormente conhecido como serviços NT)|[!INCLUDE[wxp](../../../includes/wxp-md.md)], [!INCLUDE[ws2003](../../../includes/ws2003-md.md)], [!INCLUDE[wv](../../../includes/wv-md.md)],<br /><br /> [!INCLUDE[lserver](../../../includes/lserver-md.md)]|HTTP,<br /><br /> net.tcp,<br /><br /> NET. pipe,<br /><br /> net.msmq|Não|  
|IIS 5.1|[!INCLUDE[wxp](../../../includes/wxp-md.md)]|HTTP|Sim|  
|IIS 6,0|[!INCLUDE[ws2003](../../../includes/ws2003-md.md)]|HTTP|Sim|  
|Serviço de Ativação de Processos do Windows (WAS)|[!INCLUDE[wv](../../../includes/wv-md.md)], [!INCLUDE[lserver](../../../includes/lserver-md.md)]|HTTP,<br /><br /> net.tcp,<br /><br /> NET. pipe,<br /><br /> net.msmq|Sim|  
  
 É importante observar que executando um serviço ou qualquer extensão de um host não confiável comprometimentos de segurança. Além disso, observe que, ao abrir um <xref:System.ServiceModel.ServiceHost> sob representação, um aplicativo deve garantir que o usuário não estiver conectado, por exemplo armazenando em cache o <xref:System.Security.Principal.WindowsIdentity> do usuário.  
  
## <a name="see-also"></a>Consulte também

- [Requisitos do sistema](../../../docs/framework/wcf/wcf-system-requirements.md)
- [Ciclo de vida de programação básica](../../../docs/framework/wcf/basic-programming-lifecycle.md)
- [Implementando contratos de serviço](../../../docs/framework/wcf/implementing-service-contracts.md)
- [Como: Hospedar um serviço WCF no IIS](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)
- [Como: Hospedar um serviço WCF no WAS](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md)
- [Como: Hospedar um serviço WCF em um serviço Windows gerenciado](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-a-managed-windows-service.md)
- [Como: Hospedar um serviço WCF em um aplicativo gerenciado](../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md)
