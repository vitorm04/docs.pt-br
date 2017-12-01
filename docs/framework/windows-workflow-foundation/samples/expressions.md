---
title: Expressions2
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 43a85905-77b5-4893-bb38-1cb9b293d69d
caps.latest.revision: "14"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 681b96d24288cc1a86c9c4525e31ed67f1a18331
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/28/2017
---
# <a name="expressions"></a>Expressões
Este exemplo demonstra como usar expressões básicas em um fluxo de trabalho. Consiste em um fluxo de trabalho que calcula estatísticas básicas de salário para dois funcionários de uma empresa fictícia. Duas classes, `Employee` e `SalaryStats`, são definidas em Employee.cs e em SalaryStats.cs. Essas classes são usadas em um fluxo de trabalho que mostra como executar operações aritméticas simples e da cadeia de caracteres em propriedades de variáveis de tipos complexos.  
  
 O fluxo de trabalho de cálculo de salário é definido em XAML e em C# para demonstrar os dois estilos criando. A versão XAML está contida em SalaryCalculation.xaml e pode ser exibida e editado no designer de fluxo de trabalho. A versão de C# reside em Module.vb. As expressões usadas em XAML obedecem à sintaxe do Visual Basic, e usam-se <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> e atividades da expressão de <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> para executar. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Consulte expressões do Visual Basic, [expressões do Visual Basic](http://go.microsoft.com/fwlink/?LinkId=165912). Por outro lado, as expressões em C# são gravadas como expressões lambda e uso <xref:System.Activities.Expressions.LambdaValue%601> e atividades da expressão de <xref:System.Activities.Expressions.LambdaReference%601> . Escrever expressões como expressões lambda permite que o compilador C# fornece a sintaxe que realça e verificação estático. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]expressões lambda em c#, consulte [expressões Lambda (guia de programação c#)](http://go.microsoft.com/fwlink/?LinkId=182082). Se um fluxo de trabalho é criado no código usando Visual Basic, então as expressões do Visual Basic lambda são usadas. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]expressões lambda em Visual Basic, consulte [expressões Lambda (Visual Basic)](http://go.microsoft.com/fwlink/?LinkId=152437). [!INCLUDE[crabout](../../../../includes/crabout-md.md)]sobre a criação de fluxos de trabalho usando o código, consulte [criação de fluxos de trabalho, atividades e expressões usando imperativo código](../../../../docs/framework/windows-workflow-foundation/authoring-workflows-activities-and-expressions-using-imperative-code.md).  
  
#### <a name="to-run-the-sample"></a>Para executar a amostra  
  
1.  Abra a solução de Expressions.sln em [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Pressione CTRL + SHIFT + B para compilar a solução ou selecione **compilar solução** do **criar** menu.  
  
    > [!NOTE]
    >  Para abrir SalaryCalculation.xaml no designer do Visual Studio, você deve primeiro criar seu projeto garantir que `Employee` e as classes de `SalaryStats` estão disponíveis para o designer.  
  
3.  Depois que a compilação foi bem-sucedida, pressione F5 ou selecione **iniciar depuração** do **depurar** menu. Como alternativa, você pode pressionar Ctrl + F5 ou selecionar **Start Without Debugging** do **depurar** menu para executar sem depuração.  
  
> [!IMPORTANT]
>  Os exemplos podem mais ser instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Expressions`