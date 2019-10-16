---
title: Ciclo de vida de programação básica
ms.date: 03/30/2017
helpviewer_keywords:
- service creation [WCF]
ms.assetid: 7cf21bfe-23bd-46aa-8033-609f851dbf76
ms.openlocfilehash: fe578ba3c655c9c9ea8398b9b2e4d4f974153c8e
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320822"
---
# <a name="basic-programming-lifecycle"></a>Ciclo de vida de programação básica
O Windows Communication Foundation (WCF) permite que os aplicativos se comuniquem se estão no mesmo computador, na Internet ou em diferentes plataformas de aplicativos. Este tópico descreve as tarefas que são necessárias para criar um aplicativo WCF. Para um aplicativo de exemplo funcional, consulte [introdução tutorial](getting-started-tutorial.md).  
  
## <a name="the-basic-tasks"></a>As tarefas básicas  
 As tarefas básicas a serem executadas são, em ordem:  
  
1. Defina o contrato de serviço. Um contrato de serviço especifica a assinatura de um serviço, os dados que ele troca e outros dados necessários contratuais. Para obter mais informações, consulte [Designing Service Contracts](designing-service-contracts.md).  
  
2. Implemente o contrato. Para implementar um contrato de serviço, crie uma classe que implemente o contrato e especifique comportamentos personalizados que o tempo de execução deve ter. Para obter mais informações, consulte [implementando contratos de serviço](implementing-service-contracts.md).  
  
3. Configure o serviço especificando pontos de extremidade e outras informações de comportamento. Para obter mais informações, consulte [Configurando serviços](configuring-services.md).  
  
4. Hospede o serviço. Para obter mais informações, consulte [serviços de hospedagem](hosting-services.md).  
  
5. Crie um aplicativo cliente. Para obter mais informações, consulte [Building clients](building-clients.md).  
  
 Embora os tópicos nesta seção sigam essa ordem, alguns cenários não começam no início. Por exemplo, se você quiser criar um cliente para um serviço pré-existente, comece na etapa 5. Ou, se você estiver criando um serviço que outras pessoas usarão, você pode ignorar a etapa 5.  
  
 Quando estiver familiarizado com o desenvolvimento de contratos de serviço, você também poderá ler [introdução à extensibilidade](introduction-to-extensibility.md). Se você tiver problemas com seu serviço, marque [início rápido de solução de problemas do WCF](wcf-troubleshooting-quickstart.md) para ver se outros têm problemas semelhantes ou similares.  
  
## <a name="see-also"></a>Consulte também

- [Implementando contratos de serviço](implementing-service-contracts.md)
