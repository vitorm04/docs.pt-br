---
title: Visão geral da arquitetura de transferência de dados
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data transfer [WCF], architectural overview
ms.assetid: 343c2ca2-af53-4936-a28c-c186b3524ee9
ms.openlocfilehash: 69032a04067311f4df3696474dfc9ad4df465f51
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="data-transfer-architectural-overview"></a>Visão geral da arquitetura de transferência de dados
Windows Communication Foundation (WCF) pode ser pensada como uma infraestrutura de mensagens. Pode receber mensagens, processá-los e distribuição para o código de usuário para uma ação adicional, ou pode criar mensagens de dados fornecidos pelo código do usuário e enviá-las para um destino. Neste tópico, que é direcionado para desenvolvedores avançados, descreve a arquitetura de processamento de mensagens e os dados contidos. Para uma exibição mais simples e orientada a tarefas de como enviar e receber dados, consulte [especificando a transferência de dados em contratos de serviço](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md).  
  
> [!NOTE]
>  Este tópico discute os detalhes de implementação de WCF que não são visíveis, examinando o modelo de objeto do WCF. Duas palavras de cuidado estão na ordem em relação ao detalhes de implementação documentadas. Primeiro, as descrições são simplificadas; implementação real pode ser mais complexa devido a otimizações ou outros motivos. Em segundo lugar, você nunca deve confiar em detalhes específicos de implementação, até mesmo documentado importantes, porque eles podem ser alterados sem aviso prévio de versão para a versão ou até mesmo em uma versão de serviço.  
  
## <a name="basic-architecture"></a>Arquitetura básica  
 Os principais recursos de manipulação de mensagens do WCF é o <xref:System.ServiceModel.Channels.Message> classe, que é descrita detalhadamente no [usando a classe de mensagem](../../../../docs/framework/wcf/feature-details/using-the-message-class.md). Os componentes de tempo de execução do WCF podem ser divididos em duas partes principais: a pilha de canais e a estrutura do serviço, com o <xref:System.ServiceModel.Channels.Message> classe sendo o ponto de conexão.  
  
 A pilha de canais é responsável pela conversão entre um válida <xref:System.ServiceModel.Channels.Message> instância e alguma ação que corresponde ao envio ou recebimento de dados da mensagem. No lado de envio, a pilha de canais usa válido <xref:System.ServiceModel.Channels.Message> instância e, depois de algum processamento, executa alguma ação que logicamente corresponde ao enviar a mensagem. A ação pode estar enviando pacotes TCP ou HTTP, enfileiramento de mensagens no enfileiramento de mensagens, a mensagem de gravação para um banco de dados, salvando-o em um compartilhamento de arquivos, ou qualquer outra ação, dependendo da implementação. A ação mais comum está enviando a mensagem por meio de um protocolo de rede. No lado de recebimento, o oposto acontece — uma ação for detectada (que pode ser HTTP ou TCP pacotes que chegam ou qualquer outra ação) e, após o processamento, a pilha de canais converte essa ação em uma opção válida <xref:System.ServiceModel.Channels.Message> instância.  
  
 Você pode usar o WCF usando o <xref:System.ServiceModel.Channels.Message> classe e o canal de pilha diretamente. No entanto, fazer isso é difícil e demorado. Além disso, o <xref:System.ServiceModel.Channels.Message> objeto não fornece metadados suporte, portanto você não pode gerar fortemente tipados clientes do WCF, se você usar o WCF dessa maneira.  
  
 Portanto, o WCF inclui uma estrutura de serviço que fornece um modelo de programação de fácil de usar que você pode usar para construir e receber `Message` objetos. Estrutura do serviço de mapas de serviços para [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] tipos por meio da noção de contratos de serviço e distribui as mensagens para operações de usuário que são simplesmente [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] métodos marcados com o <xref:System.ServiceModel.OperationContractAttribute> atributo (para obter mais detalhes, consulte [Criando contratos de serviço](../../../../docs/framework/wcf/designing-service-contracts.md)). Esses métodos podem ter parâmetros e retornar valores. No lado do serviço, a estrutura do serviço converte entrada <xref:System.ServiceModel.Channels.Message> valores de retorno de instâncias em parâmetros e o converte em saída <xref:System.ServiceModel.Channels.Message> instâncias. No lado do cliente, ele faz o oposto. Por exemplo, considere o `FindAirfare` operação abaixo.  
  
 [!code-csharp[c_DataArchitecture#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#1)]
 [!code-vb[c_DataArchitecture#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#1)]  
  
 Suponha que `FindAirfare` é chamado no cliente. A estrutura do serviço no cliente converte o `FromCity` e `ToCity` parâmetros em uma saída <xref:System.ServiceModel.Channels.Message> instância e passá-lo para a pilha de canais para serem enviadas.  
  
 No lado do serviço, quando um <xref:System.ServiceModel.Channels.Message> instância chega da pilha de canais, a estrutura do serviço de extrai os dados relevantes de mensagem para preencher o `FromCity` e `ToCity` parâmetros e, em seguida, chama o lado do serviço `FindAirfare` método. Quando o método retorna, a estrutura de serviço usa o valor inteiro retornado e o `IsDirectFlight` parâmetro de saída e cria um <xref:System.ServiceModel.Channels.Message> instância do objeto que contém essas informações. Ele passa a `Message` instância para a pilha de canais para ser enviada de volta ao cliente.  
  
 No lado do cliente, um <xref:System.ServiceModel.Channels.Message> surge de instância que contém a mensagem de resposta da pilha de canais. Estrutura do serviço de extrai o valor de retorno e o `IsDirectFlight` de valor e retorna-os para o chamador do cliente.  
  
## <a name="message-class"></a>Classe de mensagem  
 O <xref:System.ServiceModel.Channels.Message> classe deve ser uma representação abstrata de uma mensagem, mas seu design fortemente é vinculado à mensagem SOAP. Um <xref:System.ServiceModel.Channels.Message> contém três partes principais de informações: um corpo de mensagem, cabeçalhos de mensagem e propriedades da mensagem.  
  
## <a name="message-body"></a>Corpo da mensagem  
 O corpo da mensagem é serve para representar a carga de dados real da mensagem. O corpo da mensagem sempre é representado como um XML Infoset. Isso não significa que todas as mensagens criadas ou recebidas no WCF devem estar no formato XML. Cabe a pilha de canais para decidir como interpretar o corpo da mensagem. Ele pode emiti-lo como XML, convertê-la em outro formato ou mesmo omiti-lo inteiramente. É claro que, com a maioria das fontes WCF de associações, o corpo da mensagem é representado como conteúdo XML na seção de corpo de um envelope SOAP.  
  
 É importante observar que o `Message` classe não contém necessariamente um buffer de dados XML que representa o corpo. Logicamente, `Message` contém um XML Infoset, mas esse Infoset pode ser construída dinamicamente e nunca fisicamente pode existir na memória.  
  
### <a name="putting-data-into-the-message-body"></a>Colocar dados no corpo da mensagem  
 Não há nenhum mecanismo uniforme para colocar dados em um corpo de mensagem. O <xref:System.ServiceModel.Channels.Message> classe tem um método abstrato, <xref:System.ServiceModel.Channels.Message.OnWriteBodyContents%28System.Xml.XmlDictionaryWriter%29>, que usa um <xref:System.Xml.XmlDictionaryWriter>. Cada subclasse do <xref:System.ServiceModel.Channels.Message> classe é responsável por substituir esse método e gravar seu próprio conteúdo. O corpo da mensagem contém logicamente Infoset XML que `OnWriteBodyContent` produz. Por exemplo, considere o seguinte `Message` subclasse.  
  
 [!code-csharp[c_DataArchitecture#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#2)]
 [!code-vb[c_DataArchitecture#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#2)]  
  
 Fisicamente, um `AirfareRequestMessage` instância contém apenas duas cadeias de caracteres ("fromCity" e "toCity"). No entanto, logicamente a mensagem contém o infoset XML a seguir:  
  
```xml  
<airfareRequest>  
    <from>Tokyo</from>  
    <to>London</to>  
</airfareRequest>  
```  
  
 Naturalmente, você normalmente não criaria mensagens dessa maneira, como você pode usar a estrutura de serviço para criar uma mensagem semelhante à anterior da operação de parâmetros de contrato. Além disso, o <xref:System.ServiceModel.Channels.Message> classe tem estático `CreateMessage` métodos que você pode usar para criar as mensagens com tipos comuns de conteúdo: uma mensagem vazia, uma mensagem que contém um objeto serializado como XML com o <xref:System.Runtime.Serialization.DataContractSerializer>, uma mensagem que contém um SOAP Falha, uma mensagem que contém XML representado por um <xref:System.Xml.XmlReader>, e assim por diante.  
  
### <a name="getting-data-from-a-message-body"></a>Obtendo dados de um corpo de mensagem  
 Você pode extrair os dados armazenados no corpo da mensagem de duas maneiras principais:  
  
-   Você pode obter o corpo da mensagem inteira de uma só vez chamando o <xref:System.ServiceModel.Channels.Message.WriteBodyContents%28System.Xml.XmlDictionaryWriter%29> método e passando um gravador de XML. O corpo da mensagem completa é gravado para este gravador. Obter o corpo da mensagem inteira de uma só vez também é chamado *escrever uma mensagem*. Gravação é feita principalmente através da pilha de canais ao enviar mensagens — alguma parte da pilha de canais geralmente obterá acesso ao corpo da mensagem inteira, codificá-lo e enviá-lo.  
  
-   Outra maneira de obter informações fora do corpo da mensagem é chamar <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents> e obter um leitor de XML. O corpo da mensagem, em seguida, pode ser acessado em sequência, conforme necessário, chamando métodos do leitor. Obtendo a mensagem corpo parte-por-parte também é chamado *ler uma mensagem*. Ler a mensagem é usado basicamente pela estrutura do serviço de durante o recebimento de mensagens. Por exemplo, quando o <xref:System.Runtime.Serialization.DataContractSerializer> está em uso, a estrutura do serviço de obter um leitor de XML sobre o corpo e passá-lo para o mecanismo de desserialização, o que iniciará o mensagem elemento por elemento de leitura e construir o gráfico de objeto correspondente.  
  
 Um corpo de mensagem pode ser recuperado de uma só vez. Isso torna possível trabalhar com fluxos de somente avanço. Por exemplo, você pode escrever um <xref:System.ServiceModel.Channels.Message.OnWriteBodyContents%28System.Xml.XmlDictionaryWriter%29> substituição que lê um <xref:System.IO.FileStream> e retorna os resultados como um XML Infoset. Nunca será necessário "retroceder" para o início do arquivo.  
  
 O `WriteBodyContents` e `GetReaderAtBodyContents` métodos simplesmente Verifique se o corpo da mensagem nunca tiver sido recuperado antes e, em seguida, chamar `OnWriteBodyContents` ou `OnGetReaderAtBodyContents`, respectivamente.  
  
## <a name="message-usage-in-wcf"></a>Uso de mensagem no WCF  
 A maioria das mensagens podem ser classificadas como *saída* (aquelas que são criados pela estrutura do serviço a ser enviado pela pilha de canal) ou *entrada* (aquelas que chegam no canal de pilha e são interpretado pela estrutura do serviço). Além disso, a pilha de canais pode operar em modo de buffer ou de streaming. A estrutura de serviço também pode expor um modelo de programação transmitido ou nonstreamed. Isso leva a casos listados na tabela a seguir, juntamente com detalhes simplificadas de sua implementação.  
  
|Tipo de mensagem|Dados do corpo de mensagem|Implementação de gravação (OnWriteBodyContents)|Implementação de leitura (OnGetReaderAtBodyContents)|  
|------------------|--------------------------|--------------------------------------------------|-------------------------------------------------------|  
|Saída, criado a partir de modelo de programação nonstreamed|Os dados necessários para a mensagem de gravação (por exemplo, um objeto e o <xref:System.Runtime.Serialization.DataContractSerializer> instância necessária para serializá-lo) *|A lógica personalizada para gravar a mensagem com base em dados armazenados (por exemplo, chamar `WriteObject` no `DataContractSerializer` se esse for o serializador em uso) *|Chamar `OnWriteBodyContents`, os resultados de buffer, retornar um leitor de XML no buffer|  
|Saída, criado a partir de modelo de programação em fluxo|O `Stream` com os dados a serem gravados *|Gravar dados do fluxo armazenado usando o <xref:System.Xml.IStreamProvider> mecanismo *|Chamar `OnWriteBodyContents`, os resultados de buffer, retornar um leitor de XML no buffer|  
|Entrada da pilha de canais de streaming|Um `Stream` objeto que representa os dados sobre a rede com um <xref:System.Xml.XmlReader> sobre ele|Gravar o conteúdo de armazenado `XmlReader` usando `WriteNode`|Retorna o armazenado `XmlReader`|  
|Entrada da pilha de canais nonstreaming|Um buffer que contém o corpo de dados com um `XmlReader` sobre ele|Grava o conteúdo de armazenado `XmlReader` usando `WriteNode`|Retorna o lang armazenado|  
  
 \* Esses itens não são implementados diretamente no `Message` subclasses, mas em subclasses de <xref:System.ServiceModel.Channels.BodyWriter> classe. Para obter mais informações sobre o <xref:System.ServiceModel.Channels.BodyWriter>, consulte [usando a classe de mensagem](../../../../docs/framework/wcf/feature-details/using-the-message-class.md).  
  
## <a name="message-headers"></a>Cabeçalhos de mensagem  
 Uma mensagem pode conter cabeçalhos. Logicamente, um cabeçalho consiste em um Infoset XML que está associado com um nome, um namespace e algumas outras propriedades. Cabeçalhos de mensagem são acessados usando o `Headers` propriedade <xref:System.ServiceModel.Channels.Message>. Cada cabeçalho é representado por um <xref:System.ServiceModel.Channels.MessageHeader> classe. Normalmente, os cabeçalhos de mensagem são mapeados para cabeçalhos de mensagem SOAP ao usar uma pilha de canais configurada para trabalhar com mensagens SOAP.  
  
 Colocar as informações em um cabeçalho de mensagem e extrair informações dele são semelhante a usar o corpo da mensagem. O processo é um pouco simplificado porque não há suporte para streaming. É possível acessar o conteúdo do cabeçalho do mesmo mais de uma vez e cabeçalhos podem ser acessados na ordem arbitrária, forçando cabeçalhos sempre serem armazenados em buffer. Não há nenhum mecanismo de uso geral disponível para obter um leitor de XML em um cabeçalho de, mas não há um `MessageHeader` subclasse interno para o WCF que representa um cabeçalho legível com esse recurso. Esse tipo de `MessageHeader` é criado pela pilha de canais quando chega uma mensagem com cabeçalhos de aplicativo personalizado. Isso permite que a estrutura do serviço usar um mecanismo de desserialização, como o <xref:System.Runtime.Serialization.DataContractSerializer>, interpretar esses cabeçalhos.  
  
 Para obter mais informações, consulte [usando a classe de mensagem](../../../../docs/framework/wcf/feature-details/using-the-message-class.md).  
  
## <a name="message-properties"></a>Propriedades de mensagem  
 Uma mensagem pode conter propriedades. Um *propriedade* é qualquer [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] objeto que está associado com um nome de cadeia de caracteres. Propriedades são acessadas por meio de `Properties` propriedade `Message`.  
  
 Ao contrário do corpo da mensagem e os cabeçalhos de mensagem (que normalmente mapeiam para o corpo SOAP e os cabeçalhos SOAP, respectivamente), é possível que as propriedades de mensagem normalmente não são enviadas ou recebidas junto com as mensagens. Propriedades de mensagem existem principalmente como um mecanismo de comunicação para passar dados sobre a mensagem entre os diversos canais na pilha de canais e entre a pilha de canais e o modelo de serviço.  
  
 Por exemplo, o canal de transporte HTTP incluído como parte do WCF é capaz de gerar vários códigos de status HTTP, como "404 (não encontrado)" e "500 (erro interno do servidor)," quando ele envia respostas a clientes. Antes de enviar uma mensagem de resposta, ele verifica se o `Properties` do `Message` contém uma propriedade chamada "httpResponse" que contém um objeto do tipo <xref:System.ServiceModel.Channels.HttpResponseMessageProperty>. Se essa propriedade for encontrada, ele examinará os <xref:System.ServiceModel.Channels.HttpResponseMessageProperty.StatusCode%2A> propriedade e usar esse código de status. Se ele não for encontrado, o padrão "200 (Okey)" código é usado.  
  
 Para obter mais informações, consulte [usando a classe de mensagem](../../../../docs/framework/wcf/feature-details/using-the-message-class.md).  
  
### <a name="the-message-as-a-whole"></a>A mensagem como um todo  
 Até agora, discutimos métodos para acessar as diversas partes da mensagem em isolamento. No entanto, a <xref:System.ServiceModel.Channels.Message> classe também fornece métodos para trabalhar com a mensagem inteira como um todo. Por exemplo, o `WriteMessage` método grava a mensagem inteira para um gravador XML.  
  
 Para que isso seja possível, um mapeamento deve ser definido entre todo o `Message` instância e um XML Infoset. Na verdade, existe um mapeamento,: WCF usa o padrão de SOAP para definir esse mapeamento. Quando um `Message` instância é gravado como um XML Infoset Infoset resultante é o envelope SOAP válido que contém a mensagem. Portanto, `WriteMessage` normalmente deve executar as seguintes etapas:  
  
1.  Grave o elemento de envelope SOAP marca de abertura.  
  
2.  Gravar o elemento de cabeçalho SOAP marca de abertura, gravar todos os cabeçalhos e fechar o elemento de cabeçalho.  
  
3.  Grave o elemento de corpo SOAP marca de abertura.  
  
4.  Chamar `WriteBodyContents` ou um método equivalente para gravar o corpo.  
  
5.  Feche os elementos do corpo e envelope.  
  
 As etapas anteriores são rigorosamente associadas com o padrão de SOAP. Isso é complicado pelo fato de que várias versões de SOAP existem, por exemplo, não é possível gravar o elemento de envelope SOAP corretamente sem saber a versão SOAP em uso. Além disso, em alguns casos, pode ser desejável para desativar este específicas de SOAP complexa mapeamento completamente.  
  
 Para esses fins, um `Version` é fornecida em `Message`. Pode ser definido para a versão SOAP a ser usado ao gravar a mensagem, ou ele pode ser definido como `None` para evitar qualquer mapeamento específicas de SOAP. Se o `Version` está definida como `None`, métodos que funcionam com o ato de mensagem inteira como se a mensagem consistiu em seu corpo, por exemplo, `WriteMessage` simplesmente chamar `WriteBodyContents` em vez de executar várias etapas listadas acima. Espera-se que em mensagens de entrada, `Version` será detectado automaticamente e configurado corretamente.  
  
## <a name="the-channel-stack"></a>A pilha de canais  
  
### <a name="channels"></a>Canais  
 Conforme mencionado anteriormente, a pilha de canais é responsável por converter a saída <xref:System.ServiceModel.Channels.Message> instâncias em alguma ação (como o envio de pacotes de rede) ou conversão de alguma ação (como receber pacotes de rede) em entrada `Message` instâncias.  
  
 A pilha de canais é composta de um ou mais canais ordenados em uma sequência. Uma saída `Message` instância é passada para o primeiro canal na pilha (também chamado de *canal mais alto*), que passa para o próximo canal para baixo na pilha e assim por diante. A mensagem termina no último canal, que é chamado de *canal de transporte*. Mensagens de entrada são originadas no canal de transporte e são passadas de canal na pilha. Do canal mais alto, a mensagem geralmente é passada na estrutura de serviço. Embora esse seja o padrão comum para as mensagens de aplicativo, alguns canais podem funcionar de forma ligeiramente diferente, por exemplo, eles podem enviar suas próprias mensagens de infraestrutura sem serem passados a uma mensagem de um canal acima.  
  
 Canais podem operar na mensagem de várias maneiras, conforme ele passa por meio da pilha. A operação mais comum é a adição de um cabeçalho de uma mensagem de saída e ler os cabeçalhos em uma mensagem de entrada. Por exemplo, um canal pode calcular a assinatura digital de uma mensagem e adicioná-lo como um cabeçalho. Um canal também pode inspecionar esse cabeçalho de assinatura digital em mensagens de entrada e bloquear mensagens que não têm uma assinatura válida de fazer sua forma a pilha de canais. Canais também costuma ser definido ou Inspecione as propriedades de mensagem. O corpo da mensagem é geralmente não modificado, embora isso é permitido, por exemplo, o canal de segurança do WCF pode criptografar o corpo da mensagem.  
  
### <a name="transport-channels-and-message-encoders"></a>Canais de transporte e codificadores de mensagem  
 O canal mais baixo na pilha é responsável por transformar, na verdade, uma saída <xref:System.ServiceModel.Channels.Message>, conforme modificado por outros canais em alguma ação. No lado de recebimento, esse é o canal que converte alguma ação em um `Message` que outros canais de processo.  
  
 Como mencionado anteriormente, as ações podem ser variadas: enviar ou receber pacotes de rede em vários protocolos, ler ou gravar a mensagem em um banco de dados ou enfileiramento de mensagens ou removê-la fila a mensagem na fila de enfileiramento de mensagens, para fornecer, mas alguns exemplos. Todas essas ações têm algo em comum: eles requerem uma transformação entre o WCF`Message` instância e um grupo real de bytes que pode ser enviada, recebida, ler, escrito, na fila ou removida da fila. O processo de converter um `Message` em um grupo de bytes é chamado *codificação*e o processo inverso da criação de um `Message` de um grupo de bytes é chamado *decodificação*.  
  
 A maioria dos canais de transporte usam componentes chamados *codificadores de mensagem* para realizar a codificação e decodificação de trabalho. Um codificador de mensagem é uma subclasse do <xref:System.ServiceModel.Channels.MessageEncoder> classe. `MessageEncoder` inclui vários `ReadMessage` e `WriteMessage` sobrecargas do método para converter entre `Message` e grupos de bytes.  
  
 No lado de envio, um canal de transporte buffer passa o `Message` objeto recebida de um canal acima para `WriteMessage`. Ele obtém de volta uma matriz de bytes, que ele usa para executar a ação (como empacotar esses bytes como pacotes TCP válidos e enviá-los para o destino correto). Primeiro cria um canal de transporte streaming um `Stream` (por exemplo, mais a saída TCP conexão) e, em seguida, passa o `Stream` e o `Message` que precisa para enviar ao apropriado `WriteMessage` sobrecarga, que grava a mensagem .  
  
 No lado de recepção, um canal de transporte buffer extrai bytes de entrada (por exemplo, de pacotes de entrada TCP) em uma matriz e chamadas `ReadMessage` para obter um `Message` que pode passar mais acima na pilha de canal do objeto. Cria um canal de transporte streaming um `Stream` objeto (por exemplo, um fluxo de rede sobre a conexão de TCP de entrada) e passa para `ReadMessage` para retornar um `Message` objeto.  
  
 A separação entre os canais de transporte e o codificador de mensagem não é obrigatória. é possível gravar um canal de transporte que não usa um codificador de mensagem. No entanto, a vantagem dessa separação é a facilidade de composição. Como um canal de transporte usa apenas a base <xref:System.ServiceModel.Channels.MessageEncoder>, ele pode funcionar com qualquer WCF ou o codificador de mensagem de terceiros. Da mesma forma, o mesmo codificador normalmente pode ser usado em qualquer canal de transporte.  
  
### <a name="message-encoder-operation"></a>Operação de codificador de mensagem  
 Para descrever a uma operação típica de um codificador, é útil considerar quatro casos a seguir.  
  
|Operação|Comentário|  
|---------------|-------------|  
|Codificação, armazenada em buffer|No modo de buffer, o codificador normalmente cria um buffer de tamanho variável e, em seguida, cria um gravador de XML sobre ele. Depois, ele chama <xref:System.ServiceModel.Channels.Message.WriteMessage%28System.Xml.XmlWriter%29> na mensagem que está sendo codificada, que grava os cabeçalhos e, em seguida, o corpo, usando <xref:System.ServiceModel.Channels.Message.WriteBodyContents%28System.Xml.XmlDictionaryWriter%29>, conforme explicado na seção anterior sobre `Message` neste tópico. O conteúdo do buffer (representado como uma matriz de bytes), em seguida, é retornado para o canal de transporte a ser usado.|  
|Streaming de codificação,|No modo de fluxo, a operação é semelhante a acima, mas mais simples. Não é necessário para um buffer. Um gravador de XML é normalmente criado no fluxo e <xref:System.ServiceModel.Channels.Message.WriteMessage%28System.Xml.XmlWriter%29> é chamado no `Message` para gravar este gravador.|  
|Decodificação de buffer|Quando no modo de buffer, um especial de decodificação `Message` subclasse que contém os dados armazenados em buffer normalmente é criado. Os cabeçalhos da mensagem são lidas e um leitor de XML posicionado no corpo da mensagem é criado. Este é o leitor será retornado com <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents>.|  
|Decodificação de streaming|Ao decodificar no modo de fluxo, uma subclasse de mensagem especial normalmente é criada. O fluxo é avançado apenas o suficiente para ler todos os cabeçalhos e posicione-o no corpo da mensagem. Um leitor de XML é criado no fluxo. Este é o leitor será retornado com <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents>.|  
  
 Os codificadores podem executar outras funções. Por exemplo, os codificadores podem reunir os gravadores e leitores XML. É caro criar um novo leitor XML ou gravador sempre que necessário. Portanto, os codificadores normalmente mantêm um pool de leitores e um pool de gravadores de tamanho configurável. Nas descrições de operação de codificador descrita anteriormente, sempre que a frase "criar um leitor/gravador de XML" é usado, normalmente significa "execute um do pool, ou criar um se um não estiver disponível." O codificador (e o `Message` subclasses cria durante a decodificação) contêm a lógica para retornar os leitores e gravadores para os pools quando eles não são mais necessários (por exemplo, quando o `Message` está fechado).  
  
 O WCF fornece três codificadores de mensagem, embora seja possível criar tipos personalizados adicionais. Os tipos fornecidos são texto, binária e mecanismo de otimização de transmissão mensagem (MTOM). Elas são descritas em detalhes em [escolhendo um codificador de mensagem](../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md).  
  
### <a name="the-istreamprovider-interface"></a>A Interface IStreamProvider  
 Ao escrever uma mensagem de saída que contém um corpo transmitido para um gravador XML, o <xref:System.ServiceModel.Channels.Message> usa uma sequência de chamadas semelhantes à seguinte na sua <xref:System.ServiceModel.Channels.Message.OnWriteBodyContents%28System.Xml.XmlDictionaryWriter%29> implementação:  
  
-   Grave todas as informações necessárias antes do fluxo (por exemplo, a marca de abertura XML).  
  
-   O fluxo de gravação.  
  
-   Grave todas as informações a seguir o fluxo (por exemplo, o marca XML de fechamento).  
  
 Isso funciona bem com codificações que são semelhantes a codificação XML textual. No entanto, algumas codificações não coloque informações Infoset XML (por exemplo, marcas de início e término elementos XML) junto com os dados contidos em elementos. Por exemplo, a codificação de MTOM, a mensagem é dividida em várias partes. Uma parte contém Infoset XML, que podem conter referências a outras partes do conteúdo de elemento real. O Infoset XML é normalmente pequeno em comparação com o conteúdo em fluxo, faz sentido Infoset de buffer, grave-o e, em seguida, gravar o conteúdo de uma maneira em fluxo. Isso significa que, no momento o fechamento marca do elemento é gravada, o fluxo deve não tenha sido escrito ainda.  
  
 Para essa finalidade, o <xref:System.Xml.IStreamProvider> interface é usada. A interface tiver um <xref:System.Xml.IStreamProvider.GetStream> método que retorna o fluxo a ser gravado. A maneira correta de gravar um corpo de mensagem transmitida em <xref:System.ServiceModel.Channels.Message.OnWriteBodyContents%28System.Xml.XmlDictionaryWriter%29> é o seguinte:  
  
1.  Grave todas as informações necessárias antes do fluxo (por exemplo, a marca de abertura XML).  
  
2.  Chamar o `WriteValue` de sobrecarga no <xref:System.Xml.XmlDictionaryWriter> que leva um <xref:System.Xml.IStreamProvider>, com um `IStreamProvider` implementação que retorna o fluxo a ser gravado.  
  
3.  Grave todas as informações a seguir o fluxo (por exemplo, o marca XML de fechamento).  
  
 Com essa abordagem, o gravador de XML tem uma opção de quando chamar <xref:System.Xml.IStreamProvider.GetStream> e gravar os dados transmitidos. Por exemplo, os gravadores XML binários e textuais irá chamá-lo imediatamente e gravar o conteúdo em fluxo entre as marcas de início e término. O gravador MTOM pode optar por chamar <xref:System.Xml.IStreamProvider.GetStream> posteriormente, quando estiver pronto para gravar a parte apropriada da mensagem.  
  
## <a name="representing-data-in-the-service-framework"></a>Que representa os dados na estrutura de serviço  
 Conforme mencionado na seção "Arquitetura básica" deste tópico, a estrutura do serviço é a parte do WCF que, entre outras coisas, é responsável pela conversão entre um modelo de programação simples para os dados de mensagem e reais `Message` instâncias. Normalmente, uma troca de mensagens é representada na estrutura de serviço como um [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] método marcado com o <xref:System.ServiceModel.OperationContractAttribute> atributo. O método pode levar de alguns parâmetros e pode retornar um valor de retorno ou parâmetros (ou ambos). No lado do serviço, os parâmetros de entrada representam a mensagem de entrada e o valor de retorno em parâmetros de saída representam a mensagem de saída. No lado do cliente, o inverso é verdadeiro. O modelo de programação para descrever as mensagens usando parâmetros e o valor de retorno é descrito detalhadamente no [especificando a transferência de dados em contratos de serviço](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md). No entanto, esta seção fornece uma visão geral breve.  
  
## <a name="programming-models"></a>Modelos de programação  
 Estrutura do serviço de WCF dá suporte a cinco modelos de programação diferentes para descrever as mensagens:  
  
### <a name="1-the-empty-message"></a>1. A mensagem vazia  
 Esse é o caso mais simples. Para descrever uma mensagem de entrada vazia, não use os parâmetros de entrada.  
  
 [!code-csharp[C_DataArchitecture#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#3)]
 [!code-vb[C_DataArchitecture#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#3)]  
  
 Para descrever uma mensagem de saída vazia, use um valor de retorno void e não use nenhum parâmetros de saída:  
  
 [!code-csharp[C_DataArchitecture#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#4)]
 [!code-vb[C_DataArchitecture#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#4)]  
  
 Observe que isso é diferente de um contrato de operação unidirecional:  
  
 [!code-csharp[C_DataArchitecture#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#5)]
 [!code-vb[C_DataArchitecture#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#5)]  
  
 No `SetDesiredTemperature` exemplo, um padrão de troca de mensagem bidirecional é descrito. Uma mensagem é retornada da operação, mas ele está vazio. É possível retornar uma falha da operação. No exemplo "Lâmpada definida", o padrão de troca de mensagem é unidirecional, portanto, não há nenhuma mensagem de saída para descrever. O serviço não pode se comunicar a qualquer status de volta para o cliente nesse caso.  
  
### <a name="2-using-the-message-class-directly"></a>2. Usando a classe de mensagem diretamente  
 É possível usar o <xref:System.ServiceModel.Channels.Message> classe (ou uma de suas subclasses) diretamente em um contrato de operação. Nesse caso, a estrutura do serviço apenas transmite o `Message` da operação para a pilha de canais e vice-versa, com nenhum processamento adicional.  
  
 Há dois casos de uso principal para o uso de `Message` diretamente. Você pode usar isso para cenários avançados, quando nenhum dos outros modelos de programação fornece flexibilidade suficiente para descrever a mensagem. Por exemplo, você talvez queira usar arquivos no disco para descrever uma mensagem com as propriedades do arquivo se torne cabeçalhos de mensagem e o conteúdo do arquivo se torne o corpo da mensagem. Você pode criar algo semelhante ao seguinte.  
  
 [!code-csharp[C_DataArchitecture#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#6)]
 [!code-vb[C_DataArchitecture#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#6)]  
  
 A segunda comum usado para `Message` em um contrato de operação é quando um serviço não importantes para a mensagem em particular de conteúdo e atua na mensagem em uma caixa preta. Por exemplo, você pode ter um serviço que encaminha mensagens a vários outros destinatários. O contrato pode ser gravado da seguinte maneira.  
  
 [!code-csharp[C_DataArchitecture#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#7)]
 [!code-vb[C_DataArchitecture#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#7)]  
  
 A ação = "*" linha efetivamente desativa a distribuição de mensagem e garante que todas as mensagens enviadas para o `IForwardingService` contrato passarão para o `ForwardMessage` operação. (Normalmente, o dispatcher seria examinar cabeçalho de "Ação" da mensagem para determinar qual operação é destinado. Ação = "\*" significa "todos os valores possíveis do cabeçalho de ação de".) A combinação de ação = "\*" e usando a mensagem como um parâmetro é conhecido como "contrato universal" porque ele é capaz de receber todas as mensagens possíveis. Para poder enviar todas as mensagens possíveis, use a mensagem como o valor de retorno e defina `ReplyAction` para "\*". Isso impedirá a estrutura do serviço de adicionar seu próprio cabeçalho de ação, permitindo que você controle esse cabeçalho usando o `Message` retornar do objeto.  
  
### <a name="3-message-contracts"></a>3. Contratos de mensagem  
 WCF fornece um modelo de programação declarativo para descrever as mensagens, chamadas *contratos de mensagem*. Esse modelo é descrito detalhadamente no [usando contratos de mensagem](../../../../docs/framework/wcf/feature-details/using-message-contracts.md). Essencialmente, a mensagem inteira é representada por um único [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] tipo que usa atributos, como o <xref:System.ServiceModel.MessageBodyMemberAttribute> e <xref:System.ServiceModel.MessageHeaderAttribute> para descrever quais partes da classe de contrato de mensagem devem ser mapeado para o qual parte da mensagem.  
  
 Contratos de mensagem fornecem muito controle sobre resultante `Message` instâncias (embora, obviamente, não muito controle como usando o `Message` classe diretamente). Por exemplo, corpos de mensagens geralmente são compostos de várias partes da informação, cada um representado por seu próprio elemento XML. Esses elementos podem ocorrer ou diretamente no corpo (*sem* modo) ou pode ser *encapsulado* em um elemento XML abrangente. Usar o modelo de programação de contrato de mensagem permite que você tomar a decisão de bare versus encapsulado e controlar o nome do namespace e nome do wrapper.  
  
 O exemplo a seguir de um contrato de mensagem demonstra esses recursos.  
  
 [!code-csharp[C_DataArchitecture#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#9)]
 [!code-vb[C_DataArchitecture#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#9)]  
  
 Itens marcados para ser serializado (com o <xref:System.ServiceModel.MessageBodyMemberAttribute>, <xref:System.ServiceModel.MessageHeaderAttribute>, ou outros atributos relacionados) deve ser serializável para participar de um contrato de mensagem. Para obter mais informações, consulte a seção "Serialização" mais adiante neste tópico.  
  
### <a name="4-parameters"></a>4. Parâmetros  
 Geralmente, um desenvolvedor que deseja descrever uma operação que atua em várias partes de dados não é necessário o grau de controle que fornecem contratos de mensagem. Por exemplo, ao criar novos serviços, um não geralmente deseja tomar a decisão de bare versus encapsulado e decidir sobre o nome do elemento wrapper. Essas decisões geralmente requer conhecimento profundo de serviços Web e SOAP.  
  
 A estrutura do serviço WCF pode selecionar automaticamente a representação de SOAP melhor e mais interoperável para enviar ou receber várias partes relacionadas de informação, sem fazer com que essas opções no usuário. Isso é feito simplesmente descrevendo essas duas informações como parâmetros ou retornar valores de um contrato de operação. Por exemplo, considere o seguinte contrato de operação.  
  
 [!code-csharp[C_DataArchitecture#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#11)]
 [!code-vb[C_DataArchitecture#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#11)]  
  
 Estrutura do serviço de automaticamente decide colocar todos os três partes de informações (`customerID`, `item`, e `quantity`) no corpo da mensagem e ajuste-los em um elemento wrapper denominado `SubmitOrderRequest`.  
  
 Descrevendo as informações para ser enviado ou recebido como uma lista simple de parâmetros de contrato de operação é a abordagem recomendada, a menos que existem especiais motivos para mover para o contrato de mensagem mais complexa ou `Message`-com base em modelos de programação.  
  
### <a name="5-stream"></a>5. Fluxo  
 Usando `Stream` ou uma de suas subclasses em um contrato de operação ou como uma parte de corpo de mensagem exclusiva em um contrato de mensagem pode ser considerada um modelo de programação separado dos descritos acima. Usando `Stream` dessa maneira é a única maneira de garantir que seu contrato poderá ser usado de maneira em fluxo, com pouca escrevendo seu próprio compatível streaming `Message` subclasse. Para obter mais informações, consulte [dados grandes e Streaming](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md).  
  
 Quando `Stream` ou uma de suas subclasses é usada dessa maneira, o serializador não é invocado. Mensagens de saída, um streaming especial `Message` subclasse é criada e o fluxo é gravado como descrito na seção sobre o <xref:System.Xml.IStreamProvider> interface. Mensagens de entrada, a estrutura de serviço cria um `Stream` subclasse sobre a mensagem de entrada e fornece para a operação.  
  
## <a name="programming-model-restrictions"></a>Restrições do Modelo de Programação  
 Os modelos de programação descritos acima não podem ser combinados arbitrariamente. Por exemplo, se uma operação aceita um tipo de contrato de mensagem, o contrato de mensagem deve ser o único parâmetro de entrada. Além disso, a operação deve, em seguida, retornar uma mensagem vazia (tipo de retorno de void) ou em outro contrato de mensagem. Essas restrições do modelo de programação são descritas nos tópicos para cada modelo de programação específico: [usando contratos de mensagem](../../../../docs/framework/wcf/feature-details/using-message-contracts.md), [usando a classe de mensagem](../../../../docs/framework/wcf/feature-details/using-the-message-class.md), e [dados grandes e Streaming ](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md).  
  
## <a name="message-formatters"></a>Formatadores de mensagem  
 Os modelos de programação descritos acima são suportados Conectando componentes chamados *mensagem formatadores* na estrutura de serviço. Formatadores de mensagem são tipos que implementam o <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> ou <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> interface, ou ambos, para uso em clientes e serviços WCF, respectivamente.  
  
 Formatadores de mensagem normalmente são conectados por comportamentos. Por exemplo, o <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> conecta-se o formatador de mensagem do contrato de dados. Isso é feito no lado do serviço, definindo <xref:System.ServiceModel.Dispatcher.DispatchOperation.Formatter%2A> para o formatador correto no <xref:System.ServiceModel.Description.IOperationBehavior.ApplyDispatchBehavior%28System.ServiceModel.Description.OperationDescription%2CSystem.ServiceModel.Dispatcher.DispatchOperation%29> método, ou no lado do cliente, definindo <xref:System.ServiceModel.Dispatcher.ClientOperation.Formatter%2A> para o formatador correto no <xref:System.ServiceModel.Description.IOperationBehavior.ApplyClientBehavior%28System.ServiceModel.Description.OperationDescription%2CSystem.ServiceModel.Dispatcher.ClientOperation%29> método.  
  
 As tabelas a seguir lista os métodos que pode implementar um formatador de mensagem.  
  
|Interface|Método|Ação|  
|---------------|------------|------------|  
|<xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter>|<xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter.DeserializeRequest%28System.ServiceModel.Channels.Message%2CSystem.Object%5B%5D%29>|Converte uma entrada `Message` para parâmetros de operação|  
|<xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter>|<xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter.SerializeReply%28System.ServiceModel.Channels.MessageVersion%2CSystem.Object%5B%5D%2CSystem.Object%29>|Cria uma saída `Message` valor de retorno da operação/parâmetros de saída|  
|<xref:System.ServiceModel.Dispatcher.IClientMessageFormatter>|<xref:System.ServiceModel.Dispatcher.IClientMessageFormatter.SerializeRequest%28System.ServiceModel.Channels.MessageVersion%2CSystem.Object%5B%5D%29>|Cria uma saída `Message` de parâmetros de operação|  
|<xref:System.ServiceModel.Dispatcher.IClientMessageFormatter>|<xref:System.ServiceModel.Dispatcher.IClientMessageFormatter.DeserializeReply%28System.ServiceModel.Channels.Message%2CSystem.Object%5B%5D%29>|Converte uma entrada `Message` para um valor de retorno/parâmetros out|  
  
## <a name="serialization"></a>Serialização  
 Sempre que usar parâmetros ou contratos de mensagem para descrever o conteúdo da mensagem, você deve usar a serialização para converter entre [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] tipos e representação Infoset XML. Serialização é usada em outros lugares no WCF, por exemplo, <xref:System.ServiceModel.Channels.Message> tem um genérico <xref:System.ServiceModel.Channels.Message.GetBody%2A> método que você pode usar para ler todo o corpo da mensagem desserializado em um objeto.  
  
 WCF dá suporte a duas tecnologias de serialização "pronta" para serialização e desserialização de parâmetros e partes da mensagem: o <xref:System.Runtime.Serialization.DataContractSerializer> e `XmlSerializer`. Além disso, você pode escrever serializadores personalizados. No entanto, outras partes do WCF (como genérica `GetBody` serialização de falhas de SOAP ou método) pode ser restrita para usar somente o <xref:System.Runtime.Serialization.XmlObjectSerializer> subclasses (<xref:System.Runtime.Serialization.DataContractSerializer> e <xref:System.Runtime.Serialization.NetDataContractSerializer>, mas não o <xref:System.Xml.Serialization.XmlSerializer>), ou até mesmo ser codificado para usar somente o <xref:System.Runtime.Serialization.DataContractSerializer>.  
  
 O `XmlSerializer` é o mecanismo de serialização usado em [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] serviços Web. O `DataContractSerializer` é o novo mecanismo de serialização que compreende o modelo de programação de contrato de dados de novo. `DataContractSerializer` é a opção padrão e a opção de usar o `XmlSerializer` podem ser feitas em uma base de cada operação usando o <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior.DataContractFormatAttribute%2A> atributo.  
  
 <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> e <xref:System.ServiceModel.Description.XmlSerializerOperationBehavior> responsáveis os comportamentos de operação para conectar os formatadores de mensagem para o `DataContractSerializer` e `XmlSerializer`, respectivamente. O <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> comportamento pode operar com qualquer serializador que deriva de <xref:System.Runtime.Serialization.XmlObjectSerializer>, incluindo o <xref:System.Runtime.Serialization.NetDataContractSerializer> (descritos detalhadamente na serialização de autônomo usando). O comportamento chama uma da `CreateSerializer` sobrecargas de método virtual para obter o serializador. Para conectar um serializador diferente, crie um novo <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> subclasse e substituição `CreateSerializer` sobrecargas.  
  
## <a name="see-also"></a>Consulte também  
 [Especificando transferência de dados em contratos de serviço](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md)
