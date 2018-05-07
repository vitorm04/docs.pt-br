---
title: Controlando a auto inicialização do host de serviço do WCF
ms.date: 03/30/2017
f1_keywords:
- WcfOptions
ms.assetid: 6abe5d34-519b-4cef-8f02-3c0a7f125585
ms.openlocfilehash: fe936ee3ff42b586c733de597de808b86f3e2575
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="controlling-auto-launching-of-wcf-service-host"></a>Controlando a auto inicialização do host de serviço do WCF
Você pode controlar o recurso auto inicialização do Host de serviço do Windows Communication Foundation (WCF) (WcfSvcHost.exe) para um [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] projeto de biblioteca de serviço, ao depurar outro projeto na mesma solução do Visual Studio que contém vários projetos .  
  
 Para fazer isso, clique com botão direito do [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] projeto de serviço no **Solution Explorer**, escolha **propriedades**e clique em **WCF opções** guia. O **iniciar ao depurar outro projeto na mesma solução o Host de serviço de WCF** caixa de seleção é habilitada por padrão. Você pode desmarcar a caixa de forma que [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Host de serviço para este projeto específico não é iniciado quando o outro projeto é depurado na mesma solução.  
  
 Esse comportamento não afeta a depuração F5 ou funcionalidades adicionar referência de serviço para este projeto.  
  
 Essa opção está disponível para os projetos a seguir:  
  
-   [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Projeto de biblioteca de serviço.  
  
-   Projeto de biblioteca de serviço de fluxo de trabalho sequencial.  
  
-   Projeto de biblioteca de serviço de fluxo de trabalho de máquina de estado.  
  
-   Projeto de biblioteca de serviço de distribuição.  
  
## <a name="see-also"></a>Consulte também  
 [Host de serviço do WCF (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)
