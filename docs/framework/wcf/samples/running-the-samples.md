---
title: Executando os exemplos do Windows Communication Foundation
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: db8a83da-95c1-4a21-a9d2-48caeb6398ea
caps.latest.revision: "26"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3003c89b0cfcda9866c5b1accd154900bc650454
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="running-the-windows-communication-foundation-samples"></a>Executando os exemplos do Windows Communication Foundation
O [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] exemplos podem ser executados em uma configuração de computador único ou entre computadores. Fornecido, os exemplos estão prontos para execução em um único computador. Em uma configuração entre computadores, é necessário modificar o arquivo de configuração do exemplo. Os procedimentos a seguir explicam como executar um exemplo em configurações do mesmo computador e entre computadores. Observe que há variações nas etapas para serviços hospedados no serviços de informações da Internet (IIS) e os exemplos auto-hospedado. A maioria dos exemplos estão hospedados no IIS; Consulte as informações do Leiame do exemplo para determinar como ele está hospedado.  
  
 Em [!INCLUDE[wv](../../../../includes/wv-md.md)], exemplos que não são hospedados em IIS exigem privilégios elevados para registrar um ouvinte HTTP. sys. Use Httpcfg.exe para registrar os endereços de escuta do serviço com a conta que o serviço está em execução ou iniciar o serviço em um prompt de comando com privilégios de administrador.  
  
> [!NOTE]
>  Antes de criar ou executar qualquer uma da [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] exemplos, certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
### <a name="to-run-the-sample-on-the-same-machine"></a>Para executar o exemplo no mesmo computador  
  
1.  Se o serviço é hospedado pelo IIS, certifique-se de que você pode acessar o serviço usando um navegador, digitando o seguinte endereço: http://localhost/servicemodelsamples/service.svc. Uma página de confirmação deve ser exibida na resposta. Se a página de confirmação não for exibida, consulte [dicas de solução de problemas](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).  
  
2.  Se o serviço é auto-hospedado, execute Service.exe de \service\bin, sob a pasta de idioma específico. Atividade de serviço é exibida na janela do console de serviço.  
  
3.  Executar Client.exe de \Client\Bin.\\, sob a pasta de idioma específico. Atividade do cliente é exibida na janela do console de cliente.  
  
4.  Se o cliente e o serviço não for capazes de se comunicar, consulte [dicas de solução de problemas](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).  
  
### <a name="to-run-the-sample-across-machines"></a>Para executar o exemplo em computadores  
  
1.  Se o serviço está hospedado no IIS:  
  
    1.  No computador do serviço, crie um diretório virtual chamado ServiceModelSamples. O arquivo de lote Setupvroot.bat incluído [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) pode ser usado para criar o diretório de disco e o diretório virtual.  
  
    2.  Copie os arquivos de programa do serviço de %SystemDrive%\Inetpub\wwwroot\servicemodelsamples para o diretório virtual ServiceModelSamples no computador do serviço. Certifique-se de incluir os arquivos no diretório \bin.  
  
    3.  Teste que você pode acessar o serviço do computador cliente usando um navegador.  
  
     Se o serviço é hospedado automaticamente:  
  
    1.  No computador do serviço, crie um diretório para armazenar os arquivos de serviço.  
  
    2.  Copie os arquivos de programa do serviço da pasta \service\bin\, sob a pasta de idioma específico, para a máquina de serviço.  
  
    3.  No arquivo de configuração de serviço, altere o valor do endereço da definição do ponto de extremidade para coincidir com o novo endereço do seu serviço. Substitua todas as referências a "localhost" com um nome de domínio totalmente qualificado no endereço.  
  
    4.  Inicie Service.exe em um prompt de comando.  
  
2.  Copie os arquivos de programa do cliente na pasta \client\bin\, sob a pasta de idioma específico, para o computador cliente.  
  
3.  Defina o endereço do ponto de extremidade.  
  
    1.  Se o serviço não está em execução em uma conta de domínio, abra o arquivo de configuração do cliente e altere o valor do endereço da definição do ponto de extremidade para coincidir com o novo endereço do seu serviço. Substitua todas as referências a "localhost" com um nome de domínio totalmente qualificado no endereço.  
  
    2.  Se o serviço é executado sob uma conta de domínio, gerar novamente a configuração do cliente executando Svcutil.exe em relação ao serviço. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]executando o Svcutil.exe, consulte [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md). Use o arquivo gerado em vez do arquivo de configuração no exemplo. O arquivo de configuração gerado tem informações de identidade adicional e contém todas as configurações necessárias para se conectar ao ponto de extremidade de serviço, mesmo que eles são as configurações padrão. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]informações de identidade, consulte [autenticação e identidade de serviço](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md), e [ \<identidade >](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md).  
  
4.  No computador cliente, inicie Client.exe em um prompt de comando.  
  
### <a name="to-debug-a-service"></a>Para depurar um serviço  
  
1.  Compilação de solução (cliente e serviço) usando o **criar** menu ou CTRL + SHIFT + B.  
  
2.  Se o serviço está hospedado no IIS:  
  
    1.  Ative o serviço usando um navegador, digitando o endereço http://localhost/servicemodelsamples/service.svc.  
  
    2.  Na solução, escolha o **depurar** menu e **anexar ao processo** item de menu.  
  
    3.  Selecione o **Mostrar processos de todos os usuários** caixa de seleção.  
  
    4.  Selecione o processo de trabalho do host W3wp.exe depurar (selecione ASPNet_wp.exe no Windows XP).  
  
3.  Agora você pode definir pontos de interrupção no código de serviço e habilitar pontos de interrupção em exceções.  
  
4.  Clique no item de projeto de cliente e escolha **depurar**, **iniciar nova instância**.  
  
### <a name="to-clean-up-after-the-sample"></a>A limpeza após a amostra  
  
-   Se o serviço está hospedado no IIS para fins de segurança, remova a definição de diretório virtual e as permissões concedidas a etapas de instalação quando tiver terminado com os exemplos.  
  
## <a name="see-also"></a>Consulte também  
 [Compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md)  
 [Executar os exemplos em um grupo de trabalho e máquinas](http://msdn.microsoft.com/en-us/a451a525-e7ce-452d-9da9-620221260113)  
 [Dicas de solução de problemas](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b)
