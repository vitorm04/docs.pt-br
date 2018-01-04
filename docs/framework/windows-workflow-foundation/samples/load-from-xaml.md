---
title: Carregamento XAML
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1f103ef6-7bed-4f16-ae52-9e665c5a43d7
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 28f5f4a57f8fd6ee8b739b38735d41a118abc0cb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="load-from-xaml"></a>Carregamento XAML
Este exemplo demonstra como carregar dinamicamente um fluxo de trabalho XAML sem ter que execute a ferramenta de XamlBuildTask. Em vez disso, o exemplo chama o método de <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A> . O exemplo é um aplicativo cliente de [!INCLUDE[avalon1](../../../../includes/avalon1-md.md)] que carrega fluxos de trabalho XAML usando a classe de <xref:System.Activities.XamlIntegration.ActivityXamlServices> e os executar. Depois que foram carregados usando a classe de <xref:System.Activities.XamlIntegration.ActivityXamlServices> , <xref:System.Activities.DynamicActivity%601> é retornado que pode ser executado.  
  
#### <a name="to-use-this-sample"></a>Para usar este exemplo  
  
1.  Usando [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], abra o arquivo de solução de LoadFromXAML.sln.  
  
2.  Para criar a solução, pressione CTRL+SHIFT+B.  
  
3.  Para executar a solução, pressione CTRL+F5.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\DynamicActivity\LoadFromXAML`