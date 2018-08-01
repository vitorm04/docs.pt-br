---
title: Serialization1
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: bebb27ac-9712-4196-9931-de19fc04dbac
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: db06feefdd9697fd53d64bce60ae11c7e74f8c88
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33578060"
---
# <a name="serialization"></a>Serialização
A serialização é o processo de converter um objeto em um formato que pode ser prontamente persistente ou transportado. Por exemplo, você pode serializar um objeto, transportá-lo pela Internet usando HTTP e desserializado-lo no computador de destino.  
  
 O .NET Framework oferece três tecnologias de serialização principal otimizadas para vários cenários de serialização. A tabela a seguir lista essas tecnologias e os principais tipos de estrutura relacionados a elas.  
  
|**Nome de tecnologia**|**Tipos principais**|**Cenários**|  
|-------------------------|--------------------|-------------------|  
|**Serialização de contrato de dados**|<xref:System.Runtime.Serialization.DataContractAttribute> <br /> <xref:System.Runtime.Serialization.DataMemberAttribute> <br /> <xref:System.Runtime.Serialization.DataContractSerializer> <br /> <xref:System.Runtime.Serialization.NetDataContractSerializer> <br /> <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> <br /> <xref:System.Runtime.Serialization.ISerializable>|Persistência geral<br />Serviços Web<br />JSON|  
|**Serialização de XML**|<xref:System.Xml.Serialization.XmlSerializer>|Formato XML com controle total sobre a forma do XML|  
|**Serialização de tempo de execução (binário e SOAP)**|<xref:System.SerializableAttribute> <br /> <xref:System.Runtime.Serialization.ISerializable> <br /> <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> <br /> <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>|Comunicação remota .NET|  
  
 **✓ DO** pense quando você cria novos tipos de serialização.  
  
## <a name="choosing-the-right-serialization-technology-to-support"></a>Escolhendo a tecnologia de serialização correta que receberá suporte  
 **✓ CONSIDER** oferecer suporte a serialização de contrato de dados se instâncias de seu tipo talvez precise ser persistidas ou usado em serviços Web.  
  
 **✓ CONSIDER** com suporte a serialização de XML em vez de ou além de serialização de contrato de dados, se você precisar de mais controle sobre o formato XML que é gerado quando o tipo é serializado.  
  
 Isso pode ser necessário em alguns cenários em que você precisa usar um XML construir de interoperabilidade que não há suporte para serialização de contrato de dados, por exemplo, para produzir os atributos XML.  
  
 **✓ CONSIDER** com suporte a serialização de tempo de execução se instâncias de seu tipo precisam se deslocar entre limites de comunicação remota do .NET.  
  
 **X AVOID** com suporte a serialização de tempo de execução ou serialização XML apenas por motivos de persistência geral. Preferir a serialização de contrato de dados em vez disso.  
  
## <a name="supporting-data-contract-serialization"></a>Oferecendo suporte à serialização do contrato de dados  
 Tipos podem dar suporte a serialização de contrato de dados, aplicando o <xref:System.Runtime.Serialization.DataContractAttribute> para o tipo e o <xref:System.Runtime.Serialization.DataMemberAttribute> para os membros (propriedades e campos) do tipo.  
  
 **✓ CONSIDER** marcar membros de dados do seu tipo de público se o tipo pode ser usado em confiança parcial.  
  
 Em confiança total, serializadores de contrato de dados podem serializar e desserializar confidenciais tipos e membros, mas somente os membros públicos podem ser serializados e desserializados em confiança parcial.  
  
 **✓ DO** implementar um getter e setter em todas as propriedades que têm <xref:System.Runtime.Serialization.DataMemberAttribute>. Serializadores de contrato de dados exigem o getter e setter para o tipo a ser considerado serializável. (No .NET Framework 3.5 SP1, algumas propriedades de coleção podem ser somente obtenção.) Se o tipo não será usado na confiança parcial, um ou ambos os acessadores de propriedade poderão ser não públicos.  
  
 **✓ CONSIDER** usando os retornos de chamada de serialização para inicialização de instâncias desserializadas.  
  
 Os construtores não são chamados quando os objetos são desserializados. (Há exceções à regra. Construtores de coleções marcado com <xref:System.Runtime.Serialization.CollectionDataContractAttribute> são chamados durante a desserialização.) Portanto, qualquer lógica que é executada durante a construção normal deve ser implementada como um dos retornos de chamada de serialização.  
  
 `OnDeserializedAttribute` é o atributo de retorno de chamada mais comumente usadas. Os outros atributos da família são <xref:System.Runtime.Serialization.OnDeserializingAttribute>, <xref:System.Runtime.Serialization.OnSerializingAttribute> e <xref:System.Runtime.Serialization.OnSerializedAttribute>. Eles podem ser usados para marcar os retornos de chamada que são executados antes de desserialização, antes da serialização e, por fim, após a serialização, respectivamente.  
  
 **✓ CONSIDER** usando o <xref:System.Runtime.Serialization.KnownTypeAttribute> para indicar tipos concretos que devem ser usados ao desserializar um gráfico de objeto complexo.  
  
 **✓ DO** considerar a compatibilidade com versões anteriores e posteriores ao criar ou alterar os tipos serializáveis.  
  
 Tenha em mente que os fluxos serializados de versões futuras do tipo podem ser desserializados na versão atual de tipo e vice-versa.  
  
 Certifique-se de que entender o que os membros de dados, até mesmo privados e internos, não é possível alterar seus nomes, tipos ou até mesmo seu pedido em versões futuras do tipo, a menos que especial cuidado para preservar o contrato usando parâmetros explícitos para os atributos de contrato de dados .  
  
 Testar a compatibilidade de serialização ao fazer alterações em tipos serializáveis. Tente desserializar a nova versão em uma versão antiga e vice-versa.  
  
 **✓ CONSIDER** implementando <xref:System.Runtime.Serialization.IExtensibleDataObject> para permitir que o ciclo entre versões diferentes do tipo.  
  
 A interface permite que o serializador assegure de que nenhum dado sejam perdido durante o ciclo completo. O <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A?displayProperty=nameWithType> propriedade é usada para armazenar dados da versão futura do tipo desconhecido para a versão atual, e portanto não é possível armazenar em seus membros de dados. Quando a versão atual é subsequentemente serializada e desserializada em uma versão futura, os dados adicionais estarão disponíveis no fluxo serializado.  
  
## <a name="supporting-xml-serialization"></a>Suporte à serialização XML  
 Serialização de contrato de dados é o principal (padrão) tecnologia de serialização do .NET Framework, mas há cenários de serialização que não oferece suporte a serialização de contrato de dados. Por exemplo, ela não fornece controle total sobre o formato XML gerado ou consumido pelo serializador. Se esse controle refinado for necessária, a serialização XML deve ser usado e você precisa criar seus tipos para dar suporte a essa tecnologia de serialização.  
  
 **X AVOID** projetar seus tipos especificamente para a serialização de XML, a menos que você tenha um forte motivo para controlar a forma do XML produzido. Essa tecnologia de serialização foi substituída pela serialização do contrato de dados abordada na seção anterior.  
  
 **✓ CONSIDER** Implementando o <xref:System.Xml.Serialization.IXmlSerializable> interface se você desejar ainda mais controle sobre a forma do XML serializado que o que é oferecido por aplicar os atributos de serialização de XML. Dois métodos de interface, <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> e <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A>, permitem que você controle totalmente o fluxo XML serializado. Você também pode controlar o esquema XML que será gerado para o tipo, aplicando o `XmlSchemaProviderAttribute`.  
  
## <a name="supporting-runtime-serialization"></a>Suporte à serialização em tempo de execução  
 Serialização de tempo de execução é uma tecnologia usada pela comunicação remota do .NET. Se você acha que seus tipos serão ser transportados comunicação remota do .NET, você precisa certificar-se de que eles oferecem suporte a serialização de tempo de execução.  
  
 O suporte básico para a serialização de tempo de execução pode ser fornecido ao aplicar o <xref:System.SerializableAttribute>, e cenários mais avançados que envolvem implementar um padrão de serializável simples do tempo de execução (implementar <xref:System.Runtime.Serialization.ISerializable> e forneça o construtor de serialização).  
  
 **✓ CONSIDER** oferecer suporte a serialização de tempo de execução se seus tipos serão usados com a comunicação remota do .NET. Por exemplo, o <xref:System.AddIn?displayProperty=nameWithType> usa o namespace .NET Remoting e então todos os tipos são trocadas entre `System.AddIn` suplementos precisam oferecer suporte a serialização de tempo de execução.  
  
 **✓ CONSIDER** Implementando o padrão de serializável de tempo de execução, se desejar que o controle completo sobre o processo de serialização. Por exemplo, se você quiser transformar os dados à medida que eles forem serializados ou desserializados.  
  
 O padrão é muito simples. Tudo o que você precisa fazer é implementar a interface <xref:System.Runtime.Serialization.ISerializable> e fornecer um construtor especial que é usado quando o objeto é desserializado.  
  
 **✓ DO** fazer o construtor de serialização protegido e fornecer dois parâmetros digitados e denominado exatamente como mostrado no exemplo aqui.  
  
```  
[Serializable]  
public class Person : ISerializable {  
    protected Person(SerializationInfo info, StreamingContext context) {  
        ...  
    }  
}  
```  
  
 **✓ DO** implementar o `ISerializable` membros explicitamente.  
  
 **✓ DO** aplicar uma demanda de link para <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=nameWithType> implementação. Isso garante que somente confiáveis core e o serializador de tempo de execução tem acesso ao membro.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*  
  
 *Reimpressas pela permissão de Pearson educação, Inc. de [diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicados 22 de outubro de 2008, Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*  
  
## <a name="see-also"></a>Consulte também  
 [Diretrizes de design do Framework](../../../docs/standard/design-guidelines/index.md)  
 [Diretrizes de uso](../../../docs/standard/design-guidelines/usage-guidelines.md)
