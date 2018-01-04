---
title: "Como instalar e configurar componentes de ativação do WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: HTTP activation [WCF]
ms.assetid: 33a7054a-73ec-464d-83e5-b203aeded658
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 78c63fe58872097058292a8b100b376959a2a0b2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-install-and-configure-wcf-activation-components"></a>Como instalar e configurar componentes de ativação do WCF
Este tópico descreve as etapas necessárias para configurar o serviço de ativação de processos do Windows (também conhecido como WAS) em [!INCLUDE[wv](../../../../includes/wv-md.md)] host [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] protocolos de rede de serviços que não se comunicam por HTTP. As seções a seguir descrevem as etapas para essa configuração:  
  
-   Instalar (ou confirmar a instalação de) o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] componentes de ativação.  
  
-   Configure o WAS para oferecer suporte a um protocolo diferente de HTTP. O procedimento a seguir configura [!INCLUDE[wv](../../../../includes/wv-md.md)] para ativação TCP.  
  
 Depois de instalar e configurar o WAS, consulte [como: hospedar um serviço WCF em WAS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md) para os procedimentos para criar um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço que expõe um ponto de extremidade HTTP não utiliza o WAS.  
  
### <a name="to-install-the-wcf-non-http-activation-components"></a>Para instalar os componentes de ativação não HTTP do WCF  
  
1.  Clique o **iniciar** botão e, em seguida, clique em **painel de controle**.  
  
2.  Clique em **programas**e, em seguida, clique em **programas e recursos**.  
  
3.  Sobre o **tarefas** menu, clique em **ativar recursos do Windows ou desativar**.  
  
4.  Localizar o [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] selecione e expanda-o nó.  
  
5.  Selecione o **componentes de ativação não Http WCF** caixa e salvar a configuração.  
  
### <a name="to-configure-the-was-to-support-tcp-activation"></a>Para configurar o WAS para dar suporte à ativação TCP  
  
1.  Para dar suporte à ativação do NET. TCP, o site da Web padrão primeiro deve ser associado a uma porta NET. TCP. Você pode fazer isso usando o Appcmd.exe, que é instalado com o [!INCLUDE[iisver](../../../../includes/iisver-md.md)] conjunto de ferramentas de gerenciamento. Em uma janela de Prompt de comando de nível de administrador, execute o seguinte comando.  
  
    ```  
    %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" -+bindings.[protocol='net.tcp',bindingInformation='808:*']  
    ```  
  
    > [!NOTE]
    >  Esse comando é uma única linha de texto. Este comando adiciona uma associação de site do NET. TCP para o site da Web padrão, escutando na porta TCP 808 com qualquer nome de host.  
  
2.  Embora todos os aplicativos dentro de um site compartilham uma associação de NET. TCP comum, cada aplicativo pode habilitar o suporte do NET. TCP individualmente. Para habilitar o NET. TCP para o aplicativo, execute o seguinte comando em um prompt de comando de nível de administrador.  
  
    ```  
    %windir%\system32\inetsrv\appcmd.exe set app   
    "Default Web Site/<WCF Application>" /enabledProtocols:http,net.tcp  
    ```  
  
    > [!NOTE]
    >  Esse comando é uma única linha de texto. Este comando habilita o /\<*aplicativo WCF*> aplicativo sejam acessados usando ambos os http://localhost*/\<aplicativo WCF >* e net.tcp:// localhost /*\<aplicativo WCF >*.  
  
     Remova a associação de site do NET. TCP adicionado para este exemplo.  
  
     Como uma conveniência, as duas etapas a seguir são implementadas em um arquivo em lotes chamado RemoveNetTcpSiteBinding.cmd localizado no diretório de exemplo.  
  
    1.  Remova NET. TCP da lista de protocolos habilitados, executando o seguinte comando em uma janela de Prompt de comando de nível de administrador.  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set app   
        "Default Web Site/servicemodelsamples<WCF Application>" " /enabledProtocols:http  
        ```  
  
        > [!NOTE]
        >  Esse comando é uma única linha de texto.  
  
    2.  Remova a associação do site NET. TCP, executando o seguinte comando em uma janela de Prompt de comando com privilégios elevados:  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"   
        --bindings.[protocol='net.tcp',bindingInformation='808:*']  
        ```  
  
        > [!NOTE]
        >  Esse comando é uma única linha de texto.  
  
### <a name="to-remove-nettcp-from-the-list-of-enabled-protocols"></a>Para remover o NET. TCP da lista de protocolos habilitados  
  
1.  Para remover o NET. TCP da lista de protocolos habilitados, execute o seguinte comando em uma janela de Prompt de comando de nível de administrador.  
  
    ```  
    %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples<WCF Application>" " /enabledProtocols:http  
    ```  
  
    > [!NOTE]
    >  Esse comando é uma única linha de texto.  
  
### <a name="to-remove-the-nettcp-site-binding"></a>Para remover a associação de site do NET. TCP  
  
1.  Para remover o site do NET. TCP associação execute o seguinte comando em uma janela de Prompt de comando de nível de administrador.  
  
    ```  
    %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"   
    -bindings.[protocol='net.tcp',bindingInformation='808:*']  
    ```  
  
    > [!NOTE]
    >  Esse comando é uma única linha de texto.  
  
## <a name="see-also"></a>Consulte também  
 [Ativação TCP](../../../../docs/framework/wcf/samples/tcp-activation.md)  
 [Ativação de MSMQ](../../../../docs/framework/wcf/samples/msmq-activation.md)  
 [NamedPipe Activation](../../../../docs/framework/wcf/samples/namedpipe-activation.md)  
 [Recursos de hospedagem do Windows Server App Fabric](http://go.microsoft.com/fwlink/?LinkId=201276)
