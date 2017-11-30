---
title: 'Compilando os exemplos do Windows Communication Foundation '
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2899e7a5-9cb2-4e8d-b8d2-f31391549198
caps.latest.revision: "33"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: efb45a09fd74d397ceb95fc7e1bad7a0a5f80309
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="building-the-windows-communication-foundation-samples"></a>Compilando os exemplos do Windows Communication Foundation 
O [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] exemplos podem ser criados usando o Visual Studio 2010 ou usando o **msbuild** comando da linha de comando. Ambos os procedimentos são descritos neste tópico.  
  
> [!NOTE]
>  Antes de criar ou executar qualquer uma da [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] exemplos, verifique se você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
### <a name="to-build-the-sample-using-a-command-prompt"></a>Para criar o exemplo usando um prompt de comando  
  
1.  Abra o [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] prompt com privilégios de administrador de comando e navegue até o subdiretório específico do idioma em que o local do diretório onde você instalou o exemplo.  
  
2.  Tipo `msbuild` na linha de comando. Os arquivos de programa do cliente são criados para client\bin e os arquivos de programa de serviço são criados para service\bin. Se o serviço é hospedado por serviços de informações da Internet (IIS), os arquivos de programa de serviço também são copiados para o diretório servicemodelsamples e seu subdiretório \bin.  
  
> [!NOTE]
>  Você deve definir as ACLs no %systemdrive%\inetpub\wwwroot para conceder permissões de modificação para a conta sob a qual você está executando. Caso contrário, alguns após falha de eventos de compilação. Como alternativa, você pode deixar as ACLs que são e executar o prompt de comando do SDK como administrador.  
  
### <a name="to-build-the-sample-using-visual-studio"></a>Para criar o exemplo usando Visual Studio  
  
1.  Se você estiver usando [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[lserver](../../../../includes/lserver-md.md)], Windows 7 ou Windows Server 2008 R2 e execução [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], você deve executar [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] com permissão elevada. Para fazer isso, clique no ícone do menu Iniciar e, em seguida, clique em **executar como administrador**.  
  
2.  Do **arquivo** menu no [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)], clique em **abrir**, em seguida, clique em **projeto/solução**. Navegue até o subdiretório específico do idioma sob o diretório no qual você instalou o exemplo e clique duas vezes no ícone do arquivo. sln para abrir a solução em [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)].  
  
3.  No **criar** menu, selecione **recompilar solução**. Os arquivos de programa do cliente são criados para client\bin e os arquivos de programa de serviço são criados para service\bin. Se o serviço está hospedado no IIS, os arquivos de programa de serviço também são copiados para o diretório servicemodelsamples e seu subdiretório \bin.  
  
> [!NOTE]
>  Você deve definir as ACLs no %systemdrive%\inetpub\wwwroot para conceder permissões de modificação para a conta sob a qual você está executando. Caso contrário, alguns após falha de eventos de compilação. Como alternativa, você pode deixar as ACLs que são e executam o prompt de comando do SDK ou o Visual Studio como administrador. Algumas ações do Visual Studio (como anexar um depurador ao processo de trabalho do ASP.Net) também exigem privilégios administrativos.  
  
## <a name="setup-batch-files-and-scripts"></a>Arquivos em lotes e Scripts de instalação  
 Scripts e arquivos de lote de Setup.exe e Cleanup.exe devem ser executados em um prompt de comando do Visual Studio. Vários conjunto de backup e limpar arquivos executam tarefas que exigem privilégios administrativos e devem ser iniciadas com privilégios de administrador.  
  
## <a name="important-security-information-about-metadata-endpoints"></a>Informações de segurança importantes sobre pontos de extremidade de metadados  
 Para evitar a divulgação acidental de metadados de serviço potencialmente confidenciais, a configuração padrão para [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] serviços desabilita a publicação de metadados. Esse comportamento é seguro por padrão, mas também significa que você não pode usar metadados importa ferramenta (como Svcutil.exe) para gerar o código de cliente necessário para chamar o serviço, a menos que o comportamento de publicação de metadados do serviço é explicitamente habilitado na configuração. Para fazer experiências com os exemplos mais fácil, quase todos os exemplos de expõem um ponto de extremidade de publicação de metadados não segura. Esses pontos de extremidade são potencialmente disponíveis para consumidores não autenticados anônimos e deve ter cuidado antes de implantar esses pontos de extremidade para garantir que publicamente destinatária metadados do serviço são apropriado. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]publicação de metadados de serviço, consulte o [comportamento de publicação de metadados](../../../../docs/framework/wcf/samples/metadata-publishing-behavior.md) exemplo. Consulte o [personalizado proteger metadados de ponto de extremidade](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md) exemplo para obter um exemplo de proteção de um ponto de extremidade de metadados.  
  
## <a name="exception-handling"></a>Tratamento de Exceção  
 Em termos gerais esses exemplos não incluem o tratamento de exceções para manter o foco no assunto do exemplo de código. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]tratamento de exceção, consulte o [esperado exceções](../../../../docs/framework/wcf/samples/expected-exceptions.md) exemplo.  
  
## <a name="regenerating-clients-and-configuration-with-svcutil"></a>Regenerando os clientes e a configuração com Svcutil  
 Você pode usar o [Ferramenta Utilitária de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) para gerar novamente o código de cliente e de configuração para a maioria dos exemplos. Alguns exemplos exigem configuração editada manualmente. Por exemplo, se você usar o Svcutil.exe para gerar novamente a configuração para obter um exemplo que usa credenciais de certificado de cliente, você deve especificar manualmente as credenciais configuradas anteriormente. Alguns exemplos usam opções específicas do Svcutil.exe para afetar o código gerado, essas opções são especificadas nos tópicos de exemplo específico.  
  
#### <a name="to-regenerate-the-client-and-configuration-files"></a>Para gerar novamente os arquivos de configuração e de cliente  
  
1.  Abra um prompt de comando do SDK e navegue até o subdiretório específico do idioma em que o local do diretório onde você instalou o exemplo.  
  
2.  Se o serviço é um tipo de host da Web, use o comando a seguir.  
  
    ```  
    svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /out:generatedClient.cs  
    ```  
  
     Se o serviço é um tipo auto-hospedado o comando a seguir.  
  
    ```  
    svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost:8000/servicemodelsamples/service.svc/mex /out:generatedClient.cs  
    ```  
  
     Substitua http://localhost:8000/ServiceModelSamples/service.svc/mex com o endereço do ponto de extremidade do serviço auto-hospedado mex.  
  
     Para gerar o cliente em um tipo de Visual Basic, use o comando a seguir.  
  
    ```  
    svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /l:vb /out:generatedClient.vb  
    ```  
  
     Se o serviço é um tipo auto-hospedado, use o comando a seguir.  
  
    ```  
    svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost:8000/servicemodelsamples/service.svc/mex /l:vb /out:generatedClient.vb  
    ```  
  
    > [!NOTE]
    >  Para ignorar a geração de configuração do cliente, adicione o **/noConfig** opção.  
  
## <a name="see-also"></a>Consulte também  
 [Executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md)  
 [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) [Ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)]
