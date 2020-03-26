---
title: Solucionar problemas com os tutoriais da Windows Communication Foundation
ms.date: 01/25/2019
ms.assetid: 69a21511-0871-4c41-9a53-93110e84d7fd
ms.openlocfilehash: 73aa0f5784784cb788a7532f8e22cbe925429c41
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249611"
---
# <a name="troubleshoot-the-get-started-with-windows-communication-foundation-tutorials"></a>Solucionar problemas com os tutoriais da Windows Communication Foundation

Este artigo fornece soluções para os problemas e erros mais comuns que você pode enfrentar quando você segue os passos no [Tutorial: Comece com](getting-started-tutorial.md)os aplicativos da Windows Communication Foundation .
  
## <a name="common-problems"></a>Problemas comuns

**Não consigo encontrar os arquivos do projeto no meu disco rígido.**

 O Visual Studio salva arquivos de projeto em *C:\Users\\&lt;user&gt;name \source\repos*.  

**Não consigo encontrar o arquivo *App.config* gerado por *Svcutil.exe*.**

 No Visual Studio, a **janela Adicionar item existente** exibe apenas arquivos com as seguintes extensões por padrão:

- *.cs*
- *.resx*
- *.configurações*
- *.xsd*
- *.wsdl*

Para exibir todos os tipos de arquivos, selecione **Todos os arquivos (\*)\*** na lista de baixa no canto inferior direito da janela Adicionar **item existente.**  
  
## <a name="common-errors"></a>Erros comuns

### <a name="compile-the-service-application"></a>Compilar o aplicativo de serviço

**O erro BC30420 'Sub Main' não foi encontrado em 'GettingStartedHost.Module1'.**

O ponto de entrada está incorreto para o aplicativo Visual Basic. Faça a seguinte alteração:

   1. Na janela **'Explorador de soluções',** selecione a pasta **GettingStartedHost** e selecione **Propriedades** no menu de atalho.
    a. Na janela **GettingStartedHost,** para **objeto Iniciar,** selecione **Service.Program** (ou o ponto de entrada para seu aplicativo específico) na lista.
    b. No menu principal, selecione **'Salvar todos'** **do arquivo** > .

### <a name="run-the-service-application"></a>Execute o aplicativo de serviço

**O HTTP não pôde\/registrar URL 'http: /+:8000/GettingStarted/CalculatorService'. Seu processo não tem direitos de acesso a este namespace.**

 Para acesso adequado, inicie o processo que hospeda o serviço da Windows Communication Foundation (WCF) com privilégios administrativos:

- Para o Visual Studio: Selecione o programa Visual Studio no menu **Iniciar** e selecione **Mais** > **Executar como administrador** no menu de atalho.
- Para uma janela do console: selecione **'Prompt' de comando** no menu **Iniciar** e selecione **Mais** > **executar como administrador** no menu de atalho.
- Para o Windows Explorer: Selecione o executável e **selecione Executar como administrador** no menu de atalho.

### <a name="compile-the-client-application"></a>Compilar o aplicativo cliente

**'CalculadoraClient', não contém uma definição\<para 'nome do método\<>' e nenhum método de extensão ' nome do método>' aceitando um primeiro argumento do tipo 'CalculadoraClient' poderia ser encontrado (você está faltando uma diretiva de uso ou uma referência de montagem?)**  

Apenas os métodos que `ServiceOperationAttribute` você marca com o atributo são expostos publicamente. Se você omite o atributo `ServiceOperationAttribute` de um método na interface, você receberá esta mensagem de erro durante a `ICalculator` compilação.  

**O nome de tipo ou namespace 'CalculatorClient' não foi encontrado (você está faltando uma diretiva de uso ou uma referência de montagem?)**

 Você recebe esse erro se não adicionar o arquivo *generatedProxy.cs* (ou *gerouProxy.vb)* ao seu projeto cliente quando os gerou com a ferramenta *Svcutil.exe.*  

### <a name="run-the-client-application"></a>Execute o aplicativo do cliente

**Exceção não manuseada: System.ServiceModel.EndpointNotFoundException:\/Não foi possível se conectar a 'http: /localhost:8000/GettingStarted/CalculatorService'. Código de erro TCP 10061: Nenhuma conexão poderia ser feita porque a máquina de destino recusou ativamente.**

Esse erro ocorre se você executar o aplicativo cliente sem antes iniciar o serviço. Primeiro, execute o aplicativo host para iniciar o serviço e, em seguida, execute o aplicativo cliente.

### <a name="use-the-svcutilexe-tool"></a>Use a ferramenta Svcutil.exe

**'Svcutil' não é reconhecido como um comando interno ou externo, programa operável ou arquivo em lote.**

 *Svcutil.exe* deve estar no caminho do sistema. A solução mais fácil é usar o prompt de comando do Visual Studio. No menu **Iniciar,** selecione a **versão do Visual Studio \<>** diretório e selecione **'Solicitação de comando do \<desenvolvedor' para>de versão VS **. Este prompt de comando define o caminho do sistema para os locais corretos para todas as ferramentas enviadas como parte do Visual Studio.  
  
### <a name="run-the-service-and-client-applications"></a>Execute os aplicativos de serviço e cliente

**System.ServiceModel.Security.SecurityNegotiationException: negociação de segurança\/soap com 'http: /localhost:8000/GettingStarted/CalculatorService' para falha no destino 'http:\//localhost:8000/GettingStarted/CalculatorService' falhou**  

Esse erro ocorre em um computador com um domínio que não tem conectividade de rede. Conecte seu computador à rede ou desligue a segurança tanto para o serviço quanto para o cliente.

Para desativar a segurança:

- Para o serviço, substitua `WSHttpBinding` o código que cria o com o seguinte código:  
  
    ```csharp
    // Step 3: Add a service endpoint.
    selfhost.AddServiceEndpoint(typeof(ICalculator), new WSHttpBinding(SecurityMode.None), "CalculatorService");  
    ```

- Para o cliente, no arquivo ** \<** de configuração, atualize o elemento>de segurança sob o ** \<** elemento>vinculante da seguinte forma:  
  
    ```xml
    <binding name="WSHttpBinding_ICalculator">
      <security mode="None" />
    </binding
    ```  

## <a name="see-also"></a>Confira também  
 [Comece com aplicativos WCF](getting-started-tutorial.md)  
 [WCF solução de problemas quickstart](wcf-troubleshooting-quickstart.md)  
 [Problemas de configuração de solução de problemas](troubleshooting-setup-issues.md)
