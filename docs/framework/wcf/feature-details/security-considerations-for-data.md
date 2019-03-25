---
title: Considerações de segurança para dados
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a7eb98da-4a93-4692-8b59-9d670c79ffb2
ms.openlocfilehash: 13e596ea64fc62ed6280e74636243619178ce069
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/25/2019
ms.locfileid: "58411428"
---
# <a name="security-considerations-for-data"></a>Considerações de segurança para dados

Ao lidar com dados no Windows Communication Foundation (WCF), você deve considerar um número de categorias de ameaça. A tabela a seguir lista as classes de ameaças mais importantes relacionados ao processamento de dados. O WCF fornece ferramentas para atenuar essas ameaças.

Negação de serviço durante o recebimento de dados não confiáveis, os dados podem causar o lado de recebimento acessar uma quantidade desproporcional de vários recursos, como memória, threads, conexões disponíveis ou ciclos de processador, fazendo com que as computações longas. Um ataque de negação de serviço contra um servidor pode causar a falhar e ser capaz de processar mensagens de clientes de outros e legítimos.

Execução de código mal-intencionado dados faz com que o lado de recebimento executar código não confiável para entrada ele não pretendia.

O invasor remoto de divulgação de informações força a parte destinatária para responder a solicitações de maneira a divulgar informações mais do que pretende.

## <a name="user-provided-code-and-code-access-security"></a>Código fornecido pelo usuário e segurança de acesso do código

Um número de lugares na infraestrutura do Windows Communication Foundation (WCF), executar o código que é fornecido pelo usuário. Por exemplo, o <xref:System.Runtime.Serialization.DataContractSerializer> mecanismo de serialização pode chamar a propriedade fornecida pelo usuário `set` acessadores e `get` acessadores. A infra-estrutura de canal WCF também pode chamar em classes derivadas fornecido pelo usuário da <xref:System.ServiceModel.Channels.Message> classe.

É responsabilidade do autor do código para garantir que nenhuma vulnerabilidade de segurança existe. Por exemplo, se você criar um contrato de dados tipo com uma propriedade de membro de dados do tipo inteiro e, no `set` implementação do acessador alocar uma matriz com base no valor da propriedade, você expõe a possibilidade de um ataque de negação de serviço, se um mal-intencionado mensagem contém um valor muito grande para este membro de dados. Em geral, evite qualquer alocação com base nos dados de entrada ou extenso de processamento no código fornecido pelo usuário (especialmente se o processamento mais extenso pode ser causado por uma pequena quantidade de dados de entrada). Ao executar a análise de segurança de código fornecido pelo usuário, certifique-se também considerar todos os casos de falha (ou seja, todas as ramificações do código em que as exceções são geradas).

O exemplo de código fornecido pelo usuário a ultimate é o código dentro de sua implementação de serviço para cada operação. A segurança de sua implementação de serviço é sua responsabilidade. É fácil criar inadvertidamente as implementações de operação não segura que podem resultar em vulnerabilidades de negação de serviço. Por exemplo, uma operação que usa uma cadeia de caracteres e retorna a lista de clientes de um banco de dados cujo nome começa com essa cadeia de caracteres. Se você estiver trabalhando com um banco de dados grande e a cadeia de caracteres que está sendo passada é apenas uma única letra, seu código pode tentar criar uma mensagem maior que toda a memória disponível, fazendo com que todo o serviço falhe. (Um <xref:System.OutOfMemoryException> não é recuperável no [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] e sempre resulta no encerramento do aplicativo.)

Você deve garantir que nenhum código mal-intencionado está conectado a vários pontos de extensibilidade. Isso é especialmente relevante ao executar em confiança parcial, lidando com tipos de assemblies de confiança parcial, ou criando componentes utilizável por código parcialmente confiável. Para obter mais informações, consulte "Ameaças de confiança parcial" em uma seção posterior.

Observe que, quando em execução em confiança parcial, a infraestrutura de serialização do contrato de dados oferece suporte a apenas um subconjunto limitado de dados contrato do modelo de programação – por exemplo, membros de dados particulares ou tipos usando o <xref:System.SerializableAttribute> não há suporte para o atributo. Para obter mais informações, consulte [confiança parcial](../../../../docs/framework/wcf/feature-details/partial-trust.md).

## <a name="avoiding-unintentional-information-disclosure"></a>Evitar a divulgação não intencional de informações

Ao projetar tipos serializáveis com segurança em mente, divulgação de informações é uma preocupação possíveis.

Considere os seguintes pontos:

- O <xref:System.Runtime.Serialization.DataContractSerializer> modelo de programação permite a exposição de dados privados e internos fora do tipo ou assembly durante a serialização. Além disso, a forma de um tipo pode ser exposta durante a exportação de esquema. Certifique-se de entender a projeção de serialização do tipo. Se você não quiser que qualquer coisa exposta, desabilitar serializá-lo (por exemplo, por não aplicação de <xref:System.Runtime.Serialization.DataMemberAttribute> atributo no caso de um contrato de dados).

- Lembre-se de que o mesmo tipo pode ter várias projeções de serialização, dependendo do serializador em uso. O mesmo tipo pode expor um conjunto de dados quando usado com o <xref:System.Runtime.Serialization.DataContractSerializer> e outro conjunto de dados quando usado com o <xref:System.Xml.Serialization.XmlSerializer>. Acidentalmente usar o serializador errado pode levar à divulgação de informações.

- Usando o <xref:System.Xml.Serialization.XmlSerializer> herdados procedimento remoto (RPC) de chamar / modo codificado pode sem querer expor a forma do grafo do objeto no lado de envio para o lado de recebimento.

## <a name="preventing-denial-of-service-attacks"></a>Impedindo ataques de negação de serviço

### <a name="quotas"></a>Cotas

Fazendo com que o lado de recebimento alocar uma quantidade significativa de memória é um potencial ataque de negação de serviço. Embora esta seção se concentra em problemas de consumo de memória resultantes de mensagens grandes, podem ocorrer outros ataques. Por exemplo, as mensagens podem usar uma quantidade desproporcional de tempo de processamento.

Ataques de negação de serviço geralmente são atenuados com o uso de cotas. Quando uma cota for ultrapassada, um <xref:System.ServiceModel.QuotaExceededException> exceção normalmente é lançada. Sem a cota, uma mensagem mal-intencionada pode fazer com que toda a memória disponível ser acessado, resultando em uma <xref:System.OutOfMemoryException> exceção ou todas as pilhas disponíveis para serem acessados, resultando em um <xref:System.StackOverflowException>.

O cenário de cota excedida é recuperável; Se encontrado em um serviço em execução, a mensagem que está sendo processada no momento será descartada e o serviço continua em execução e processa mensagens adicionais. Os cenários de estouro de memória insuficiente e pilha, no entanto, não são recuperáveis em qualquer lugar do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]; o serviço será encerrado se ele encontrar essas exceções.

Cotas no WCF não envolvem qualquer pré-alocação. Por exemplo, se o <xref:System.ServiceModel.Channels.TransportBindingElement.MaxReceivedMessageSize%2A> cota (encontrada em várias classes) é definida como 128 KB, isso não significa que 128 KB é alocado automaticamente para cada mensagem. O real valor alocado depende do tamanho de mensagem de entrada real.

Muitas cotas estão disponíveis na camada de transporte. Essas são as cotas impostas pelo canal de transporte específico em uso (HTTP, TCP e assim por diante). Embora este tópico discute algumas dessas cotas, essas cotas são descritas detalhadamente na [cotas de transporte](../../../../docs/framework/wcf/feature-details/transport-quotas.md).

### <a name="hashtable-vulnerability"></a>Vulnerabilidade de tabela de hash

Existe uma vulnerabilidade quando os contratos de dados contêm coleções ou tabelas de hash. O problema ocorre se um grande número de valores é inserido em uma tabela de hash em que um grande número desses valores de gerar o mesmo valor de hash. Isso pode ser usado como um ataque DOS.  Essa vulnerabilidade pode ser reduzida definindo a cota de associação MaxReceivedMessageSize. Tome cuidado ao definir essa cota a fim de evitar esses ataques. Essa cota coloca um limite superior no tamanho da mensagem do WCF. Além disso, evite usar coleções ou tabelas de hash em seus contratos de dados.

## <a name="limiting-memory-consumption-without-streaming"></a>Limitando o consumo de memória sem Streaming

O modelo de segurança em torno de mensagens grandes depende se o streaming está em uso. No caso do basic, não transmitidos por Streaming, as mensagens são armazenadas em buffer na memória. Nesse caso, use o <xref:System.ServiceModel.Channels.TransportBindingElement.MaxReceivedMessageSize%2A> cota a <xref:System.ServiceModel.Channels.TransportBindingElement> ou em associações fornecidas pelo sistema para proteger contra mensagens grandes, limitando o tamanho máximo da mensagem para acessar. Observe que um serviço pode processar várias mensagens ao mesmo tempo, caso em que eles estão todos em memória. Use o recurso de limitação para reduzir essa ameaça.

Observe também que `MaxReceivedMessageSize` não coloca um limite superior no consumo de memória por mensagem, mas limita-lo para dentro de um fator constante. Por exemplo, se o `MaxReceivedMessageSize` é 1 MB e é recebida uma mensagem de 1 MB e, em seguida, desserializada memória adicional é necessária para conter o grafo de objeto desserializado, resultando em bem de consumo de memória total acima de 1 MB. Por esse motivo, evite criar tipos serializáveis que podem resultar em consumo de memória significativa sem muitos dados de entrada. Por exemplo, um contrato de dados "MyContract" com campos de membro de dados opcionais 50 e um adicional 100 campos privados pôde ser instanciado com a construção de XML "\<MyContract / >". Esse XML resulta em memória que está sendo acessada para campos de 150. Observe que os membros de dados são opcionais por padrão. O problema é complexo quando desse tipo é parte de uma matriz.

`MaxReceivedMessageSize` sozinho não é suficiente para impedir que todos os ataques de negação de serviço. Por exemplo, o desserializador pode ser forçado para desserializar um grafo de objeto aninhado mais profundamente (um objeto que contém o outro objeto que contém uma outra e assim por diante) por uma mensagem de entrada. Tanto a <xref:System.Runtime.Serialization.DataContractSerializer> e o <xref:System.Xml.Serialization.XmlSerializer> chamar métodos de forma aninhada para desserializar esses gráficos. O aninhamento profundo de chamadas de método pode resultar em um irrecuperável <xref:System.StackOverflowException>. Essa ameaça é atenuada, definindo o <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement.MaxDepth%2A> cota para limitar o nível de aninhamento de XML, conforme discutido na seção "Usando XML com segurança" posteriormente neste tópico.

Definir cotas adicionais como `MaxReceivedMessageSize` é especialmente importante ao usar a codificação binária de XML. Usando a codificação binária é um pouco equivalente à compactação: um pequeno grupo de bytes na mensagem de entrada pode representar muitos dados. Assim, até mesmo uma mensagem ajustando-se para o `MaxReceivedMessageSize` limite pode levar muito mais memória no formulário totalmente expandido. Para atenuar essas ameaças específicas de XML, todas as cotas do leitor XML devem ser definidas corretamente, conforme discutido na seção "Usando XML com segurança" neste tópico.

## <a name="limiting-memory-consumption-with-streaming"></a>Limitando o consumo de memória com a transmissão

Quando o streaming, você pode usar um pequeno `MaxReceivedMessageSize` configuração para proteger contra ataques de negação de serviço. No entanto, em cenários mais complexos são possíveis com a transmissão. Por exemplo, um serviço de upload de arquivo aceita arquivos maiores que toda a memória disponível. Nesse caso, defina o `MaxReceivedMessageSize` para um valor muito grande, esperar que quase nenhum dado é armazenado em buffer na memória e a mensagem transmite diretamente no disco. Se uma mensagem mal-intencionada pode forçar o WCF em buffer os dados em vez de transmitir-nesse caso, alguma forma `MaxReceivedMessageSize` não protege contra a mensagem de acesso a toda a memória disponível.

Para atenuar essa ameaça, as configurações de cota específico existem em vários componentes de processamento de dados WCF esse limite de buffer. O mais importante é o `MaxBufferSize` propriedade em vários elementos de associação de transporte e associações padrão. Quando o streaming, essa cota deve ser definida levando em consideração a quantidade máxima de memória que você está disposto a alocar por mensagem. Assim como acontece com `MaxReceivedMessageSize`, a configuração não coloca um máximo absoluto consumo de memória, mas apenas limita-lo para dentro de um fator constante. Além disso, como com `MaxReceivedMessageSize`, lembre-se da possibilidade de várias mensagens que estão sendo processadas simultaneamente.

### <a name="maxbuffersize-details"></a>MaxBufferSize detalhes

O `MaxBufferSize` propriedade limita qualquer em massa WCF buffer faz. Por exemplo, o WCF sempre armazena cabeçalhos SOAP e falhas de SOAP, bem como quaisquer partes MIME não consideradas na ordem natural de leitura em uma mensagem MTOM Message Transmission Optimization Mechanism (). Essa configuração limita a quantidade de armazenamento em buffer em todos esses casos.

O WCF faz isso passando o `MaxBufferSize` valor para os vários componentes que podem armazenar em buffer. Por exemplo, algumas <xref:System.ServiceModel.Channels.Message.CreateMessage%2A> sobrecargas do <xref:System.ServiceModel.Channels.Message> classe take um `maxSizeOfHeaders` parâmetro. O WCF passa o `MaxBufferSize` valor para esse parâmetro para limitar a quantidade de buffer de cabeçalho SOAP. É importante definir esse parâmetro ao usar o <xref:System.ServiceModel.Channels.Message> classe diretamente. Em geral, ao usar um componente no WCF que usa os parâmetros de cota, é importante entender as implicações de segurança desses parâmetros e configurá-los corretamente.

O codificador de mensagem MTOM também tem um `MaxBufferSize` configuração. Ao usar associações padrão, isso é definido automaticamente para o nível de transporte `MaxBufferSize` valor. No entanto, ao usar o elemento de associação do codificador de mensagem MTOM para construir uma ligação personalizada, é importante definir o `MaxBufferSize` propriedade como um valor seguro quando o streaming é usada.

## <a name="xml-based-streaming-attacks"></a>Streaming de ataques baseados em XML

`MaxBufferSize` sozinho não é suficiente para garantir que o WCF não pode ser forçado para armazenamento em buffer ao streaming é esperado. Por exemplo, os leitores XML WCF sempre buffer a marca de início de elemento XML inteira quando começar a ler um novo elemento. Isso é feito para que namespaces e atributos sejam processados corretamente. Se `MaxReceivedMessageSize` está configurado para ser grande (por exemplo, para permitir que um arquivo grande de direct-to-disk cenário de streaming), uma mensagem mal-intencionada pode ser construída em que o corpo da mensagem inteira é uma grande marca de início de elemento XML. Uma tentativa de lê-lo resulta em um <xref:System.OutOfMemoryException>. Esse é um dos muitos ataques de negação de serviço de baseado em XML possíveis que podem todos ser atenuados com cotas do leitor XML, discutidas na seção "Usando XML com segurança" neste tópico. Quando o streaming, é especialmente importante para definir todas essas cotas.

### <a name="mixing-streaming-and-buffering-programming-models"></a>Combinação de Streaming e armazenamento em buffer os modelos de programação

Muitas possíveis ataques são provenientes de misturar modelos de programação streaming e não são de streaming no mesmo serviço. Suponha que exista um contrato de serviço com duas operações: uma usa um <xref:System.IO.Stream> e o outro usa uma matriz de algum tipo personalizado. Suponha também que `MaxReceivedMessageSize` é definida com um valor grande para habilitar a primeira operação processar grandes fluxos. Infelizmente, isso significa que mensagens grandes agora pode ser enviada para a segunda operação e os dados de buffers do desserializador na memória como uma matriz antes da operação é chamada. Este é um ataque de negação de serviço possíveis: o `MaxBufferSize` cota não limita o tamanho do corpo da mensagem, que é o que o desserializador funciona com.

Por esse motivo, evite a mistura de operações com base em fluxo e não transmitidos por Streaming no mesmo contrato. Se você com certeza deve combinar os dois modelos de programação, use as seguintes precauções:

- Desativar o <xref:System.Runtime.Serialization.IExtensibleDataObject> recurso definindo a <xref:System.ServiceModel.ServiceBehaviorAttribute.IgnoreExtensionDataObject%2A> propriedade da <xref:System.ServiceModel.ServiceBehaviorAttribute> para `true`. Isso garante que somente os membros que fazem parte do contrato são desserializados.

- Defina as <xref:System.Runtime.Serialization.DataContractSerializer.MaxItemsInObjectGraph%2A> propriedade do <xref:System.Runtime.Serialization.DataContractSerializer> como um valor seguro. Essa cota também está disponível no <xref:System.ServiceModel.ServiceBehaviorAttribute> atributo ou por meio da configuração. Essa cota limita o número de objetos que serão desserializados em um episódio de desserialização. Normalmente, cada operação parâmetro ou mensagem de parte do corpo em um contrato de mensagem é desserializado em um episódio. Ao desserializar matrizes, cada entrada da matriz é contada como um objeto separado.

- Defina todas as cotas do leitor XML para valores seguros. Preste atenção às <xref:System.Xml.XmlDictionaryReaderQuotas.MaxDepth%2A>, <xref:System.Xml.XmlDictionaryReaderQuotas.MaxStringContentLength%2A>, e <xref:System.Xml.XmlDictionaryReaderQuotas.MaxArrayLength%2A> e evitar cadeias de caracteres em operações de não streaming.

- Examine a lista de tipos conhecidos, tendo em mente que qualquer um deles pode ser instanciado a qualquer momento (consulte a seção "Impedindo não intencionais tipos do que está sendo carregado" mais adiante neste tópico).

- Não use todos os tipos que implementam o <xref:System.Xml.Serialization.IXmlSerializable> interface que muitos dados do buffer. Não adicione esses tipos à lista de tipos conhecidos.

- Não use o <xref:System.Xml.XmlElement>, <xref:System.Xml.XmlNode> matrizes <xref:System.Byte> matrizes ou tipos que implementam <xref:System.Runtime.Serialization.ISerializable> em um contrato.

- Não use o <xref:System.Xml.XmlElement>, <xref:System.Xml.XmlNode> matrizes <xref:System.Byte> matrizes ou tipos que implementam <xref:System.Runtime.Serialization.ISerializable> na lista de tipos conhecidos.

As precauções anteriores se aplicam quando a operação de streaming não usa o <xref:System.Runtime.Serialization.DataContractSerializer>. Nunca misture streaming e modelos de programação não são de streaming no mesmo serviço, se você estiver usando o <xref:System.Xml.Serialization.XmlSerializer>, porque ele não tem a proteção do <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior.MaxItemsInObjectGraph%2A> cota.

### <a name="slow-stream-attacks"></a>Ataques de Stream lento

Uma classe de ataques de negação de serviço de streaming não envolve o consumo de memória. Em vez disso, o ataque envolve um lento remetente ou receptor de dados. Enquanto aguarda os dados a ser enviado ou recebido, recursos como threads e conexões disponíveis são esgotados. Essa situação poderá ocorrer como resultado de um ataque mal-intencionado ou de um remetente/destinatário legítimo em uma conexão de rede lenta.

Para atenuar esses ataques, defina os tempos limite de transporte corretamente. Para obter mais informações, consulte [cotas de transporte](../../../../docs/framework/wcf/feature-details/transport-quotas.md). Em segundo lugar, nunca use síncrono `Read` ou `Write` operações ao trabalhar com fluxos no WCF.

## <a name="using-xml-safely"></a>Usando XML com segurança

> [!NOTE]
> Embora esta seção é sobre XML, as informações também se aplica a documentos de notação JSON (JavaScript Object). As cotas funcionam da mesma forma, usando [mapeamento entre JSON e XML](../../../../docs/framework/wcf/feature-details/mapping-between-json-and-xml.md).

### <a name="secure-xml-readers"></a>Proteger os leitores XML

O XML Infoset constitui a base de todo o processamento de mensagem no WCF. Ao aceitar os dados XML de uma fonte não confiável, um número de ataque de negação de serviço existem possibilidades que deve ser reduzido. O WCF fornece os leitores XML especiais e seguros. Esses leitores são criados automaticamente ao usar uma das codificações padrão no WCF (texto, binária ou MTOM).

Alguns dos recursos de segurança desses leitores estão sempre ativas. Por exemplo, os leitores nunca processam definições de tipo de documento (DTDs), que são uma fonte potencial de ataques de negação de serviço e nunca devem aparecer em mensagens legítimas de SOAP. Outros recursos de segurança incluem as cotas do leitor que devem ser configuradas, que são descritas na seção a seguir.

Ao trabalhar diretamente com os leitores XML (como ao escrever seu próprio codificador personalizado ou ao trabalhar diretamente com o <xref:System.ServiceModel.Channels.Message> classe), sempre use os leitores seguros do WCF, quando há uma chance de trabalhar com dados não confiáveis. Criar os leitores de seguros chamando um dos estática de fábrica sobrecargas do método de <xref:System.Xml.XmlDictionaryReader.CreateTextReader%2A>, <xref:System.Xml.XmlDictionaryReader.CreateBinaryReader%2A>, ou <xref:System.Xml.XmlDictionaryReader.CreateMtomReader%2A> sobre o <xref:System.Xml.XmlDictionaryReader> classe. Ao criar um leitor, passe valores de cota de seguro. Não chame o `Create` sobrecargas de método. Eles não criam um leitor do WCF. Em vez disso, é criado um leitor que não seja protegido pelos recursos de segurança descritos nesta seção.

### <a name="reader-quotas"></a>Cotas do leitor

Os leitores XML seguros tem cinco cotas configuráveis. Eles normalmente são configurados usando o `ReaderQuotas` propriedade na codificação de elementos de associação ou associações padrão ou usando um <xref:System.Xml.XmlDictionaryReaderQuotas> objeto passado durante a criação de um leitor.

#### <a name="maxbytesperread"></a>MaxBytesPerRead

Essa cota limita o número de bytes que são lidos em uma única `Read` de início da operação ao ler o elemento de marca e seus atributos. (Em casos não transmitidos por Streaming, o nome do elemento em si não é contado em relação à cota.) <xref:System.Xml.XmlDictionaryReaderQuotas.MaxBytesPerRead%2A> é importante pelos seguintes motivos:

- O nome do elemento e seus atributos são sempre armazenados em buffer na memória quando elas são lidas. Portanto, é importante definir essa cota corretamente no modo para impedir que o armazenamento em buffer excessivo quando o streaming é esperado de streaming. Consulte o `MaxDepth` seção de cota para obter informações sobre a quantidade real de buffer ocorre.

- Ter atributos XML demais pode consumir todo o tempo de processamento de maneira desproporcional porque a exclusividade dos nomes de atributo tem que ser verificada. O `MaxBytesPerRead` atenua essa ameaça.

#### <a name="maxdepth"></a>MaxDepth

Essa cota limita a profundidade máxima de aninhamento dos elementos XML. Por exemplo, o documento "\<um >\<B >\<C / >\</b >\</A >" tem uma profundidade de aninhamento de três. <xref:System.Xml.XmlDictionaryReaderQuotas.MaxDepth%2A> é importante pelos seguintes motivos:

- O `MaxDepth` interage com o `MaxBytesPerRead`: o leitor sempre mantém dados na memória para o elemento atual e todos os seus ancestrais, para que o consumo máximo de memória do leitor seja proporcional ao produto dessas duas configurações.

- Ao desserializar um grafo de objeto aninhado mais profundamente, o desserializador é forçado para acessar a pilha inteira e gerar um <xref:System.StackOverflowException> irrecuperável. Uma correlação direta existe entre aninhamento de XML e aninhamento de objeto para <xref:System.Runtime.Serialization.DataContractSerializer> e <xref:System.Xml.Serialization.XmlSerializer>. Use `MaxDepth` para atenuar essa ameaça.

#### <a name="maxnametablecharcount"></a>MaxNameTableCharCount

Essa cota limita o tamanho do que o leitor *nametable*. O nametable contém algumas cadeias de caracteres (como namespaces e prefixos) que são encontrados ao processar um documento XML. Como essas cadeias de caracteres são armazenados em buffer na memória, defina essa cota para evitar o armazenamento em buffer excessivo quando o streaming é esperado.

#### <a name="maxstringcontentlength"></a>MaxStringContentLength

Essa cota limita o tamanho máximo da cadeia de caracteres que o leitor de XML retorna. Essa cota não limita o consumo de memória no próprio leitor de XML, mas no componente que esteja usando o leitor. Por exemplo, quando o <xref:System.Runtime.Serialization.DataContractSerializer> usa um leitor protegido com <xref:System.Xml.XmlDictionaryReaderQuotas.MaxStringContentLength%2A>, ele não desserializa as cadeias de caracteres maiores do que essa cota. Ao usar o <xref:System.Xml.XmlDictionaryReader> classe diretamente, nem todos os aspectos de métodos essa cota, mas apenas os métodos que são projetados especificamente para ler cadeias de caracteres, como o <xref:System.Xml.XmlDictionaryReader.ReadContentAsString%2A> método. O <xref:System.Xml.XmlReader.Value%2A> propriedade o leitor não é afetada por essa cota e, portanto, não deve ser usada quando a proteção fornece essa cota é necessária.

#### <a name="maxarraylength"></a>MaxArrayLength

Essa cota limita o tamanho máximo de uma matriz de primitivas que o leitor de XML retorna, inclusive matrizes de bytes. Essa cota não limita o consumo de memória no próprio leitor de XML, mas em qualquer componente que esteja usando o leitor. Por exemplo, quando o <xref:System.Runtime.Serialization.DataContractSerializer> usa um leitor protegido com <xref:System.Xml.XmlDictionaryReaderQuotas.MaxArrayLength%2A>, ele não desserializa as matrizes de bytes maiores do que essa cota. É importante definir essa cota ao tentar combinar modelos de programação em buffer e transmissão em um único contrato. Tenha em mente que, ao usar o <xref:System.Xml.XmlDictionaryReader> classe diretamente, apenas os métodos que são projetados especificamente para ler as matrizes de tamanho arbitrário de determinados tipos primitivos, como <xref:System.Xml.XmlDictionaryReader.ReadInt32Array%2A>, respeita essa cota.

## <a name="threats-specific-to-the-binary-encoding"></a>Ameaças específicas para a codificação binária

O XML binário codificação dá suporte a WCF inclui um *cadeias de caracteres de dicionário* recurso. Uma cadeia de caracteres grande pode ser codificada usando somente alguns bytes. Isso permite que os ganhos significativos de desempenho, mas apresenta novas ameaças de negação de serviço que devem ser reduzidas.

Há dois tipos de dicionários: *estáticos* e *dinâmico*. O dicionário estático é uma lista interna de cadeias de caracteres longas que podem ser representados usando um código curto na codificação binária. Esta lista de cadeias de caracteres é fixada quando o leitor é criado e não pode ser modificado. Nenhuma das cadeias de caracteres no dicionário estático que o WCF usa por padrão é grande o suficiente para oferecer uma ameaça grave de negação de serviço, embora ainda possa ser usados em um ataque de expansão do dicionário. Em cenários avançados em que você fornecer seu próprio dicionário estático, tenha cuidado ao introduzir cadeias de caracteres de dicionário grandes.

O recurso de dicionários dinâmico permite que as mensagens definir suas próprias cadeias de caracteres e associá-los a códigos curtos. Esses mapeamentos de código a cadeia de caracteres são mantidos na memória durante a sessão de comunicação inteira, de modo que as mensagens subsequentes não precisará reenviar as cadeias de caracteres e podem utilizar códigos que já estão definidos. Essas cadeias de caracteres podem ser de comprimento arbitrário e, portanto, representem uma ameaça mais grave que aquelas no dicionário estático.

O primeiro risco deve ser reduzido é a possibilidade do dicionário dinâmico se tornar muito grande (tabela de mapeamento de código a cadeia de caracteres). Esse dicionário pode ser expandido ao longo de várias mensagens e então o `MaxReceivedMessageSize` cota não oferece nenhuma proteção porque ele se aplica somente a cada mensagem separadamente. Portanto, um separado <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement.MaxSessionSize%2A> propriedade existir no <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement> que limita o tamanho do dicionário.

Ao contrário da maioria das outras cotas, essa cota se aplica também ao escrever mensagens. Se ele for excedido durante a leitura de uma mensagem, o `QuotaExceededException` é lançada como de costume. Se ele for excedido durante a gravação de uma mensagem, qualquer cadeia de caracteres que fazem com que a cota seja excedido é gravadas como-está, sem usar o recurso dinâmico dicionários.

### <a name="dictionary-expansion-threats"></a>Ameaças de expansão de dicionário

Uma classe significativa de ataques de binário específico provém da expansão do dicionário. Uma pequena mensagem em formato binário pode transformar em uma mensagem muito grande em formulário textual totalmente expandido se ele faz uso extensivo do recurso de dicionários de cadeia de caracteres. O fator de expansão para cadeias de caracteres de dicionário dinâmico é limitado pelo <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement.MaxSessionSize%2A> cota, porque nenhuma cadeia de caracteres de dicionário dinâmico excede o tamanho máximo do dicionário inteiro.

O <xref:System.Xml.XmlDictionaryReaderQuotas.MaxNameTableCharCount%2A>, `MaxStringContentLength`, e `MaxArrayLength` propriedades apenas limitam o consumo de memória. Eles normalmente não são necessários para minimizar essas ameaças no uso de não transmitidos por Streaming, porque o uso de memória já é limitado pelo `MaxReceivedMessageSize`. No entanto, `MaxReceivedMessageSize` contagens de bytes de expansão de pré-lançamento. Quando a codificação binária está em uso, consumo de memória potencialmente pode ir além `MaxReceivedMessageSize`limitada apenas por um fator de <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement.MaxSessionSize%2A>. Por esse motivo, é importante sempre definir todas as cotas do leitor (especialmente <xref:System.Xml.XmlDictionaryReaderQuotas.MaxStringContentLength%2A>) ao usar a codificação binária.

Ao usar a codificação binária junto com o <xref:System.Runtime.Serialization.DataContractSerializer>, o `IExtensibleDataObject` interface pode ser usado indevidamente para montar um ataque de expansão do dicionário. Essencialmente, essa interface fornece armazenamento ilimitado para dados arbitrários que não não uma parte do contrato. Se as cotas não podem ser definidas como baixas o suficiente, de modo que `MaxSessionSize` multiplicado por `MaxReceivedMessageSize` não representar um problema, desabilite o `IExtensibleDataObject` ao usar a codificação binária de recursos. Defina a `IgnoreExtensionDataObject` propriedade para `true` no `ServiceBehaviorAttribute` atributo. Como alternativa, não implemente o `IExtensibleDataObject` interface. Para obter mais informações, consulte [Contratos de dados compatíveis por encaminhamento](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md).

### <a name="quotas-summary"></a>Resumo de cotas

A tabela a seguir resume as orientações sobre as cotas.

|Condição|Cotas importantes para definir|
|---------------|-----------------------------|
|Sem streaming ou transmissão de mensagens pequenas, texto ou codificação de MTOM|`MaxReceivedMessageSize`, `MaxBytesPerRead` e `MaxDepth`|
|Sem streaming ou transmissão de mensagens pequenas, binárias de codificação|`MaxReceivedMessageSize`, `MaxSessionSize`e todos os `ReaderQuotas`|
|Transmissão de mensagens grandes, texto ou codificação de MTOM|`MaxBufferSize` e tudo `ReaderQuotas`|
|Streaming mensagens grandes, binárias de codificação|`MaxBufferSize`, `MaxSessionSize`e todos os `ReaderQuotas`|

- Tempos limite no nível de transporte devem sempre ser definidos e nunca usem leituras/gravações síncronas quando streaming estiver em uso, independentemente se você estiver transmitindo mensagens grandes ou pequenas.

- Em caso de dúvida sobre uma cota, defina-o como um valor seguro em vez de deixá-la aberta.

## <a name="preventing-malicious-code-execution"></a>Impedindo a execução de código mal-intencionado

As seguintes classes gerais de ameaças podem executar o código e ter efeitos indesejados:

- O desserializador carrega um tipo não seguro, mal-intencionado ou sensível à segurança.

- Uma mensagem de entrada faz com que o desserializador construir uma instância de um tipo normalmente segura de tal forma que ele tem consequências não intencionais.

As seções a seguir discutem essas classes de ameaças ainda mais.

## <a name="datacontractserializer"></a>DataContractSerializer

(Para obter informações de segurança sobre o <xref:System.Xml.Serialization.XmlSerializer>, consulte a documentação relevante.) O modelo de segurança para o <xref:System.Xml.Serialization.XmlSerializer> é semelhante do <xref:System.Runtime.Serialization.DataContractSerializer>e diferem principalmente em detalhes. Por exemplo, o <xref:System.Xml.Serialization.XmlIncludeAttribute> atributo é usado para inclusão de tipo em vez do <xref:System.Runtime.Serialization.KnownTypeAttribute> atributo. No entanto, algumas ameaças exclusivas para o <xref:System.Xml.Serialization.XmlSerializer> discutidos posteriormente neste tópico.

### <a name="preventing-unintended-types-from-being-loaded"></a>Impedir que os tipos não intencionais que está sendo carregado

Carregamento de tipos não intencionais pode ter consequências importantes, se o tipo é mal-intencionado ou apenas tem efeitos colaterais de sensível à segurança. Um tipo pode conter vulnerabilidades de segurança explorável, realizar ações confidenciais de segurança em seu construtor ou o construtor de classe, têm um grande volume de memória que facilita os ataques de negação de serviço, ou pode lançar exceções não recuperável. Tipos podem ter construtores de classe que são executados assim que o tipo é carregado e antes de todas as instâncias são criadas. Por esses motivos, é importante controlar o conjunto de tipos que o desserializador pode ser carregado.

O <xref:System.Runtime.Serialization.DataContractSerializer> desserializa em uma forma acoplada. Ele nunca lê common language runtime (CLR) nomes de tipo e assembly dos dados de entrada. Isso é semelhante ao comportamento do <xref:System.Xml.Serialization.XmlSerializer>, mas é diferente do comportamento do <xref:System.Runtime.Serialization.NetDataContractSerializer>, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>e o <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>. Um acoplamento apresenta um grau de segurança, pois o invasor remoto não pode indicar um tipo arbitrário para carregar apenas por esse tipo na mensagem de nomenclatura.

O <xref:System.Runtime.Serialization.DataContractSerializer> sempre tem permissão para carregar um tipo que está atualmente previsto acordo com o contrato. Por exemplo, se um contrato de dados tem um membro de dados do tipo `Customer`, o <xref:System.Runtime.Serialization.DataContractSerializer> tem permissão para carregar o `Customer` tipo quando ele desserializa este membro de dados.

Além disso, o <xref:System.Runtime.Serialization.DataContractSerializer> oferece suporte a polimorfismo. Um membro de dados pode ser declarado como <xref:System.Object>, mas os dados de entrada podem conter um `Customer` instância. Isso é possível somente se o `Customer` tipo foi feito "conhecido" para o desserializador por meio de um desses mecanismos:

- <xref:System.Runtime.Serialization.KnownTypeAttribute> atributo aplicado a um tipo.

- `KnownTypeAttribute` especificando um método que retorna uma lista de tipos de atributo.

- `ServiceKnownTypeAttribute` atributo.

- O `KnownTypes` seção de configuração.

- Uma lista de tipos conhecidos passados explicitamente para o <xref:System.Runtime.Serialization.DataContractSerializer> durante a construção, se usar o serializador diretamente.

Cada um desses mecanismos aumenta a área de superfície com a introdução de mais tipos que o desserializador pode carregar. Controle cada um desses mecanismos para garantir que nenhum tipo mal-intencionado ou não intencional é adicionado à lista de tipos conhecidos.

Depois que um tipo conhecido está no escopo, ele pode ser carregado a qualquer momento e instâncias do tipo podem ser criadas, mesmo se o contrato proíbe o uso efetivo. Por exemplo, suponha que o tipo "MyDangerousType" é adicionado à lista de tipos conhecidos usando um dos mecanismos acima. Isso significa que:

- `MyDangerousType` é carregado e seu construtor de classe seja executado.

- Mesmo quando a desserialização de um contrato de dados com um membro de dados de cadeia de caracteres, uma mensagem mal-intencionada ainda pode causar uma instância de `MyDangerousType` para criar. O código no `MyDangerousType`, como setters de propriedade podem ser executadas. Depois que isso for feito, o desserializador tenta atribuir essa instância para o membro de dados de cadeia de caracteres e falhar com uma exceção.

Ao escrever um método que retorna uma lista de tipos conhecidos, ou ao passar uma lista diretamente para o <xref:System.Runtime.Serialization.DataContractSerializer> construtor, certifique-se de que o código que prepara a lista é seguro e funciona apenas em dados confiáveis.

Se especificar os tipos conhecidos na configuração, certifique-se de que o arquivo de configuração é seguro. Sempre use nomes fortes na configuração (especificando a chave pública do assembly assinado em que reside o tipo), mas não especificar a versão do tipo a ser carregado. O carregador do tipo escolhe automaticamente a versão mais recente, se possível. Se você especificar uma versão específica na configuração, você corre o risco a seguir: Um tipo pode ter uma vulnerabilidade de segurança que pode ser corrigida em uma versão futura, mas ainda é a versão vulnerável carregado porque ela é explicitamente especificada na configuração.

Número excessivo de tipos conhecidos tem outra consequência: O <xref:System.Runtime.Serialization.DataContractSerializer> cria um cache de código de serialização/desserialização no domínio do aplicativo, com uma entrada para cada tipo, ele deve serializar e desserializar. Esse cache nunca é limpo, desde que o domínio do aplicativo está em execução. Portanto, um invasor que está ciente de que um aplicativo usa muitos tipos conhecidos pode fazer com que a desserialização de todos esses tipos, fazendo com que o cache consumir uma desproporcionalmente grande quantidade de memória.

### <a name="preventing-types-from-being-in-an-unintended-state"></a>Impedir que os tipos de estar em um estado não pretendido

Um tipo pode ter restrições de consistência interno que devem ser impostas. Deve-se ter cuidado para evitar a interrupção essas restrições durante a desserialização.

O exemplo a seguir de um tipo representa o estado de uma câmara de vácuo de uma nave espacial e impõe a restrição que interna e as portas externas não podem ser abertas ao mesmo tempo.

[!code-csharp[DataContractAttribute#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/datacontractattribute/cs/overview.cs#3)]
[!code-vb[DataContractAttribute#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/datacontractattribute/vb/overview.vb#3)]

Um invasor pode enviar uma mensagem mal-intencionada, como este, contornar as restrições e Obtendo o objeto em um estado inválido, que pode ter consequências não intencionais e imprevisíveis.

```xml
<SpaceStationAirlock>
    <innerDoorOpen>true</innerDoorOpen>
    <outerDoorOpen>true</outerDoorOpen>
</SpaceStationAirlock>
```

Essa situação pode ser evitada com esteja ciente de que os seguintes pontos:

- Quando o <xref:System.Runtime.Serialization.DataContractSerializer> desserializa a maioria das classes, construtores não são executados. Portanto, não confie em qualquer gerenciamento de estado feito no construtor.

- Use retornos de chamada para garantir que o objeto está em um estado válido. O retorno de chamada é marcado com o <xref:System.Runtime.Serialization.OnDeserializedAttribute> atributo é especialmente útil porque ele é executado após a desserialização é concluída e tem a oportunidade de examinar e corrigir o estado geral. Para obter mais informações, consulte [retornos de chamada de serialização tolerantes à versão](../../../../docs/framework/wcf/feature-details/version-tolerant-serialization-callbacks.md).

- Não crie tipos de contrato de dados para contar com uma ordem específica na qual propriedade setters devem ser chamados.

- Tenha cuidado ao usar tipos herdados marcados com o <xref:System.SerializableAttribute> atributo. Muitos deles foram projetados para funcionar com [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] comunicação remota para uso com dados confiáveis apenas. Os tipos existentes marcados com esse atributo não podem ter sido projetados com segurança de estado em mente.

- Não confie na <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> propriedade do <xref:System.Runtime.Serialization.DataMemberAttribute> atributo para garantir a presença de dados que diz respeito a segurança de estado. Dados podem ser sempre `null`, `zero`, ou `invalid`.

- Nunca confiança um grafo de objeto desserializado de uma fonte de dados não confiáveis sem validá-lo primeiro. Cada objeto individual pode estar em um estado consistente, mas o grafo de objeto que não pode ser um inteiro. Além disso, mesmo se o modo de preservação do gráfico de objeto for desabilitado, o grafo desserializado pode ter várias referências ao mesmo objeto ou ter referências circulares. Para obter mais informações, consulte [serialização e desserialização](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md).

### <a name="using-the-netdatacontractserializer-securely"></a>Usando o NetDataContractSerializer com segurança

O <xref:System.Runtime.Serialization.NetDataContractSerializer> é um mecanismo de serialização que usa tipos de acoplamento rígido. Isso é semelhante a <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> e o <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>. Ou seja, ele determina que tipo de instanciar lendo o [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] nome do assembly e tipo de dados de entrada. Embora seja uma parte do WCF, não há nenhuma maneira fornecida de conectar esse mecanismo de serialização; código personalizado deve ser escrito. O `NetDataContractSerializer` é fornecido principalmente para facilitar a migração do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] comunicação remota para o WCF. Para obter mais informações, consulte a seção relevante [serialização e desserialização](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md).

Porque a mensagem em si pode indicar qualquer tipo pode ser carregado, o <xref:System.Runtime.Serialization.NetDataContractSerializer> mecanismo é inerentemente inseguro e deve ser usado somente com dados confiáveis. É possível torná-lo seguro, escrevendo um associador de tipo seguro, limitando o tipo que permite que apenas tipos seguros de carga (usando o <xref:System.Runtime.Serialization.NetDataContractSerializer.Binder%2A> propriedade).

Mesmo quando usados com dados confiáveis, os dados de entrada podem especificar o tipo para carregar, especialmente se o <xref:System.Runtime.Serialization.NetDataContractSerializer.AssemblyFormat%2A> estiver definida como <xref:System.Runtime.Serialization.Formatters.FormatterAssemblyStyle.Simple>. Qualquer pessoa com acesso ao diretório do aplicativo ou ao cache de assembly global pode substituir um tipo mal-intencionados no lugar do que deveria ser carregado. Sempre verifique se a segurança do diretório do aplicativo e do cache de assembly global, corretamente definindo permissões.

Em geral, se você permitir o acesso do código parcialmente confiável para seus `NetDataContractSerializer` da instância ou outra forma controla o seletor substituto (<xref:System.Runtime.Serialization.ISurrogateSelector>) ou o associador de serialização (<xref:System.Runtime.Serialization.SerializationBinder>), o código pode exercer um grande controle sobre o processo de serialização/desserialização. Por exemplo, ele pode injetar tipos arbitrários, levar à divulgação de informações, violar o grafo de objeto resultante ou os dados serializados ou estouro resultante fluxo serializado.

Outra preocupação de segurança com o `NetDataContractSerializer` é uma negação de serviço, não uma ameaça de execução de código mal-intencionado. Ao usar o `NetDataContractSerializer`, sempre defina o <xref:System.Runtime.Serialization.NetDataContractSerializer.MaxItemsInObjectGraph%2A> cota como um valor seguro. É fácil construir uma pequena mensagem mal-intencionada que aloca uma matriz de objetos cujo tamanho é limitado apenas por essa cota.

### <a name="xmlserializer-specific-threats"></a>Ameaças específicas de XmlSerializer

O <xref:System.Xml.Serialization.XmlSerializer> modelo de segurança é semelhante do <xref:System.Runtime.Serialization.DataContractSerializer>. Algumas ameaças, no entanto, são exclusivas para o <xref:System.Xml.Serialization.XmlSerializer>.

O <xref:System.Xml.Serialization.XmlSerializer> gera *assemblies de serialização* em tempo de execução que contêm código que realmente serializa e desserializa; esses assemblies são criados em um diretório de arquivos temporários. Se algum outro processo ou usuário tem direitos de acesso a esse diretório, elas podem substituir o código de serialização/desserialização com um código arbitrário. O <xref:System.Xml.Serialization.XmlSerializer> executa esse código usando seu contexto de segurança, em vez do código de serialização/desserialização. Verifique se que as permissões estão definidas corretamente no diretório de arquivos temporários para evitar que isso aconteça.

O <xref:System.Xml.Serialization.XmlSerializer> também tem um modo em que ele usa os assemblies de serialização pré-gerado em vez de gerá-las em tempo de execução. Esse modo é disparado sempre que o <xref:System.Xml.Serialization.XmlSerializer> pode encontrar um assembly de serialização adequado. O <xref:System.Xml.Serialization.XmlSerializer> verificações ou não o assembly de serialização foi assinado pela mesma chave que foi usado para assinar o assembly que contém os tipos que está sendo serializados. Isso oferece proteção contra assemblies maliciosos sendo disfarçados como assemblies de serialização. No entanto, se o assembly que contém seus tipos serializáveis não estiver assinado, o <xref:System.Xml.Serialization.XmlSerializer> não é possível executar essa verificação e usa qualquer assembly com o nome correto. Isso possibilita executar código mal-intencionado. Sempre assinar os assemblies que contêm seus tipos serializáveis ou controlar rigorosamente o acesso ao diretório do seu aplicativo e o cache de assembly global para evitar a introdução de assemblies maliciosos.

O <xref:System.Xml.Serialization.XmlSerializer> podem estar sujeitos a um ataque de negação de serviço. O <xref:System.Xml.Serialization.XmlSerializer> não tem um `MaxItemsInObjectGraph` cota (como estão disponível no <xref:System.Runtime.Serialization.DataContractSerializer>). Portanto, ela desserializa uma quantidade arbitrária de objetos, limitada somente pelo tamanho da mensagem.

### <a name="partial-trust-threats"></a>Ameaças de confiança parcial

Observe as seguintes preocupações sobre ameaças relacionadas ao código em execução com confiança parcial. Essas ameaças incluem código mal-intencionado parcialmente confiável, bem como código mal-intencionado parcialmente confiável em combinação com outros cenários de ataque (por exemplo, código parcialmente confiável que constrói uma cadeia de caracteres específica e, em seguida, desserializá-los).

- Ao usar quaisquer componentes de serialização, nunca Declare qualquer permissões antes de tal uso, mesmo que o cenário de serialização toda está dentro do escopo de sua declaração, e você não está lidando com os dados não confiáveis ou objetos. Tal uso pode levar a vulnerabilidades de segurança.

- Em casos em que o código parcialmente confiável tem controle sobre o processo de serialização, por meio de pontos de extensibilidade (substitutos), os tipos que está sendo serializados, ou por outros meios, o código parcialmente confiável pode fazer com que o serializador a ser uma grande quantidade de saída dados em fluxo serializado, o que pode causar negação de serviço (DoS) para o destinatário do fluxo. Se você estiver serializando destinados a um destino que é sensível a ameaças de dados, não serializar os tipos de confiança parcial ou caso contrário, permita a serialização de controle do código parcialmente confiável.

- Se você permitir acesso a código parcialmente confiável para seus <xref:System.Runtime.Serialization.DataContractSerializer> da instância ou outra forma controla a [substitutos de contrato de dados](../../../../docs/framework/wcf/extending/data-contract-surrogates.md), ele pode exercer uma grande quantidade de controle sobre o processo de serialização/desserialização. Por exemplo, ele pode injetar tipos arbitrários, levar à divulgação de informações, violar o grafo de objeto resultante ou os dados serializados ou estouro resultante fluxo serializado. Equivalente a <xref:System.Runtime.Serialization.NetDataContractSerializer> ameaça é descrita na seção "Usando o NetDataContractSerializer com segurança".

- Se o <xref:System.Runtime.Serialization.DataContractAttribute> atributo é aplicado a um tipo (ou o tipo é marcado como <xref:System.SerializableAttribute> , mas não é <xref:System.Runtime.Serialization.ISerializable>), o desserializador pode criar uma instância desse tipo, mesmo que todos os construtores não públicos ou protegidos por demanda.

- Nunca confie o resultado da desserialização, a menos que os dados a ser desserializado são confiáveis e você tiver certeza de que todos os tipos conhecidos são tipos que você confia. Observe que tipos conhecidos não são carregados do arquivo de configuração de aplicativo, (mas são carregados do arquivo de configuração do computador) quando em execução em confiança parcial.

- Se você passar um <xref:System.Runtime.Serialization.DataContractSerializer> instância com um substituto adicionado ao código parcialmente confiável, o código pode alterar quaisquer configurações modificáveis que substituto.

- Para um objeto desserializado, se o leitor de XML (ou os dados nele) vem do código parcialmente confiável, tratar o objeto desserializado resultante como dados não confiáveis.

- O fato de que o <xref:System.Runtime.Serialization.ExtensionDataObject> não público do tipo tem membros não significa que os dados dentro dele são seguros. Por exemplo, se você desserializar a partir de uma fonte de dados com privilégios em um objeto no qual residem o alguns dados, mão, em seguida, esse objeto para código parcialmente confiável, o código parcialmente confiável pode ler os dados no `ExtensionDataObject` ao serializar o objeto. Considere a configuração <xref:System.Runtime.Serialization.DataContractSerializer.IgnoreExtensionDataObject%2A> para `true` quando a desserialização de uma fonte de dados com privilégios em um objeto que é posterior passado para código parcialmente confiável.

- <xref:System.Runtime.Serialization.DataContractSerializer> e <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> dão suporte à serialização de membros particulares, protegidos, internos e públicos em confiança total. No entanto, em confiança parcial, somente os membros públicos podem ser serializados. Um <xref:System.Security.SecurityException> será lançada se um aplicativo tenta serializar um membro não público.

    Para permitir que internos ou membros internos protegidos a ser serializado em confiança parcial, use o <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atributo do assembly. Esse atributo permite que um assembly declarar que seus membros internos são visíveis para algum outro assembly. Nesse caso, um assembly que quer que seus membros internos serializados declara que seus membros internos são visíveis para Serialization.

    A vantagem dessa abordagem é que ele não requer um caminho de geração de código com privilégios elevados.

    Ao mesmo tempo, há duas grandes desvantagens.

    A primeira desvantagem é que a propriedade de aceitação do <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atributo é todo o assembly. Ou seja, você não pode especificar que somente uma determinada classe pode ter seus membros internos serializados. É claro, você ainda pode optar para não serializar um membro interno específico, simplesmente não adicionando um <xref:System.Runtime.Serialization.DataMemberAttribute> a esse membro de atributo. Da mesma forma, um desenvolvedor também pode optar por tornar um membro interno em vez de particular ou protegido com preocupações de visibilidade pequena.

    A segunda desvantagem é que ele ainda não suporta a membros particulares ou protegidos.

    Para ilustrar o uso do <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> de atributo em confiança parcial, considere o seguinte programa:

    [!code-csharp[CDF_WCF_SecurityConsiderationsForData#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/cdf_wcf_securityconsiderationsfordata/cs/program.cs#1)]

    No exemplo acima, `PermissionsHelper.InternetZone` corresponde à <xref:System.Security.PermissionSet> para confiança parcial. Agora, sem a <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atributo, o aplicativo falhará, gerando um <xref:System.Security.SecurityException> indicando que os membros não públicos não podem ser serializados em confiança parcial.

    No entanto, se adicionarmos a seguinte linha ao arquivo de origem, o programa é executado com êxito.

    [!code-csharp[CDF_WCF_SecurityConsiderationsForData#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/cdf_wcf_securityconsiderationsfordata/cs/program.cs#2)]

## <a name="other-state-management-concerns"></a>Outras questões de gerenciamento de estado

Algumas outras preocupações sobre o gerenciamento de estado do objeto valem a pena mencionar:

- Ao usar o modelo de programação baseado em fluxo com um transporte de streaming, o processamento da mensagem ocorre conforme a mensagem chega. O remetente da mensagem pode anular a operação de envio no meio do fluxo, deixando seu código em um estado imprevisível se mais conteúdo era esperado. Em geral, não confie no fluxo que está sendo concluída e não executam qualquer trabalho em uma operação baseada em fluxo que não pode ser revertida, novamente, caso o fluxo será anulado. Isso também se aplica à situação em que uma mensagem pode estar malformada após o corpo de streaming (por exemplo, ela pode estar faltando uma marca de fim para o envelope SOAP ou ter um corpo de mensagem segundo).

- Usando o `IExtensibleDataObject` recurso pode fazer com que dados confidenciais a ser emitido. Se você está aceitando dados de uma fonte não confiável em contratos de dados com `IExtensibleObjectData` e posteriormente emitir novamente-lo em um canal seguro no qual as mensagens são assinadas, é potencialmente atestar dados que você não sabe nada sobre. Além disso, o estado geral que você está enviando pode ser inválido, se você considera as partes conhecidas e desconhecidas de dados. Evitar essa situação, qualquer um dos seletivamente definindo a propriedade de extensão de dados como `null` ou ao desabilitar seletivamente a `IExtensibleObjectData` recurso.

## <a name="schema-import"></a>Importação de esquema

Normalmente, o processo de importação de esquema para gerar tipos ocorre somente em tempo de design, por exemplo, ao usar o [ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) em um serviço Web para gerar uma classe de cliente. No entanto, em cenários mais avançados, você pode processar um esquema em tempo de execução. Lembre-se de que isso pode expor você quanto a riscos de negação de serviço. Algum esquema pode levar muito tempo para ser importado. Nunca use o <xref:System.Xml.Serialization.XmlSerializer> componente de importação de esquema em tais cenários, se os esquemas, possivelmente, são provenientes de uma fonte não confiável.

## <a name="threats-specific-to-aspnet-ajax-integration"></a>Ameaças específicas para a integração do AJAX ASP.NET

Quando o usuário implementa <xref:System.ServiceModel.Description.WebScriptEnablingBehavior> ou <xref:System.ServiceModel.Description.WebHttpBehavior>, WCF expõe um ponto de extremidade que pode aceitar mensagens XML e JSON. No entanto, há apenas um conjunto de cotas do leitor, usado pelo leitor de XML e o leitor JSON. Algumas configurações de cota podem ser apropriadas para um leitor, mas muito grande para o outro.

Ao implementar `WebScriptEnablingBehavior`, o usuário tem a opção de expor um proxy JavaScript no ponto de extremidade. Os seguintes problemas de segurança devem ser considerados:

- Informações sobre o serviço (nomes de operação, nomes de parâmetro e assim por diante) podem ser obtidas por meio do exame proxy JavaScript.

- Ao usar o ponto de extremidade do JavaScript, informações confidenciais e privadas podem ser retidas no cliente de cache do navegador da Web.

## <a name="a-note-on-components"></a>Uma observação sobre componentes

O WCF é um sistema flexível e personalizável. A maioria do conteúdo deste tópico se concentrar em cenários mais comuns de uso do WCF. No entanto, é possível compor o WCF fornece de muitas maneiras diferentes de componentes. É importante entender as implicações de segurança do uso de cada componente. Em particular:

- Quando você deve usar leitores XML, use os leitores a <xref:System.Xml.XmlDictionaryReader> classe fornece em vez de quaisquer outros leitores. Leitores de seguros são criados usando <xref:System.Xml.XmlDictionaryReader.CreateTextReader%2A>, <xref:System.Xml.XmlDictionaryReader.CreateBinaryReader%2A>, ou <xref:System.Xml.XmlDictionaryReader.CreateMtomReader%2A> métodos. Não use o <xref:System.Xml.XmlReader.Create%2A> método. Sempre configure os leitores com cotas seguras. Os mecanismos de serialização no WCF são seguros somente quando usada com leitores XML seguros do WCF.

- Ao usar o <xref:System.Runtime.Serialization.DataContractSerializer> para desserializar dados potencialmente não confiáveis, sempre defina o <xref:System.Runtime.Serialization.DataContractSerializer.MaxItemsInObjectGraph%2A> propriedade.

- Ao criar uma mensagem, defina as `maxSizeOfHeaders` parâmetro se `MaxReceivedMessageSize` não oferece proteção suficiente.

- Durante a criação de um codificador, sempre configurar as cotas relevantes, como `MaxSessionSize` e `MaxBufferSize`.

- Ao usar um filtro de mensagem de XPath, defina o <xref:System.ServiceModel.Dispatcher.XPathMessageFilter.NodeQuota%2A> para limitar a quantidade de nós XML que visita o filtro. Não use expressões XPath que pode levar muito tempo para ser sem visitar o número de nós de computação.

- Em geral, ao usar qualquer componente que aceita uma cota, compreender suas implicações de segurança e defini-lo como um valor seguro.

## <a name="see-also"></a>Consulte também

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Xml.XmlDictionaryReader>
- <xref:System.Xml.Serialization.XmlSerializer>
- [Tipos conhecidos de contrato de dados](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
