---
title: Solução de problemas do tutorial de introdução
ms.date: 03/30/2017
ms.assetid: 69a21511-0871-4c41-9a53-93110e84d7fd
ms.openlocfilehash: 12812bd1ef88eab14a8defed0b71657b0d33c618
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33807782"
---
# <a name="troubleshooting-the-getting-started-tutorial"></a>Solução de problemas do tutorial de introdução
Este tópico lista os problemas mais comuns encontrados ao trabalhar com o Tutorial de Introdução e como resolvê-los.  
  
1.  [Não é possível localizar os arquivos de projeto no disco rígido.](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md#BKMK_q1)  
  
2.  [Ao tentar executar o aplicativo de serviço: HTTP não pôde registrar a URL http://+:8000/ServiceModelSamples/Service/. O processo não tem direitos de acesso a esse namespace.](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md#BKMK_q2)  
  
3.  [Tentativa de usar a ferramenta Svcutil.exe: 'svcutil' não é reconhecido como um comando interno ou externo, um programa operável ou arquivo em lotes.](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md#BKMK_q3)  
  
4.  [Não é possível localizar o arquivo App. config gerado pelo Svcutil.exe.](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md#BKMK_q4)  
  
5.  [Compilar o aplicativo cliente: 'CalculatorClient' não contém uma definição para '&lt;nome do método&gt;'e nenhum método de extensão'&lt;nome do método&gt;' aceitando um primeiro argumento do tipo 'CalculatorClient' foi encontrado (está faltando um usando diretiva ou uma referência de assembly?)](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md#BKMK_q5)  
  
6.  [Compilar o aplicativo cliente: O nome do namespace ou tipo 'CalculatorClient' não pôde ser encontrado (está faltando um usando diretiva ou uma referência de assembly?)](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md#BKMK_q6)  
  
7.  [Executando o cliente: exceção sem tratamento: System.ServiceModel.EndpointNotFoundException: não foi possível conectar ao http://localhost:8000/ServiceModelSamples/Service/CalculatorService. Código de erro TCP 10061: nenhuma conexão pôde ser feita porque a máquina de destino recusou ativamente.](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md#BKMK_q7)  
  
<a name="BKMK_q1"></a>   
## <a name="i-am-unable-to-find-the-project-files-on-my-hard-drive"></a>Não é possível localizar os arquivos de projeto no disco rígido.  
 O Visual Studio salva arquivos de projeto c:\Users\\< usuário name\Documents\\< versão do Visual Studio\>\Projects na [!INCLUDE[wv](../../../includes/wv-md.md)] e [!INCLUDE[win7_client_secondref](../../../includes/win7-client-secondref-md.md)]e c:\Documents and Settings\\< nome de usuário \>Documentos \My\\< versão do Visual Studio\>\Projects em versões anteriores do Windows.  
  
<a name="BKMK_q2"></a>   
## <a name="attempting-to-run-the-service-application-http-could-not-register-url-http8000servicemodelsamplesservice-your-process-does-not-have-access-rights-to-this-namespace"></a>Ao tentar executar o aplicativo de serviço: HTTP não pôde registrar a URL http://+:8000/ServiceModelSamples/Service/. O processo não tem direitos de acesso a esse namespace.  
 O processo que hospeda um serviço WCF deve ser executado com privilégios administrativos. Se você estiver executando o serviço de dentro de [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] você deve executar [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] como um administrador. Para fazer assim, clique em **iniciar**, clique com botão direito [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] e selecione **executar como administrador**. Se você estiver executando o serviço em um prompt de linha de comando, você deve iniciar o prompt de linha de comando como um administrador de maneira semelhante. Clique em **iniciar**, clique com botão direito **Prompt de comando** e selecione **executar como administrador**.  
  
<a name="BKMK_q3"></a>   
## <a name="attempting-to-use-the-svcutilexe-tool-svcutil-is-not-recognized-as-an-internal-or-external-command-operable-program-or-batch-file"></a>Tentativa de usar a ferramenta Svcutil.exe: 'svcutil' não é reconhecido como um comando interno ou externo, um programa operável ou arquivo em lotes.  
 Svcutil.exe deve estar no caminho do sistema. A solução mais fácil é usar o Prompt de comando. Clique em **iniciar**, selecione **todos os programas**, [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)], **ferramentas do Visual Studio**, e [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] **Prompt de comando**. Esse prompt de comando define o caminho do sistema para os locais corretos para todas as ferramentas de envio como parte do [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)].  
  
<a name="BKMK_q4"></a>   
## <a name="unable-to-find-the-appconfig-file-generated-by-svcutilexe"></a>Não é possível localizar o arquivo App. config gerado pelo Svcutil.exe.  
 O **Add Existing Item** caixa de diálogo exibe somente os arquivos com as seguintes extensões por padrão:. cs,. resx,. Settings,. xsd, WSDL. Você pode especificar que você deseja ver todos os tipos de arquivo selecionando **todos os arquivos (\*.\*)**  na lista suspensa da caixa de listagem no canto inferior direito do **Add Existing Item** caixa de diálogo.  
  
<a name="BKMK_q5"></a>   
## <a name="compiling-the-client-application-calculatorclient-does-not-contain-a-definition-for-method-name-and-no-extension-method-method-name-accepting-a-first-argument-of-type-calculatorclient-could-be-found-are-you-missing-a-using-directive-or-an-assembly-reference"></a>Compilar o aplicativo cliente: 'CalculatorClient' não contém uma definição para '\<nome do método >' e nenhum método de extensão '\<nome do método >' aceitando um primeiro argumento do tipo 'CalculatorClient' pôde ser encontrado (tem não está usando uma diretiva ou uma referência de assembly?)  
 Somente os métodos que são marcados com o `ServiceOperationAttribute` são expostos para o mundo exterior. Se você omitir o `ServiceOperationAttribute` atributo de um dos métodos no `ICalculator` você receber essa mensagem de erro ao compilar um aplicativo cliente que faz uma chamada para a operação não tem o atributo de interface.  
  
<a name="BKMK_q6"></a>   
## <a name="compiling-the-client-application-the-type-or-namespace-name-calculatorclient-could-not-be-found-are-you-missing-a-using-directive-or-an-assembly-reference"></a>Compilar o aplicativo cliente: O nome do namespace ou tipo 'CalculatorClient' não pôde ser encontrado (está faltando um usando diretiva ou uma referência de assembly?)  
 Você receberá esse erro se você não adicionar o arquivo Proxy.cs ou Proxy.vb ao seu projeto de cliente.  
  
<a name="BKMK_q7"></a>   
## <a name="running-the-client-unhandled-exception-systemservicemodelendpointnotfoundexception-could-not-connect-to-httplocalhost8000servicemodelsamplesservicecalculatorservice-tcp-error-code-10061-no-connection-could-be-made-because-the-target-machine-actively-refused-it"></a>Executando o cliente: exceção sem tratamento: System.ServiceModel.EndpointNotFoundException: não foi possível conectar ao http://localhost:8000/ServiceModelSamples/Service/CalculatorService. Código de erro TCP 10061: nenhuma conexão pôde ser feita porque a máquina de destino recusou ativamente.  
 Esse erro ocorre se você executar o aplicativo cliente sem executar o serviço.  
  
<a name="BKMK_q8"></a>   
## <a name="unhandled-exception-systemservicemodelsecuritysecuritynegotiationexception-soap-security-negotiation-with-httplocalhost8000servicemodelsamplesservicecalculatorservice-for-target-httplocalhost8000servicemodelsamplesservicecalculatorservice-failed"></a>Exceção sem tratamento: System.ServiceModel.Security.SecurityNegotiationException: negociação de segurança SOAP com 'http://localhost:8000/ServiceModelSamples/Service/CalculatorService'para o destino de'http://localhost:8000/ServiceModelSamples/Service/CalculatorService' falhou  
 Esse erro ocorre em um computador ingressado no domínio que não tenha conectividade de rede. Conectar o computador à rede ou desativar a segurança para o cliente e o serviço. Para o serviço, modifique o código que cria o WSHttpBinding ao seguinte.  
  
```  
// Step 3 of the hosting procedure: Add a service endpoint  
selfhost.AddServiceEndpoint(typeof(ICalculator), new WSHttpBinding(SecurityMode.None), "CalculatorService");  
```  
  
 Para o cliente, altere o  **\<segurança >** elemento sob o  **\<associação >** elemento para ser o seguinte:  
  
```xml  
<security mode="Node" />  
```  
  
## <a name="see-also"></a>Consulte também  
 [Tutorial de Introdução](../../../docs/framework/wcf/getting-started-tutorial.md)  
 [Início rápido de solução de problemas do WCF](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md)  
 [Solução de problemas de instalação](../../../docs/framework/wcf/troubleshooting-setup-issues.md)
