---
title: 'Compilando os exemplos do Windows Communication Foundation '
ms.date: 03/30/2017
ms.assetid: 2899e7a5-9cb2-4e8d-b8d2-f31391549198
ms.openlocfilehash: 46f4015c00916a5cab932e8fd2539c7c86588a30
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43565780"
---
# <a name="building-the-windows-communication-foundation-samples"></a>Compilando os exemplos do Windows Communication Foundation 

Os exemplos do Windows Communication Foundation (WCF) podem ser criados usando o IDE do Visual Studio ou usando o **msbuild** comando da linha de comando. Ambos os procedimentos são descritos neste tópico.

> [!NOTE]
> Antes de criar ou executar qualquer um dos exemplos do WCF, verifique se você executou o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).

## <a name="to-build-the-sample-using-a-command-prompt"></a>Para criar o exemplo usando um prompt de comando

1.  Abra o Prompt de comando do desenvolvedor para Visual Studio e navegue até o subdiretório específico do idioma em que o local do diretório onde você instalou o exemplo.

2.  Tipo `msbuild` na linha de comando. Os arquivos de programa do cliente são incorporados *client\bin* e os arquivos de programa de serviço são criados para *service\bin*. Se o serviço é hospedado pelo Internet Information Services (IIS), os arquivos de programa de serviço também são copiados para o *servicemodelsamples* diretório e seu *\bin* subdiretório.

> [!NOTE]
> Você deve definir as ACLs no *%systemdrive%\inetpub\wwwroot* para conceder permissões de modificação para a conta sob a qual você está executando. Caso contrário, alguns lançar falha de eventos de build. Como alternativa, você pode deixar as ACLs que são e executar o prompt de comando do SDK como administrador.

## <a name="to-build-the-sample-using-visual-studio"></a>Para criar o exemplo usando Visual Studio

1. Dos **arquivo** menu no Visual Studio, selecione **abra** > **projeto/solução**. Navegue até o subdiretório específico do idioma sob o diretório no qual você instalou o exemplo e clique duas vezes no ícone do arquivo. sln para abrir a solução no Visual Studio.

1. Dos **construir** menu, selecione **recompilar solução**.

   Os arquivos de programa do cliente são criados para client\bin e os arquivos de programa de serviço são criados para service\bin. Se o serviço está hospedado no IIS, os arquivos de programa de serviço também são copiados para o *servicemodelsamples* diretório e seu *\bin* subdiretório.

> [!NOTE]
> Você deve definir as ACLs no %systemdrive%\inetpub\wwwroot para conceder permissões de modificação para a conta sob a qual você está executando. Caso contrário, alguns lançar falha de eventos de build. Como alternativa, você pode deixar as ACLs que são e executar o prompt de comando do SDK ou o Visual Studio como administrador. Algumas ações do Visual Studio (como anexar um depurador ao processo de trabalho ASP.Net) também exigem privilégios administrativos.

## <a name="setup-batch-files-and-scripts"></a>Arquivos em lotes e Scripts de instalação
 Scripts e arquivos de lote Setup.exe e Cleanup.exe devem ser executados no Prompt de comando do desenvolvedor para Visual Studio. Vários conjunto de backup e limpeza dos arquivos de executar tarefas que exigem privilégios administrativos e devem ser iniciadas com privilégios de administrador.

## <a name="important-security-information-about-metadata-endpoints"></a>Informações de segurança importantes sobre pontos de extremidade de metadados
 Para evitar a divulgação acidental de metadados de serviço potencialmente confidenciais, a configuração padrão para serviços Windows Communication Foundation (WCF) desabilita a publicação de metadados. Esse comportamento é seguro por padrão, mas também significa que você não pode usar metadados importar ferramenta (como Svcutil.exe) para gerar o código de cliente necessário para chamar o serviço, a menos que o comportamento de publicação de metadados do serviço é explicitamente habilitado na configuração. Para fazer experiências com os exemplos mais fácil, quase todos os exemplos de expõem um ponto de extremidade de publicação de metadados não segura. Esses pontos de extremidade estão potencialmente disponíveis para os consumidores não autenticados anônimos e tome cuidado antes de implantar esses pontos de extremidade para garantir que publicamente divulga metadados de um serviço são apropriado. Para obter mais informações sobre como publicar metadados de serviço, consulte o [comportamento de publicação de metadados](../../../../docs/framework/wcf/samples/metadata-publishing-behavior.md) exemplo. Consulte a [ponto de extremidade do personalizado proteger metadados](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md) exemplo para obter um exemplo de proteger um ponto de extremidade de metadados.

## <a name="exception-handling"></a>Tratamento de Exceção
 Em termos gerais esses exemplos não incluem o tratamento de exceções para manter o código com foco no assunto da amostra. Para obter mais informações sobre o tratamento de exceção, consulte o [esperado exceções](../../../../docs/framework/wcf/samples/expected-exceptions.md) exemplo.

## <a name="regenerating-clients-and-configuration-with-svcutil"></a>Regenerando os clientes e a configuração com Svcutil
 Você pode usar o [ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) para gerar novamente o código de cliente e a configuração para a maioria dos exemplos. Alguns exemplos exigem configuração editada manualmente. Por exemplo, se você usar Svcutil.exe para gerar novamente a configuração para obter um exemplo que usa as credenciais de certificado do cliente, você deve especificar manualmente as credenciais configuradas anteriormente. Alguns exemplos de usam opções específicas de Svcutil.exe para afetar o código gerado, essas opções são especificadas nos tópicos de exemplo específicos.

### <a name="to-regenerate-the-client-and-configuration-files"></a>Para gerar novamente os arquivos de configuração e de cliente

1.  Abra um prompt de comando do SDK e navegue até o subdiretório específico do idioma em que o local do diretório onde você instalou o exemplo.

2.  Se o serviço for um tipo hospedados na Web, use o comando a seguir.

    ```
    svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /out:generatedClient.cs
    ```

     Se o serviço é um tipo auto-hospedado o comando a seguir.

    ```
    svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost:8000/servicemodelsamples/service.svc/mex /out:generatedClient.cs
    ```

     Substitua http://localhost:8000/ServiceModelSamples/service.svc/mex com o endereço do ponto de extremidade de mex do serviço auto-hospedado.

     Para gerar o cliente em um tipo de Visual Basic, use o comando a seguir.

    ```
    svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /l:vb /out:generatedClient.vb
    ```

     Se o serviço for um tipo auto-hospedado, use o comando a seguir.

    ```
    svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost:8000/servicemodelsamples/service.svc/mex /l:vb /out:generatedClient.vb
    ```

    > [!NOTE]
    > Para ignorar a geração de configuração do cliente, adicione a **/noConfig** opção.

## <a name="see-also"></a>Consulte também

- [Executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md)
- [Ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
