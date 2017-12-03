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
# <a name="serializable-types"></a><span data-ttu-id="b834a-102">Tipos serializáveis</span><span class="sxs-lookup"><span data-stu-id="b834a-102">Serializable Types</span></span>
<span data-ttu-id="b834a-103">Por padrão, o <xref:System.Runtime.Serialization.DataContractSerializer> serializa todos os tipos de publicamente visíveis.</span><span class="sxs-lookup"><span data-stu-id="b834a-103">By default, the <xref:System.Runtime.Serialization.DataContractSerializer> serializes all publicly visible types.</span></span> <span data-ttu-id="b834a-104">Todas as propriedades públicas de leitura/gravação e os campos do tipo são serializados.</span><span class="sxs-lookup"><span data-stu-id="b834a-104">All public read/write properties and fields of the type are serialized.</span></span>  
  
 <span data-ttu-id="b834a-105">Você pode alterar o comportamento padrão, aplicando o <xref:System.Runtime.Serialization.DataContractAttribute> e <xref:System.Runtime.Serialization.DataMemberAttribute> atributos para os tipos e membros esse recurso pode ser útil em situações em que você tem os tipos que não estão sob seu controle e não podem ser modificados para adicionar atributos.</span><span class="sxs-lookup"><span data-stu-id="b834a-105">You can change the default behavior by applying the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> attributes to the types and members This feature can be useful in situations in which you have types that are not under your control and cannot be modified to add attributes.</span></span> <span data-ttu-id="b834a-106">O <xref:System.Runtime.Serialization.DataContractSerializer> reconhece esses tipos "desmarcados".</span><span class="sxs-lookup"><span data-stu-id="b834a-106">The <xref:System.Runtime.Serialization.DataContractSerializer> recognizes such "unmarked" types.</span></span>  
  
## <a name="serialization-defaults"></a><span data-ttu-id="b834a-107">Padrões de serialização</span><span class="sxs-lookup"><span data-stu-id="b834a-107">Serialization Defaults</span></span>  
 <span data-ttu-id="b834a-108">Você pode aplicar o <xref:System.Runtime.Serialization.DataContractAttribute> e <xref:System.Runtime.Serialization.DataMemberAttribute> atributos para controlar explicitamente ou personalizar a serialização de tipos e membros.</span><span class="sxs-lookup"><span data-stu-id="b834a-108">You can apply the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> attributes to explicitly control or customize the serialization of types and members.</span></span> <span data-ttu-id="b834a-109">Além disso, você pode aplicar esses atributos para campos particulares.</span><span class="sxs-lookup"><span data-stu-id="b834a-109">In addition, you can apply these attributes to private fields.</span></span> <span data-ttu-id="b834a-110">No entanto, até mesmo tipos que não são marcados com esses atributos são serializados e desserializados.</span><span class="sxs-lookup"><span data-stu-id="b834a-110">However, even types that are not marked with these attributes are serialized and deserialized.</span></span> <span data-ttu-id="b834a-111">As seguintes regras e exceções se aplicam:</span><span class="sxs-lookup"><span data-stu-id="b834a-111">The following rules and exceptions apply:</span></span>  
  
-   <span data-ttu-id="b834a-112">O <xref:System.Runtime.Serialization.DataContractSerializer> infere um contrato de dados de tipos sem atributos usando as propriedades padrão dos tipos de recém-criado.</span><span class="sxs-lookup"><span data-stu-id="b834a-112">The <xref:System.Runtime.Serialization.DataContractSerializer> infers a data contract from types without attributes using the default properties of the newly created types.</span></span>  
  
-   <span data-ttu-id="b834a-113">Todos os campos e propriedades públicas com público `get` e `set` métodos são serializados, a menos que você aplique a <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute> a esse membro de atributo.</span><span class="sxs-lookup"><span data-stu-id="b834a-113">All public fields, and properties with public `get` and `set` methods are serialized, unless you apply the <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute> attribute to that member.</span></span>  
  
-   <span data-ttu-id="b834a-114">A semântica de serialização é semelhante do <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="b834a-114">The serialization semantics are similar to those of the <xref:System.Xml.Serialization.XmlSerializer>.</span></span>  
  
-   <span data-ttu-id="b834a-115">Em tipos desmarcados, somente os tipos públicos com construtores que não têm parâmetros são serializados.</span><span class="sxs-lookup"><span data-stu-id="b834a-115">In unmarked types, only public types with constructors that do not have parameters are serialized.</span></span> <span data-ttu-id="b834a-116">A exceção a essa regra é <xref:System.Runtime.Serialization.ExtensionDataObject> usado com o <xref:System.Runtime.Serialization.IExtensibleDataObject> interface.</span><span class="sxs-lookup"><span data-stu-id="b834a-116">The exception to this rule is <xref:System.Runtime.Serialization.ExtensionDataObject> used with the <xref:System.Runtime.Serialization.IExtensibleDataObject> interface.</span></span>  
  
-   <span data-ttu-id="b834a-117">Campos somente leitura, propriedades sem um `get` ou `set` método e as propriedades com interno ou privado `set` ou `get` métodos não são serializados.</span><span class="sxs-lookup"><span data-stu-id="b834a-117">Read-only fields, properties without a `get` or `set` method, and properties with internal or private `set` or `get` methods are not serialized.</span></span> <span data-ttu-id="b834a-118">Essas propriedades são ignoradas e nenhuma exceção for lançada, exceto no caso de coleções somente get.</span><span class="sxs-lookup"><span data-stu-id="b834a-118">Such properties are ignored and no exception is thrown, except in the case of get-only collections.</span></span>  
  
-   <span data-ttu-id="b834a-119"><xref:System.Xml.Serialization.XmlSerializer>atributos (como `XmlElement`, `XmlAttribute`, `XmlIgnore`, `XmlInclude`e assim por diante) são ignorados.</span><span class="sxs-lookup"><span data-stu-id="b834a-119"><xref:System.Xml.Serialization.XmlSerializer> attributes (such as `XmlElement`, `XmlAttribute`, `XmlIgnore`, `XmlInclude`, and so on) are ignored.</span></span>  
  
-   <span data-ttu-id="b834a-120">Se você não se aplicam a <xref:System.Runtime.Serialization.DataContractAttribute> atributo para um determinado tipo, o serializador ignora qualquer membro no tipo ao qual o <xref:System.Runtime.Serialization.DataMemberAttribute> atributo é aplicado.</span><span class="sxs-lookup"><span data-stu-id="b834a-120">If you do not apply the <xref:System.Runtime.Serialization.DataContractAttribute> attribute to a given type, the serializer ignores any member in that type to which the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute is applied.</span></span>  
  
-   <span data-ttu-id="b834a-121">O <xref:System.Runtime.Serialization.DataContractSerializer.KnownTypes%2A> propriedade tem suporte em tipos não marcados com o <xref:System.Runtime.Serialization.DataContractAttribute> atributo.</span><span class="sxs-lookup"><span data-stu-id="b834a-121">The <xref:System.Runtime.Serialization.DataContractSerializer.KnownTypes%2A> property is supported in types not marked with the <xref:System.Runtime.Serialization.DataContractAttribute> attribute.</span></span> <span data-ttu-id="b834a-122">Isso inclui suporte para o <xref:System.Runtime.Serialization.KnownTypeAttribute> atributo em tipos desmarcados.</span><span class="sxs-lookup"><span data-stu-id="b834a-122">This includes support for the <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute on unmarked types.</span></span>  
  
-   <span data-ttu-id="b834a-123">Para "opt out" do processo de serialização para membros públicos, propriedades ou campos, aplicar o <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute> a esse membro de atributo.</span><span class="sxs-lookup"><span data-stu-id="b834a-123">To "opt out" of the serialization process for public members, properties, or fields, apply the <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute> attribute to that member.</span></span>  
  
## <a name="inheritance"></a><span data-ttu-id="b834a-124">Herança</span><span class="sxs-lookup"><span data-stu-id="b834a-124">Inheritance</span></span>  
 <span data-ttu-id="b834a-125">Tipos não marcados (tipos sem o <xref:System.Runtime.Serialization.DataContractAttribute> atributo) pode herdar de tipos que têm esse atributo; no entanto, não é permitido o inverso: tipos com o atributo não podem herdar de tipos desmarcados.</span><span class="sxs-lookup"><span data-stu-id="b834a-125">Unmarked types (types without the <xref:System.Runtime.Serialization.DataContractAttribute> attribute) can inherit from types that do have this attribute; however, the reverse is not permitted: types with the attribute cannot inherit from unmarked types.</span></span> <span data-ttu-id="b834a-126">Essa regra é aplicada principalmente para garantir a compatibilidade com versões anteriores com o código escrito em versões anteriores do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b834a-126">This rule is enforced primarily to ensure backward compatibility with code written in earlier versions of [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b834a-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b834a-127">See Also</span></span>  
 <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute>  
 <xref:System.Runtime.Serialization.DataContractAttribute>  
 <xref:System.Runtime.Serialization.DataMemberAttribute>  
 <xref:System.Xml.Serialization.XmlSerializer>  
 [<span data-ttu-id="b834a-128">Tipos com suporte pelo serializador de contrato de dados</span><span class="sxs-lookup"><span data-stu-id="b834a-128">Types Supported by the Data Contract Serializer</span></span>](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md)
