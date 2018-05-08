---
title: Atividade de RangeEnumeration
ms.date: 03/30/2017
ms.assetid: ca5b78f4-94fa-4aa7-830d-26039ac422c8
ms.openlocfilehash: 9aa04c80f20e2d410fb49e2d07d836c8c5ab1b4d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="rangeenumeration-activity"></a>Atividade de RangeEnumeration
Este exemplo demonstra como criar uma atividade personalizado que executa iterações sobre uma coleção de números. A tabela a seguir detalha os arquivos de chave incluídos no exemplo.  
  
|Nome do arquivo|Descrição|  
|---------------|-----------------|  
|RangeEnumeration.cs|Define uma atividade personalizada chamada `RangeEnumeration` que substitui a classe e loops de <xref:System.Activities.NativeActivity> com uma série de números.|  
|RangeEnumerationSample.cs|Um aplicativo cliente que usa a atividade de `RangeEnumeration` para iterar sobre uma coleção de números.|  
  
 A tabela a seguir detalha as propriedades de atividade de `RangeEnumeration` .  
  
|Propriedade|Descrição|  
|--------------|-----------------|  
|Início|O inteiro para iniciar o loop do.|  
|Stop|O inteiro para parar no loop.|  
|Etapa|Especifica quanto para iterar cada vez.|  
|Corpo|Especifica o código para executar durante cada iteração.|  
  
#### <a name="to-use-this-sample"></a>Para usar este exemplo  
  
1.  Usando [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], abra o arquivo de solução de RangeEnumeration.sln.  
  
2.  Para criar a solução, pressione CTRL+SHIFT+B.  
  
3.  Para executar a solução, pressione CTRL+F5.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\RangeEnumeration`