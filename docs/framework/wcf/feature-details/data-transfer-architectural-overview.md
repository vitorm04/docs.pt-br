---
title: Visão geral da arquitetura de transferência de dados
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data transfer [WCF], architectural overview
ms.assetid: 343c2ca2-af53-4936-a28c-c186b3524ee9
ms.openlocfilehash: bb903f6d182c7a8be915daf67a4df30475cfae62
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59127446"
---
# <a name="data-transfer-architectural-overview"></a>Visão geral da arquitetura de transferência de dados
Windows Communication Foundation (WCF) pode ser pensada como uma infraestrutura de mensagens. Ele pode receber mensagens, processá-los e distribuí-los para o código de usuário para outra ação, ou pode construir mensagens de dados fornecidos pelo código do usuário e enviá-las para um destino. Este tópico, que é destinado a desenvolvedores avançados, descreve a arquitetura para lidar com mensagens e os dados contidos. Para uma exibição mais simples e orientada a tarefas de como enviar e receber dados, consulte [especificando a transferência de dados em contratos de serviço](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md).  
  
> [!NOTE]
>  Este tópico discute os detalhes de implementação de WCF que não são visíveis, examinando o modelo de objeto do WCF. Duas palavras de advertência estão na ordem em relação a detalhes de implementação documentadas. Em primeiro lugar, as descrições são simplificadas; implementação real pode ser mais complexa devido a otimizações ou por outros motivos. Em segundo lugar, você nunca deve confiar nos detalhes da implementação específica, até mesmo documentado aqueles, porque eles podem ser alterados sem aviso prévio de versão para versão ou até mesmo em uma versão de serviço.  
  
## <a name="basic-architecture"></a>Arquitetura básica  
 No núcleo dos recursos de manipulação de mensagens do WCF é a <xref:System.ServiceModel.Channels.Message> classe, que é descrito detalhadamente nas [usando a classe de mensagem](../../../../docs/framework/wcf/feature-details/using-the-message-class.md). Os componentes de tempo de execução do WCF podem ser divididos em duas partes principais: a pilha de canais e a estrutura de serviço, com o <xref:System.ServiceModel.Channels.Message> classe sendo o ponto de conexão.  
  
 A pilha de canais é responsável por converter entre válido <xref:System.ServiceModel.Channels.Message> instância e alguma ação que corresponde ao envio ou recebimento de dados da mensagem. No lado de envio, a pilha de canais usa válido <xref:System.ServiceModel.Channels.Message> da instância e, depois de algum processamento, executa alguma ação que corresponde logicamente a enviar a mensagem. A ação pode estar enviando pacotes TCP ou HTTP, enfileiramento de mensagens a mensagem no enfileiramento de mensagens, gravar a mensagem em um banco de dados, salvando-o em um compartilhamento de arquivos ou qualquer outra ação, dependendo da implementação. A ação mais comum é enviar a mensagem por um protocolo de rede. No lado do recebimento, o oposto acontece — uma ação é detectada (que pode ser pacotes TCP ou HTTP que chegam ou qualquer outra ação) e, após o processamento, a pilha de canais converte essa ação em um válido <xref:System.ServiceModel.Channels.Message> instância.  
  
 Você pode usar o WCF usando o <xref:System.ServiceModel.Channels.Message> classe e o canal de pilha diretamente. No entanto, fazer isso é difícil e demorado. Além disso, o <xref:System.ServiceModel.Channels.Message> objeto não fornece nenhum suporte a metadados, portanto, você não pode gerar clientes do WCF com rigidez de tipos, se você usar o WCF dessa maneira.  
  
 Portanto, o WCF inclui uma estrutura de serviço que fornece um modelo de programação fácil de usar que você pode usar para construir e receber `Message` objetos. Estrutura do serviço de mapas de serviços [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] tipos por meio da noção de contratos de serviço e envia mensagens para operações de usuário que são simplesmente [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] métodos marcados com o <xref:System.ServiceModel.OperationContractAttribute> atributo (para obter mais detalhes, consulte [Criando contratos de serviço](../../../../docs/framework/wcf/designing-service-contracts.md)). Esses métodos podem ter parâmetros e retornar valores. No lado do serviço, a estrutura de serviço converte recebidas <xref:System.ServiceModel.Channels.Message> instâncias em parâmetros e o converte em retornam valores para saída <xref:System.ServiceModel.Channels.Message> instâncias. No lado do cliente, ele faz o oposto. Por exemplo, considere o `FindAirfare` operação abaixo.  
  
 [!code-csharp[c_DataArchitecture#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#1)]
 [!code-vb[c_DataArchitecture#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#1)]  
  
 Suponha que `FindAirfare` é chamado no cliente. Converte a estrutura de serviço no cliente do `FromCity` e `ToCity` parâmetros em uma saída <xref:System.ServiceModel.Channels.Message> da instância e passá-lo para a pilha de canal a ser enviada.  
  
 No lado do serviço, quando um <xref:System.ServiceModel.Channels.Message> instância chega da pilha de canal, a estrutura de serviço extrai os dados relevantes da mensagem para preencher a `FromCity` e `ToCity` parâmetros e, em seguida, chama o lado do serviço `FindAirfare` método. Quando o método retorna, a estrutura de serviço usa o valor inteiro retornado e o `IsDirectFlight` parâmetro de saída e cria um <xref:System.ServiceModel.Channels.Message> instância do objeto que contém essas informações. Em seguida, ele passa a `Message` instância para a pilha de canal a ser enviada de volta ao cliente.  
  
 No lado do cliente, um <xref:System.ServiceModel.Channels.Message> surge de instância que contém a mensagem de resposta da pilha de canal. A estrutura de serviço extrai o valor de retorno e o `IsDirectFlight` de valor e retorna-os para o chamador do cliente.  
  
## <a name="message-class"></a>Classe de mensagem  
 O <xref:System.ServiceModel.Channels.Message> classe deve ser uma representação abstrata de uma mensagem, mas seu design está intimamente ligado à mensagem SOAP. Um <xref:System.ServiceModel.Channels.Message> contém três partes principais de informação: propriedades de mensagem, cabeçalhos de mensagem e um corpo de mensagem.  
  
## <a name="message-body"></a>Corpo da mensagem  
 O corpo da mensagem destina-se para representar o conteúdo dos dados reais da mensagem. O corpo da mensagem sempre é representado como um XML Infoset. Isso não significa que todas as mensagens criadas ou recebidas no WCF devem estar no formato XML. Cabe a pilha de canais para decidir como interpretar o corpo da mensagem. Ele pode emiti-los como XML, convertê-lo em algum outro formato ou até mesmo omiti-lo inteiramente. É claro que, com a maioria das fontes de associações de WCF, o corpo da mensagem é representado como conteúdo XML na seção de corpo de um envelope SOAP.  
  
 É importante observar que o `Message` classe necessariamente não contêm um buffer com dados XML que representa o corpo. Logicamente, `Message` contém um XML Infoset, mas esse Infoset pode ser construída dinamicamente e nunca fisicamente pode existir na memória.  
  
### <a name="putting-data-into-the-message-body"></a>Colocar dados no corpo da mensagem  
 Não há nenhum mecanismo uniforme para colocar dados em um corpo de mensagem. O <xref:System.ServiceModel.Channels.Message> classe tem um método abstrato <xref:System.ServiceModel.Channels.Message.OnWriteBodyContents%28System.Xml.XmlDictionaryWriter%29>, que utiliza um <xref:System.Xml.XmlDictionaryWriter>. Cada subclasse do <xref:System.ServiceModel.Channels.Message> classe é responsável por substituir esse método e escrever seu próprio conteúdo. O corpo da mensagem contém o XML Infoset logicamente que `OnWriteBodyContent` produz. Por exemplo, considere o seguinte `Message` subclasse.  
  
 [!code-csharp[c_DataArchitecture#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#2)]
 [!code-vb[c_DataArchitecture#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#2)]  
  
 Fisicamente, um `AirfareRequestMessage` instância contém apenas duas cadeias de caracteres ("fromCity" e "toCity"). No entanto, logicamente a mensagem contém o infoset XML a seguir:  
  
```xml  
<airfareRequest>  
    <from>Tokyo</from>  
    <to>London</to>  
</airfareRequest>  
```  
  
 É claro, você normalmente não criaria mensagens dessa maneira, porque você pode usar a estrutura de serviço para criar uma mensagem semelhante à anterior da operação de parâmetros do contrato. Além disso, o <xref:System.ServiceModel.Channels.Message> classe tem estático `CreateMessage` métodos que você pode usar para criar as mensagens com tipos comuns de conteúdo: uma mensagem vazia, uma mensagem que contém um objeto serializado para XML com o <xref:System.Runtime.Serialization.DataContractSerializer>, uma mensagem que contém um SOAP mensagem de falha, uma que contém XML representado por um <xref:System.Xml.XmlReader>e assim por diante.  
  
### <a name="getting-data-from-a-message-body"></a>Obtendo dados de um corpo de mensagem  
 Você pode extrair os dados armazenados em um corpo de mensagem de duas maneiras principais:  
  
-   Você pode obter o corpo da mensagem inteira ao mesmo tempo, chamando o <xref:System.ServiceModel.Channels.Message.WriteBodyContents%28System.Xml.XmlDictionaryWriter%29> método e passar um gravador de XML. O corpo da mensagem completa for escrito neste gravador. Também é chamado de obter o corpo da mensagem inteira de uma só vez *gravar uma mensagem*. Gravação é feita principalmente pela pilha de canais ao enviar mensagens — alguma parte da pilha de canais geralmente será obter acesso ao corpo da mensagem inteira, codificá-lo e enviá-lo.  
  
-   Outra maneira de obter informações fora do corpo da mensagem é chamar <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents> e obtenha um leitor de XML. O corpo da mensagem, em seguida, pode ser acessado sequencialmente conforme necessário chamando métodos no leitor. Também é chamado de obter a mensagem corpo--detalhadamente *lendo uma mensagem*. Ler a mensagem é usado principalmente pela estrutura de serviço ao receber mensagens. Por exemplo, quando o <xref:System.Runtime.Serialization.DataContractSerializer> está em uso, a estrutura de serviço têm um leitor de XML sobre o corpo e passá-lo para o mecanismo de desserialização, que será iniciado, em seguida, ler o mensagem elemento por elemento e construir o gráfico do objeto correspondente.  
  
 Um corpo de mensagem pode ser recuperado apenas uma vez. Isso torna possível trabalhar com fluxos somente encaminhamento. Por exemplo, você pode escrever uma <xref:System.ServiceModel.Channels.Message.OnWriteBodyContents%28System.Xml.XmlDictionaryWriter%29> substituição que lê de um <xref:System.IO.FileStream> e retorna os resultados como um XML Infoset. Você nunca precisará "retroceder" para o início do arquivo.  
  
 O `WriteBodyContents` e `GetReaderAtBodyContents` métodos simplesmente verificam se o corpo da mensagem nunca foi obtido antes e, em seguida, chame `OnWriteBodyContents` ou `OnGetReaderAtBodyContents`, respectivamente.  
  
## <a name="message-usage-in-wcf"></a>Uso de mensagem no WCF  
 A maioria das mensagens podem ser classificados como *saída* (aquelas que são criados pela estrutura de serviço a ser enviado pela pilha de canais) ou *entrada* (aquelas que chegam do canal de pilha e são interpretado pela estrutura de serviço). Além disso, a pilha de canais pode operar no modo em buffer ou fluxo. A estrutura de serviço também pode expor um modelo de programação transmitido ou nonstreamed. Isso leva a casos listados na tabela a seguir, juntamente com detalhes simplificadas da sua implementação.  
  
|Tipo de mensagem|Dados do corpo de mensagem|Implementação de gravação (OnWriteBodyContents)|Read (OnGetReaderAtBodyContents) Implementation|  
|------------------|--------------------------|--------------------------------------------------|-------------------------------------------------------|  
|Saída, criado a partir de modelo de programação nonstreamed|Os dados necessários para gravar a mensagem (por exemplo, um objeto e o <xref:System.Runtime.Serialization.DataContractSerializer> instância necessária serializá-lo) *|Lógica personalizada para gravar a mensagem com base em dados armazenados (por exemplo, chamar `WriteObject` sobre o `DataContractSerializer` se esse for o serializador em uso) *|Chamar `OnWriteBodyContents`, os resultados do buffer, retornar um leitor de XML em buffer|  
|Saída, criado a partir do modelo de programação em fluxo|O `Stream` com os dados a serem gravados *|Gravar dados de fluxo armazenado usando o <xref:System.Xml.IStreamProvider> mecanismo *|Chamar `OnWriteBodyContents`, os resultados do buffer, retornar um leitor de XML em buffer|  
|Entrada da pilha de canais de streaming|Um `Stream` objeto que representa os dados chegando pela rede com um <xref:System.Xml.XmlReader> sobre ele|Gravar o conteúdo de armazenado `XmlReader` usando `WriteNode`|Retorna o armazenado `XmlReader`|  
|Entrada da pilha de canal nonstreaming|Um buffer que contém o corpo de dados com um `XmlReader` sobre ele|Grava o conteúdo do armazenado `XmlReader` usando `WriteNode`|Retorna o lang armazenado|  
  
 \* Esses itens não são implementados diretamente na `Message` subclasses, mas em subclasses do <xref:System.ServiceModel.Channels.BodyWriter> classe. Para obter mais informações sobre o <xref:System.ServiceModel.Channels.BodyWriter>, consulte [usando a classe de mensagem](../../../../docs/framework/wcf/feature-details/using-the-message-class.md).  
  
## <a name="message-headers"></a>Cabeçalhos de mensagem  
 Uma mensagem pode conter cabeçalhos. Logicamente, um cabeçalho consiste em um Infoset XML que está associado com um nome, um namespace e algumas outras propriedades. Cabeçalhos de mensagem são acessados usando o `Headers` propriedade <xref:System.ServiceModel.Channels.Message>. Cada cabeçalho é representado por um <xref:System.ServiceModel.Channels.MessageHeader> classe. Normalmente, os cabeçalhos de mensagem são mapeados para cabeçalhos de mensagem SOAP ao usar uma pilha de canais configurada para trabalhar com mensagens SOAP.  
  
 Colocando as informações em um cabeçalho de mensagem e extrair informações dele são semelhante a usar o corpo da mensagem. O processo um pouco é simplificado porque não há suporte para streaming. É possível acessar o conteúdo do cabeçalho mesmo mais de uma vez e cabeçalhos podem ser acessados na ordem arbitrária, forçando os cabeçalhos para sempre ser armazenados em buffer. Não há nenhum mecanismo para fins gerais disponível para obter um leitor de XML sobre um cabeçalho, mas há um `MessageHeader` subclasse interno para o WCF que representa um cabeçalho legível com esse recurso. Esse tipo de `MessageHeader` é criado pela pilha de canais quando chega uma mensagem com cabeçalhos de aplicativo personalizado. Isso permite que a estrutura de serviço para usar um mecanismo de desserialização, tais como o <xref:System.Runtime.Serialization.DataContractSerializer>, para interpretar esses cabeçalhos.  
  
 Para obter mais informações, consulte [usando a classe de mensagem](../../../../docs/framework/wcf/feature-details/using-the-message-class.md).  
  
## <a name="message-properties"></a>Propriedades da mensagem  
 Uma mensagem pode conter propriedades. Um *propriedade* é qualquer [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] objeto que está associado com um nome de cadeia de caracteres. Propriedades são acessadas por meio de `Properties` propriedade `Message`.  
  
 Ao contrário do corpo da mensagem e os cabeçalhos de mensagem (que normalmente mapeiam para o corpo SOAP e os cabeçalhos SOAP, respectivamente), propriedades de mensagem normalmente não são enviadas ou recebidas junto com as mensagens. Propriedades de mensagem existem principalmente como um mecanismo de comunicação para passar dados sobre a mensagem entre os vários canais na pilha de canais e entre a pilha de canais e o modelo de serviço.  
  
 Por exemplo, o canal de transporte HTTP incluído como parte do WCF é capaz de produzir vários códigos de status HTTP, como "404 (não encontrado)" e "500 (erro interno do servidor)," quando ele envia respostas aos clientes. Antes de enviar uma mensagem de resposta, ele verifica se o `Properties` do `Message` contêm uma propriedade chamada "httpResponse" que contém um objeto do tipo <xref:System.ServiceModel.Channels.HttpResponseMessageProperty>. Se essa propriedade for encontrada, ele examinará a <xref:System.ServiceModel.Channels.HttpResponseMessageProperty.StatusCode%2A> propriedade e usar esse código de status. Se não for encontrado, o padrão "200 (Okey)" código é usado.  
  
 Para obter mais informações, consulte [usando a classe de mensagem](../../../../docs/framework/wcf/feature-details/using-the-message-class.md).  
  
### <a name="the-message-as-a-whole"></a>A mensagem como um todo  
 Até agora, discutimos métodos para acessar as várias partes da mensagem em isolamento. No entanto, o <xref:System.ServiceModel.Channels.Message> classe também fornece métodos para trabalhar com a mensagem inteira como um todo. Por exemplo, o `WriteMessage` método grava a mensagem inteira para um gravador de XML.  
  
 Para que isso seja possível, um mapeamento deve ser definido entre todo o `Message` instância e um XML Infoset. Na verdade, existe um mapeamento: O WCF usa o padrão SOAP para definir esse mapeamento. Quando um `Message` instância é escrito como um XML Infoset, o Infoset resultante é o envelope SOAP válido que contém a mensagem. Portanto, `WriteMessage` normalmente executaria as seguintes etapas:  
  
1.  Gravar o marca de abertura do elemento envelope SOAP.  
  
2.  Gravar o elemento de cabeçalho SOAP marca de abertura, gravar todos os cabeçalhos e fechar o elemento de cabeçalho.  
  
3.  Gravar o elemento de corpo SOAP marca de abertura.  
  
4.  Chamar `WriteBodyContents` ou um método equivalente para gravar o corpo.  
  
5.  Feche os elementos de corpo e o envelope.  
  
 As etapas anteriores estão intimamente ligadas ao padrão de SOAP. Isso é complicado pelo fato de que há várias versões do SOAP, por exemplo, é impossível gravar o elemento do envelope SOAP corretamente sem saber a versão SOAP em uso. Além disso, em alguns casos, pode ser desejável para desativar esse complexa específicas de SOAP mapeando completamente.  
  
 Para esses fins, uma `Version` propriedade é fornecida em `Message`. Pode ser definido para a versão do SOAP a ser usado ao gravar a mensagem, ou ele pode ser definido como `None` para impedir que os mapeamentos de SOAP específicas. Se o `Version` estiver definida como `None`, os métodos que funcionam com o ato de toda a mensagem como se a mensagem consistiu em seu corpo, por exemplo, `WriteMessage` simplesmente chamaria `WriteBodyContents` em vez de executar as várias etapas listadas acima. Espera-se que nas mensagens de entrada, `Version` será detectado automaticamente e definido corretamente.  
  
## <a name="the-channel-stack"></a>A pilha de canais  
  
### <a name="channels"></a>Canais  
 Conforme mencionado anteriormente, a pilha de canais é responsável por converter de saída <xref:System.ServiceModel.Channels.Message> instâncias em alguma ação (como enviar pacotes pela rede) ou conversão de alguma ação (como receber pacotes de rede) em entrada `Message` instâncias.  
  
 A pilha de canais é composta de um ou mais canais ordenados em uma sequência. Uma saída `Message` instância é passada para o primeiro canal na pilha de (também chamado de *canal superior*), que o passa para o próximo canal para baixo na pilha e assim por diante. A mensagem termina no último canal, que é chamado de *canal de transporte*. Mensagens de entrada se originam no canal de transporte e são passadas para o canal para cima na pilha. Do canal do nível mais alto, a mensagem geralmente é passada na estrutura de serviço. Embora esse seja o padrão comum para mensagens de aplicativo, alguns canais podem funcionar de forma ligeiramente diferente, por exemplo, eles podem enviar suas próprias mensagens de infra-estrutura sem serem passados a uma mensagem de um canal acima.  
  
 Canais podem operar na mensagem de várias maneiras, conforme eles passam por meio da pilha. A operação mais comum é adicionar um cabeçalho a uma mensagem de saída e lendo cabeçalhos em uma mensagem de entrada. Por exemplo, um canal pode calcular a assinatura digital de uma mensagem e adicioná-lo como um cabeçalho. Um canal também pode inspecionar esse cabeçalho de assinatura digital em mensagens de entrada e bloquear mensagens que não têm uma assinatura válida do abrindo caminho até a pilha de canal. Canais também costumam ser definido ou inspecionar as propriedades da mensagem. O corpo da mensagem é geralmente não modificado, embora isso é permitido, por exemplo, o canal de segurança do WCF pode criptografar o corpo da mensagem.  
  
### <a name="transport-channels-and-message-encoders"></a>Canais de transporte e codificadores de mensagem  
 O canal na extremidade inferior da pilha é responsável por transformar, na verdade, uma saída <xref:System.ServiceModel.Channels.Message>, conforme modificado por outros canais, em alguma ação. No lado do recebimento, isso é o canal que converte alguma ação em um `Message` que outros canais de processo.  
  
 Conforme mencionado anteriormente, as ações podem ser variadas: enviar ou receber pacotes de rede por meio de vários protocolos, ler ou gravar a mensagem em um banco de dados ou enfileiramento de mensagens ou remover a mensagem em uma fila de enfileiramento de mensagens, para fornecer, mas alguns exemplos. Todas essas ações têm algo em comum: eles exigem uma transformação entre o WCF`Message` instância e um grupo real de bytes que pode ser enviada, recebida, ler, escrito, na fila ou removida da fila. O processo de converter um `Message` em um grupo de bytes é chamado *codificação*e o processo inverso de criação de uma `Message` de um grupo de bytes é chamado *decodificação*.  
  
 A maioria dos canais de transporte usam componentes chamados *codificadores de mensagem* para realizar a codificação e decodificação de trabalho. Um codificador de mensagem é uma subclasse do <xref:System.ServiceModel.Channels.MessageEncoder> classe. `MessageEncoder` inclui vários `ReadMessage` e `WriteMessage` sobrecargas de método para converter entre `Message` e grupos de bytes.  
  
 No lado de envio, passa um canal de transporte de armazenamento em buffer os `Message` objeto que ele recebeu de um canal acima para `WriteMessage`. Novamente, ele obtém uma matriz de bytes, que ele usa para executar sua ação (como empacotar esses bytes como pacotes TCP válidos e enviá-los para o destino correto). Primeiro cria um canal de transporte de streaming uma `Stream` (por exemplo, ao longo de saída TCP conexão) e, em seguida, passa a `Stream` e o `Message` que precisa para enviar ao apropriado `WriteMessage` sobrecarregar, que grava a mensagem .  
  
 No lado do recebimento, um canal de transporte de armazenamento em buffer extrai bytes de entrada (por exemplo, de pacotes de entrada TCP) em uma matriz e chama `ReadMessage` para obter um `Message` que possam passar mais acima na pilha de canal do objeto. Um canal de transporte streaming cria uma `Stream` objeto (por exemplo, um fluxo de rede sobre a conexão de TCP de entrada) e a passará para `ReadMessage` para retornar um `Message` objeto.  
  
 A separação entre os canais de transporte e codificador de mensagem não é obrigatória. é possível escrever um canal de transporte que não usa um codificador de mensagem. No entanto, a vantagem dessa separação é a facilidade de composição. Desde que um canal de transporte usa apenas a base <xref:System.ServiceModel.Channels.MessageEncoder>, ele pode funcionar com qualquer WCF ou o codificador de mensagem de terceiros. Da mesma forma, o codificador mesmo normalmente pode ser usado em qualquer canal de transporte.  
  
### <a name="message-encoder-operation"></a>Operação de codificador de mensagem  
 Para descrever a uma operação típica de um codificador, é útil pensar em quatro casos a seguir.  
  
|Operação|Comentário|  
|---------------|-------------|  
|A codificação, armazenados em buffer|No modo com buffer, o codificador normalmente cria um buffer de tamanho variável e, em seguida, cria um gravador de XML sobre ele. Em seguida, ele chama <xref:System.ServiceModel.Channels.Message.WriteMessage%28System.Xml.XmlWriter%29> na mensagem que está sendo codificada, que grava os cabeçalhos e, em seguida, o corpo, usando <xref:System.ServiceModel.Channels.Message.WriteBodyContents%28System.Xml.XmlDictionaryWriter%29>, conforme explicado na seção anterior sobre `Message` neste tópico. O conteúdo do buffer (representados como uma matriz de bytes), em seguida, é retornado para o canal de transporte a ser usado.|  
|A codificação, transmitidos|No modo de streaming, a operação é semelhante ao acima, mas mais simples. Não é necessário para um buffer. Normalmente, um gravador de XML é criado sobre o fluxo e <xref:System.ServiceModel.Channels.Message.WriteMessage%28System.Xml.XmlWriter%29> é chamado no `Message` para gravá-los para este gravador.|  
|Decodificação, armazenados em buffer|Ao decodificar no modo com buffer um especial `Message` subclasse que contém os dados armazenados em buffer é normalmente criado. Os cabeçalhos da mensagem são lidos e um leitor de XML posicionado no corpo da mensagem é criado. Isso é que o leitor que será retornado com <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents>.|  
|Decodificação, transmitidos|Ao decodificar no modo Streaming, uma subclasse de mensagem especial normalmente é criada. O fluxo é avançado apenas o suficiente para ler todos os cabeçalhos e posicione-o no corpo da mensagem. Um leitor de XML é criado no fluxo. Isso é que o leitor que será retornado com <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents>.|  
  
 Codificadores podem executar outras funções também. Por exemplo, os codificadores podem reunir os gravadores e leitores XML. É caro criar um novo leitor XML ou gravador toda vez que for necessária. Portanto, os codificadores normalmente mantêm um pool de leitores e um pool de gravadores de tamanho configurável. Nas descrições de operação do codificador descritas anteriormente, sempre que a frase "criar um leitor/gravador de XML" for usado, ele normalmente significa "assumir um do pool ou criar um se um não está disponível". O codificador (e o `Message` subclasses que ele cria durante a decodificação) contêm a lógica para retornar os leitores e gravadores para os pools depois que eles não são mais necessários (por exemplo, quando o `Message` é fechado).  
  
 O WCF fornece três codificadores de mensagem, embora seja possível criar tipos personalizados adicionais. Os tipos fornecidos são texto, binária e MTOM Message Transmission Optimization Mechanism (). Elas são descritas detalhadamente no [escolhendo um codificador de mensagem](../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md).  
  
### <a name="the-istreamprovider-interface"></a>A Interface IStreamProvider  
 Ao gravar uma mensagem de saída que contém um corpo de streaming em um gravador XML, o <xref:System.ServiceModel.Channels.Message> usa uma sequência de chamadas semelhantes ao seguinte no seu <xref:System.ServiceModel.Channels.Message.OnWriteBodyContents%28System.Xml.XmlDictionaryWriter%29> implementação:  
  
-   Grave as informações necessárias que precede o fluxo (por exemplo, a marca de abertura XML).  
  
-   Gravar o fluxo.  
  
-   Grave todas as informações a seguir o fluxo (por exemplo, o marcação XML de fechamento).  
  
 Isso funciona bem com codificações que são semelhantes a codificação XML textual. No entanto, algumas codificações não coloque informações Infoset XML (por exemplo, tags para iniciar e terminar a elementos XML) junto com os dados contidos em elementos. Por exemplo, na codificação de MTOM, a mensagem é dividida em várias partes. Uma parte contém o Infoset XML, que pode conter referências a outras partes de conteúdo do elemento real. O XML Infoset é normalmente pequeno em comparação com o conteúdo em fluxo, portanto, faz sentido armazenar em buffer o Infoset, grave-out e, em seguida, gravar o conteúdo de uma forma em fluxo. Isso significa que, no momento o fechamento marca de elemento é escrita, o fluxo deve não tenha sido escrito ainda.  
  
 Para essa finalidade, o <xref:System.Xml.IStreamProvider> interface é usada. A interface tem um <xref:System.Xml.IStreamProvider.GetStream> método que retorna o fluxo a ser gravado. A maneira correta de escrever um corpo de mensagem transmitidos em <xref:System.ServiceModel.Channels.Message.OnWriteBodyContents%28System.Xml.XmlDictionaryWriter%29> é da seguinte maneira:  
  
1.  Grave as informações necessárias que precede o fluxo (por exemplo, a marca de abertura XML).  
  
2.  Chame o `WriteValue` sobrecarregar do <xref:System.Xml.XmlDictionaryWriter> que usa um <xref:System.Xml.IStreamProvider>, com um `IStreamProvider` implementação que retorna o fluxo a ser gravado.  
  
3.  Grave todas as informações a seguir o fluxo (por exemplo, o marcação XML de fechamento).  
  
 Com essa abordagem, o gravador de XML tem uma opção de quando chamar <xref:System.Xml.IStreamProvider.GetStream> e gravar os dados transmitidos. Por exemplo, os gravadores XML textuais e binários serão chamá-lo imediatamente e gravar o conteúdo transmitido entre as marcas de início e término. O gravador MTOM pode optar por chamar <xref:System.Xml.IStreamProvider.GetStream> posteriormente, quando ele está pronto para gravar a parte apropriada da mensagem.  
  
## <a name="representing-data-in-the-service-framework"></a>Que representa a estrutura do serviço de dados  
 Conforme mencionado na seção "Arquitetura básica" deste tópico, a estrutura de serviço é a parte do WCF que, entre outras coisas, é responsável por converter entre um modelo de programação fácil de usar para os dados de mensagem e real `Message` instâncias. Normalmente, uma troca de mensagens é representada na estrutura do serviço de como uma [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] método marcado com o <xref:System.ServiceModel.OperationContractAttribute> atributo. O método pode levar alguns parâmetros e pode retornar um valor de retorno ou parâmetros (ou ambos). No lado do serviço, os parâmetros de entrada representam a mensagem de entrada e o valor de retorno em parâmetros de saída representam a mensagem de saída. No lado do cliente, o inverso é verdadeiro. O modelo de programação para descrever as mensagens usando parâmetros e o valor de retorno é descrito detalhadamente no [especificando a transferência de dados em contratos de serviço](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md). No entanto, esta seção fornecerá uma breve visão geral.  
  
## <a name="programming-models"></a>Modelos de programação  
 A estrutura de serviço do WCF dá suporte a cinco modelos de programação diferentes para descrever as mensagens:  
  
### <a name="1-the-empty-message"></a>1. A mensagem vazia  
 Esse é o caso mais simples. Para descrever uma mensagem de entrada vazia, não use parâmetros de entrada.  
  
 [!code-csharp[C_DataArchitecture#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#3)]
 [!code-vb[C_DataArchitecture#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#3)]  
  
 Para descrever uma mensagem de saída vazia, use um valor de retorno void e não use os parâmetros de saída:  
  
 [!code-csharp[C_DataArchitecture#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#4)]
 [!code-vb[C_DataArchitecture#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#4)]  
  
 Observe que isso é diferente de um contrato de operação unidirecional:  
  
 [!code-csharp[C_DataArchitecture#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#5)]
 [!code-vb[C_DataArchitecture#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#5)]  
  
 No `SetDesiredTemperature` exemplo, um padrão de troca de mensagens bidirecional é descrito. Uma mensagem é retornada da operação, mas ele está vazio. É possível retornar uma falha da operação. No exemplo "Definir lâmpada", o padrão de troca de mensagem é unidirecional, portanto, não há nenhuma mensagem de saída para descrever. O serviço não pode se comunicar a qualquer status de volta para o cliente nesse caso.  
  
### <a name="2-using-the-message-class-directly"></a>2. Usando a classe de mensagem diretamente  
 É possível usar o <xref:System.ServiceModel.Channels.Message> classe (ou uma de suas subclasses) diretamente em um contrato de operação. Nesse caso, a estrutura de serviço transmite apenas a `Message` da operação para a pilha de canais e vice-versa, com nenhum processamento adicional.  
  
 Há dois casos de uso principal para o uso `Message` diretamente. Você pode usar isso para cenários avançados, quando nenhum dos outros modelos de programação dá flexibilidade suficiente para descrever sua mensagem. Por exemplo, você talvez queira usar arquivos no disco para descrever uma mensagem, com as propriedades do arquivo se tornando cabeçalhos de mensagem e o conteúdo do arquivo se tornando o corpo da mensagem. Você pode criar algo semelhante ao seguinte.  
  
 [!code-csharp[C_DataArchitecture#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#6)]
 [!code-vb[C_DataArchitecture#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#6)]  
  
 A segunda comum usado para `Message` em um contrato de operação é quando um serviço não se importa a mensagem específica de conteúdo e atua na mensagem, como em uma caixa preta. Por exemplo, você pode ter um serviço que encaminha mensagens para vários outros destinatários. O contrato pode ser escrito da seguinte maneira.  
  
 [!code-csharp[C_DataArchitecture#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#7)]
 [!code-vb[C_DataArchitecture#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#7)]  
  
 A ação = "*" linha efetivamente desativa despacho de mensagens e garante que todas as mensagens enviadas para o `IForwardingService` contrato passarão para o `ForwardMessage` operação. (Normalmente, o dispatcher examinaria cabeçalho de "Ação" da mensagem para determinar qual operação é destinado. Ação = "\*" significa "todos os possíveis valores do cabeçalho da ação".) A combinação da ação = "\*" e usando a mensagem como um parâmetro é conhecido como o "contrato universal" porque ele é capaz de receber todas as possíveis mensagens. Para poder enviar todas as possíveis mensagens, use a mensagem como o valor retornado e defina `ReplyAction` para "\*". Isso impedirá que a estrutura do serviço de adicionar seu próprio cabeçalho Action, permitindo que você controlar esse cabeçalho usando o `Message` você retornar do objeto.  
  
### <a name="3-message-contracts"></a>3. Contratos de mensagem  
 O WCF fornece um modelo de programação declarativo para descrever mensagens, chamadas *contratos de mensagem*. Esse modelo é descrito detalhadamente no [contratos de mensagem usando](../../../../docs/framework/wcf/feature-details/using-message-contracts.md). Essencialmente, a mensagem inteira é representada por uma única [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] tipo que usa atributos como o <xref:System.ServiceModel.MessageBodyMemberAttribute> e <xref:System.ServiceModel.MessageHeaderAttribute> para descrever quais partes da classe de contrato de mensagem devem ser mapeado para o qual parte da mensagem.  
  
 Contratos de mensagem fornecem muito controle sobre resultante `Message` instâncias (embora, obviamente, não tanto controle quanto usar o `Message` classe diretamente). Por exemplo, corpos de mensagem geralmente são compostos de várias partes da informação, cada um representado por seu próprio elemento XML. Esses elementos podem ocorrer diretamente no corpo (*bare* modo) ou pode ser *encapsulado* em um elemento XML abrangente. Usar o modelo de programação de contrato de mensagem permite que você tomar a decisão bare versus encapsulado e controlar o nome do namespace e nome do wrapper.  
  
 O exemplo a seguir de um contrato de mensagem demonstra esses recursos.  
  
 [!code-csharp[C_DataArchitecture#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#9)]
 [!code-vb[C_DataArchitecture#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#9)]  
  
 Itens marcados para ser serializados (com o <xref:System.ServiceModel.MessageBodyMemberAttribute>, <xref:System.ServiceModel.MessageHeaderAttribute>, ou outros atributos relacionados) deve ser serializável para participar de um contrato de mensagem. Para obter mais informações, consulte a seção "Serialização" mais adiante neste tópico.  
  
### <a name="4-parameters"></a>4. Parâmetros  
 Muitas vezes, um desenvolvedor que deseja para descrever uma operação que atua em várias partes de dados não é necessário o grau de controle que fornece contratos de mensagem. Por exemplo, durante a criação de novos serviços, um não geralmente deseja tomar a decisão bare versus encapsulado e decidir sobre o nome do elemento wrapper. Tomar essas decisões muitas vezes requer um profundo conhecimento de serviços da Web e SOAP.  
  
 Estrutura do serviço de WCF pode selecionar automaticamente a representação de SOAP melhor e mais interoperável para envio ou recebimento de várias partes relacionadas de informação, sem forçar essas opções de logon do usuário. Isso é feito simplesmente descrevendo essas duas informações como parâmetros ou valores de retorno de um contrato de operação. Por exemplo, considere o seguinte contrato de operação.  
  
 [!code-csharp[C_DataArchitecture#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#11)]
 [!code-vb[C_DataArchitecture#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#11)]  
  
 A estrutura de serviços decide automaticamente colocar todas as três partes de informações (`customerID`, `item`, e `quantity`) para o corpo da mensagem e a quebra automática de linha-los em um elemento wrapper chamado `SubmitOrderRequest`.  
  
 Que descreve as informações a serem enviados ou recebidos como uma simple lista de parâmetros de contrato de operação é a abordagem recomendada, a menos que existam de motivos especiais para mover para o contrato de mensagem mais complexa ou `Message`-com base em modelos de programação.  
  
### <a name="5-stream"></a>5. Fluxo  
 Usando `Stream` ou uma de suas subclasses em um contrato de operação ou como uma parte do corpo de mensagem exclusiva em um contrato de mensagem pode ser considerada um modelo de programação separado daquelas descritas acima. Usando o `Stream` dessa maneira é a única maneira de garantir que seu contrato será utilizável de uma forma em fluxo, sem que seja necessário escrever sua própria streaming compatível com `Message` subclasse. Para obter mais informações, consulte [dados grandes e Streaming](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md).  
  
 Quando `Stream` ou uma de suas subclasses é usada dessa forma, o serializador não é invocado. Mensagens de saída, um streaming especial `Message` subclasse é criada e o fluxo é gravado como descrito na seção sobre o <xref:System.Xml.IStreamProvider> interface. Mensagens de entrada, a estrutura de serviço cria um `Stream` subclasse na mensagem de entrada e fornece-o para a operação.  
  
## <a name="programming-model-restrictions"></a>Restrições do Modelo de Programação  
 Os modelos de programação descritos acima não podem ser combinados arbitrariamente. Por exemplo, se uma operação aceita um tipo de contrato de mensagem, o contrato de mensagem deve ser seu único parâmetro de entrada. Além disso, a operação deve, em seguida, retornar uma mensagem vazia (tipo de retorno nulo) ou outro contrato de mensagem. Essas restrições do modelo de programação são descritas nos tópicos para cada modelo de programação específico: [Usando contratos de mensagem](../../../../docs/framework/wcf/feature-details/using-message-contracts.md), [usando a classe Message](../../../../docs/framework/wcf/feature-details/using-the-message-class.md), e [dados grandes e Streaming](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md).  
  
## <a name="message-formatters"></a>Formatadores de mensagem  
 Os modelos de programação descritos acima têm suporte Conectando componentes chamados *formatadores de mensagem* na estrutura de serviço. Formatadores de mensagem são tipos que implementam o <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> ou <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> interface, ou ambos, para uso em clientes e clientes do serviço WCF, respectivamente.  
  
 Formatadores de mensagem normalmente estão conectados por comportamentos. Por exemplo, o <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> conecta o formatador de mensagem de contrato de dados. Isso é feito no lado do serviço, definindo <xref:System.ServiceModel.Dispatcher.DispatchOperation.Formatter%2A> para o formatador correto na <xref:System.ServiceModel.Description.IOperationBehavior.ApplyDispatchBehavior%28System.ServiceModel.Description.OperationDescription%2CSystem.ServiceModel.Dispatcher.DispatchOperation%29> método, ou no lado do cliente, definindo <xref:System.ServiceModel.Dispatcher.ClientOperation.Formatter%2A> para o formatador correto no <xref:System.ServiceModel.Description.IOperationBehavior.ApplyClientBehavior%28System.ServiceModel.Description.OperationDescription%2CSystem.ServiceModel.Dispatcher.ClientOperation%29> método.  
  
 As tabelas a seguir lista os métodos que um formatador de mensagem pode implementar.  
  
|Interface|Método|Ação|  
|---------------|------------|------------|  
|<xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter>|<xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter.DeserializeRequest%28System.ServiceModel.Channels.Message%2CSystem.Object%5B%5D%29>|Converte uma entrada `Message` aos parâmetros de operação|  
|<xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter>|<xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter.SerializeReply%28System.ServiceModel.Channels.MessageVersion%2CSystem.Object%5B%5D%2CSystem.Object%29>|Cria uma saída `Message` valor de retorno da operação/parâmetros de saída|  
|<xref:System.ServiceModel.Dispatcher.IClientMessageFormatter>|<xref:System.ServiceModel.Dispatcher.IClientMessageFormatter.SerializeRequest%28System.ServiceModel.Channels.MessageVersion%2CSystem.Object%5B%5D%29>|Cria uma saída `Message` de parâmetros de operação|  
|<xref:System.ServiceModel.Dispatcher.IClientMessageFormatter>|<xref:System.ServiceModel.Dispatcher.IClientMessageFormatter.DeserializeReply%28System.ServiceModel.Channels.Message%2CSystem.Object%5B%5D%29>|Converte uma entrada `Message` para um valor de retorno/parâmetros de saída|  
  
## <a name="serialization"></a>Serialização  
 Sempre que usar contratos de mensagem ou parâmetros para descrever o conteúdo da mensagem, você deve usar a serialização para converter entre [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] tipos e a representação XML Infoset. A serialização é usada em outros lugares no WCF, por exemplo, <xref:System.ServiceModel.Channels.Message> tem um genérico <xref:System.ServiceModel.Channels.Message.GetBody%2A> método que você pode usar para ler todo o corpo da mensagem desserializado em um objeto.  
  
 O WCF oferece suporte a duas tecnologias de serialização "pronta" para serializar e desserializar parâmetros e partes da mensagem: o <xref:System.Runtime.Serialization.DataContractSerializer> e o `XmlSerializer`. Além disso, você pode escrever os serializadores personalizados. No entanto, outras partes do WCF (, como a genérica `GetBody` serialização de falha do método ou SOAP) pode ser restrita para usar somente o <xref:System.Runtime.Serialization.XmlObjectSerializer> subclasses (<xref:System.Runtime.Serialization.DataContractSerializer> e <xref:System.Runtime.Serialization.NetDataContractSerializer>, mas não o <xref:System.Xml.Serialization.XmlSerializer>), ou até mesmo ser embutido em código para usar somente o <xref:System.Runtime.Serialization.DataContractSerializer>.  
  
 O `XmlSerializer` é o mecanismo de serialização usado em [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] serviços Web. O `DataContractSerializer` é o novo mecanismo de serialização que compreende o modelo de programação de contrato de dados de novo. `DataContractSerializer` é a opção padrão e a opção de usar o `XmlSerializer` podem ser feitas por operação usando o <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior.DataContractFormatAttribute%2A> atributo.  
  
 <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> e <xref:System.ServiceModel.Description.XmlSerializerOperationBehavior> responsáveis os comportamentos de operação para conexão com os formatadores de mensagem para o `DataContractSerializer` e o `XmlSerializer`, respectivamente. O <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> comportamento, na verdade, pode operar com o serializador que deriva <xref:System.Runtime.Serialization.XmlObjectSerializer>, incluindo o <xref:System.Runtime.Serialization.NetDataContractSerializer> (descrito em detalhes na serialização de stand-alone usando). O comportamento chama um do `CreateSerializer` sobrecargas de método virtual para obter o serializador. Para conectar um serializador diferente, crie um novo <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> subclasse e substituição `CreateSerializer` sobrecargas.  
  
## <a name="see-also"></a>Consulte também

- [Especificando transferência de dados em contratos de serviço](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md)
