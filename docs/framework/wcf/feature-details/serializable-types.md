---
title: "Tipos serializáveis"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f1c8539a-6a79-4413-b294-896f0957b2cd
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4e368472db3bdca73661586821106174e13d4d24
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="serializable-types"></a>Tipos serializáveis
Por padrão, o <xref:System.Runtime.Serialization.DataContractSerializer> serializa todos os tipos de publicamente visíveis. Todas as propriedades públicas de leitura/gravação e os campos do tipo são serializados.  
  
 Você pode alterar o comportamento padrão, aplicando o <xref:System.Runtime.Serialization.DataContractAttribute> e <xref:System.Runtime.Serialization.DataMemberAttribute> atributos para os tipos e membros esse recurso pode ser útil em situações em que você tem os tipos que não estão sob seu controle e não podem ser modificados para adicionar atributos. O <xref:System.Runtime.Serialization.DataContractSerializer> reconhece esses tipos "desmarcados".  
  
## <a name="serialization-defaults"></a>Padrões de serialização  
 Você pode aplicar o <xref:System.Runtime.Serialization.DataContractAttribute> e <xref:System.Runtime.Serialization.DataMemberAttribute> atributos para controlar explicitamente ou personalizar a serialização de tipos e membros. Além disso, você pode aplicar esses atributos para campos particulares. No entanto, até mesmo tipos que não são marcados com esses atributos são serializados e desserializados. As seguintes regras e exceções se aplicam:  
  
-   O <xref:System.Runtime.Serialization.DataContractSerializer> infere um contrato de dados de tipos sem atributos usando as propriedades padrão dos tipos de recém-criado.  
  
-   Todos os campos e propriedades públicas com público `get` e `set` métodos são serializados, a menos que você aplique a <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute> a esse membro de atributo.  
  
-   A semântica de serialização é semelhante do <xref:System.Xml.Serialization.XmlSerializer>.  
  
-   Em tipos desmarcados, somente os tipos públicos com construtores que não têm parâmetros são serializados. A exceção a essa regra é <xref:System.Runtime.Serialization.ExtensionDataObject> usado com o <xref:System.Runtime.Serialization.IExtensibleDataObject> interface.  
  
-   Campos somente leitura, propriedades sem um `get` ou `set` método e as propriedades com interno ou privado `set` ou `get` métodos não são serializados. Essas propriedades são ignoradas e nenhuma exceção for lançada, exceto no caso de coleções somente get.  
  
-   <xref:System.Xml.Serialization.XmlSerializer>atributos (como `XmlElement`, `XmlAttribute`, `XmlIgnore`, `XmlInclude`e assim por diante) são ignorados.  
  
-   Se você não se aplicam a <xref:System.Runtime.Serialization.DataContractAttribute> atributo para um determinado tipo, o serializador ignora qualquer membro no tipo ao qual o <xref:System.Runtime.Serialization.DataMemberAttribute> atributo é aplicado.  
  
-   O <xref:System.Runtime.Serialization.DataContractSerializer.KnownTypes%2A> propriedade tem suporte em tipos não marcados com o <xref:System.Runtime.Serialization.DataContractAttribute> atributo. Isso inclui suporte para o <xref:System.Runtime.Serialization.KnownTypeAttribute> atributo em tipos desmarcados.  
  
-   Para "opt out" do processo de serialização para membros públicos, propriedades ou campos, aplicar o <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute> a esse membro de atributo.  
  
## <a name="inheritance"></a>Herança  
 Tipos não marcados (tipos sem o <xref:System.Runtime.Serialization.DataContractAttribute> atributo) pode herdar de tipos que têm esse atributo; no entanto, não é permitido o inverso: tipos com o atributo não podem herdar de tipos desmarcados. Essa regra é aplicada principalmente para garantir a compatibilidade com versões anteriores com o código escrito em versões anteriores do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute>  
 <xref:System.Runtime.Serialization.DataContractAttribute>  
 <xref:System.Runtime.Serialization.DataMemberAttribute>  
 <xref:System.Xml.Serialization.XmlSerializer>  
 [Tipos com suporte pelo serializador de contrato de dados](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md)
