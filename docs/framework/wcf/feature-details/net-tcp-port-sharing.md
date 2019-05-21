---
title: Compartilhamento de porta Net.TCP
ms.date: 03/30/2017
helpviewer_keywords:
- port activation [WCF]
- port sharing [WCF]
ms.assetid: f13692ee-a179-4439-ae72-50db9534eded
ms.openlocfilehash: 8eb0a2a5b8b6edad17477e1fd65f72b540a8a674
ms.sourcegitcommit: ffd7dd79468a81bbb0d6449f6d65513e050c04c4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/21/2019
ms.locfileid: "65960039"
---
# <a name="nettcp-port-sharing"></a>Compartilhamento de porta Net.TCP
Windows Communication Foundation (WCF) fornece um novo protocolo de rede com base em TCP (net.tcp://) para comunicação de alto desempenho. O WCF também apresenta um novo componente do sistema, o serviço de compartilhamento de porta NET. TCP que permite que as portas do NET. TCP sejam compartilhadas entre vários processos do usuário.  
  
## <a name="background-and-motivation"></a>Plano de fundo e motivação  
 Quando o protocolo TCP/IP foi introduzido pela primeira vez, apenas um pequeno número de protocolos de aplicativo feita usá-lo. TCP/IP usado números de porta para diferenciar entre aplicativos atribuindo um número de porta exclusivo de 16 bits para cada protocolo de aplicativo. Por exemplo, o tráfego HTTP hoje é padronizado para usar a porta TCP 80, SMTP usa a porta 25 TCP e FTP usa portas TCP 20 e 21. Outros aplicativos usando o TCP como um transporte podem escolher outro número de porta disponível, por convenção, ou por meio da padronização formal.  
  
 Usar números de porta para fazer a distinção entre aplicativos teve problemas de segurança. Em geral, os firewalls estão configurados para bloquear o tráfego TCP em todas as portas, exceto para alguns pontos de entrada conhecido, para que implantar um aplicativo que usa uma porta não padrão é frequentemente complicada ou até mesmo impossível devido à presença de firewalls corporativos e pessoais. Aplicativos que podem se comunicar através das portas padrão, bem conhecidas que já são permitidas, reduza a superfície de ataque externo. Muitos aplicativos de rede fazem uso do HTTP do protocolo porque a maioria dos firewalls são configurados por padrão para permitir o tráfego na porta TCP 80.  
  
 O HTTP. Modelo SYS na qual o tráfego para muitos aplicativos diferentes do HTTP é multiplexado em uma única porta TCP se tornou padrão na plataforma Windows. Isso fornece um ponto de controle comum para o firewall de administradores, permitindo que os desenvolvedores de aplicativos minimizar o custo de implantação da criação de novos aplicativos que podem tornar usem a rede.  
  
 A capacidade de compartilhar portas em vários aplicativos HTTP tem sido um recurso de Internet Information Services (IIS). No entanto, ele era somente com a introdução do HTTP. SYS (o modo de kernel ouvinte de protocolo HTTP) com [!INCLUDE[iis601](../../../../includes/iis601-md.md)] que essa infraestrutura totalmente foi generalizada. Em vigor, o HTTP. SYS permite que os processos de usuário arbitrários compartilhar as portas TCP dedicadas ao tráfego HTTP. Essa funcionalidade permite que diversos aplicativos HTTP coexistam no mesmo computador físico em processos separados, isolados compartilhando a infraestrutura de rede necessária para enviar e receber o tráfego na porta TCP 80. O serviço de compartilhamento de porta NET. TCP permite que o mesmo tipo de compartilhamento para aplicativos do NET. TCP de porta.  
  
## <a name="port-sharing-architecture"></a>Arquitetura de compartilhamento de porta  
 A arquitetura de compartilhamento de porta no WCF tem três componentes principais:  
  
- Um processo de trabalho: Qualquer processo net.tcp:// usando portas compartilhadas se comunicando.  
  
- O transporte TCP do WCF: Implementa o protocolo net.tcp://.  
  
- O serviço de compartilhamento de porta NET. TCP: Permite que vários processos de trabalho compartilhar a mesma porta TCP.  
  
 O serviço de compartilhamento de porta NET. TCP é um serviço do Windows de modo de usuário que aceita conexões net.tcp:// em nome os processos de trabalho que se conectam por meio dele. Quando chega uma conexão de soquete, a serviço de compartilhamento de porta inspeciona o fluxo de mensagem de entrada para obter seu endereço de destino. Com base nesse endereço, a serviço de compartilhamento de porta pode rotear o fluxo de dados para o aplicativo que, por fim, a processa.  
  
 Quando um serviço WCF que usa a porta net.tcp:// é aberto, a infraestrutura de transporte TCP do WCF não diretamente abre um soquete TCP no processo do aplicativo. Em vez disso, a infraestrutura de transporte registra o endereço de base do serviço identificador de recurso uniforme (URI) com o serviço de compartilhamento de porta NET. TCP e aguarda a serviço para escutar mensagens em seu nome de compartilhamento de porta.  A serviço de compartilhamento de porta expede mensagens endereçadas para o serviço de aplicativo à medida que eles chegam.  
  
## <a name="installing-port-sharing"></a>Instalando o compartilhamento de porta  
 O serviço de compartilhamento de porta NET. TCP está disponível em todos os sistemas operacionais que dão suporte a WinFX, mas o serviço não está habilitado por padrão. Como uma precaução de segurança, um administrador deve habilitar manualmente o serviço de compartilhamento de porta NET. TCP antes do primeiro uso. O serviço de compartilhamento de porta NET. TCP expõe opções de configuração que permitem que você manipule várias características dos soquetes de rede pela porta do serviço de compartilhamento de propriedade. Para obter mais informações, confira [Como: Habilitar o serviço de compartilhamento de porta NET. TCP](../../../../docs/framework/wcf/feature-details/how-to-enable-the-net-tcp-port-sharing-service.md).  
  
## <a name="using-nettcp-port-sharing-in-an-application"></a>Usando em um aplicativo de compartilhamento de porta NET. TCP  
 A maneira mais fácil de usar em seu aplicativo do WCF de compartilhamento de porta net.tcp:// é expor um serviço usando o <xref:System.ServiceModel.NetTcpBinding> e, em seguida, para habilitar o serviço de compartilhamento de porta NET. TCP usando o <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> propriedade.  
  
 Para obter mais informações sobre como fazer isso, confira [Como: Configurar um serviço WCF para usar compartilhamento de porta](../../../../docs/framework/wcf/feature-details/how-to-configure-a-wcf-service-to-use-port-sharing.md).  
  
## <a name="security-implications-of-port-sharing"></a>Implicações de segurança de compartilhamento de porta  
 Embora o serviço de compartilhamento de porta NET. TCP fornece uma camada de processamento entre aplicativos e a rede, aplicativos que usam o compartilhamento de porta ainda devem ser protegidos como se eles foram escutando diretamente na rede. Especificamente, os aplicativos que usam o compartilhamento de porta devem avaliar os privilégios de processo sob a qual eles são executados. Considere a execução de seu aplicativo usando a conta de serviço de rede interna, que é executado com o conjunto mínimo de privilégios de processo necessários para comunicação de rede.  
  
## <a name="see-also"></a>Consulte também

- [Configurando o serviço de compartilhamento de porta NET.TCP](../../../../docs/framework/wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md)
- [Hospedagem](../../../../docs/framework/wcf/feature-details/hosting.md)
- [Como: Configurar um serviço WCF para usar compartilhamento de porta](../../../../docs/framework/wcf/feature-details/how-to-configure-a-wcf-service-to-use-port-sharing.md)
- [Como: Habilitar o serviço de compartilhamento de porta NET. TCP](../../../../docs/framework/wcf/feature-details/how-to-enable-the-net-tcp-port-sharing-service.md)
