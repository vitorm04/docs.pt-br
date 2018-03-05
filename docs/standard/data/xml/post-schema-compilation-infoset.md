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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 5b55271306abdca95694bd8fb2ebb6e538d060ae
ms.sourcegitcommit: ba765893e3efcece67d99fd6d5ce0074b050d1d9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/02/2018
---
# <a name="post-schema-compilation-infoset"></a><span data-ttu-id="f2cd7-102">Compilação Infoset de pré esquema</span><span class="sxs-lookup"><span data-stu-id="f2cd7-102">Post-Schema Compilation Infoset</span></span>
<span data-ttu-id="f2cd7-103">A [Recomendação de esquema XML World Wide Web Consortium (W3C)](https://www.w3.org/XML/Schema) discute as informações definidas (infoset) que devem ser expostas para a validação de pré-esquema e a compilação de pré-esquema.</span><span class="sxs-lookup"><span data-stu-id="f2cd7-103">The [World Wide Web Consortium (W3C) XML Schema Recommendation](https://www.w3.org/XML/Schema) discusses the information set (infoset) that must be exposed for pre-schema validation and post-schema compilation.</span></span> <span data-ttu-id="f2cd7-104">O modelo de objeto (SOM) de esquema XML exibe essa exposição antes e após o método de <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> de <xref:System.Xml.Schema.XmlSchemaSet> é chamado.</span><span class="sxs-lookup"><span data-stu-id="f2cd7-104">The XML Schema Object Model (SOM) views this exposure before and after the <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> method of the <xref:System.Xml.Schema.XmlSchemaSet> is called.</span></span>  
  
 <span data-ttu-id="f2cd7-105">O infoset de validação de pré-compilação esquema é compilado durante a edição do esquema.</span><span class="sxs-lookup"><span data-stu-id="f2cd7-105">The pre-schema validation infoset is built during the editing of the schema.</span></span> <span data-ttu-id="f2cd7-106">O infoset de compilação de pré esquema é gerado após o método de <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> de <xref:System.Xml.Schema.XmlSchemaSet> é chamado, durante a compilação do esquema, e expostas como propriedades.</span><span class="sxs-lookup"><span data-stu-id="f2cd7-106">The post-schema compilation infoset is generated after the <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> method of the <xref:System.Xml.Schema.XmlSchemaSet> is called, during compilation of the schema, and is exposed as properties.</span></span>  
  
 <span data-ttu-id="f2cd7-107">O SOM é o modelo de objeto que representa os infosets de validação de pré-compilação e esquema de compilação de esquema posteriores; consiste nas classes no namespace de <xref:System.Xml.Schema?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="f2cd7-107">The SOM is the object model that represents the pre-schema validation and post-schema compilation infosets; it consists of the classes in the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="f2cd7-108">Todas as propriedades de leitura e gravação das classes no namespace de <xref:System.Xml.Schema> pertencem ao infoset de validação de pré-compilação esquema, quando todas as propriedades somente leitura das classes no namespace de <xref:System.Xml.Schema> pertencerem ao infoset de compilação de pré esquema.</span><span class="sxs-lookup"><span data-stu-id="f2cd7-108">All read and write properties of classes in the <xref:System.Xml.Schema> namespace belong to the pre-schema validation infoset, while all read-only properties of classes in the <xref:System.Xml.Schema> namespace belong to the post-schema compilation infoset.</span></span> <span data-ttu-id="f2cd7-109">A exceção a essa regra é as seguintes propriedades, que são propriedades de infoset de compilação de infoset e posteriores do esquema de validação de pré-compilação esquema.</span><span class="sxs-lookup"><span data-stu-id="f2cd7-109">The exception to this rule are the following properties, which are both pre-schema validation infoset and post-schema compilation infoset properties.</span></span>  
  
|<span data-ttu-id="f2cd7-110">Classe</span><span class="sxs-lookup"><span data-stu-id="f2cd7-110">Class</span></span>|<span data-ttu-id="f2cd7-111">propriedade</span><span class="sxs-lookup"><span data-stu-id="f2cd7-111">Property</span></span>|  
|-----------|--------------|  
|<xref:System.Xml.Schema.XmlSchemaObject>|<xref:System.Xml.Schema.XmlSchemaObject.Parent%2A>|  
|<xref:System.Xml.Schema.XmlSchema>|<span data-ttu-id="f2cd7-112"><xref:System.Xml.Schema.XmlSchema.AttributeFormDefault%2A>, <xref:System.Xml.Schema.XmlSchema.BlockDefault%2A>, <xref:System.Xml.Schema.XmlSchema.ElementFormDefault%2A>, <xref:System.Xml.Schema.XmlSchema.FinalDefault%2A>, <xref:System.Xml.Schema.XmlSchema.TargetNamespace%2A></span><span class="sxs-lookup"><span data-stu-id="f2cd7-112"><xref:System.Xml.Schema.XmlSchema.AttributeFormDefault%2A>, <xref:System.Xml.Schema.XmlSchema.BlockDefault%2A>, <xref:System.Xml.Schema.XmlSchema.ElementFormDefault%2A>, <xref:System.Xml.Schema.XmlSchema.FinalDefault%2A>, <xref:System.Xml.Schema.XmlSchema.TargetNamespace%2A></span></span>|  
|<xref:System.Xml.Schema.XmlSchemaExternal>|<xref:System.Xml.Schema.XmlSchemaExternal.Schema%2A>|  
|<xref:System.Xml.Schema.XmlSchemaAttributeGroup>|<xref:System.Xml.Schema.XmlSchemaAttributeGroup.AnyAttribute%2A>|  
|<xref:System.Xml.Schema.XmlSchemaParticle>|<span data-ttu-id="f2cd7-113"><xref:System.Xml.Schema.XmlSchemaParticle.MaxOccurs%2A>, <xref:System.Xml.Schema.XmlSchemaParticle.MinOccurs%2A></span><span class="sxs-lookup"><span data-stu-id="f2cd7-113"><xref:System.Xml.Schema.XmlSchemaParticle.MaxOccurs%2A>, <xref:System.Xml.Schema.XmlSchemaParticle.MinOccurs%2A></span></span>|  
|<xref:System.Xml.Schema.XmlSchemaComplexType>|<xref:System.Xml.Schema.XmlSchemaComplexType.AnyAttribute%2A>|  
  
 <span data-ttu-id="f2cd7-114">Por exemplo, <xref:System.Xml.Schema.XmlSchemaElement> e <xref:System.Xml.Schema.XmlSchemaComplexType> classe têm `BlockResolved` e propriedades de `FinalResolved` .</span><span class="sxs-lookup"><span data-stu-id="f2cd7-114">For example, the <xref:System.Xml.Schema.XmlSchemaElement> and <xref:System.Xml.Schema.XmlSchemaComplexType> classes both have `BlockResolved` and `FinalResolved` properties.</span></span> <span data-ttu-id="f2cd7-115">Essas propriedades são usadas para armazenar valores para as propriedades de `Block` e de `Final` após o esquema foi compilado e validado.</span><span class="sxs-lookup"><span data-stu-id="f2cd7-115">These properties are used to hold the values for the `Block` and `Final` properties after the schema has been compiled and validated.</span></span> <span data-ttu-id="f2cd7-116">`BlockResolved` e `FinalResolved` são propriedades somente leitura que fazem parte de infoset de compilação de pré esquema.</span><span class="sxs-lookup"><span data-stu-id="f2cd7-116">`BlockResolved` and `FinalResolved` are read-only properties that are part of the post-schema compilation infoset.</span></span>  
  
 <span data-ttu-id="f2cd7-117">O exemplo a seguir mostra a propriedade de <xref:System.Xml.Schema.XmlSchemaElement.ElementSchemaType%2A> da classe de <xref:System.Xml.Schema.XmlSchemaElement> definida após validar o esquema.</span><span class="sxs-lookup"><span data-stu-id="f2cd7-117">The following example shows the <xref:System.Xml.Schema.XmlSchemaElement.ElementSchemaType%2A> property of the <xref:System.Xml.Schema.XmlSchemaElement> class set after validating the schema.</span></span> <span data-ttu-id="f2cd7-118">Antes de validação, a propriedade contém uma referência de `null` , e <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> é definido como o nome do tipo em questão.</span><span class="sxs-lookup"><span data-stu-id="f2cd7-118">Before validation, the property contains a `null` reference, and the <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> is set to the name of the type in question.</span></span> <span data-ttu-id="f2cd7-119">Após a validação, <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> é resolvido para um tipo válido, e o objeto do tipo está disponível através da propriedade de <xref:System.Xml.Schema.XmlSchemaElement.ElementSchemaType%2A> .</span><span class="sxs-lookup"><span data-stu-id="f2cd7-119">After validation, the <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> is resolved to a valid type, and the type object is available through the <xref:System.Xml.Schema.XmlSchemaElement.ElementSchemaType%2A> property.</span></span>  
  
 [!code-cpp[PsciSample#1](../../../../samples/snippets/cpp/VS_Snippets_Data/PsciSample/CPP/PsciSample.cpp#1)]
 [!code-csharp[PsciSample#1](../../../../samples/snippets/csharp/VS_Snippets_Data/PsciSample/CS/PsciSample.cs#1)]
 [!code-vb[PsciSample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/PsciSample/VB/PsciSample.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="f2cd7-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f2cd7-120">See Also</span></span>  
 <span data-ttu-id="f2cd7-121">[XML Schema Object Model (SOM)](../../../../docs/standard/data/xml/xml-schema-object-model-som.md) [SOM (Modelo de Objeto de Esquema) XML]</span><span class="sxs-lookup"><span data-stu-id="f2cd7-121">[XML Schema Object Model (SOM)](../../../../docs/standard/data/xml/xml-schema-object-model-som.md)</span></span>
