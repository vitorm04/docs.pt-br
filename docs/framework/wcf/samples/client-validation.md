---
title: "Validação de cliente"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f0c1f805-1a81-4d0d-a112-bf5e2e87a631
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f187e6fb64fd3bbf08b3d0b92917ffc640b02186
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="client-validation"></a>Validação de cliente
Os serviços com frequência publicar metadados para habilitar a geração automática e a configuração de tipos de proxy de cliente. Quando o serviço não for confiável, os aplicativos cliente devem validar que os metadados está de acordo com a política do aplicativo cliente sobre segurança, transações, o tipo de contrato de serviço e assim por diante. O exemplo a seguir demonstra como gravar um cliente de comportamento de ponto de extremidade que valida o ponto de extremidade de serviço para garantir que esse ponto de extremidade de serviço é seguro.  
  
 O serviço expõe quatro pontos de extremidade de serviço. O primeiro ponto de extremidade usa o WSDualHttpBinding, o segundo ponto de extremidade usa a autenticação NTLM, o terceiro ponto de extremidade permite que o fluxo de transações e o ponto de extremidade quarto usa autenticação baseada em certificado.  
  
 O cliente usa o <xref:System.ServiceModel.Description.MetadataResolver> classe para recuperar os metadados para o serviço. O cliente impõe uma política de proibindo associações duplex, a autenticação NTLM e o fluxo de transações usando o comportamento de validação. Para cada <xref:System.ServiceModel.Description.ServiceEndpoint> instância importada de metadados do serviço, o aplicativo cliente adiciona uma instância do `InternetClientValidatorBehavior` comportamento de ponto de extremidade para o <xref:System.ServiceModel.Description.ServiceEndpoint> antes de tentar usar um [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] cliente para se conectar ao ponto de extremidade. O comportamento `Validate` método é executado antes de todas as operações no serviço são chamadas e impõe a política do cliente, lançando `InvalidOperationExceptions`.  
  
### <a name="to-build-the-sample"></a>Para criar o exemplo  
  
1.  Para criar a solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
### <a name="to-run-the-sample-on-the-same-computer"></a>Para executar o exemplo no mesmo computador  
  
1.  Abra um prompt de comando do Visual Studio com privilégios de administrador e execute bat da pasta de instalação do exemplo. Isso instala todos os certificados necessários para executar o exemplo.  
  
2.  Execute o aplicativo de serviço do \service\bin\Debug.  
  
3.  Execute o aplicativo cliente de \client\bin\Debug. Atividade do cliente é exibida no aplicativo de console do cliente.  
  
4.  Se o cliente e o serviço não for capazes de se comunicar, consulte [dicas de solução de problemas](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).  
  
5.  Remova os certificados executando Cleanup.bat quando você tiver terminado com o exemplo. Outros exemplos de segurança usam os mesmos certificados.  
  
### <a name="to-run-the-sample-across-computers"></a>Para executar o exemplo em computadores  
  
1.  No servidor, em um prompt de comando do Visual Studio executar com privilégios de administrador, digite `setup.bat service`. Executando `setup.bat` com o `service` argumento cria um certificado de serviço com o nome de domínio totalmente qualificado do computador e exporta o certificado de serviço para um arquivo chamado Service.cer.  
  
2.  No servidor, edite o App. config para refletir o novo nome do certificado. Ou seja, alterar o `findValue` atributo o [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) elemento para o nome de domínio totalmente qualificado do computador.  
  
3.  Copie o arquivo de Service.cer do diretório de serviço para o diretório do cliente no computador cliente.  
  
4.  No cliente, abra um prompt de comando do Visual Studio com privilégios de administrador e digite `setup.bat client`. Executando `setup.bat` com o `client` argumento cria um certificado de cliente chamado Client.com e exporta o certificado de cliente para um arquivo chamado cer.  
  
5.  No arquivo client.cs, altere o valor do endereço do ponto de extremidade MEX e `findValue` para definir o certificado do servidor padrão para coincidir com o novo endereço do seu serviço. Para fazer isso, substituindo o host local com o nome de domínio totalmente qualificado do servidor. Reconstrução.  
  
6.  Copie o arquivo CER do diretório do cliente para o diretório de serviço no servidor.  
  
7.  No cliente, execute ImportServiceCert.bat em um prompt de comando do Visual Studio aberto com privilégios de administrador. Isso importa o certificado de serviço do arquivo Service.cer para CurrentUser - TrustedPeople repositório.  
  
8.  No servidor, execute ImportClientCert.bat em um prompt de comando do Visual Studio aberto com privilégios de administrador. Isso importa o certificado de cliente do arquivo CER para o repositório de LocalMachine - TrustedPeople.  
  
9. No computador do serviço, compilar o projeto de serviço no Visual Studio e execute service.exe.  
  
10. No computador cliente, execute client.exe.  
  
    1.  Se o cliente e o serviço não for capazes de se comunicar, consulte [dicas de solução de problemas](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).  
  
### <a name="to-clean-up-after-the-sample"></a>A limpeza após a amostra  
  
-   Execute Cleanup.bat na pasta exemplos depois de terminar a execução do exemplo.  
  
    > [!NOTE]
    >  Esse script não remove os certificados de serviço em um cliente ao executar este exemplo entre computadores. Se você tiver executado [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] exemplos que usam certificados em computadores, certifique-se de desmarcar os certificados de serviço que foram instalados em CurrentUser - TrustedPeople repositório. Para fazer isso, use o seguinte comando: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>. For example: certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.  
  
## <a name="see-also"></a>Consulte também  
 [Usando metadados](../../../../docs/framework/wcf/feature-details/using-metadata.md)
