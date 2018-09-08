---
title: Para atividades
ms.date: 03/30/2017
ms.assetid: 2ea751b4-36f0-48aa-a115-70a2ab89f6d8
ms.openlocfilehash: 7a7023abb9057ab4b25552fbf9a81cd2ae2b4e88
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44131744"
---
# <a name="for-activity"></a>Para atividades
Para o exemplo demonstra como criar uma atividade personalizado que herda de <xref:System.Activities.NativeActivity>, e usá-lo em um fluxo de trabalho para executar um exemplo do mundo real. A atividade personalizado incluída nas funções deste exemplo desejar da declaração C# `for` . T  
  
 A atividade personalizado de `For` tem propriedades chamadas `InitAction`, `IterationAction`, `Condition`, e `Body` que correspondem à declaração de inicialização, a instrução iterativa, a condição de continuação de linha, e a declaração do corpo respectivamente localizada na instrução padrão de C# `For` .  
  
 A tabela a seguir descreve os arquivos de chave no exemplo.  
  
|Arquivo|Descrição|  
|----------|-----------------|  
|For.cs|Definição de classe para atividades personalizado de `For` , que estende a classe de <xref:System.Activities.NativeActivity> para fornecer funcionalidade da declaração C# `For` .|  
|Module.vb|Um aplicativo cliente que executa o trabalho iterativo básico em uma coleção usando a atividade personalizado de `For` .|  
  
> [!NOTE]
>  Ao usar a atividade de `For` personalizado, certifique-se de que a propriedade de `Condition` é definida; se não um loop infinito pode ocorrer.  
  
## <a name="demonstrates"></a>Demonstra  
 Crie uma atividade personalizado que herda de <xref:System.Activities.NativeActivity>.  
  
## <a name="discussion"></a>Discussão  
 A tabela a seguir descreve as propriedades de atividade incluída neste exemplo.  
  
 InitAction  
 Declaração de inicialização  
  
 IterationAction  
 Instrução iterativa  
  
 Condição  
 Declaração de continuação de linha  
  
 Corpo  
 Instrução do corpo  
  
 A atividade herda de <xref:System.Activities.NativeActivity> para conceder acesso aos recursos de tempo de execução como agendar atividades adicionais para executar, usando um dos métodos de `ScheduleActivity` de <xref:System.Activities.NativeActivityContext>.  
  
#### <a name="to-use-this-sample"></a>Para usar este exemplo  
  
1.  Usando [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], abra o arquivo de solução de For.sln.  
  
2.  Crie a solução, pressionando CTRL+SHIFT+B.  
  
3.  Executar a solução, pressionando F5.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\For`