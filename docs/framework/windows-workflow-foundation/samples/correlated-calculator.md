---
title: Calculadora correlacionada
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c365166e-6552-49a4-bf17-9f4e597d4d41
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 53d96e090edabc65b7356497c3726d29e46c4ea7
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/28/2017
---
# <a name="correlated-calculator"></a>Calculadora correlacionada
Este exemplo demonstra como usar as atividades de mensagens (<xref:System.ServiceModel.Activities.Receive> e <xref:System.ServiceModel.Activities.SendReply>) no designer com correlação conteudo com base em um parâmetro na mensagem. Nesse cenário, o funcionamento da calculadora estão em um trem paralelo. Uma instância e uma correlação (com base em `CalculatorId`) são criadas quando a primeira mensagem é enviada para o fluxo de trabalho, e mensagens subsequentes com a mesma `CalculatorId` são distribuídos a essa instância até que a operação de redefinição é chamada. O cliente é implementado como um aplicativo de WPF que usa um proxy código baseado de cliente para se comunicar com o serviço.  
  
#### <a name="to-use-this-sample"></a>Para usar este exemplo  
  
1.  Inicie [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] em permissões elevadas, abra o arquivo de solução de For.sln.  
  
    1.  Navegue até a pasta que contém [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
    2.  Devenv.exe e selecione **executar como administrador**.  
  
2.  Usando [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], abra o arquivo de solução de CorrelatedCalculator.sln.  
  
3.  Para criar a solução, pressione CTRL+SHIFT+B.  
  
4.  Para executar o projeto de serviço, pressione CTRL+F5.  
  
5.  Uma vez que o serviço está pronto e escutar mensagens, em Solution Explorer, clique com o botão direito do mouse no projeto do cliente e executá-lo.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\CorellatedCalculator`