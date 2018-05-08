---
title: Decodificadores personalizados
ms.date: 03/30/2017
ms.assetid: fa0e1d7f-af36-4bf4-aac9-cd4eab95bc4f
ms.openlocfilehash: 4f7b011b038714ee8349e74f6be270c85aed0a7b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="custom-encoders"></a>Decodificadores personalizados
Este tópico discute como criar decodificadores personalizados.  
  
 No Windows Communication Foundation (WCF), use um *associação* para especificar como transferir dados através de uma rede entre os pontos de extremidade. Uma associação é composta de uma sequência de *elementos de associação*. Uma associação inclui elementos de associação de protocolo opcional, como segurança, necessário *codificador de mensagem* elemento de associação e um elemento de associação de transporte necessário. Um codificador de mensagem é representado por uma elemento de associação de codificação de mensagem. Três codificadores de mensagem estão incluídos no [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]: binário, o mecanismo de otimização de transmissão mensagem (MTOM) e o texto.  
  
 Uma elemento de associação de codificação serializa uma saída de mensagem <xref:System.ServiceModel.Channels.Message> e passa para o transporte ou recebe o formato serializado de uma mensagem do transporte e passa para a camada de protocolo, se presente, ou para o aplicativo, caso ainda não presentes.  
  
 Codificadores de mensagem transform <xref:System.ServiceModel.Channels.Message> instâncias para e de uma representação de transmissão. Embora os codificadores são descritos como sentar-se acima da camada de transporte na pilha de canais, eles residem dentro da camada de transporte. Transportes (por exemplo, HTTP) formatar a mensagem de acordo com os requisitos do padrão de transporte. Codificadores (por exemplo Xml de texto) apenas codificam a mensagem.  
  
 Ao se conectar a um servidor ou cliente preexistente, talvez você não tenha a opção de usar uma codificação de mensagem específica. No entanto, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviços podem se tornar acessíveis através de vários pontos de extremidade, cada um com um codificador de mensagem diferentes. Quando um codificador único não abrange todo o público para o serviço, considere a possibilidade de expor seu serviço em vários pontos de extremidade. Aplicativos cliente podem escolher o ponto de extremidade que é melhor para eles. Usar vários pontos de extremidade permite que você combine as vantagens de codificadores de mensagem diferente com outros elementos de associação.  
  
## <a name="system-provided-encoders"></a>Codificadores fornecido pelo sistema  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] fornece várias associações fornecidas pelo sistema que são projetadas para cobrir os cenários mais comuns do aplicativo. Cada uma dessas vinculações combinar um transporte, o codificador de mensagem e outras opções (security, por exemplo). Este tópico descreve como estender o `Text`, `Binary`, e `MTOM` mensagem codificadores são incluídos no [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], ou criar seu próprio codificador personalizado. O codificador de mensagem de texto oferece suporte tanto uma codificação de XML simples como codificações SOAP. O modo de codificação XML simples do codificador de mensagem de texto é chamado o codificador POX ("Plain Old XML") para distingui-lo de que a codificação de SOAP com base em texto.  
  
 Para obter mais informações sobre as combinações de elementos de associação fornecidos pelas associações de fornecido pelo sistema, consulte a seção correspondente [selecionando um transporte](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md).  
  
## <a name="how-to-work-with-system-provided-encoders"></a>Como trabalhar com codificadores fornecido pelo sistema  
 Uma codificação é adicionada a uma associação usando uma classe derivada de <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] fornece os seguintes tipos de elementos de associação derivados de <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> classe que pode fornecer para texto, binária e codificação de mecanismo de otimização de transmissão da mensagem (MTOM):  
  
-   <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>: Mais interoperável, mas o codificador menos eficiente para mensagens XML. Um cliente de serviço Web ou serviço Web geralmente pode entender XML textual. No entanto, não é eficiente transmitir grandes blocos de dados binários como texto.  
  
-   <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>Representa o elemento de associação que especifica a codificação de caracteres e versionamento de mensagens utilizados para mensagens XML baseadas em binário. Isso é mais eficiente das opções de codificação, mas menos interoperável, porque ele é suportado somente pelo [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] pontos de extremidade.  
  
-   <<!--zz xref:System.ServiceModel.Channels.MTOMMessageEncodingBindingElement --> `System.ServiceModel.Channels.MTOMMessageEncodingBindingElement`>: representa o elemento de associação que especifica a codificação de caracteres e versionamento de mensagem usado para uma mensagem usando uma codificação de mecanismo de otimização de transmissão da mensagem (MTOM). MTOM é uma tecnologia eficiente para transmitir dados binários em [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] mensagens. O codificador MTOM tenta equilíbrio entre eficiência e interoperabilidade. A codificação de MTOM transmite a maioria dos XML no formato textual, mas otimiza o transmiti-los como blocos grandes de dados binários-é, sem conversão de texto.  
  
 O elemento de associação cria um binário, MTOM ou texto <xref:System.ServiceModel.Channels.MessageEncoderFactory>. A fábrica cria um binário, MTOM ou texto <xref:System.ServiceModel.Channels.MessageEncoderFactory> instância. Normalmente, há apenas uma única instância. No entanto se sessões forem usadas, um codificador diferente pode ser fornecido para cada sessão. O codificador binário usa isso para coordenar dicionários dinâmicos (consulte a infraestrutura de XML).  
  
 O <xref:System.ServiceModel.Channels.MessageEncoder.ReadMessage%2A> e <xref:System.ServiceModel.Channels.MessageEncoder.WriteMessage%2A> métodos são o núcleo dos codificadores. Fornecem os métodos para ler uma mensagem de um fluxo ou de um <xref:System.Byte> matriz. Matrizes de bytes são usados quando o transporte está operando no modo de buffer. Mensagens sempre são gravadas em fluxos. Se o transporte deve buffer de mensagem, ele fornece um fluxo que realiza o buffer.  
  
 O restante dos membros a trabalhar com o suporte ao conteúdo, tipos de mídia, e <xref:System.ServiceModel.Channels.MessageEncoder.MessageVersion%2A>. O transporte chama esses métodos de codificador para testar se a mensagem de entrada pode ser decodificada por ele, ou para determinar se a mensagem de saída é válida para este codificador.  
  
 Cada um dos três implementações de codificador adiciona propriedades que são relevantes para as codificações específicas e é completamente configurável. Os codificadores também expõem cotas leitor que têm padrões seguros. Consulte infraestrutura XML para uma discussão sobre as cotas.  
  
## <a name="features-of-system-provided-encoders"></a>Recursos de codificadores fornecido pelo sistema  
 Há um número de recursos fornecidos pelos codificadores fornecido pelo sistema.  
  
### <a name="pooling"></a>Agrupamento  
 Cada uma das implementações do codificador tenta pool tanto quanto possível. Reduzir as alocações é uma maneira de chave para melhorar o desempenho do código gerenciado. Para executar este pool, usam as implementações de `SynchronizedPool` classe. O arquivo c# contém uma descrição das otimizações adicionais usados por esta classe.  
  
 `XmlDictionaryReader` e `XmlDictionaryWriter` instâncias são agrupadas e reinicializadas para evitar a alocar novos para cada mensagem. Para os leitores, um `OnClose` o leitor recupera o retorno de chamada quando `Close()` é chamado. O codificador recicla também alguns objetos de estado de mensagem usados durante a construção de mensagens. Os tamanhos desses pools são configuráveis pelo `MaxReadPoolSize` e `MaxWritePoolSize` propriedades em cada uma das três classes derivadas de <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>.  
  
### <a name="binary-encoding"></a>Codificação binária  
 Quando usa sessões de codificação binária, a cadeia de caracteres de dicionário dinâmico deve ser comunicada ao destinatário da mensagem. Isso é feito, prefixando a mensagem com as cadeias de caracteres de dicionário dinâmico. O receptor ignora as cadeias de caracteres, adiciona à sessão e processa a mensagem. Corretamente passar cadeias de caracteres de dicionário requer que o transporte de buffer.  
  
 As cadeias de caracteres são anexadas à mensagem pelo interno `AddSessionInformationToMessage` método. Ele adiciona as cadeias de caracteres UTF-8 para a frente da mensagem prefixada com seu comprimento. O cabeçalho do dicionário inteiro, em seguida, é prefixado com o tamanho de seus dados. A operação inversa é executada por interno `ExtractSessionInformationFromMessage` método.  
  
 Além de chaves do dicionário dinâmico de processamento, mensagens em buffer de sessão são recebidas de uma maneira exclusiva. Em vez de criar um leitor sobre o documento e processá-la, o codificador binário usa interno `MessagePatterns` classe para decompor o fluxo binário. A ideia é que a maioria das mensagens têm um determinado conjunto de cabeçalhos que aparecem em uma determinada ordem quando gerados pelo [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. O sistema padrão quebra a mensagem separadas com base no qual ele espera. Se for bem-sucedido, ele inicializa um <xref:System.ServiceModel.Channels.MessageHeaders> objeto sem analisar o XML. Caso contrário, ele reverterá para o método padrão.  
  
### <a name="mtom-encoding"></a>Codificação de MTOM  
 O <<!--zz xref:System.ServiceModel.Channels.MTOMMessageEncodingBindingElement --> `System.ServiceModel.Channels.MTOMMessageEncodingBindingElement`> classe tem uma propriedade de configuração adicional chamada <<!--zz xref:System.ServiceModel.Channels.MTOMMessageEncodingBindingElement --> `System.ServiceModel.Channels.MTOMMessageEncodingBindingElement`. MaxBufferSize % 2A >. Isso coloca um limite superior no quanto dados é permitido para armazenar em buffer durante o processo de leitura de uma mensagem. O XML informações definidas (Infoset) ou outras partes MIME, talvez precise ser armazenado em buffer para remontar todas as partes MIME em uma única mensagem.  
  
 Para funcionar corretamente com HTTP, a classe de codificador de mensagem MTOM interna fornece algumas APIs interno de `GetContentType` (que também é interno) e `WriteMessage`, que é pública e pode ser substituído. Mais de comunicação deve ocorrer para garantir que os valores nos cabeçalhos HTTP concordam com os valores de cabeçalhos MIME.  
  
 Internamente, o codificador de mensagem MTOM usa [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]do leitores de texto e é semelhante para o codificador de texto. A principal diferença é que ele otimiza a grandes blocos de binário ou "binário" BLOBs (objetos grandes), por não convertê-las para codificação de Base 64 antes de ser incorporada em bytes de mensagem. Em vez disso, esses BLOBs são mantidas extraídos e referenciado como os anexos de MIME.  
  
## <a name="writing-your-own-encoder"></a>Escrevendo seu próprio codificador  
 Para implementar seu próprio codificador de mensagem personalizada, você deve fornecer implementações personalizadas das seguintes classes de base abstratas:  
  
-   <xref:System.ServiceModel.Channels.MessageEncoder>  
  
-   <xref:System.ServiceModel.Channels.MessageEncoderFactory>  
  
-   <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>  
  
 Conversão da representação na memória de uma mensagem em uma representação que pode ser gravada em um fluxo é encapsulado dentro de <xref:System.ServiceModel.Channels.MessageEncoder> classe, que serve como uma fábrica para leitores XML e os gravadores XML que oferecem suporte a tipos específicos de codificações XML.  
  
-   Os principais métodos dessa classe que você deve substituir são:  
  
-   <xref:System.ServiceModel.Channels.MessageEncoder.WriteMessage%2A> qual toma uma <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> do objeto e grava-o em um <xref:System.IO.Stream> objeto.  
  
-   <xref:System.ServiceModel.Channels.MessageEncoder.ReadMessage%2A> qual toma uma <xref:System.IO.Stream> objeto e um tamanho máximo do cabeçalho e retorna um <xref:System.ServiceModel.Channels.Message> objeto.  
  
 É o código escrito em métodos que manipula a conversão entre o protocolo de transporte padrão e a codificação personalizada.  
  
 Em seguida, você precisa codificar uma classe de fábrica que cria seu codificador personalizado. Substituir o <xref:System.ServiceModel.Channels.MessageEncoderFactory.Encoder%2A> para retornar uma instância de personalizados <xref:System.ServiceModel.Channels.MessageEncoder>.  
  
 Conecte-se e personalizados <xref:System.ServiceModel.Channels.MessageEncoderFactory> para a pilha do elemento de associação usada para configurar o serviço ou cliente, substituindo o <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.CreateMessageEncoderFactory%2A> método para retornar uma instância dessa fábrica.  
  
 Há dois exemplos fornecidos com [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] que ilustram o processo com o código de exemplo: [codificador de mensagem personalizado: codificador de texto personalizado](../../../../docs/framework/wcf/samples/custom-message-encoder-custom-text-encoder.md) e [codificador de mensagem personalizado: codificador de compactação](../../../../docs/framework/wcf/samples/custom-message-encoder-compression-encoder.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>  
 <xref:System.ServiceModel.Channels.MessageEncoderFactory>  
 <xref:System.ServiceModel.Channels.MessageEncoder>  
 [Visão geral da arquitetura de transferência de dados](../../../../docs/framework/wcf/feature-details/data-transfer-architectural-overview.md)  
 [Escolhendo um codificador de mensagem](../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)  
 [Escolhendo um transporte](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)
