---
title: Referência de esquema de contrato de dados
ms.date: 03/30/2017
helpviewer_keywords:
- data contracts [WCF], schema reference
ms.assetid: 9ebb0ebe-8166-4c93-980a-7c8f1f38f7c0
ms.openlocfilehash: 04d1f753e5788460404942a21a29e1612f674e90
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84593562"
---
# <a name="data-contract-schema-reference"></a><span data-ttu-id="49e6e-102">Referência de esquema de contrato de dados</span><span class="sxs-lookup"><span data-stu-id="49e6e-102">Data Contract Schema Reference</span></span>

<span data-ttu-id="49e6e-103">Este tópico descreve o subconjunto do esquema XML (XSD) usado pelo <xref:System.Runtime.Serialization.DataContractSerializer> para descrever tipos de Common Language Runtime (CLR) para serialização de XML.</span><span class="sxs-lookup"><span data-stu-id="49e6e-103">This topic describes the subset of the XML Schema (XSD) used by <xref:System.Runtime.Serialization.DataContractSerializer> to describe common language runtime (CLR) types for XML serialization.</span></span>

## <a name="datacontractserializer-mappings"></a><span data-ttu-id="49e6e-104">Mapeamentos do DataContractSerializer</span><span class="sxs-lookup"><span data-stu-id="49e6e-104">DataContractSerializer Mappings</span></span>

<span data-ttu-id="49e6e-105">O `DataContractSerializer` mapeia os tipos CLR para xsd quando os metadados são exportados de um serviço de Windows Communication Foundation (WCF) usando um ponto de extremidade de metadados ou a [ferramenta de utilitário de metadados ServiceModel (svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="49e6e-105">The `DataContractSerializer` maps CLR types to XSD when metadata is exported from a Windows Communication Foundation (WCF) service using a metadata endpoint or the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="49e6e-106">Para obter mais informações, consulte [serializador de contrato de dados](data-contract-serializer.md).</span><span class="sxs-lookup"><span data-stu-id="49e6e-106">For more information, see [Data Contract Serializer](data-contract-serializer.md).</span></span>

<span data-ttu-id="49e6e-107">O `DataContractSerializer` também MAPEIA XSD para tipos CLR quando svcutil. exe é usado para acessar documentos WSDL (linguagem de descrição de serviços Web) ou xsd e gerar contratos de dados para serviços ou clientes.</span><span class="sxs-lookup"><span data-stu-id="49e6e-107">The `DataContractSerializer` also maps XSD to CLR types when Svcutil.exe is used to access Web Services Description Language (WSDL) or XSD documents and generate data contracts for services or clients.</span></span>

<span data-ttu-id="49e6e-108">Somente as instâncias de esquema XML que estão em conformidade com os requisitos declarados neste documento podem ser mapeadas para tipos CLR usando o `DataContractSerializer` .</span><span class="sxs-lookup"><span data-stu-id="49e6e-108">Only XML Schema instances that conform to requirements stated in this document can be mapped to CLR types using `DataContractSerializer`.</span></span>

### <a name="support-levels"></a><span data-ttu-id="49e6e-109">Níveis de suporte</span><span class="sxs-lookup"><span data-stu-id="49e6e-109">Support Levels</span></span>

<span data-ttu-id="49e6e-110">O `DataContractSerializer` fornece os seguintes níveis de suporte para um determinado recurso de esquema XML:</span><span class="sxs-lookup"><span data-stu-id="49e6e-110">The `DataContractSerializer` provides the following levels of support for a given XML Schema feature:</span></span>

- <span data-ttu-id="49e6e-111">**Com suporte**.</span><span class="sxs-lookup"><span data-stu-id="49e6e-111">**Supported**.</span></span> <span data-ttu-id="49e6e-112">Há um mapeamento explícito desse recurso para tipos CLR ou atributos (ou ambos) usando `DataContractSerializer` .</span><span class="sxs-lookup"><span data-stu-id="49e6e-112">There is explicit mapping from this feature to CLR types or attributes (or both) using `DataContractSerializer`.</span></span>

- <span data-ttu-id="49e6e-113">**Ignorado**.</span><span class="sxs-lookup"><span data-stu-id="49e6e-113">**Ignored**.</span></span> <span data-ttu-id="49e6e-114">O recurso é permitido em esquemas importados pelo `DataContractSerializer` , mas não tem efeito sobre a geração de código.</span><span class="sxs-lookup"><span data-stu-id="49e6e-114">The feature is allowed in schemas imported by the `DataContractSerializer`, but has no effect on code generation.</span></span>

- <span data-ttu-id="49e6e-115">**Proibido**.</span><span class="sxs-lookup"><span data-stu-id="49e6e-115">**Forbidden**.</span></span> <span data-ttu-id="49e6e-116">O `DataContractSerializer` não oferece suporte à importação de um esquema usando o recurso.</span><span class="sxs-lookup"><span data-stu-id="49e6e-116">The `DataContractSerializer` does not support importing a schema using the feature.</span></span> <span data-ttu-id="49e6e-117">Por exemplo, svcutil. exe, ao acessar um WSDL com um esquema que usa esse recurso, volta a usar o <xref:System.Xml.Serialization.XmlSerializer> em vez disso.</span><span class="sxs-lookup"><span data-stu-id="49e6e-117">For example, Svcutil.exe, when accessing a WSDL with a schema that uses such a feature, falls back to using the <xref:System.Xml.Serialization.XmlSerializer> instead.</span></span> <span data-ttu-id="49e6e-118">Isso é por padrão.</span><span class="sxs-lookup"><span data-stu-id="49e6e-118">This is by default.</span></span>

## <a name="general-information"></a><span data-ttu-id="49e6e-119">Informações gerais</span><span class="sxs-lookup"><span data-stu-id="49e6e-119">General Information</span></span>

- <span data-ttu-id="49e6e-120">O namespace do esquema é descrito em [esquema XML](https://www.w3.org/2001/XMLSchema).</span><span class="sxs-lookup"><span data-stu-id="49e6e-120">The schema namespace is described at [XML Schema](https://www.w3.org/2001/XMLSchema).</span></span> <span data-ttu-id="49e6e-121">O prefixo "XS" é usado neste documento.</span><span class="sxs-lookup"><span data-stu-id="49e6e-121">The prefix "xs" is used in this document.</span></span>

- <span data-ttu-id="49e6e-122">Todos os atributos com um namespace não esquema são ignorados.</span><span class="sxs-lookup"><span data-stu-id="49e6e-122">Any attributes with a non-schema namespace are ignored.</span></span>

- <span data-ttu-id="49e6e-123">Todas as anotações (exceto aquelas descritas neste documento) são ignoradas.</span><span class="sxs-lookup"><span data-stu-id="49e6e-123">Any annotations (except for those described in this document) are ignored.</span></span>

### <a name="xsschema-attributes"></a><span data-ttu-id="49e6e-124">\<xs:schema>: atributos</span><span class="sxs-lookup"><span data-stu-id="49e6e-124">\<xs:schema>: attributes</span></span>

|<span data-ttu-id="49e6e-125">Atributo</span><span class="sxs-lookup"><span data-stu-id="49e6e-125">Attribute</span></span>|<span data-ttu-id="49e6e-126">DataContract</span><span class="sxs-lookup"><span data-stu-id="49e6e-126">DataContract</span></span>|
|---------------|------------------|
|`attributeFormDefault`|<span data-ttu-id="49e6e-127">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="49e6e-127">Ignored.</span></span>|
|`blockDefault`|<span data-ttu-id="49e6e-128">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="49e6e-128">Ignored.</span></span>|
|`elementFormDefault`|<span data-ttu-id="49e6e-129">Deve ser qualificado.</span><span class="sxs-lookup"><span data-stu-id="49e6e-129">Must be qualified.</span></span> <span data-ttu-id="49e6e-130">Todos os elementos devem ser qualificados para que um esquema seja suportado pelo `DataContractSerializer` .</span><span class="sxs-lookup"><span data-stu-id="49e6e-130">All elements must be qualified for a schema to be supported by `DataContractSerializer`.</span></span> <span data-ttu-id="49e6e-131">Isso pode ser feito por meio da definição xs:schema/@elementFormDefault de "qualified" ou pela definição xs:element/@form de "qualified" em cada declaração de elemento individual.</span><span class="sxs-lookup"><span data-stu-id="49e6e-131">This can be accomplished by either setting xs:schema/@elementFormDefault to "qualified" or by setting xs:element/@form to "qualified" on each individual element declaration.</span></span>|
|`finalDefault`|<span data-ttu-id="49e6e-132">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="49e6e-132">Ignored.</span></span>|
|`Id`|<span data-ttu-id="49e6e-133">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="49e6e-133">Ignored.</span></span>|
|`targetNamespace`|<span data-ttu-id="49e6e-134">Com suporte e mapeado para o namespace de contrato de dados.</span><span class="sxs-lookup"><span data-stu-id="49e6e-134">Supported and mapped to the data contract namespace.</span></span> <span data-ttu-id="49e6e-135">Se esse atributo não for especificado, o namespace em branco será usado.</span><span class="sxs-lookup"><span data-stu-id="49e6e-135">If this attribute is not specified, the blank namespace is used.</span></span> <span data-ttu-id="49e6e-136">Não pode ser o namespace reservado `http://schemas.microsoft.com/2003/10/Serialization/` .</span><span class="sxs-lookup"><span data-stu-id="49e6e-136">Cannot be the reserved namespace `http://schemas.microsoft.com/2003/10/Serialization/`.</span></span>|
|`version`|<span data-ttu-id="49e6e-137">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="49e6e-137">Ignored.</span></span>|

### <a name="xsschema-contents"></a><span data-ttu-id="49e6e-138">\<xs:schema>: conteúdo</span><span class="sxs-lookup"><span data-stu-id="49e6e-138">\<xs:schema>: contents</span></span>

|<span data-ttu-id="49e6e-139">Sumário</span><span class="sxs-lookup"><span data-stu-id="49e6e-139">Contents</span></span>|<span data-ttu-id="49e6e-140">Esquema</span><span class="sxs-lookup"><span data-stu-id="49e6e-140">Schema</span></span>|
|--------------|------------|
|`include`|<span data-ttu-id="49e6e-141">Com suporte.</span><span class="sxs-lookup"><span data-stu-id="49e6e-141">Supported.</span></span> <span data-ttu-id="49e6e-142">`DataContractSerializer`dá suporte a xs: include e xs: import.</span><span class="sxs-lookup"><span data-stu-id="49e6e-142">`DataContractSerializer` supports xs:include and xs:import.</span></span> <span data-ttu-id="49e6e-143">No entanto, svcutil. exe restringe o seguinte `xs:include/@schemaLocation` e `xs:import/@location` faz referência quando os metadados são carregados de um arquivo local.</span><span class="sxs-lookup"><span data-stu-id="49e6e-143">However, Svcutil.exe restricts following `xs:include/@schemaLocation` and `xs:import/@location` references when metadata is loaded from a local file.</span></span> <span data-ttu-id="49e6e-144">A lista de arquivos de esquema deve ser passada por meio de um mecanismo fora de banda e não `include` nesse caso; `include` os documentos de esquema d são ignorados.</span><span class="sxs-lookup"><span data-stu-id="49e6e-144">The list of schema files must be passed through an out-of-band mechanism and not through `include` in this case; `include`d schema documents are ignored.</span></span>|
|`redefine`|<span data-ttu-id="49e6e-145">Negado.</span><span class="sxs-lookup"><span data-stu-id="49e6e-145">Forbidden.</span></span> <span data-ttu-id="49e6e-146">O uso de `xs:redefine` é proibido por `DataContractSerializer` por motivos de segurança `x:redefine` : `schemaLocation` requer que seja seguido.</span><span class="sxs-lookup"><span data-stu-id="49e6e-146">The use of `xs:redefine` is forbidden by `DataContractSerializer` for security reasons: `x:redefine` requires `schemaLocation` to be followed.</span></span> <span data-ttu-id="49e6e-147">Em determinadas circunstâncias, svcutil. exe usando DataContract restringe o uso de `schemaLocation` .</span><span class="sxs-lookup"><span data-stu-id="49e6e-147">In certain circumstances, Svcutil.exe using DataContract restricts use of `schemaLocation`.</span></span>|
|`import`|<span data-ttu-id="49e6e-148">Com suporte.</span><span class="sxs-lookup"><span data-stu-id="49e6e-148">Supported.</span></span> <span data-ttu-id="49e6e-149">`DataContractSerializer`dá suporte a `xs:include` e `xs:import` .</span><span class="sxs-lookup"><span data-stu-id="49e6e-149">`DataContractSerializer` supports `xs:include` and `xs:import`.</span></span> <span data-ttu-id="49e6e-150">No entanto, svcutil. exe restringe o seguinte `xs:include/@schemaLocation` e `xs:import/@location` faz referência quando os metadados são carregados de um arquivo local.</span><span class="sxs-lookup"><span data-stu-id="49e6e-150">However, Svcutil.exe restricts following `xs:include/@schemaLocation` and `xs:import/@location` references when metadata is loaded from a local file.</span></span> <span data-ttu-id="49e6e-151">A lista de arquivos de esquema deve ser passada por meio de um mecanismo fora de banda e não `include` nesse caso; `include` os documentos de esquema d são ignorados.</span><span class="sxs-lookup"><span data-stu-id="49e6e-151">The list of schema files must be passed through an out-of-band mechanism and not through `include` in this case; `include`d schema documents are ignored.</span></span>|
|`simpleType`|<span data-ttu-id="49e6e-152">Com suporte.</span><span class="sxs-lookup"><span data-stu-id="49e6e-152">Supported.</span></span> <span data-ttu-id="49e6e-153">Consulte a `xs:simpleType` seção.</span><span class="sxs-lookup"><span data-stu-id="49e6e-153">See the `xs:simpleType` section.</span></span>|
|`complexType`|<span data-ttu-id="49e6e-154">Com suporte, mapeia para contratos de dados.</span><span class="sxs-lookup"><span data-stu-id="49e6e-154">Supported, maps to data contracts.</span></span> <span data-ttu-id="49e6e-155">Consulte a `xs:complexType` seção.</span><span class="sxs-lookup"><span data-stu-id="49e6e-155">See the `xs:complexType` section.</span></span>|
|`group`|<span data-ttu-id="49e6e-156">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="49e6e-156">Ignored.</span></span> <span data-ttu-id="49e6e-157">`DataContractSerializer`não oferece suporte ao uso de `xs:group` , `xs:attributeGroup` e `xs:attribute` .</span><span class="sxs-lookup"><span data-stu-id="49e6e-157">`DataContractSerializer` does not support use of `xs:group`, `xs:attributeGroup`, and `xs:attribute`.</span></span> <span data-ttu-id="49e6e-158">Essas declarações são ignoradas como filhos de `xs:schema` , mas não podem ser referenciadas de dentro `complexType` ou de outras construções com suporte.</span><span class="sxs-lookup"><span data-stu-id="49e6e-158">These declarations are ignored as children of `xs:schema`, but cannot be referenced from within `complexType` or other supported constructs.</span></span>|
|`attributeGroup`|<span data-ttu-id="49e6e-159">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="49e6e-159">Ignored.</span></span> <span data-ttu-id="49e6e-160">`DataContractSerializer`não oferece suporte ao uso de `xs:group` , `xs:attributeGroup` e `xs:attribute` .</span><span class="sxs-lookup"><span data-stu-id="49e6e-160">`DataContractSerializer` does not support use of `xs:group`, `xs:attributeGroup`, and `xs:attribute`.</span></span> <span data-ttu-id="49e6e-161">Essas declarações são ignoradas como filhos de `xs:schema` , mas não podem ser referenciadas de dentro `complexType` ou de outras construções com suporte.</span><span class="sxs-lookup"><span data-stu-id="49e6e-161">These declarations are ignored as children of `xs:schema`, but cannot be referenced from within `complexType` or other supported constructs.</span></span>|
|`element`|<span data-ttu-id="49e6e-162">Com suporte.</span><span class="sxs-lookup"><span data-stu-id="49e6e-162">Supported.</span></span> <span data-ttu-id="49e6e-163">Consulte declaração de elemento global (teste).</span><span class="sxs-lookup"><span data-stu-id="49e6e-163">See Global Element Declaration (GED).</span></span>|
|`attribute`|<span data-ttu-id="49e6e-164">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="49e6e-164">Ignored.</span></span> <span data-ttu-id="49e6e-165">`DataContractSerializer`não oferece suporte ao uso de `xs:group` , `xs:attributeGroup` e `xs:attribute` .</span><span class="sxs-lookup"><span data-stu-id="49e6e-165">`DataContractSerializer` does not support use of `xs:group`, `xs:attributeGroup`, and `xs:attribute`.</span></span> <span data-ttu-id="49e6e-166">Essas declarações são ignoradas como filhos de `xs:schema` , mas não podem ser referenciadas de dentro `complexType` ou de outras construções com suporte.</span><span class="sxs-lookup"><span data-stu-id="49e6e-166">These declarations are ignored as children of `xs:schema`, but cannot be referenced from within `complexType` or other supported constructs.</span></span>|
|`notation`|<span data-ttu-id="49e6e-167">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="49e6e-167">Ignored.</span></span>|

## <a name="complex-types--xscomplextype"></a><span data-ttu-id="49e6e-168">Tipos complexos –\<xs:complexType></span><span class="sxs-lookup"><span data-stu-id="49e6e-168">Complex Types – \<xs:complexType></span></span>

### <a name="general-information"></a><span data-ttu-id="49e6e-169">Informações gerais</span><span class="sxs-lookup"><span data-stu-id="49e6e-169">General Information</span></span>

<span data-ttu-id="49e6e-170">Cada tipo complexo é \<xs:complexType> mapeado para um contrato de dados.</span><span class="sxs-lookup"><span data-stu-id="49e6e-170">Each complex type \<xs:complexType> maps to a data contract.</span></span>

### <a name="xscomplextype-attributes"></a><span data-ttu-id="49e6e-171">\<xs:complexType>: atributos</span><span class="sxs-lookup"><span data-stu-id="49e6e-171">\<xs:complexType>: attributes</span></span>

|<span data-ttu-id="49e6e-172">Atributo</span><span class="sxs-lookup"><span data-stu-id="49e6e-172">Attribute</span></span>|<span data-ttu-id="49e6e-173">Esquema</span><span class="sxs-lookup"><span data-stu-id="49e6e-173">Schema</span></span>|
|---------------|------------|
|`abstract`|<span data-ttu-id="49e6e-174">Deve ser false (padrão).</span><span class="sxs-lookup"><span data-stu-id="49e6e-174">Must be false (default).</span></span>|
|`block`|<span data-ttu-id="49e6e-175">Negado.</span><span class="sxs-lookup"><span data-stu-id="49e6e-175">Forbidden.</span></span>|
|`final`|<span data-ttu-id="49e6e-176">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="49e6e-176">Ignored.</span></span>|
|`id`|<span data-ttu-id="49e6e-177">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="49e6e-177">Ignored.</span></span>|
|`mixed`|<span data-ttu-id="49e6e-178">Deve ser false (padrão).</span><span class="sxs-lookup"><span data-stu-id="49e6e-178">Must be false (default).</span></span>|
|`name`|<span data-ttu-id="49e6e-179">Com suporte e mapeado para o nome do contrato de dados.</span><span class="sxs-lookup"><span data-stu-id="49e6e-179">Supported and mapped to the data contract name.</span></span> <span data-ttu-id="49e6e-180">Se houver períodos no nome, será feita uma tentativa de mapear o tipo para um tipo interno.</span><span class="sxs-lookup"><span data-stu-id="49e6e-180">If there are periods in the name, an attempt is made to map the type to an inner type.</span></span> <span data-ttu-id="49e6e-181">Por exemplo, um tipo complexo chamado é `A.B` mapeado para um tipo de contrato de dados que é um tipo interno de um tipo com o nome do contrato de dados `A` , mas somente se existir um tipo de contrato de dados.</span><span class="sxs-lookup"><span data-stu-id="49e6e-181">For example, a complex type named `A.B` maps to a data contract type that is an inner type of a type with the data contract name `A`, but only if such a data contract type exists.</span></span> <span data-ttu-id="49e6e-182">Mais de um nível de aninhamento é possível: por exemplo, `A.B.C` pode ser um tipo interno, mas somente se `A` e `A.B` ambos existirem.</span><span class="sxs-lookup"><span data-stu-id="49e6e-182">More than one level of nesting is possible: for example, `A.B.C` can be an inner type, but only if `A` and `A.B` both exist.</span></span>|

### <a name="xscomplextype-contents"></a><span data-ttu-id="49e6e-183">\<xs:complexType>: conteúdo</span><span class="sxs-lookup"><span data-stu-id="49e6e-183">\<xs:complexType>: contents</span></span>

|<span data-ttu-id="49e6e-184">Sumário</span><span class="sxs-lookup"><span data-stu-id="49e6e-184">Contents</span></span>|<span data-ttu-id="49e6e-185">Esquema</span><span class="sxs-lookup"><span data-stu-id="49e6e-185">Schema</span></span>|
|--------------|------------|
|`simpleContent`|<span data-ttu-id="49e6e-186">As extensões são proibidas.</span><span class="sxs-lookup"><span data-stu-id="49e6e-186">Extensions are forbidden.</span></span><br /><br /> <span data-ttu-id="49e6e-187">A restrição só é permitida a partir de `anySimpleType` .</span><span class="sxs-lookup"><span data-stu-id="49e6e-187">Restriction is allowed only from `anySimpleType`.</span></span>|
|`complexContent`|<span data-ttu-id="49e6e-188">Com suporte.</span><span class="sxs-lookup"><span data-stu-id="49e6e-188">Supported.</span></span> <span data-ttu-id="49e6e-189">Consulte "herança".</span><span class="sxs-lookup"><span data-stu-id="49e6e-189">See "Inheritance".</span></span>|
|`group`|<span data-ttu-id="49e6e-190">Negado.</span><span class="sxs-lookup"><span data-stu-id="49e6e-190">Forbidden.</span></span>|
|`all`|<span data-ttu-id="49e6e-191">Negado.</span><span class="sxs-lookup"><span data-stu-id="49e6e-191">Forbidden.</span></span>|
|`choice`|<span data-ttu-id="49e6e-192">Proibido</span><span class="sxs-lookup"><span data-stu-id="49e6e-192">Forbidden</span></span>|
|`sequence`|<span data-ttu-id="49e6e-193">Com suporte, mapeia para membros de dados de um contrato de dados.</span><span class="sxs-lookup"><span data-stu-id="49e6e-193">Supported, maps to data members of a data contract.</span></span>|
|`attribute`|<span data-ttu-id="49e6e-194">Proibido, mesmo que use = "proibido" (com uma exceção).</span><span class="sxs-lookup"><span data-stu-id="49e6e-194">Forbidden, even if use="prohibited" (with one exception).</span></span> <span data-ttu-id="49e6e-195">Há suporte apenas para atributos opcionais do namespace de esquema de serialização padrão.</span><span class="sxs-lookup"><span data-stu-id="49e6e-195">Only optional attributes from the Standard Serialization Schema namespace are supported.</span></span> <span data-ttu-id="49e6e-196">Eles não são mapeados para membros de dados no modelo de programação de contrato de dados.</span><span class="sxs-lookup"><span data-stu-id="49e6e-196">They do not map to data members in the data contract programming model.</span></span> <span data-ttu-id="49e6e-197">Atualmente, apenas um desses atributos tem significado e é discutido na seção ISerializable.</span><span class="sxs-lookup"><span data-stu-id="49e6e-197">Currently, only one such attribute has meaning and is discussed in the ISerializable section.</span></span> <span data-ttu-id="49e6e-198">Todos os outros são ignorados.</span><span class="sxs-lookup"><span data-stu-id="49e6e-198">All others are ignored.</span></span>|
|`attributeGroup`|<span data-ttu-id="49e6e-199">Negado.</span><span class="sxs-lookup"><span data-stu-id="49e6e-199">Forbidden.</span></span> <span data-ttu-id="49e6e-200">Na versão v1 do WCF, `DataContractSerializer` o ignora a presença de `attributeGroup` Inside `xs:complexType` .</span><span class="sxs-lookup"><span data-stu-id="49e6e-200">In the WCF v1 release, `DataContractSerializer` ignores the presence of `attributeGroup` inside `xs:complexType`.</span></span>|
|`anyAttribute`|<span data-ttu-id="49e6e-201">Negado.</span><span class="sxs-lookup"><span data-stu-id="49e6e-201">Forbidden.</span></span>|
|<span data-ttu-id="49e6e-202">(vazio)</span><span class="sxs-lookup"><span data-stu-id="49e6e-202">(empty)</span></span>|<span data-ttu-id="49e6e-203">Mapeia para um contrato de dados sem membros de dados.</span><span class="sxs-lookup"><span data-stu-id="49e6e-203">Maps to a data contract with no data members.</span></span>|

### <a name="xssequence-in-a-complex-type-attributes"></a><span data-ttu-id="49e6e-204">\<xs:sequence>em um tipo complexo: atributos</span><span class="sxs-lookup"><span data-stu-id="49e6e-204">\<xs:sequence> in a complex type: attributes</span></span>

|<span data-ttu-id="49e6e-205">Atributo</span><span class="sxs-lookup"><span data-stu-id="49e6e-205">Attribute</span></span>|<span data-ttu-id="49e6e-206">Esquema</span><span class="sxs-lookup"><span data-stu-id="49e6e-206">Schema</span></span>|
|---------------|------------|
|`id`|<span data-ttu-id="49e6e-207">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="49e6e-207">Ignored.</span></span>|
|`maxOccurs`|<span data-ttu-id="49e6e-208">Deve ser 1 (padrão).</span><span class="sxs-lookup"><span data-stu-id="49e6e-208">Must be 1 (default).</span></span>|
|`minOccurs`|<span data-ttu-id="49e6e-209">Deve ser 1 (padrão).</span><span class="sxs-lookup"><span data-stu-id="49e6e-209">Must be 1 (default).</span></span>|

### <a name="xssequence-in-a-complex-type-contents"></a><span data-ttu-id="49e6e-210">\<xs:sequence>em um tipo complexo: conteúdo</span><span class="sxs-lookup"><span data-stu-id="49e6e-210">\<xs:sequence> in a complex type: contents</span></span>

|<span data-ttu-id="49e6e-211">Sumário</span><span class="sxs-lookup"><span data-stu-id="49e6e-211">Contents</span></span>|<span data-ttu-id="49e6e-212">Esquema</span><span class="sxs-lookup"><span data-stu-id="49e6e-212">Schema</span></span>|
|--------------|------------|
|`element`|<span data-ttu-id="49e6e-213">Cada instância é mapeada para um membro de dados.</span><span class="sxs-lookup"><span data-stu-id="49e6e-213">Each instance maps to a data member.</span></span>|
|`group`|<span data-ttu-id="49e6e-214">Negado.</span><span class="sxs-lookup"><span data-stu-id="49e6e-214">Forbidden.</span></span>|
|`choice`|<span data-ttu-id="49e6e-215">Negado.</span><span class="sxs-lookup"><span data-stu-id="49e6e-215">Forbidden.</span></span>|
|`sequence`|<span data-ttu-id="49e6e-216">Negado.</span><span class="sxs-lookup"><span data-stu-id="49e6e-216">Forbidden.</span></span>|
|`any`|<span data-ttu-id="49e6e-217">Negado.</span><span class="sxs-lookup"><span data-stu-id="49e6e-217">Forbidden.</span></span>|
|<span data-ttu-id="49e6e-218">(vazio)</span><span class="sxs-lookup"><span data-stu-id="49e6e-218">(empty)</span></span>|<span data-ttu-id="49e6e-219">Mapeia para um contrato de dados sem membros de dados.</span><span class="sxs-lookup"><span data-stu-id="49e6e-219">Maps to a data contract with no data members.</span></span>|

## <a name="elements--xselement"></a><span data-ttu-id="49e6e-220">Elementos\<xs:element></span><span class="sxs-lookup"><span data-stu-id="49e6e-220">Elements – \<xs:element></span></span>

### <a name="general-information"></a><span data-ttu-id="49e6e-221">Informações gerais</span><span class="sxs-lookup"><span data-stu-id="49e6e-221">General Information</span></span>

<span data-ttu-id="49e6e-222">`<xs:element>`pode ocorrer nos seguintes contextos:</span><span class="sxs-lookup"><span data-stu-id="49e6e-222">`<xs:element>` can occur in the following contexts:</span></span>

- <span data-ttu-id="49e6e-223">Ele pode ocorrer em um `<xs:sequence>` , que descreve um membro de dados de um contrato de dados regular (não coleção).</span><span class="sxs-lookup"><span data-stu-id="49e6e-223">It can occur within an `<xs:sequence>`, which describes a data member of a regular (non-collection) data contract.</span></span> <span data-ttu-id="49e6e-224">Nesse caso, o `maxOccurs` atributo deve ser 1.</span><span class="sxs-lookup"><span data-stu-id="49e6e-224">In this case, the `maxOccurs` attribute must be 1.</span></span> <span data-ttu-id="49e6e-225">(Um valor de 0 não é permitido).</span><span class="sxs-lookup"><span data-stu-id="49e6e-225">(A value of 0 is not allowed).</span></span>

- <span data-ttu-id="49e6e-226">Ele pode ocorrer em um `<xs:sequence>` , que descreve um membro de dados de um contrato de dados de coleção.</span><span class="sxs-lookup"><span data-stu-id="49e6e-226">It can occur within an `<xs:sequence>`, which describes a data member of a collection data contract.</span></span> <span data-ttu-id="49e6e-227">Nesse caso, o `maxOccurs` atributo deve ser maior que 1 ou "não associado".</span><span class="sxs-lookup"><span data-stu-id="49e6e-227">In this case, the `maxOccurs` attribute must be greater than 1 or "unbounded".</span></span>

- <span data-ttu-id="49e6e-228">Ele pode ocorrer dentro de uma `<xs:schema>` como uma declaração de elemento global (teste).</span><span class="sxs-lookup"><span data-stu-id="49e6e-228">It can occur within an `<xs:schema>` as a Global Element Declaration (GED).</span></span>

### <a name="xselement-with-maxoccurs1-within-an-xssequence-data-members"></a><span data-ttu-id="49e6e-229">\<xs:element>com maxOccurs = 1 em um \<xs:sequence> (membros de dados)</span><span class="sxs-lookup"><span data-stu-id="49e6e-229">\<xs:element> with maxOccurs=1 within an \<xs:sequence> (Data Members)</span></span>

|<span data-ttu-id="49e6e-230">Atributo</span><span class="sxs-lookup"><span data-stu-id="49e6e-230">Attribute</span></span>|<span data-ttu-id="49e6e-231">Esquema</span><span class="sxs-lookup"><span data-stu-id="49e6e-231">Schema</span></span>|
|---------------|------------|
|`ref`|<span data-ttu-id="49e6e-232">Negado.</span><span class="sxs-lookup"><span data-stu-id="49e6e-232">Forbidden.</span></span>|
|`name`|<span data-ttu-id="49e6e-233">Com suporte, é mapeado para o nome do membro de dados.</span><span class="sxs-lookup"><span data-stu-id="49e6e-233">Supported, maps to the data member name.</span></span>|
|`type`|<span data-ttu-id="49e6e-234">Com suporte, mapeia para o tipo de membro de dados.</span><span class="sxs-lookup"><span data-stu-id="49e6e-234">Supported, maps to the data member type.</span></span> <span data-ttu-id="49e6e-235">Para obter mais informações, consulte mapeamento de tipo/primitivo.</span><span class="sxs-lookup"><span data-stu-id="49e6e-235">For more information, see Type/primitive mapping.</span></span> <span data-ttu-id="49e6e-236">Se não for especificado (e o elemento não contiver um tipo anônimo), `xs:anyType` será assumido.</span><span class="sxs-lookup"><span data-stu-id="49e6e-236">If not specified (and the element does not contain an anonymous type), `xs:anyType` is assumed.</span></span>|
|`block`|<span data-ttu-id="49e6e-237">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="49e6e-237">Ignored.</span></span>|
|`default`|<span data-ttu-id="49e6e-238">Negado.</span><span class="sxs-lookup"><span data-stu-id="49e6e-238">Forbidden.</span></span>|
|`fixed`|<span data-ttu-id="49e6e-239">Negado.</span><span class="sxs-lookup"><span data-stu-id="49e6e-239">Forbidden.</span></span>|
|`form`|<span data-ttu-id="49e6e-240">Deve ser qualificado.</span><span class="sxs-lookup"><span data-stu-id="49e6e-240">Must be qualified.</span></span> <span data-ttu-id="49e6e-241">Esse atributo pode ser definido por meio `elementFormDefault` de on `xs:schema` .</span><span class="sxs-lookup"><span data-stu-id="49e6e-241">This attribute can be set through `elementFormDefault` on `xs:schema`.</span></span>|
|`id`|<span data-ttu-id="49e6e-242">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="49e6e-242">Ignored.</span></span>|
|`maxOccurs`|<span data-ttu-id="49e6e-243">1</span><span class="sxs-lookup"><span data-stu-id="49e6e-243">1</span></span>|
|`minOccurs`|<span data-ttu-id="49e6e-244">Mapeia para a <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> propriedade de um membro de dados ( `IsRequired` é verdadeiro quando `minOccurs` é 1).</span><span class="sxs-lookup"><span data-stu-id="49e6e-244">Maps to the <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> property of a data member (`IsRequired` is true when `minOccurs` is 1).</span></span>|
|`nillable`|<span data-ttu-id="49e6e-245">Afeta o mapeamento de tipo.</span><span class="sxs-lookup"><span data-stu-id="49e6e-245">Affects type mapping.</span></span> <span data-ttu-id="49e6e-246">Consulte mapeamento de tipo/primitivo.</span><span class="sxs-lookup"><span data-stu-id="49e6e-246">See Type/primitive mapping.</span></span>|

### <a name="xselement-with-maxoccurs1-within-an-xssequence-collections"></a><span data-ttu-id="49e6e-247">\<xs:element>com maxOccurs>1 em um \<xs:sequence> (coleções)</span><span class="sxs-lookup"><span data-stu-id="49e6e-247">\<xs:element> with maxOccurs>1 within an \<xs:sequence> (Collections)</span></span>

- <span data-ttu-id="49e6e-248">Mapeia para um <xref:System.Runtime.Serialization.CollectionDataContractAttribute> .</span><span class="sxs-lookup"><span data-stu-id="49e6e-248">Maps to a <xref:System.Runtime.Serialization.CollectionDataContractAttribute>.</span></span>

- <span data-ttu-id="49e6e-249">Em tipos de coleção, apenas um xs: Element é permitido dentro de uma sequência xs:.</span><span class="sxs-lookup"><span data-stu-id="49e6e-249">In collection types, only one xs:element is allowed within an xs:sequence.</span></span>

 <span data-ttu-id="49e6e-250">As coleções podem ser dos seguintes tipos:</span><span class="sxs-lookup"><span data-stu-id="49e6e-250">Collections can be of the following types:</span></span>

- <span data-ttu-id="49e6e-251">Coleções regulares (por exemplo, matrizes).</span><span class="sxs-lookup"><span data-stu-id="49e6e-251">Regular collections (for example, arrays).</span></span>

- <span data-ttu-id="49e6e-252">Coleções de dicionário (mapeando um valor para outro; por exemplo, a <xref:System.Collections.Hashtable> ).</span><span class="sxs-lookup"><span data-stu-id="49e6e-252">Dictionary collections (mapping one value to another; for example, a <xref:System.Collections.Hashtable>).</span></span>

- <span data-ttu-id="49e6e-253">A única diferença entre um dicionário e uma matriz de um tipo de par chave/valor está no modelo de programação gerado.</span><span class="sxs-lookup"><span data-stu-id="49e6e-253">The only difference between a dictionary and an array of a key/value pair type is in the generated programming model.</span></span> <span data-ttu-id="49e6e-254">Há um mecanismo de anotação de esquema que pode ser usado para indicar que um determinado tipo é uma coleção de dicionários.</span><span class="sxs-lookup"><span data-stu-id="49e6e-254">There is a schema annotation mechanism that can be used to indicate that a given type is a dictionary collection.</span></span>

<span data-ttu-id="49e6e-255">As regras para os `ref` atributos,,,, `block` `default` `fixed` `form` e `id` são as mesmas para o caso não coleção.</span><span class="sxs-lookup"><span data-stu-id="49e6e-255">The rules for the `ref`, `block`, `default`, `fixed`, `form`, and `id` attributes are the same as for the non-collection case.</span></span> <span data-ttu-id="49e6e-256">Outros atributos incluem os da tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="49e6e-256">Other attributes include those in the following table.</span></span>

|<span data-ttu-id="49e6e-257">Atributo</span><span class="sxs-lookup"><span data-stu-id="49e6e-257">Attribute</span></span>|<span data-ttu-id="49e6e-258">Esquema</span><span class="sxs-lookup"><span data-stu-id="49e6e-258">Schema</span></span>|
|---------------|------------|
|`name`|<span data-ttu-id="49e6e-259">Com suporte, mapeia para a <xref:System.Runtime.Serialization.CollectionDataContractAttribute.ItemName%2A> propriedade no `CollectionDataContractAttribute` atributo.</span><span class="sxs-lookup"><span data-stu-id="49e6e-259">Supported, maps to the <xref:System.Runtime.Serialization.CollectionDataContractAttribute.ItemName%2A> property in the `CollectionDataContractAttribute` attribute.</span></span>|
|`type`|<span data-ttu-id="49e6e-260">Com suporte, é mapeado para o tipo armazenado na coleção.</span><span class="sxs-lookup"><span data-stu-id="49e6e-260">Supported, maps to the type stored in the collection.</span></span>|
|`maxOccurs`|<span data-ttu-id="49e6e-261">Maior que 1 ou "não associado".</span><span class="sxs-lookup"><span data-stu-id="49e6e-261">Greater than 1 or "unbounded".</span></span> <span data-ttu-id="49e6e-262">O esquema de DC deve usar "não associado".</span><span class="sxs-lookup"><span data-stu-id="49e6e-262">The DC schema should use "unbounded".</span></span>|
|`minOccurs`|<span data-ttu-id="49e6e-263">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="49e6e-263">Ignored.</span></span>|
|`nillable`|<span data-ttu-id="49e6e-264">Afeta o mapeamento de tipo.</span><span class="sxs-lookup"><span data-stu-id="49e6e-264">Affects type mapping.</span></span> <span data-ttu-id="49e6e-265">Esse atributo é ignorado para coleções de dicionário.</span><span class="sxs-lookup"><span data-stu-id="49e6e-265">This attribute is ignored for dictionary collections.</span></span>|

### <a name="xselement-within-an-xsschema-global-element-declaration"></a><span data-ttu-id="49e6e-266">\<xs:element>dentro de uma \<xs:schema> declaração de elemento global</span><span class="sxs-lookup"><span data-stu-id="49e6e-266">\<xs:element> within an \<xs:schema> Global Element Declaration</span></span>

- <span data-ttu-id="49e6e-267">Uma declaração de elemento global (teste) que tem o mesmo nome e namespace como um tipo no esquema, ou que define um tipo anônimo dentro dele mesmo, é considerada associada ao tipo.</span><span class="sxs-lookup"><span data-stu-id="49e6e-267">A Global Element Declaration (GED) that has the same name and namespace as a type in schema, or that defines an anonymous type inside itself, is said to be associated with the type.</span></span>

- <span data-ttu-id="49e6e-268">Exportação de esquema: os GEDs associados são gerados para cada tipo gerado, simples e complexo.</span><span class="sxs-lookup"><span data-stu-id="49e6e-268">Schema export: associated GEDs are generated for every generated type, both simple and complex.</span></span>

- <span data-ttu-id="49e6e-269">Desserialização/serialização: os GEDs associados são usados como elementos raiz para o tipo.</span><span class="sxs-lookup"><span data-stu-id="49e6e-269">Deserialization/serialization: associated GEDs are used as root elements for the type.</span></span>

- <span data-ttu-id="49e6e-270">Importação de esquema: os GEDs associados não são necessários e serão ignorados se seguirem as seguintes regras (a menos que eles definam tipos).</span><span class="sxs-lookup"><span data-stu-id="49e6e-270">Schema import: associated GEDs are not required and are ignored if they follow the following rules (unless they define types).</span></span>

|<span data-ttu-id="49e6e-271">Atributo</span><span class="sxs-lookup"><span data-stu-id="49e6e-271">Attribute</span></span>|<span data-ttu-id="49e6e-272">Esquema</span><span class="sxs-lookup"><span data-stu-id="49e6e-272">Schema</span></span>|
|---------------|------------|
|`abstract`|<span data-ttu-id="49e6e-273">Deve ser false para GEDs associados.</span><span class="sxs-lookup"><span data-stu-id="49e6e-273">Must be false for associated GEDs.</span></span>|
|`block`|<span data-ttu-id="49e6e-274">Proibido no GEDs associado.</span><span class="sxs-lookup"><span data-stu-id="49e6e-274">Forbidden in associated GEDs.</span></span>|
|`default`|<span data-ttu-id="49e6e-275">Proibido no GEDs associado.</span><span class="sxs-lookup"><span data-stu-id="49e6e-275">Forbidden in associated GEDs.</span></span>|
|`final`|<span data-ttu-id="49e6e-276">Deve ser false para GEDs associados.</span><span class="sxs-lookup"><span data-stu-id="49e6e-276">Must be false for associated GEDs.</span></span>|
|`fixed`|<span data-ttu-id="49e6e-277">Proibido no GEDs associado.</span><span class="sxs-lookup"><span data-stu-id="49e6e-277">Forbidden in associated GEDs.</span></span>|
|`id`|<span data-ttu-id="49e6e-278">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="49e6e-278">Ignored.</span></span>|
|`name`|<span data-ttu-id="49e6e-279">Com suporte.</span><span class="sxs-lookup"><span data-stu-id="49e6e-279">Supported.</span></span> <span data-ttu-id="49e6e-280">Consulte a definição de GEDs associada.</span><span class="sxs-lookup"><span data-stu-id="49e6e-280">See the definition of associated GEDs.</span></span>|
|`nillable`|<span data-ttu-id="49e6e-281">Deve ser verdadeiro para GEDs associados.</span><span class="sxs-lookup"><span data-stu-id="49e6e-281">Must be true for associated GEDs.</span></span>|
|`substitutionGroup`|<span data-ttu-id="49e6e-282">Proibido no GEDs associado.</span><span class="sxs-lookup"><span data-stu-id="49e6e-282">Forbidden in associated GEDs.</span></span>|
|`type`|<span data-ttu-id="49e6e-283">Com suporte, e deve corresponder ao tipo associado para GEDs associado (a menos que o elemento contenha um tipo anônimo).</span><span class="sxs-lookup"><span data-stu-id="49e6e-283">Supported, and must match the associated type for associated GEDs (unless the element contains an anonymous type).</span></span>|

### <a name="xselement-contents"></a><span data-ttu-id="49e6e-284">\<xs:element>: conteúdo</span><span class="sxs-lookup"><span data-stu-id="49e6e-284">\<xs:element>: contents</span></span>

|<span data-ttu-id="49e6e-285">Sumário</span><span class="sxs-lookup"><span data-stu-id="49e6e-285">Contents</span></span>|<span data-ttu-id="49e6e-286">Esquema</span><span class="sxs-lookup"><span data-stu-id="49e6e-286">Schema</span></span>|
|--------------|------------|
|`simpleType`|<span data-ttu-id="49e6e-287">Com suporte. \*</span><span class="sxs-lookup"><span data-stu-id="49e6e-287">Supported.\*</span></span>|
|`complexType`|<span data-ttu-id="49e6e-288">Com suporte. \*</span><span class="sxs-lookup"><span data-stu-id="49e6e-288">Supported.\*</span></span>|
|`unique`|<span data-ttu-id="49e6e-289">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="49e6e-289">Ignored.</span></span>|
|`key`|<span data-ttu-id="49e6e-290">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="49e6e-290">Ignored.</span></span>|
|`keyref`|<span data-ttu-id="49e6e-291">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="49e6e-291">Ignored.</span></span>|
|<span data-ttu-id="49e6e-292">(blank)</span><span class="sxs-lookup"><span data-stu-id="49e6e-292">(blank)</span></span>|<span data-ttu-id="49e6e-293">Com suporte.</span><span class="sxs-lookup"><span data-stu-id="49e6e-293">Supported.</span></span>|

<span data-ttu-id="49e6e-294">\*Ao usar o `simpleType` `complexType,` mapeamento e para tipos anônimos é o mesmo que para tipos não anônimos, exceto pelo fato de que não há nenhum contrato de dados anônimo e, portanto, um acordo de dados nomeado é criado, com um nome gerado derivado do nome do elemento.</span><span class="sxs-lookup"><span data-stu-id="49e6e-294">\* When using the `simpleType` and `complexType,` mapping for anonymous types is the same as for non-anonymous types, except that there is no anonymous data contracts, and so a named data contract is created, with a generated name derived from the element name.</span></span> <span data-ttu-id="49e6e-295">As regras para tipos anônimos estão na lista a seguir:</span><span class="sxs-lookup"><span data-stu-id="49e6e-295">The rules for anonymous types are in the following list:</span></span>

- <span data-ttu-id="49e6e-296">Detalhe da implementação do WCF: se o `xs:element` nome não contiver pontos, o tipo anônimo será mapeado para um tipo interno do tipo de contrato de dados externo.</span><span class="sxs-lookup"><span data-stu-id="49e6e-296">WCF implementation detail: If the `xs:element` name does not contain periods, the anonymous type maps to an inner type of the outer data contract type.</span></span> <span data-ttu-id="49e6e-297">Se o nome contiver pontos, o tipo de contrato de dados resultante será independente (não um tipo interno).</span><span class="sxs-lookup"><span data-stu-id="49e6e-297">If the name contains periods, the resulting data contract type is independent (not an inner type).</span></span>

- <span data-ttu-id="49e6e-298">O nome do contrato de dados gerado do tipo interno é o nome do contrato de dados do tipo externo seguido de um ponto, o nome do elemento e a cadeia de caracteres "tipo".</span><span class="sxs-lookup"><span data-stu-id="49e6e-298">The generated data contract name of the inner type is the data contract name of the outer type followed by a period, the name of the element, and the string "Type".</span></span>

- <span data-ttu-id="49e6e-299">Se já existir um contrato de dados com esse nome, o nome será exclusivo acrescentando "1", "2", "3" e assim por diante até que um nome exclusivo seja criado.</span><span class="sxs-lookup"><span data-stu-id="49e6e-299">If a data contract with such a name already exists, the name is made unique by appending "1", "2", "3", and so on until a unique name is created.</span></span>

## <a name="simple-types---xssimpletype"></a><span data-ttu-id="49e6e-300">Tipos simples-\<xs:simpleType></span><span class="sxs-lookup"><span data-stu-id="49e6e-300">Simple Types - \<xs:simpleType></span></span>

### <a name="xssimpletype-attributes"></a><span data-ttu-id="49e6e-301">\<xs:simpleType>: atributos</span><span class="sxs-lookup"><span data-stu-id="49e6e-301">\<xs:simpleType>: attributes</span></span>

|<span data-ttu-id="49e6e-302">Atributo</span><span class="sxs-lookup"><span data-stu-id="49e6e-302">Attribute</span></span>|<span data-ttu-id="49e6e-303">Esquema</span><span class="sxs-lookup"><span data-stu-id="49e6e-303">Schema</span></span>|
|---------------|------------|
|`final`|<span data-ttu-id="49e6e-304">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="49e6e-304">Ignored.</span></span>|
|`id`|<span data-ttu-id="49e6e-305">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="49e6e-305">Ignored.</span></span>|
|`name`|<span data-ttu-id="49e6e-306">Com suporte, é mapeado para o nome do contrato de dados.</span><span class="sxs-lookup"><span data-stu-id="49e6e-306">Supported, maps to the data contract name.</span></span>|

### <a name="xssimpletype-contents"></a><span data-ttu-id="49e6e-307">\<xs:simpleType>: conteúdo</span><span class="sxs-lookup"><span data-stu-id="49e6e-307">\<xs:simpleType>: contents</span></span>

|<span data-ttu-id="49e6e-308">Sumário</span><span class="sxs-lookup"><span data-stu-id="49e6e-308">Contents</span></span>|<span data-ttu-id="49e6e-309">Esquema</span><span class="sxs-lookup"><span data-stu-id="49e6e-309">Schema</span></span>|
|--------------|------------|
|`restriction`|<span data-ttu-id="49e6e-310">Com suporte.</span><span class="sxs-lookup"><span data-stu-id="49e6e-310">Supported.</span></span> <span data-ttu-id="49e6e-311">Mapeia para contratos de dados de enumeração.</span><span class="sxs-lookup"><span data-stu-id="49e6e-311">Maps to enumeration data contracts.</span></span> <span data-ttu-id="49e6e-312">Esse atributo será ignorado se não corresponder ao padrão de enumeração.</span><span class="sxs-lookup"><span data-stu-id="49e6e-312">This attribute is ignored if it does not match the enumeration pattern.</span></span> <span data-ttu-id="49e6e-313">Consulte a `xs:simpleType` seção restrições.</span><span class="sxs-lookup"><span data-stu-id="49e6e-313">See the `xs:simpleType` restrictions section.</span></span>|
|`list`|<span data-ttu-id="49e6e-314">Com suporte.</span><span class="sxs-lookup"><span data-stu-id="49e6e-314">Supported.</span></span> <span data-ttu-id="49e6e-315">Mapeia para sinalizar contratos de dados de enumeração.</span><span class="sxs-lookup"><span data-stu-id="49e6e-315">Maps to flag enumeration data contracts.</span></span> <span data-ttu-id="49e6e-316">Consulte a `xs:simpleType` seção listas.</span><span class="sxs-lookup"><span data-stu-id="49e6e-316">See the `xs:simpleType` lists section.</span></span>|
|`union`|<span data-ttu-id="49e6e-317">Negado.</span><span class="sxs-lookup"><span data-stu-id="49e6e-317">Forbidden.</span></span>|

### \<xs:restriction>

- <span data-ttu-id="49e6e-318">Há suporte para restrições de tipo complexo apenas para base = " `xs:anyType` ".</span><span class="sxs-lookup"><span data-stu-id="49e6e-318">Complex type restrictions are supported only for base="`xs:anyType`".</span></span>

- <span data-ttu-id="49e6e-319">Restrições de tipo simples de `xs:string` que não têm facetas de restrição diferentes de `xs:enumeration` são mapeadas para contratos de dados de enumeração.</span><span class="sxs-lookup"><span data-stu-id="49e6e-319">Simple type restrictions of `xs:string` that do not have any restriction facets other than `xs:enumeration` are mapped to enumeration data contracts.</span></span>

- <span data-ttu-id="49e6e-320">Todas as outras restrições de tipo simples são mapeadas para os tipos que elas restringem.</span><span class="sxs-lookup"><span data-stu-id="49e6e-320">All other simple type restrictions are mapped to the types they restrict.</span></span> <span data-ttu-id="49e6e-321">Por exemplo, uma restrição de `xs:int` é mapeada para um número inteiro, da mesma forma como `xs:int` faz.</span><span class="sxs-lookup"><span data-stu-id="49e6e-321">For example, a restriction of `xs:int` maps to an integer, just as `xs:int` itself does.</span></span> <span data-ttu-id="49e6e-322">Para obter mais informações sobre mapeamento de tipo primitivo, consulte mapeamento de tipo/primitivo.</span><span class="sxs-lookup"><span data-stu-id="49e6e-322">For more information about primitive type mapping, see Type/primitive mapping.</span></span>

### <a name="xsrestriction-attributes"></a><span data-ttu-id="49e6e-323">\<xs:restriction>: atributos</span><span class="sxs-lookup"><span data-stu-id="49e6e-323">\<xs:restriction>: attributes</span></span>

|<span data-ttu-id="49e6e-324">Atributo</span><span class="sxs-lookup"><span data-stu-id="49e6e-324">Attribute</span></span>|<span data-ttu-id="49e6e-325">Esquema</span><span class="sxs-lookup"><span data-stu-id="49e6e-325">Schema</span></span>|
|---------------|------------|
|`base`|<span data-ttu-id="49e6e-326">Deve ser um tipo simples com suporte ou `xs:anyType` .</span><span class="sxs-lookup"><span data-stu-id="49e6e-326">Must be a supported simple type or `xs:anyType`.</span></span>|
|`id`|<span data-ttu-id="49e6e-327">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="49e6e-327">Ignored.</span></span>|

### <a name="xsrestriction-for-all-other-cases-contents"></a><span data-ttu-id="49e6e-328">\<xs:restriction>para todos os outros casos: conteúdo</span><span class="sxs-lookup"><span data-stu-id="49e6e-328">\<xs:restriction> for all other cases: contents</span></span>

|<span data-ttu-id="49e6e-329">Sumário</span><span class="sxs-lookup"><span data-stu-id="49e6e-329">Contents</span></span>|<span data-ttu-id="49e6e-330">Esquema</span><span class="sxs-lookup"><span data-stu-id="49e6e-330">Schema</span></span>|
|--------------|------------|
|`simpleType`|<span data-ttu-id="49e6e-331">Se presente, deve ser derivado de um tipo primitivo com suporte.</span><span class="sxs-lookup"><span data-stu-id="49e6e-331">If present, must be derived from a supported primitive type.</span></span>|
|`minExclusive`|<span data-ttu-id="49e6e-332">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="49e6e-332">Ignored.</span></span>|
|`minInclusive`|<span data-ttu-id="49e6e-333">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="49e6e-333">Ignored.</span></span>|
|`maxExclusive`|<span data-ttu-id="49e6e-334">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="49e6e-334">Ignored.</span></span>|
|`maxInclusive`|<span data-ttu-id="49e6e-335">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="49e6e-335">Ignored.</span></span>|
|`totalDigits`|<span data-ttu-id="49e6e-336">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="49e6e-336">Ignored.</span></span>|
|`fractionDigits`|<span data-ttu-id="49e6e-337">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="49e6e-337">Ignored.</span></span>|
|`length`|<span data-ttu-id="49e6e-338">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="49e6e-338">Ignored.</span></span>|
|`minLength`|<span data-ttu-id="49e6e-339">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="49e6e-339">Ignored.</span></span>|
|`maxLength`|<span data-ttu-id="49e6e-340">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="49e6e-340">Ignored.</span></span>|
|`enumeration`|<span data-ttu-id="49e6e-341">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="49e6e-341">Ignored.</span></span>|
|`whiteSpace`|<span data-ttu-id="49e6e-342">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="49e6e-342">Ignored.</span></span>|
|`pattern`|<span data-ttu-id="49e6e-343">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="49e6e-343">Ignored.</span></span>|
|<span data-ttu-id="49e6e-344">(blank)</span><span class="sxs-lookup"><span data-stu-id="49e6e-344">(blank)</span></span>|<span data-ttu-id="49e6e-345">Com suporte.</span><span class="sxs-lookup"><span data-stu-id="49e6e-345">Supported.</span></span>|

## <a name="enumeration"></a><span data-ttu-id="49e6e-346">Enumeração</span><span class="sxs-lookup"><span data-stu-id="49e6e-346">Enumeration</span></span>

### <a name="xsrestriction-for-enumerations-attributes"></a><span data-ttu-id="49e6e-347">\<xs:restriction>para enumerações: atributos</span><span class="sxs-lookup"><span data-stu-id="49e6e-347">\<xs:restriction> for enumerations: attributes</span></span>

|<span data-ttu-id="49e6e-348">Atributo</span><span class="sxs-lookup"><span data-stu-id="49e6e-348">Attribute</span></span>|<span data-ttu-id="49e6e-349">Esquema</span><span class="sxs-lookup"><span data-stu-id="49e6e-349">Schema</span></span>|
|---------------|------------|
|`base`|<span data-ttu-id="49e6e-350">Se presente, deve ser `xs:string` .</span><span class="sxs-lookup"><span data-stu-id="49e6e-350">If present, must be `xs:string`.</span></span>|
|`id`|<span data-ttu-id="49e6e-351">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="49e6e-351">Ignored.</span></span>|

### <a name="xsrestriction-for-enumerations-contents"></a><span data-ttu-id="49e6e-352">\<xs:restriction>para enumerações: conteúdo</span><span class="sxs-lookup"><span data-stu-id="49e6e-352">\<xs:restriction> for enumerations: contents</span></span>

|<span data-ttu-id="49e6e-353">Sumário</span><span class="sxs-lookup"><span data-stu-id="49e6e-353">Contents</span></span>|<span data-ttu-id="49e6e-354">Esquema</span><span class="sxs-lookup"><span data-stu-id="49e6e-354">Schema</span></span>|
|--------------|------------|
|`simpleType`|<span data-ttu-id="49e6e-355">Se presente, deve ser uma restrição de enumeração com suporte do contrato de dados (esta seção).</span><span class="sxs-lookup"><span data-stu-id="49e6e-355">If present, must be an enumeration restriction supported by the data contract (this section).</span></span>|
|`minExclusive`|<span data-ttu-id="49e6e-356">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="49e6e-356">Ignored.</span></span>|
|`minInclusive`|<span data-ttu-id="49e6e-357">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="49e6e-357">Ignored.</span></span>|
|`maxExclusive`|<span data-ttu-id="49e6e-358">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="49e6e-358">Ignored.</span></span>|
|`maxInclusive`|<span data-ttu-id="49e6e-359">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="49e6e-359">Ignored.</span></span>|
|`totalDigits`|<span data-ttu-id="49e6e-360">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="49e6e-360">Ignored.</span></span>|
|`fractionDigits`|<span data-ttu-id="49e6e-361">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="49e6e-361">Ignored.</span></span>|
|`length`|<span data-ttu-id="49e6e-362">Negado.</span><span class="sxs-lookup"><span data-stu-id="49e6e-362">Forbidden.</span></span>|
|`minLength`|<span data-ttu-id="49e6e-363">Negado.</span><span class="sxs-lookup"><span data-stu-id="49e6e-363">Forbidden.</span></span>|
|`maxLength`|<span data-ttu-id="49e6e-364">Negado.</span><span class="sxs-lookup"><span data-stu-id="49e6e-364">Forbidden.</span></span>|
|`enumeration`|<span data-ttu-id="49e6e-365">Com suporte.</span><span class="sxs-lookup"><span data-stu-id="49e6e-365">Supported.</span></span> <span data-ttu-id="49e6e-366">A enumeração "ID" é ignorada e "valor" é mapeado para o nome do valor no contrato de dados de enumeração.</span><span class="sxs-lookup"><span data-stu-id="49e6e-366">Enumeration "id" is ignored, and "value" maps to the value name in the enumeration data contract.</span></span>|
|`whiteSpace`|<span data-ttu-id="49e6e-367">Negado.</span><span class="sxs-lookup"><span data-stu-id="49e6e-367">Forbidden.</span></span>|
|`pattern`|<span data-ttu-id="49e6e-368">Negado.</span><span class="sxs-lookup"><span data-stu-id="49e6e-368">Forbidden.</span></span>|
|<span data-ttu-id="49e6e-369">(vazio)</span><span class="sxs-lookup"><span data-stu-id="49e6e-369">(empty)</span></span>|<span data-ttu-id="49e6e-370">Com suporte, mapeia para o tipo de enumeração vazio.</span><span class="sxs-lookup"><span data-stu-id="49e6e-370">Supported, maps to empty enumeration type.</span></span>|

 <span data-ttu-id="49e6e-371">O código a seguir mostra uma classe de enumeração C#.</span><span class="sxs-lookup"><span data-stu-id="49e6e-371">The following code shows a C# enumeration class.</span></span>

```csharp
public enum MyEnum
{
  first = 3,
  second = 4,
  third =5
}
```

<span data-ttu-id="49e6e-372">Essa classe é mapeada para o esquema a seguir pelo `DataContractSerializer` .</span><span class="sxs-lookup"><span data-stu-id="49e6e-372">This class maps to the following schema by the `DataContractSerializer`.</span></span> <span data-ttu-id="49e6e-373">Se os valores de enumeração começarem de 1, os `xs:annotation` blocos não serão gerados.</span><span class="sxs-lookup"><span data-stu-id="49e6e-373">If enumeration values start from 1, `xs:annotation` blocks are not generated.</span></span>

```xml
<xs:simpleType name="MyEnum">
  <xs:restriction base="xs:string">
    <xs:enumeration value="first">
      <xs:annotation>
        <xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">
          3
          </EnumerationValue>
        </xs:appinfo>
      </xs:annotation>
    </xs:enumeration>
    <xs:enumeration value="second">
      <xs:annotation>
        <xs:appinfo>
          <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">
          4
          </EnumerationValue>
        </xs:appinfo>
      </xs:annotation>
    </xs:enumeration>
  </xs:restriction>
</xs:simpleType>
```

### \<xs:list>

<span data-ttu-id="49e6e-374">`DataContractSerializer`mapeia tipos de enumeração marcados com `System.FlagsAttribute` para `xs:list` derivado de `xs:string` .</span><span class="sxs-lookup"><span data-stu-id="49e6e-374">`DataContractSerializer` maps enumeration types marked with `System.FlagsAttribute` to `xs:list` derived from `xs:string`.</span></span> <span data-ttu-id="49e6e-375">Não há `xs:list` suporte para nenhuma outra variação.</span><span class="sxs-lookup"><span data-stu-id="49e6e-375">No other `xs:list` variations are supported.</span></span>

### <a name="xslist-attributes"></a><span data-ttu-id="49e6e-376">\<xs:list>: atributos</span><span class="sxs-lookup"><span data-stu-id="49e6e-376">\<xs:list>: attributes</span></span>

|<span data-ttu-id="49e6e-377">Atributo</span><span class="sxs-lookup"><span data-stu-id="49e6e-377">Attribute</span></span>|<span data-ttu-id="49e6e-378">Esquema</span><span class="sxs-lookup"><span data-stu-id="49e6e-378">Schema</span></span>|
|---------------|------------|
|`itemType`|<span data-ttu-id="49e6e-379">Negado.</span><span class="sxs-lookup"><span data-stu-id="49e6e-379">Forbidden.</span></span>|
|`id`|<span data-ttu-id="49e6e-380">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="49e6e-380">Ignored.</span></span>|

### <a name="xslist-contents"></a><span data-ttu-id="49e6e-381">\<xs:list>: conteúdo</span><span class="sxs-lookup"><span data-stu-id="49e6e-381">\<xs:list>: contents</span></span>

|<span data-ttu-id="49e6e-382">Sumário</span><span class="sxs-lookup"><span data-stu-id="49e6e-382">Contents</span></span>|<span data-ttu-id="49e6e-383">Esquema</span><span class="sxs-lookup"><span data-stu-id="49e6e-383">Schema</span></span>|
|--------------|------------|
|`simpleType`|<span data-ttu-id="49e6e-384">Deve ser restrição do `xs:string` uso da `xs:enumeration` faceta.</span><span class="sxs-lookup"><span data-stu-id="49e6e-384">Must be restriction from `xs:string` using `xs:enumeration` facet.</span></span>|

<span data-ttu-id="49e6e-385">Se o valor de enumeração não seguir uma potência de 2 progressão (padrão para sinalizadores), o valor será armazenado no `xs:annotation/xs:appInfo/ser:EnumerationValue` elemento.</span><span class="sxs-lookup"><span data-stu-id="49e6e-385">If enumeration value does not follow a power of 2 progression (default for Flags), the value is stored in the `xs:annotation/xs:appInfo/ser:EnumerationValue` element.</span></span>

<span data-ttu-id="49e6e-386">Por exemplo, o código a seguir sinaliza um tipo de enumeração.</span><span class="sxs-lookup"><span data-stu-id="49e6e-386">For example, the following code flags an enumeration type.</span></span>

```csharp
[Flags]
public enum AuthFlags
{
  AuthAnonymous = 1,
  AuthBasic = 2,
  AuthNTLM = 4,
  AuthMD5 = 16,
  AuthWindowsLiveID = 64,
}
```

<span data-ttu-id="49e6e-387">Esse tipo é mapeado para o esquema a seguir.</span><span class="sxs-lookup"><span data-stu-id="49e6e-387">This type maps to the following schema.</span></span>

```xml
<xs:simpleType name="AuthFlags">
    <xs:list>
      <xs:simpleType>
        <xs:restriction base="xs:string">
          <xs:enumeration value="AuthAnonymous" />
          <xs:enumeration value="AuthBasic" />
          <xs:enumeration value="AuthNTLM" />
          <xs:enumeration value="AuthMD5">
            <xs:annotation>
              <xs:appinfo>
                <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">16</EnumerationValue>
              </xs:appinfo>
            </xs:annotation>
          </xs:enumeration>
          <xs:enumeration value="AuthWindowsLiveID">
            <xs:annotation>
              <xs:appinfo>
                <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Serialization/">64</EnumerationValue>
              </xs:appinfo>
            </xs:annotation>
          </xs:enumeration>
        </xs:restriction>
      </xs:simpleType>
    </xs:list>
  </xs:simpleType>
```

## <a name="inheritance"></a><span data-ttu-id="49e6e-388">Herança</span><span class="sxs-lookup"><span data-stu-id="49e6e-388">Inheritance</span></span>

### <a name="general-rules"></a><span data-ttu-id="49e6e-389">Regras gerais</span><span class="sxs-lookup"><span data-stu-id="49e6e-389">General rules</span></span>

<span data-ttu-id="49e6e-390">Um contrato de dados pode herdar de outro contrato de dados.</span><span class="sxs-lookup"><span data-stu-id="49e6e-390">A data contract can inherit from another data contract.</span></span> <span data-ttu-id="49e6e-391">Esses contratos de dados são mapeados para uma base e são derivados por tipos de extensão usando a `<xs:extension>` construção de esquema XML.</span><span class="sxs-lookup"><span data-stu-id="49e6e-391">Such data contracts map to a base and are derived by extension types using the `<xs:extension>` XML Schema construct.</span></span>

<span data-ttu-id="49e6e-392">Um contrato de dados não pode herdar de um contrato de dados de coleção.</span><span class="sxs-lookup"><span data-stu-id="49e6e-392">A data contract cannot inherit from a collection data contract.</span></span>

<span data-ttu-id="49e6e-393">Por exemplo, o código a seguir é um contrato de dados.</span><span class="sxs-lookup"><span data-stu-id="49e6e-393">For example, the following code is a data contract.</span></span>

```csharp
[DataContract]
public class Person
{
  [DataMember]
  public string Name;
}
[DataContract]
public class Employee : Person
{
  [DataMember]
  public int ID;
}
```

<span data-ttu-id="49e6e-394">Este contrato de dados é mapeado para a seguinte declaração de tipo de esquema XML.</span><span class="sxs-lookup"><span data-stu-id="49e6e-394">This data contract maps to the following XML Schema type declaration.</span></span>

```xml
<xs:complexType name="Employee">
 <xs:complexContent mixed="false">
  <xs:extension base="tns:Person">
   <xs:sequence>
    <xs:element minOccurs="0" name="ID" type="xs:int"/>
   </xs:sequence>
  </xs:extension>
 </xs:complexContent>
</xs:complexType>
<xs:complexType name="Person">
 <xs:sequence>
  <xs:element minOccurs="0" name="Name"
    nillable="true" type="xs:string"/>
 </xs:sequence>
</xs:complexType>
```

### <a name="xscomplexcontent-attributes"></a><span data-ttu-id="49e6e-395">\<xs:complexContent>: atributos</span><span class="sxs-lookup"><span data-stu-id="49e6e-395">\<xs:complexContent>: attributes</span></span>

|<span data-ttu-id="49e6e-396">Atributo</span><span class="sxs-lookup"><span data-stu-id="49e6e-396">Attribute</span></span>|<span data-ttu-id="49e6e-397">Esquema</span><span class="sxs-lookup"><span data-stu-id="49e6e-397">Schema</span></span>|
|---------------|------------|
|`id`|<span data-ttu-id="49e6e-398">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="49e6e-398">Ignored.</span></span>|
|`mixed`|<span data-ttu-id="49e6e-399">Deve ser false.</span><span class="sxs-lookup"><span data-stu-id="49e6e-399">Must be false.</span></span>|

### <a name="xscomplexcontent-contents"></a><span data-ttu-id="49e6e-400">\<xs:complexContent>: conteúdo</span><span class="sxs-lookup"><span data-stu-id="49e6e-400">\<xs:complexContent>: contents</span></span>

|<span data-ttu-id="49e6e-401">Sumário</span><span class="sxs-lookup"><span data-stu-id="49e6e-401">Contents</span></span>|<span data-ttu-id="49e6e-402">Esquema</span><span class="sxs-lookup"><span data-stu-id="49e6e-402">Schema</span></span>|
|--------------|------------|
|`restriction`|<span data-ttu-id="49e6e-403">Proibido, exceto quando base = " `xs:anyType` ".</span><span class="sxs-lookup"><span data-stu-id="49e6e-403">Forbidden, except when base="`xs:anyType`".</span></span> <span data-ttu-id="49e6e-404">O último é equivalente a colocar o conteúdo do `xs:restriction` diretamente sob o contêiner do `xs:complexContent` .</span><span class="sxs-lookup"><span data-stu-id="49e6e-404">The latter is equivalent to placing the content of the `xs:restriction` directly under the container of the `xs:complexContent`.</span></span>|
|`extension`|<span data-ttu-id="49e6e-405">Com suporte.</span><span class="sxs-lookup"><span data-stu-id="49e6e-405">Supported.</span></span> <span data-ttu-id="49e6e-406">Mapeia para herança de contrato de dados.</span><span class="sxs-lookup"><span data-stu-id="49e6e-406">Maps to data contract inheritance.</span></span>|

### <a name="xsextension-in-xscomplexcontent-attributes"></a><span data-ttu-id="49e6e-407">\<xs:extension>em \<xs:complexContent> : atributos</span><span class="sxs-lookup"><span data-stu-id="49e6e-407">\<xs:extension> in \<xs:complexContent>: attributes</span></span>

|<span data-ttu-id="49e6e-408">Atributo</span><span class="sxs-lookup"><span data-stu-id="49e6e-408">Attribute</span></span>|<span data-ttu-id="49e6e-409">Esquema</span><span class="sxs-lookup"><span data-stu-id="49e6e-409">Schema</span></span>|
|---------------|------------|
|`id`|<span data-ttu-id="49e6e-410">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="49e6e-410">Ignored.</span></span>|
|`base`|<span data-ttu-id="49e6e-411">Com suporte.</span><span class="sxs-lookup"><span data-stu-id="49e6e-411">Supported.</span></span> <span data-ttu-id="49e6e-412">Mapeia para o tipo de contrato de dados base do qual este tipo herda.</span><span class="sxs-lookup"><span data-stu-id="49e6e-412">Maps to the base data contract type that this type inherits from.</span></span>|

### <a name="xsextension-in-xscomplexcontent-contents"></a><span data-ttu-id="49e6e-413">\<xs:extension>em \<xs:complexContent> : conteúdo</span><span class="sxs-lookup"><span data-stu-id="49e6e-413">\<xs:extension> in \<xs:complexContent>: contents</span></span>

<span data-ttu-id="49e6e-414">As regras são as mesmas para o `<xs:complexType>` conteúdo.</span><span class="sxs-lookup"><span data-stu-id="49e6e-414">The rules are the same as for `<xs:complexType>` contents.</span></span>

<span data-ttu-id="49e6e-415">Se um `<xs:sequence>` for fornecido, seus elementos de membro serão mapeados para membros de dados adicionais que estão presentes no contrato de dados derivado.</span><span class="sxs-lookup"><span data-stu-id="49e6e-415">If an `<xs:sequence>` is provided, its member elements map to additional data members that are present in the derived data contract.</span></span>

<span data-ttu-id="49e6e-416">Se um tipo derivado contiver um elemento com o mesmo nome de um elemento em um tipo base, a declaração de elemento duplicado será mapeada para um membro de dados com um nome que é gerado para ser exclusivo.</span><span class="sxs-lookup"><span data-stu-id="49e6e-416">If a derived type contains an element with the same name as an element in a base type, the duplicate element declaration maps to a data member with a name that is generated to be unique.</span></span> <span data-ttu-id="49e6e-417">Números inteiros positivos são adicionados ao nome do membro de dados ("member1", "membro2" e assim por diante) até que um nome exclusivo seja encontrado.</span><span class="sxs-lookup"><span data-stu-id="49e6e-417">Positive integer numbers are added to the data member name ("member1", "member2", and so on) until a unique name is found.</span></span> <span data-ttu-id="49e6e-418">Por outro lado</span><span class="sxs-lookup"><span data-stu-id="49e6e-418">Conversely:</span></span>

- <span data-ttu-id="49e6e-419">Se um contrato de dados derivado tiver um membro de dados com o mesmo nome e tipo como um membro de dados em um contrato de dados base, o `DataContractSerializer` gerará esse elemento correspondente no tipo derivado.</span><span class="sxs-lookup"><span data-stu-id="49e6e-419">If a derived data contract has a data member with the same name and type as a data member in a base data contract, `DataContractSerializer` generates this corresponding element in the derived type.</span></span>

- <span data-ttu-id="49e6e-420">Se um contrato de dados derivado tiver um membro de dados com o mesmo nome que um membro de dados em um contrato de dados base, mas um tipo diferente, o `DataContractSerializer` importará um esquema com um elemento do tipo `xs:anyType` no tipo base e nas declarações de tipo derivado.</span><span class="sxs-lookup"><span data-stu-id="49e6e-420">If a derived data contract has a data member with the same name as a data member in a base data contract but a different type, the `DataContractSerializer` imports a schema with an element of the type `xs:anyType` in both base type and derived type declarations.</span></span> <span data-ttu-id="49e6e-421">O nome do tipo original é preservado em `xs:annotations/xs:appInfo/ser:ActualType/@Name` .</span><span class="sxs-lookup"><span data-stu-id="49e6e-421">The original type name is preserved in `xs:annotations/xs:appInfo/ser:ActualType/@Name`.</span></span>

<span data-ttu-id="49e6e-422">Ambas as variações podem levar a um esquema com um modelo de conteúdo ambíguo, que depende da ordem dos respectivos membros de dados.</span><span class="sxs-lookup"><span data-stu-id="49e6e-422">Both variations may lead to a schema with an ambiguous content model, which depends on the order of the respective data members.</span></span>

## <a name="typeprimitive-mapping"></a><span data-ttu-id="49e6e-423">Mapeamento de tipo/primitivo</span><span class="sxs-lookup"><span data-stu-id="49e6e-423">Type/primitive mapping</span></span>

<span data-ttu-id="49e6e-424">O `DataContractSerializer` usa o mapeamento a seguir para tipos primitivos de esquema XML.</span><span class="sxs-lookup"><span data-stu-id="49e6e-424">The `DataContractSerializer` uses the following mapping for XML Schema primitive types.</span></span>

|<span data-ttu-id="49e6e-425">Tipo XSD</span><span class="sxs-lookup"><span data-stu-id="49e6e-425">XSD type</span></span>|<span data-ttu-id="49e6e-426">Tipo .NET</span><span class="sxs-lookup"><span data-stu-id="49e6e-426">.NET type</span></span>|
|--------------|---------------|
|`anyType`|<span data-ttu-id="49e6e-427"><xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="49e6e-427"><xref:System.Object>.</span></span>|
|`anySimpleType`|<span data-ttu-id="49e6e-428"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="49e6e-428"><xref:System.String>.</span></span>|
|`duration`|<span data-ttu-id="49e6e-429"><xref:System.TimeSpan>.</span><span class="sxs-lookup"><span data-stu-id="49e6e-429"><xref:System.TimeSpan>.</span></span>|
|`dateTime`|<span data-ttu-id="49e6e-430"><xref:System.DateTime>.</span><span class="sxs-lookup"><span data-stu-id="49e6e-430"><xref:System.DateTime>.</span></span>|
|`dateTimeOffset`|<span data-ttu-id="49e6e-431"><xref:System.DateTime>e <xref:System.TimeSpan> para o deslocamento.</span><span class="sxs-lookup"><span data-stu-id="49e6e-431"><xref:System.DateTime> and <xref:System.TimeSpan> for the offset.</span></span> <span data-ttu-id="49e6e-432">Consulte a serialização de DateTimeOffset abaixo.</span><span class="sxs-lookup"><span data-stu-id="49e6e-432">See DateTimeOffset Serialization below.</span></span>|
|`time`|<span data-ttu-id="49e6e-433"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="49e6e-433"><xref:System.String>.</span></span>|
|`date`|<span data-ttu-id="49e6e-434"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="49e6e-434"><xref:System.String>.</span></span>|
|`gYearMonth`|<span data-ttu-id="49e6e-435"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="49e6e-435"><xref:System.String>.</span></span>|
|`gYear`|<span data-ttu-id="49e6e-436"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="49e6e-436"><xref:System.String>.</span></span>|
|`gMonthDay`|<span data-ttu-id="49e6e-437"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="49e6e-437"><xref:System.String>.</span></span>|
|`gDay`|<span data-ttu-id="49e6e-438"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="49e6e-438"><xref:System.String>.</span></span>|
|`gMonth`|<span data-ttu-id="49e6e-439"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="49e6e-439"><xref:System.String>.</span></span>|
|`boolean`|<xref:System.Boolean>|
|`base64Binary`|<span data-ttu-id="49e6e-440">Matriz <xref:System.Byte>.</span><span class="sxs-lookup"><span data-stu-id="49e6e-440"><xref:System.Byte> array.</span></span>|
|`hexBinary`|<span data-ttu-id="49e6e-441"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="49e6e-441"><xref:System.String>.</span></span>|
|`float`|<span data-ttu-id="49e6e-442"><xref:System.Single>.</span><span class="sxs-lookup"><span data-stu-id="49e6e-442"><xref:System.Single>.</span></span>|
|`double`|<span data-ttu-id="49e6e-443"><xref:System.Double>.</span><span class="sxs-lookup"><span data-stu-id="49e6e-443"><xref:System.Double>.</span></span>|
|`anyURI`|<span data-ttu-id="49e6e-444"><xref:System.Uri>.</span><span class="sxs-lookup"><span data-stu-id="49e6e-444"><xref:System.Uri>.</span></span>|
|`QName`|<span data-ttu-id="49e6e-445"><xref:System.Xml.XmlQualifiedName>.</span><span class="sxs-lookup"><span data-stu-id="49e6e-445"><xref:System.Xml.XmlQualifiedName>.</span></span>|
|`string`|<span data-ttu-id="49e6e-446"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="49e6e-446"><xref:System.String>.</span></span>|
|`normalizedString`|<span data-ttu-id="49e6e-447"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="49e6e-447"><xref:System.String>.</span></span>|
|`token`|<span data-ttu-id="49e6e-448"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="49e6e-448"><xref:System.String>.</span></span>|
|`language`|<span data-ttu-id="49e6e-449"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="49e6e-449"><xref:System.String>.</span></span>|
|`Name`|<span data-ttu-id="49e6e-450"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="49e6e-450"><xref:System.String>.</span></span>|
|`NCName`|<span data-ttu-id="49e6e-451"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="49e6e-451"><xref:System.String>.</span></span>|
|`ID`|<span data-ttu-id="49e6e-452"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="49e6e-452"><xref:System.String>.</span></span>|
|`IDREF`|<span data-ttu-id="49e6e-453"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="49e6e-453"><xref:System.String>.</span></span>|
|`IDREFS`|<span data-ttu-id="49e6e-454"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="49e6e-454"><xref:System.String>.</span></span>|
|`ENTITY`|<span data-ttu-id="49e6e-455"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="49e6e-455"><xref:System.String>.</span></span>|
|`ENTITIES`|<span data-ttu-id="49e6e-456"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="49e6e-456"><xref:System.String>.</span></span>|
|`NMTOKEN`|<span data-ttu-id="49e6e-457"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="49e6e-457"><xref:System.String>.</span></span>|
|`NMTOKENS`|<span data-ttu-id="49e6e-458"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="49e6e-458"><xref:System.String>.</span></span>|
|`decimal`|<span data-ttu-id="49e6e-459"><xref:System.Decimal>.</span><span class="sxs-lookup"><span data-stu-id="49e6e-459"><xref:System.Decimal>.</span></span>|
|`integer`|<span data-ttu-id="49e6e-460"><xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="49e6e-460"><xref:System.Int64>.</span></span>|
|`nonPositiveInteger`|<span data-ttu-id="49e6e-461"><xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="49e6e-461"><xref:System.Int64>.</span></span>|
|`negativeInteger`|<span data-ttu-id="49e6e-462"><xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="49e6e-462"><xref:System.Int64>.</span></span>|
|`long`|<span data-ttu-id="49e6e-463"><xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="49e6e-463"><xref:System.Int64>.</span></span>|
|`int`|<span data-ttu-id="49e6e-464"><xref:System.Int32>.</span><span class="sxs-lookup"><span data-stu-id="49e6e-464"><xref:System.Int32>.</span></span>|
|`short`|<span data-ttu-id="49e6e-465"><xref:System.Int16>.</span><span class="sxs-lookup"><span data-stu-id="49e6e-465"><xref:System.Int16>.</span></span>|
|`Byte`|<span data-ttu-id="49e6e-466"><xref:System.SByte>.</span><span class="sxs-lookup"><span data-stu-id="49e6e-466"><xref:System.SByte>.</span></span>|
|`nonNegativeInteger`|<span data-ttu-id="49e6e-467"><xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="49e6e-467"><xref:System.Int64>.</span></span>|
|`unsignedLong`|<span data-ttu-id="49e6e-468"><xref:System.UInt64>.</span><span class="sxs-lookup"><span data-stu-id="49e6e-468"><xref:System.UInt64>.</span></span>|
|`unsignedInt`|<span data-ttu-id="49e6e-469"><xref:System.UInt32>.</span><span class="sxs-lookup"><span data-stu-id="49e6e-469"><xref:System.UInt32>.</span></span>|
|`unsignedShort`|<span data-ttu-id="49e6e-470"><xref:System.UInt16>.</span><span class="sxs-lookup"><span data-stu-id="49e6e-470"><xref:System.UInt16>.</span></span>|
|`unsignedByte`|<span data-ttu-id="49e6e-471"><xref:System.Byte>.</span><span class="sxs-lookup"><span data-stu-id="49e6e-471"><xref:System.Byte>.</span></span>|
|`positiveInteger`|<span data-ttu-id="49e6e-472"><xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="49e6e-472"><xref:System.Int64>.</span></span>|

## <a name="iserializable-types-mapping"></a><span data-ttu-id="49e6e-473">Mapeamento de tipos ISerializable</span><span class="sxs-lookup"><span data-stu-id="49e6e-473">ISerializable types mapping</span></span>

<span data-ttu-id="49e6e-474">No .NET Framework versão 1,0, <xref:System.Runtime.Serialization.ISerializable> foi introduzido como um mecanismo geral para serializar objetos para persistência ou transferência de dados.</span><span class="sxs-lookup"><span data-stu-id="49e6e-474">In .NET Framework version 1.0, <xref:System.Runtime.Serialization.ISerializable> was introduced as a general mechanism to serialize objects for persistence or data transfer.</span></span> <span data-ttu-id="49e6e-475">Há muitos tipos de .NET Framework que implementam `ISerializable` e que podem ser passados entre aplicativos.</span><span class="sxs-lookup"><span data-stu-id="49e6e-475">There are many .NET Framework types that implement `ISerializable` and that can be passed between applications.</span></span> <span data-ttu-id="49e6e-476"><xref:System.Runtime.Serialization.DataContractSerializer>Naturalmente, o oferece suporte para `ISerializable` classes.</span><span class="sxs-lookup"><span data-stu-id="49e6e-476"><xref:System.Runtime.Serialization.DataContractSerializer> naturally provides support for `ISerializable` classes.</span></span> <span data-ttu-id="49e6e-477">Os `DataContractSerializer` tipos de esquema de implementação de mapas `ISerializable` que diferem somente pelo QName (nome qualificado) do tipo e são efetivamente coleções de propriedades.</span><span class="sxs-lookup"><span data-stu-id="49e6e-477">The `DataContractSerializer` maps `ISerializable` implementation schema types that differ only by the QName (qualified name) of the type and are effectively property collections.</span></span> <span data-ttu-id="49e6e-478">Por exemplo, o `DataContractSerializer` mapeia <xref:System.Exception> para o seguinte tipo xsd no `http://schemas.datacontract.org/2004/07/System` namespace.</span><span class="sxs-lookup"><span data-stu-id="49e6e-478">For example, the `DataContractSerializer` maps <xref:System.Exception> to the following XSD type in the `http://schemas.datacontract.org/2004/07/System` namespace.</span></span>

```xml
<xs:complexType name="Exception">
 <xs:sequence>
  <xs:any minOccurs="0" maxOccurs="unbounded"
      namespace="##local" processContents="skip"/>
 </xs:sequence>
 <xs:attribute ref="ser:FactoryType"/>
</xs:complexType>
```

<span data-ttu-id="49e6e-479">O atributo opcional `ser:FactoryType` declarado no esquema de serialização do contrato de dados faz referência a uma classe de fábrica que pode desserializar o tipo.</span><span class="sxs-lookup"><span data-stu-id="49e6e-479">The optional attribute `ser:FactoryType` declared in the Data Contract Serialization schema references a factory class that can deserialize the type.</span></span> <span data-ttu-id="49e6e-480">A classe de fábrica deve fazer parte da coleção de tipos conhecidos da `DataContractSerializer` instância que está sendo usada.</span><span class="sxs-lookup"><span data-stu-id="49e6e-480">The factory class must be part of the known types collection of the `DataContractSerializer` instance being used.</span></span> <span data-ttu-id="49e6e-481">Para obter mais informações sobre tipos conhecidos, consulte [tipos conhecidos de contrato de dados](data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="49e6e-481">For more information about known types, see [Data Contract Known Types](data-contract-known-types.md).</span></span>

## <a name="datacontract-serialization-schema"></a><span data-ttu-id="49e6e-482">Esquema de serialização DataContract</span><span class="sxs-lookup"><span data-stu-id="49e6e-482">DataContract Serialization Schema</span></span>

<span data-ttu-id="49e6e-483">Vários esquemas exportados pelos `DataContractSerializer` tipos, elementos e atributos de uso de um namespace de serialização de contrato de dados especial:</span><span class="sxs-lookup"><span data-stu-id="49e6e-483">A number of schemas exported by the `DataContractSerializer` use types, elements, and attributes from a special Data Contract Serialization namespace:</span></span>

`http://schemas.microsoft.com/2003/10/Serialization`

<span data-ttu-id="49e6e-484">A seguir está uma declaração de esquema de serialização de contrato de dados completa.</span><span class="sxs-lookup"><span data-stu-id="49e6e-484">The following is a complete Data Contract Serialization schema declaration.</span></span>

```xml
<xs:schema attributeFormDefault="qualified"
   elementFormDefault="qualified"
   targetNamespace =
    "http://schemas.microsoft.com/2003/10/Serialization/"
   xmlns:xs="http://www.w3.org/2001/XMLSchema"
   xmlns:tns="http://schemas.microsoft.com/2003/10/Serialization/">

 <!-- Top-level elements for primitive types. -->
 <xs:element name="anyType" nillable="true" type="xs:anyType"/>
 <xs:element name="anyURI" nillable="true" type="xs:anyURI"/>
 <xs:element name="base64Binary"
       nillable="true" type="xs:base64Binary"/>
 <xs:element name="boolean" nillable="true" type="xs:boolean"/>
 <xs:element name="byte" nillable="true" type="xs:byte"/>
 <xs:element name="dateTime" nillable="true" type="xs:dateTime"/>
 <xs:element name="decimal" nillable="true" type="xs:decimal"/>
 <xs:element name="double" nillable="true" type="xs:double"/>
 <xs:element name="float" nillable="true" type="xs:float"/>
 <xs:element name="int" nillable="true" type="xs:int"/>
 <xs:element name="long" nillable="true" type="xs:long"/>
 <xs:element name="QName" nillable="true" type="xs:QName"/>
 <xs:element name="short" nillable="true" type="xs:short"/>
 <xs:element name="string" nillable="true" type="xs:string"/>
 <xs:element name="unsignedByte"
       nillable="true" type="xs:unsignedByte"/>
 <xs:element name="unsignedInt"
       nillable="true" type="xs:unsignedInt"/>
 <xs:element name="unsignedLong"
       nillable="true" type="xs:unsignedLong"/>
 <xs:element name="unsignedShort"
       nillable="true" type="xs:unsignedShort"/>

 <!-- Primitive types introduced for certain .NET simple types. -->
 <xs:element name="char" nillable="true" type="tns:char"/>
 <xs:simpleType name="char">
  <xs:restriction base="xs:int"/>
 </xs:simpleType>

 <!-- xs:duration is restricted to an ordered value space,
    to map to System.TimeSpan -->
 <xs:element name="duration" nillable="true" type="tns:duration"/>
 <xs:simpleType name="duration">
  <xs:restriction base="xs:duration">
   <xs:pattern
     value="\-?P(\d*D)?(T(\d*H)?(\d*M)?(\d*(\.\d*)?S)?)?"/>
   <xs:minInclusive value="-P10675199DT2H48M5.4775808S"/>
   <xs:maxInclusive value="P10675199DT2H48M5.4775807S"/>
  </xs:restriction>
 </xs:simpleType>

 <xs:element name="guid" nillable="true" type="tns:guid"/>
 <xs:simpleType name="guid">
  <xs:restriction base="xs:string">
   <xs:pattern value="[\da-fA-F]{8}-[\da-fA-F]{4}-[\da-fA-F]{4}-[\da-fA-F]{4}-[\da-fA-F]{12}"/>
  </xs:restriction>
 </xs:simpleType>

 <!-- This is used for schemas exported from ISerializable type. -->
 <xs:attribute name="FactoryType" type="xs:QName"/>
</xs:schema>
```

<span data-ttu-id="49e6e-485">O seguinte deve ser observado:</span><span class="sxs-lookup"><span data-stu-id="49e6e-485">The following should be noted:</span></span>

- <span data-ttu-id="49e6e-486">`ser:char`é introduzido para representar caracteres Unicode do tipo <xref:System.Char> .</span><span class="sxs-lookup"><span data-stu-id="49e6e-486">`ser:char` is introduced to represent Unicode characters of type <xref:System.Char>.</span></span>

- <span data-ttu-id="49e6e-487">O `valuespace` de `xs:duration` é reduzido para um conjunto ordenado para que ele possa ser mapeado para um <xref:System.TimeSpan> .</span><span class="sxs-lookup"><span data-stu-id="49e6e-487">The `valuespace` of `xs:duration` is reduced to an ordered set so that it can be mapped to a <xref:System.TimeSpan>.</span></span>

- <span data-ttu-id="49e6e-488">`FactoryType`é usado em esquemas exportados de tipos derivados de <xref:System.Runtime.Serialization.ISerializable> .</span><span class="sxs-lookup"><span data-stu-id="49e6e-488">`FactoryType` is used in schemas exported from types that are derived from <xref:System.Runtime.Serialization.ISerializable>.</span></span>

## <a name="importing-non-datacontract-schemas"></a><span data-ttu-id="49e6e-489">Importando esquemas não DataContract</span><span class="sxs-lookup"><span data-stu-id="49e6e-489">Importing non-DataContract schemas</span></span>

<span data-ttu-id="49e6e-490">`DataContractSerializer`tem a `ImportXmlTypes` opção de permitir a importação de esquemas que não estão de acordo com o `DataContractSerializer` perfil XSD (consulte a <xref:System.Runtime.Serialization.XsdDataContractImporter.Options%2A> Propriedade).</span><span class="sxs-lookup"><span data-stu-id="49e6e-490">`DataContractSerializer` has the `ImportXmlTypes` option to allow import of schemas that do not conform to the `DataContractSerializer` XSD profile (see the <xref:System.Runtime.Serialization.XsdDataContractImporter.Options%2A> property).</span></span> <span data-ttu-id="49e6e-491">Definir essa opção para `true` habilitar a aceitação de tipos de esquema não conformes e de mapeamento para a implementação a seguir, <xref:System.Xml.Serialization.IXmlSerializable> Encapsulando uma matriz de <xref:System.Xml.XmlNode> (somente o nome da classe difere).</span><span class="sxs-lookup"><span data-stu-id="49e6e-491">Setting this option to `true` enables acceptance of non-conforming schema types and mapping them to the following implementation, <xref:System.Xml.Serialization.IXmlSerializable> wrapping an array of <xref:System.Xml.XmlNode> (only the class name differs).</span></span>

```csharp
[GeneratedCodeAttribute("System.Runtime.Serialization", "3.0.0.0")]
[System.Xml.Serialization.XmlSchemaProviderAttribute("ExportSchema")]
[System.Xml.Serialization.XmlRootAttribute(IsNullable=false)]
public partial class Person : object, IXmlSerializable
{
  private XmlNode[] nodesField;
  private static XmlQualifiedName typeName =
new XmlQualifiedName("Person","http://Microsoft.ServiceModel.Samples");
  public XmlNode[] Nodes
  {
    get {return this.nodesField;}
    set {this.nodesField = value;}
  }
  public void ReadXml(XmlReader reader)
  {
    this.nodesField = XmlSerializableServices.ReadNodes(reader);
  }
  public void WriteXml(XmlWriter writer)
  {
    XmlSerializableServices.WriteNodes(writer, this.Nodes);
  }
  public System.Xml.Schema.XmlSchema GetSchema()
  {
    return null;
  }
  public static XmlQualifiedName ExportSchema(XmlSchemaSet schemas)
  {
    XmlSerializableServices.AddDefaultSchema(schemas, typeName);
    return typeName;
  }
}
```

## <a name="datetimeoffset-serialization"></a><span data-ttu-id="49e6e-492">Serialização de DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="49e6e-492">DateTimeOffset Serialization</span></span>

<span data-ttu-id="49e6e-493">O <xref:System.DateTimeOffset> não é tratado como um tipo primitivo.</span><span class="sxs-lookup"><span data-stu-id="49e6e-493">The <xref:System.DateTimeOffset> is not treated as a primitive type.</span></span> <span data-ttu-id="49e6e-494">Em vez disso, ele é serializado como um elemento complexo com duas partes.</span><span class="sxs-lookup"><span data-stu-id="49e6e-494">Instead, it is serialized as a complex element with two parts.</span></span> <span data-ttu-id="49e6e-495">A primeira parte representa a data e hora, e a segunda parte representa o deslocamento a partir da data e hora.</span><span class="sxs-lookup"><span data-stu-id="49e6e-495">The first part represents the date time, and the second part represents the offset from the date time.</span></span> <span data-ttu-id="49e6e-496">Um exemplo de um valor de DateTimeOffset serializado é mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="49e6e-496">An example of a serialized DateTimeOffset value is shown in the following code.</span></span>

```xml
<OffSet xmlns:a="http://schemas.datacontract.org/2004/07/System">
  <DateTime i:type="b:dateTime" xmlns=""
    xmlns:b="http://www.w3.org/2001/XMLSchema">2008-08-28T08:00:00
  </DateTime>
  <OffsetMinutes i:type="b:short" xmlns=""
   xmlns:b="http://www.w3.org/2001/XMLSchema">-480
   </OffsetMinutes>
</OffSet>
```

<span data-ttu-id="49e6e-497">O esquema é o seguinte.</span><span class="sxs-lookup"><span data-stu-id="49e6e-497">The schema is as follows.</span></span>

```xml
<xs:schema targetNamespace="http://schemas.datacontract.org/2004/07/System">
   <xs:complexType name="DateTimeOffset">
      <xs:sequence minOccurs="1" maxOccurs="1">
         <xs:element name="DateTime" type="xs:dateTime"
         minOccurs="1" maxOccurs="1" />
         <xs:element name="OffsetMinutes" type="xs:short"
         minOccurs="1" maxOccurs="1" />
      </xs:sequence>
   </xs:complexType>
</xs:schema>
```

## <a name="see-also"></a><span data-ttu-id="49e6e-498">Consulte também</span><span class="sxs-lookup"><span data-stu-id="49e6e-498">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- <xref:System.Runtime.Serialization.XsdDataContractImporter>
- [<span data-ttu-id="49e6e-499">Usando contratos de dados</span><span class="sxs-lookup"><span data-stu-id="49e6e-499">Using Data Contracts</span></span>](using-data-contracts.md)
