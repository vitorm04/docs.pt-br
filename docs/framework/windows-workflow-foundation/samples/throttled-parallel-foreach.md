---
title: Paralelo estrangulado ForEach
ms.date: 03/30/2017
ms.assetid: f2855b5f-e9a7-433d-96a4-40fc31025215
ms.openlocfilehash: 8691edb8a5a61204b187be8def553f2f06be0f0d
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48581856"
---
# <a name="throttled-parallel-foreach"></a>Paralelo estrangulado ForEach
O `ThrottleParallelForEach` atividade é semelhante de <!--zz <xref:System.Activities.Statements.ParallelForEach>--> `System.Activities.Statements.ParallelForEach` atividade com uma exceção que permite que define um fator de simultaneidade para restringir o número de ramificações simultâneas para executar. A atividade de `ThrottleParallelForEach` deriva de <xref:System.Activities.NativeActivity>, porque precisa agendar outras atividades (as atividades filho) e isso é acessível somente por meio da classe <xref:System.Activities.NativeActivityContext> .

## <a name="projects"></a>Projetos

|**ProjectName**|**Descrição**|**Arquivos principais**|
|-|-|-|
|ThrottledParallelForEach|Contém a atividade de `ThrottledParallelForEach` e o designer.|ThrottledParallelForEach.cs<br /><br /> A definição de atividade de `ThrottledParallelForEach` .|
|CodeTestClient|Exemplo do aplicativo cliente que configura e executa um fluxo de trabalho com `ThrottledParallelForEach` usando o código obrigatório.|Module.vb<br /><br /> Define e executa uma instância de fluxo de trabalho de exemplo.|

#### <a name="to-use-this-sample"></a>Para usar este exemplo

1.  Usando o Visual Studio 2010, abra o arquivo de Throttledparallelforeach.

2.  Para criar a solução, pressione CTRL+SHIFT+B.

3.  Para executar a solução, pressione F5.

> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\ThrottledParallelForEach`