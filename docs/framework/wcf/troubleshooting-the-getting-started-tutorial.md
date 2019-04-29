---
title: Solucionar problemas de Get iniciado com tutoriais do Windows Communication Foundation
ms.date: 01/25/2019
ms.assetid: 69a21511-0871-4c41-9a53-93110e84d7fd
ms.openlocfilehash: 8089e0fee262d07be591069982b1aacfbeae2521
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61791463"
---
# <a name="troubleshoot-the-get-started-with-windows-communication-foundation-tutorials"></a>Solucionar problemas de Get iniciado com tutoriais do Windows Communication Foundation

Este artigo fornece soluções para problemas e erros, você poderá enfrentar ao seguir as etapas mais comuns de [Tutorial: Introdução a aplicativos do Windows Communication Foundation](getting-started-tutorial.md). 
  
## <a name="common-problems"></a>Problemas comuns

**Não consigo localizar os arquivos de projeto no meu disco rígido.**

 O Visual Studio salva arquivos de projeto no *C:\Users\\&lt;nome de usuário&gt;\source\repos*.  

**Não é possível localizar o *App. config* arquivo gerado pelo *Svcutil.exe*.**

 No Visual Studio, o **Add Existing Item** janela exibe apenas os arquivos com as seguintes extensões por padrão: 
- *.cs* 
- *.resx* 
- *.settings*
- *.xsd* 
- *.wsdl*

Para exibir todos os tipos de arquivo, selecione **todos os arquivos (\*.\*)**  na lista suspensa no canto inferior direito dos **Add Existing Item** janela.  
  
## <a name="common-errors"></a>Erros comuns

### <a name="compile-the-service-application"></a>Compilar o aplicativo de serviço 

**Erro BC30420 'Sub Main' não foi encontrado em 'GettingStartedHost.Module1'.**

O ponto de entrada está incorreto para o aplicativo Visual Basic. Faça a seguinte alteração:

   1. No **Gerenciador de soluções** janela, selecione a **GettingStartedHost** pasta e, em seguida, selecione **propriedades** no menu de atalho.
    a. No **GettingStartedHost** janela, para **objeto de inicialização**, selecione **Service.Program** (ou o ponto de entrada para seu aplicativo específico) na lista. 
    b. No menu principal, selecione **arquivo** > **Salvar tudo**.

### <a name="run-the-service-application"></a>Execute o aplicativo de serviço 

**HTTP não foi possível registrar a URL ' http:\// +: 8000/GettingStarted/CalculatorService '. O processo não tem direitos de acesso a esse namespace.** 

 Para o acesso adequado, inicie o processo que hospeda o serviço do Windows Communication Foundation (WCF) com privilégios administrativos:
- Para o Visual Studio: Selecione o programa Visual Studio na **inicie** menu e, em seguida, selecione **mais** > **executar como administrador** no menu de atalho.
- Para uma janela do console: Selecione **Prompt de comando** na **inicie** menu e, em seguida, selecione **mais** > **executar como administrador** partir do atalho menu.
- Para o Windows Explorer: Selecione o executável e, em seguida, selecione **executar como administrador** no menu de atalho.

### <a name="compile-the-client-application"></a>Compilar o aplicativo cliente

**'CalculatorClient' não contém uma definição para '\<nome do método >' e nenhum método de extensão '\<nome do método >' aceitando um primeiro argumento do tipo 'CalculatorClient' pôde ser encontrado (está faltando um usando diretiva ou um referência de assembly?)**  

Somente os métodos que você marca com o `ServiceOperationAttribute` atributo são expostos publicamente. Se você omitir a `ServiceOperationAttribute` atributo de um método no `ICalculator` interface, você receber essa mensagem de erro durante a compilação.  

**O nome do namespace ou tipo 'CalculatorClient' não pôde ser encontrado (está faltando um usando diretiva ou uma referência de assembly?)**

 Você recebe esse erro se você não adicionar o *generatedProxy.cs* (ou *generatedProxy.vb*) ao seu projeto de cliente quando você gerou-los com o *Svcutil.exe* ferramenta .  

### <a name="run-the-client-application"></a>Executar o aplicativo cliente

**Exceção sem tratamento: System.ServiceModel.EndpointNotFoundException: Não foi possível se conectar ao ' http:\//localhost:8000/GettingStarted/CalculatorService '. Código de erro TCP 10061: Nenhuma conexão pôde ser feita porque a máquina de destino recusou-a ativamente.**

Esse erro ocorre se você executar o aplicativo cliente sem primeiro iniciar o serviço. Primeiro, execute o aplicativo de host para iniciar o serviço e, em seguida, executar o aplicativo cliente.

### <a name="use-the-svcutilexe-tool"></a>Use a ferramenta Svcutil.exe
   
**'Svcutil' não é reconhecido como um comando interno ou externo, programa operável ou arquivo em lotes.**

 *Svcutil.exe* deve estar no caminho do sistema. A solução mais fácil é usar o prompt de comando do Visual Studio. Dos **inicie** menu, selecione o **Visual Studio \<versão >** diretório, em seguida, selecione **Prompt de comando do desenvolvedor para VS \<versão >**. Esse prompt de comando define o caminho do sistema para os locais corretos para todas as ferramentas que é fornecidas como parte do Visual Studio.  
  
### <a name="run-the-service-and-client-applications"></a>Executar os aplicativos de serviço e cliente

**System.ServiceModel.Security.SecurityNegotiationException: Negociação de segurança SOAP com ' http:\//localhost:8000/GettingStarted/CalculatorService ' para o destino ' http:\//localhost:8000/GettingStarted/CalculatorService ' falhou**  

Esse erro ocorre em um computador ingressado no domínio que não tem conectividade de rede. Conectar o computador à rede ou desativar a segurança para o serviço e o cliente. 

Para desativar a segurança:

- Para o serviço, substitua o código que cria o `WSHttpBinding` com o código a seguir:  
  
    ```csharp
    // Step 3: Add a service endpoint.
    selfhost.AddServiceEndpoint(typeof(ICalculator), new WSHttpBinding(SecurityMode.None), "CalculatorService");  
    ```

- Para atualização do cliente, no arquivo de configuração, o  **\<segurança >** elemento sob o  **\<associação >** elemento da seguinte maneira:  
  
    ```xml
    <binding name="WSHttpBinding_ICalculator" security mode="None" />
    ```  

## <a name="see-also"></a>Consulte também  
 [Introdução a aplicativos do WCF](getting-started-tutorial.md)  
 [Início rápido de solução de problemas do WCF](wcf-troubleshooting-quickstart.md)  
 [Solução de problemas de instalação](troubleshooting-setup-issues.md)
