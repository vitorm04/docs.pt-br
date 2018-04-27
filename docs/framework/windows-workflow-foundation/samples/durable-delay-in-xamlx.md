---
title: Atraso durável em XAMLX
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: efc38df4-2d34-453c-8e59-2c21d1307354
caps.latest.revision: 7
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8fa5a9e4287bcbcb490754b84a8b5060d321f779
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2018
---
# <a name="durable-delay-in-xamlx"></a>Atraso durável em XAMLX
Este exemplo demonstra como usar um atraso durável, que é um atraso que persiste o fluxo de trabalho para um dispositivo durável durante o atraso.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\DurableDelayXamlx`  
  
## <a name="discussion"></a>Discussão  
 O fluxo de trabalho de exemplo contém duas mensagens em um arquivo local que são separadas por um atraso. Quando o atraso é disparado, o trabalho são descarregados e esperam 5 segundos no armazenamento de instância de trabalho antes de ser recarregado na memória.  
  
 O arquivo .xamlx é um serviço de fluxo de trabalho que está hospedado no Visual Studio. O Visual Studio usa Cassini que usa um serviço de fluxo de trabalho de host para host de fluxo de trabalho.  
  
 Além de hospedar o trabalho, o host serviço de trabalho gerencia as instâncias de fluxo de trabalho carregar e descarregando as. Para iniciar uma instância da definição do Windows Workflow Foundation (WF) (no host do serviço de fluxo de trabalho), defina um cliente que envia uma mensagem para o <xref:System.ServiceModel.Activities.Receive> atividade no fluxo de trabalho. Este <xref:System.ServiceModel.Activities.Receive> tem sua propriedade de <xref:System.ServiceModel.Activities.Receive.CanCreateInstance%2A> definida como `true`, permitindo que você criar uma nova instância de fluxo de trabalho uma vez que recebe uma mensagem.  
  
 Durante a inicialização, um comportamento de instância de unload é adicionado ao arquivo de configuração que especifica ao host serviço de fluxo de trabalho em que deve descarregar uma instância no armazenamento de persistência (base de dados). Para esse exemplo, descarrega a instância imediatamente após o fluxo de trabalho aparece ociosa (quando o atraso é disparado).  
  
#### <a name="to-use-this-sample"></a>Para usar este exemplo  
  
1.  Abra um prompt de comando do [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Navegue até a pasta de DurableDelayXamlx \ CS.  
  
3.  Executar Setup.cmd.  
  
4.  Execução [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] como um administrador.  
  
5.  Abra o arquivo de solução de DurableDelayXamlx.sln.  
  
6.  Em **Solution Explorer**, a solução e selecione **propriedades**.  
  
7.  Selecione **vários projetos de inicialização** e defina os dois projetos como **iniciar**.  
  
8.  Para criar a solução, pressione CTRL+SHIFT+B.  
  
9. Para executar a solução, pressione CTRL+F5.  
  
#### <a name="to-uninstall-this-sample"></a>Para desinstalar este exemplo  
  
1.  Abra um prompt de comando do [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Navegue até a pasta de DurableDelayXamlx \ CS.  
  
3.  Execução Cleanup.cmd.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\DurableDelayXamlX`
