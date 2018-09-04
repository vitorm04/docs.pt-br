---
title: Hospedagem no serviço de ativação do processo do Windows
ms.date: 03/30/2017
helpviewer_keywords:
- hosting services [WCF], WAS
ms.assetid: d2b9d226-15b7-41fc-8c9a-cb651ac20ecd
ms.openlocfilehash: 0fe38b690d093e5a0bbe90d2b62e56b5d0cb4816
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43534703"
---
# <a name="hosting-in-windows-process-activation-service"></a>Hospedagem no serviço de ativação do processo do Windows
O serviço de ativação de processos do Windows (WAS) gerencia a ativação e o tempo de vida dos processos de trabalho que contêm aplicativos que hospedar serviços do Windows Communication Foundation (WCF). O modelo de processo WAS generaliza o [!INCLUDE[iis601](../../../../includes/iis601-md.md)] modelo de processo para o servidor HTTP, removendo a dependência no HTTP. Isso permite que os serviços do WCF para usar HTTP e protocolos não HTTP, como o NET. TCP, em um ambiente de hospedagem que oferece suporte à ativação baseada em mensagem e oferece a capacidade de hospedar um grande número de aplicativos em um determinado computador.  
  
 Para obter mais informações sobre a criação de um serviço WCF que é executado no ambiente de hospedagem do WAS, consulte [como: hospedar um serviço WCF no WAS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md).  
  
 O modelo de processo WAS oferece vários recursos que permitem que os aplicativos sejam hospedados em uma maneira que é mais robusto, mais gerenciável e que usa recursos com eficiência:  
  
-   Ativação baseada em mensagem de aplicativos e aplicativos de processo de trabalho iniciados e interrompidos dinamicamente em resposta aos itens de trabalho de entrada que chegam usando HTTP e protocolos de rede não-HTTP.  
  
-   Aplicativo robusto e reciclagem do processo de trabalho para manter a integridade dos aplicativos em execução.  
  
-   Configuração de aplicativos centralizado e gerenciamento.  
  
-   Permite que os aplicativos tirar proveito do modelo de processo do IIS sem exigir que o volume de implantação de uma instalação completa do IIS.  
  
 Para obter mais informações sobre os recursos do WAS, consulte [IIS 7.0 Beta: administração de Web do IIS 7.0](../../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md).  
  
 [O Windows Server AppFabric](https://go.microsoft.com/fwlink/?LinkId=196496) funciona com [!INCLUDE[iisver](../../../../includes/iisver-md.md)] e o Windows o serviço de ativação de processos (WAS) para fornecer um ambiente de serviços NET4 WCF e WF de hospedagem de aplicativos avançados. Esses benefícios incluem gerenciamento de ciclo de vida do processo, reciclagem de processo, hospedagem compartilhada, proteção rápida contra falha, órfão de processo, ativação e sob demanda e monitoramento de integridade. Para obter informações detalhadas, consulte [recursos de hospedagem de AppFabric](https://go.microsoft.com/fwlink/?LinkId=196494) e [conceitos de hospedagem de AppFabric](https://go.microsoft.com/fwlink/?LinkId=196495).  
  
## <a name="elements-of-the-was-addressing-model"></a>Elementos do WAS do modelo de endereçamento  
 Aplicativos têm endereços de identificador de recurso uniforme (URI), que são as unidades de código cujo ambiente de execução e tempo de vida são gerenciados pelo servidor. Uma instância de servidor única do WAS pode ser doméstica para muitos aplicativos diferentes. Organizam os servidores de aplicativos em grupos chamados *sites*. Dentro de um site, aplicativos são organizados de forma hierárquica que reflete a estrutura dos URIs que servem como seus endereços externos.  
  
 Endereços de aplicativo têm duas partes: um prefixo URI base e um endereço específico do aplicativo, relativo (caminho), que fornece o endereço externo para um aplicativo quando unidas. O prefixo URI base é construído com a associação do site e é usado para todos os aplicativos no site. Endereços de aplicativo, em seguida, são construídos por meio de fragmentos de caminho específico do aplicativo (por exemplo, "/ applicationOne") e acrescentando-os para o prefixo URI base (por exemplo, "baseaddress="NET.TCP://localhost:6080/vmmhelperservice/") para chegar até o URI do aplicativo completo.  
  
 A tabela a seguir ilustra vários cenários possíveis de endereçamento para sites WAS com HTTP e associações do site não HTTP.  
  
|Cenário|Associações do site|Caminho do aplicativo|URIs de aplicativo básico|  
|--------------|-------------------|----------------------|---------------------------|  
|Somente HTTP|http: *: 80:\*|/appTwo|http://localhost/appTwo/|  
|HTTP e não HTTP|http: *: 80:\*<br /><br /> NET. TCP: 808:\*|/appTwo|http://localhost/appTwo/<br />NET.TCP://localhost/appTwo/|  
|Não-HTTP apenas|NET. pipe: *|/appThree|NET.pipe://appThree/|  
  
 Serviços e recursos dentro de um aplicativo também podem ser resolvidos. Dentro de um aplicativo, os recursos do aplicativo são endereçados relativo ao caminho base do aplicativo. Por exemplo, suponha que um site em um nome de máquina contoso.com tem associações de site para protocolos HTTP e NET. TCP. Também supõem que o site contém um aplicativo localizado em /Billing, que expõe um serviço em GetOrders.svc. Em seguida, se o serviço GetOrders.svc exposto a um ponto de extremidade com um endereço relativo da SecureEndpoint, o ponto de extremidade de serviço deve ser exposto nos URIs a seguir:  
  
 http://contoso.com/Billing/GetOrders.svc/SecureEndpoint  
NET.TCP://contoso.com/Billing/GetOrders.svc/SecureEndpoint  
  
## <a name="the-was-runtime"></a>O WAS tempo de execução  
 Aplicativos são organizados em sites para fins de endereçamento e de gerenciamento. Em tempo de execução aplicativos também são agrupados juntos em pools de aplicativos. Um pool de aplicativos pode hospedar vários aplicativos diferentes de muitos sites diferentes. Todos os aplicativos dentro de um pool de aplicativos compartilham um conjunto comum de características de tempo de execução. Por exemplo, todos são executados sob a mesma versão do common language runtime (CLR) e todas elas compartilham uma identidade comum do processo. Cada pool de aplicativos corresponde a uma instância de um processo de trabalho (w3wp.exe). Cada aplicativo gerenciado em execução dentro de um pool de aplicativos compartilhados é isolado de outros aplicativos por meio de um AppDomain do CLR.  
  
## <a name="see-also"></a>Consulte também  
 [Arquitetura de ativação WAS](../../../../docs/framework/wcf/feature-details/was-activation-architecture.md)  
 [Configurando o WAS para utilização com o WCF](../../../../docs/framework/wcf/feature-details/configuring-the-wpa--service-for-use-with-wcf.md)  
 [Como instalar e configurar os componentes de ativação do WCF](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md)  
 [Como hospedar um serviço do WCF no WAS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md)  
 [Recursos de hospedagem do Windows Server App Fabric](https://go.microsoft.com/fwlink/?LinkId=201276)
