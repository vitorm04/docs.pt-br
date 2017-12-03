---
title: "Hospedagem no serviço de ativação do processo do Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: hosting services [WCF], WAS
ms.assetid: d2b9d226-15b7-41fc-8c9a-cb651ac20ecd
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 63f44a6380d2bca4ad831c590920e09ab93610c4
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="hosting-in-windows-process-activation-service"></a>Hospedagem no serviço de ativação do processo do Windows
O serviço de ativação de processos do Windows (WAS) gerencia a ativação e a vida útil dos processos de trabalho que contêm aplicativos que hospedam [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] serviços. O modelo de processo WAS generaliza o [!INCLUDE[iis601](../../../../includes/iis601-md.md)] modelo de processo para o servidor HTTP, removendo a dependência no HTTP. Isso permite que [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services para usar HTTP e protocolos não HTTP, como o Net.TCP, em um ambiente de hospedagem que oferece suporte à ativação baseada em mensagem e oferece a capacidade de hospedar um grande número de aplicativos em determinado computador.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Criando um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] consulte de serviço que executa no WAS do ambiente de hospedagem [como: hospedar um serviço WCF em WAS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md).  
  
 O modelo de processo WAS oferece vários recursos que permitem que os aplicativos sejam hospedados em um modo que é mais robusto, mais gerenciáveis e que usa recursos de forma eficiente:  
  
-   Ativação baseada em mensagem de aplicativos e aplicativos de processo de trabalho iniciados e interrompidos dinamicamente em resposta aos itens de trabalho de entrada que chegam usando HTTP e protocolos de rede não HTTP.  
  
-   Aplicativo robusto e reciclagem do processo de trabalho para manter a integridade de aplicativos em execução.  
  
-   Configuração de aplicativo centralizado e gerenciamento.  
  
-   Permite que aplicativos tirar proveito do modelo de processo do IIS sem a necessidade do volume de implantação de uma instalação completa do IIS.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Recursos do WAS, consulte [IIS 7.0 Beta: administração da Web do IIS 7.0](../../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md).  
  
 [Windows Server AppFabric](http://go.microsoft.com/fwlink/?LinkId=196496) funciona com [!INCLUDE[iisver](../../../../includes/iisver-md.md)] e o serviço de ativação de processos (WAS) do Windows para fornecer aplicativos avançados de ambiente para NET4 WCF e WF Serviços de hospedagem. Esses benefícios incluem gerenciamento de ciclo de vida do processo, a reciclagem do processo, hospedagem compartilhada, proteção rápida contra falha, processo deixar arquivos órfãos, ativação sob demanda e monitoramento de integridade. Para obter informações detalhadas, consulte [recursos de hospedagem do AppFabric](http://go.microsoft.com/fwlink/?LinkId=196494) e [conceitos de hospedagem do AppFabric](http://go.microsoft.com/fwlink/?LinkId=196495).  
  
## <a name="elements-of-the-was-addressing-model"></a>Elementos do WAS do modelo de endereçamento  
 Aplicativos têm endereços de identificador de recurso uniforme (URI), que são as unidades de código cujo ambiente de tempo de vida e execução são gerenciados pelo servidor. Pode ser uma instância de servidor único do WAS base em vários aplicativos diferentes. Organizam os servidores de aplicativos em grupos chamados *sites*. Em um site, aplicativos são organizados de forma hierárquica que reflete a estrutura dos URIs que servem como seus endereços externos.  
  
 Endereços de aplicativo têm duas partes: um prefixo URI base e um endereço específico do aplicativo, relativo (caminho) que fornecem o endereço externo para um aplicativo quando unidas. O prefixo URI base é construído com a associação do site e é usado para todos os aplicativos sob o site. Endereços de aplicativo, em seguida, são construídos colocando os fragmentos de caminho específico do aplicativo (como "/ applicationOne") e anexando-los para o prefixo URI base (por exemplo, "net.tcp://localhost") para chegar ao URI do aplicativo completo.  
  
 A tabela a seguir ilustra vários cenários possíveis de endereçamento para sites do WAS com HTTP e associações de site não HTTP.  
  
|Cenário|Associações de site|Caminho do aplicativo|URIs de aplicativo básico|  
|--------------|-------------------|----------------------|---------------------------|  
|HTTP apenas|http: *: 80:\*|/appTwo|http://localhost/appTwo/|  
|HTTP e não HTTP|http: *: 80:\*<br /><br /> NET. TCP: 808:\*|/appTwo|http://localhost/appTwo/<br />NET.TCP://localhost/appTwo/|  
|Diferente de HTTP apenas|NET. pipe: *|/appThree|NET.pipe://appThree/|  
  
 Serviços e recursos em um aplicativo também podem ser resolvidos. Dentro de um aplicativo, os recursos de aplicativo são endereçados relativo ao caminho base do aplicativo. Por exemplo, suponha que um site em um nome de máquina contoso.com tem associações de site para protocolos HTTP e Net.TCP. Suponha também que o site contém um aplicativo localizado em /Billing, que expõe um serviço em GetOrders.svc. Em seguida, se o serviço GetOrders.svc exposto a um ponto de extremidade com um endereço relativo da SecureEndpoint, o ponto de extremidade de serviço deve ser exposto nos URIs a seguir:  
  
 http://contoso.com/Billing/GetOrders.svc/SecureEndpoint  
NET.TCP://contoso.com/Billing/GetOrders.svc/SecureEndpoint  
  
## <a name="the-was-runtime"></a>O WAS em tempo de execução  
 Aplicativos são organizados em sites para fins de endereçamento e gerenciamento. Em tempo de execução aplicativos também são agrupados juntos em pools de aplicativos. Um pool de aplicativos pode hospedar vários aplicativos diferentes de vários sites diferentes. Todos os aplicativos dentro de um pool de aplicativos compartilham um conjunto comum de características de tempo de execução. Por exemplo, todos executados sob a mesma versão do common language runtime (CLR) e todos eles compartilham uma identidade de processo comum. Cada pool de aplicativos corresponde a uma instância de um processo de trabalho (w3wp.exe). Cada aplicativo gerenciado em execução dentro de um pool de aplicativo compartilhado é isolado de outros aplicativos por meio de um AppDomain do CLR.  
  
## <a name="see-also"></a>Consulte também  
 [ARQUITETURA de ativação](../../../../docs/framework/wcf/feature-details/was-activation-architecture.md)  
 [Configurando o WAS para utilização com o WCF](../../../../docs/framework/wcf/feature-details/configuring-the-wpa--service-for-use-with-wcf.md)  
 [Como: instalar e configurar os componentes de ativação do WCF](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md)  
 [Como hospedar um serviço do WCF no WAS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md)  
 [Recursos de hospedagem do Windows Server App Fabric](http://go.microsoft.com/fwlink/?LinkId=201276)
