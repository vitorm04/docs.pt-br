---
title: InvokeMethod
ms.date: 03/30/2017
ms.assetid: 04988eb3-65f8-456d-b1bd-509f5d05a57c
ms.openlocfilehash: 861e0cf160aec9814abcf8c27c37ce13a5d88b2a
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44047705"
---
# <a name="invokemethod"></a>InvokeMethod
Este exemplo mostra as diferentes maneiras de usar a atividade de <xref:System.Activities.Statements.InvokeMethod> para chamar métodos de uma classe.  
  
 Um método pertence a uma classe e representa um conjunto contido de operações. A atividade de <xref:System.Activities.Statements.InvokeMethod> oferece a você a capacidade de chamar métodos contra objetos, ou tipos de passar os parâmetros, e para obter o valor de retorno. Os métodos podem ser chamados de forma síncrona ou de forma assíncrona.  
  
## <a name="sample-details"></a>Detalhes de exemplo  
 Este exemplo usa a atividade de <xref:System.Activities.Statements.InvokeMethod> para executar os seguintes situações:  
  
1.  Chamar um método de instância sem parâmetros.  
  
2.  Chamar um método de instância com dois parâmetros (<xref:System.String> e <xref:System.Int32>).  
  
3.  Chamar um método de instância com dois parâmetros (<xref:System.String> e <xref:System.Int32>) e uma matriz de parâmetros de tipo <xref:System.String>[].  
  
4.  Chamar um método de instância com dois parâmetros de tipo <xref:System.Int32> e um resultado de tipo <xref:System.Int32>. Nesse cenário, o valor do resultado é associado a uma variável e usado em outra atividade. É exibido no console usando a atividade de <xref:System.Activities.Statements.WriteLine> .  
  
5.  Chamar um método estático com dois parâmetros de tipo <xref:System.String> e <xref:System.Int32>.  
  
6.  Chamar um método de instância com um parâmetro de tipo genérico <xref:System.String>.  
  
7.  Chamar um método estático com dois parâmetros de tipo genéricos <xref:System.String> e <xref:System.Int32>.  
  
8.  Chamar um método de instância que tem um parâmetro passado por referência de tipo <xref:System.String>. Nesse cenário, o parâmetro de referência é associado a uma variável (`outParam`) e usado em outra atividade. É exibido no console usando a atividade de <xref:System.Activities.Statements.WriteLine> .  
  
9. Chamar um método de instância assíncrono.  
  
10. Chamar dois diferentes métodos na mesma instância de um objeto usando duas atividades de <xref:System.Activities.Statements.InvokeMethod> .  
  
11. Armazenar um valor em uma instância de um objeto.  
  
12. Recuperar um valor de uma instância de um objeto.  
  
## <a name="to-use-this-sample"></a>Para usar este exemplo  
 Este exemplo é fornecido em duas versões. A primeira versão deste exemplo demonstra o uso de <xref:System.Activities.Statements.InvokeMethod> por meio do c# o código usando o modelo de programação do Windows Workflow Foundation (WF) e pode ser encontrado na pasta de codedworkflow \ CS. A segunda versão demonstra o uso de <xref:System.Activities.Statements.InvokeMethod> usando XAML e pode ser encontrada na pasta de DesignerWorkflow \ CS.  
  
#### <a name="to-run-the-coded-workflow-sample"></a>Para executar o exemplo codificado de fluxo de trabalho  
  
1.  Usando [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], abra o arquivo de solução de InvokeMethodUsage.sln na pasta de CodedWorkflow \ CS.  
  
2.  Para criar a solução, pressione CTRL+SHIFT+B.  
  
3.  Para executar a solução, pressione CTRL+F5.  
  
#### <a name="to-run-the-designer-workflow-sample"></a>Para executar o exemplo de fluxo de trabalho do designer  
  
1.  Usando [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], abra o arquivo de solução de InvokeMethodUsage.sln na pasta de DesignerWorkflow \ CS.  
  
2.  Para criar a solução, pressione CTRL+SHIFT+B.  
  
3.  Para executar a solução, pressione CTRL+F5.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\InvokeMethod`