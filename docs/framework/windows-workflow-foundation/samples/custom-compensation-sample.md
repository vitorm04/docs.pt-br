---
title: Exemplo de compensação personalizado
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 385920da-9284-44bf-9fe9-0d87c7478ec5
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c4d7219a2f16091d1997de6186312cce5ece0bd1
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="custom-compensation-sample"></a>Exemplo de compensação personalizado
Este exemplo mostra como usar <xref:System.Activities.Statements.CompensableActivity> e seu manipulador de compensação para definir a lógica personalizada de compensação. O cenário modelado nesse exemplo é uma agência de arrendamento do caminhão.  
  
## <a name="sample-details"></a>Detalhes de exemplo  
 As etapas simuladas são:  
  
1.  As aspas alugado do caminhão de um usuário por uma determinada data.  
  
2.  Três empresas do caminhão são entradas em contato e as três aspas são fornecidas.  
  
3.  O usuário seleciona uma citação do caminhão e continua a ordem pelo cartão de crédito.  
  
4.  O aplicativo cancela as outras aspas de dois caminhões.  
  
5.  O aplicativo carrega uma taxa de serviço que é não reembolsável para contas não superiores se cancelamento acontece 10 dias ou menos antes da data de retorno.  
  
6.  O aplicativo carrega a taxa de alugado caminhão.  
  
7.  O aplicativo esperado até a data de fallback ou até que o cliente decidir cancelar a reserva, qualquer vem primeiro.  
  
8.  Se o cliente cancela a reserva, lógica personalizada de compensação de <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> é executado de acordo com a seguinte lógica:  
  
    1.  Se o cliente tem uma conta não superior e é menor que 10 dias de data de retorno, então a taxa de serviço é carregada ainda; caso contrário, o aplicativo reembolsa a taxa de serviço.  
  
    2.  O resto das atividades compensáveis (taxa de pedido de caminhão + ordem de caminhão) é executado de acordo com a lógica padrão de compensação, que é compensar em ordem inversa de execução.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Usando [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], abra a solução de CustomCompensation.sln. Ele está localizado no diretório \ WF básico compensação \ \ \ CustomCompensation.  
  
2.  Pressione CTRL+SHIFT+B para criar a solução.  
  
3.  O pressionar o CTRL + F5 para executar o aplicativo.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Compensation\CustomCompensation`