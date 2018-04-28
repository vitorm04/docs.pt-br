---
title: Usando a classe de mensagens
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: d1d62bfb-2aa3-4170-b6f8-c93d3afdbbed
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c63a0a88997a1c35b24562bcca3e0fdb40ebfd41
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2018
---
# <a name="using-the-message-class"></a>Usando a classe de mensagens
O <xref:System.ServiceModel.Channels.Message> classe é fundamental para [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]. Toda a comunicação entre clientes e serviços, por fim, resulta em <xref:System.ServiceModel.Channels.Message> instâncias que estão sendo enviadas e recebidas.  
  
 Você normalmente não deve interagir com o <xref:System.ServiceModel.Channels.Message> classe diretamente. Em vez disso, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] construções de modelo de serviço, como dados de contratos, contratos de mensagem e contratos de operação, são usados para descrever as mensagens de entrada e saídas. No entanto, em alguns cenários avançados de você pode programar usando o <xref:System.ServiceModel.Channels.Message> classe diretamente. Por exemplo, talvez você queira usar o <xref:System.ServiceModel.Channels.Message> classe:  
  
-   Quando você precisa de uma maneira alternativa de criação de conteúdo da mensagem de saída (por exemplo, criar uma mensagem diretamente de um arquivo no disco), em vez de serialização [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] objetos.  
  
-   Quando você precisa de uma maneira alternativa de usar o conteúdo da mensagem de entrada (por exemplo, quando você deseja aplicar uma transformação XSLT para o conteúdo XML bruto) em vez de desserialização em [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] objetos.  
  
-   Quando você precisa lidar com mensagens de maneira geral, independentemente do conteúdo da mensagem (por exemplo, quando o roteamento ou o encaminhamento de mensagens ao compilar um roteador, o balanceador de carga ou publicar-inscrever-se o sistema).  
  
 Antes de usar o <xref:System.ServiceModel.Channels.Message> classe, familiarize-se com o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] arquitetura de transferência de dados [visão geral de arquitetura de transferência de dados](../../../../docs/framework/wcf/feature-details/data-transfer-architectural-overview.md).  
  
 Um <xref:System.ServiceModel.Channels.Message> é um contêiner de finalidade geral para os dados, mas seu design segue rigorosamente o design de uma mensagem no protocolo SOAP. Assim como em SOAP, uma mensagem tem um corpo de mensagem e cabeçalhos. O corpo da mensagem contém os dados de carga real, enquanto os cabeçalhos contêm os contêineres de dados nomeado adicionais. As regras para ler e gravar o corpo e os cabeçalhos são diferentes, por exemplo, os cabeçalhos são sempre armazenados em buffer na memória e podem ser acessados em qualquer ordem qualquer número de vezes, enquanto o corpo pode ser lido apenas uma vez e pode ser transmitido. Normalmente, ao usar o SOAP, o corpo da mensagem é mapeado para o corpo SOAP e os cabeçalhos de mensagem são mapeados para os cabeçalhos SOAP.  
  
## <a name="using-the-message-class-in-operations"></a>Usando a classe de mensagem em operações  
 Você pode usar o <xref:System.ServiceModel.Channels.Message> classe como um parâmetro de entrada de uma operação, o valor de retorno de uma operação, ou ambos. Se <xref:System.ServiceModel.Channels.Message> é usado em qualquer lugar em uma operação, as seguintes restrições se aplicam:  
  
-   A operação não pode ter qualquer `out` ou `ref` parâmetros.  
  
-   Não é possível haver mais de um `input` parâmetro. Se o parâmetro estiver presente, ele deve ser mensagem ou um tipo de contrato de mensagem.  
  
-   O tipo de retorno deve ser `void`, `Message`, ou uma tipo de contrato de mensagem.  
  
 O exemplo de código a seguir contém um contrato de operação válida.  
  
 [!code-csharp[C_UsingTheMessageClass#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#1)]
 [!code-vb[C_UsingTheMessageClass#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#1)]  
  
## <a name="creating-basic-messages"></a>Criando mensagens básicas  
 O <xref:System.ServiceModel.Channels.Message> classe fornece estático `CreateMessage` métodos de fábrica que você pode usar para criar as mensagens básicas.  
  
 Todos os `CreateMessage` sobrecargas usam um parâmetro de versão do tipo <xref:System.ServiceModel.Channels.MessageVersion> que indica as versões SOAP e WS-Addressing a ser usado para a mensagem. Se você quiser usar as mesmas versões de protocolo da mensagem de entrada, você pode usar o <xref:System.ServiceModel.OperationContext.IncomingMessageVersion%2A> propriedade o <xref:System.ServiceModel.OperationContext> instância obtido o <xref:System.ServiceModel.OperationContext.Current%2A> propriedade. A maioria dos `CreateMessage` sobrecargas também tem um parâmetro de cadeia de caracteres que indica a ação a ser usado para a mensagem SOAP. Versão pode ser definida como `None` para desabilitar a geração de envelope SOAP, a mensagem consiste apenas o corpo.  
  
## <a name="creating-messages-from-objects"></a>Criando mensagens de objetos  
 O mais básico `CreateMessage` sobrecarga que usa apenas uma versão e uma ação cria uma mensagem com um corpo vazio. Entra em outra sobrecarga adicional <xref:System.Object> parâmetro; isso cria uma mensagem cujo corpo é a representação serializada do objeto especificado. Use o <xref:System.Runtime.Serialization.DataContractSerializer> com configurações padrão para serialização. Se você deseja usar um serializador diferente, ou o `DataContractSerializer` configurado de forma diferente, use o `CreateMessage` sobrecarga que também usa um `XmlObjectSerializer` parâmetro.  
  
 Por exemplo, para retornar um objeto em uma mensagem, você pode usar o código a seguir.  
  
 [!code-csharp[C_UsingTheMessageClass#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#2)]
 [!code-vb[C_UsingTheMessageClass#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#2)]  
  
## <a name="creating-messages-from-xml-readers"></a>Criando mensagens de leitores XML  
 Há `CreateMessage` sobrecargas que usam um <xref:System.Xml.XmlReader> ou um <xref:System.Xml.XmlDictionaryReader> para o corpo em vez de um objeto. Nesse caso, o corpo da mensagem contém o XML resultante da leitura do leitor de XML passado. Por exemplo, o código a seguir retorna uma mensagem com o corpo de conteúdo lido de um arquivo XML.  
  
 [!code-csharp[C_UsingTheMessageClass#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#3)]
 [!code-vb[C_UsingTheMessageClass#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#3)]  
  
 Além disso, há `CreateMessage` sobrecargas que usam um <xref:System.Xml.XmlReader> ou um <xref:System.Xml.XmlDictionaryReader> que representa a mensagem inteira e não apenas o corpo. Essas sobrecargas também usam um número inteiro `maxSizeOfHeaders` parâmetro. Cabeçalhos sempre são armazenados em buffer na memória assim que a mensagem for criada, e esse parâmetro limita a quantidade de buffer ocorre. É importante definir esse parâmetro como um valor de seguro se o XML é proveniente de uma fonte não confiável para reduzir a possibilidade de um ataque de negação de serviço. As versões SOAP e WS-Addressing da mensagem que representa o leitor de XML devem corresponder as versões indicadas usando o parâmetro de versão.  
  
## <a name="creating-messages-with-bodywriter"></a>Criando mensagens com BodyWriter  
 Um `CreateMessage` sobrecarregar leva um `BodyWriter` instância para descrever o corpo da mensagem. A `BodyWriter` é uma classe abstrata que pode ser derivada para personalizar como os corpos de mensagens são criados. Você pode criar seus próprios `BodyWriter` derivado da classe para descrever os corpos de mensagens de forma personalizada. Você deve substituir o `BodyWriter.OnWriteBodyContents` método que utiliza um <xref:System.Xml.XmlDictionaryWriter>; esse método é responsável por gravar o corpo.  
  
 Gravadores de corpo podem ser armazenados em buffer ou sem buffer (Streaming). Gravadores de buffer de corpo podem gravar seu conteúdo várias vezes, enquanto aquelas em fluxo podem gravar o conteúdo apenas uma vez. O `IsBuffered` propriedade indica se um gravador de corpo em buffer ou não. Você pode definir isso para o gravador de corpo chamando protegido `BodyWriter` construtor que usa um `isBuffered` parâmetro booliano. Gravadores de corpo suportam a criação de um gravador de buffer de corpo de um gravador de corpo não armazenado em buffer. Você pode substituir o `OnCreateBufferedCopy` método para personalizar esse processo. Por padrão, um buffer na memória que contém o XML retornado por `OnWriteBodyContents` é usado. `OnCreateBufferedCopy` leva um `maxBufferSize` parâmetro inteiro; se você substituir esse método, você não deve criar buffers maior do que esse tamanho máximo.  
  
 O `BodyWriter` classe fornece a `WriteBodyContents` e `CreateBufferedCopy` métodos, que são essencialmente fino wrappers em torno `OnWriteBodyContents` e `OnCreateBufferedCopy` métodos, respectivamente. Esses métodos fazem a verificação de estado para garantir que um gravador de corpo não armazenado em buffer não é acessado mais de uma vez. Esses métodos são chamados diretamente somente durante a criação personalizada `Message` derivado classes com base em `BodyWriters`.  
  
## <a name="creating-fault-messages"></a>Mensagens de falha de criação  
 Você pode usar certos `CreateMessage` mensagens de falha de sobrecargas para criar o SOAP. O mais básico desses leva um <xref:System.ServiceModel.Channels.MessageFault> objeto que descreve a falha. Outras sobrecargas são fornecidas para conveniência. O primeiro como sobrecarga que usa um `FaultCode` e uma cadeia de caracteres do motivo e cria um `MessageFault` usando `MessageFault.CreateFault` usando essas informações. A outra sobrecarga utiliza um objeto de detalhe e também transmite a `CreateFault` junto com o código de falha e o motivo. Por exemplo, a operação a seguir retorna uma falha.  
  
 [!code-csharp[C_UsingTheMessageClass#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#4)]
 [!code-vb[C_UsingTheMessageClass#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#4)]  
  
## <a name="extracting-message-body-data"></a>Extrair dados de corpo de mensagem  
 O `Message` classe oferece várias maneiras de extração de informações de seu corpo. Eles podem ser classificados nas seguintes categorias:  
  
-   Obtendo o corpo da mensagem inteira gravado simultaneamente em um gravador de XML. Isso é conhecido como *escrever uma mensagem*.  
  
-   Obtendo um leitor de XML sobre o corpo da mensagem. Isso permite acesso a mensagem corpo parte-por-parte posterior conforme necessário. Isso é conhecido como *ler uma mensagem*.  
  
-   A mensagem inteira, incluindo seu corpo pode ser copiada para um buffer de memória do <xref:System.ServiceModel.Channels.MessageBuffer> tipo. Isso é conhecido como *copiando uma mensagem*.  
  
 Você pode acessar o corpo de um `Message` apenas uma vez, independentemente de como ele é acessado. Um objeto de mensagem tem um `State` propriedade, que é definida inicialmente como criado. Os métodos de três acesso descritos na lista anterior definem o estado gravadas, leitura e copiados, respectivamente. Além disso, um `Close` método pode definir o estado fechado quando o conteúdo do corpo de mensagem não é mais necessário. O corpo da mensagem pode ser acessado apenas no estado criado e não há nenhuma maneira para retornar ao estado criado depois que o estado é alterado.  
  
## <a name="writing-messages"></a>Mensagens de gravação  
 O <xref:System.ServiceModel.Channels.Message.WriteBodyContents%28System.Xml.XmlDictionaryWriter%29> método grava o conteúdo do corpo de um determinado `Message` instância para o gravador XML especificado. O <xref:System.ServiceModel.Channels.Message.WriteBody%2A> método faz o mesmo, exceto que ele inclui o conteúdo do corpo no elemento wrapper apropriada (por exemplo, <`soap:body`>). Por fim, <xref:System.ServiceModel.Channels.Message.WriteMessage%2A> gravações limite a mensagem inteira, incluindo a quebra automática de envelope e os cabeçalhos de SOAP. Se SOAP estiver desativada (versão `MessageVersion.None`), todos os três métodos fazem a mesma coisa: gravar o conteúdo do corpo de mensagem.  
  
 Por exemplo, o código a seguir grava o corpo de uma mensagem de entrada para um arquivo.  
  
 [!code-csharp[C_UsingTheMessageClass#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#5)]
 [!code-vb[C_UsingTheMessageClass#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#5)]  
  
 Dois métodos auxiliares adicionais gravar determinadas marcas de elemento de início SOAP. Esses métodos não acessam o corpo da mensagem e portanto não alterar o estado da mensagem. Elas incluem:  
  
-   <xref:System.ServiceModel.Channels.Message.WriteStartBody%2A> grava o elemento de corpo de início, por exemplo, `<soap:Body>`.  
  
-   <xref:System.ServiceModel.Channels.Message.WriteStartEnvelope%2A> grava o elemento de envelope inicial, por exemplo, `<soap:Envelope>`.  
  
 Para gravar a extremidade correspondente marcas de elemento, chamar `WriteEndElement` no gravador de XML correspondente. Esses métodos raramente são chamados diretamente.  
  
## <a name="reading-messages"></a>Leitura de mensagens  
 A principal maneira de ler um corpo de mensagem é chamar <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A>. Você obtém um <xref:System.Xml.XmlDictionaryReader> que você pode usar para ler o corpo da mensagem. Observe que o <xref:System.ServiceModel.Channels.Message> faz a transição para o estado de leitura, assim como <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> é chamado, e não quando você usa o leitor de XML retornado.  
  
 O <xref:System.ServiceModel.Channels.Message.GetBody%2A> método também permite que você acesse o corpo da mensagem como um tipo de objeto. Internamente, esse método usa `GetReaderAtBodyContents`, e, portanto, além disso, ele mudará o estado da mensagem para o <xref:System.ServiceModel.Channels.MessageState.Read> estado (consulte a <xref:System.ServiceModel.Channels.Message.State%2A> propriedade).  
  
 É recomendável verificar o <xref:System.ServiceModel.Channels.Message.IsEmpty%2A> propriedade, nesse caso, o corpo da mensagem está vazio e <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> lança um <xref:System.InvalidOperationException>. Além disso, se for uma mensagem recebida (por exemplo, a resposta), você talvez também queira verificar <xref:System.ServiceModel.Channels.Message.IsFault%2A>, que indica se a mensagem contém uma falha.  
  
 A sobrecarga mais básica do <xref:System.ServiceModel.Channels.Message.GetBody%2A> desserializa o corpo da mensagem em uma instância de um tipo (indicado pelo parâmetro genérico) usando um <xref:System.Runtime.Serialization.DataContractSerializer> configurado com as configurações padrão e o <xref:System.Runtime.Serialization.DataContractSerializer.MaxItemsInObjectGraph%2A> cota desabilitada. Se você deseja usar um mecanismo de serialização diferentes, ou configurar o `DataContractSerializer` de forma diferente do padrão, use o <xref:System.ServiceModel.Channels.Message.GetBody%2A> sobrecarga que utiliza um <xref:System.Runtime.Serialization.XmlObjectSerializer>.  
  
 Por exemplo, o código a seguir extrai dados de um corpo de mensagem que contém um serializado `Person` do objeto e imprime o nome da pessoa.  
  
 [!code-csharp[C_UsingTheMessageClass#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#6)]
 [!code-vb[C_UsingTheMessageClass#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#6)]  
  
## <a name="copying-a-message-into-a-buffer"></a>Copiando uma mensagem em um Buffer  
 Às vezes, é necessário para acessar o corpo da mensagem mais de uma vez, por exemplo, para encaminhar a mesma mensagem para vários destinos, como parte de um sistema de assinantes do publicador. Nesse caso, é necessário para a mensagem inteira (incluindo o corpo) do buffer na memória. Você pode fazer isso chamando <xref:System.ServiceModel.Channels.Message.CreateBufferedCopy%28System.Int32%29>. Esse método aceita um parâmetro de número inteiro que representa o tamanho máximo do buffer e cria um buffer não seja maior que esse tamanho. É importante definir isso como um valor de seguro, se a mensagem é proveniente de uma fonte não confiável.  
  
 O buffer é retornado como um <xref:System.ServiceModel.Channels.MessageBuffer> instância. Você pode acessar dados no buffer de várias maneiras. A principal maneira é chamar <xref:System.ServiceModel.Channels.Message.CreateMessage%2A> criar `Message` instâncias do buffer.  
  
 Outra maneira de acessar os dados no buffer é implementar o <xref:System.Xml.XPath.IXPathNavigable> interface que o <xref:System.ServiceModel.Channels.MessageBuffer> classe implementa acessem diretamente o XML subjacente. Alguns <xref:System.ServiceModel.Channels.MessageBuffer.CreateNavigator%2A> sobrecargas permitem que você crie <xref:System.Xml.XPath> navegadores protegidos por uma cota de nó, limitando o número de nós XML que podem ser visitados. Isso ajuda a impedir ataques negação de serviço com base no tempo de processamento maior. Citação está desabilitada por padrão. Alguns `CreateNavigator` sobrecargas permitem que você especifique como o espaço em branco devem ser tratado no XML usando o <xref:System.Xml.XmlSpace> enumeração, com o padrão que está sendo `XmlSpace.None`.  
  
 Uma maneira final para acessar o conteúdo de um buffer de mensagem é gravar seu conteúdo para um fluxo usando <xref:System.ServiceModel.Channels.Message.WriteMessage%2A>.  
  
 O exemplo a seguir demonstra o processo de trabalho com um `MessageBuffer`: uma mensagem de entrada é encaminhada para vários destinatários e, em seguida, é registrada em um arquivo. Sem buffer, isso não for possível, porque o corpo da mensagem, em seguida, pode ser acessado apenas uma vez.  
  
 [!code-csharp[C_UsingTheMessageClass#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#7)]
 [!code-vb[C_UsingTheMessageClass#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#7)]  
  
 O `MessageBuffer` classe tem outros membros vale a pena observar. O <xref:System.ServiceModel.Channels.MessageBuffer.Close%2A> método pode ser chamado para liberar recursos quando o conteúdo do buffer não é mais necessário. O <xref:System.ServiceModel.Channels.MessageBuffer.BufferSize%2A> propriedade retorna o tamanho do buffer alocado. O <xref:System.ServiceModel.Channels.MessageBuffer.MessageContentType%2A> propriedade retorna o tipo de conteúdo de MIME da mensagem.  
  
## <a name="accessing-the-message-body-for-debugging"></a>Acessando o corpo da mensagem de depuração  
 Para fins de depuração, você pode chamar o <xref:System.ServiceModel.Channels.Message.ToString%2A> método para obter uma representação da mensagem como uma cadeia de caracteres. Essa representação geralmente corresponde a maneira como uma mensagem seria na conexão se ele foi codificado com o codificador de texto, exceto que o XML seria melhor formatado para fins de legibilidade humana. A única exceção a isso é o corpo da mensagem. O corpo pode ser lido apenas uma vez, e `ToString` não altera o estado da mensagem. Portanto, o `ToString` pode não ser capaz de acessar o corpo de método e pode substituir um espaço reservado (por exemplo, "..." ou três pontos) em vez do corpo da mensagem. Portanto, não use `ToString` para as mensagens de log se o conteúdo do corpo das mensagens é importante.  
  
## <a name="accessing-other-message-parts"></a>Acesso a outras partes da mensagem  
 Várias propriedades são fornecidas para acessar informações sobre a mensagem que não seja o seu conteúdo do corpo. No entanto, eles não podem ser chamados depois que a mensagem foi fechada:  
  
-   O <xref:System.ServiceModel.Channels.Message.Headers%2A> propriedade representa os cabeçalhos de mensagem. Consulte a seção "Trabalhando com cabeçalhos" neste tópico.  
  
-   O <xref:System.ServiceModel.Channels.Message.Properties%2A> propriedade representa as propriedades de mensagem, que são partes de dados nomeada anexados à mensagem de que não geralmente obter emitida quando a mensagem é enviada. Consulte a seção "Trabalhando com propriedades", mais adiante neste tópico.  
  
-   O <xref:System.ServiceModel.Channels.Message.Version%2A> propriedade indica a versão SOAP e WS-Addressing associada à mensagem, ou `None` se SOAP estiver desabilitado.  
  
-   O <xref:System.ServiceModel.Channels.Message.IsFault%2A> propriedade retorna `true` se a mensagem é uma mensagem de falha SOAP.  
  
-   O <xref:System.ServiceModel.Channels.Message.IsEmpty%2A> propriedade retorna `true` se a mensagem está vazia.  
  
 Você pode usar o <xref:System.ServiceModel.Channels.Message.GetBodyAttribute%28System.String%2CSystem.String%29> método para acessar um determinado atributo no elemento body wrapper (por exemplo, `<soap:Body>`) identificada por um determinado nome e namespace. Se um atributo não for encontrado, `null` será retornado. Esse método pode ser chamado apenas quando o `Message` está no estado criado (quando o corpo da mensagem ainda não tiver sido acessado).  
  
## <a name="working-with-headers"></a>Trabalhando com cabeçalhos  
 Um `Message` pode conter qualquer número de fragmentos de XML nomeados chamado *cabeçalhos*. Cada fragmento normalmente é mapeado para um cabeçalho SOAP. Cabeçalhos são acessados por meio de `Headers` propriedade do tipo <xref:System.ServiceModel.Channels.MessageHeaders>. <xref:System.ServiceModel.Channels.MessageHeaders> é uma coleção de <xref:System.ServiceModel.Channels.MessageHeaderInfo> objetos e os cabeçalhos individuais podem ser acessados por meio de seu <xref:System.Collections.IEnumerable> interface ou por meio do seu indexador. Por exemplo, o código a seguir lista os nomes de todos os cabeçalhos em uma `Message`.  
  
 [!code-csharp[C_UsingTheMessageClass#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#8)]
 [!code-vb[C_UsingTheMessageClass#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#8)]  
  
#### <a name="adding-removing-finding-headers"></a>Adicionando, removendo, localizando cabeçalhos  
 Você pode adicionar um novo cabeçalho no final de todos os cabeçalhos existentes usando o <xref:System.ServiceModel.Channels.MessageHeaders.Add%2A> método. Você pode usar o <xref:System.ServiceModel.Channels.MessageHeaders.Insert%2A> método para inserir um cabeçalho em um índice específico. Cabeçalhos existentes são deslocados para o item inserido. Cabeçalhos são ordenados de acordo com seu índice, e o primeiro índice disponível é 0. Você pode usar as várias <xref:System.ServiceModel.Channels.MessageHeaders.CopyHeadersFrom%2A> sobrecargas do método para adicionar cabeçalhos de outro `Message` ou `MessageHeaders` instância. Algumas sobrecargas copiem um cabeçalho individual, enquanto outros usuários copiar todos eles. O <xref:System.ServiceModel.Channels.MessageHeaders.Clear%2A> método Remove todos os cabeçalhos. O <xref:System.ServiceModel.Channels.MessageHeaders.RemoveAt%2A> método Remove um cabeçalho em um índice específico (deslocamento de todos os cabeçalhos após ele). O <xref:System.ServiceModel.Channels.MessageHeaders.RemoveAll%2A> método Remove todos os cabeçalhos com um determinado nome e namespace.  
  
 Recuperar um cabeçalho específico usando o <xref:System.ServiceModel.Channels.MessageHeaders.FindHeader%2A> método. Esse método usa o nome e o namespace do cabeçalho para localizar e retorna seu índice. Se o cabeçalho ocorre mais de uma vez, uma exceção será lançada. Se o cabeçalho não for encontrado, ele retornará -1.  
  
 No modelo de cabeçalho de SOAP, os cabeçalhos podem ter um `Actor` valor que especifica o destinatário pretendido do cabeçalho. O mais básico `FindHeader` sobrecarga procura somente cabeçalhos destinados para o destinatário final da mensagem. No entanto, outra sobrecarga permite que você especifique qual `Actor` valores são incluídos na pesquisa. Para obter mais informações, consulte a especificação de SOAP.  
  
 Um <xref:System.ServiceModel.Channels.MessageHeaders.CopyTo%28System.ServiceModel.Channels.MessageHeaderInfo%5B%5D%2CSystem.Int32%29> método é fornecido para copiar os cabeçalhos de uma <xref:System.ServiceModel.Channels.MessageHeaders> coleção para uma matriz de <xref:System.ServiceModel.Channels.MessageHeaderInfo> objetos.  
  
 Para acessar os dados XML em um cabeçalho, você pode chamar <xref:System.ServiceModel.Channels.MessageHeaders.GetReaderAtHeader%2A> e retornar um leitor de XML para o índice de cabeçalho específico. Se você quiser desserializar o conteúdo de cabeçalho em um objeto, use <xref:System.ServiceModel.Channels.MessageHeaders.GetHeader%60%601%28System.Int32%29> ou uma das outras sobrecargas. As sobrecargas mais básicas desserializar cabeçalhos usando o <xref:System.Runtime.Serialization.DataContractSerializer> configurado no padrão de forma. Se você deseja usar um serializador diferente ou uma configuração diferente do `DataContractSerializer`, use uma das sobrecargas que levam um `XmlObjectSerializer`. Também há sobrecargas que têm o nome do cabeçalho, namespace e, opcionalmente, uma lista de `Actor` valores em vez de um índice, essa é uma combinação de `FindHeader` e `GetHeader`.  
  
## <a name="working-with-properties"></a>Trabalhando com propriedades  
 Um `Message` instância pode conter um número arbitrário de objetos nomeados de tipos arbitrários. Essa coleção é acessada por meio de `Properties` propriedade do tipo `MessageProperties`. A coleção implementa o <xref:System.Collections.Generic.IDictionary%602> interface e atua como um mapeamento de <xref:System.String> para <xref:System.Object>. Normalmente, os valores de propriedade não são mapeados diretamente para qualquer parte da mensagem na conexão, mas em vez disso, forneça várias dicas de processamento de mensagem para os vários canais no [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] pilha de canais ou o <xref:System.ServiceModel.Channels.MessageHeaders.CopyTo%28System.ServiceModel.Channels.MessageHeaderInfo%5B%5D%2CSystem.Int32%29> estrutura do serviço. Para obter um exemplo, consulte [Data Transfer Overview arquitetura](../../../../docs/framework/wcf/feature-details/data-transfer-architectural-overview.md).  
  
## <a name="inheriting-from-the-message-class"></a>Herança da classe de mensagem  
 Se o interno mensagem tipos criados usando `CreateMessage` não atender às suas necessidades, crie uma classe que deriva de `Message` classe.  
  
### <a name="defining-the-message-body-contents"></a>Definir o conteúdo do corpo de mensagem  
 Existem três principais técnicas para acessar dados em um corpo de mensagem: gravar, ler e copiá-la para um buffer. Essas operações resultam no <xref:System.ServiceModel.Channels.Message.OnWriteBodyContents%2A>, <xref:System.ServiceModel.Channels.Message.OnGetReaderAtBodyContents%2A>, e <xref:System.ServiceModel.Channels.Message.OnCreateBufferedCopy%2A> métodos que está sendo chamados, respectivamente, em sua classe derivada de `Message`. A base de `Message` classe garante que apenas um desses métodos é chamado para cada `Message` instância, e que ele não é chamado mais de uma vez. A classe base também garante que os métodos não são chamados em uma mensagem fechada. Não é necessário para controlar o estado de mensagem em sua implementação.  
  
 <xref:System.ServiceModel.Channels.Message.OnWriteBodyContents%2A> é um método abstrato e deve ser implementado. A maneira mais simples para definir o conteúdo do corpo da mensagem é escrever usando esse método. Por exemplo, a seguinte mensagem de erro contém números aleatórios 100.000 de 1 a 20.  
  
 [!code-csharp[C_UsingTheMessageClass#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#9)]
 [!code-vb[C_UsingTheMessageClass#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#9)]  
  
 O `OnGetReaderAtBodyContents` e `OnCreateBufferedCopy` métodos têm implementações padrão que funcionam na maioria dos casos. A chamada de implementações padrão `OnWriteBodyContents`, os resultados de buffer e trabalhar com o buffer resultante. No entanto, em alguns casos isso pode não ser suficiente. No exemplo anterior, ler os resultados de mensagem em 100.000 elementos XML que está sendo armazenado em buffer, que podem não ser desejáveis. Talvez você queira substituir `OnGetReaderAtBodyContents` para retornar um personalizado `XmlDictionaryReader` derivado da classe que serve de números aleatórios. Em seguida, você pode substituir `OnWriteBodyContents` para usar o leitor de que o `OnGetReaderAtBodyContents` propriedade retorna, conforme mostrado no exemplo a seguir.  
  
 [!code-csharp[C_UsingTheMessageClass#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#10)]
 [!code-vb[C_UsingTheMessageClass#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#10)]  
  
 Da mesma forma, talvez você queira substituir `OnCreateBufferedCopy` para retornar o seu próprio `MessageBuffer` classe derivada.  
  
 Além de fornecer o conteúdo do corpo de mensagem, sua classe de mensagem derivada também deve substituir o `Version`, `Headers`, e `Properties` propriedades.  
  
 Observe que, se você criar uma cópia de uma mensagem, a cópia usa os cabeçalhos de mensagem do original.  
  
### <a name="other-members-that-can-be-overridden"></a>Outros membros que podem ser substituídos  
 Você pode substituir o <xref:System.ServiceModel.Channels.Message.OnWriteStartEnvelope%2A>, <xref:System.ServiceModel.Channels.Message.OnWriteStartHeaders%2A>, e <xref:System.ServiceModel.Channels.Message.OnWriteStartBody%2A> métodos para especificar como o envelope SOAP, cabeçalhos SOAP e elemento de corpo SOAP marcas iniciam são gravados. Normalmente, eles correspondem às `<soap:Envelope>`, `<soap:Header>`, e `<soap:Body>`. Esses métodos normalmente não devem gravar nada se o `Version` propriedade retorna `MessageVersion.None`.  
  
> [!NOTE]
>  A implementação padrão de `OnGetReaderAtBodyContents` chamadas `OnWriteStartEnvelope` e `OnWriteStartBody` antes de chamar `OnWriteBodyContents` e os resultados de buffer. Cabeçalhos não são gravados.  
  
 Substituir o <xref:System.ServiceModel.Channels.Message.OnWriteMessage%2A> método para alterar a maneira como a mensagem inteira é construída de suas várias partes. O `OnWriteMessage` método é chamado de <xref:System.ServiceModel.Channels.Message.WriteMessage%2A> e do padrão <xref:System.ServiceModel.Channels.Message.OnCreateBufferedCopy%2A> implementação. Observe que substituindo <xref:System.ServiceModel.Channels.Message.WriteMessage%2A> não é uma prática recomendada. É melhor substituir as `On` métodos (por exemplo, <xref:System.ServiceModel.Channels.Message.OnWriteStartEnvelope%2A>, <xref:System.ServiceModel.Channels.Message.OnWriteStartHeaders%2A>, e <xref:System.ServiceModel.Channels.BodyWriter.OnWriteBodyContents%2A>.  
  
 Substituir <xref:System.ServiceModel.Channels.Message.OnBodyToString%2A> para substituir a maneira como o corpo da mensagem é representado durante a depuração. O padrão é para representá-lo como três pontos ("..."). Observe que esse método pode ser chamado o várias vezes quando o estado da mensagem é algo que não seja fechado. Uma implementação deste método nunca deve causar qualquer ação que deve ser executada somente uma vez (como a leitura de um fluxo somente de encaminhamento).  
  
 Substituir o <xref:System.ServiceModel.Channels.Message.OnGetBodyAttribute%2A> método para permitir o acesso a atributos no elemento de corpo SOAP. Esse método pode ser chamado várias vezes, mas o `Message` tipo base garante que ele é chamado apenas quando a mensagem estiver no estado criado. Não é necessário para verificar o estado em uma implementação. A implementação padrão sempre retorna `null`, que indica que não há nenhum atributo no elemento body.  
  
 Se seu `Message` objeto deve fazer qualquer limpeza especial quando o corpo da mensagem não é mais necessário, você pode substituir <xref:System.ServiceModel.Channels.Message.OnClose%2A>. A implementação padrão não fará nada.  
  
 O `IsEmpty` e `IsFault` propriedades podem ser substituídas. Por padrão, ambos retornam `false`.
