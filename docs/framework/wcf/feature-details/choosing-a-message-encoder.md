---
title: Escolhendo um codificador de mensagem
ms.date: 03/30/2017
ms.assetid: 2204d82d-d962-4922-a79e-c9a231604f19
ms.openlocfilehash: a306896af7a73d43956638981908c12d86126a9f
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80345250"
---
# <a name="choosing-a-message-encoder"></a>Escolhendo um codificador de mensagem
Este tópico discute critérios para a escolha entre os codificadores de mensagens que estão incluídos no Windows Communication Foundation (WCF): mecanismo de otimização binária, de texto e de transmissão de mensagens (MTOM).  
  
 No WCF, você especifica como transferir dados através de uma rede entre pontos finais por meio de uma *vinculação,* que é composta por uma seqüência de *elementos de ligação*. Um codificador de mensagens é representado por um elemento de codificação de mensagem na pilha de vinculação. Uma vinculação inclui elementos de vinculação de protocolo opcionais, como um elemento de vinculação de segurança ou um elemento de vinculação de mensagens confiável, um elemento de vinculação de codificação de mensagens necessário e um elemento de vinculação de transporte necessário.  
  
 O elemento de encodificação da mensagem está abaixo dos elementos de ligação de protocolo opcionais e acima do elemento de ligação de transporte necessário. No lado de saída, um codificador de mensagens serializa a saída <xref:System.ServiceModel.Channels.Message> e passa para o transporte. No lado de entrada, um codificador de mensagens <xref:System.ServiceModel.Channels.Message> recebe a forma serializada de um do transporte e passa-a para a camada de protocolo superior, se presente, ou para o aplicativo, se não.  
  
 Ao se conectar a um cliente ou servidor pré-existente, você pode não ter escolha sobre o uso de uma codificação de mensagens específica, uma vez que você precisa codificar suas mensagens de uma maneira que o outro lado está esperando. No entanto, se você estiver escrevendo um serviço WCF, você pode expor seu serviço através de vários pontos finais, cada um usando uma codificação de mensagem diferente. Isso permite que os clientes escolham a melhor codificação para falar com o seu serviço sobre o ponto final que é melhor para eles, além de dar aos seus clientes a flexibilidade para escolher a codificação que é melhor para eles. O uso de vários pontos finais também permite combinar as vantagens de diferentes codificações de mensagens com outros elementos de ligação.  
  
## <a name="system-provided-encoders"></a>Codificadores fornecidos pelo sistema  
 O WCF inclui três codificadores de mensagens, que são representados pelas três classes a seguir:  
  
- <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>, o codificador de mensagens de texto suporta tanto a codificação XML simples quanto a codificação SOAP. O modo de codificação XML simples do codificador de mensagens de texto é chamado de "XML simples e antigo" (POX) para distingui-lo da codificação SOAP baseada em texto. Para habilitar a <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement.MessageVersion%2A> POX, defina a propriedade como <xref:System.ServiceModel.Channels.MessageVersion.None%2A>. Use o codificador de mensagens de texto para interoperar com pontos finais não-WCF.  
  
- <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>, o codificador de mensagens binárias, usa um formato binário compacto e é otimizado para comunicação WCF para WCF, e portanto não é interoperável. Este também é o codificador mais performático de todos os codificadores que o WCF fornece.  
  
- <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>, o elemento de vinculação, especifica a codificação de caracteres e a versão de mensagem para mensagens usando codificação MTOM. O MTOM é uma tecnologia eficiente para transmitir dados binários em mensagens WCF. O codificador MTOM tenta criar um equilíbrio entre eficiência e interoperabilidade. A codificação MTOM transmite a maioria dos XML na forma textual, mas otimiza grandes blocos de dados binários transmitindo-os como está, sem conversão para texto. Em termos de eficiência, entre os codificadores que o WCF fornece, o MTOM está entre texto (o mais lento) e binário (o mais rápido).  
  
## <a name="how-to-choose-a-message-encoder"></a>Como escolher um codificador de mensagens  
 A tabela a seguir descreve fatores comuns usados para escolher um codificador de mensagens. Priorize os fatores que são importantes para o seu aplicativo e, em seguida, escolha os codificadores de mensagens que funcionam melhor com esses fatores. Certifique-se de considerar quaisquer fatores adicionais não listados nesta tabela e quaisquer codificadores de mensagens personalizados que possam ser necessários em seu aplicativo.  
  
|Fator|Descrição|Codificadores que suportam esse fator|  
|------------|-----------------|---------------------------------------|  
|Conjuntos de caracteres suportados|<xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>e <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> suportam apenas as codificações UTF8 e UTF16 Unicode (*grande-endiana* e *pouco endiana).* Se forem necessárias outras codificações, como UTF7 ou ASCII, um codificador personalizado deve ser usado. Para obter um codificador personalizado de exemplo, consulte [Encoder de mensagens personalizadas](https://docs.microsoft.com/dotnet/framework/wcf/samples/custom-message-encoder-custom-text-encoder).|Texto|  
|Inspeção|Inspeção é a capacidade de examinar mensagens durante a transmissão. As codificações de texto, com ou sem o uso de SOAP, permitem que as mensagens sejam inspecionadas e analisadas por muitas aplicações sem o uso de ferramentas especializadas. Observe que o uso da segurança de transferência, tanto no nível de mensagem quanto de transporte, afeta sua capacidade de inspecionar mensagens. A confidencialidade protege uma mensagem de ser examinada e a integridade protege uma mensagem de ser modificada.|Texto|  
|Confiabilidade|Confiabilidade é a resiliência de um codificador para erros de transmissão. A confiabilidade também pode ser fornecida na camada de mensagem, transporte ou aplicativo. Todos os codificadores Padrão WCF assumem que outra camada está fornecendo confiabilidade. O codificador tem pouca capacidade de se recuperar de um erro de transmissão.|Nenhum|  
|Simplicidade|A simplicidade representa a facilidade com que você pode criar codificadores e decodificadores para uma especificação de codificação. As codificações de texto são particularmente vantajosas para a simplicidade, e a codificação de texto POX tem a vantagem adicional de não exigir suporte para o processamento de SOAP.|Texto (POX)|  
|Tamanho|A codificação determina a quantidade de sobrecarga imposta ao conteúdo. O tamanho das mensagens codificadas está diretamente relacionado com o throughput máximo das operações de serviço. As codificações binárias são geralmente mais compactas do que as codificações de texto. Quando o tamanho da mensagem estiver em um prêmio, considere também comprimir o conteúdo da mensagem durante a codificação. No entanto, a compressão adiciona custos de processamento tanto para o remetente de mensagens quanto para o receptor.|Binário|  
|Streaming|O streaming permite que os aplicativos comecem a processar uma mensagem antes que toda a mensagem tenha chegado. O uso efetivo do streaming requer que os dados importantes para uma mensagem estejam disponíveis no início da mensagem para que o aplicativo receptor não seja obrigado a esperar que ele chegue. Além disso, os aplicativos que usam transferência transmitida devem organizar os dados na mensagem gradualmente para que o conteúdo não tenha dependências avançadas. Em muitos casos, você deve comprometer entre o conteúdo de streaming e ter o menor tamanho de transferência possível para esse conteúdo.|Nenhum|  
|Suporte a ferramentas de terceiros|As áreas de apoio para uma codificação incluem desenvolvimento e diagnóstico. Desenvolvedores terceirizados fizeram um grande investimento em bibliotecas e kits de ferramentas para o manuseio de mensagens codificadas no formato POX.|Texto (POX)|  
|Interoperabilidade|Este fator refere-se à capacidade de um codificador WCF de interoperar com serviços não-WCF.|Texto<br /><br /> MTOM (parcial)|  
  
Nota: Ao usar o Codificador Binário, usar a configuração IgnoreWhitespace ao criar um XMLReader não terá efeito.  Por exemplo, se você fizer o seguinte dentro de uma operação de serviço:  

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

A partir do WCF 4.5, o codificador binário do WCF adiciona suporte para compactação. Isso permite que você use o algoritmo gzip/deflate para enviar mensagens compactadas de um cliente WCF e também responda com mensagens compactadas de um serviço WCF auto-hospedado. Esse recurso permite a compactação nos transportes HTTP e TCP. Um serviço WCF hospedado no IIS sempre pode ser habilitado para enviar respostas compactadas configurando o servidor host IIS. O tipo de compactação é configurado com a propriedade <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement.CompressionFormat%2A?displayProperty=nameWithType>. Esta propriedade é definida <xref:System.ServiceModel.Channels.CompressionFormat?displayProperty=nameWithType> como um dos valores de enum:

- <xref:System.ServiceModel.Channels.CompressionFormat.Deflate>
- <xref:System.ServiceModel.Channels.CompressionFormat.GZip>
- <xref:System.ServiceModel.Channels.CompressionFormat.None>
  
Uma vez que esta propriedade só está exposta no binaryMessageEncodingBindingElement, você precisará criar uma vinculação personalizada como a seguinte para usar esse recurso:

 ```xml
 <customBinding>
   <binding name="BinaryCompressionBinding">
     <binaryMessageEncoding compressionFormat ="GZip" />
     <httpTransport />
  </binding>
</customBinding>
 ```

Tanto o cliente quanto o serviço precisam concordar em enviar e receber mensagens compactadas e, portanto, a propriedade compressionFormat deve ser configurada no elemento binaryMessageEncoding no cliente e no serviço. Um ProtocolException é acionado se o serviço ou o cliente não estiver configurado para compactação, mas o outro lado está. A habilitação da compressão deve ser cuidadosamente considerada. A compactação é mais útil se a largura de banda da rede for um gargalo. No caso de a CPU ser o gargalo, a compressão diminuirá a capacidade de throughput. Os testes apropriados devem ser feitos em um ambiente simulado para descobrir se isso beneficia a aplicação  
  
## <a name="see-also"></a>Confira também

- [Ligações](../../../../docs/framework/wcf/feature-details/bindings.md)
