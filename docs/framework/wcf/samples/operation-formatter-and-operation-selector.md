---
title: Formatador de operação e seletor de operação
ms.date: 03/30/2017
ms.assetid: 1c27e9fe-11f8-4377-8140-828207b98a0e
ms.openlocfilehash: a814de7433f2d06491245dc1d6e6e637b514118a
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44065925"
---
# <a name="operation-formatter-and-operation-selector"></a>Formatador de operação e seletor de operação
Este exemplo demonstra como pontos de extensibilidade do Windows Communication Foundation (WCF) podem ser usados para permitir que os dados de mensagem em um formato diferente daquele que espera WCF. Por padrão, formatadores do WCF esperam parâmetros do método a ser incluído no `soap:body` elemento. O exemplo mostra como implementar um formatador de operação personalizada que analisa dados de parâmetro de uma cadeia de caracteres de consulta HTTP GET em vez disso e invoca métodos usando esses dados.  
  
 O exemplo se baseia a [guia de Introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md), que implementa o `ICalculator` contrato de serviço. Ele mostra como adicionar, subtrair, multiplicar e mensagens de divisão podem ser alteradas para usar o HTTP GET para solicitações de cliente-servidor e mensagens de HTTP POST com POX para respostas de servidor para cliente.  
  
 Para fazer isso, o exemplo fornece o seguinte:  
  
-   `QueryStringFormatter`, que implementa <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> e <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> para o cliente e servidor, respectivamente e processa os dados na cadeia de caracteres de consulta.  
  
-   `UriOperationSelector`, que implementa <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> no servidor para executar a expedição da operação com base no nome da operação na solicitação GET.  
  
-   `EnableHttpGetRequestsBehavior` ponto de extremidade comportamento (e a configuração correspondente), que adiciona o seletor de operação necessária para o tempo de execução.  
  
-   Mostra como inserir um novo formatador de operação no tempo de execução.  
  
-   Neste exemplo, o cliente e o serviço são aplicativos de console (.exe).  
  
> [!NOTE]
>  As instruções de procedimento e compilação de configuração para este exemplo estão localizadas no final deste tópico.  
  
## <a name="key-concepts"></a>Conceitos Principais  
 `QueryStringFormatter` -O formatador de operação é o componente no WCF que é responsável por converter uma mensagem em uma matriz de objetos de parâmetro e uma matriz de objetos de parâmetro em uma mensagem. Isso é feito no cliente usando o <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> interface e no servidor com o <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> interface. Essas interfaces permitem que os usuários obtenham as mensagens de solicitação e resposta do `Serialize` e `Deserialize` métodos.  
  
 Neste exemplo, `QueryStringFormatter` implementa duas interfaces e é implementado no cliente e servidor.  
  
 Solicitação:  
  
-   O exemplo usa o <xref:System.ComponentModel.TypeConverter> classe para converter dados de parâmetro na mensagem de solicitação em cadeias de caracteres. Se um <xref:System.ComponentModel.TypeConverter> não está disponível para um tipo específico, o gera de formatador de exemplo uma exceção.  
  
-   No `IClientMessageFormatter.SerializeRequest` método no cliente, o formatador cria um URI com o endereço apropriado e anexa o nome da operação como um sufixo. Esse nome é usado para o qual expedir a operação apropriada no servidor. Em seguida, usa a matriz de objetos de parâmetro e serializa os dados de parâmetro para a cadeia de caracteres de consulta URI usando nomes de parâmetro e os valores convertidos pelo <xref:System.ComponentModel.TypeConverter> classe. O <xref:System.ServiceModel.Channels.MessageHeaders.To%2A> e <xref:System.ServiceModel.Channels.MessageProperties.Via%2A> propriedades são definidas para esse URI. <xref:System.ServiceModel.Channels.MessageProperties> é acessado por meio de <xref:System.ServiceModel.Channels.Message.Properties%2A> propriedade.  
  
-   No `IDispatchMessageFormatter.DeserializeRequest` método no servidor, o formatador recupera o `Via` URI nas propriedades de mensagem de solicitação de entrada. Ele analisa os pares nome-valor na cadeia de caracteres de consulta URI em valores e nomes de parâmetro e usa os valores e nomes de parâmetro para preencher a matriz de parâmetros passados para o método. Observe que a expedição da operação já ocorreu, portanto, o sufixo de nome de operação é ignorado nesse método.  
  
 Resposta:  
  
-   Neste exemplo, HTTP GET é usado somente para a solicitação. O formatador delega o envio da resposta para o formatador original que seria usado para gerar uma mensagem XML. Um dos objetivos deste exemplo é mostrar como tal um formatador de delegação pode ser implementado.  
  
### <a name="uripathsuffixoperationselector-class"></a>Classe UriPathSuffixOperationSelector  
 O <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> interface permite que os usuários implementar sua própria lógica para qual operação deve ser expedida uma mensagem específica.  
  
 Neste exemplo, `UriPathSuffixOperationSelector` devem ser implementados no servidor para selecionar a operação apropriada, como o nome da operação está incluído no URI GET HTTP em vez de um cabeçalho de ação na mensagem. O exemplo está configurado para permitir que os nomes de operação somente maiusculas de minúsculas.  
  
 O `SelectOperation` método recebe a mensagem de entrada e procura o `Via` URI em suas propriedades de mensagem. Ele extrai o sufixo de nome de operação do URI, procura uma tabela interna para obter o nome da operação que a mensagem deve ser expedida para e retorna esse nome de operação.  
  
### <a name="enablehttpgetrequestsbehavior-class"></a>Classe EnableHttpGetRequestsBehavior  
 O `UriPathSuffixOperationSelector` componente pode ser configurado programaticamente ou por meio de um comportamento de ponto de extremidade. O exemplo implementa o `EnableHttpGetRequestsBehavior` comportamento, que é especificado no arquivo de configuração de aplicativo do serviço.  
  
 No servidor:  
  
 O <xref:System.ServiceModel.Dispatcher.DispatchRuntime.OperationSelector%2A> é definido como o <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> implementação.  
  
 Por padrão, o WCF usa um filtro de endereço de correspondência exata. O URI na mensagem de entrada contém um sufixo de nome de operação seguido por uma cadeia de caracteres de consulta que contém os dados de parâmetro, portanto, o comportamento de ponto de extremidade também altera o filtro de endereço para ser um prefixo correspondem ao filtro. Ele usa o WCF<xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> para essa finalidade.  
  
### <a name="installing-operation-formatters"></a>Instalando os formatadores de operação  
 Comportamentos de operação que especificam os formatadores são exclusivos. Um tal comportamento sempre é implementado por padrão para cada operação criar o formatador de operação necessária. No entanto, esses comportamentos se parecer com o comportamento de qualquer outra operação; eles não são identificáveis por qualquer outro atributo. Para instalar um comportamento de substituição, a implementação deve procurar comportamentos de formatador específicas que são instalados pelo carregador do tipo de WCF por padrão e ou substituí-lo ou adicionar um comportamento compatível com a ser executado após o comportamento padrão.  
  
 Esses comportamentos de formatadores de operação podem ser configurados por meio de programação antes de chamar <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A?displayProperty=nameWithType> ou especificando um comportamento de operação é executado após o padrão. No entanto, ele não pode ser facilmente configurado por um comportamento de ponto de extremidade (e, portanto, pela configuração) porque o modelo de comportamento não permite um comportamento substituir outros comportamentos ou caso contrário, modificar a árvore de descrição.  
  
 No cliente:  
  
 O <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> implementação deve ser implementada para que ele possa converter as solicitações em solicitações HTTP GET e delegar ao formatador para respostas original. Isso é feito chamando o `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` método auxiliar.  
  
 Isso deve ser feito antes de chamar `CreateChannel`.  
  
```  
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
  
-   O <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> interface deve ser implementada para que ele pode ler as solicitações HTTP GET e delegar para o formatador original para gravação de respostas. Isso é feito chamando o mesmo `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` método auxiliar que o cliente (consulte o exemplo de código anterior).  
  
-   Isso deve ser feito antes de <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> é chamado. Neste exemplo, vamos mostrar como o formatador manualmente é modificado antes de chamar <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>. Outra maneira de atingir a mesma coisa é derivar uma classe de <xref:System.ServiceModel.ServiceHost> que faz as chamadas para `EnableHttpGetRequestsBehavior.ReplaceFormatterBehavior` antes de abrir (consulte documentação e exemplos para obter exemplos de hospedagem).  
  
### <a name="user-experience"></a>Experiência do usuário  
 No servidor:  
  
-   O servidor `ICalculator` implementação não precisa alterar.  
  
-   App. config para o serviço deve usar uma ligação personalizada POX que define o `messageVersion` atributo o `textMessageEncoding` elemento a ser `None`.  
  
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
  
-   O App. config para o serviço também deve especificar personalizado `EnableHttpGetRequestsBehavior` adicionando-o para a seção de extensões de comportamento e usá-lo.  
  
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
  
-   Adicionar operação formatadores antes de chamar <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.  
  
 No cliente:  
  
-   A implementação do cliente não precisa alterar.  
  
-   App. config para o cliente deve usar uma ligação personalizada POX que define o `messageVersion` atributo o `textMessageEncoding` elemento a ser `None`. Uma diferença do serviço é que o cliente deve habilitar o endereçamento manual para que o endereço de saída pode ser modificada.  
  
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
  
-   O App. config para o cliente deve especificar o mesmo personalizado `EnableHttpGetRequestsBehavior` como o servidor.  
  
-   Adicionar operação formatadores antes de chamar <xref:System.ServiceModel.ChannelFactory%601.CreateChannel>.  
  
 Quando você executar o exemplo, as respostas e solicitações de operação são exibidas na janela do console de cliente. Todas as quatro operações (Adicionar, subtrair, multiplicar e dividir) deve ter êxito.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Formatters\QuieryStringFormatter`  
  
##### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Para criar a solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="see-also"></a>Consulte também
