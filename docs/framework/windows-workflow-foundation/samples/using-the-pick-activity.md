---
title: Usando a atividade de picareta
ms.date: 03/30/2017
ms.assetid: b89be812-a247-4025-b0e3-ffb20db027a6
ms.openlocfilehash: 7ca4527cc1d5bc90ed1ec4df3eef6cf2d8b93b4e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142609"
---
# <a name="using-the-pick-activity"></a>Usando a atividade de picareta
Este exemplo demonstra como usar a atividade de <xref:System.Activities.Statements.Pick> .

 A atividade de <xref:System.Activities.Statements.Pick> fornece a modelagem com base em eventos do controle. Se comporta semelhante à declaração C# `switch` , que executa somente um dos ramificações na declaração de `switch` . Diferentemente de instrução de `switch` em que uma ramificação é executado em com base em um valor, a atividade de <xref:System.Activities.Statements.Pick> executa uma ramificação com base em como uma atividade completa.

 Este exemplo solicita um usuário a digite seu nome no console em um período de tempo especificado. A atividade de <xref:System.Activities.Statements.Pick> no exemplo tem duas ramificações de que são executados com base na se o usuário digita em seu nome dentro de 5 segundos ou não. Se o usuário digita em seu nome dentro de 5 segundos, o primeiro ramificação será executado, que contém uma atividade personalizado de `ReadLine` ; se não a outra ramificação é executado, que contém uma atividade de <xref:System.Activities.Statements.Delay> . Uma vez que um nome de usuário é digitado no console, o nome de usuário é impresso no console. Se uma entrada não é inserido em 5 segundos, a operação é esgotado.

## <a name="demonstrates"></a>Demonstra
 atividade de<xref:System.Activities.Statements.Pick> .

## <a name="discussion"></a>Discussão
 O exemplo inclui um fluxo de trabalho do designer e fluxo de trabalho codificado.

 Fluxo de trabalho do designer A versão designer da amostra demonstra como criar um fluxo de trabalho no designer. Os seguintes arquivos estão incluídos:

- Module.vb: Inclui a função de `Main` que executa o fluxo de trabalho de exemplo.

- ReadString.cs: Uma atividade personalizado que lê algumas entradas de console.

- Sequence1.xaml: Um fluxo de trabalho criado usando o designer que usa a picareta.

 Fluxo de trabalho codificado A versão codificada da amostra demonstra como criar um fluxo de trabalho no designer. Os seguintes arquivos estão incluídos:

- Module.vb: Inclui a função de `Main` que executa o fluxo de trabalho de exemplo.

- ReadString.cs: Uma atividade personalizado que lê algumas entradas de console.

#### <a name="to-use-this-sample"></a>Para usar este exemplo

1. Usando o Visual Studio 2010, abra o arquivo de solução Pick.sln.

2. Para criar a solução, pressione CTRL+SHIFT+B.

3. Para executar a solução, pressione F5.

> [!IMPORTANT]
> Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation). Este exemplo está localizado no seguinte diretório.  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\Pick`
