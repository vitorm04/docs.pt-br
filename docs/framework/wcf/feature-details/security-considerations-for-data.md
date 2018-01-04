---
title: "Considerações de segurança para dados"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: a7eb98da-4a93-4692-8b59-9d670c79ffb2
caps.latest.revision: "23"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: bb7a40bc38a3fdf3f7be2b31e30e768e26be2d15
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="security-considerations-for-data"></a>Considerações de segurança para dados
Ao lidar com dados em [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], você deve considerar um número de categorias de ameaça. A tabela a seguir lista as classes de ameaça mais importantes relacionados ao processamento de dados. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]fornece ferramentas para reduzir essas ameaças.  
  
 Negação de serviço  
 Ao receber dados não confiáveis, os dados podem causar o lado de recebimento acessar uma quantidade desproporcional de vários recursos, como memória, threads, conexões disponíveis ou ciclos do processador fazendo cálculos longos. Um ataque de negação de serviço em um servidor pode causar falhar e ser incapaz de processar mensagens de clientes de outros, legítimas.  
  
 Execução de código mal-intencionado  
 Os dados de entrada não confiáveis faz com que o lado de recebimento executar o código que ele não pretendia.  
  
 Divulgação de informações  
 O invasor remoto força a parte destinatária para responder a solicitações de forma a divulgar informações mais do que pretende.  
  
## <a name="user-provided-code-and-code-access-security"></a>Segurança de acesso de código e o código fornecido pelo usuário  
 Um número de locais de [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] infraestrutura para executar o código que é fornecido pelo usuário. Por exemplo, o <xref:System.Runtime.Serialization.DataContractSerializer> mecanismo de serialização pode chamar a propriedade fornecida pelo usuário `set` acessadores e `get` acessadores. O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] infraestrutura channel também pode chamar em fornecidos pelo usuário classes derivadas do <xref:System.ServiceModel.Channels.Message> classe.  
  
 É responsabilidade do autor do código para garantir que as vulnerabilidades de segurança não existam. Por exemplo, se você criar um contrato de dados tipo com uma propriedade de membro de dados do tipo inteiro e, no `set` implementação do acessador alocar uma matriz com base no valor da propriedade, você expõe a possibilidade de um ataque de negação de serviço se um mal-intencionado mensagem contém um valor muito grande para este membro de dados. Em geral, evite qualquer alocações com base nos dados de entrada ou longas processamento no código fornecido pelo usuário (especialmente se o processamento mais extenso pode ser causado por uma pequena quantidade de dados de entrada). Ao executar a análise de segurança de código fornecido pelo usuário, certifique-se de analisar todos os casos de falha (ou seja, todas as ramificações do código em que as exceções são geradas).  
  
 O exemplo de código fornecido pelo usuário a ultimate é o código dentro de sua implementação de serviço para cada operação. A segurança de sua implementação de serviço é sua responsabilidade. É fácil criar inadvertidamente implementações de operação não seguros que podem resultar em vulnerabilidades de negação de serviço. Por exemplo, uma operação que utiliza uma cadeia de caracteres e retorna a lista de clientes de um banco de dados cujo nome começa com essa cadeia de caracteres. Se você estiver trabalhando com um banco de dados grande e a cadeia de caracteres que está sendo passada é apenas uma única letra, seu código pode tentar criar uma mensagem maior que toda a memória disponível, ocasionando falha no serviço inteiro. (Um <xref:System.OutOfMemoryException> não é recuperável no [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] e sempre resulta no encerramento do aplicativo.)  
  
 Certifique-se de que nenhum código mal-intencionado é conectado a vários pontos de extensibilidade. Isso é especialmente relevante quando em execução em confiança parcial, lidar com tipos de assemblies parcialmente confiável, ou criando componentes utilizável por código parcialmente confiável. Para obter mais informações, consulte "Ameaças de confiança parcial" em uma seção posterior.  
  
 Observe que, quando executado em confiança parcial, a infraestrutura de serialização de contrato de dados oferece suporte a apenas um subconjunto limitado do contrato programação modelo de dados - por exemplo, membros de dados particulares ou tipos usando a <xref:System.SerializableAttribute> não há suporte para o atributo. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Confiança parcial](../../../../docs/framework/wcf/feature-details/partial-trust.md).  
  
## <a name="avoiding-unintentional-information-disclosure"></a>Evitar a divulgação de informações não intencional  
 Ao criar tipos serializáveis pensando na segurança, divulgação de informações é uma possível preocupação.  
  
 Considere os seguintes pontos:  
  
-   O <xref:System.Runtime.Serialization.DataContractSerializer> modelo de programação permite que a exposição de dados particulares e internas fora do tipo ou assembly durante a serialização. Além disso, a forma de um tipo pode ser exposta durante a exportação de esquema. Certifique-se de entender a projeção de serialização do tipo. Se você não deseja que nada expostos, desabilitar serializá-lo (por exemplo, aplicando não o <xref:System.Runtime.Serialization.DataMemberAttribute> atributo no caso de um contrato de dados).  
  
-   Lembre-se de que o mesmo tipo pode ter vários projeções de serialização, dependendo do serializador em uso. O mesmo tipo pode expor um conjunto de dados quando usado com o <xref:System.Runtime.Serialization.DataContractSerializer> e outro conjunto de dados quando usado com o <xref:System.Xml.Serialization.XmlSerializer>. Usar acidentalmente o serializador incorreto pode levar à divulgação de informações.  
  
-   Usando o <xref:System.Xml.Serialization.XmlSerializer> herdados procedimento remoto (RPC) de chamar / modo codificado acidentalmente pode expor a forma do gráfico do objeto no lado de envio para o lado de recebimento.  
  
## <a name="preventing-denial-of-service-attacks"></a>Evitando ataques de negação de serviço  
  
### <a name="quotas"></a>Cotas  
 Fazendo com que o lado de recebimento alocar uma quantidade significativa de memória é um ataque de negação de serviço. Embora esta seção se concentra em problemas de consumo de memória, decorrentes de mensagens grandes, podem ocorrer outros ataques. Por exemplo, as mensagens podem usar uma quantidade desproporcional de tempo de processamento.  
  
 Ataques de negação de serviço geralmente são atenuadas com o uso de cotas. Quando uma cota for ultrapassada, um <xref:System.ServiceModel.QuotaExceededException> normalmente exceção. Sem a cota, uma mensagem mal-intencionado pode fazer com que toda a memória disponível ser acessado, resultando em uma <xref:System.OutOfMemoryException> exceção ou todas as pilhas disponíveis para serem acessados, resultando em um <xref:System.StackOverflowException>.  
  
 O cenário de cota excedida podem ser recuperado; Se encontrado em um serviço em execução, a mensagem que está sendo processada no momento será descartada e o serviço continua em execução e processa mensagens adicionais. Os cenários de estouro de falta de memória e a pilha, no entanto, não são recuperáveis em qualquer lugar do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]; o serviço será encerrado se ele encontrar essas exceções.  
  
 Cotas no [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] não envolvem qualquer pré-alocação. Por exemplo, se o <xref:System.ServiceModel.Channels.TransportBindingElement.MaxReceivedMessageSize%2A> cota (encontrada em várias classes) é definida como 128 KB, isso não significa que 128 KB automaticamente é alocada para cada mensagem. O valor real alocado depende do tamanho real de mensagens de entrada.  
  
 Cotas muitos estão disponíveis na camada de transporte. Essas são as cotas impostas pelo canal de transporte específico em uso (HTTP, TCP e assim por diante). Enquanto este tópico discute algumas dessas cotas, essas cotas são descritas em detalhes em [cotas de transporte](../../../../docs/framework/wcf/feature-details/transport-quotas.md).  
  
### <a name="hashtable-vulnerability"></a>Vulnerabilidade da tabela de hash  
 Existe uma vulnerabilidade quando contratos de dados contém tabelas de hash ou coleções. O problema ocorre se um grande número de valores é inserido em uma tabela de hash em que um grande número desses valores gerar o mesmo valor de hash. Isso pode ser usado como um ataque DOS.  Essa vulnerabilidade pode ser atenuada definindo a cota de associação MaxRecievedMessageSize. Deve-se ter cuidado ao definir essa cota para evitar tais ataques. Essa cota coloca um limite superior no tamanho da mensagem WCF. Além disso, evite usar tabelas de hash ou coleções em seus contratos de dados.  
  
## <a name="limiting-memory-consumption-without-streaming"></a>Limitar o consumo de memória sem Streaming  
 O modelo de segurança em torno de mensagens grandes depende se o fluxo está em uso. No caso de basic, não de streaming, as mensagens são armazenados em buffer na memória. Nesse caso, use o <xref:System.ServiceModel.Channels.TransportBindingElement.MaxReceivedMessageSize%2A> cota o <xref:System.ServiceModel.Channels.TransportBindingElement> ou as associações fornecidas pelo sistema para proteger contra mensagens grandes, limitando o tamanho máximo da mensagem para acessar. Observe que um serviço pode processar várias mensagens ao mesmo tempo, caso em que todos eles estão na memória. Use o recurso de limitação para atenuar essa ameaça.  
  
 Observe também que `MaxReceivedMessageSize` não estabelece um limite superior no consumo de memória por mensagem, mas limita dentro de um fator constante. Por exemplo, se o `MaxReceivedMessageSize` é 1 MB e uma mensagem de 1 MB é recebida e, em seguida, desserializada memória adicional é necessária para conter o gráfico de objeto desserializado, resultando em bem de consumo total de memória acima de 1 MB. Por esse motivo, evite criar tipos serializáveis que podem resultar em consumo de memória significativa sem muitos dados de entrada. Por exemplo, um contrato de dados "MyContract" com campos de membro de dados opcional 50 e campos particulares 100 adicionais pode ser instanciado com a construção de XML "\<MyContract / >". Esse XML resulta na memória que está sendo acessada para 150 campos. Observe que os membros de dados são opcionais por padrão. O problema aumenta quando desse tipo é parte de uma matriz.  
  
 `MaxReceivedMessageSize`sozinho não é suficiente para impedir que todos os ataques de negação de serviço. Por exemplo, o desserializador pode ser forçado ao desserializar um gráfico de objeto aninhadas (um objeto que contém o outro objeto que contém um do outro e assim por diante), uma mensagem de entrada. Tanto o <xref:System.Runtime.Serialization.DataContractSerializer> e <xref:System.Xml.Serialization.XmlSerializer> chamar métodos de forma aninhada ao desserializar esses gráficos. Aninhamento de profundidade de chamadas de método pode resultar em um irrecuperável <xref:System.StackOverflowException>. Essa ameaça é reduzida, definindo o <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement.MaxDepth%2A> cota para limitar o nível de aninhamento de XML, conforme discutido na seção "Usando XML com segurança" posteriormente no tópico.  
  
 Configurando cotas adicionais `MaxReceivedMessageSize` é especialmente importante ao usar a codificação binária de XML. Usando a codificação binária é um pouco equivalente à compactação: um pequeno grupo de bytes na mensagem de entrada pode representar muitos dados. Assim, até mesmo uma mensagem de ajuste para o `MaxReceivedMessageSize` limite pode levar muito mais memória na forma totalmente expandida. Para reduzir essas ameaças específicas de XML, todas as cotas do leitor XML devem ser definidas corretamente, conforme discutido na seção "Usando XML com segurança" neste tópico.  
  
## <a name="limiting-memory-consumption-with-streaming"></a>Limitar o consumo de memória com Streaming  
 Quando o fluxo, você pode usar um pequeno `MaxReceivedMessageSize` configuração para proteger contra ataques de negação de serviço. No entanto, em cenários mais complexos são possíveis com a transmissão. Por exemplo, um serviço de carregamento de arquivo aceita arquivos maiores do que toda a memória disponível. Nesse caso, defina o `MaxReceivedMessageSize` para um valor muito grande, esperar que quase nenhum dado é armazenado em buffer na memória e a mensagem fluxos direto no disco. Se uma mensagem mal-intencionado pode impor alguma forma [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] para dados de buffer em vez de streaming-nesse caso, `MaxReceivedMessageSize` não protege contra a mensagem de acesso a toda a memória disponível.  
  
 Para atenuar essa ameaça, as configurações de cota específico existem em várias [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] componentes de processamento de dados que o limitam de buffer. O mais importante é o `MaxBufferSize` propriedade em vários elementos de associação de transporte e associações padrão. Quando a transmissão, essa cota deve ser definida levando em consideração a quantidade máxima de memória que você está disposto a alocar por mensagem. Assim como acontece com `MaxReceivedMessageSize`, a configuração não coloca um máximo absoluto consumo de memória, mas ele limita apenas dentro de um fator constante. Além disso, como com `MaxReceivedMessageSize`, lembre-se da possibilidade de várias mensagens que estão sendo processadas simultaneamente.  
  
### <a name="maxbuffersize-details"></a>MaxBufferSize detalhes  
 O `MaxBufferSize` propriedade limita qualquer buffer em massa [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] does. Por exemplo, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] buffers sempre cabeçalhos SOAP e falhas de SOAP, bem como quaisquer partes MIME encontrados não em ordem de leitura natural em uma mensagem do mecanismo de otimização de transmissão da mensagem (MTOM). Essa configuração limita a quantidade de buffer em todos esses casos.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]realiza isso passando o `MaxBufferSize` valor para os vários componentes que podem buffer. Por exemplo, alguns <xref:System.ServiceModel.Channels.Message.CreateMessage%2A> sobrecargas do <xref:System.ServiceModel.Channels.Message> classe têm um `maxSizeOfHeaders` parâmetro. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]passa o `MaxBufferSize` valor para esse parâmetro para limitar a quantidade de buffer de cabeçalho SOAP. É importante definir esse parâmetro ao usar o <xref:System.ServiceModel.Channels.Message> classe diretamente. Em geral, ao usar um componente no [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] que usa parâmetros de cota, é importante entender as implicações de segurança desses parâmetros e configurá-los corretamente.  
  
 O codificador de mensagem MTOM também tem um `MaxBufferSize` configuração. Ao usar associações padrão, isso será definido automaticamente para o nível de transporte `MaxBufferSize` valor. No entanto, ao usar o elemento de associação do codificador de mensagem MTOM para construir uma associação personalizada, é importante definir o `MaxBufferSize` propriedade para um valor de segurança quando o fluxo é usada.  
  
## <a name="xml-based-streaming-attacks"></a>Streaming de ataques baseados em XML  
 `MaxBufferSize`sozinho não é suficiente para garantir que [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] não pode ser forçado em buffer ao streaming é esperado. Por exemplo, o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] leitores XML sempre buffer a marca de início de elemento XML inteira ao começar a ler um novo elemento. Isso é feito para que os namespaces e atributos são processados corretamente. Se `MaxReceivedMessageSize` está configurado para ser grande (por exemplo, para habilitar um arquivo grande direta para disco streaming cenário), uma mensagem mal-intencionado pode ser construída em que o corpo da mensagem inteira é uma marca de início de elemento XML grande. Uma tentativa de lê-lo resulta em um <xref:System.OutOfMemoryException>. Isso é um dos muitos ataques de negação de serviço de baseado em XML possíveis que podem todos ser atenuados com o uso de cotas do leitor XML, discutidas na seção "Usando XML com segurança" neste tópico. Quando a transmissão, é especialmente importante definir todas essas cotas.  
  
### <a name="mixing-streaming-and-buffering-programming-models"></a>Combinação de Streaming e modelos de programação de buffer  
 Muitos ataques possíveis são provenientes de misturar modelos de programação streaming e não são de streaming no mesmo serviço. Suponha que há um contrato de serviço com duas operações: deles terá um <xref:System.IO.Stream> e o outro usa uma matriz de tipo personalizado. Suponha também que `MaxReceivedMessageSize` é definido com um valor grande para habilitar a primeira operação processar grandes fluxos. Infelizmente, isso significa que mensagens grandes podem agora ser enviada para a segunda operação e os armazena os dados de desserialização na memória como uma matriz antes que a operação é chamada. Este é um ataque de negação de serviço: o `MaxBufferSize` cota não limita o tamanho do corpo da mensagem, que é o que o desserializador funciona com.  
  
 Por esse motivo, evite a combinação de operações com base em fluxo e não de streaming no mesmo contrato. Se você absolutamente deve combinar os dois modelos de programação, use as seguintes precauções:  
  
-   Desativar o <xref:System.Runtime.Serialization.IExtensibleDataObject> recurso definindo o <xref:System.ServiceModel.ServiceBehaviorAttribute.IgnoreExtensionDataObject%2A> propriedade o <xref:System.ServiceModel.ServiceBehaviorAttribute> para `true`. Isso garante que somente os membros que fazem parte do contrato desserializados.  
  
-   Definir o <xref:System.Runtime.Serialization.DataContractSerializer.MaxItemsInObjectGraph%2A> propriedade o <xref:System.Runtime.Serialization.DataContractSerializer> para um valor de seguro. Essa cota também está disponível no <xref:System.ServiceModel.ServiceBehaviorAttribute> atributo ou por meio da configuração. Essa cota limita o número de objetos que são desserializado em um episódio de desserialização. Normalmente, cada operação mensagem ou parâmetro de parte do corpo de um contrato de mensagem é desserializado em um episódio. Durante a desserialização matrizes, cada entrada da matriz é contada como um objeto separado.  
  
-   Defina todas as cotas do leitor XML para valores de seguros. Preste atenção às <xref:System.Xml.XmlDictionaryReaderQuotas.MaxDepth%2A>, <xref:System.Xml.XmlDictionaryReaderQuotas.MaxStringContentLength%2A>, e <xref:System.Xml.XmlDictionaryReaderQuotas.MaxArrayLength%2A> e evitar cadeias de caracteres em operações não são de streaming.  
  
-   Examine a lista de tipos conhecidos, tendo em mente que qualquer um deles pode ser instanciado a qualquer momento (consulte a seção "Impedindo não intencionais tipos do que está sendo carregado" mais adiante neste tópico).  
  
-   Não use quaisquer tipos que implementam o <xref:System.Xml.Serialization.IXmlSerializable> interface que muitos dados de buffer. Não adicione tipos à lista de tipos conhecidos.  
  
-   Não use o <xref:System.Xml.XmlElement>, <xref:System.Xml.XmlNode> matrizes, <xref:System.Byte> matrizes ou tipos que implementam <xref:System.Runtime.Serialization.ISerializable> em um contrato.  
  
-   Não use o <xref:System.Xml.XmlElement>, <xref:System.Xml.XmlNode> matrizes, <xref:System.Byte> matrizes ou tipos que implementam <xref:System.Runtime.Serialization.ISerializable> na lista de tipos conhecidos.  
  
 As precauções anteriores se aplicam quando a operação de streaming não usa o <xref:System.Runtime.Serialization.DataContractSerializer>. Nunca misturar streaming e modelos de programação não são de streaming no mesmo serviço se você estiver usando o <xref:System.Xml.Serialization.XmlSerializer>, porque ele não tem a proteção de <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior.MaxItemsInObjectGraph%2A> cota.  
  
### <a name="slow-stream-attacks"></a>Ataques de fluxo lento  
 Uma classe de ataques de negação de serviço de streaming não envolve o consumo de memória. Em vez disso, o ataque envolve um remetente lenta ou receptor de dados. Enquanto aguarda os dados a serem enviados ou recebidos, recursos, como threads e conexões disponíveis são esgotados. Essa situação pode ocorrer como resultado de um ataque mal-intencionado ou de um remetente/destinatário legítimo em uma conexão de rede lenta.  
  
 Para atenuar esses ataques, defina os tempos limite de transporte corretamente. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Cotas de transporte](../../../../docs/framework/wcf/feature-details/transport-quotas.md). Em segundo lugar, nunca use síncrona `Read` ou `Write` operações ao trabalhar com fluxos em [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
## <a name="using-xml-safely"></a>Usando XML com segurança  
  
> [!NOTE]
>  Embora esta seção é sobre XML, as informações também se aplica a documentos JSON JavaScript Object Notation (). As cotas funcionam da mesma forma, usando [mapeamento entre JSON e XML](../../../../docs/framework/wcf/feature-details/mapping-between-json-and-xml.md).  
  
### <a name="secure-xml-readers"></a>Proteger os leitores XML  
 O XML Infoset constitui a base de todo o processamento de mensagem no [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Ao aceitar os dados XML de uma fonte não confiável, um número de ataque de negação de serviço existem possibilidades que deve ser reduzido. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]fornece leitores XML especiais e seguros. Esses leitores são criados automaticamente ao usar uma das codificações padrão em [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] (texto, binária ou MTOM).  
  
 Alguns dos recursos de segurança desses leitores sempre estão ativas. Por exemplo, os leitores nunca processam definições de tipo de documento (DTDs), que são uma fonte em potencial de ataques de negação de serviço e nunca devem aparecer nas mensagens SOAP legítimas. Outros recursos de segurança incluem cotas leitor devem ser configuradas, que são descritas na seção a seguir.  
  
 Ao trabalhar diretamente com leitores XML (como quando escrever seu próprio codificador personalizado ou ao trabalhar diretamente com o <xref:System.ServiceModel.Channels.Message> classe), sempre use o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] proteger leitores quando há uma possibilidade de trabalhar com dados não confiáveis. Criar os leitores seguros por uma chamada de fábrica estática sobrecargas do método de <xref:System.Xml.XmlDictionaryReader.CreateTextReader%2A>, <xref:System.Xml.XmlDictionaryReader.CreateBinaryReader%2A>, ou <xref:System.Xml.XmlDictionaryReader.CreateMtomReader%2A> no <xref:System.Xml.XmlDictionaryReader> classe. Ao criar um leitor, passe valores de cota segura. Não chame o `Create` sobrecargas do método. Eles não criam um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] leitor. Em vez disso, é criado um leitor que não seja protegido por recursos de segurança descritos nesta seção.  
  
### <a name="reader-quotas"></a>Cotas de leitor  
 Os leitores XML seguros tem cinco cotas configuráveis. Eles normalmente são configurados usando o `ReaderQuotas` propriedade na codificação elementos de associação ou associações padrão ou usando um <xref:System.Xml.XmlDictionaryReaderQuotas> objeto passado durante a criação de um leitor.  
  
#### <a name="maxbytesperread"></a>MaxBytesPerRead  
 Essa cota limita o número de bytes lidos em um único `Read` de início da operação ao ler o elemento de marca e seus atributos. (Em casos de streaming não, o nome do elemento em si não é contado em relação à cota.) <xref:System.Xml.XmlDictionaryReaderQuotas.MaxBytesPerRead%2A> é importante pelos seguintes motivos:  
  
-   O nome do elemento e seus atributos são sempre armazenados em buffer na memória quando elas estão sendo lidos. Portanto, é importante definir essa cota corretamente no modo para impedir que o buffer excessiva quando se espera que streaming de streaming. Consulte o `MaxDepth` seção de cota para obter informações sobre a quantidade real de buffer ocorre.  
  
-   Ter atributos XML demais pode consumir todo o tempo de processamento de maneira desproporcional porque a exclusividade dos nomes de atributo tem que ser verificada. O `MaxBytesPerRead` atenua essa ameaça.  
  
#### <a name="maxdepth"></a>MaxDepth  
 Essa cota limita a profundidade máxima de aninhamento dos elementos XML. Por exemplo, o documento "\<um >\<B >\<C / >\</b >\</A >" tem uma profundidade de aninhamento de três. <xref:System.Xml.XmlDictionaryReaderQuotas.MaxDepth%2A>é importante pelos seguintes motivos:  
  
-   O `MaxDepth` interage com o `MaxBytesPerRead`: o leitor sempre mantém dados na memória para o elemento atual e todos os seus ancestrais, para que o consumo máximo de memória do leitor seja proporcional ao produto dessas duas configurações.  
  
-   Ao desserializar um grafo de objeto aninhado mais profundamente, o desserializador é forçado para acessar a pilha inteira e gerar um <xref:System.StackOverflowException> irrecuperável. Uma correlação direta existe entre aninhamento de XML e aninhamento de objeto para <xref:System.Runtime.Serialization.DataContractSerializer> e <xref:System.Xml.Serialization.XmlSerializer>. Use `MaxDepth` para atenuar essa ameaça.  
  
#### <a name="maxnametablecharcount"></a>MaxNameTableCharCount  
 Essa cota limita o tamanho do leitor de *nametable*. O nametable contém algumas cadeias de caracteres (como namespaces e prefixos) que são encontrados ao processar um documento XML. Como essas cadeias de caracteres são armazenados em buffer na memória, defina essa cota para evitar buffer excessiva quando fluxo é esperado.  
  
#### <a name="maxstringcontentlength"></a>MaxStringContentLength  
 Essa cota limita o tamanho máximo da cadeia de caracteres que o leitor de XML retorna. Essa cota não limita o consumo de memória no próprio leitor de XML, mas no componente que esteja usando o leitor. Por exemplo, quando o <xref:System.Runtime.Serialization.DataContractSerializer> usa um leitor protegido com <xref:System.Xml.XmlDictionaryReaderQuotas.MaxStringContentLength%2A>, ele não desserializa as cadeias de caracteres maiores do que essa cota. Ao usar o <xref:System.Xml.XmlDictionaryReader> classe diretamente, nem todos os aspectos de métodos essa cota, mas apenas os métodos que são projetados especificamente para ler as cadeias de caracteres, como o <xref:System.Xml.XmlDictionaryReader.ReadContentAsString%2A> método. O <xref:System.Xml.XmlReader.Value%2A> propriedade do leitor não é afetada por essa cota e, portanto, não deve ser usada quando a proteção fornece essa cota é necessária.  
  
#### <a name="maxarraylength"></a>MaxArrayLength  
 Essa cota limita o tamanho máximo de uma matriz de primitivas que o leitor de XML retorna, inclusive matrizes de bytes. Essa cota não limita o consumo de memória no próprio leitor de XML, mas em qualquer componente que esteja usando o leitor. Por exemplo, quando o <xref:System.Runtime.Serialization.DataContractSerializer> usa um leitor protegido com <xref:System.Xml.XmlDictionaryReaderQuotas.MaxArrayLength%2A>, ele não desserializa as matrizes de bytes maiores do que essa cota. É importante definir essa cota durante a tentativa de misturar modelos de programação em buffer e streaming em um único contrato. Tenha em mente que, ao usar o <xref:System.Xml.XmlDictionaryReader> classe diretamente, apenas os métodos que são projetados especificamente para ler as matrizes de tamanho arbitrário de determinados tipos primitivos, como <xref:System.Xml.XmlDictionaryReader.ReadInt32Array%2A>, respeitam essa cota.  
  
## <a name="threats-specific-to-the-binary-encoding"></a>Ameaças específicas para a codificação binária  
 A codificação XML binário [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] inclui dá suporte a um *cadeias de caracteres de dicionário* recurso. Uma grande cadeia de caracteres pode ser codificada usando apenas alguns bytes. Isso permite que os ganhos significativos de desempenho, mas apresenta novas ameaças de negação de serviço que devem ser reduzidas.  
  
 Há dois tipos de dicionários: *estático* e *dinâmico*. O dicionário estático é uma lista interna de cadeias de caracteres longas que podem ser representadas usando um código curto em codificação binária. Esta lista de cadeias de caracteres é fixo quando o leitor é criado e não pode ser modificado. Nenhuma das cadeias de caracteres no dicionário estático que [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usa por padrão é suficientemente grande para oferecer uma ameaça grave de negação de serviço, embora ainda pode ser usados em um ataque de expansão do dicionário. Em cenários avançados em que você fornecer seu próprio dicionário estático, tenha cuidado ao introduzir cadeias de caracteres de dicionário grande.  
  
 O recurso de dicionários dinâmico permite que mensagens definir suas próprias cadeias de caracteres e associá-los com códigos curtos. Esses mapeamentos de código de cadeia de caracteres são mantidos na memória durante a sessão de comunicação inteira, de modo que as mensagens subsequentes não é necessário que reenviar as cadeias de caracteres e podem utilizar códigos que já estão definidos. Essas cadeias de caracteres podem ser de comprimento arbitrário e, portanto, representem uma ameaça mais grave no dicionário estático.  
  
 A primeira ameaça que deve ser reduzida é a possibilidade do dicionário dinâmico se tornando muito grande (tabela de mapeamento de código de cadeia de caracteres). Esse dicionário pode ser expandido ao longo de várias mensagens e portanto o `MaxReceivedMessageSize` cota não oferece proteção porque ele só se aplica a cada mensagem separadamente. Portanto, um separado <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement.MaxSessionSize%2A> propriedade existir no <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement> que limita o tamanho do dicionário.  
  
 Ao contrário da maioria das outras cotas, essa cota se aplica também ao escrever mensagens. Se for excedido durante a leitura de uma mensagem, o `QuotaExceededException` é gerada como de costume. Se for excedido durante a gravação de uma mensagem, cadeias de caracteres que causam a cota de ser excedido são gravadas como-é, sem usar o recurso de dicionários dinâmico.  
  
### <a name="dictionary-expansion-threats"></a>Ameaças de expansão de dicionário  
 Uma classe significativa de ataques específicos de binário advém da expansão do dicionário. Uma mensagem pequena em formato binário pode transformar em uma mensagem grande em forma textual totalmente expandida se faz uso extensivo do recurso de dicionários de cadeia de caracteres. O fator de expansão para cadeias de caracteres de dicionário dinâmico é limitado pelo <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement.MaxSessionSize%2A> cota, porque nenhuma cadeia de caracteres de dicionário dinâmico excede o tamanho máximo do dicionário inteiro.  
  
 O <xref:System.Xml.XmlDictionaryReaderQuotas.MaxNameTableCharCount%2A>, `MaxStringContentLength`, e `MaxArrayLength` propriedades apenas limitam o consumo de memória. Eles normalmente não são necessários para minimizar essas ameaças no uso de streaming não porque o uso de memória já é limitado pelo `MaxReceivedMessageSize`. No entanto, `MaxReceivedMessageSize` conta pré-expansão bytes. Quando a codificação binária está em uso, o consumo de memória pode potencialmente ir além `MaxReceivedMessageSize`, limitado somente por um fator de <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement.MaxSessionSize%2A>. Por esse motivo, é importante definir sempre todas as cotas do leitor (especialmente <xref:System.Xml.XmlDictionaryReaderQuotas.MaxStringContentLength%2A>) ao usar a codificação binária.  
  
 Ao usar a codificação binária junto com o <xref:System.Runtime.Serialization.DataContractSerializer>, o `IExtensibleDataObject` interface pode ser usado de forma incorreta para montar um ataque de expansão do dicionário. Essencialmente, essa interface fornece armazenamento ilimitado para dados arbitrários que não faz parte do contrato. Se as cotas não podem ser definidas como baixas o suficiente, de modo que `MaxSessionSize` multiplicado por `MaxReceivedMessageSize` não representar um problema, desabilite o `IExtensibleDataObject` recurso ao usar a codificação binária. Definir o `IgnoreExtensionDataObject` propriedade `true` no `ServiceBehaviorAttribute` atributo. Como alternativa, não é implementam o `IExtensibleDataObject` interface. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Contratos de dados compatíveis por encaminhamento](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md).  
  
### <a name="quotas-summary"></a>Resumo de cotas  
 A tabela a seguir resume as diretrizes sobre as cotas.  
  
|Condição|Cotas importantes definir|  
|---------------|-----------------------------|  
|Nenhum streaming ou fluxo de mensagens pequenas, texto ou codificação de MTOM|`MaxReceivedMessageSize`, `MaxBytesPerRead` e `MaxDepth`|  
|Nenhum streaming ou fluxo de mensagens pequenas, binárias de codificação|`MaxReceivedMessageSize`, `MaxSessionSize`e todos os`ReaderQuotas`|  
|Fluxo de mensagens grandes, texto ou codificação de MTOM|`MaxBufferSize`e todos os`ReaderQuotas`|  
|Codificação de streaming mensagens grandes binárias|`MaxBufferSize`, `MaxSessionSize`e todos os`ReaderQuotas`|  
  
-   Tempos limite de nível de transporte deve sempre ser definido e nunca use leituras/gravações síncronas quando o fluxo está em uso, independentemente se você estiver realizando o streaming de mensagens grandes ou pequenas.  
  
-   Em caso de dúvida sobre uma cota, defina-o como um valor de seguro em vez de deixá-la aberta.  
  
## <a name="preventing-malicious-code-execution"></a>Impedindo a execução de código mal-intencionado  
 As seguintes classes gerais de ameaças podem executar código e ter efeitos indesejados:  
  
-   O desserializador carrega um tipo não seguro, mal-intencionado ou sensível à segurança.  
  
-   Uma mensagem de entrada faz com que o desserializador construir uma instância de um tipo de segurança normalmente de tal forma que ele tem consequências não intencionais.  
  
 As seções a seguir discutem essas classes de ameaças adicionais.  
  
## <a name="datacontractserializer"></a>DataContractSerializer  
 (Para obter informações de segurança sobre o <xref:System.Xml.Serialization.XmlSerializer>, consulte a documentação relevante.) O modelo de segurança para o <xref:System.Xml.Serialization.XmlSerializer> é semelhante do <xref:System.Runtime.Serialization.DataContractSerializer>e diferem principalmente em detalhes. Por exemplo, o <xref:System.Xml.Serialization.XmlIncludeAttribute> atributo é usado para a inclusão de tipo em vez do <xref:System.Runtime.Serialization.KnownTypeAttribute> atributo. No entanto, algumas ameaças exclusivas para o <xref:System.Xml.Serialization.XmlSerializer> são discutidos neste tópico.  
  
### <a name="preventing-unintended-types-from-being-loaded"></a>Impedir que os tipos não intencionais que está sendo carregado  
 Carregar tipos pode ter consequências significativas, se o tipo é mal-intencionado ou apenas tem efeitos colaterais de segurança. Um tipo pode conter vulnerabilidade de segurança explorável, executar ações de segurança em seu construtor ou o construtor de classe, têm uma superfície de memória grandes que facilita a ataques de negação de serviço, ou pode gerar exceções não recuperável. Tipos podem ter construtores de classe executam assim que o tipo é carregado e antes que todas as instâncias são criadas. Por esses motivos, é importante controlar o conjunto de tipos que o desserializador pode carregar.  
  
 O <xref:System.Runtime.Serialization.DataContractSerializer> desserializa de forma flexível. Nunca lê common language runtime (CLR) nomes de tipo e assembly de dados de entrada. Isso é semelhante ao comportamento do <xref:System.Xml.Serialization.XmlSerializer>, mas é diferente do comportamento do <xref:System.Runtime.Serialization.NetDataContractSerializer>, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>e o <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>. Acoplamento apresenta um nível de segurança, porque o invasor remoto não pode indicar um tipo arbitrário para carregar apenas por esse tipo na mensagem de nomenclatura.  
  
 O <xref:System.Runtime.Serialization.DataContractSerializer> sempre tem permissão para carregar um tipo que atualmente é esperado acordo com o contrato. Por exemplo, se um contrato de dados tem um membro de dados do tipo `Customer`, o <xref:System.Runtime.Serialization.DataContractSerializer> tem permissão para carregar o `Customer` tipo quando ele desserializa este membro de dados.  
  
 Além disso, o <xref:System.Runtime.Serialization.DataContractSerializer> oferece suporte a polimorfismo. Um membro de dados pode ser declarado como <xref:System.Object>, mas os dados de entrada podem conter um `Customer` instância. Isso é possível somente se o `Customer` tipo foi feito "conhecido" para o desserializador por meio de um desses mecanismos:  
  
-   <xref:System.Runtime.Serialization.KnownTypeAttribute>aplicado a um tipo de atributo.  
  
-   `KnownTypeAttribute`especificando um método que retorna uma lista de tipos de atributo.  
  
-   `ServiceKnownTypeAttribute`atributo.  
  
-   O `KnownTypes` seção de configuração.  
  
-   Uma lista de tipos conhecidos passado explicitamente para o <xref:System.Runtime.Serialization.DataContractSerializer> durante a construção, se usar o serializador diretamente.  
  
 Cada um desses mecanismos aumenta a área da superfície introduzindo mais tipos que o desserializador pode carregar. Controle cada um desses mecanismos para garantir que nenhum tipo mal-intencionado ou indesejado é adicionado à lista de tipos conhecidos.  
  
 Depois que um tipo conhecido estiver no escopo, pode ser carregado a qualquer momento e instâncias do tipo podem ser criadas, mesmo se o contrato proíbe realmente usá-lo. Por exemplo, suponha que o tipo "MyDangerousType" é adicionada à lista de tipos conhecidos usando um dos mecanismos acima. Isso significa que:  
  
-   `MyDangerousType`é carregado e o construtor de classe é executado.  
  
-   Mesmo quando a desserialização de um contrato de dados com um membro de dados de cadeia de caracteres, uma mensagem mal-intencionado ainda pode causar uma instância de `MyDangerousType` para criar. O código no `MyDangerousType`, como setters de propriedade, pode ser executada. Depois que isso for feito, o desserializador tenta atribuir essa instância para o membro de dados de cadeia de caracteres e falhar com uma exceção.  
  
 Ao escrever um método que retorna uma lista de tipos conhecidos, ou ao passar uma lista diretamente para o <xref:System.Runtime.Serialization.DataContractSerializer> construtor, certifique-se de que o código que prepara a lista é seguro e funciona apenas em dados confiáveis.  
  
 Se especificar tipos conhecidos na configuração, certifique-se de que o arquivo de configuração é seguro. Sempre use nomes de alta segurança na configuração (especificando a chave pública do assembly assinado onde reside o tipo), mas não especificar a versão do tipo de carga. O carregador de tipo escolhe automaticamente a versão mais recente, se possível. Se você especificar uma versão específica na configuração, você corre o risco de seguinte: um tipo pode ter uma vulnerabilidade de segurança que pode ser corrigida em uma versão futura, mas a versão vulnerável ainda é carregado porque ele é explicitamente especificado na configuração.  
  
 Ter muitos tipos conhecidos tem outra consequência: O <xref:System.Runtime.Serialization.DataContractSerializer> cria um cache de código de serialização/desserialização no domínio do aplicativo, com uma entrada para cada tipo deve serializar e desserializar. Esse cache é limpo nunca desde que o domínio de aplicativo está em execução. Portanto, um invasor que está ciente de que um aplicativo usa muitos tipos conhecidos pode causar a desserialização de todos esses tipos, fazendo com que o cache consumir uma desproporcionalmente grande quantidade de memória.  
  
### <a name="preventing-types-from-being-in-an-unintended-state"></a>Impedir que os tipos em um estado não intencional  
 Um tipo pode ter restrições de consistência interna que devem ser impostas. Deve-se ter cuidado para evitar essas restrições durante a desserialização.  
  
 O exemplo a seguir de um tipo representa o estado de uma câmara em uma nave espacial e impõe a restrição que interna e as portas externas não podem ser abertas ao mesmo tempo.  
  
 [!code-csharp[DataContractAttribute#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/datacontractattribute/cs/overview.cs#3)]
 [!code-vb[DataContractAttribute#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/datacontractattribute/vb/overview.vb#3)]  
  
 Um invasor pode enviar uma mensagem mal-intencionado assim, ao redor das restrições e Obtendo o objeto em um estado inválido, o que pode ter consequências não intencionais e imprevisíveis.  
  
```xml  
<SpaceStationAirlock>  
    <innerDoorOpen>true</innerDoorOpen>  
    <outerDoorOpen>true</outerDoorOpen>  
</SpaceStationAirlock>  
```  
  
 Essa situação pode ser evitada por estar ciente dos pontos a seguir:  
  
-   Quando o <xref:System.Runtime.Serialization.DataContractSerializer> desserializa a maioria das classes, construtores não são executados. Portanto, não confie em qualquer feito no construtor de gerenciamento de estado.  
  
-   Use retornos de chamada para garantir que o objeto está em um estado válido. O retorno de chamada é marcado com o <xref:System.Runtime.Serialization.OnDeserializedAttribute> atributo é especialmente útil porque ele é executado após a desserialização foi concluída e tem a oportunidade de examinar e corrigir o estado geral. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Retornos de chamada de serialização tolerantes à versão](../../../../docs/framework/wcf/feature-details/version-tolerant-serialization-callbacks.md).  
  
-   Não crie tipos de contrato de dados para confiar em qualquer ordem específica na qual propriedade setters devem ser chamados.  
  
-   Tome cuidado usando tipos herdados marcados com o <xref:System.SerializableAttribute> atributo. Muitas delas foram projetadas para trabalhar com [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] remoting para uso com apenas dados confiáveis. Os tipos existentes marcados com esse atributo podem não tiver sido criados com a segurança de estado em mente.  
  
-   Não confie no <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> propriedade o `DataMemberAttribute` atributo para garantir a presença de dados que diz respeito a segurança de estado. Dados podem ser sempre `null`, `zero`, ou `invalid`.  
  
-   Nunca confiança um gráfico de objeto desserializado a partir de uma fonte de dados não confiável sem validá-lo primeiro. Cada objeto individual pode estar em um estado consistente, mas o gráfico de objeto que não pode ser um inteiro. Além disso, mesmo se o modo de preservação de gráfico de objeto estiver desabilitado, o gráfico desserializado pode ter várias referências ao mesmo objeto ou ter referências circulares. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Serialização e desserialização](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md).  
  
### <a name="using-the-netdatacontractserializer-securely"></a>Usando o NetDataContractSerializer com segurança  
 O <xref:System.Runtime.Serialization.NetDataContractSerializer> é um mecanismo de serialização que usa um acoplamento de tipos. Isso é semelhante de <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> e <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>. Ou seja, ele determina que tipo de instanciar lendo o [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] assembly e nome de tipo de dados de entrada. Embora seja uma parte de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], não há nenhuma maneira fornecida de conectar esse mecanismo de serialização; código personalizado deve ser gravado. O `NetDataContractSerializer` é fornecida principalmente para facilitar a migração do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] remoto para [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]a seção em [serialização e desserialização](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md).  
  
 Porque a mensagem em si pode indicar qualquer tipo pode ser carregado, o <xref:System.Runtime.Serialization.NetDataContractSerializer> mecanismo é intrinsecamente não segura e deve ser usado apenas com dados confiáveis. É possível proteger escrevendo um associador de tipo seguro, limitando o tipo que permite que somente os tipos seguros carregar (usando o <xref:System.Runtime.Serialization.NetDataContractSerializer.Binder%2A> propriedade).  
  
 Mesmo quando usados com dados confiáveis, os dados de entrada insuficientemente podem especificar o tipo de carga, especialmente se o <xref:System.Runtime.Serialization.NetDataContractSerializer.AssemblyFormat%2A> está definida como <xref:System.Runtime.Serialization.Formatters.FormatterAssemblyStyle.Simple>. Qualquer pessoa com acesso ao diretório do aplicativo ou no cache de assembly global pode substituir um tipo mal-intencionado no lugar que deve ser carregado. Sempre verifique se a segurança do diretório do aplicativo e do cache de assembly global definindo as permissões corretamente.  
  
 Em geral, se você permitir acesso de código parcialmente confiável ao seu `NetDataContractSerializer` instância ou caso contrário, o seletor de substitutos de controle (<xref:System.Runtime.Serialization.ISurrogateSelector>) ou o associador de serialização (<xref:System.Runtime.Serialization.SerializationBinder>), o código pode exercer uma grande quantidade de controle sobre o processo de serialização/desserialização. Por exemplo, ele pode injetar tipos arbitrários, levar a divulgação de informações, adulterar o gráfico resultante do objeto ou dados serializados ou estouro resultante fluxo serializado.  
  
 Outro problema de segurança com o `NetDataContractSerializer` é uma negação de serviço, não uma ameaça de execução de código mal-intencionado. Ao usar o `NetDataContractSerializer`, sempre defina a <xref:System.Runtime.Serialization.NetDataContractSerializer.MaxItemsInObjectGraph%2A> cota para um valor de segurança. É fácil construir uma mensagem pequena mal-intencionados que aloca uma matriz de objetos cujo tamanho é limitado apenas por essa cota.  
  
### <a name="xmlserializer-specific-threats"></a>Ameaças específicas de XmlSerializer  
 O <xref:System.Xml.Serialization.XmlSerializer> modelo de segurança é semelhante do <xref:System.Runtime.Serialization.DataContractSerializer>. No entanto, algumas ameaças, são exclusivas para o <xref:System.Xml.Serialization.XmlSerializer>.  
  
 O <xref:System.Xml.Serialization.XmlSerializer> gera *assemblies de serialização* em tempo de execução que contêm código que realmente serializa e desserializa; esses assemblies são criados em um diretório de arquivos temporários. Se algum outro processo ou usuário tem direitos de acesso ao diretório, eles podem substituir o código de serialização/desserialização com um código arbitrário. O <xref:System.Xml.Serialization.XmlSerializer> executa esse código usando o contexto de segurança, em vez do código de serialização/desserialização. Verifique se que as permissões estão definidas corretamente no diretório de arquivos temporários para evitar que isso aconteça.  
  
 O <xref:System.Xml.Serialization.XmlSerializer> também tem um modo em que ele usa os assemblies de serialização gerado em vez de gerá-los em tempo de execução. Esse modo é disparado sempre que o <xref:System.Xml.Serialization.XmlSerializer> pode localizar um assembly de serialização adequado. O <xref:System.Xml.Serialization.XmlSerializer> verifica se o assembly de serialização foi assinado pela mesma chave que foi usada para assinar o assembly que contém os tipos que está sendo serializados. Isso oferece proteção contra assemblies maliciosos sendo disfarçados assemblies de serialização. No entanto, se o assembly que contém seus tipos serializáveis não estiver assinado, o <xref:System.Xml.Serialization.XmlSerializer> não é possível executar essa verificação e usa qualquer assembly com o nome correto. Isso possibilita a execução do código mal-intencionado. Assinar sempre os assemblies que contêm seus tipos serializáveis ou controlar rigorosamente o acesso ao diretório do aplicativo e o cache de assembly global para evitar a introdução de assemblies maliciosos.  
  
 O <xref:System.Xml.Serialization.XmlSerializer> podem estar sujeitos a um ataque de negação de serviço. O <xref:System.Xml.Serialization.XmlSerializer> não tem um `MaxItemsInObjectGraph` cota (como está disponível na <xref:System.Runtime.Serialization.DataContractSerializer>). Portanto, ele desserializa uma quantidade arbitrária de objetos, limitado apenas pelo tamanho da mensagem.  
  
### <a name="partial-trust-threats"></a>Ameaças de confiança parcial  
 Observe as seguintes questões sobre ameaças relacionadas a código em execução com confiança parcial. Essas ameaças incluem mal-intencionado código parcialmente confiável, bem como código mal-intencionado parcialmente confiável em combinação com outros cenários de ataque (por exemplo, parcialmente confiável código que constrói uma cadeia de caracteres específica e, em seguida, desserializá-lo).  
  
-   Ao usar os componentes de serialização, nunca assert todas as permissões antes de tal uso, mesmo que o cenário de serialização inteira é dentro do escopo de sua declaração, e você não está lidando com os dados não confiáveis ou objetos. Tal uso pode levar a vulnerabilidades de segurança.  
  
-   Em casos em que o código parcialmente confiável tem controle sobre o processo de serialização, por meio de pontos de extensibilidade (substitutos), que está sendo serializados, de tipos ou outros meios, o código parcialmente confiável pode causar o serializador gerar uma grande quantidade de dados no fluxo serializado, que pode causar negação de serviço (DoS) para o receptor deste fluxo. Se a serialização de dados destinados a um destino que diferencia ameaças DoS, não serializar tipos parcialmente confiável ou caso contrário, deixe a serialização de controle do código parcialmente confiável.  
  
-   Se você permitir acesso de código parcialmente confiável para seus <xref:System.Runtime.Serialization.DataContractSerializer> instância ou controlar a [substitutos de contrato de dados](../../../../docs/framework/wcf/extending/data-contract-surrogates.md), ele pode exercer um grande controle sobre o processo de serialização/desserialização. Por exemplo, ele pode injetar tipos arbitrários, levar a divulgação de informações, adulterar o gráfico resultante do objeto ou dados serializados ou estouro resultante fluxo serializado. Um equivalente <xref:System.Runtime.Serialization.NetDataContractSerializer> ameaça é descrita na seção "Usando o NetDataContractSerializer com segurança".  
  
-   Se o <xref:System.Runtime.Serialization.DataContractAttribute> atributo é aplicado a um tipo (ou o tipo marcado como `[Serializable]` , mas não é `ISerializable`), o desserializador pode criar uma instância de um tipo como esse mesmo que todos os construtores não público ou protegido por demanda.  
  
-   Nunca confie o resultado de desserialização, a menos que os dados a ser desserializado são confiáveis e ter certeza de que todos os tipos conhecidos são tipos que você confia. Observe que tipos conhecidos não são carregadas do arquivo de configuração de aplicativo, (mas são carregados a partir do arquivo de configuração do computador) quando em execução em confiança parcial.  
  
-   Se você passar um `DataContractSerializer` instância com um substituto adicionada ao código parcialmente confiável, o código pode alterar quaisquer configurações modificáveis esse alternativo.  
  
-   Para um objeto desserializado, se o leitor de XML (ou os dados contidos) vem de código parcialmente confiável, tratar o objeto desserializado resultante como dados não confiáveis.  
  
-   O fato de que o <xref:System.Runtime.Serialization.ExtensionDataObject> não público do tipo tem membros não significa que os dados nela são seguros. Por exemplo, se você desserializar a partir de uma fonte de dados com privilégios em um objeto no qual residem o alguns dados, disponível depois que o objeto para o código parcialmente confiável, o código parcialmente confiável pode ler os dados no `ExtensionDataObject` ao serializar o objeto. Considere a configuração de <xref:System.Runtime.Serialization.DataContractSerializer.IgnoreExtensionDataObject%2A> para `true` quando a desserialização de uma fonte de dados com privilégios em um objeto que for posteriormente passado para código parcialmente confiável.  
  
-   <xref:System.Runtime.Serialization.DataContractSerializer>e <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> oferecem suporte a serialização de membros privados, protegidos, internos e públicos em confiança total. No entanto, em confiança parcial, somente os membros públicos podem ser serializados. Um `SecurityException` é gerada se um aplicativo tenta serializar um membro não público.  
  
     Para permitir interno ou membros internos protegidos a ser serializado em confiança parcial, use o `System.Runtime.CompilerServices.InternalsVisibleTo` atributo do assembly. Este atributo permite um assembly declarar que seus membros internos são visíveis para algum outro assembly. Nesse caso, um assembly que deseja que seus membros internos serializados declara que seus membros internos são visíveis para System.Runtime.Serialization.dll.  
  
     A vantagem dessa abordagem é que ele não requer um caminho de geração de código com privilégios elevados.  
  
     Ao mesmo tempo, há duas grandes desvantagens.  
  
     A primeira desvantagem é que a propriedade de aceitação do `InternalsVisibleTo` atributo é todo o assembly. Ou seja, você não pode especificar que somente uma determinada classe pode ter seus membros internos serializados. Naturalmente, você ainda pode escolher para não serializar um membro interno específico, simplesmente não adicionando um `DataMember` a esse membro de atributo. Da mesma forma, um desenvolvedor também pode escolher tornar um membro interno em vez de particular ou protegido com preocupações de visibilidade pequena.  
  
     A segunda desvantagem é que ainda não dá suporte a membros particulares ou protegidos.  
  
     Para ilustrar o uso do `InternalsVisibleTo` atributo em confiança parcial, considere o seguinte programa:  
  
     [!code-csharp[CDF_WCF_SecurityConsiderationsForData#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/cdf_wcf_securityconsiderationsfordata/cs/program.cs#1)]  
  
     No exemplo acima, `PermissionsHelper.InternetZone` corresponde do `PermissionSet` de confiança parcial. Agora, sem `InternalsVisibleToAttribute`, o aplicativo falhará, gerando um `SecurityException` indicando que os membros não públicos não podem ser serializados em confiança parcial.  
  
     No entanto, se adicionar a seguinte linha ao arquivo de origem, o programa é executado com êxito.  
  
     [!code-csharp[CDF_WCF_SecurityConsiderationsForData#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/cdf_wcf_securityconsiderationsfordata/cs/program.cs#2)]  
  
## <a name="other-state-management-concerns"></a>Outros problemas de gerenciamento de estado  
 Algumas outras preocupações sobre o gerenciamento de estado do objeto são vale a pena mencionar:  
  
-   Ao usar o modelo de programação baseado em fluxo com um transporte de streaming, o processamento da mensagem ocorre como a mensagem chega. O remetente da mensagem pode anular a operação de envio no meio de fluxo, deixando o seu código em um estado imprevisível se mais conteúdo era esperado. Em geral, não confie no fluxo que está sendo concluída e não executar qualquer trabalho em uma operação com base em fluxo que não pode ser revertida novamente no caso do fluxo foi anulado. Isso também se aplica à situação em que uma mensagem pode estar mal formada após o corpo de streaming (por exemplo, ele pode estar faltando uma marca de fim para o envelope SOAP ou pode ter um corpo de mensagem segundo).  
  
-   Usando o `IExtensibleDataObject` recurso pode fazer com que os dados confidenciais ser emitida. Se você estiver retornando dados de uma fonte não confiável em contratos de dados com `IExtensibleObjectData` e mais tarde novamente emitindo-lo em um canal seguro em que as mensagens são assinadas, você está potencialmente atestar dados que você não sabe nada sobre. Além disso, o estado geral que você está enviando pode ser inválido, se você considerar as partes conhecidas e desconhecidas dos dados. Evitar essa situação, qualquer seletivamente definindo a propriedade de dados de extensão `null` ou desabilitando seletivamente o `IExtensibleObjectData` recurso.  
  
## <a name="schema-import"></a>Importação de esquema  
 Normalmente, o processo de importação de esquema para gerar tipos ocorre somente em tempo de design, por exemplo, ao usar o [Ferramenta Utilitária de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) em um serviço da Web para gerar uma classe de cliente. No entanto, em cenários mais avançados, você pode processar um esquema em tempo de execução. Lembre-se de que isso pode expor você quanto a riscos de negação de serviço. Alguns esquema pode levar muito tempo para ser importado. Nunca use o <xref:System.Xml.Serialization.XmlSerializer> componente de importação de esquema nesses cenários se esquemas possivelmente são provenientes de uma fonte não confiável.  
  
## <a name="threats-specific-to-aspnet-ajax-integration"></a>Ameaças específicas para a integração de AJAX ASP.NET  
 Quando o usuário implementa <xref:System.ServiceModel.Description.WebScriptEnablingBehavior> ou <xref:System.ServiceModel.Description.WebHttpBehavior>, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] expõe um ponto de extremidade que aceita mensagens XML e JSON. No entanto, há apenas um conjunto de cotas do leitor, usado pelo leitor de XML e o leitor JSON. Algumas configurações de cota podem ser apropriado para um leitor, mas muito grande para o outro.  
  
 Ao implementar `WebScriptEnablingBehavior`, o usuário tem a opção para expor um proxy JavaScript no ponto de extremidade. Os seguintes problemas de segurança devem ser considerados:  
  
-   Informações sobre o serviço (nomes de operação, os nomes de parâmetro e assim por diante) podem ser obtidas por meio do exame proxy JavaScript.  
  
-   Ao usar o ponto de extremidade do JavaScript, informações confidenciais e privadas podem ser retidas no cliente de cache do navegador da Web.  
  
## <a name="a-note-on-components"></a>Uma observação sobre componentes  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]é um sistema flexível e personalizável. A maioria do conteúdo deste tópico enfocam os mais comuns [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] cenários de uso. No entanto, é possível compor componentes [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] fornece muitas maneiras diferentes. É importante entender as implicações de segurança do uso de cada componente. Em particular:  
  
-   Quando você deve usar leitores XML, use os leitores a <xref:System.Xml.XmlDictionaryReader> classe fornece em vez de quaisquer outros leitores. Leitores de seguros são criados usando <xref:System.Xml.XmlDictionaryReader.CreateTextReader%2A>, <xref:System.Xml.XmlDictionaryReader.CreateBinaryReader%2A>, ou <xref:System.Xml.XmlDictionaryReader.CreateMtomReader%2A> métodos. Não use o <xref:System.Xml.XmlReader.Create%2A> método. Sempre configure os leitores com as cotas de seguras. A serialização de mecanismos em [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] são seguras somente quando usada com leitores XML seguros de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
-   Ao usar o <xref:System.Runtime.Serialization.DataContractSerializer> para desserializar dados potencialmente não confiáveis, defina sempre o <xref:System.Runtime.Serialization.DataContractSerializer.MaxItemsInObjectGraph%2A> propriedade.  
  
-   Ao criar uma mensagem, defina o `maxSizeOfHeaders` parâmetro se `MaxReceivedMessageSize` não oferece proteção suficiente.  
  
-   Ao criar um codificador, sempre configurar as cotas relevantes, como `MaxSessionSize` e `MaxBufferSize`.  
  
-   Ao usar um filtro de mensagem do XPath, defina o <xref:System.ServiceModel.Dispatcher.XPathMessageFilter.NodeQuota%2A> para limitar a quantidade de nós XML visita o filtro. Não use expressões XPath que podem levar muito tempo para sem visitar vários nós de computação.  
  
-   Em geral, ao usar qualquer componente que aceita uma cota, compreender suas implicações de segurança e defina-o como um valor de seguro.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 <xref:System.Xml.XmlDictionaryReader>  
 <xref:System.Xml.Serialization.XmlSerializer>  
 [Tipos conhecidos de contrato de dados](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
