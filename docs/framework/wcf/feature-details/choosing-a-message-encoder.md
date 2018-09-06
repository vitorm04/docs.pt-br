---
title: Escolhendo um codificador de mensagem
ms.date: 03/30/2017
ms.assetid: 2204d82d-d962-4922-a79e-c9a231604f19
ms.openlocfilehash: 5d2b55f04954cdd855ff9e224d2bc0405919f7a3
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43773101"
---
# <a name="choosing-a-message-encoder"></a>Escolhendo um codificador de mensagem
Este tópico discute os critérios para escolher entre os codificadores de mensagem que estão incluídos no Windows Communication Foundation (WCF): MTOM Message Transmission Optimization Mechanism (), texto e binário.  
  
 No WCF, você especificar como transferir dados através de uma rede entre pontos de extremidade por meio de um *vinculação*, que é composto de uma sequência de *elementos de associação*. Um codificador de mensagem é representado por uma elemento de associação na pilha de associação de codificação de mensagem. Uma associação inclui elementos de associação de protocolo opcional, como um elemento de associação de segurança ou elemento de associação de mensagens confiável, uma elemento de associação e um elemento de associação de transporte obrigatório de codificação de mensagem necessária.  
  
 O elemento de associação de codificação de mensagem fica abaixo os elementos de associação de protocolo opcional e acima do elemento de associação de transporte obrigatório. No lado da saída, um codificador de mensagem serializa a saída <xref:System.ServiceModel.Channels.Message> e o passa para o transporte. No lado da entrada, um codificador de mensagem recebe a forma serializada de um <xref:System.ServiceModel.Channels.Message> do transporte e passa-o para o maior protocolo de camada, se estiver presente, ou para o aplicativo, se não.  
  
 Ao se conectar a um servidor ou cliente já existente, você não pode ter uma opção sobre como usar uma codificação de mensagem específica, pois você precisa codificar as mensagens de forma que o outro lado está esperando. No entanto, se você estiver escrevendo um serviço WCF, você pode expor seu serviço por meio de vários pontos de extremidade, cada um usando a codificação de mensagem diferente. Isso permite que os clientes escolher a melhor codificação para conversar com seu serviço sobre o ponto de extremidade que é melhor para eles, bem como aos seus clientes a flexibilidade de escolher a codificação que é melhor para eles. Usar vários pontos de extremidade também permite que você combine as vantagens de codificações diferentes de mensagem com outros elementos de associação.  
  
## <a name="system-provided-encoders"></a>Codificadores fornecido pelo sistema  
 O WCF inclui três codificadores de mensagem, que são representados pelas três classes:  
  
-   <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>, o codificador de mensagem de texto, oferece suporte para codificação de XML sem formatação e codificação SOAP. O modo de codificação sem formatação XML do codificador de mensagem de texto é chamado de "plain old XML" (POX) para diferenciá-lo de codificação de SOAP com base em texto. Para habilitar POX, defina as <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement.MessageVersion%2A> propriedade para <xref:System.ServiceModel.Channels.MessageVersion.None%2A>. Use o codificador de mensagem de texto para interoperar com pontos de extremidade não WCF.  
  
-   <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>, o codificador de mensagem binária usa um formato binário compacto e é otimizado para o WCF para comunicação WCF e, portanto, não é interoperável. Isso também é o codificador de alto desempenho a maioria dos codificadores que o WCF fornece.  
  
-   <<!--zz xref:System.ServiceModel.Channels.MTOMMessageEncodingBindingElement --> `System.ServiceModel.Channels.MTOMMessageEncodingBindingElement`>, o elemento de associação Especifica a codificação de caracteres e versionamento de mensagem para mensagens usando a codificação de MTOM. MTOM é uma tecnologia eficiente para a transmissão de dados binários em mensagens do WCF. O codificador MTOM tenta criar um equilíbrio entre a eficiência e interoperabilidade. A codificação de MTOM transmite a maioria dos XML no formato textual, mas otimiza blocos grandes de dados binários, transmiti-los como-está, sem a conversão em texto. Em termos de eficiência, entre os codificadores que o WCF fornece, MTOM é texto entre as palavras (o mais lento) e o binário (o mais rápido).  
  
## <a name="how-to-choose-a-message-encoder"></a>Como escolher um codificador de mensagem  
 A tabela a seguir descreve os fatores comuns usados para escolher um codificador de mensagem. Priorize os fatores que são importantes para seu aplicativo e, em seguida, escolha os codificadores de mensagem que funcionam melhor com esses fatores. Certifique-se de considerar os fatores adicionais não listados nessa tabela e qualquer codificadores de mensagem personalizada que podem ser necessário em seu aplicativo.  
  
|fator|Descrição|Codificadores que dão suporte a esse fator|  
|------------|-----------------|---------------------------------------|  
|Conjuntos de caracteres com suporte|<xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> e <<!--zz xref:System.ServiceModel.Channels.MTOMMessageEncodingBindingElement --> `System.ServiceModel.Channels.MTOMMessageEncodingBindingElement`> dão suporte apenas a UTF8 e UTF16 Unicode (*big-endian* e *little endian*) codificações. Se outras codificações são necessárias, como UTF7 ou ASCII, um codificador personalizado deve ser usado. Para um codificador personalizado de exemplo, consulte [codificador de mensagem personalizado](https://go.microsoft.com/fwlink/?LinkId=119857).|Texto|  
|Inspeção|A inspeção é a capacidade de examinar as mensagens durante a transmissão. Codificações de texto, com ou sem o uso de SOAP, permitir que as mensagens sejam inspecionadas e analisados por muitos aplicativos sem o uso de ferramentas especializadas. Observe que o uso de segurança de transferência no nível de mensagem ou de transporte, afeta sua capacidade de inspecionar mensagens. Confidencialidade protege uma mensagem de que está sendo examinado e integridade protege uma mensagem de que está sendo modificado.|Texto|  
|Confiabilidade|A confiabilidade é a resiliência de um codificador para erros de transmissão. Confiabilidade também pode ser fornecida na mensagem, transporte ou camada de aplicativo. Todos os codificadores WCF padrão pressupõem que a outra camada está fornecendo confiabilidade. O codificador tem pouca possibilidade de se recuperar de um erro de transmissão.|Nenhum|  
|Manter a simplicidade|Simplicidade representa a facilidade com a qual você pode criar codificadores e decodificadores para uma especificação de codificação. Codificações de texto são particularmente vantajosas para manter a simplicidade e a codificação de texto POX tem a vantagem adicional de não exigir suporte para o processamento SOAP.|Texto (POX)|  
|Tamanho|A codificação determina a quantidade de sobrecarga imposta sobre o conteúdo. O tamanho de mensagens codificadas está diretamente relacionado à taxa de transferência máxima de operações de serviço. As codificações binárias são geralmente mais compactas do que as codificações de texto. Quando o tamanho da mensagem é reduzido, considere compactar também o conteúdo da mensagem durante a codificação. No entanto, a compactação adiciona os custos de processamento para o remetente da mensagem e o receptor.|Binário|  
|Streaming|Streaming permite que os aplicativos começar a processar uma mensagem antes de toda a mensagem chegou. Efetivamente, usando o streaming requer que os dados importantes para uma mensagem estar disponível no início da mensagem para que o aplicativo de recebimento não é necessário aguardar a chegada. Além disso, aplicativos que usam a transferência de streaming devem organizar os dados na mensagem de forma incremental para que o conteúdo não tem dependências de encaminhamento. Em muitos casos, você deve se comprometer entre conteúdo de streaming e ter o menor tamanho de transferência possível para esse conteúdo.|Nenhum|  
|3º suporte a ferramentas de terceiros|Áreas de suporte para uma codificação incluem desenvolvimento e diagnóstico. Os desenvolvedores de terceiros fez um grande investimento em bibliotecas e kits de ferramentas para lidar com mensagens codificadas no formato POX.|Texto (POX)|  
|Interoperabilidade|Esse fator refere-se à capacidade de um codificador de WCF para interoperar com serviços WCF não.|Texto<br /><br /> MTOM (parcial)|  
  
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

A partir do WCF 4.5, o codificador binário do WCF adiciona suporte para compactação. Isso permite que você use o algoritmo gzip nebo deflate para enviar mensagens compactadas de um cliente WCF e também responder com mensagens compactadas de um serviço WCF auto-hospedado. Esse recurso habilita a compactação em transportes TCP e HTTP. Um IIS hospedado WCF sempre é possível habilitar o serviço para enviar respostas compactadas, configurando o servidor de host do IIS. O tipo de compactação é configurado com a propriedade <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement.CompressionFormat%2A?displayProperty=nameWithType>. Essa propriedade é definida como um do <xref:System.ServiceModel.Channels.CompressionFormat?displayProperty=nameWithType> valores de enumeração:

* `CompressionFormat.Deflate`
* `CompressionFormat.GZip`
* `CompressionFormat.None`
  
Uma vez que essa propriedade só é exposta em binaryMessageEncodingBindingElement, você precisará criar uma associação personalizada semelhante à seguinte para usar esse recurso:

 ```xml
 <customBinding>
   <binding name="BinaryCompressionBinding">
     <binaryMessageEncoding compressionFormat ="GZip" />
     <httpTransport />
  </binding>
</customBinding>
 ```

O cliente e o serviço precisam concordar em enviar e receber mensagens compactadas e, portanto, a propriedade compressionFormat deve ser configurada no elemento binaryMessageEncoding no cliente e serviço. Um ProtocolException será lançada se o cliente ou serviço não está configurado para compactação, mas o outro lado é. A habilitação da compactação deve ser cuidadosamente considerada. A compactação é mais útil se a largura de banda de rede é um gargalo. No caso em que a CPU é o gargalo, compactação irá diminuir a taxa de transferência. O teste apropriado deve ser feito em um ambiente simulado para descobrir se isso beneficia o aplicativo  
  
## <a name="see-also"></a>Consulte também

[Associações](../../../../docs/framework/wcf/feature-details/bindings.md)
