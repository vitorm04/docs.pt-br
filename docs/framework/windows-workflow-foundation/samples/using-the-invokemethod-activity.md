---
title: Usando a atividade de InvokeMethod
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b6643550-d043-4ac7-8069-9c55ebbb4233
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ba0c2333c14eaebdb6409323bb6b92aa2b29d2ec
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="using-the-invokemethod-activity"></a>Usando a atividade de InvokeMethod
Este exemplo demonstra como usar o <!--zz <xref:System.Activities.Statements.InvokeMethod%601> --> [ <code>System.Activities.Statements.InvokeMethod\`1</code> ](https://msdn.microsoft.com/library/dd647677.aspx) atividade invocar métodos públicos em classes públicas. O <!--zz <xref:System.Activities.Statements.InvokeMethod%601> --> [ <code>System.Activities.Statements.InvokeMethod\`1</code> ](https://msdn.microsoft.com/library/dd647677.aspx) atividade permite que um fluxo de trabalho chamar métodos em objetos, passar parâmetros, obter o valor de retorno, especificar tipos de métodos genéricos e especificar se o método é síncrono ou assíncrono. 
  
Há uma versão não genérica do <xref:System.Activities.Statements.InvokeMethod> atividade em que o valor de retorno é definido como o <xref:System.Activities.Statements.InvokeMethod.Result%2A> propriedade e uma versão genérica do <!--zz <xref:System.Activities.Statements.InvokeMethod%601> --> [ <code>System.Activities.Statements.InvokeMethod\`1</code> ](https://msdn.microsoft.com/library/dd647677.aspx) em que o valor de retorno é retornado de atividade por meio de <!--zz <xref:System.Activities.Statements.InvokeMethod.Result%601.Result%2A> --> [ <code>System.Activities.Statements.InvokeMethod\`1.Result</code> ](https://msdn.microsoft.com/library/dd987724.aspx) propriedade do tipo `TResult`. 
  
 Este exemplo demonstra como chamar vários tipos de método. A lista a seguir detalha os tipos de método demonstrado no exemplo:  
  
-   Chamar um método de instância sem parâmetros.  
  
-   Chamar um método de instância com dois parâmetros (System.String e System.Int32).  
  
-   Chamar um método de instância com dois parâmetros (System.String e System.Int32) e uma matriz de parâmetros de tipo System.String [].  
  
-   Chamar um método de instância com dois parâmetros (dois números System.Int32) e resultado do tipo System.Int32.  
  
     O valor de retorno é associado a uma variável e impresso no console usando a atividade de <xref:System.Activities.Statements.WriteLine> .  
  
-   Chamar um método estático com dois parâmetros (System.String e System.Int32).  
  
-   Chamar um método de instância com um parâmetro genérico (System.String).  
  
-   Chamar um método estático com dois parâmetros genéricos (System.String e System.Int32).  
  
-   Chamar um método de instância que tem um parâmetro passado por referência (System.String).  
  
     O parâmetro referenciado é associado a uma variável e impresso no console usando a atividade de <xref:System.Activities.Statements.WriteLine> .  
  
-   Chamar um método de instância assíncrono.  
  
## <a name="to-use-this-sample"></a>Para usar este exemplo  
  
1.  Usando [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], abra o arquivo de solução de InvokeMethodUsage.sln.  
  
2.  Para criar a solução, pressione CTRL+SHIFT+B.  
  
3.  Para executar a solução, pressione CTRL+F5.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\InvokeMethod`