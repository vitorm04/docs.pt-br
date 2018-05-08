---
title: Ativação de XAML
ms.date: 03/30/2017
ms.assetid: 486760e2-bb10-4ed5-8c02-fe7472498d2d
ms.openlocfilehash: 8621b0ea7b390c81e76ac7eeedb0b547b44320d7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="xaml-activation"></a>Ativação de XAML
Este exemplo demonstra como hospedar um fluxo de trabalho declarativo no IIS. O exemplo é um fluxo de trabalho básico chamado `EchoService` que tenha uma operação.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para (página de download) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\XAMLActivation`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Abra a solução de XAMLActivation.sln em [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Compile a solução pressionando **F5**.  
  
3.  Execução WcfTestClient.exe. Do prompt de comando, digite o seguinte:  
  
    1.  CD %SystemDrive% \ program files \ Microsoft Visual Studio 10.0 \ Common7 \ IDE  
  
    2.  Execução WcfTestClient.exe.  
  
4.  Definir o endereço do serviço em WcfTestClient.exe pressionando CTRL + SHIFT + A e definir o endereço do serviço como http://localhost:56133/Service.xamlx.  
  
5.  Executar a operação de eco para testar o serviço.  
  
6.  Implantar o serviço no IIS usando DeployToIIS.Bat em um prompt de comando com privilégios de administrador.  
  
7.  Atualize o endereço de serviço no cliente para http://localhost/XAMLActivation/Service.xamlx e testar o serviço novamente usando WcfTestClient.exe.
