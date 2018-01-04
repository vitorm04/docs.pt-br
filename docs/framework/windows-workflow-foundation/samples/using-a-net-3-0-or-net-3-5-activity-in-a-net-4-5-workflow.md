---
title: Usando uma atividade do .NET Framework 3.0 ou do.NET Framework 3.5 em um fluxo de trabalho do .NET Framework 4.5
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6c53fd4c-5dd0-4fb4-ab6b-111302629548
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 05660c3dc91d9d7cdba506670f62711752d7d100
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="using-a-net-framework-30-or-net-framework-35-activity-in-a-net-framework-45-workflow"></a>Usando uma atividade do .NET Framework 3.0 ou do.NET Framework 3.5 em um fluxo de trabalho do .NET Framework 4.5
A atividade de <xref:System.Activities.Statements.Interop> permite que você execute uma atividade do .NET Framework 3.0 [!INCLUDE[wf](../../../../includes/wf-md.md)] em um fluxo de trabalho [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] . Este exemplo demonstra como usar a atividade de <xref:System.Activities.Statements.Interop> para passar uma cadeia de caracteres como um argumento para uma atividade personalizado de [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] .  
  
## <a name="to-use-this-sample"></a>Para usar este exemplo  
  
1.  Usando [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], abra o arquivo de solução de SimpleInterop.sln.  
  
2.  Para criar a solução, pressione CTRL+SHIFT+B.  
  
3.  Para executar a solução, pressione CTRL+F5.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Migration\SimpleInterop`  
  
## <a name="see-also"></a>Consulte também
