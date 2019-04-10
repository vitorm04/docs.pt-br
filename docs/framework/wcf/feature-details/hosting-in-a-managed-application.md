---
title: Hospedagem em um aplicativo gerenciado
ms.date: 03/30/2017
ms.assetid: af70132d-e9e1-4f32-b20f-f0014629758a
ms.openlocfilehash: 415a6fef511d7d7397a38882801e5848e2998a11
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59218791"
---
# <a name="hosting-in-a-managed-application"></a>Hospedagem em um aplicativo gerenciado
Serviços do Windows Communication Foundation (WCF) podem ser hospedados em qualquer [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] aplicativo. Serviços de hospedagem interna é a opção de hospedagem mais flexível porque requer que a infra-estrutura mínimos para implantar. No entanto, também é a opção de hospedagem menos robusta, porque os aplicativos gerenciados não fornecem hospedagem avançados e recursos de gerenciamento de outras opções de hospedagem no WCF, como os serviços de Internet Information Services (IIS) e Windows.  
  
 Para criar um serviço auto-hospedado, crie e abra uma instância da <xref:System.ServiceModel.ServiceHost>, que inicia um serviço de escuta de mensagens. Para obter mais informações, confira [Como: Hospedar um serviço WCF em um aplicativo gerenciado](../../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md).  
  
 Para obter um exemplo completo sobre como definir um contrato, implemente o contrato e hospedar um serviço dentro de um aplicativo gerenciado, consulte a [Tutorial de Introdução](../../../../docs/framework/wcf/getting-started-tutorial.md) e o [auto-hospedar](../../../../docs/framework/wcf/samples/self-host.md).  
  
 As seções a seguir descrevem cenários comuns que usam essa opção de hospedagem.  
  
## <a name="console-applications"></a>Aplicativos de console  
 Cenários comuns que permite a hospedagem interna são serviços WCF em execução dentro de aplicativos de console. Hospedar um serviço WCF dentro de um aplicativo de console é geralmente útil durante a fase de desenvolvimento do serviço. Isso os torna fácil de depurar, fácil de obter as informações de rastreamento para descobrir o que está acontecendo dentro do aplicativo e fácil de mover-se copiando-os para novos locais.  
  
## <a name="rich-client-applications"></a>Aplicativos cliente avançados  
 Outros cenários comuns que permite a hospedagem interna são aplicativos cliente avançados, como aqueles baseados em Windows Presentation Foundation (WPF) ou Windows Forms (WinForms). Essa opção de hospedagem também torna mais fácil para aplicativos cliente avançados, tais como [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] e os aplicativos WinForms, para se comunicar com o mundo exterior. Por exemplo, um cliente de colaboração ponto a ponto que usa [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] para sua interface do usuário e também hospeda um serviço WCF que permite que outros clientes para conectá-lo e compartilhar informações.  
  
## <a name="see-also"></a>Consulte também

- [Serviços de hospedagem](../../../../docs/framework/wcf/hosting-services.md)
- [Guia de introdução ao tutorial](../../../../docs/framework/wcf/getting-started-tutorial.md)
