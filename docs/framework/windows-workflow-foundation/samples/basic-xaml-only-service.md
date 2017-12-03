---
title: "Serviço básico XAML apenas"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c106feb0-0245-43b5-aefe-93ce0e4d38eb
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 06a302b13db3b82dabb43989ac272df0d9aac008
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="basic-xaml-only-service"></a>Serviço básico XAML apenas
Este exemplo demonstra como criar um serviço XAML somente. O cenário é um serviço de diagnóstico para carro- problemas relacionados. O serviço é implementado como um fluxo de trabalho que faz a um cliente a série de perguntas diagnosticar o problema. Há dois tipos de problemas que o serviço pode diagnosticar (o carro não inicia ou o ar condicionamento que não funciona). O modelo solicitação/resposta usos de fluxo de trabalho de designer expor três operações de serviço simples. O serviço está hospedado no IIS criando um diretório virtual no IIS e copiando o service1.xamlx e os arquivos web.config no diretório virtual, nenhum código compilado é necessário. Por padrão Este exemplo copiará automaticamente os arquivos necessários para o diretório virtual criado quando você seguir as instruções de instalação para os exemplos do WCF e WF: [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) quando compilado no Visual Studio 2010.  
  
#### <a name="to-use-this-sample"></a>Para usar este exemplo  
  
1.  Carregar a solução do projeto em [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] e compile o projeto.  
  
2.  Executam aplicativo cliente gerado em [] do diretório da solução cliente \ \ bin \ debug.  
  
3.  As cópias do aplicativo - out as opções, selecione uma opção. O aplicativo faz em algumas questões, responde-lhes sim ou nenhum (usando chaves de Y/N). Quando o serviço é feito que diagnostica problemas, o aplicativo imprime para fora um diagnóstico.  
  
4.  O aplicativo volta em padrões. Você pode diagnosticar outro problema ou sair do aplicativo.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\XAMLService`