---
title: Tipos com suporte fornecido pelo serializador de contrato de dados
ms.date: 03/30/2017
helpviewer_keywords:
- serialization [WCF], supported types
ms.assetid: 7381b200-437a-4506-9556-d77bf1bc3f34
ms.openlocfilehash: 2fc33d3cfcbcb00e69728b73edf4a03f0dbab77e
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2019
ms.locfileid: "65878617"
---
# <a name="types-supported-by-the-data-contract-serializer"></a>Tipos com suporte fornecido pelo serializador de contrato de dados
Windows Communication Foundation (WCF) usa o <xref:System.Runtime.Serialization.DataContractSerializer> como seu mecanismo de serialização padrão para converter dados em XML e para converter XML novamente em dados. O <xref:System.Runtime.Serialization.DataContractSerializer> foi projetado para serializar *contrato de dados* tipos. No entanto, ele dá suporte a muitos outros tipos, o que podem ser considerados como tendo um contrato de dados implícita. A seguir está uma lista completa de tipos que pode ser serializado:  
  
- Todos os tipos visíveis publicamente que tem um construtor que não tem parâmetros.  
  
- Tipos de contrato de dados. Esses são os tipos para os quais o <xref:System.Runtime.Serialization.DataContractAttribute> atributo foi aplicado. Novos tipos personalizados que representam os objetos de negócios devem normalmente ser criados como dados de tipos de contrato. Para obter mais informações, consulte [contratos de dados usando](../../../../docs/framework/wcf/feature-details/using-data-contracts.md) e [tipos serializáveis](../../../../docs/framework/wcf/feature-details/serializable-types.md).  
  
- Tipos de coleção. Estes são os tipos que representam listas de dados. Eles podem ser matrizes regulares de tipos ou tipos de coleção, como <xref:System.Collections.ArrayList> e <xref:System.Collections.Generic.Dictionary%602>. O <xref:System.Runtime.Serialization.CollectionDataContractAttribute> atributo pode ser usado para personalizar a serialização desses tipos, mas não é necessário. Para obter mais informações, consulte [tipos de coleção em contratos de dados](../../../../docs/framework/wcf/feature-details/collection-types-in-data-contracts.md).  
  
- Tipos de enumeração. Enumerações, incluindo enumerações de sinalizador são serializáveis. Opcionalmente, os tipos de enumeração podem ser marcados com o <xref:System.Runtime.Serialization.DataContractAttribute> de atributo, caso em que cada membro que participa de serialização deve ser marcado com o <xref:System.Runtime.Serialization.EnumMemberAttribute> atributo. Os membros que não são marcados como não são serializados. Para obter mais informações, consulte [tipos de enumeração em contratos de dados](../../../../docs/framework/wcf/feature-details/enumeration-types-in-data-contracts.md).  
  
- Tipos primitivos do .NET framework. Os seguintes tipos incorporados ao .NET Framework podem todos ser serializados e são considerados tipos primitivos: <xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.Int32>, <xref:System.Int64>, <xref:System.UInt16>, <xref:System.UInt32>, <xref:System.UInt64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Boolean>, <xref:System.Char>, <xref:System.Decimal>, <xref:System.Object>, e <xref:System.String>.  
  
- Outros tipos primitivos. Esses tipos não são primitivos no .NET Framework, mas são tratados como primitivos no formato XML serializado. Esses tipos são <xref:System.DateTime>, <xref:System.DateTimeOffset>, <xref:System.TimeSpan>, <xref:System.Guid>, <xref:System.Uri>, <xref:System.Xml.XmlQualifiedName>e matrizes de <xref:System.Byte>.  
  
    > [!NOTE]
    >  Ao contrário de outros tipos primitivos, <xref:System.DateTimeOffset> não é um tipo conhecido por padrão. Para obter mais informações, consulte [tipos conhecidos de contrato de dados](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)).  
  
- Tipos marcados com o <xref:System.SerializableAttribute> atributo. Muitos tipos incluídos na biblioteca de classe base do .NET Framework se enquadram nessa categoria. O <xref:System.Runtime.Serialization.DataContractSerializer> totalmente compatível com esse modelo de programação de serialização que foi usado pela comunicação remota do .NET Framework, o <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>e o <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>, incluindo suporte para o <xref:System.Runtime.Serialization.ISerializable> interface.  
  
- Tipos que representam tipos que representam dados relacionais do ADO.NET ou XML bruto. O <xref:System.Xml.XmlElement> e a matriz de <xref:System.Xml.XmlNode> tipos têm suporte como uma maneira de representar o XML diretamente. Além disso, tipos que implementam o <xref:System.Xml.Serialization.IXmlSerializable> interface são suportadas, incluindo relacionado <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> atributo e o <xref:System.Xml.Linq.XDocument> e <xref:System.Xml.Linq.XElement> tipos. O ADO.NET<xref:System.Data.DataTable> tipo e o <xref:System.Data.DataSet> tipo (bem como suas classes derivadas tipados) implementam a <xref:System.Xml.Serialization.IXmlSerializable> de interface e, portanto, se encaixa nessa categoria. Para obter mais informações, consulte [XML e tipos ADO.NET em contratos de dados](../../../../docs/framework/wcf/feature-details/xml-and-ado-net-types-in-data-contracts.md).  
  
## <a name="limitations-of-using-certain-types-in-partial-trust-mode"></a>Modo de confiança de limitações do uso de certos tipos parcial  
 A seguir está uma lista de limitações ao usar determinados tipos em cenários de modo de confiança parcial:  
  
- Para serializar ou desserializar um tipo que implementa <xref:System.Runtime.Serialization.ISerializable> em código parcialmente confiável usando o <xref:System.Runtime.Serialization.DataContractSerializer> requer que o <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter%2A> e <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A> permissões.  
  
- Ao executar o código do WCF [confiança parcial](../../../../docs/framework/wcf/feature-details/partial-trust.md) modo, a serialização e desserialização de `readonly` campos (ambos `public` e `private`) não tem suporte. Isso ocorre porque a IL gerada não é verificável e, portanto, requer permissões elevadas.  
  
- Tanto a <xref:System.Runtime.Serialization.DataContractSerializer> e o <xref:System.Xml.Serialization.XmlSerializer> têm suporte em um ambiente de confiança parcial. No entanto, usar o <xref:System.Runtime.Serialization.DataContractSerializer> está sujeito a condições a seguir:  
  
    - Todos os serializável `[DataContract]` tipos devem ser públicos.  
  
    - Todos os serializável `[DataMember]` campos ou propriedades em um `[DataContract]` tipo deve ser pública e leitura/gravação. A serialização e desserialização de `readonly` campos não tem suporte durante a execução do WCF em um aplicativo parcialmente confiável.  
  
    - O `[Serializable]` / `ISerializable]` não há suporte para o modelo de programação em um ambiente de confiança parcial.  
  
    - Conhecidos tipos devem ser especificados no código ou configuração de nível de máquina (`Machine.config`). Tipos conhecidos não podem ser especificados na configuração de nível de aplicativo por motivos de segurança.  
  
- Tipos que implementam <xref:System.Runtime.Serialization.IObjectReference> lançar uma exceção em um ambiente parcialmente confiável, porque o <xref:System.Runtime.Serialization.IObjectReference.GetRealObject%2A> método requer a permissão de segurança `[SecurityPermission(SecurityAction.LinkDemand, Flags=SecurityPermissionFlag.SerializationFormatter)]`.  
  
## <a name="additional-notes-on-serialization"></a>Observações adicionais sobre serialização  
 As regras a seguir também se aplicam a tipos com suporte pelo serializador de contrato de dados:  
  
- Tipos genéricos são totalmente compatíveis com o serializador de contrato de dados.  
  
- Tipos anuláveis são totalmente compatíveis com o serializador de contrato de dados.  
  
- Tipos de interface são tratados como <xref:System.Object> ou, no caso de interfaces de coleção, como tipos de coleção.  
  
- Há suporte para estruturas e classes.  
  
- O <xref:System.Runtime.Serialization.DataContractSerializer> não oferece suporte para o modelo de programação usado pelo <xref:System.Xml.Serialization.XmlSerializer> e serviços da Web do ASP.NET. Em particular, não oferece suporte a atributos como <xref:System.Xml.Serialization.XmlElementAttribute> e <xref:System.Xml.Serialization.XmlAttributeAttribute>. Para habilitar o suporte para esse modelo de programação, o WCF deve ser alternado para usar o <xref:System.Xml.Serialization.XmlSerializer> em vez do <xref:System.Runtime.Serialization.DataContractSerializer>.  
  
- O <xref:System.DBNull> tipo é tratado de maneira especial. Ele é um tipo singleton e após a desserialização o desserializador respeita a restrição de singleton e aponta todos `DBNull` referências para a instância singleton. Porque `DBNull` é um tipo serializável, ela exige <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter%2A> permissão.  
  
## <a name="see-also"></a>Consulte também

- [XML e tipos ADO.NET em contratos de dados](../../../../docs/framework/wcf/feature-details/xml-and-ado-net-types-in-data-contracts.md)
- [Usando contratos de dados](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
- [Tipos serializáveis](../../../../docs/framework/wcf/feature-details/serializable-types.md)
- [Tipos de coleção em contratos de dados](../../../../docs/framework/wcf/feature-details/collection-types-in-data-contracts.md)
- [Tipos de enumeração em contratos de dados](../../../../docs/framework/wcf/feature-details/enumeration-types-in-data-contracts.md)
