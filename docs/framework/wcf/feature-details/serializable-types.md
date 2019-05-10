---
title: Tipos serializáveis
ms.date: 03/30/2017
ms.assetid: f1c8539a-6a79-4413-b294-896f0957b2cd
ms.openlocfilehash: df00623ba45b356561d4d80d970fdf36ee6a377f
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64586148"
---
# <a name="serializable-types"></a>Tipos serializáveis
Por padrão, o <xref:System.Runtime.Serialization.DataContractSerializer> serializa todos os tipos visíveis publicamente. Todas as propriedades de leitura/gravação pública e campos do tipo são serializados.  
  
 Você pode alterar o comportamento padrão aplicando o <xref:System.Runtime.Serialization.DataContractAttribute> e <xref:System.Runtime.Serialization.DataMemberAttribute> atributos para os tipos e membros esse recurso pode ser útil em situações em que você tenha tipos que não estão sob seu controle e não podem ser modificados para adicionar atributos. O <xref:System.Runtime.Serialization.DataContractSerializer> reconhece esses tipos "desmarcados".  
  
## <a name="serialization-defaults"></a>Padrões de serialização  
 Você pode aplicar a <xref:System.Runtime.Serialization.DataContractAttribute> e <xref:System.Runtime.Serialization.DataMemberAttribute> atributos para controlar ou personalizar a serialização de tipos e membros explicitamente. Além disso, você pode aplicar esses atributos a campos privados. No entanto, até mesmo tipos que não são marcados com esses atributos são serializados e desserializados. As seguintes regras e exceções se aplicam:  
  
- O <xref:System.Runtime.Serialization.DataContractSerializer> infere um contrato de dados de tipos sem atributos usando as propriedades padrão dos tipos recém-criado.  
  
- Todos os campos e propriedades públicos com pública `get` e `set` métodos são serializados, a menos que você aplique o <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute> a esse membro de atributo.  
  
- A semântica de serialização é semelhante do <xref:System.Xml.Serialization.XmlSerializer>.  
  
- Em tipos desmarcados, somente os tipos públicos com construtores que não têm parâmetros são serializados. A exceção a essa regra é <xref:System.Runtime.Serialization.ExtensionDataObject> usado com o <xref:System.Runtime.Serialization.IExtensibleDataObject> interface.  
  
- Campos somente leitura, propriedades sem um `get` ou `set` método e as propriedades com interno ou privado `set` ou `get` métodos não são serializados. Essas propriedades são ignoradas e nenhuma exceção é lançada, exceto no caso de coleções somente obtenção.  
  
- <xref:System.Xml.Serialization.XmlSerializer> atributos (como `XmlElement`, `XmlAttribute`, `XmlIgnore`, `XmlInclude`e assim por diante) são ignorados.  
  
- Se você não se aplicam a <xref:System.Runtime.Serialization.DataContractAttribute> atributo a um determinado tipo, o serializador ignora qualquer membro no tipo ao qual o <xref:System.Runtime.Serialization.DataMemberAttribute> atributo é aplicado.  
  
- O <xref:System.Runtime.Serialization.DataContractSerializer.KnownTypes%2A> há suporte para a propriedade em tipos não marcados com o <xref:System.Runtime.Serialization.DataContractAttribute> atributo. Isso inclui suporte para o <xref:System.Runtime.Serialization.KnownTypeAttribute> atributo nos tipos desmarcados.  
  
- Para "opt out" do processo de serialização para os membros públicos, propriedades ou campos, aplicar o <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute> a esse membro de atributo.  
  
## <a name="inheritance"></a>Herança  
 Tipos desmarcados (tipos sem o <xref:System.Runtime.Serialization.DataContractAttribute> atributo) podem herdar de tipos que têm esse atributo; no entanto, o inverso não é permitido: tipos com o atributo não podem herdar de tipos desmarcados. Essa regra é aplicada principalmente para garantir a compatibilidade com versões anteriores com o código escrito em versões anteriores do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute>
- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- <xref:System.Xml.Serialization.XmlSerializer>
- [Tipos com suporte pelo serializador de contrato de dados](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md)
