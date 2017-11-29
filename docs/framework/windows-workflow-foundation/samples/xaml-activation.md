---
title: "Ativação de XAML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 486760e2-bb10-4ed5-8c02-fe7472498d2d
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f513b10c84de968d5a18b800037b512aad90399e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="xaml-activation"></a>Ativação de XAML
Este exemplo demonstra como hospedar um fluxo de trabalho declarativo no IIS. O exemplo é um fluxo de trabalho básico chamado `EchoService` que tenha uma operação.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existe, vá (página de download) baixar todos os exemplos de [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e de [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\XAMLActivation`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Abra a solução de XAMLActivation.sln em [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Compile a solução pressionando **F5**.  
  
3.  Execução WcfTestClient.exe. Do prompt de comando, digite o seguinte:  
  
    1.  CD %SystemDrive% \ program files \ Microsoft Visual Studio 10.0 \ Common7 \ IDE  
  
    2.  Execução WcfTestClient.exe.  
  
4.  Defina o endereço de serviço em WcfTestClient.exe pressionando CTRL+SHIFT+A e definindo o endereço de serviço a http://localhost:56133/Service.xamlx.  
  
5.  Executar a operação de eco para testar o serviço.  
  
6.  Implantar o serviço no IIS usando DeployToIIS.Bat em um prompt de comando com privilégios de administrador.  
  
7.  Atualizar o endereço do serviço no cliente a http://localhost/XAMLActivation/Service.xamlx e testar o serviço que usa novamente WcfTestClient.exe.
