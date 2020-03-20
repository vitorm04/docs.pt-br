---
title: Formatador de operação e seletor de operação
ms.date: 03/30/2017
ms.assetid: 1c27e9fe-11f8-4377-8140-828207b98a0e
ms.openlocfilehash: 9d1bc0afa54f89e064eab3f3e45da60c8d10de38
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144273"
---
# <a name="operation-formatter-and-operation-selector"></a>Formatador de operação e seletor de operação
Esta amostra demonstra como os pontos de extensibilidade da Windows Communication Foundation (WCF) podem ser usados para permitir dados de mensagens em um formato diferente do que o WCF espera. Por padrão, os assuntos do WCF esperam `soap:body` que os parâmetros do método sejam incluídos o elemento. A amostra mostra como implementar uma operação personalizada que analisa dados de parâmetros de uma seqüência de consultas HTTP GET e invoca métodos usando esses dados.  
  
 A amostra é baseada no [Getting](../../../../docs/framework/wcf/samples/getting-started-sample.md)Started `ICalculator` , que implementa o contrato de serviço. Ele mostra como as mensagens Add, Subtract, Multiply e Divide podem ser alteradas para usar http get para solicitações de cliente para servidor e POST HTTP com mensagens POX para respostas de servidor para cliente.  
  
 Para isso, a amostra fornece o seguinte:  
  
- `QueryStringFormatter`, que <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> implementa e <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> para o cliente e servidor, respectivamente, e processa os dados na cadeia de consulta.  
  
- `UriOperationSelector`, que <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> implementa no servidor para executar o envio de operação com base no nome da operação na solicitação GET.  
  
- `EnableHttpGetRequestsBehavior`comportamento de ponto final (e configuração correspondente), que adiciona o seletor de operação necessário ao tempo de execução.  
  
- Mostra como inserir uma nova operação no tempo de execução.  
  
- Nesta amostra, tanto o cliente quanto o serviço são aplicativos de console (.exe).  
  
> [!NOTE]
> O procedimento de configuração e as instruções de construção desta amostra estão localizados no final deste tópico.  
  
## <a name="key-concepts"></a>Conceitos Principais  
 `QueryStringFormatter`- A matéria-atacante de operação é o componente no WCF que é responsável por converter uma mensagem em uma matriz de objetos de parâmetro e uma matriz de objetos de parâmetro em uma mensagem. Isso é feito no <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> cliente usando a interface <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> e no servidor com a interface. Essas interfaces permitem que os usuários obtenham `Serialize` `Deserialize` as mensagens de solicitação e resposta dos métodos e.  
  
 Nesta amostra, `QueryStringFormatter` implementa ambas as interfaces e é implementada no cliente e servidor.  
  
 Solicitação:  
  
- A amostra <xref:System.ComponentModel.TypeConverter> usa a classe para converter dados de parâmetros na mensagem de solicitação para e a partir de strings. Se <xref:System.ComponentModel.TypeConverter> a não estiver disponível para um tipo específico, a matéria-guia da amostra abre uma exceção.  
  
- No `IClientMessageFormatter.SerializeRequest` método no cliente, o formatter cria um URI com o endereço apropriado e anexa o nome da operação como um sufixo. Este nome é usado para despachar para a operação apropriada no servidor. Em seguida, ele pega a matriz de objetos de parâmetro e serializa os dados de parâmetro <xref:System.ComponentModel.TypeConverter> para a seqüência de consulta uri usando nomes de parâmetros e os valores convertidos pela classe. As <xref:System.ServiceModel.Channels.MessageHeaders.To%2A> <xref:System.ServiceModel.Channels.MessageProperties.Via%2A> propriedades e propriedades são então definidas para este URI. <xref:System.ServiceModel.Channels.MessageProperties>é acessado através <xref:System.ServiceModel.Channels.Message.Properties%2A> da propriedade.  
  
- No `IDispatchMessageFormatter.DeserializeRequest` método no servidor, o formatter `Via` recupera o URI nas propriedades de mensagem de solicitação recebidas. Ele analisa os pares de valor de nome na seqüência de consulta uri em nomes e valores de parâmetros e usa os nomes e valores dos parâmetros para preencher a matriz de parâmetros passados para o método. Observe que o despacho de operação já ocorreu, de modo que o sufixo nome da operação é ignorado neste método.  
  
 Resposta:  
  
- Nesta amostra, HTTP GET é usado apenas para a solicitação. A matéria-geral delega o envio da resposta ao formatter original que teria sido usado para gerar uma mensagem XML. Um dos objetivos desta amostra é mostrar como essa matéria delegante pode ser implementada.  
  
### <a name="uripathsuffixoperationselector-class"></a>UriPathSuffixClasseClasseClasseSelector  
 A <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> interface permite que os usuários implementem sua própria lógica para a qual operação uma determinada mensagem deve ser enviada.  
  
 Nesta amostra, `UriPathSuffixOperationSelector` deve ser implementado no servidor para selecionar a operação apropriada porque o nome da operação está incluído no HTTP GET URI em vez de um cabeçalho de ação na mensagem. A amostra é configurada para permitir apenas nomes de operação insensíveis a casos.  
  
 O `SelectOperation` método pega a mensagem `Via` recebida e procura o URI em suas propriedades de mensagem. Ele extrai o sufixo de nome de operação do URI, procura uma tabela interna para obter o nome da operação para o qual a mensagem deve ser enviada e retorna o nome da operação.  
  
### <a name="enablehttpgetrequestsbehavior-class"></a>AtivarhttpGetRequestsClasse de comportamento  
 O `UriPathSuffixOperationSelector` componente pode ser configurado programáticamente ou através de um comportamento de ponto final. A amostra implementa o `EnableHttpGetRequestsBehavior` comportamento, que é especificado no arquivo de configuração do aplicativo do serviço.  
  
 No servidor:  
  
 O <xref:System.ServiceModel.Dispatcher.DispatchRuntime.OperationSelector%2A> está definido <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> para a implementação.  
  
 Por padrão, o WCF usa um filtro de endereço de correspondência exata. O URI na mensagem recebida contém um sufixo de nome de operação seguido de uma seqüência de consultas que contém dados de parâmetros, de modo que o comportamento do ponto final também altera o filtro de endereço para ser um filtro de correspondência de prefixo. Ele usa o<xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> WCF para este fim.  
  
### <a name="installing-operation-formatters"></a>Instalação de operações formatters  
 Os comportamentos de operação que especificam assuntos formais são únicos. Um desses comportamentos é sempre implementado por padrão para cada operação para criar a operação necessária. No entanto, esses comportamentos parecem apenas mais um comportamento de operação; eles não são identificáveis por qualquer outro atributo. Para instalar um comportamento de substituição, a implementação deve procurar comportamentos específicos de matéria que são instalados pelo carregador de tipo WCF por padrão e substituí-lo ou adicionar um comportamento compatível para executar após o comportamento padrão.  
  
 Esses comportamentos de operações podem ser configurados <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A?displayProperty=nameWithType> programáticamente antes de ligar ou especificando um comportamento de operação que é executado após o padrão. No entanto, ele não pode ser facilmente configurado por um comportamento de ponto final (e, portanto, por configuração) porque o modelo de comportamento não permite que um comportamento substitua outros comportamentos ou modifique a árvore de descrição.  
  
 No cliente:  
  
 A <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> implementação deve ser implementada para que possa converter as solicitações em solicitações HTTP GET e delegar ao formatter original para respostas. Isso é feito `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` chamando o método auxiliar.  
  
 Isso deve ser `CreateChannel`feito antes de chamar.  
  
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
  
- A <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> interface deve ser implementada para que possa ler as solicitações HTTP GET e delegar ao formatter original para escrever respostas. Isso é feito chamando o mesmo `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` método auxiliar que o cliente (veja a amostra de código anterior).  
  
- Isso deve ser <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> feito antes que seja chamado. Nesta amostra, mostramos como a matéria formatéria <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>é modificada manualmente antes de chamar . Outra maneira de conseguir a mesma coisa <xref:System.ServiceModel.ServiceHost> é obter `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` uma classe que faz as chamadas para antes de abrir (consulte documentação de hospedagem e amostras por exemplo).  
  
### <a name="user-experience"></a>Experiência do usuário  
 No servidor:  
  
- A `ICalculator` implementação do servidor não precisa ser mudada.  
  
- O App.config para o serviço deve usar `messageVersion` uma vinculação POX personalizada que define o atributo `textMessageEncoding` do elemento como `None`.  
  
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
  
- O App.config para o serviço `EnableHttpGetRequestsBehavior` também deve especificar o costume adicionando-o à seção de extensões de comportamento e usando-o.  
  
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
  
- Adicione a operação <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>para assuntos antes de chamar .  
  
 No cliente:  
  
- A implementação do cliente não precisa mudar.  
  
- O App.config para o cliente deve usar `messageVersion` uma vinculação POX personalizada que define o atributo `textMessageEncoding` do elemento para `None`. Uma diferença em relação ao serviço é que o cliente deve habilitar endereçamento manual para que o endereço de saída para ser modificado.  
  
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
  
- O App.config para o cliente `EnableHttpGetRequestsBehavior` deve especificar o mesmo costume que o servidor.  
  
- Adicione a operação <xref:System.ServiceModel.ChannelFactory%601.CreateChannel>para assuntos antes de chamar .  
  
 Quando você executa a amostra, as solicitações e respostas da operação são exibidas na janela do console cliente. Todas as quatro operações (Adicionar, Subtrair, Multiplicar e Dividir) devem ter sucesso.  
  
> [!IMPORTANT]
> Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation). Este exemplo está localizado no seguinte diretório.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Formatters\QueryStringFormatter`  
  
##### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Para construir a solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Para executar a amostra em uma configuração de máquina única ou cruzada, siga as instruções em [Executar as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
