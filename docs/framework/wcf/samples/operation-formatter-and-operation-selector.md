---
title: Formatador de operação e seletor de operação
ms.date: 03/30/2017
ms.assetid: 1c27e9fe-11f8-4377-8140-828207b98a0e
ms.openlocfilehash: 64f2d807946d5365c01cd1a46488c868ebc603ac
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74714636"
---
# <a name="operation-formatter-and-operation-selector"></a>Formatador de operação e seletor de operação
Este exemplo demonstra como os pontos de extensibilidade do Windows Communication Foundation (WCF) podem ser usados para permitir dados de mensagem em um formato diferente do esperado pelo WCF. Por padrão, os formatadores do WCF esperam que os parâmetros do método sejam incluídos no elemento `soap:body`. O exemplo mostra como implementar um formatador de operação personalizada que analisa dados de parâmetro de uma cadeia de caracteres de consulta HTTP GET e invoca métodos que usam esses dados.  
  
 O exemplo é baseado na [introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md), que implementa o contrato de serviço `ICalculator`. Ele mostra como as mensagens adicionar, subtrair, multiplicar e dividir podem ser alteradas para usar HTTP GET para solicitações de cliente para servidor e HTTP POST com mensagens POX para respostas de servidor para cliente.  
  
 Para fazer isso, o exemplo fornece o seguinte:  
  
- `QueryStringFormatter`, que implementa <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> e <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> para o cliente e servidor, respectivamente, e processa os dados na cadeia de caracteres de consulta.  
  
- `UriOperationSelector`, que implementa <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> no servidor para executar a expedição de operação com base no nome da operação na solicitação GET.  
  
- `EnableHttpGetRequestsBehavior` o comportamento do ponto de extremidade (e a configuração correspondente), que adiciona o seletor de operação necessário ao tempo de execução.  
  
- Mostra como inserir um novo formatador de operação no tempo de execução.  
  
- Neste exemplo, o cliente e o serviço são aplicativos de console (. exe).  
  
> [!NOTE]
> O procedimento de instalação e as instruções de Build para este exemplo estão localizados no final deste tópico.  
  
## <a name="key-concepts"></a>Conceitos principais  
 `QueryStringFormatter`-o formatador de operação é o componente no WCF que é responsável pela conversão de uma mensagem em uma matriz de objetos de parâmetro e uma matriz de objetos de parâmetro em uma mensagem. Isso é feito no cliente usando a interface <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> e no servidor com a interface <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter>. Essas interfaces permitem que os usuários obtenham as mensagens de solicitação e resposta dos métodos `Serialize` e `Deserialize`.  
  
 Neste exemplo, `QueryStringFormatter` implementa ambas as interfaces e é implementada no cliente e no servidor.  
  
 Solicitação:  
  
- O exemplo usa a classe <xref:System.ComponentModel.TypeConverter> para converter dados de parâmetro na mensagem de solicitação de e para cadeias de caracteres. Se um <xref:System.ComponentModel.TypeConverter> não estiver disponível para um tipo específico, o formatador de exemplo lançará uma exceção.  
  
- No método `IClientMessageFormatter.SerializeRequest` no cliente, o formatador cria um URI com o apropriado para endereçar e acrescentar o nome da operação como um sufixo. Esse nome é usado para enviar para a operação apropriada no servidor. Em seguida, ele pega a matriz de objetos de parâmetro e serializa os dados de parâmetro para a cadeia de caracteres de consulta de URI usando nomes de parâmetro e os valores convertidos pela classe <xref:System.ComponentModel.TypeConverter>. As propriedades <xref:System.ServiceModel.Channels.MessageHeaders.To%2A> e <xref:System.ServiceModel.Channels.MessageProperties.Via%2A> são, então, definidas para esse URI. <xref:System.ServiceModel.Channels.MessageProperties> é acessado por meio da propriedade <xref:System.ServiceModel.Channels.Message.Properties%2A>.  
  
- No método `IDispatchMessageFormatter.DeserializeRequest` no servidor, o formatador recupera o URI `Via` nas propriedades da mensagem de solicitação de entrada. Ele analisa os pares de nome-valor na cadeia de caracteres de consulta de URI em valores e nomes de parâmetros e usa os nomes e valores de parâmetro para preencher a matriz de parâmetros passada para o método. Observe que a expedição da operação já ocorreu, portanto, o sufixo do nome da operação é ignorado nesse método.  
  
 Resposta:  
  
- Neste exemplo, HTTP GET é usado somente para a solicitação. O formatador delega o envio da resposta ao formatador original que teria sido usado para gerar uma mensagem XML. Uma das metas deste exemplo é mostrar como esse formatador de delegação pode ser implementado.  
  
### <a name="uripathsuffixoperationselector-class"></a>Classe UriPathSuffixOperationSelector  
 A interface <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> permite que os usuários implementem sua própria lógica para a qual operação uma determinada mensagem deve ser expedida.  
  
 Neste exemplo, `UriPathSuffixOperationSelector` deve ser implementada no servidor para selecionar a operação apropriada porque o nome da operação está incluído no URI GET HTTP em vez de um cabeçalho Action na mensagem. O exemplo é configurado para permitir apenas nomes de operação que não diferenciam maiúsculas de minúsculas.  
  
 O método `SelectOperation` usa a mensagem de entrada e pesquisa o URI de `Via` em suas propriedades de mensagem. Ele extrai o sufixo de nome de operação do URI, pesquisa uma tabela interna para obter o nome da operação para a qual a mensagem deve ser expedida e retorna esse nome de operação.  
  
### <a name="enablehttpgetrequestsbehavior-class"></a>Classe EnableHttpGetRequestsBehavior  
 O componente `UriPathSuffixOperationSelector` pode ser configurado programaticamente ou por meio de um comportamento de ponto de extremidade. O exemplo implementa o comportamento de `EnableHttpGetRequestsBehavior`, que é especificado no arquivo de configuração de aplicativo do serviço.  
  
 No servidor:  
  
 O <xref:System.ServiceModel.Dispatcher.DispatchRuntime.OperationSelector%2A> é definido como a implementação de <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector>.  
  
 Por padrão, o WCF usa um filtro de endereço de correspondência exata. O URI na mensagem de entrada contém um sufixo de nome de operação seguido por uma cadeia de caracteres de consulta que contém dados de parâmetro, portanto, o comportamento do ponto de extremidade também altera o filtro de endereço para ser um filtro de correspondência de prefixo. Ele usa o<xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> do WCF para essa finalidade.  
  
### <a name="installing-operation-formatters"></a>Instalando formatadores de operação  
 Comportamentos de operação que especificam formatadores são exclusivos. Um desses comportamentos é sempre implementado por padrão para cada operação para criar o formatador de operação necessário. No entanto, esses comportamentos parecem apenas outro comportamento de operação; Eles não são identificáveis por nenhum outro atributo. Para instalar um comportamento de substituição, a implementação deve procurar comportamentos de formatador específicos instalados pelo carregador do tipo WCF por padrão e substituí-lo ou adicionar um comportamento compatível para execução após o comportamento padrão.  
  
 Esses comportamentos de formatadores de operação podem ser configurados programaticamente antes de chamar <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A?displayProperty=nameWithType> ou especificando um comportamento de operação que é executado após o padrão. No entanto, ele não pode ser facilmente configurado por um comportamento de ponto de extremidade (e, portanto, por configuração) porque o modelo de comportamento não permite que um comportamento substitua outros comportamentos ou, de outra forma, modifica a árvore de descrição.  
  
 No cliente:  
  
 A implementação de <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> deve ser implementada para que possa converter as solicitações em solicitações HTTP GET e delegar para o formatador original para respostas. Isso é feito chamando o método auxiliar `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior`.  
  
 Isso deve ser feito antes de chamar `CreateChannel`.  
  
```csharp  
void ReplaceFormatterBehavior(OperationDescription operationDescription, EndpointAddress address)  
{  
    // Remove the DataContract behavior if it is present.  
    IOperationBehavior formatterBehavior = operationDescription.Behaviors.Remove<DataContractSerializerOperationBehavior>();  
    if (formatterBehavior == null)  
    {  
        // Remove the XmlSerializer behavior if it is present.  
        formatterBehavior = operationDescription.Behaviors.Remove<XmlSerializerOperationBehavior>();  
        ...  
    }  
  
    // Remember what the innerFormatterBehavior was.  
    DelegatingFormatterBehavior delegatingFormatterBehavior = new DelegatingFormatterBehavior(address);  
    delegatingFormatterBehavior.InnerFormatterBehavior = formatterBehavior;  
   operationDescription.Behaviors.Add(delegatingFormatterBehavior);  
}  
```  
  
 No servidor:  
  
- A interface de <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> deve ser implementada para que possa ler solicitações HTTP GET e delegar ao formatador original para gravar respostas. Isso é feito chamando o mesmo método auxiliar `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` como o cliente (consulte o exemplo de código anterior).  
  
- Isso deve ser feito antes que <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> seja chamado. Neste exemplo, mostramos como o formatador é modificado manualmente antes de chamar <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>. Outra maneira de obter a mesma coisa é derivar uma classe de <xref:System.ServiceModel.ServiceHost> que faz as chamadas para `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` antes de abrir (consulte a documentação e exemplos de hospedagem para obter exemplos).  
  
### <a name="user-experience"></a>Experiência do usuário  
 No servidor:  
  
- A implementação do `ICalculator` do servidor não precisa ser alterada.  
  
- O app. config do serviço deve usar uma associação POX personalizada que define o atributo `messageVersion` do elemento `textMessageEncoding` como `None`.  
  
    ```xml  
    <bindings>  
      <customBinding>  
        <binding name="poxBinding">  
          <textMessageEncoding messageVersion="None" />  
          <httpTransport />  
        </binding>  
      </customBinding>  
    </bindings>  
    ```  
  
- O app. config para o serviço também deve especificar o `EnableHttpGetRequestsBehavior` personalizado adicionando-o à seção de extensões de comportamento e usando-o.  
  
    ```xml  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="enableHttpGetRequestsBehavior">  
          <enableHttpGetRequests />  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
  
    <extensions>  
      <behaviorExtensions>  
        <!-- Enabling HTTP GET requests: Behavior Extension -->  
        <add   
          name="enableHttpGetRequests"           type="Microsoft.ServiceModel.Samples.EnableHttpGetRequestsBehaviorElement, QueryStringFormatter, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
      </behaviorExtensions>  
    </extensions>  
    ```  
  
- Adicione os formatadores de operação antes de chamar <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.  
  
 No cliente:  
  
- A implementação do cliente não precisa ser alterada.  
  
- O app. config do cliente deve usar uma associação POX personalizada que define o atributo `messageVersion` do elemento `textMessageEncoding` como `None`. Uma diferença do serviço é que o cliente deve habilitar o endereçamento manual para que o endereço de saída possa ser modificado.  
  
    ```xml  
    <bindings>  
      <customBinding>  
        <binding name="poxBinding">  
          <textMessageEncoding messageVersion="None" />  
          <httpTransport manualAddressing="True" />  
        </binding>  
      </customBinding>  
    </bindings>  
    ```  
  
- O app. config do cliente deve especificar o mesmo `EnableHttpGetRequestsBehavior` personalizado que o servidor.  
  
- Adicione os formatadores de operação antes de chamar <xref:System.ServiceModel.ChannelFactory%601.CreateChannel>.  
  
 Quando você executa o exemplo, as solicitações de operação e as respostas são exibidas na janela do console do cliente. Todas as quatro operações (adicionar, subtrair, multiplicar e dividir) devem ter sucesso.  
  
> [!IMPORTANT]
> Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] amostras. Este exemplo está localizado no seguinte diretório.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Formatters\QueryStringFormatter`  
  
##### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Verifique se você executou o [procedimento de configuração única para os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Para compilar a solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Para executar o exemplo em uma configuração de computador único ou cruzado, siga as instruções em [executando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
