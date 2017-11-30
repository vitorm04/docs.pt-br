---
title: "Compilação Infoset de pré esquema"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 7f1bc7f4-401b-459f-9078-f099cc711fde
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 77fe1790a4ff2f910a740e969e458549f1fd9642
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="post-schema-compilation-infoset"></a>Compilação Infoset de pré esquema
O [recomendação de esquema de XML do World Wide Web Consortium (W3C)](http://go.microsoft.com/fwlink/?linkid=45242) discute o conjunto de informações (infoset) que deve ser exposto para validação do esquema de pré-lançamento e pós-esquema compilação. O modelo de objeto (SOM) de esquema XML exibe essa exposição antes e após o método de <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> de <xref:System.Xml.Schema.XmlSchemaSet> é chamado.  
  
 O infoset de validação de pré-compilação esquema é compilado durante a edição do esquema. O infoset de compilação de pré esquema é gerado após o método de <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> de <xref:System.Xml.Schema.XmlSchemaSet> é chamado, durante a compilação do esquema, e expostas como propriedades.  
  
 O SOM é o modelo de objeto que representa os infosets de validação de pré-compilação e esquema de compilação de esquema posteriores; consiste nas classes no namespace de <xref:System.Xml.Schema?displayProperty=nameWithType> . Todas as propriedades de leitura e gravação das classes no namespace de <xref:System.Xml.Schema> pertencem ao infoset de validação de pré-compilação esquema, quando todas as propriedades somente leitura das classes no namespace de <xref:System.Xml.Schema> pertencerem ao infoset de compilação de pré esquema. A exceção a essa regra é as seguintes propriedades, que são propriedades de infoset de compilação de infoset e posteriores do esquema de validação de pré-compilação esquema.  
  
|Classe|Propriedade|  
|-----------|--------------|  
|<xref:System.Xml.Schema.XmlSchemaObject>|<xref:System.Xml.Schema.XmlSchemaObject.Parent%2A>|  
|<xref:System.Xml.Schema.XmlSchema>|<xref:System.Xml.Schema.XmlSchema.AttributeFormDefault%2A>, <xref:System.Xml.Schema.XmlSchema.BlockDefault%2A>, <xref:System.Xml.Schema.XmlSchema.ElementFormDefault%2A>, <xref:System.Xml.Schema.XmlSchema.FinalDefault%2A>, <xref:System.Xml.Schema.XmlSchema.TargetNamespace%2A>|  
|<xref:System.Xml.Schema.XmlSchemaExternal>|<xref:System.Xml.Schema.XmlSchemaExternal.Schema%2A>|  
|<xref:System.Xml.Schema.XmlSchemaAttributeGroup>|<xref:System.Xml.Schema.XmlSchemaAttributeGroup.AnyAttribute%2A>|  
|<xref:System.Xml.Schema.XmlSchemaParticle>|<xref:System.Xml.Schema.XmlSchemaParticle.MaxOccurs%2A>, <xref:System.Xml.Schema.XmlSchemaParticle.MinOccurs%2A>|  
|<xref:System.Xml.Schema.XmlSchemaComplexType>|<xref:System.Xml.Schema.XmlSchemaComplexType.AnyAttribute%2A>|  
  
 Por exemplo, <xref:System.Xml.Schema.XmlSchemaElement> e <xref:System.Xml.Schema.XmlSchemaComplexType> classe têm `BlockResolved` e propriedades de `FinalResolved` . Essas propriedades são usadas para armazenar valores para as propriedades de `Block` e de `Final` após o esquema foi compilado e validado. `BlockResolved` e `FinalResolved` são propriedades somente leitura que fazem parte de infoset de compilação de pré esquema.  
  
 O exemplo a seguir mostra a propriedade de <xref:System.Xml.Schema.XmlSchemaElement.ElementSchemaType%2A> da classe de <xref:System.Xml.Schema.XmlSchemaElement> definida após validar o esquema. Antes de validação, a propriedade contém uma referência de `null` , e <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> é definido como o nome do tipo em questão. Após a validação, <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> é resolvido para um tipo válido, e o objeto do tipo está disponível através da propriedade de <xref:System.Xml.Schema.XmlSchemaElement.ElementSchemaType%2A> .  
  
 [!code-cpp[PsciSample#1](../../../../samples/snippets/cpp/VS_Snippets_Data/PsciSample/CPP/PsciSample.cpp#1)]
 [!code-csharp[PsciSample#1](../../../../samples/snippets/csharp/VS_Snippets_Data/PsciSample/CS/PsciSample.cs#1)]
 [!code-vb[PsciSample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/PsciSample/VB/PsciSample.vb#1)]  
  
## <a name="see-also"></a>Consulte também  
 [XML Schema Object Model (SOM)](../../../../docs/standard/data/xml/xml-schema-object-model-som.md) [SOM (Modelo de Objeto de Esquema) XML]
