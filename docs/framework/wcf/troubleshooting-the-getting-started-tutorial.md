---
title: Solucionar problemas dos tutoriais de introdução aos Windows Communication Foundation
ms.date: 01/25/2019
ms.assetid: 69a21511-0871-4c41-9a53-93110e84d7fd
ms.openlocfilehash: 10a2f8f718d802a7aab067b882f0d5cf3dc28dca
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928577"
---
# <a name="troubleshoot-the-get-started-with-windows-communication-foundation-tutorials"></a>Solucionar problemas dos tutoriais de introdução aos Windows Communication Foundation

Este artigo fornece soluções para os problemas e erros mais comuns que você pode enfrentar ao seguir as etapas no [tutorial: Introdução aos aplicativos](getting-started-tutorial.md)Windows Communication Foundation. 
  
## <a name="common-problems"></a>Problemas comuns

**Não consigo encontrar os arquivos de projeto em meu disco rígido.**

 O Visual Studio salva arquivos de projeto em *\\C:\Users&gt;&lt;User Name \source\repos*.  

**Não consigo encontrar o arquivo *app. config* gerado por *svcutil. exe*.**

 No Visual Studio, a janela **Adicionar item existente** exibe apenas os arquivos com as seguintes extensões por padrão: 

- *.cs* 
- *.resx* 
- *.settings*
- *.xsd* 
- *.wsdl*

Para exibir todos os tipos de arquivo, selecione **todos\*os\*arquivos (.)** na lista suspensa no canto inferior direito da janela **Adicionar item existente** .  
  
## <a name="common-errors"></a>Erros comuns

### <a name="compile-the-service-application"></a>Compilar o aplicativo de serviço 

**Erro BC30420 ' Sub Main ' não encontrado em ' GettingStartedHost. Module1 '.**

O ponto de entrada está incorreto para o aplicativo Visual Basic. Faça a seguinte alteração:

   1. Na janela **Gerenciador de soluções** , selecione a pasta **GettingStartedHost** e, em seguida, selecione **Propriedades** no menu de atalho.
    a. Na janela **GettingStartedHost** , para **objeto de inicialização**, selecione **Service. Program** (ou o ponto de entrada para seu aplicativo específico) na lista. 
    b. No menu principal, selecione **arquivo** > **salvar tudo**.

### <a name="run-the-service-application"></a>Executar o aplicativo de serviço 

**O http não pôde registrar a URL '\/http:/+: 8000/gettingstarted/CalculatorService '. Seu processo não tem direitos de acesso a este namespace.** 

 Para obter acesso adequado, inicie o processo que hospeda o serviço do Windows Communication Foundation (WCF) com privilégios administrativos:

- Para o Visual Studio: Selecione o programa Visual Studio no menu **Iniciar** e, em seguida, selecione **mais** > **Executar como administrador** no menu de atalho.
- Para uma janela de console: Selecione **prompt de comando** no **menu iniciar** e, em seguida, selecione **mais** > **Executar como administrador** no menu de atalho.
- Para o Windows Explorer: Selecione o executável e, em seguida, selecione **Executar como administrador** no menu de atalho.

### <a name="compile-the-client-application"></a>Compilar o aplicativo cliente

**' CalculatorClient ', não contém uma definição para '\<Method Name > ' e não foi possível encontrar nenhum método de extensão '\<nome do método > ' aceitando um primeiro argumento do tipo ' CalculatorClient ' (está faltando uma diretiva using ou um referência de assembly?)**  

Somente os métodos que você marca com o `ServiceOperationAttribute` atributo são expostos publicamente. Se você omitir `ServiceOperationAttribute` o atributo de um método `ICalculator` na interface, receberá essa mensagem de erro durante a compilação.  

**Não foi possível encontrar o nome do tipo ou do namespace ' CalculatorClient ' (está faltando uma diretiva using ou uma referência de assembly?)**

 Você receberá esse erro se não adicionar o arquivo *generatedProxy.cs* (ou *generatedProxy. vb*) ao seu projeto de cliente quando os tiver gerado com a ferramenta *svcutil. exe* .  

### <a name="run-the-client-application"></a>Executar o aplicativo cliente

**Exceção sem tratamento: System.ServiceModel.EndpointNotFoundException: Não foi possível conectar-se a\/' http:/localhost: 8000/gettingstarted/CalculatorService '. Código de erro TCP 10061: Não foi possível estabelecer uma conexão porque a máquina de destino a recusou ativamente.**

Esse erro ocorrerá se você executar o aplicativo cliente sem primeiro iniciar o serviço. Primeiro, execute o aplicativo host para iniciar o serviço e, em seguida, execute o aplicativo cliente.

### <a name="use-the-svcutilexe-tool"></a>Usar a ferramenta svcutil. exe
   
**' SvcUtil ' não é reconhecido como comando interno ou externo, programa operável ou arquivo em lotes.**

 *Svcutil. exe* deve estar no caminho do sistema. A solução mais fácil é usar o prompt de comando do Visual Studio. No menu **Iniciar** , selecione o diretório **> versão \<do Visual Studio** e, em seguida, selecione **prompt de comando do desenvolvedor para vs \<versão >** . Esse prompt de comando define o caminho do sistema para os locais corretos de todas as ferramentas enviadas como parte do Visual Studio.  
  
### <a name="run-the-service-and-client-applications"></a>Executar os aplicativos de serviço e cliente

**System.ServiceModel.Security.SecurityNegotiationException: A negociação de segurança SOAP com '\/http:/localhost: 8000/gettingstarted/CalculatorService ' para o destino\/' http:/localhost: 8000/gettingstarted/CalculatorService ' falhou**  

Esse erro ocorre em um computador ingressado no domínio que não tem conectividade de rede. Conecte seu computador à rede ou desative a segurança para o serviço e o cliente. 

Para desativar a segurança:

- Para o serviço, substitua o código que cria o `WSHttpBinding` com o código a seguir:  
  
    ```csharp
    // Step 3: Add a service endpoint.
    selfhost.AddServiceEndpoint(typeof(ICalculator), new WSHttpBinding(SecurityMode.None), "CalculatorService");  
    ```

- Para o cliente, no arquivo de configuração, atualize o  **\<elemento Security >** sob o  **\<elemento Binding >** da seguinte maneira:  
  
    ```xml
    <binding name="WSHttpBinding_ICalculator" security mode="None" />
    ```  

## <a name="see-also"></a>Consulte também  
 [Introdução aos aplicativos WCF](getting-started-tutorial.md)  
 [Início rápido da solução de problemas do WCF](wcf-troubleshooting-quickstart.md)  
 [Solucionando problemas de instalação](troubleshooting-setup-issues.md)
