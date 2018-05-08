---
title: Hospedagem em um aplicativo gerenciado
ms.date: 03/30/2017
ms.assetid: af70132d-e9e1-4f32-b20f-f0014629758a
ms.openlocfilehash: f374c199fb1982ab8854e41c0c8308f46451d9d0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="hosting-in-a-managed-application"></a>Hospedagem em um aplicativo gerenciado
Serviços Windows Communication Foundation (WCF) podem ser hospedados em qualquer [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] aplicativo. Os serviços de hospedagem é a opção de hospedagem mais flexível porque ela exige a menor infra-estrutura para implantar. No entanto, também é a opção de hospedagem menos eficiente, porque os aplicativos gerenciados não fornecem hospedagem avançada e recursos de gerenciamento de outras opções de hospedagem no WCF, como os serviços de Internet Information Services (IIS) e Windows.  
  
 Para criar um serviço auto-hospedado, crie e abra uma instância do <xref:System.ServiceModel.ServiceHost>, que inicia um serviço de escuta de mensagens. Para obter mais informações, consulte [como: hospedar um serviço WCF em um aplicativo gerenciado](../../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md).  
  
 Para obter um exemplo completo sobre como definir um contrato, implemente o contrato e hospedar um serviço dentro de um aplicativo gerenciado, consulte o [Tutorial de Introdução](../../../../docs/framework/wcf/getting-started-tutorial.md) e [auto-host](../../../../docs/framework/wcf/samples/self-host.md).  
  
 As seções a seguir descrevem cenários comuns que usam essa opção de hospedagem.  
  
## <a name="console-applications"></a>Aplicativos de console  
 Cenários comuns que permite a auto-hospedagem são serviços WCF em execução em aplicativos de console. Hospedar um serviço WCF dentro de um aplicativo de console é normalmente útil durante a fase de desenvolvimento do serviço. Isso os torna fácil depurar obter informações de rastreamento para descobrir o que está acontecendo no aplicativo e fácil de mover copiando-os para novos locais.  
  
## <a name="rich-client-applications"></a>Aplicativos de cliente avançado  
 Outros cenários comuns que permite a auto-hospedagem são aplicativos cliente avançados, como aqueles baseados em Windows Presentation Foundation (WPF) ou Windows Forms (WinForms). Essa opção de hospedagem também torna mais fácil para aplicativos cliente avançados, como [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] e aplicativos WinForms, para se comunicar com o mundo exterior. Por exemplo, um cliente de colaboração ponto a ponto que usa [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] para sua interface de usuário e também hospeda um serviço WCF que permite que outros clientes para se conectar a ele e compartilhar informações.  
  
## <a name="see-also"></a>Consulte também  
 [Hospedando serviços](../../../../docs/framework/wcf/hosting-services.md)  
 [Tutorial de Introdução](../../../../docs/framework/wcf/getting-started-tutorial.md)
