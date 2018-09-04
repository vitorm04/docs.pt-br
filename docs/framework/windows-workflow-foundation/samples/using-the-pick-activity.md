---
title: Usando a atividade de picareta
ms.date: 03/30/2017
ms.assetid: b89be812-a247-4025-b0e3-ffb20db027a6
ms.openlocfilehash: 193b60bff7b08c0de9a0957668483eb73be97274
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43563156"
---
# <a name="using-the-pick-activity"></a>Usando a atividade de picareta
Este exemplo demonstra como usar a atividade de <xref:System.Activities.Statements.Pick> .  
  
 A atividade de <xref:System.Activities.Statements.Pick> fornece a modelagem com base em eventos do controle. Se comporta semelhante à declaração C# `switch` , que executa somente um dos ramificações na declaração de `switch` . Diferentemente de instrução de `switch` em que uma ramificação é executado em com base em um valor, a atividade de <xref:System.Activities.Statements.Pick> executa uma ramificação com base em como uma atividade completa.  
  
 Este exemplo solicita um usuário a digite seu nome no console em um período de tempo especificado. A atividade de <xref:System.Activities.Statements.Pick> no exemplo tem duas ramificações de que são executados com base na se o usuário digita em seu nome dentro de 5 segundos ou não. Se o usuário digita em seu nome dentro de 5 segundos, o primeiro ramificação será executado, que contém uma atividade personalizado de `ReadLine` ; se não a outra ramificação é executado, que contém uma atividade de <xref:System.Activities.Statements.Delay> . Uma vez que um nome de usuário é digitado no console, o nome de usuário é impresso no console. Se uma entrada não é inserido em 5 segundos, a operação é esgotado.  
  
## <a name="demonstrates"></a>Demonstra  
 atividade de<xref:System.Activities.Statements.Pick> .  
  
## <a name="discussion"></a>Discussão  
 O exemplo inclui um fluxo de trabalho do designer e fluxo de trabalho codificado.  
  
 Fluxo de trabalho do designer  
 A versão de designer exemplo demonstra como criar um fluxo de trabalho no designer. Os seguintes arquivos estão incluídos:  
  
-   Module.vb: Inclui a função de `Main` que executa o fluxo de trabalho de exemplo.  
  
-   ReadString.cs: Uma atividade personalizado que lê algumas entradas de console.  
  
-   Sequence1.xaml: Um fluxo de trabalho criado usando o designer que usa a picareta.  
  
 Fluxo de trabalho codificado  
 A versão codificado de exemplo demonstra como criar um fluxo de trabalho no designer. Os seguintes arquivos estão incluídos:  
  
-   Module.vb: Inclui a função de `Main` que executa o fluxo de trabalho de exemplo.  
  
-   ReadString.cs: Uma atividade personalizado que lê algumas entradas de console.  
  
#### <a name="to-use-this-sample"></a>Para usar este exemplo  
  
1.  Usando [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], abra o arquivo de solução de Pick.sln.  
  
2.  Para criar a solução, pressione CTRL+SHIFT+B.  
  
3.  Para executar a solução, pressione F5.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\Pick`