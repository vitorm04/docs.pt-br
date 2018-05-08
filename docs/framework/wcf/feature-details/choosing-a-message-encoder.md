---
title: Escolhendo um codificador de mensagem
ms.date: 03/30/2017
ms.assetid: 2204d82d-d962-4922-a79e-c9a231604f19
ms.openlocfilehash: bf40d31e3ee04136a094b5045f2502e29caceec8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="choosing-a-message-encoder"></a>Escolhendo um codificador de mensagem
Este tópico discute os critérios para escolher entre os codificadores de mensagem que estão incluídos no Windows Communication Foundation (WCF): binários, o texto e o mecanismo de otimização de transmissão mensagem (MTOM).  
  
 No WCF, que você especificar como transferir dados através de uma rede entre pontos de extremidade por meio de um *associação*, que é composto de uma sequência de *elementos de associação*. Um codificador de mensagem é representado por uma elemento de associação na pilha de associação de codificação de mensagem. Uma associação inclui elementos de associação de protocolo opcional, como um elemento de associação de segurança ou elemento de associação de mensagens confiável, uma elemento de associação e um elemento de associação de transporte necessário de codificação de mensagem necessária.  
  
 O elemento de associação de codificação de mensagem fica abaixo os elementos de associação de protocolo opcional e acima do elemento de associação de transporte necessário. O lado de saída, um codificador de mensagem serializa a saída <xref:System.ServiceModel.Channels.Message> e passa para o transporte. No lado da entrada, um codificador de mensagem recebido o formato serializado de um <xref:System.ServiceModel.Channels.Message> do transporte e passa para o protocolo mais alto de camada, se presente, ou para o aplicativo, se não.  
  
 Ao se conectar a um servidor ou cliente já existente, talvez você não tenha uma opção sobre como usar uma codificação de mensagem específica desde que você precisa codificar as mensagens de forma que o outro lado é esperado. No entanto, se você estiver escrevendo um serviço WCF, você pode expor o serviço por meio de vários pontos de extremidade, cada um usando a codificação de mensagem diferentes. Isso permite que os clientes escolher a melhor codificação para conversar com seu serviço sobre o ponto de extremidade que é melhor para eles, bem como dando a seus clientes a flexibilidade de escolher a codificação é melhor para eles. Usar vários pontos de extremidade também permite que você combine as vantagens de mensagem diferentes codificações com outros elementos de associação.  
  
## <a name="system-provided-encoders"></a>Codificadores fornecido pelo sistema  
 O WCF inclui três codificadores de mensagem, que são representados por três classes a seguir:  
  
-   <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>, o codificador de mensagem de texto, dá suporte a codificação de XML simples e codificação SOAP. O modo de codificação de XML simples do codificador de mensagem de texto é chamado de "plain old XML" (POX) para diferenciá-lo da codificação de SOAP com base em texto. Para habilitar POX, defina o <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement.MessageVersion%2A> propriedade <xref:System.ServiceModel.Channels.MessageVersion.None%2A>. Use o codificador de mensagem de texto para interagir com pontos de extremidade do WCF não.  
  
-   <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>, o codificador de mensagem binária, usa um formato binário compacto e é otimizado para o WCF para comunicação WCF e, portanto, não é interoperável. Isso também é o codificador de alto desempenho mais de todos os codificadores que WCF fornece.  
  
-   <<!--zz xref:System.ServiceModel.Channels.MTOMMessageEncodingBindingElement --> `System.ServiceModel.Channels.MTOMMessageEncodingBindingElement`>, o elemento de associação Especifica a codificação de caracteres e versionamento de mensagem para mensagens usando a codificação de MTOM. MTOM é uma tecnologia eficiente para transmitir dados binários em mensagens do WCF. O codificador MTOM tenta criar um equilíbrio entre eficiência e interoperabilidade. A codificação de MTOM transmite a maioria dos XML no formato textual, mas otimiza o transmiti-los como blocos grandes de dados binários-é, sem conversão de texto. Em termos de eficiência, entre os codificadores que WCF fornece, MTOM é entre (mais lento) de texto e binários (o mais rápido).  
  
## <a name="how-to-choose-a-message-encoder"></a>Como escolher um codificador de mensagem  
 A tabela a seguir descreve os fatores comuns usados para escolher um codificador de mensagem. Priorize os fatores que são importantes para seu aplicativo e, em seguida, escolha os codificadores de mensagem que funcionam melhor com esses fatores. Certifique-se de considerar os fatores adicionais não listados nessa tabela e qualquer codificadores de mensagem personalizado que podem ser necessário em seu aplicativo.  
  
|Fator|Descrição|Codificadores que oferecem suporte a esse fator|  
|------------|-----------------|---------------------------------------|  
|Conjuntos de caracteres com suporte|<xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> e <<!--zz xref:System.ServiceModel.Channels.MTOMMessageEncodingBindingElement --> `System.ServiceModel.Channels.MTOMMessageEncodingBindingElement`> oferece suporte somente aos UTF8 e UTF16 Unicode (*big-endian* e *little endian*) codificações. Se outras codificações são necessárias, como UTF7 ou ASCII, um codificador personalizado deve ser usado. Para um codificador personalizado de exemplo, consulte [codificador de mensagem personalizado](http://go.microsoft.com/fwlink/?LinkId=119857).|Texto|  
|Inspeção|A inspeção é a capacidade de examinar as mensagens durante a transmissão. Codificações de texto, com ou sem o uso de SOAP, permitir que as mensagens ser inspecionado e analisados por muitos aplicativos sem o uso de ferramentas especializadas. Observe que o uso da segurança de transferência, no nível de mensagem ou o transporte, afeta a capacidade de inspecionar mensagens. Confidencialidade impede que uma mensagem que está sendo examinado e integridade impede que uma mensagem que está sendo modificado.|Texto|  
|Confiabilidade|Confiabilidade é a resiliência de um codificador para erros de transmissão. Também é possível fornecer confiabilidade na mensagem, transporte ou camada de aplicativo. Todos os codificadores WCF padrão presumem que outra camada está fornecendo confiabilidade. O codificador tem pouca capacidade de recuperação de um erro de transmissão.|Nenhum|  
|Simplicidade|Simplicidade representa a facilidade com que você pode criar codificadores e decodificadores de uma especificação de codificação. Codificações de texto são particularmente vantajosas para manter a simplicidade e a codificação de texto POX tem a vantagem adicional de não exigir suporte para processamento SOAP.|Texto (POX)|  
|Tamanho|A codificação determina a quantidade de sobrecarga imposta sobre o conteúdo. O tamanho de mensagens codificadas está diretamente relacionado à taxa de transferência máxima das operações de serviço. Codificações binárias são geralmente mais compactas do que de codificações de texto. Quando o tamanho da mensagem é alto, considere compactar também o conteúdo da mensagem durante a codificação. No entanto, a compactação adiciona custos de processamento para o remetente da mensagem e o destinatário.|Binário|  
|Streaming|Streaming permite que aplicativos começar a processar uma mensagem antes da mensagem inteira foi recebido. Efetivamente usando fluxo contínuo requer que os dados importantes para uma mensagem estejam disponíveis no início da mensagem para que o aplicativo de recebimento não é necessário aguardar a chegada. Além disso, os aplicativos que usam a transferência em fluxo devem organizar os dados na mensagem incrementalmente para que o conteúdo não tem dependências de encaminhamento. Em muitos casos, é necessária uma combinação entre o conteúdo de streaming e com o menor tamanho de transferência possível para esse conteúdo.|Nenhum|  
|3º suporte a ferramentas de terceiros|Áreas de suporte para uma codificação incluem o desenvolvimento e diagnóstico. Os desenvolvedores de terceiros fez um grande investimento em bibliotecas e kits de ferramentas para lidar com mensagens codificadas no formato POX.|Texto (POX)|  
|Interoperabilidade|Esse fator refere-se à capacidade de um codificador WCF para interoperar com serviços WCF não.|Texto<br /><br /> MTOM (parcial)|  
  
Observação: Ao usar o codificador binário, usando a configuração de IgnoreWhitespace durante a criação de um XMLReader não terá efeito.  Por exemplo, se você fizer o seguinte dentro de uma operação de serviço:  

```csharp
public void OperationContract(XElement input)
{
    Console.WriteLine("{0}", input.Value);
    int counter = 0;
    var xreader = input.CreateReader();
    var reader = XmlReader.Create(xreader, new XmlReaderSettings() { IgnoreWhitespace = true });
    while (reader.Read())
    {
        counter++;
    }

    Console.WriteLine("Read {0} lines with reader", counter);
}
```  
  
A configuração IgnoreWhitespace é ignorada.  
  
## <a name="compression-and-the-binary-encoder"></a>Compactação e o codificador binário

A partir do WCF 4.5, o codificador binário do WCF adiciona suporte para compactação. Isso permite que você use o algoritmo gzip/deflate para enviar mensagens compactadas de um cliente WCF e também responder com mensagens compactadas do serviço WCF auto-hospedado. Esse recurso permite a compactação em transportes HTTP e TCP. Um IIS hospedado WCF sempre é possível habilitar o serviço para enviar respostas compactadas ao configurar o servidor de host IIS. O tipo de compactação é configurado com a propriedade <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement.CompressionFormat%2A?displayProperty=nameWithType>. Essa propriedade é definida como um do <xref:System.ServiceModel.Channels.CompressionFormat?displayProperty=nameWithType> valores de enum:

* `CompressionFormat.Deflate`
* `CompressionFormat.GZip`
* `CompressionFormat.None`
  
Como essa propriedade é exposta somente em binaryMessageEncodingBindingElement, você precisará criar uma associação personalizada com o seguinte para usar esse recurso:

 ```xml
 <customBinding>
   <binding name="BinaryCompressionBinding">
     <binaryMessageEncoding compressionFormat ="GZip" />
     <httpTransport />
  </binding>
</customBinding>
 ```

O cliente e o serviço precisam concordar em enviar e receber mensagens compactadas e, portanto, a propriedade compressionFormat deve ser configurada no elemento binaryMessageEncoding no cliente e o serviço. Uma ProtocolException é gerada se o serviço ou cliente não está configurado para compactação, mas o outro lado é. A habilitação da compactação deve ser cuidadosamente considerada. A compactação é mais útil se a largura de banda de rede é um afunilamento. No caso em que a CPU é o afunilamento, compactação irá diminuir a taxa de transferência. Teste apropriado deve ser feito em um ambiente simulado para saber se isso beneficia o aplicativo  
  
## <a name="see-also"></a>Consulte também

[Associações](../../../../docs/framework/wcf/feature-details/bindings.md)
