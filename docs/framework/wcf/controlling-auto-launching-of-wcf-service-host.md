---
title: Controlando a auto inicialização do host de serviço do WCF
ms.date: 03/30/2017
f1_keywords:
- WcfOptions
ms.assetid: 6abe5d34-519b-4cef-8f02-3c0a7f125585
ms.openlocfilehash: 63c3ca00c0cdc0b28de0fe245b616acd04ca50fe
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2018
---
# <a name="controlling-auto-launching-of-wcf-service-host"></a>Controlando a auto inicialização do host de serviço do WCF
Você pode controlar o recurso auto inicialização do Host de serviço do Windows Communication Foundation (WCF) (WcfSvcHost.exe) para um projeto de biblioteca de serviços WCF, quando você depurar outro projeto na mesma solução do Visual Studio que contém vários projetos.  
  
 Para fazer isso, clique com botão direito no projeto de serviço do WCF no **Solution Explorer**, escolha **propriedades**e clique em **WCF opções** guia. O **iniciar ao depurar outro projeto na mesma solução o Host de serviço de WCF** caixa de seleção é habilitada por padrão. Você pode desmarcar a caixa para que o Host de serviço do WCF para este projeto específico não é iniciado quando o outro projeto é depurado na mesma solução.  
  
 Esse comportamento não afeta a depuração F5 ou funcionalidades adicionar referência de serviço para este projeto.  
  
 Essa opção está disponível para os projetos a seguir:  
  
-   Projeto de biblioteca de serviço do WCF.  
  
-   Projeto de biblioteca de serviço de fluxo de trabalho sequencial.  
  
-   Projeto de biblioteca de serviço de fluxo de trabalho de máquina de estado.  
  
-   Projeto de biblioteca de serviço de distribuição.  
  
## <a name="see-also"></a>Consulte também  
 [Host de serviço do WCF (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)
