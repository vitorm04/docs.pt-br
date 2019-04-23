---
title: Ciclo de vida de programação básica
ms.date: 03/30/2017
helpviewer_keywords:
- service creation [WCF]
ms.assetid: 7cf21bfe-23bd-46aa-8033-609f851dbf76
ms.openlocfilehash: 6d9ea3b877e7c735cf789039b2a6956037372888
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59330552"
---
# <a name="basic-programming-lifecycle"></a>Ciclo de vida de programação básica
Windows Communication Foundation (WCF) permite que aplicativos se comuniquem independentemente de estarem no mesmo computador, através da Internet ou em diferentes plataformas de aplicativo. Este tópico descreve as tarefas que são necessários para compilar um aplicativo WCF. Para um aplicativo de exemplo funcional, consulte [Tutorial de Introdução](../../../docs/framework/wcf/getting-started-tutorial.md).  
  
## <a name="the-basic-tasks"></a>As tarefas básicas  
 As tarefas básicas para executar são, em ordem:  
  
1. Defina o contrato de serviço. Um contrato de serviço Especifica a assinatura de um serviço, os dados que ele troca e outros dados necessários ao contrato. Para obter mais informações, consulte [Criando contratos de serviço](../../../docs/framework/wcf/designing-service-contracts.md).  
  
2. Implemente o contrato. Para implementar um contrato de serviço, crie uma classe que implementa o contrato e especifique comportamentos personalizados que o tempo de execução deve ter. Para obter mais informações, consulte [implementar contratos de serviço](../../../docs/framework/wcf/implementing-service-contracts.md).  
  
3. Configure o serviço especificando pontos de extremidade e outras informações de comportamento. Para obter mais informações, consulte [Configurando os serviços de](../../../docs/framework/wcf/configuring-services.md).  
  
4. Hospede o serviço. Para obter mais informações, consulte [serviços de hospedagem](../../../docs/framework/wcf/hosting-services.md).  
  
5. Crie um aplicativo cliente. Para obter mais informações, consulte [compilando clientes](../../../docs/framework/wcf/building-clients.md).  
  
 Embora os tópicos nesta seção siga esta ordem, alguns cenários não começar no início. Por exemplo, se você quiser criar um cliente para um serviço preexistente, você começa com a etapa 5. Ou, se você estiver criando um serviço que outras pessoas usarão, você pode ignorar a etapa 5.  
  
 Quando estiver familiarizado com o desenvolvimento de contratos de serviço, você também pode ler [Introdução à extensibilidade](../../../docs/framework/wcf/introduction-to-extensibility.md). Se você tiver problemas com seu serviço, verifique [início rápido de solução de problemas do WCF](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md) para ver se outras pessoas tenham problemas iguais ou semelhantes.  
  
## <a name="see-also"></a>Consulte também

- [Implementando contratos de serviço](../../../docs/framework/wcf/implementing-service-contracts.md)
