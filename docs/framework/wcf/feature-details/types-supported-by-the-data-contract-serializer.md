---
title: Tipos com suporte fornecido pelo serializador de contrato de dados
ms.date: 03/30/2017
helpviewer_keywords:
- serialization [WCF], supported types
ms.assetid: 7381b200-437a-4506-9556-d77bf1bc3f34
ms.openlocfilehash: f3eedda6c9493688680099f4b07810aebf69ff8a
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249455"
---
# <a name="types-supported-by-the-data-contract-serializer"></a>Tipos com suporte fornecido pelo serializador de contrato de dados

O Windows Communication Foundation (WCF) usa o <xref:System.Runtime.Serialization.DataContractSerializer> como seu mecanismo de serialização padrão para converter dados em XML e converter XML de volta em dados. O <xref:System.Runtime.Serialization.DataContractSerializer> é projetado para serializar tipos *de contratos de dados.* No entanto, ele suporta muitos outros tipos, que podem ser considerados como tendo um contrato de dados implícito. A seguir está uma lista completa de tipos que podem ser serializados:

- Todos os tipos publicamente visíveis que possuem um construtor que não tem parâmetros.

- Tipos de contrato de dados. Estes são tipos <xref:System.Runtime.Serialization.DataContractAttribute> aos quais o atributo foi aplicado. Novos tipos personalizados que representam objetos de negócios devem ser normalmente criados como tipos de contrato de dados. Para obter mais informações, consulte [Usando contratos de dados](../../../../docs/framework/wcf/feature-details/using-data-contracts.md) e tipos [serializáveis](../../../../docs/framework/wcf/feature-details/serializable-types.md).

- Tipos de coleção. Estes são tipos que representam listas de dados. Estes podem ser matrizes regulares de <xref:System.Collections.ArrayList> tipos, ou tipos de coleta, tais como e <xref:System.Collections.Generic.Dictionary%602>. O <xref:System.Runtime.Serialization.CollectionDataContractAttribute> atributo pode ser usado para personalizar a serialização desses tipos, mas não é necessário. Para obter mais informações, consulte [Tipos de Coleta em Contratos de Dados](../../../../docs/framework/wcf/feature-details/collection-types-in-data-contracts.md).

- Tipos de enumeração. Enumerações, incluindo enumerações de bandeiras, são serializáveis. Opcionalmente, os tipos de enumeração podem ser marcados com o atributo, <xref:System.Runtime.Serialization.DataContractAttribute> nesse <xref:System.Runtime.Serialization.EnumMemberAttribute> caso cada membro que participa da serialização deve ser marcado com o atributo. Membros que não estão marcados não são serializados. Para obter mais informações, consulte [Tipos de Enumeração em Contratos de Dados](../../../../docs/framework/wcf/feature-details/enumeration-types-in-data-contracts.md).

- .NET Framework tipos primitivos. Os seguintes tipos incorporados no Quadro .NET podem ser todos <xref:System.Byte> <xref:System.SByte>serializados e são considerados tipos <xref:System.Char> <xref:System.Decimal>primitivos: , <xref:System.Object>, <xref:System.String> <xref:System.UInt16> <xref:System.UInt32> <xref:System.UInt64> <xref:System.Single> <xref:System.Double> <xref:System.Int16>, <xref:System.Int32>, <xref:System.Int64>, , , , , , , , , , , <xref:System.Boolean>, , , e .

- Outros tipos primitivos. Esses tipos não são primitivos no .NET Framework, mas são tratados como primitivos na forma XML serializada. Estes <xref:System.DateTime>tipos <xref:System.DateTimeOffset> <xref:System.TimeSpan>são, <xref:System.Uri> <xref:System.Xml.XmlQualifiedName>, , <xref:System.Guid>, <xref:System.Byte>, , , , e matrizes de .

  > [!NOTE]
  > Ao contrário de <xref:System.DateTimeOffset> outros tipos primitivos, não é um tipo conhecido por padrão. Para obter mais informações, consulte Data Contract Known Types ( [Tipos conhecidos)](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)

- Tipos marcados <xref:System.SerializableAttribute> com o atributo. Muitos tipos incluídos na biblioteca de classe base do .NET Framework se enquadram nessa categoria. O <xref:System.Runtime.Serialization.DataContractSerializer> modelo de programação de serialização que foi usado pelo <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>.NET <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>Framework remoting, <xref:System.Runtime.Serialization.ISerializable> o , e o , incluindo suporte para a interface.

- Tipos que representam XML bruto ou tipos que representam dados ADO.NET relacionais. A <xref:System.Xml.XmlElement> matriz <xref:System.Xml.XmlNode> e a matriz de tipos são suportados como uma forma de representar xml diretamente. Além disso, os <xref:System.Xml.Serialization.IXmlSerializable> tipos que implementam a <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> interface são <xref:System.Xml.Linq.XDocument> <xref:System.Xml.Linq.XElement> suportados, incluindo o atributo relacionado, e os e tipos. O<xref:System.Data.DataTable> ADO.NET tipo <xref:System.Data.DataSet> e o tipo (assim como suas classes <xref:System.Xml.Serialization.IXmlSerializable> derivadas digitadas) implementam a interface e, portanto, se encaixam nesta categoria. Para obter mais informações, consulte [XML e ADO.NET Tipos em Contratos de Dados](../../../../docs/framework/wcf/feature-details/xml-and-ado-net-types-in-data-contracts.md).

## <a name="limitations-of-using-certain-types-in-partial-trust-mode"></a>Limitações do uso de certos tipos no modo de confiança parcial

A seguir está uma lista de limitações ao usar certos tipos em cenários de modo de confiança parcial:

- Para serializar ou desserializar <xref:System.Runtime.Serialization.ISerializable> um tipo que implementa <xref:System.Runtime.Serialization.DataContractSerializer> em <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter%2A> <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A> código parcialmente confiável usando as permissões requer e as permissões.

- Ao executar o código WCF no modo [Confiança Parcial,](../../../../docs/framework/wcf/feature-details/partial-trust.md) a `public` `private`serialização e desserialização dos `readonly` campos (ambos e ) não é suportada. Isso porque o IL gerado é inverificável e, portanto, requer permissões elevadas.

- Tanto <xref:System.Runtime.Serialization.DataContractSerializer> o <xref:System.Xml.Serialization.XmlSerializer> e o são apoiados em um ambiente de confiança parcial. No entanto, <xref:System.Runtime.Serialization.DataContractSerializer> o uso do está sujeito às seguintes condições:

  - Todos os `[DataContract]` tipos serializáveis devem ser públicos.

  - Todos os `[DataMember]` campos ou `[DataContract]` propriedades serializáveis em um tipo devem ser públicos e ler/gravar. A serialização e desserialização dos `readonly` campos não é suportada ao executar o WCF em um aplicativo parcialmente confiável.

  - `[Serializable]` / O `ISerializable]` modelo de programação não é suportado em um ambiente de confiança parcial.

  - Os tipos conhecidos devem ser especificados`Machine.config`em código ou configuração em nível de máquina ( ). Os tipos conhecidos não podem ser especificados na configuração em nível de aplicativo por razões de segurança.

- Os tipos <xref:System.Runtime.Serialization.IObjectReference> que implementam lançam uma exceção <xref:System.Runtime.Serialization.IObjectReference.GetRealObject%2A> em um `[SecurityPermission(SecurityAction.LinkDemand, Flags=SecurityPermissionFlag.SerializationFormatter)]`ambiente parcialmente confiável porque o método requer a permissão de segurança .

## <a name="additional-notes-on-serialization"></a>Notas adicionais sobre serialização

As seguintes regras também se aplicam aos tipos suportados pelo Serializador de Contratos de Dados:

- Os tipos genéricos são totalmente suportados pelo serializador de contratos de dados.

- Os tipos de valor anulados são totalmente suportados pelo serializador de contratos de dados.

- Os tipos de <xref:System.Object> interface são tratados como ou, no caso de interfaces de coleta, como tipos de coleta.

- Tanto estruturas quanto classes são apoiadas.

- O <xref:System.Runtime.Serialization.DataContractSerializer> não suporta o modelo de <xref:System.Xml.Serialization.XmlSerializer> programação utilizado pelos serviços web e ASP.NET. Em particular, não suporta atributos como <xref:System.Xml.Serialization.XmlElementAttribute> e <xref:System.Xml.Serialization.XmlAttributeAttribute>. Para habilitar o suporte a este modelo de <xref:System.Xml.Serialization.XmlSerializer> programação, <xref:System.Runtime.Serialization.DataContractSerializer>o WCF deve ser alternado para usar o em vez de .

- O <xref:System.DBNull> tipo é tratado de forma especial. É um tipo singleton, e após a desserialização o desserializador respeita a restrição singleton e aponta todas as `DBNull` referências à instância singleton. Por `DBNull` ser um tipo serializável, exige <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter%2A> permissão.

## <a name="see-also"></a>Confira também

- [Tipos de XML e ADO.NET em contratos de dados](../../../../docs/framework/wcf/feature-details/xml-and-ado-net-types-in-data-contracts.md)
- [Usando contratos de dados](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
- [Tipos serializáveis](../../../../docs/framework/wcf/feature-details/serializable-types.md)
- [Tipos de coleção em contratos de dados](../../../../docs/framework/wcf/feature-details/collection-types-in-data-contracts.md)
- [Tipos de enumeração em contratos de dados](../../../../docs/framework/wcf/feature-details/enumeration-types-in-data-contracts.md)
