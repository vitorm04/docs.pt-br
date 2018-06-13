---
title: Exemplo compensável de atividades
ms.date: 03/30/2017
ms.assetid: 58f4898c-b2b8-44a4-9a73-3bef4da6d5ba
ms.openlocfilehash: 8008eaaca062723cab1efabfb1b25018353c73b5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33513998"
---
# <a name="compensable-activity-sample"></a>Exemplo compensável de atividades
Este exemplo demonstra como usar a atividade de `CompensableActivity` para definir o trabalho a ser feitos se necessário para uma determinada ação durante a execução normal e o trabalho que é necessário para ser feito para compensar essa ação, mais tarde.  A primeira parte do exemplo mostra como unidades de trabalho compensável podem ser definidas no Windows Workflow Foundation (WF) usando um `CompensableActivity` atividade e como elas são executadas em uma execução bem-sucedida.  A segunda parte do exemplo mostra como as mesmas unidades de trabalho compensável recebem automaticamente de compensação inesperado quando um evento é atingido e a instância de fluxo de trabalho é cancelada.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Usando o Visual Studio 2010, abra o CompensableActivity.sln.  
  
2.  Crie a solução. CTRL+SHIFT+B pressionando.  
  
3.  Executar o aplicativo pressionando F5.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Compensation\BasicCompensableActivity`