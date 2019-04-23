---
title: Controlando a auto inicialização do host de serviço do WCF
ms.date: 03/30/2017
f1_keywords:
- WcfOptions
ms.assetid: 6abe5d34-519b-4cef-8f02-3c0a7f125585
ms.openlocfilehash: 2fa060e567fba9bb5e6344b2c8fc67fb639ad0f7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59228491"
---
# <a name="controlling-auto-launching-of-wcf-service-host"></a>Controlando a auto inicialização do host de serviço do WCF
Você pode controlar o recurso a autoinicialização do Host de serviço do Windows Communication Foundation (WCF) (WcfSvcHost.exe) para um projeto de biblioteca de serviço WCF, quando você depurar outro projeto na mesma solução do Visual Studio que contém vários projetos.  
  
 Para fazer isso, clique com botão direito no projeto de serviço do WCF no **Gerenciador de soluções**, escolha **Properties**e clique em **opções do WCF** guia. O **iniciar durante a depuração de outro projeto na mesma solução o Host de serviço de WCF** caixa de seleção é habilitada por padrão. Você pode desmarcar a caixa para que o Host de serviço do WCF para esse projeto específico não é iniciada quando outro projeto é depurado na mesma solução.  
  
 Esse comportamento não afeta a depuração F5, ou as funcionalidades de adicionar referência de serviço para este projeto.  
  
 Essa opção está disponível para os projetos a seguir:  
  
-   Projeto de biblioteca de serviço do WCF.  
  
-   Projeto de biblioteca de serviço de fluxo de trabalho sequencial.  
  
-   Projeto de biblioteca de serviço de fluxo de trabalho de máquina de estado.  
  
-   Projeto de biblioteca de serviço de sindicalização.  
  
## <a name="see-also"></a>Consulte também

- [Host de serviço do WCF (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)
