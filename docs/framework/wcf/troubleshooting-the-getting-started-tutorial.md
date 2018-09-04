---
title: Solução de problemas do tutorial de introdução
ms.date: 03/30/2017
ms.assetid: 69a21511-0871-4c41-9a53-93110e84d7fd
ms.openlocfilehash: 43128743ba16aefc8669ace85070a16d80145a71
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43519415"
---
# <a name="troubleshooting-the-getting-started-tutorial"></a>Solução de problemas do tutorial de introdução
Este tópico lista os problemas mais comuns encontrados ao trabalhar por meio do Tutorial de Introdução e como resolvê-los.  
  
**Não consigo localizar os arquivos de projeto no meu disco rígido.**

 O Visual Studio salva arquivos de projeto em c:\users\\<user name>\Documents\\< versão do Visual Studio\>\Projects.  
  
**A tentativa de executar o aplicativo de serviço: HTTP não foi possível registrar a URL `http://+:8000/ServiceModelSamples/Service/`.** 
 **Seu processo não tem direitos de acesso a esse namespace.** 

 O processo que hospeda um serviço WCF deve ser executado com privilégios administrativos. Se você estiver executando o serviço de dentro do Visual Studio, você deve executar o Visual Studio como administrador. Para isso, clique em **inicie**, clique com botão direito **Visual Studio \< *versão* >**  e selecione **executar como administrador**. Se você estiver executando o serviço em um prompt de linha de comando na janela do console, você deve iniciar a janela do console como um administrador de maneira semelhante. Clique em **inicie**, clique com botão direito **Prompt de comando** e selecione **executar como administrador**.  
  
**A tentativa de usar a ferramenta Svcutil.exe: 'svcutil' não é reconhecido como um comando interno ou externo, programa operável ou arquivo em lotes.**

 Svcutil.exe deve estar no caminho do sistema. A solução mais fácil é usar o Prompt de comando. Clique em **inicie**, selecione **todos os programas**, **Visual Studio \< *versão*>**,  **Ferramentas do Visual Studio**, e **Prompt de comando do desenvolvedor para Visual Studio**. Esse prompt de comando define o caminho do sistema para os locais corretos para todas as ferramentas que é fornecidas como parte do Visual Studio.  

**Não é possível localizar o arquivo App. config gerado pelo Svcutil.exe.**

 O **Add Existing Item** caixa de diálogo exibe somente os arquivos com as seguintes extensões por padrão:. cs,. resx,. Settings,. xsd,. WSDL. Você pode especificar que você deseja ver todos os tipos de arquivo, selecionando **todos os arquivos (\*.\*)**  na caixa de lista suspensa no canto inferior direito do **Add Existing Item** caixa de diálogo.  


**Compilando o aplicativo cliente: 'CalculatorClient' não contém uma definição para '\<nome do método >' e nenhum método de extensão '\<nome do método >' aceitando um primeiro argumento do tipo 'CalculatorClient' pôde ser encontrado (tem não está usando uma diretiva ou uma referência de assembly?)**  

Somente os métodos que são marcados com o `ServiceOperationAttribute` são expostos para o mundo exterior. Se você omitir a `ServiceOperationAttribute` atributo de um dos métodos a `ICalculator` interface, você receber essa mensagem de erro ao compilar um aplicativo cliente que faz uma chamada para a operação não tem o atributo.  

**Compilando o aplicativo cliente: O nome do namespace ou tipo 'CalculatorClient' não pôde ser encontrado (está faltando um usando diretiva ou uma referência de assembly?)**

 Você receberá esse erro se você não adicionar o arquivo Proxy.cs ou Proxy.vb ao seu projeto de cliente.  

**Executando o cliente: exceção sem tratamento: System.ServiceModel.EndpointNotFoundException: não foi possível conectar ao `http://localhost:8000/ServiceModelSamples/Service/CalculatorService`. Código de erro TCP 10061: nenhuma conexão pôde ser feita porque a máquina de destino recusou-a ativamente.**

Esse erro ocorre se você executar o aplicativo cliente sem executar o serviço.  
  
**Exceção sem tratamento: System.ServiceModel.Security.SecurityNegotiationException: negociação de segurança SOAP com `http://localhost:8000/ServiceModelSamples/Service/CalculatorService` de destino `http://localhost:8000/ServiceModelSamples/Service/CalculatorService` falhou**  

Esse erro ocorre em um computador ingressado no domínio que não tem conectividade de rede. Conectar seu computador à rede ou desativar a segurança para o cliente e o serviço. Para o serviço, modifique o código que cria o WSHttpBinding ao seguinte.  
  
```csharp
// Step 3 of the hosting procedure: Add a service endpoint  
selfhost.AddServiceEndpoint(typeof(ICalculator), new WSHttpBinding(SecurityMode.None), "CalculatorService");  
```

Para o cliente, altere o  **\<segurança >** elemento sob o  **\<associação >** elemento para o seguinte:  
  
```xml
<security mode="Node" />  
```  

## <a name="see-also"></a>Consulte também  
 [Tutorial de Introdução](../../../docs/framework/wcf/getting-started-tutorial.md)  
 [Início rápido de solução de problemas do WCF](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md)  
 [Solução de problemas de instalação](../../../docs/framework/wcf/troubleshooting-setup-issues.md)
