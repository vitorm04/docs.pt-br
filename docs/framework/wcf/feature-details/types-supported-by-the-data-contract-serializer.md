---
title: Tipos com suporte fornecido pelo serializador de contrato de dados
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- serialization [WCF], supported types
ms.assetid: 7381b200-437a-4506-9556-d77bf1bc3f34
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 98eb46e0f31995efe7db177d90691a9f59288590
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="types-supported-by-the-data-contract-serializer"></a>Tipos com suporte fornecido pelo serializador de contrato de dados
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]usa o <xref:System.Runtime.Serialization.DataContractSerializer> como seu mecanismo de serialização padrão para converter dados em XML e converter XML novamente nos dados. O <xref:System.Runtime.Serialization.DataContractSerializer> foi projetado para serializar *contrato de dados* tipos. No entanto, ele oferece suporte a muitos outros tipos, o que podem ser considerados como tendo um contrato de dados implícita. O exemplo a seguir é uma lista completa de tipos que pode ser serializado:  
  
-   Todos os tipos visíveis publicamente que tem um construtor que não tem parâmetros.  
  
-   Tipos de contrato de dados. Estes são os tipos para os quais o <xref:System.Runtime.Serialization.DataContractAttribute> atributo foi aplicado. Novos tipos personalizados que representam objetos de negócios devem normalmente ser criados como dados de tipos de contrato. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Usando contratos de dados](../../../../docs/framework/wcf/feature-details/using-data-contracts.md) e [tipos serializáveis](../../../../docs/framework/wcf/feature-details/serializable-types.md).  
  
-   Tipos de coleção. Estes são os tipos que representam as listas de dados. Eles podem ser matrizes regulares de tipos ou tipos de coleção, como <xref:System.Collections.ArrayList> e <xref:System.Collections.Generic.Dictionary%602>. O <xref:System.Runtime.Serialization.CollectionDataContractAttribute> atributo pode ser usado para personalizar a serialização desses tipos, mas não é necessário. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Tipos de coleção em contratos de dados](../../../../docs/framework/wcf/feature-details/collection-types-in-data-contracts.md).  
  
-   Tipos de enumeração. Enumerações, incluindo enumerações de sinalizador são serializáveis. Opcionalmente, os tipos de enumeração podem ser marcados com o <xref:System.Runtime.Serialization.DataContractAttribute> de atributo, caso em que cada membro que participa de serialização deve ser marcado com o <xref:System.Runtime.Serialization.EnumMemberAttribute> atributo. Membros que não são marcados como não são serializados. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Tipos de enumeração em contratos de dados](../../../../docs/framework/wcf/feature-details/enumeration-types-in-data-contracts.md).  
  
-   Tipos primitivos do .NET framework. Os seguintes tipos criados no .NET Framework podem todos ser serializados e são considerados tipos primitivos: <xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.Int32>, <xref:System.Int64>, <xref:System.UInt16>, <xref:System.UInt32>, <xref:System.UInt64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Boolean>, <xref:System.Char>, <xref:System.Decimal>, <xref:System.Object>, e <xref:System.String>.  
  
-   Outros tipos primitivos. Esses tipos não são tipos primitivos do .NET Framework, mas são tratados como primitivos no formato XML serializado. Esses tipos são <xref:System.DateTime>, <xref:System.DateTimeOffset>, <xref:System.TimeSpan>, <xref:System.Guid>, <xref:System.Uri>, <xref:System.Xml.XmlQualifiedName>e matrizes de <xref:System.Byte>.  
  
    > [!NOTE]
    >  Ao contrário de outros tipos primitivos, <xref:System.DateTimeOffset> não é um tipo conhecido por padrão. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Tipos conhecidos de contrato de dados](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)).  
  
-   Tipos marcados com o <xref:System.SerializableAttribute> atributo. Muitos tipos incluídos no [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] primavera de biblioteca de classe base nessa categoria. O <xref:System.Runtime.Serialization.DataContractSerializer> totalmente dá suporte a este modelo de programação de serialização que foi usado pela comunicação remota do .NET Framework, o <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>e o <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>, incluindo suporte para o <xref:System.Runtime.Serialization.ISerializable> interface.  
  
-   Tipos que representam bruto XML ou tipos que representam [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] dados relacionais. O <xref:System.Xml.XmlElement> e matriz de <xref:System.Xml.XmlNode> tipos têm suporte como uma forma de representar o XML diretamente. Além disso, tipos que implementam o <xref:System.Xml.Serialization.IXmlSerializable> interface têm suporte, incluindo as relacionadas <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> atributo e o <xref:System.Xml.Linq.XDocument> e <xref:System.Xml.Linq.XElement> tipos. O [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] <xref:System.Data.DataTable> tipo e o <xref:System.Data.DataSet> tipo (bem como suas classes derivadas tipados) todos implementam o <xref:System.Xml.Serialization.IXmlSerializable> de interface e, portanto, se encaixam nesta categoria. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][XML e tipos ADO.NET em contratos de dados](../../../../docs/framework/wcf/feature-details/xml-and-ado-net-types-in-data-contracts.md).  
  
## <a name="limitations-of-using-certain-types-in-partial-trust-mode"></a>Modo de confiança de limitações de uso de certos tipos parcial  
 A seguir está uma lista de limitações ao usar determinados tipos de cenários de modo de confiança parcial:  
  
-   Para serializar ou desserializar um tipo que implementa <xref:System.Runtime.Serialization.ISerializable> código parcialmente confiável usando o <xref:System.Runtime.Serialization.DataContractSerializer> requer o <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter%2A> e <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A> permissões.  
  
-   Ao executar [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] de código em [confiança parcial](../../../../docs/framework/wcf/feature-details/partial-trust.md) modo, a serialização e desserialização de `readonly` campos (ambos `public` e `private`) não tem suporte. Isso ocorre porque o IL gerado não é verificável e, portanto, requer permissões elevadas.  
  
-   Tanto o <xref:System.Runtime.Serialization.DataContractSerializer> e <xref:System.Xml.Serialization.XmlSerializer> têm suporte em um ambiente de confiança parcial. No entanto, usar o <xref:System.Runtime.Serialization.DataContractSerializer> está sujeita às seguintes condições:  
  
    -   Todos os serializável `[DataContract]` tipos devem ser públicos.  
  
    -   Todos os serializável `[DataMember]` campos ou propriedades em um `[DataContract]` tipo deve ser público e leitura/gravação. A serialização e desserialização de `readonly` campos não é suportado quando executando [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] em um aplicativo parcialmente confiável.  
  
    -   O `[Serializable]` / `ISerializable]` não há suporte para o modelo de programação em um ambiente de confiança parcial.  
  
    -   Conhecido tipos devem ser especificados no código ou configuração de nível de máquina (`Machine.config`). Tipos conhecidos não podem ser especificados na configuração de nível de aplicativo por motivos de segurança.  
  
-   Tipos que implementam <xref:System.Runtime.Serialization.IObjectReference> lançar uma exceção em um ambiente parcialmente confiável, porque o <xref:System.Runtime.Serialization.IObjectReference.GetRealObject%2A> método requer a permissão de segurança `[SecurityPermission(SecurityAction.LinkDemand, Flags=SecurityPermissionFlag.SerializationFormatter)]`.  
  
## <a name="additional-notes-on-serialization"></a>Observações adicionais sobre serialização  
 As seguintes regras também se aplicam a tipos com suporte pelo serializador de contrato de dados:  
  
-   Tipos genéricos são totalmente suportados pelo serializador de contrato de dados.  
  
-   Tipos anuláveis são totalmente suportados pelo serializador de contrato de dados.  
  
-   Tipos de interface são tratados como <xref:System.Object> ou, no caso de interfaces de coleção, como tipos de coleção.  
  
-   Há suporte para estruturas e classes.  
  
-   O <xref:System.Runtime.Serialization.DataContractSerializer> não oferece suporte para o modelo de programação usado pelo <xref:System.Xml.Serialization.XmlSerializer> e [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] serviços Web. Em particular, não dá suporte a atributos como <xref:System.Xml.Serialization.XmlElementAttribute> e <xref:System.Xml.Serialization.XmlAttributeAttribute>. Para habilitar o suporte para este modelo de programação, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] deve ser ativada para usar o <xref:System.Xml.Serialization.XmlSerializer> em vez do <xref:System.Runtime.Serialization.DataContractSerializer>.  
  
-   O <xref:System.DBNull> tipo é tratado de maneira especial. Ele é um tipo singleton e após a desserialização o desserializador respeita a restrição de singleton e todos os pontos `DBNull` referências para a instância singleton. Porque `DBNull` é um tipo serializável, ele exige <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter%2A> permissão.  
  
## <a name="see-also"></a>Consulte também  
 [XML e tipos ADO.NET em contratos de dados](../../../../docs/framework/wcf/feature-details/xml-and-ado-net-types-in-data-contracts.md)  
 [Usando contratos de dados](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)  
 [Tipos serializáveis](../../../../docs/framework/wcf/feature-details/serializable-types.md)  
 [Tipos de coleção em contratos de dados](../../../../docs/framework/wcf/feature-details/collection-types-in-data-contracts.md)  
 [Tipos de enumeração em contratos de dados](../../../../docs/framework/wcf/feature-details/enumeration-types-in-data-contracts.md)
