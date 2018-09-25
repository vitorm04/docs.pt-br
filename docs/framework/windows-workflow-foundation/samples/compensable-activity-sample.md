---
title: Exemplo compensável de atividades
ms.date: 03/30/2017
ms.assetid: 58f4898c-b2b8-44a4-9a73-3bef4da6d5ba
ms.openlocfilehash: 3bf1d120cd700830a98f53495f7e9989ffec73db
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47089818"
---
# <a name="compensable-activity-sample"></a>Exemplo compensável de atividades
Este exemplo demonstra como usar a atividade de `CompensableActivity` para definir o trabalho a ser feitos se necessário para uma determinada ação durante a execução normal e o trabalho que é necessário para ser feito para compensar essa ação, mais tarde.  A primeira parte do exemplo mostra como unidades de trabalho compensável podem ser definidas no Windows Workflow Foundation (WF) usando um `CompensableActivity` atividade e como eles são executados em uma execução bem-sucedida.  A segunda parte do exemplo mostra como as mesmas unidades de trabalho compensável recebem automaticamente de compensação inesperado quando um evento é atingido e a instância de fluxo de trabalho é cancelada.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Usando o Visual Studio 2010, abra o CompensableActivity.sln.  
  
2.  Crie a solução. CTRL+SHIFT+B pressionando.  
  
3.  Executar o aplicativo pressionando F5.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Compensation\BasicCompensableActivity`