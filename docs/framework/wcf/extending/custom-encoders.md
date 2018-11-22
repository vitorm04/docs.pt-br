---
title: Decodificadores personalizados
ms.date: 03/30/2017
ms.assetid: fa0e1d7f-af36-4bf4-aac9-cd4eab95bc4f
ms.openlocfilehash: 036cbff9046df2d1179c5cc0921dd8d89757558b
ms.sourcegitcommit: 8145ad08288bf141d68e3256cb1f7a3ad842ca33
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2018
ms.locfileid: "50034313"
---
# <a name="custom-encoders"></a>Decodificadores personalizados
Este tópico discute como criar codificadores personalizados.  
  
 No Windows Communication Foundation (WCF), use uma *associação* para especificar como transferir dados através de uma rede entre pontos de extremidade. Uma associação é composta de uma sequência de *elementos de associação*. Uma associação inclui elementos de associação de protocolo opcional, como segurança, um necessária *codificador de mensagem* elemento de associação e um elemento de associação de transporte obrigatório. Um codificador de mensagem é representado por uma elemento de associação de codificação de mensagem. Três codificadores de mensagem são incluídos no WCF: binário, MTOM Message Transmission Optimization Mechanism () e texto.  
  
 Uma elemento de associação de codificação que serializa uma saída de mensagem <xref:System.ServiceModel.Channels.Message> e passa-o para o transporte ou recebe o formato serializado de uma mensagem de transporte e passa para a camada de protocolo, se estiver presente, ou para o aplicativo, se ainda não presentes.  
  
 Codificadores de mensagem transform <xref:System.ServiceModel.Channels.Message> instâncias de e para uma representação da conexão. Embora os codificadores são descritos como localizado acima da camada de transporte na pilha de canais, eles residem dentro da camada de transporte. Transportes (por exemplo, HTTP) formatar a mensagem de acordo com os requisitos do padrão de transporte. Codificadores (por exemplo Xml de texto) simplesmente codificam a mensagem.  
  
 Ao se conectar a um servidor ou cliente preexistente, você não pode ter uma opção sobre como usar uma codificação de mensagem específica. No entanto, os serviços WCF podem se tornar acessíveis por meio de vários pontos de extremidade, cada um com um codificador de mensagem diferentes. Quando um único codificador não abrange todo o público para seu serviço, considere a exposição de seu serviço em vários pontos de extremidade. Aplicativos cliente, em seguida, podem escolher o ponto de extremidade que é melhor para eles. Usar vários pontos de extremidade permite que você combine as vantagens de codificadores de mensagem diferente com outros elementos de associação.  
  
## <a name="system-provided-encoders"></a>Codificadores fornecido pelo sistema  
 O WCF fornece várias associações fornecidas pelo sistema que são projetadas para cobrir os cenários mais comuns do aplicativo. Cada uma dessas vinculações combinar um transporte, o codificador de mensagem e outras opções (segurança, por exemplo). Este tópico descreve como estender o `Text`, `Binary`, e `MTOM` codificadores que estão incluídos no WCF, ou criar seu próprio codificador personalizado de mensagem. O codificador de mensagem de texto oferece suporte tanto uma codificação de XML sem formatação, bem como as codificações SOAP. O modo de codificação sem formatação XML do codificador de mensagem de texto é chamado o codificador POX ("Plain Old XML") para distingui-lo de que a codificação de SOAP com base em texto.  
  
 Para obter mais informações sobre as combinações de elementos de associação fornecidos pelas associações fornecidas pelo sistema, consulte a seção correspondente em [escolhendo um transporte](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md).  
  
## <a name="how-to-work-with-system-provided-encoders"></a>Como trabalhar com os codificadores fornecido pelo sistema  
 Uma codificação é adicionada a uma associação usando uma classe derivada de <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>.  
  
 O WCF fornece os seguintes tipos de elementos de associação derivados de <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> classe que pode fornecer para texto, binária e codificação de MTOM Message Transmission Optimization Mechanism ():  
  
-   <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>: Mais interoperável, mas o codificador menos eficiente para mensagens XML. Um serviço Web ou o cliente do serviço Web geralmente pode compreender XML textual. No entanto, não é eficiente transmitir grandes blocos de dados binários como texto.  
  
-   <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>: Representa o elemento de associação que especifica a codificação de caracteres e versionamento de mensagens utilizados para mensagens XML baseadas em binário. Isso é mais eficiente das opções de codificação, mas menos interoperável, porque só é suportado pelos pontos de extremidade do WCF.  
  
-   <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>: Representa o elemento de associação que especifica a codificação de caracteres e o controle de versão de mensagem usado para uma mensagem usando a codificação de MTOM Message Transmission Optimization Mechanism (). MTOM é uma tecnologia eficiente para a transmissão de dados binários em mensagens do WCF. O codificador MTOM tenta equilibrar entre a eficiência e interoperabilidade. A codificação de MTOM transmite a maioria dos XML no formato textual, mas otimiza blocos grandes de dados binários, transmiti-los como-está, sem a conversão em texto.  
  
 O elemento de associação cria um binário, MTOM ou texto <xref:System.ServiceModel.Channels.MessageEncoderFactory>. O factory cria um binário, MTOM ou texto <xref:System.ServiceModel.Channels.MessageEncoderFactory> instância. Normalmente, há apenas uma única instância. No entanto se sessões forem usadas, um codificador diferente pode ser fornecido para cada sessão. O codificador binário faz uso disso para coordenar dicionários dinâmicos (consulte a infra-estrutura de XML).  
  
 O <xref:System.ServiceModel.Channels.MessageEncoder.ReadMessage%2A> e <xref:System.ServiceModel.Channels.MessageEncoder.WriteMessage%2A> métodos são o núcleo dos codificadores. Os métodos fornecem para ler uma mensagem de um fluxo ou de um <xref:System.Byte> matriz. Matrizes de bytes são usados quando o transporte está operando no modo em buffer. As mensagens serão sempre gravadas fluxos. Se o transporte deve armazenar em buffer a mensagem, ele fornece um fluxo que faz o buffer.  
  
 O restante dos membros a trabalhar com o suporte ao conteúdo, tipos de mídia, e <xref:System.ServiceModel.Channels.MessageEncoder.MessageVersion%2A>. O transporte chama esses métodos de codificador para testar se a mensagem de entrada pode ser decodificada por ele, ou para determinar se a mensagem de saída é válida para este codificador.  
  
 Cada um dos três implementações de codificador adiciona as propriedades que são relevantes para as codificações específicas e é totalmente configurável. Os codificadores também expõem as cotas do leitor que têm padrões de segurança. Consulte infraestrutura XML para uma discussão sobre as cotas.  
  
## <a name="features-of-system-provided-encoders"></a>Recursos do que codificadores fornecido pelo sistema  
 Há uma série de recursos fornecidos pelos codificadores fornecido pelo sistema.  
  
### <a name="pooling"></a>Agrupamento  
 Cada uma das implementações de codificador tenta pool tanto quanto possível. Redução das alocações é uma maneira importante de melhorar o desempenho do código gerenciado. Para atingir esse pool, usam as implementações de `SynchronizedPool` classe. O arquivo do c# contém uma descrição das otimizações adicionais usados por esta classe.  
  
 `XmlDictionaryReader` e `XmlDictionaryWriter` instâncias são agrupadas e reinicializadas para evitar a alocar novos para cada mensagem. Para os leitores, uma `OnClose` recupera o leitor o retorno de chamada quando `Close()` é chamado. O codificador também é reciclado alguns objetos de estado de mensagem usados ao construir mensagens. Os tamanhos desses pools são configuráveis pelo `MaxReadPoolSize` e `MaxWritePoolSize` propriedades em cada uma das três classes derivadas de <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>.  
  
### <a name="binary-encoding"></a>Codificação binária  
 Quando usa sessões de codificação binária, a cadeia de caracteres de dicionário dinâmico deve ser comunicada para o receptor da mensagem. Isso é feito, prefixando a mensagem com as cadeias de caracteres de dicionário dinâmico. O receptor corta as cadeias de caracteres, adiciona-os à sessão e processa a mensagem. Corretamente passar cadeias de caracteres de dicionário requer que o transporte ser armazenados em buffer.  
  
 As cadeias de caracteres são acrescentadas à mensagem pelo interno `AddSessionInformationToMessage` método. Ele adiciona as cadeias de caracteres como UTF-8 para a frente da mensagem prefixada com seu comprimento. O cabeçalho do dicionário inteiro, em seguida, é prefixado com o tamanho de seus dados. A operação inversa é executada pelo interno `ExtractSessionInformationFromMessage` método.  
  
 Além das chaves de dicionário dinâmico de processamento, mensagens em buffer de sessão são recebidas de uma maneira exclusiva. Em vez de criar um leitor sobre o documento e processá-la, o codificador binário usa interno `MessagePatterns` classe desconstruir o fluxo binário. A ideia é que a maioria das mensagens têm um determinado conjunto de cabeçalhos que aparecem em uma determinada ordem quando gerado pelo WCF. O sistema padrão quebra a distância com base no que ele espera de mensagem. Se for bem-sucedido, ele inicializa um <xref:System.ServiceModel.Channels.MessageHeaders> objeto sem analisar o XML. Caso contrário, ele reverterá para o método padrão.  
  
### <a name="mtom-encoding"></a>Codificação de MTOM  
 O <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> classe tem uma propriedade de configuração adicional chamada <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement.MaxBufferSize%2A>. Isso coloca um limite superior em quanto dados ele pode armazenar em buffer durante o processo de leitura de uma mensagem. O conjunto de informações XML (Infoset) ou outras partes MIME, talvez precise ser armazenado em buffer para remontar todas as partes MIME em uma única mensagem.  
  
 Para funcionar corretamente com HTTP, a classe de codificador de mensagem MTOM interna fornece algumas APIs internas para `GetContentType` (que também é interno) e `WriteMessage`, que é pública e pode ser substituído. Comunicação mais deve ocorrer para garantir que os valores nos cabeçalhos HTTP concordam com os valores nos cabeçalhos MIME.  
  
 Internamente, o codificador de mensagem MTOM usa os leitores de texto do WCF e é semelhante ao codificador de texto. A principal diferença é que ele otimiza grandes partes do binário ou "binário" BLOBs (objetos grandes), por não convertê-las para codificação de Base 64 antes que está sendo inserido em bytes de mensagem. Em vez disso, esses BLOBs são mantidos extraídos e referenciado como anexos de MIME.  
  
## <a name="writing-your-own-encoder"></a>Escrevendo seu próprio codificador  
 Para implementar seu próprio codificador de mensagem personalizada, você deve fornecer implementações personalizadas das seguintes classes base abstratas:  
  
-   <xref:System.ServiceModel.Channels.MessageEncoder>  
  
-   <xref:System.ServiceModel.Channels.MessageEncoderFactory>  
  
-   <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>  
  
 Conversão da representação na memória de uma mensagem em uma representação que pode ser gravada em um fluxo é encapsulada dentro de <xref:System.ServiceModel.Channels.MessageEncoder> classe, que serve como uma fábrica para leitores XML e gravadores XML que oferecem suporte a tipos específicos de codificações XML.  
  
-   Os principais métodos dessa classe que você deve substituir são:  
  
-   <xref:System.ServiceModel.Channels.MessageEncoder.WriteMessage%2A> que utiliza um <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> do objeto e os grava em um <xref:System.IO.Stream> objeto.  
  
-   <xref:System.ServiceModel.Channels.MessageEncoder.ReadMessage%2A> que utiliza um <xref:System.IO.Stream> objeto e um tamanho máximo do cabeçalho e retorna um <xref:System.ServiceModel.Channels.Message> objeto.  
  
 É o código que você escreve esses métodos que manipula a conversão entre o protocolo de transporte padrão e sua codificação personalizada.  
  
 Em seguida, você precisa codificar uma classe de fábrica que cria seu codificador personalizado. Substituir a <xref:System.ServiceModel.Channels.MessageEncoderFactory.Encoder%2A> para retornar uma instância do seu personalizado <xref:System.ServiceModel.Channels.MessageEncoder>.  
  
 Em seguida, conecte seu personalizado <xref:System.ServiceModel.Channels.MessageEncoderFactory> a pilha do elemento de associação usada para configurar o serviço ou cliente, substituindo o <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.CreateMessageEncoderFactory%2A> método para retornar uma instância desse Data Factory.  
  
 Há dois exemplos fornecidos com o WCF que ilustram esse processo com o código de exemplo: [codificador de mensagem personalizada: codificador de texto personalizado](../../../../docs/framework/wcf/samples/custom-message-encoder-custom-text-encoder.md) e [codificador de mensagem personalizada: codificador de compactação](../../../../docs/framework/wcf/samples/custom-message-encoder-compression-encoder.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>  
 <xref:System.ServiceModel.Channels.MessageEncoderFactory>  
 <xref:System.ServiceModel.Channels.MessageEncoder>  
 [Visão geral da arquitetura de transferência de dados](../../../../docs/framework/wcf/feature-details/data-transfer-architectural-overview.md)  
 [Escolhendo um codificador de mensagem](../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)  
 [Escolhendo um transporte](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)
