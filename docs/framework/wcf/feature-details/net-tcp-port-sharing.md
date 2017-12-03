---
title: Compartilhamento de porta Net.TCP
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- port activation [WCF]
- port sharing [WCF]
ms.assetid: f13692ee-a179-4439-ae72-50db9534eded
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c54ce56cccffa350479d0dd4dcec130ddd004764
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="nettcp-port-sharing"></a>Compartilhamento de porta Net.TCP
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]Fornece um novo protocolo de rede baseada em TCP (net.tcp://) para comunicação de alto desempenho. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]também apresenta um novo componente do sistema, o serviço de compartilhamento de porta NET. TCP que permite que portas NET. TCP ser compartilhado entre vários processos de usuário.  
  
## <a name="background-and-motivation"></a>Plano de fundo e motivação  
 Quando o protocolo TCP/IP foi apresentado pela primeira vez, somente um pequeno número de protocolos de aplicativo feita usá-lo. TCP/IP usada números de porta para diferenciar entre os aplicativos, atribuindo um número de porta exclusivo de 16 bits para cada protocolo de aplicativo. Por exemplo, o tráfego HTTP hoje é padronizado para usar a porta TCP 80, SMTP usa a porta TCP 25 e FTP usa as portas TCP 20 e 21. Outros aplicativos usando TCP como um transporte podem escolher outro número de porta disponível, por convenção, ou por meio de padronização formal.  
  
 Usar números de porta para diferenciar entre aplicativos teve problemas de segurança. Em geral, os firewalls estão configurados para bloquear o tráfego TCP em todas as portas, exceto para alguns pontos de entrada conhecido para que implantar um aplicativo que usa uma porta não padrão geralmente é complicado ou até mesmo impossível devido à presença de firewalls corporativos e pessoais. Aplicativos que podem se comunicar através das portas padrão, bem conhecidas que já são permitidas, reduzir a superfície de ataque externo. Muitos aplicativos de rede fazem uso do HTTP do protocolo porque a maioria dos firewalls são configurados por padrão para permitir o tráfego na porta TCP 80.  
  
 O HTTP. Modelo de sistema no qual o tráfego de vários aplicativos diferentes de HTTP é multiplexado em uma única porta TCP se tornou padrão na plataforma Windows. Isso fornece um ponto de controle comum para firewall administradores enquanto permite que os desenvolvedores de aplicativos minimizar o custo de implantação de criação de novos aplicativos que podem tornar usem a rede.  
  
 A capacidade de compartilhar portas em vários aplicativos de HTTP foi um recurso de serviços de informações da Internet (IIS). No entanto, é somente com a introdução do HTTP. SYS (o modo de kernel protocolo ouvinte HTTP) com [!INCLUDE[iis601](../../../../includes/iis601-md.md)] que essa infraestrutura totalmente foi generalizada. Na realidade, o HTTP. SYS permite que os processos de usuário arbitrários de compartilhar portas TCP dedicadas ao tráfego HTTP. Esse recurso permite que vários aplicativos HTTP coexistam no mesmo computador físico em processos separados, isolados ao compartilhamento da infraestrutura de rede necessária para enviar e receber o tráfego pela porta TCP 80. O serviço de compartilhamento de porta NET. TCP permite que o mesmo tipo de porta NET. TCP aplicativos de compartilhamento.  
  
## <a name="port-sharing-architecture"></a>Arquitetura de compartilhamento de porta  
 A arquitetura de compartilhamento de porta no [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] tem três componentes principais:  
  
-   Um processo de trabalho: Qualquer processo se comunicar por net.tcp:// usando portas compartilhadas.  
  
-   O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] transporte TCP: implementa o protocolo net.tcp://.  
  
-   O serviço de compartilhamento de porta NET. TCP: Permite que vários processos de trabalho compartilhem a mesma porta TCP.  
  
 O serviço de compartilhamento de porta NET. TCP é um serviço do Windows de modo de usuário que aceita conexões de net.tcp:// em nome dos processos de trabalho que se conectam por meio dele. Quando chega uma conexão de soquete, a serviço de compartilhamento de porta inspeciona o fluxo de mensagem de entrada para obter o endereço de destino. Com base nesse endereço, a serviço de compartilhamento de porta pode rotear o fluxo de dados para o aplicativo que, por fim, a processa.  
  
 Quando um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço que usa a porta net.tcp:// é aberto, o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] infraestrutura de transporte TCP não abre diretamente um soquete TCP no processo do aplicativo. Em vez disso, a infraestrutura de transporte registra o endereço de base do serviço identificador de recurso uniforme (URI) com o serviço de compartilhamento de porta NET. TCP e aguarda a serviço para escutar mensagens em seu nome de compartilhamento de porta.  A serviço de compartilhamento de porta envia as mensagens destinadas para o serviço de aplicativo assim que elas chegam.  
  
## <a name="installing-port-sharing"></a>Instalando o compartilhamento de porta  
 O serviço de compartilhamento de porta NET. TCP está disponível em todos os sistemas operacionais que oferecem suporte a [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)], mas o serviço não está habilitado por padrão. Como uma precaução de segurança, um administrador deve habilitar manualmente o serviço de compartilhamento de porta NET. TCP antes do primeiro uso. O serviço de compartilhamento de porta NET. TCP expõe as opções de configuração que permitem que você manipule várias características de soquetes de rede pela porta do serviço de compartilhamento de propriedade. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Como: habilitar o serviço de compartilhamento de porta NET. TCP](../../../../docs/framework/wcf/feature-details/how-to-enable-the-net-tcp-port-sharing-service.md).  
  
## <a name="using-nettcp-port-sharing-in-an-application"></a>Usando em um aplicativo de compartilhamento de porta NET. TCP  
 A maneira mais fácil de usar a porta net.tcp:// compartilhamento em sua [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplicativo é expor um serviço usando o <xref:System.ServiceModel.NetTcpBinding> e, em seguida, habilitar o serviço de compartilhamento de porta NET. TCP usando o <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> propriedade.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]como fazer isso, consulte [como: configurar um serviço WCF para usar o compartilhamento de porta](../../../../docs/framework/wcf/feature-details/how-to-configure-a-wcf-service-to-use-port-sharing.md).  
  
## <a name="security-implications-of-port-sharing"></a>Implicações de segurança de compartilhamento de porta  
 Embora o serviço de compartilhamento de porta NET. TCP fornece uma camada de processamento entre aplicativos e rede, os aplicativos que usam o compartilhamento de porta ainda devem ser protegidos como se eles foram escuta diretamente na rede. Especificamente, os aplicativos que usam o compartilhamento de porta devem avaliar os privilégios do processo em que executarem. Considere a execução de seu aplicativo usando a conta de serviço de rede interna, que é executado com um conjunto mínimo de privilégios de processo necessário para a comunicação de rede.  
  
## <a name="see-also"></a>Consulte também  
 [Configurando o serviço de compartilhamento de porta NET. TCP](../../../../docs/framework/wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md)  
 [Hospedagem](../../../../docs/framework/wcf/feature-details/hosting.md)  
 [Como: configurar um serviço WCF para compartilhamento de porta de uso](../../../../docs/framework/wcf/feature-details/how-to-configure-a-wcf-service-to-use-port-sharing.md)  
 [Como: habilitar o serviço de compartilhamento de porta NET. TCP](../../../../docs/framework/wcf/feature-details/how-to-enable-the-net-tcp-port-sharing-service.md)
