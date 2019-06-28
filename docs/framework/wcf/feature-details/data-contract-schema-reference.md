---
title: Referência de esquema de contrato de dados
ms.date: 03/30/2017
helpviewer_keywords:
- data contracts [WCF], schema reference
ms.assetid: 9ebb0ebe-8166-4c93-980a-7c8f1f38f7c0
ms.openlocfilehash: e736b963fe081832995cdc8d9c2ab41ac34cf980
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/28/2019
ms.locfileid: "67425380"
---
# <a name="data-contract-schema-reference"></a><span data-ttu-id="c9a37-102">Referência de esquema de contrato de dados</span><span class="sxs-lookup"><span data-stu-id="c9a37-102">Data Contract Schema Reference</span></span>

<span data-ttu-id="c9a37-103">Este tópico descreve o subconjunto do esquema XML (XSD) usada pelo <xref:System.Runtime.Serialization.DataContractSerializer> para descrever o common language runtime (CLR) tipos para serialização de XML.</span><span class="sxs-lookup"><span data-stu-id="c9a37-103">This topic describes the subset of the XML Schema (XSD) used by <xref:System.Runtime.Serialization.DataContractSerializer> to describe common language runtime (CLR) types for XML serialization.</span></span>

## <a name="datacontractserializer-mappings"></a><span data-ttu-id="c9a37-104">Mapeamentos de DataContractSerializer</span><span class="sxs-lookup"><span data-stu-id="c9a37-104">DataContractSerializer Mappings</span></span>

<span data-ttu-id="c9a37-105">O `DataContractSerializer` mapeia tipos CLR para XSD quando os metadados são exportados de um serviço do Windows Communication Foundation (WCF) usando um ponto de extremidade de metadados ou o [ferramenta Utilitário de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="c9a37-105">The `DataContractSerializer` maps CLR types to XSD when metadata is exported from a Windows Communication Foundation (WCF) service using a metadata endpoint or the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="c9a37-106">Para obter mais informações, consulte [serializador de contrato de dados](../../../../docs/framework/wcf/feature-details/data-contract-serializer.md).</span><span class="sxs-lookup"><span data-stu-id="c9a37-106">For more information, see [Data Contract Serializer](../../../../docs/framework/wcf/feature-details/data-contract-serializer.md).</span></span>

<span data-ttu-id="c9a37-107">O `DataContractSerializer` também mapeia XSD para tipos CLR quando Svcutil.exe é usado para acessar os documentos de descrição de linguagem WSDL (Web Services) ou XSD e gerar contratos de dados para serviços ou clientes.</span><span class="sxs-lookup"><span data-stu-id="c9a37-107">The `DataContractSerializer` also maps XSD to CLR types when Svcutil.exe is used to access Web Services Description Language (WSDL) or XSD documents and generate data contracts for services or clients.</span></span>

<span data-ttu-id="c9a37-108">Somente as instâncias de esquema XML que atendem aos requisitos mencionados neste documento podem ser mapeadas para tipos CLR usando `DataContractSerializer`.</span><span class="sxs-lookup"><span data-stu-id="c9a37-108">Only XML Schema instances that conform to requirements stated in this document can be mapped to CLR types using `DataContractSerializer`.</span></span>

### <a name="support-levels"></a><span data-ttu-id="c9a37-109">Níveis de suporte</span><span class="sxs-lookup"><span data-stu-id="c9a37-109">Support Levels</span></span>

<span data-ttu-id="c9a37-110">O `DataContractSerializer` fornece os seguintes níveis de suporte para um determinado recurso de esquema XML:</span><span class="sxs-lookup"><span data-stu-id="c9a37-110">The `DataContractSerializer` provides the following levels of support for a given XML Schema feature:</span></span>

- <span data-ttu-id="c9a37-111">**Suporte para**.</span><span class="sxs-lookup"><span data-stu-id="c9a37-111">**Supported**.</span></span> <span data-ttu-id="c9a37-112">Não há mapeamento explícito desse recurso para o CLR tipos atributos (ou ambos) usando `DataContractSerializer`.</span><span class="sxs-lookup"><span data-stu-id="c9a37-112">There is explicit mapping from this feature to CLR types or attributes (or both) using `DataContractSerializer`.</span></span>

- <span data-ttu-id="c9a37-113">**Ignorado**.</span><span class="sxs-lookup"><span data-stu-id="c9a37-113">**Ignored**.</span></span> <span data-ttu-id="c9a37-114">O recurso é permitido em esquemas importadas pelo `DataContractSerializer`, mas não tem efeito sobre a geração de código.</span><span class="sxs-lookup"><span data-stu-id="c9a37-114">The feature is allowed in schemas imported by the `DataContractSerializer`, but has no effect on code generation.</span></span>

- <span data-ttu-id="c9a37-115">**Proibido**.</span><span class="sxs-lookup"><span data-stu-id="c9a37-115">**Forbidden**.</span></span> <span data-ttu-id="c9a37-116">O `DataContractSerializer` não oferece suporte à importação de um esquema usando o recurso.</span><span class="sxs-lookup"><span data-stu-id="c9a37-116">The `DataContractSerializer` does not support importing a schema using the feature.</span></span> <span data-ttu-id="c9a37-117">Por exemplo, Svcutil.exe, ao acessar um WSDL com um esquema que usa o recurso, voltará a usar o <xref:System.Xml.Serialization.XmlSerializer> em vez disso.</span><span class="sxs-lookup"><span data-stu-id="c9a37-117">For example, Svcutil.exe, when accessing a WSDL with a schema that uses such a feature, falls back to using the <xref:System.Xml.Serialization.XmlSerializer> instead.</span></span> <span data-ttu-id="c9a37-118">Isso é por padrão.</span><span class="sxs-lookup"><span data-stu-id="c9a37-118">This is by default.</span></span>

## <a name="general-information"></a><span data-ttu-id="c9a37-119">Informações gerais</span><span class="sxs-lookup"><span data-stu-id="c9a37-119">General Information</span></span>

- <span data-ttu-id="c9a37-120">O namespace do esquema é descrito em [esquema XML](https://go.microsoft.com/fwlink/?LinkId=95475).</span><span class="sxs-lookup"><span data-stu-id="c9a37-120">The schema namespace is described at [XML Schema](https://go.microsoft.com/fwlink/?LinkId=95475).</span></span> <span data-ttu-id="c9a37-121">O prefixo "xs" é usado neste documento.</span><span class="sxs-lookup"><span data-stu-id="c9a37-121">The prefix "xs" is used in this document.</span></span>

- <span data-ttu-id="c9a37-122">Todos os atributos com um namespace de esquema não são ignorados.</span><span class="sxs-lookup"><span data-stu-id="c9a37-122">Any attributes with a non-schema namespace are ignored.</span></span>

- <span data-ttu-id="c9a37-123">Todas as anotações (exceto aqueles descritos neste documento) são ignoradas.</span><span class="sxs-lookup"><span data-stu-id="c9a37-123">Any annotations (except for those described in this document) are ignored.</span></span>

### <a name="xsschema-attributes"></a><span data-ttu-id="c9a37-124">\<xs:schema>: attributes</span><span class="sxs-lookup"><span data-stu-id="c9a37-124">\<xs:schema>: attributes</span></span>

|<span data-ttu-id="c9a37-125">Atributo</span><span class="sxs-lookup"><span data-stu-id="c9a37-125">Attribute</span></span>|<span data-ttu-id="c9a37-126">DataContract</span><span class="sxs-lookup"><span data-stu-id="c9a37-126">DataContract</span></span>|
|---------------|------------------|
|`attributeFormDefault`|<span data-ttu-id="c9a37-127">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="c9a37-127">Ignored.</span></span>|
|`blockDefault`|<span data-ttu-id="c9a37-128">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="c9a37-128">Ignored.</span></span>|
|`elementFormDefault`|<span data-ttu-id="c9a37-129">Deve ser qualificado.</span><span class="sxs-lookup"><span data-stu-id="c9a37-129">Must be qualified.</span></span> <span data-ttu-id="c9a37-130">Todos os elementos devem ser qualificados para um esquema para serem suportados por `DataContractSerializer`.</span><span class="sxs-lookup"><span data-stu-id="c9a37-130">All elements must be qualified for a schema to be supported by `DataContractSerializer`.</span></span> <span data-ttu-id="c9a37-131">Isso pode ser feito configurando xs:schema/@elementFormDefault para "qualified" ou definindo xs:element/@form a "qualificado" na declaração de cada elemento individual.</span><span class="sxs-lookup"><span data-stu-id="c9a37-131">This can be accomplished by either setting xs:schema/@elementFormDefault to "qualified" or by setting xs:element/@form to "qualified" on each individual element declaration.</span></span>|
|`finalDefault`|<span data-ttu-id="c9a37-132">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="c9a37-132">Ignored.</span></span>|
|`Id`|<span data-ttu-id="c9a37-133">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="c9a37-133">Ignored.</span></span>|
|`targetNamespace`|<span data-ttu-id="c9a37-134">Suporte e mapeado para o namespace de contrato de dados.</span><span class="sxs-lookup"><span data-stu-id="c9a37-134">Supported and mapped to the data contract namespace.</span></span> <span data-ttu-id="c9a37-135">Se esse atributo não for especificado, o namespace em branco será usado.</span><span class="sxs-lookup"><span data-stu-id="c9a37-135">If this attribute is not specified, the blank namespace is used.</span></span> <span data-ttu-id="c9a37-136">Não pode ser o namespace reservado `http://schemas.microsoft.com/2003/10/Serialization/`.</span><span class="sxs-lookup"><span data-stu-id="c9a37-136">Cannot be the reserved namespace `http://schemas.microsoft.com/2003/10/Serialization/`.</span></span>|
|`version`|<span data-ttu-id="c9a37-137">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="c9a37-137">Ignored.</span></span>|

### <a name="xsschema-contents"></a><span data-ttu-id="c9a37-138">\<xs:schema>: contents</span><span class="sxs-lookup"><span data-stu-id="c9a37-138">\<xs:schema>: contents</span></span>

|<span data-ttu-id="c9a37-139">Conteúdo</span><span class="sxs-lookup"><span data-stu-id="c9a37-139">Contents</span></span>|<span data-ttu-id="c9a37-140">Esquema</span><span class="sxs-lookup"><span data-stu-id="c9a37-140">Schema</span></span>|
|--------------|------------|
|`include`|<span data-ttu-id="c9a37-141">Com suporte.</span><span class="sxs-lookup"><span data-stu-id="c9a37-141">Supported.</span></span> <span data-ttu-id="c9a37-142">`DataContractSerializer` dá suporte a xs: incluir e xs: importde.</span><span class="sxs-lookup"><span data-stu-id="c9a37-142">`DataContractSerializer` supports xs:include and xs:import.</span></span> <span data-ttu-id="c9a37-143">No entanto, restringe Svcutil.exe seguintes `xs:include/@schemaLocation` e `xs:import/@location` faz referência quando os metadados são carregados de um arquivo local.</span><span class="sxs-lookup"><span data-stu-id="c9a37-143">However, Svcutil.exe restricts following `xs:include/@schemaLocation` and `xs:import/@location` references when metadata is loaded from a local file.</span></span> <span data-ttu-id="c9a37-144">A lista de arquivos de esquema deve ser passada por meio de um mecanismo fora de banda e não `include` nesse caso; `include`documentos de esquema d são ignorados.</span><span class="sxs-lookup"><span data-stu-id="c9a37-144">The list of schema files must be passed through an out-of-band mechanism and not through `include` in this case; `include`d schema documents are ignored.</span></span>|
|`redefine`|<span data-ttu-id="c9a37-145">Negado.</span><span class="sxs-lookup"><span data-stu-id="c9a37-145">Forbidden.</span></span> <span data-ttu-id="c9a37-146">O uso de `xs:redefine` é proibida pela `DataContractSerializer` por motivos de segurança: `x:redefine` requer `schemaLocation` a ser seguido.</span><span class="sxs-lookup"><span data-stu-id="c9a37-146">The use of `xs:redefine` is forbidden by `DataContractSerializer` for security reasons: `x:redefine` requires `schemaLocation` to be followed.</span></span> <span data-ttu-id="c9a37-147">Em determinadas circunstâncias, Svcutil.exe usando DataContract restringe o uso de `schemaLocation`.</span><span class="sxs-lookup"><span data-stu-id="c9a37-147">In certain circumstances, Svcutil.exe using DataContract restricts use of `schemaLocation`.</span></span>|
|`import`|<span data-ttu-id="c9a37-148">Com suporte.</span><span class="sxs-lookup"><span data-stu-id="c9a37-148">Supported.</span></span> <span data-ttu-id="c9a37-149">`DataContractSerializer` dá suporte a `xs:include` e `xs:import`.</span><span class="sxs-lookup"><span data-stu-id="c9a37-149">`DataContractSerializer` supports `xs:include` and `xs:import`.</span></span> <span data-ttu-id="c9a37-150">No entanto, restringe Svcutil.exe seguintes `xs:include/@schemaLocation` e `xs:import/@location` faz referência quando os metadados são carregados de um arquivo local.</span><span class="sxs-lookup"><span data-stu-id="c9a37-150">However, Svcutil.exe restricts following `xs:include/@schemaLocation` and `xs:import/@location` references when metadata is loaded from a local file.</span></span> <span data-ttu-id="c9a37-151">A lista de arquivos de esquema deve ser passada por meio de um mecanismo fora de banda e não `include` nesse caso; `include`documentos de esquema d são ignorados.</span><span class="sxs-lookup"><span data-stu-id="c9a37-151">The list of schema files must be passed through an out-of-band mechanism and not through `include` in this case; `include`d schema documents are ignored.</span></span>|
|`simpleType`|<span data-ttu-id="c9a37-152">Com suporte.</span><span class="sxs-lookup"><span data-stu-id="c9a37-152">Supported.</span></span> <span data-ttu-id="c9a37-153">Consulte o `xs:simpleType` seção.</span><span class="sxs-lookup"><span data-stu-id="c9a37-153">See the `xs:simpleType` section.</span></span>|
|`complexType`|<span data-ttu-id="c9a37-154">Com suporte, é mapeado para contratos de dados.</span><span class="sxs-lookup"><span data-stu-id="c9a37-154">Supported, maps to data contracts.</span></span> <span data-ttu-id="c9a37-155">Consulte o `xs:complexType` seção.</span><span class="sxs-lookup"><span data-stu-id="c9a37-155">See the `xs:complexType` section.</span></span>|
|`group`|<span data-ttu-id="c9a37-156">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="c9a37-156">Ignored.</span></span> <span data-ttu-id="c9a37-157">`DataContractSerializer` não suporta o uso de `xs:group`, `xs:attributeGroup`, e `xs:attribute`.</span><span class="sxs-lookup"><span data-stu-id="c9a37-157">`DataContractSerializer` does not support use of `xs:group`, `xs:attributeGroup`, and `xs:attribute`.</span></span> <span data-ttu-id="c9a37-158">Essas declarações são ignoradas como filhos `xs:schema`, mas não pode ser referenciado de dentro `complexType` ou outras construções com suporte.</span><span class="sxs-lookup"><span data-stu-id="c9a37-158">These declarations are ignored as children of `xs:schema`, but cannot be referenced from within `complexType` or other supported constructs.</span></span>|
|`attributeGroup`|<span data-ttu-id="c9a37-159">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="c9a37-159">Ignored.</span></span> <span data-ttu-id="c9a37-160">`DataContractSerializer` não suporta o uso de `xs:group`, `xs:attributeGroup`, e `xs:attribute`.</span><span class="sxs-lookup"><span data-stu-id="c9a37-160">`DataContractSerializer` does not support use of `xs:group`, `xs:attributeGroup`, and `xs:attribute`.</span></span> <span data-ttu-id="c9a37-161">Essas declarações são ignoradas como filhos `xs:schema`, mas não pode ser referenciado de dentro `complexType` ou outras construções com suporte.</span><span class="sxs-lookup"><span data-stu-id="c9a37-161">These declarations are ignored as children of `xs:schema`, but cannot be referenced from within `complexType` or other supported constructs.</span></span>|
|`element`|<span data-ttu-id="c9a37-162">Com suporte.</span><span class="sxs-lookup"><span data-stu-id="c9a37-162">Supported.</span></span> <span data-ttu-id="c9a37-163">Consulte a declaração de elemento Global (teste).</span><span class="sxs-lookup"><span data-stu-id="c9a37-163">See Global Element Declaration (GED).</span></span>|
|`attribute`|<span data-ttu-id="c9a37-164">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="c9a37-164">Ignored.</span></span> <span data-ttu-id="c9a37-165">`DataContractSerializer` não suporta o uso de `xs:group`, `xs:attributeGroup`, e `xs:attribute`.</span><span class="sxs-lookup"><span data-stu-id="c9a37-165">`DataContractSerializer` does not support use of `xs:group`, `xs:attributeGroup`, and `xs:attribute`.</span></span> <span data-ttu-id="c9a37-166">Essas declarações são ignoradas como filhos `xs:schema`, mas não pode ser referenciado de dentro `complexType` ou outras construções com suporte.</span><span class="sxs-lookup"><span data-stu-id="c9a37-166">These declarations are ignored as children of `xs:schema`, but cannot be referenced from within `complexType` or other supported constructs.</span></span>|
|`notation`|<span data-ttu-id="c9a37-167">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="c9a37-167">Ignored.</span></span>|

## <a name="complex-types--xscomplextype"></a><span data-ttu-id="c9a37-168">Tipos complexos – \<xs:complexType ></span><span class="sxs-lookup"><span data-stu-id="c9a37-168">Complex Types – \<xs:complexType></span></span>

### <a name="general-information"></a><span data-ttu-id="c9a37-169">Informações gerais</span><span class="sxs-lookup"><span data-stu-id="c9a37-169">General Information</span></span>

<span data-ttu-id="c9a37-170">Cada tipo complexo \<xs:complexType > é mapeado para um contrato de dados.</span><span class="sxs-lookup"><span data-stu-id="c9a37-170">Each complex type \<xs:complexType> maps to a data contract.</span></span>

### <a name="xscomplextype-attributes"></a><span data-ttu-id="c9a37-171">\<xs:complexType >: atributos</span><span class="sxs-lookup"><span data-stu-id="c9a37-171">\<xs:complexType>: attributes</span></span>

|<span data-ttu-id="c9a37-172">Atributo</span><span class="sxs-lookup"><span data-stu-id="c9a37-172">Attribute</span></span>|<span data-ttu-id="c9a37-173">Esquema</span><span class="sxs-lookup"><span data-stu-id="c9a37-173">Schema</span></span>|
|---------------|------------|
|`abstract`|<span data-ttu-id="c9a37-174">Deve ser false (padrão).</span><span class="sxs-lookup"><span data-stu-id="c9a37-174">Must be false (default).</span></span>|
|`block`|<span data-ttu-id="c9a37-175">Negado.</span><span class="sxs-lookup"><span data-stu-id="c9a37-175">Forbidden.</span></span>|
|`final`|<span data-ttu-id="c9a37-176">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="c9a37-176">Ignored.</span></span>|
|`id`|<span data-ttu-id="c9a37-177">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="c9a37-177">Ignored.</span></span>|
|`mixed`|<span data-ttu-id="c9a37-178">Deve ser false (padrão).</span><span class="sxs-lookup"><span data-stu-id="c9a37-178">Must be false (default).</span></span>|
|`name`|<span data-ttu-id="c9a37-179">Suporte e mapeado para o nome do contrato de dados.</span><span class="sxs-lookup"><span data-stu-id="c9a37-179">Supported and mapped to the data contract name.</span></span> <span data-ttu-id="c9a37-180">Se houver períodos no nome, é feita uma tentativa para mapear o tipo para um tipo interno.</span><span class="sxs-lookup"><span data-stu-id="c9a37-180">If there are periods in the name, an attempt is made to map the type to an inner type.</span></span> <span data-ttu-id="c9a37-181">Por exemplo, um tipo complexo chamado `A.B` é mapeado para um contrato de dados tipo que é um tipo interno de um tipo com o nome do contrato de dados `A`, mas somente se o tipo de contrato de tal um tipo de dados existe.</span><span class="sxs-lookup"><span data-stu-id="c9a37-181">For example, a complex type named `A.B` maps to a data contract type that is an inner type of a type with the data contract name `A`, but only if such a data contract type exists.</span></span> <span data-ttu-id="c9a37-182">Mais de um nível de aninhamento é possível: por exemplo, `A.B.C` pode ser um tipo interno, mas somente se `A` e `A.B` ambas existir.</span><span class="sxs-lookup"><span data-stu-id="c9a37-182">More than one level of nesting is possible: for example, `A.B.C` can be an inner type, but only if `A` and `A.B` both exist.</span></span>|

### <a name="xscomplextype-contents"></a><span data-ttu-id="c9a37-183">\<xs:complexType>: contents</span><span class="sxs-lookup"><span data-stu-id="c9a37-183">\<xs:complexType>: contents</span></span>

|<span data-ttu-id="c9a37-184">Conteúdo</span><span class="sxs-lookup"><span data-stu-id="c9a37-184">Contents</span></span>|<span data-ttu-id="c9a37-185">Esquema</span><span class="sxs-lookup"><span data-stu-id="c9a37-185">Schema</span></span>|
|--------------|------------|
|`simpleContent`|<span data-ttu-id="c9a37-186">As extensões são proibidas.</span><span class="sxs-lookup"><span data-stu-id="c9a37-186">Extensions are forbidden.</span></span><br /><br /> <span data-ttu-id="c9a37-187">Restrição só é permitida em `anySimpleType`.</span><span class="sxs-lookup"><span data-stu-id="c9a37-187">Restriction is allowed only from `anySimpleType`.</span></span>|
|`complexContent`|<span data-ttu-id="c9a37-188">Com suporte.</span><span class="sxs-lookup"><span data-stu-id="c9a37-188">Supported.</span></span> <span data-ttu-id="c9a37-189">Consulte "Herança".</span><span class="sxs-lookup"><span data-stu-id="c9a37-189">See "Inheritance".</span></span>|
|`group`|<span data-ttu-id="c9a37-190">Negado.</span><span class="sxs-lookup"><span data-stu-id="c9a37-190">Forbidden.</span></span>|
|`all`|<span data-ttu-id="c9a37-191">Negado.</span><span class="sxs-lookup"><span data-stu-id="c9a37-191">Forbidden.</span></span>|
|`choice`|<span data-ttu-id="c9a37-192">Proibido</span><span class="sxs-lookup"><span data-stu-id="c9a37-192">Forbidden</span></span>|
|`sequence`|<span data-ttu-id="c9a37-193">Com suporte, é mapeado para membros de dados de um contrato de dados.</span><span class="sxs-lookup"><span data-stu-id="c9a37-193">Supported, maps to data members of a data contract.</span></span>|
|`attribute`|<span data-ttu-id="c9a37-194">Proibido, mesmo que use = "prohibited" (com uma exceção).</span><span class="sxs-lookup"><span data-stu-id="c9a37-194">Forbidden, even if use="prohibited" (with one exception).</span></span> <span data-ttu-id="c9a37-195">Somente os atributos opcionais do namespace do esquema de serialização padrão têm suporte.</span><span class="sxs-lookup"><span data-stu-id="c9a37-195">Only optional attributes from the Standard Serialization Schema namespace are supported.</span></span> <span data-ttu-id="c9a37-196">Eles não são mapeados para membros de dados no modelo de programação de contrato de dados.</span><span class="sxs-lookup"><span data-stu-id="c9a37-196">They do not map to data members in the data contract programming model.</span></span> <span data-ttu-id="c9a37-197">Atualmente, apenas um desses atributos tem um significado e é abordado na seção de ISerializable.</span><span class="sxs-lookup"><span data-stu-id="c9a37-197">Currently, only one such attribute has meaning and is discussed in the ISerializable section.</span></span> <span data-ttu-id="c9a37-198">Todos os outros são ignorados.</span><span class="sxs-lookup"><span data-stu-id="c9a37-198">All others are ignored.</span></span>|
|`attributeGroup`|<span data-ttu-id="c9a37-199">Negado.</span><span class="sxs-lookup"><span data-stu-id="c9a37-199">Forbidden.</span></span> <span data-ttu-id="c9a37-200">Na versão v1 do WCF, `DataContractSerializer` ignora a presença `attributeGroup` dentro de `xs:complexType`.</span><span class="sxs-lookup"><span data-stu-id="c9a37-200">In the WCF v1 release, `DataContractSerializer` ignores the presence of `attributeGroup` inside `xs:complexType`.</span></span>|
|`anyAttribute`|<span data-ttu-id="c9a37-201">Negado.</span><span class="sxs-lookup"><span data-stu-id="c9a37-201">Forbidden.</span></span>|
|<span data-ttu-id="c9a37-202">(vazio)</span><span class="sxs-lookup"><span data-stu-id="c9a37-202">(empty)</span></span>|<span data-ttu-id="c9a37-203">Mapeia para um contrato de dados sem membros de dados.</span><span class="sxs-lookup"><span data-stu-id="c9a37-203">Maps to a data contract with no data members.</span></span>|

### <a name="xssequence-in-a-complex-type-attributes"></a><span data-ttu-id="c9a37-204">\<xs: sequence > em um tipo complexo: atributos</span><span class="sxs-lookup"><span data-stu-id="c9a37-204">\<xs:sequence> in a complex type: attributes</span></span>

|<span data-ttu-id="c9a37-205">Atributo</span><span class="sxs-lookup"><span data-stu-id="c9a37-205">Attribute</span></span>|<span data-ttu-id="c9a37-206">Esquema</span><span class="sxs-lookup"><span data-stu-id="c9a37-206">Schema</span></span>|
|---------------|------------|
|`id`|<span data-ttu-id="c9a37-207">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="c9a37-207">Ignored.</span></span>|
|`maxOccurs`|<span data-ttu-id="c9a37-208">Deve ser 1 (padrão).</span><span class="sxs-lookup"><span data-stu-id="c9a37-208">Must be 1 (default).</span></span>|
|`minOccurs`|<span data-ttu-id="c9a37-209">Deve ser 1 (padrão).</span><span class="sxs-lookup"><span data-stu-id="c9a37-209">Must be 1 (default).</span></span>|

### <a name="xssequence-in-a-complex-type-contents"></a><span data-ttu-id="c9a37-210">\<xs: sequence > em um tipo complexo: conteúdo</span><span class="sxs-lookup"><span data-stu-id="c9a37-210">\<xs:sequence> in a complex type: contents</span></span>

|<span data-ttu-id="c9a37-211">Conteúdo</span><span class="sxs-lookup"><span data-stu-id="c9a37-211">Contents</span></span>|<span data-ttu-id="c9a37-212">Esquema</span><span class="sxs-lookup"><span data-stu-id="c9a37-212">Schema</span></span>|
|--------------|------------|
|`element`|<span data-ttu-id="c9a37-213">Cada instância é mapeado para um membro de dados.</span><span class="sxs-lookup"><span data-stu-id="c9a37-213">Each instance maps to a data member.</span></span>|
|`group`|<span data-ttu-id="c9a37-214">Negado.</span><span class="sxs-lookup"><span data-stu-id="c9a37-214">Forbidden.</span></span>|
|`choice`|<span data-ttu-id="c9a37-215">Negado.</span><span class="sxs-lookup"><span data-stu-id="c9a37-215">Forbidden.</span></span>|
|`sequence`|<span data-ttu-id="c9a37-216">Negado.</span><span class="sxs-lookup"><span data-stu-id="c9a37-216">Forbidden.</span></span>|
|`any`|<span data-ttu-id="c9a37-217">Negado.</span><span class="sxs-lookup"><span data-stu-id="c9a37-217">Forbidden.</span></span>|
|<span data-ttu-id="c9a37-218">(vazio)</span><span class="sxs-lookup"><span data-stu-id="c9a37-218">(empty)</span></span>|<span data-ttu-id="c9a37-219">Mapeia para um contrato de dados sem membros de dados.</span><span class="sxs-lookup"><span data-stu-id="c9a37-219">Maps to a data contract with no data members.</span></span>|

## <a name="elements--xselement"></a><span data-ttu-id="c9a37-220">Elements – \<xs:element></span><span class="sxs-lookup"><span data-stu-id="c9a37-220">Elements – \<xs:element></span></span>

### <a name="general-information"></a><span data-ttu-id="c9a37-221">Informações gerais</span><span class="sxs-lookup"><span data-stu-id="c9a37-221">General Information</span></span>

<span data-ttu-id="c9a37-222">`<xs:element>` pode ocorrer nos seguintes contextos:</span><span class="sxs-lookup"><span data-stu-id="c9a37-222">`<xs:element>` can occur in the following contexts:</span></span>

- <span data-ttu-id="c9a37-223">Ele pode ocorrer dentro de um `<xs:sequence>`, que descreve um membro de dados de um contrato de dados de regulares (não da coleção).</span><span class="sxs-lookup"><span data-stu-id="c9a37-223">It can occur within an `<xs:sequence>`, which describes a data member of a regular (non-collection) data contract.</span></span> <span data-ttu-id="c9a37-224">Nesse caso, o `maxOccurs` atributo deve ser 1.</span><span class="sxs-lookup"><span data-stu-id="c9a37-224">In this case, the `maxOccurs` attribute must be 1.</span></span> <span data-ttu-id="c9a37-225">(Um valor de 0 não é permitido).</span><span class="sxs-lookup"><span data-stu-id="c9a37-225">(A value of 0 is not allowed).</span></span>

- <span data-ttu-id="c9a37-226">Ele pode ocorrer dentro de um `<xs:sequence>`, que descreve um membro de dados de um contrato de dados de coleção.</span><span class="sxs-lookup"><span data-stu-id="c9a37-226">It can occur within an `<xs:sequence>`, which describes a data member of a collection data contract.</span></span> <span data-ttu-id="c9a37-227">Nesse caso, o `maxOccurs` atributo deve ser maior que 1 ou "unbounded".</span><span class="sxs-lookup"><span data-stu-id="c9a37-227">In this case, the `maxOccurs` attribute must be greater than 1 or "unbounded".</span></span>

- <span data-ttu-id="c9a37-228">Ele pode ocorrer dentro de um `<xs:schema>` como uma declaração de elemento Global (teste).</span><span class="sxs-lookup"><span data-stu-id="c9a37-228">It can occur within an `<xs:schema>` as a Global Element Declaration (GED).</span></span>

### <a name="xselement-with-maxoccurs1-within-an-xssequence-data-members"></a><span data-ttu-id="c9a37-229">\<xs: element > com maxOccurs = 1 dentro de um \<xs: sequence > (membros de dados)</span><span class="sxs-lookup"><span data-stu-id="c9a37-229">\<xs:element> with maxOccurs=1 within an \<xs:sequence> (Data Members)</span></span>

|<span data-ttu-id="c9a37-230">Atributo</span><span class="sxs-lookup"><span data-stu-id="c9a37-230">Attribute</span></span>|<span data-ttu-id="c9a37-231">Esquema</span><span class="sxs-lookup"><span data-stu-id="c9a37-231">Schema</span></span>|
|---------------|------------|
|`ref`|<span data-ttu-id="c9a37-232">Negado.</span><span class="sxs-lookup"><span data-stu-id="c9a37-232">Forbidden.</span></span>|
|`name`|<span data-ttu-id="c9a37-233">Com suporte, é mapeado para o nome do membro de dados.</span><span class="sxs-lookup"><span data-stu-id="c9a37-233">Supported, maps to the data member name.</span></span>|
|`type`|<span data-ttu-id="c9a37-234">Tipo de suporte, é mapeado para o membro de dados.</span><span class="sxs-lookup"><span data-stu-id="c9a37-234">Supported, maps to the data member type.</span></span> <span data-ttu-id="c9a37-235">Para obter mais informações, consulte o mapeamento de tipo/primitivo.</span><span class="sxs-lookup"><span data-stu-id="c9a37-235">For more information, see Type/primitive mapping.</span></span> <span data-ttu-id="c9a37-236">Se não for especificado (e o elemento não contém um tipo anônimo), `xs:anyType` será assumido.</span><span class="sxs-lookup"><span data-stu-id="c9a37-236">If not specified (and the element does not contain an anonymous type), `xs:anyType` is assumed.</span></span>|
|`block`|<span data-ttu-id="c9a37-237">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="c9a37-237">Ignored.</span></span>|
|`default`|<span data-ttu-id="c9a37-238">Negado.</span><span class="sxs-lookup"><span data-stu-id="c9a37-238">Forbidden.</span></span>|
|`fixed`|<span data-ttu-id="c9a37-239">Negado.</span><span class="sxs-lookup"><span data-stu-id="c9a37-239">Forbidden.</span></span>|
|`form`|<span data-ttu-id="c9a37-240">Deve ser qualificado.</span><span class="sxs-lookup"><span data-stu-id="c9a37-240">Must be qualified.</span></span> <span data-ttu-id="c9a37-241">Esse atributo pode ser definido por meio `elementFormDefault` em `xs:schema`.</span><span class="sxs-lookup"><span data-stu-id="c9a37-241">This attribute can be set through `elementFormDefault` on `xs:schema`.</span></span>|
|`id`|<span data-ttu-id="c9a37-242">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="c9a37-242">Ignored.</span></span>|
|`maxOccurs`|<span data-ttu-id="c9a37-243">1</span><span class="sxs-lookup"><span data-stu-id="c9a37-243">1</span></span>|
|`minOccurs`|<span data-ttu-id="c9a37-244">Mapeia para o <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> propriedade de um membro de dados (`IsRequired` é verdadeiro quando `minOccurs` é 1).</span><span class="sxs-lookup"><span data-stu-id="c9a37-244">Maps to the <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> property of a data member (`IsRequired` is true when `minOccurs` is 1).</span></span>|
|`nillable`|<span data-ttu-id="c9a37-245">Afeta o mapeamento de tipo.</span><span class="sxs-lookup"><span data-stu-id="c9a37-245">Affects type mapping.</span></span> <span data-ttu-id="c9a37-246">Consulte o mapeamento de tipo/primitivo.</span><span class="sxs-lookup"><span data-stu-id="c9a37-246">See Type/primitive mapping.</span></span>|

### <a name="xselement-with-maxoccurs1-within-an-xssequence-collections"></a><span data-ttu-id="c9a37-247">\<xs: element > com maxOccurs > 1 dentro de um \<xs: sequence > (coleções)</span><span class="sxs-lookup"><span data-stu-id="c9a37-247">\<xs:element> with maxOccurs>1 within an \<xs:sequence> (Collections)</span></span>

- <span data-ttu-id="c9a37-248">É mapeado para um <xref:System.Runtime.Serialization.CollectionDataContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="c9a37-248">Maps to a <xref:System.Runtime.Serialization.CollectionDataContractAttribute>.</span></span>

- <span data-ttu-id="c9a37-249">Em tipos de coleção, xs: element apenas um é permitido dentro de um xs: sequence.</span><span class="sxs-lookup"><span data-stu-id="c9a37-249">In collection types, only one xs:element is allowed within an xs:sequence.</span></span>

 <span data-ttu-id="c9a37-250">As coleções podem ser dos seguintes tipos:</span><span class="sxs-lookup"><span data-stu-id="c9a37-250">Collections can be of the following types:</span></span>

- <span data-ttu-id="c9a37-251">Coleções regulares (por exemplo, matrizes).</span><span class="sxs-lookup"><span data-stu-id="c9a37-251">Regular collections (for example, arrays).</span></span>

- <span data-ttu-id="c9a37-252">Coleções de dicionário (mapeamento de um valor para outro; por exemplo, um <xref:System.Collections.Hashtable>).</span><span class="sxs-lookup"><span data-stu-id="c9a37-252">Dictionary collections (mapping one value to another; for example, a <xref:System.Collections.Hashtable>).</span></span>

- <span data-ttu-id="c9a37-253">É a única diferença entre um dicionário e uma matriz de um tipo de par chave/valor no modelo de programação gerado.</span><span class="sxs-lookup"><span data-stu-id="c9a37-253">The only difference between a dictionary and an array of a key/value pair type is in the generated programming model.</span></span> <span data-ttu-id="c9a37-254">Há um mecanismo de anotação de esquema que pode ser usado para indicar que um determinado tipo é uma coleção de dicionário.</span><span class="sxs-lookup"><span data-stu-id="c9a37-254">There is a schema annotation mechanism that can be used to indicate that a given type is a dictionary collection.</span></span>

<span data-ttu-id="c9a37-255">As regras para o `ref`, `block`, `default`, `fixed`, `form`, e `id` atributos são as mesmas para o caso não seja de coleção.</span><span class="sxs-lookup"><span data-stu-id="c9a37-255">The rules for the `ref`, `block`, `default`, `fixed`, `form`, and `id` attributes are the same as for the non-collection case.</span></span> <span data-ttu-id="c9a37-256">Outros atributos incluem aqueles na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="c9a37-256">Other attributes include those in the following table.</span></span>

|<span data-ttu-id="c9a37-257">Atributo</span><span class="sxs-lookup"><span data-stu-id="c9a37-257">Attribute</span></span>|<span data-ttu-id="c9a37-258">Esquema</span><span class="sxs-lookup"><span data-stu-id="c9a37-258">Schema</span></span>|
|---------------|------------|
|`name`|<span data-ttu-id="c9a37-259">Com suporte, é mapeado para o <xref:System.Runtime.Serialization.CollectionDataContractAttribute.ItemName%2A> propriedade no `CollectionDataContractAttribute` atributo.</span><span class="sxs-lookup"><span data-stu-id="c9a37-259">Supported, maps to the <xref:System.Runtime.Serialization.CollectionDataContractAttribute.ItemName%2A> property in the `CollectionDataContractAttribute` attribute.</span></span>|
|`type`|<span data-ttu-id="c9a37-260">Com suporte, é mapeado para o tipo armazenado na coleção.</span><span class="sxs-lookup"><span data-stu-id="c9a37-260">Supported, maps to the type stored in the collection.</span></span>|
|`maxOccurs`|<span data-ttu-id="c9a37-261">Maior que 1 ou "unbounded".</span><span class="sxs-lookup"><span data-stu-id="c9a37-261">Greater than 1 or "unbounded".</span></span> <span data-ttu-id="c9a37-262">O esquema do controlador de domínio deve usar "unbounded".</span><span class="sxs-lookup"><span data-stu-id="c9a37-262">The DC schema should use "unbounded".</span></span>|
|`minOccurs`|<span data-ttu-id="c9a37-263">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="c9a37-263">Ignored.</span></span>|
|`nillable`|<span data-ttu-id="c9a37-264">Afeta o mapeamento de tipo.</span><span class="sxs-lookup"><span data-stu-id="c9a37-264">Affects type mapping.</span></span> <span data-ttu-id="c9a37-265">Esse atributo é ignorado para coleções de dicionário.</span><span class="sxs-lookup"><span data-stu-id="c9a37-265">This attribute is ignored for dictionary collections.</span></span>|

### <a name="xselement-within-an-xsschema-global-element-declaration"></a><span data-ttu-id="c9a37-266">\<xs: element > dentro de um \<xs: schema > declaração de elemento Global</span><span class="sxs-lookup"><span data-stu-id="c9a37-266">\<xs:element> within an \<xs:schema> Global Element Declaration</span></span>

- <span data-ttu-id="c9a37-267">Um Global elemento declaração (teste) que tem o mesmo nome e namespace como um tipo no esquema, ou que define um tipo anônimo dentro deles, deve ser associado ao tipo.</span><span class="sxs-lookup"><span data-stu-id="c9a37-267">A Global Element Declaration (GED) that has the same name and namespace as a type in schema, or that defines an anonymous type inside itself, is said to be associated with the type.</span></span>

- <span data-ttu-id="c9a37-268">Exportação de esquema: GEDs associados são gerados para cada tipo gerado, simple e complexo.</span><span class="sxs-lookup"><span data-stu-id="c9a37-268">Schema export: associated GEDs are generated for every generated type, both simple and complex.</span></span>

- <span data-ttu-id="c9a37-269">Serialização/desserialização: GEDs associados são usados como elementos raiz para o tipo.</span><span class="sxs-lookup"><span data-stu-id="c9a37-269">Deserialization/serialization: associated GEDs are used as root elements for the type.</span></span>

- <span data-ttu-id="c9a37-270">Importação de esquema: GEDs associados não são necessários e serão ignorados se eles seguem as regras a seguir (a menos que elas definem tipos).</span><span class="sxs-lookup"><span data-stu-id="c9a37-270">Schema import: associated GEDs are not required and are ignored if they follow the following rules (unless they define types).</span></span>

|<span data-ttu-id="c9a37-271">Atributo</span><span class="sxs-lookup"><span data-stu-id="c9a37-271">Attribute</span></span>|<span data-ttu-id="c9a37-272">Esquema</span><span class="sxs-lookup"><span data-stu-id="c9a37-272">Schema</span></span>|
|---------------|------------|
|`abstract`|<span data-ttu-id="c9a37-273">Deve ser falsa para GEDs associados.</span><span class="sxs-lookup"><span data-stu-id="c9a37-273">Must be false for associated GEDs.</span></span>|
|`block`|<span data-ttu-id="c9a37-274">Proibido em GEDs associados.</span><span class="sxs-lookup"><span data-stu-id="c9a37-274">Forbidden in associated GEDs.</span></span>|
|`default`|<span data-ttu-id="c9a37-275">Proibido em GEDs associados.</span><span class="sxs-lookup"><span data-stu-id="c9a37-275">Forbidden in associated GEDs.</span></span>|
|`final`|<span data-ttu-id="c9a37-276">Deve ser falsa para GEDs associados.</span><span class="sxs-lookup"><span data-stu-id="c9a37-276">Must be false for associated GEDs.</span></span>|
|`fixed`|<span data-ttu-id="c9a37-277">Proibido em GEDs associados.</span><span class="sxs-lookup"><span data-stu-id="c9a37-277">Forbidden in associated GEDs.</span></span>|
|`id`|<span data-ttu-id="c9a37-278">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="c9a37-278">Ignored.</span></span>|
|`name`|<span data-ttu-id="c9a37-279">Com suporte.</span><span class="sxs-lookup"><span data-stu-id="c9a37-279">Supported.</span></span> <span data-ttu-id="c9a37-280">Consulte a definição de GEDs associados.</span><span class="sxs-lookup"><span data-stu-id="c9a37-280">See the definition of associated GEDs.</span></span>|
|`nillable`|<span data-ttu-id="c9a37-281">Deve ser verdadeira para GEDs associados.</span><span class="sxs-lookup"><span data-stu-id="c9a37-281">Must be true for associated GEDs.</span></span>|
|`substitutionGroup`|<span data-ttu-id="c9a37-282">Proibido em GEDs associados.</span><span class="sxs-lookup"><span data-stu-id="c9a37-282">Forbidden in associated GEDs.</span></span>|
|`type`|<span data-ttu-id="c9a37-283">Com suporte e deve corresponder ao tipo associado para GEDs associados (a menos que o elemento contém um tipo anônimo).</span><span class="sxs-lookup"><span data-stu-id="c9a37-283">Supported, and must match the associated type for associated GEDs (unless the element contains an anonymous type).</span></span>|

### <a name="xselement-contents"></a><span data-ttu-id="c9a37-284">\<xs:element>: contents</span><span class="sxs-lookup"><span data-stu-id="c9a37-284">\<xs:element>: contents</span></span>

|<span data-ttu-id="c9a37-285">Conteúdo</span><span class="sxs-lookup"><span data-stu-id="c9a37-285">Contents</span></span>|<span data-ttu-id="c9a37-286">Esquema</span><span class="sxs-lookup"><span data-stu-id="c9a37-286">Schema</span></span>|
|--------------|------------|
|`simpleType`|<span data-ttu-id="c9a37-287">Supported.\*</span><span class="sxs-lookup"><span data-stu-id="c9a37-287">Supported.\*</span></span>|
|`complexType`|<span data-ttu-id="c9a37-288">Supported.\*</span><span class="sxs-lookup"><span data-stu-id="c9a37-288">Supported.\*</span></span>|
|`unique`|<span data-ttu-id="c9a37-289">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="c9a37-289">Ignored.</span></span>|
|`key`|<span data-ttu-id="c9a37-290">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="c9a37-290">Ignored.</span></span>|
|`keyref`|<span data-ttu-id="c9a37-291">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="c9a37-291">Ignored.</span></span>|
|<span data-ttu-id="c9a37-292">(blank)</span><span class="sxs-lookup"><span data-stu-id="c9a37-292">(blank)</span></span>|<span data-ttu-id="c9a37-293">Com suporte.</span><span class="sxs-lookup"><span data-stu-id="c9a37-293">Supported.</span></span>|

<span data-ttu-id="c9a37-294">\* Ao usar o `simpleType` e `complexType,` mapeamento para tipos anônimos é o mesmo para tipos não anônimos, exceto que não há nenhum contrato de dados anônimos e, portanto, um contrato de dados nomeado é criado, com um nome gerado derivado do nome do elemento.</span><span class="sxs-lookup"><span data-stu-id="c9a37-294">\* When using the `simpleType` and `complexType,` mapping for anonymous types is the same as for non-anonymous types, except that there is no anonymous data contracts, and so a named data contract is created, with a generated name derived from the element name.</span></span> <span data-ttu-id="c9a37-295">As regras para tipos anônimos são na lista a seguir:</span><span class="sxs-lookup"><span data-stu-id="c9a37-295">The rules for anonymous types are in the following list:</span></span>

- <span data-ttu-id="c9a37-296">Detalhe de implementação do WCF: Se o `xs:element` nome não contém pontos, o tipo anônimo é mapeado para um tipo interno do tipo de contrato de dados externa.</span><span class="sxs-lookup"><span data-stu-id="c9a37-296">WCF implementation detail: If the `xs:element` name does not contain periods, the anonymous type maps to an inner type of the outer data contract type.</span></span> <span data-ttu-id="c9a37-297">Se o nome contiver períodos, o tipo de contrato de dados resultante é independente (não um tipo interno).</span><span class="sxs-lookup"><span data-stu-id="c9a37-297">If the name contains periods, the resulting data contract type is independent (not an inner type).</span></span>

- <span data-ttu-id="c9a37-298">O nome do contrato de dados gerados de tipo interno é o nome do contrato de dados do tipo externo seguido por um período, o nome do elemento e a cadeia de caracteres "Tipo".</span><span class="sxs-lookup"><span data-stu-id="c9a37-298">The generated data contract name of the inner type is the data contract name of the outer type followed by a period, the name of the element, and the string "Type".</span></span>

- <span data-ttu-id="c9a37-299">Se um dado contrato com esse nome já existir, o nome é feito exclusivo acrescentando "1", "2", "3", e assim por diante até que um nome exclusivo é criado.</span><span class="sxs-lookup"><span data-stu-id="c9a37-299">If a data contract with such a name already exists, the name is made unique by appending "1", "2", "3", and so on until a unique name is created.</span></span>

## <a name="simple-types---xssimpletype"></a><span data-ttu-id="c9a37-300">Tipos simples - \<xs:simpleType ></span><span class="sxs-lookup"><span data-stu-id="c9a37-300">Simple Types - \<xs:simpleType></span></span>

### <a name="xssimpletype-attributes"></a><span data-ttu-id="c9a37-301">\<xs:simpleType >: atributos</span><span class="sxs-lookup"><span data-stu-id="c9a37-301">\<xs:simpleType>: attributes</span></span>

|<span data-ttu-id="c9a37-302">Atributo</span><span class="sxs-lookup"><span data-stu-id="c9a37-302">Attribute</span></span>|<span data-ttu-id="c9a37-303">Esquema</span><span class="sxs-lookup"><span data-stu-id="c9a37-303">Schema</span></span>|
|---------------|------------|
|`final`|<span data-ttu-id="c9a37-304">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="c9a37-304">Ignored.</span></span>|
|`id`|<span data-ttu-id="c9a37-305">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="c9a37-305">Ignored.</span></span>|
|`name`|<span data-ttu-id="c9a37-306">Com suporte, é mapeado para os dados de nome de contrato.</span><span class="sxs-lookup"><span data-stu-id="c9a37-306">Supported, maps to the data contract name.</span></span>|

### <a name="xssimpletype-contents"></a><span data-ttu-id="c9a37-307">\<xs:simpleType>: contents</span><span class="sxs-lookup"><span data-stu-id="c9a37-307">\<xs:simpleType>: contents</span></span>

|<span data-ttu-id="c9a37-308">Conteúdo</span><span class="sxs-lookup"><span data-stu-id="c9a37-308">Contents</span></span>|<span data-ttu-id="c9a37-309">Esquema</span><span class="sxs-lookup"><span data-stu-id="c9a37-309">Schema</span></span>|
|--------------|------------|
|`restriction`|<span data-ttu-id="c9a37-310">Com suporte.</span><span class="sxs-lookup"><span data-stu-id="c9a37-310">Supported.</span></span> <span data-ttu-id="c9a37-311">Mapeia para contratos de dados de enumeração.</span><span class="sxs-lookup"><span data-stu-id="c9a37-311">Maps to enumeration data contracts.</span></span> <span data-ttu-id="c9a37-312">Esse atributo é ignorado se ele não coincide com o padrão da enumeração.</span><span class="sxs-lookup"><span data-stu-id="c9a37-312">This attribute is ignored if it does not match the enumeration pattern.</span></span> <span data-ttu-id="c9a37-313">Consulte o `xs:simpleType` seção de restrições.</span><span class="sxs-lookup"><span data-stu-id="c9a37-313">See the `xs:simpleType` restrictions section.</span></span>|
|`list`|<span data-ttu-id="c9a37-314">Com suporte.</span><span class="sxs-lookup"><span data-stu-id="c9a37-314">Supported.</span></span> <span data-ttu-id="c9a37-315">Mapeia para contratos de dados de enumeração do sinalizador.</span><span class="sxs-lookup"><span data-stu-id="c9a37-315">Maps to flag enumeration data contracts.</span></span> <span data-ttu-id="c9a37-316">Consulte o `xs:simpleType` lista seção.</span><span class="sxs-lookup"><span data-stu-id="c9a37-316">See the `xs:simpleType` lists section.</span></span>|
|`union`|<span data-ttu-id="c9a37-317">Negado.</span><span class="sxs-lookup"><span data-stu-id="c9a37-317">Forbidden.</span></span>|

### <a name="xsrestriction"></a><span data-ttu-id="c9a37-318">\<xs:restriction></span><span class="sxs-lookup"><span data-stu-id="c9a37-318">\<xs:restriction></span></span>

- <span data-ttu-id="c9a37-319">Restrições de tipo complexos têm suporte apenas para base = "`xs:anyType`".</span><span class="sxs-lookup"><span data-stu-id="c9a37-319">Complex type restrictions are supported only for base="`xs:anyType`".</span></span>

- <span data-ttu-id="c9a37-320">As restrições de tipo simples `xs:string` que não têm qualquer facetas de restrição diferentes de `xs:enumeration` são mapeados para os contratos de dados de enumeração.</span><span class="sxs-lookup"><span data-stu-id="c9a37-320">Simple type restrictions of `xs:string` that do not have any restriction facets other than `xs:enumeration` are mapped to enumeration data contracts.</span></span>

- <span data-ttu-id="c9a37-321">Todas as outras restrições de tipo simples são mapeadas para os tipos de que restringem a eles.</span><span class="sxs-lookup"><span data-stu-id="c9a37-321">All other simple type restrictions are mapped to the types they restrict.</span></span> <span data-ttu-id="c9a37-322">Por exemplo, uma restrição `xs:int` mapeia para um número inteiro, assim como `xs:int` em si faz.</span><span class="sxs-lookup"><span data-stu-id="c9a37-322">For example, a restriction of `xs:int` maps to an integer, just as `xs:int` itself does.</span></span> <span data-ttu-id="c9a37-323">Para obter mais informações sobre o mapeamento de tipo primitivo, consulte o mapeamento de tipo/primitivo.</span><span class="sxs-lookup"><span data-stu-id="c9a37-323">For more information about primitive type mapping, see Type/primitive mapping.</span></span>

### <a name="xsrestriction-attributes"></a><span data-ttu-id="c9a37-324">\<xs: Restriction >: atributos</span><span class="sxs-lookup"><span data-stu-id="c9a37-324">\<xs:restriction>: attributes</span></span>

|<span data-ttu-id="c9a37-325">Atributo</span><span class="sxs-lookup"><span data-stu-id="c9a37-325">Attribute</span></span>|<span data-ttu-id="c9a37-326">Esquema</span><span class="sxs-lookup"><span data-stu-id="c9a37-326">Schema</span></span>|
|---------------|------------|
|`base`|<span data-ttu-id="c9a37-327">Deve ser um tipo simple com suporte ou `xs:anyType`.</span><span class="sxs-lookup"><span data-stu-id="c9a37-327">Must be a supported simple type or `xs:anyType`.</span></span>|
|`id`|<span data-ttu-id="c9a37-328">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="c9a37-328">Ignored.</span></span>|

### <a name="xsrestriction-for-all-other-cases-contents"></a><span data-ttu-id="c9a37-329">\<xs: Restriction > todos os outros casos: conteúdo</span><span class="sxs-lookup"><span data-stu-id="c9a37-329">\<xs:restriction> for all other cases: contents</span></span>

|<span data-ttu-id="c9a37-330">Conteúdo</span><span class="sxs-lookup"><span data-stu-id="c9a37-330">Contents</span></span>|<span data-ttu-id="c9a37-331">Esquema</span><span class="sxs-lookup"><span data-stu-id="c9a37-331">Schema</span></span>|
|--------------|------------|
|`simpleType`|<span data-ttu-id="c9a37-332">Se estiver presente, deve ser derivado de um tipo primitivo com suporte.</span><span class="sxs-lookup"><span data-stu-id="c9a37-332">If present, must be derived from a supported primitive type.</span></span>|
|`minExclusive`|<span data-ttu-id="c9a37-333">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="c9a37-333">Ignored.</span></span>|
|`minInclusive`|<span data-ttu-id="c9a37-334">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="c9a37-334">Ignored.</span></span>|
|`maxExclusive`|<span data-ttu-id="c9a37-335">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="c9a37-335">Ignored.</span></span>|
|`maxInclusive`|<span data-ttu-id="c9a37-336">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="c9a37-336">Ignored.</span></span>|
|`totalDigits`|<span data-ttu-id="c9a37-337">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="c9a37-337">Ignored.</span></span>|
|`fractionDigits`|<span data-ttu-id="c9a37-338">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="c9a37-338">Ignored.</span></span>|
|`length`|<span data-ttu-id="c9a37-339">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="c9a37-339">Ignored.</span></span>|
|`minLength`|<span data-ttu-id="c9a37-340">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="c9a37-340">Ignored.</span></span>|
|`maxLength`|<span data-ttu-id="c9a37-341">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="c9a37-341">Ignored.</span></span>|
|`enumeration`|<span data-ttu-id="c9a37-342">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="c9a37-342">Ignored.</span></span>|
|`whiteSpace`|<span data-ttu-id="c9a37-343">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="c9a37-343">Ignored.</span></span>|
|`pattern`|<span data-ttu-id="c9a37-344">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="c9a37-344">Ignored.</span></span>|
|<span data-ttu-id="c9a37-345">(blank)</span><span class="sxs-lookup"><span data-stu-id="c9a37-345">(blank)</span></span>|<span data-ttu-id="c9a37-346">Com suporte.</span><span class="sxs-lookup"><span data-stu-id="c9a37-346">Supported.</span></span>|

## <a name="enumeration"></a><span data-ttu-id="c9a37-347">Enumeração</span><span class="sxs-lookup"><span data-stu-id="c9a37-347">Enumeration</span></span>

### <a name="xsrestriction-for-enumerations-attributes"></a><span data-ttu-id="c9a37-348">\<xs: Restriction > para enumerações: atributos</span><span class="sxs-lookup"><span data-stu-id="c9a37-348">\<xs:restriction> for enumerations: attributes</span></span>

|<span data-ttu-id="c9a37-349">Atributo</span><span class="sxs-lookup"><span data-stu-id="c9a37-349">Attribute</span></span>|<span data-ttu-id="c9a37-350">Esquema</span><span class="sxs-lookup"><span data-stu-id="c9a37-350">Schema</span></span>|
|---------------|------------|
|`base`|<span data-ttu-id="c9a37-351">Se estiver presente, deve ser `xs:string`.</span><span class="sxs-lookup"><span data-stu-id="c9a37-351">If present, must be `xs:string`.</span></span>|
|`id`|<span data-ttu-id="c9a37-352">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="c9a37-352">Ignored.</span></span>|

### <a name="xsrestriction-for-enumerations-contents"></a><span data-ttu-id="c9a37-353">\<xs: Restriction > para enumerações: conteúdo</span><span class="sxs-lookup"><span data-stu-id="c9a37-353">\<xs:restriction> for enumerations: contents</span></span>

|<span data-ttu-id="c9a37-354">Conteúdo</span><span class="sxs-lookup"><span data-stu-id="c9a37-354">Contents</span></span>|<span data-ttu-id="c9a37-355">Esquema</span><span class="sxs-lookup"><span data-stu-id="c9a37-355">Schema</span></span>|
|--------------|------------|
|`simpleType`|<span data-ttu-id="c9a37-356">Se estiver presente, deve ser uma restrição de enumeração com suporte pelo contrato de dados (Esta seção).</span><span class="sxs-lookup"><span data-stu-id="c9a37-356">If present, must be an enumeration restriction supported by the data contract (this section).</span></span>|
|`minExclusive`|<span data-ttu-id="c9a37-357">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="c9a37-357">Ignored.</span></span>|
|`minInclusive`|<span data-ttu-id="c9a37-358">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="c9a37-358">Ignored.</span></span>|
|`maxExclusive`|<span data-ttu-id="c9a37-359">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="c9a37-359">Ignored.</span></span>|
|`maxInclusive`|<span data-ttu-id="c9a37-360">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="c9a37-360">Ignored.</span></span>|
|`totalDigits`|<span data-ttu-id="c9a37-361">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="c9a37-361">Ignored.</span></span>|
|`fractionDigits`|<span data-ttu-id="c9a37-362">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="c9a37-362">Ignored.</span></span>|
|`length`|<span data-ttu-id="c9a37-363">Negado.</span><span class="sxs-lookup"><span data-stu-id="c9a37-363">Forbidden.</span></span>|
|`minLength`|<span data-ttu-id="c9a37-364">Negado.</span><span class="sxs-lookup"><span data-stu-id="c9a37-364">Forbidden.</span></span>|
|`maxLength`|<span data-ttu-id="c9a37-365">Negado.</span><span class="sxs-lookup"><span data-stu-id="c9a37-365">Forbidden.</span></span>|
|`enumeration`|<span data-ttu-id="c9a37-366">Com suporte.</span><span class="sxs-lookup"><span data-stu-id="c9a37-366">Supported.</span></span> <span data-ttu-id="c9a37-367">Enumeração "id" será ignorada e o "valor" é mapeado para o nome do valor no contrato de dados de enumeração.</span><span class="sxs-lookup"><span data-stu-id="c9a37-367">Enumeration "id" is ignored, and "value" maps to the value name in the enumeration data contract.</span></span>|
|`whiteSpace`|<span data-ttu-id="c9a37-368">Negado.</span><span class="sxs-lookup"><span data-stu-id="c9a37-368">Forbidden.</span></span>|
|`pattern`|<span data-ttu-id="c9a37-369">Negado.</span><span class="sxs-lookup"><span data-stu-id="c9a37-369">Forbidden.</span></span>|
|<span data-ttu-id="c9a37-370">(vazio)</span><span class="sxs-lookup"><span data-stu-id="c9a37-370">(empty)</span></span>|<span data-ttu-id="c9a37-371">Com suporte, é mapeado para o tipo de enumeração vazia.</span><span class="sxs-lookup"><span data-stu-id="c9a37-371">Supported, maps to empty enumeration type.</span></span>|

 <span data-ttu-id="c9a37-372">O código a seguir mostra uma classe de enumeração do c#.</span><span class="sxs-lookup"><span data-stu-id="c9a37-372">The following code shows a C# enumeration class.</span></span>

```csharp
public enum MyEnum
{
  first = 3,
  second = 4,
  third =5
}
```

<span data-ttu-id="c9a37-373">Essa classe é mapeada para o esquema a seguir, o `DataContractSerializer`.</span><span class="sxs-lookup"><span data-stu-id="c9a37-373">This class maps to the following schema by the `DataContractSerializer`.</span></span> <span data-ttu-id="c9a37-374">Se os valores de enumeração Iniciar de 1, `xs:annotation` blocos não são gerados.</span><span class="sxs-lookup"><span data-stu-id="c9a37-374">If enumeration values start from 1, `xs:annotation` blocks are not generated.</span></span>

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

### <a name="xslist"></a><span data-ttu-id="c9a37-375">\<xs:list></span><span class="sxs-lookup"><span data-stu-id="c9a37-375">\<xs:list></span></span>

<span data-ttu-id="c9a37-376">`DataContractSerializer` tipos de enumeração de mapas marcados com `System.FlagsAttribute` à `xs:list` derivado de `xs:string`.</span><span class="sxs-lookup"><span data-stu-id="c9a37-376">`DataContractSerializer` maps enumeration types marked with `System.FlagsAttribute` to `xs:list` derived from `xs:string`.</span></span> <span data-ttu-id="c9a37-377">Nenhum outro `xs:list` variações têm suporte.</span><span class="sxs-lookup"><span data-stu-id="c9a37-377">No other `xs:list` variations are supported.</span></span>

### <a name="xslist-attributes"></a><span data-ttu-id="c9a37-378">\<xs: List >: atributos</span><span class="sxs-lookup"><span data-stu-id="c9a37-378">\<xs:list>: attributes</span></span>

|<span data-ttu-id="c9a37-379">Atributo</span><span class="sxs-lookup"><span data-stu-id="c9a37-379">Attribute</span></span>|<span data-ttu-id="c9a37-380">Esquema</span><span class="sxs-lookup"><span data-stu-id="c9a37-380">Schema</span></span>|
|---------------|------------|
|`itemType`|<span data-ttu-id="c9a37-381">Negado.</span><span class="sxs-lookup"><span data-stu-id="c9a37-381">Forbidden.</span></span>|
|`id`|<span data-ttu-id="c9a37-382">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="c9a37-382">Ignored.</span></span>|

### <a name="xslist-contents"></a><span data-ttu-id="c9a37-383">\<xs:list>: contents</span><span class="sxs-lookup"><span data-stu-id="c9a37-383">\<xs:list>: contents</span></span>

|<span data-ttu-id="c9a37-384">Conteúdo</span><span class="sxs-lookup"><span data-stu-id="c9a37-384">Contents</span></span>|<span data-ttu-id="c9a37-385">Esquema</span><span class="sxs-lookup"><span data-stu-id="c9a37-385">Schema</span></span>|
|--------------|------------|
|`simpleType`|<span data-ttu-id="c9a37-386">Deve ser a restrição `xs:string` usando `xs:enumeration` faceta.</span><span class="sxs-lookup"><span data-stu-id="c9a37-386">Must be restriction from `xs:string` using `xs:enumeration` facet.</span></span>|

<span data-ttu-id="c9a37-387">Se o valor de enumeração não segue uma potência de 2 de progressão (padrão para sinalizadores), o valor é armazenado no `xs:annotation/xs:appInfo/ser:EnumerationValue` elemento.</span><span class="sxs-lookup"><span data-stu-id="c9a37-387">If enumeration value does not follow a power of 2 progression (default for Flags), the value is stored in the `xs:annotation/xs:appInfo/ser:EnumerationValue` element.</span></span>

<span data-ttu-id="c9a37-388">Por exemplo, o código a seguir sinaliza um tipo de enumeração.</span><span class="sxs-lookup"><span data-stu-id="c9a37-388">For example, the following code flags an enumeration type.</span></span>

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

<span data-ttu-id="c9a37-389">Esse tipo mapeia para o esquema a seguir.</span><span class="sxs-lookup"><span data-stu-id="c9a37-389">This type maps to the following schema.</span></span>

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

## <a name="inheritance"></a><span data-ttu-id="c9a37-390">Herança</span><span class="sxs-lookup"><span data-stu-id="c9a37-390">Inheritance</span></span>

### <a name="general-rules"></a><span data-ttu-id="c9a37-391">Regras gerais</span><span class="sxs-lookup"><span data-stu-id="c9a37-391">General rules</span></span>

<span data-ttu-id="c9a37-392">Um contrato de dados pode herdar de outro contrato de dados.</span><span class="sxs-lookup"><span data-stu-id="c9a37-392">A data contract can inherit from another data contract.</span></span> <span data-ttu-id="c9a37-393">Tais contratos de dados do mapa em uma base e são derivados por meio de tipos de extensão usando o `<xs:extension>` constructo de esquema XML.</span><span class="sxs-lookup"><span data-stu-id="c9a37-393">Such data contracts map to a base and are derived by extension types using the `<xs:extension>` XML Schema construct.</span></span>

<span data-ttu-id="c9a37-394">Um contrato de dados não pode herdar de um contrato de dados de coleção.</span><span class="sxs-lookup"><span data-stu-id="c9a37-394">A data contract cannot inherit from a collection data contract.</span></span>

<span data-ttu-id="c9a37-395">Por exemplo, o código a seguir é um contrato de dados.</span><span class="sxs-lookup"><span data-stu-id="c9a37-395">For example, the following code is a data contract.</span></span>

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

<span data-ttu-id="c9a37-396">Esse contrato de dados é mapeado para a seguinte declaração de tipo de esquema XML.</span><span class="sxs-lookup"><span data-stu-id="c9a37-396">This data contract maps to the following XML Schema type declaration.</span></span>

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

### <a name="xscomplexcontent-attributes"></a><span data-ttu-id="c9a37-397">\<xs:complexContent >: atributos</span><span class="sxs-lookup"><span data-stu-id="c9a37-397">\<xs:complexContent>: attributes</span></span>

|<span data-ttu-id="c9a37-398">Atributo</span><span class="sxs-lookup"><span data-stu-id="c9a37-398">Attribute</span></span>|<span data-ttu-id="c9a37-399">Esquema</span><span class="sxs-lookup"><span data-stu-id="c9a37-399">Schema</span></span>|
|---------------|------------|
|`id`|<span data-ttu-id="c9a37-400">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="c9a37-400">Ignored.</span></span>|
|`mixed`|<span data-ttu-id="c9a37-401">Deve ser false.</span><span class="sxs-lookup"><span data-stu-id="c9a37-401">Must be false.</span></span>|

### <a name="xscomplexcontent-contents"></a><span data-ttu-id="c9a37-402">\<xs:complexContent>: contents</span><span class="sxs-lookup"><span data-stu-id="c9a37-402">\<xs:complexContent>: contents</span></span>

|<span data-ttu-id="c9a37-403">Conteúdo</span><span class="sxs-lookup"><span data-stu-id="c9a37-403">Contents</span></span>|<span data-ttu-id="c9a37-404">Esquema</span><span class="sxs-lookup"><span data-stu-id="c9a37-404">Schema</span></span>|
|--------------|------------|
|`restriction`|<span data-ttu-id="c9a37-405">Proibido, exceto quando base = "`xs:anyType`".</span><span class="sxs-lookup"><span data-stu-id="c9a37-405">Forbidden, except when base="`xs:anyType`".</span></span> <span data-ttu-id="c9a37-406">A última opção é equivalente a colocar o conteúdo a `xs:restriction` diretamente no contêiner do `xs:complexContent`.</span><span class="sxs-lookup"><span data-stu-id="c9a37-406">The latter is equivalent to placing the content of the `xs:restriction` directly under the container of the `xs:complexContent`.</span></span>|
|`extension`|<span data-ttu-id="c9a37-407">Com suporte.</span><span class="sxs-lookup"><span data-stu-id="c9a37-407">Supported.</span></span> <span data-ttu-id="c9a37-408">Mapeia para a herança de contrato de dados.</span><span class="sxs-lookup"><span data-stu-id="c9a37-408">Maps to data contract inheritance.</span></span>|

### <a name="xsextension-in-xscomplexcontent-attributes"></a><span data-ttu-id="c9a37-409">\<xs: Extension > em \<xs:complexContent >: atributos</span><span class="sxs-lookup"><span data-stu-id="c9a37-409">\<xs:extension> in \<xs:complexContent>: attributes</span></span>

|<span data-ttu-id="c9a37-410">Atributo</span><span class="sxs-lookup"><span data-stu-id="c9a37-410">Attribute</span></span>|<span data-ttu-id="c9a37-411">Esquema</span><span class="sxs-lookup"><span data-stu-id="c9a37-411">Schema</span></span>|
|---------------|------------|
|`id`|<span data-ttu-id="c9a37-412">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="c9a37-412">Ignored.</span></span>|
|`base`|<span data-ttu-id="c9a37-413">Com suporte.</span><span class="sxs-lookup"><span data-stu-id="c9a37-413">Supported.</span></span> <span data-ttu-id="c9a37-414">Mapeia para o contrato de dados base de tipo que este tipo herda.</span><span class="sxs-lookup"><span data-stu-id="c9a37-414">Maps to the base data contract type that this type inherits from.</span></span>|

### <a name="xsextension-in-xscomplexcontent-contents"></a><span data-ttu-id="c9a37-415">\<xs: Extension > em \<xs:complexContent >: conteúdo</span><span class="sxs-lookup"><span data-stu-id="c9a37-415">\<xs:extension> in \<xs:complexContent>: contents</span></span>

<span data-ttu-id="c9a37-416">As regras são os mesmos para `<xs:complexType>` conteúdo.</span><span class="sxs-lookup"><span data-stu-id="c9a37-416">The rules are the same as for `<xs:complexType>` contents.</span></span>

<span data-ttu-id="c9a37-417">Se um `<xs:sequence>` for fornecido, o membro de elementos são mapeados para os membros de dados adicionais que estão presentes no contrato de dados derivado.</span><span class="sxs-lookup"><span data-stu-id="c9a37-417">If an `<xs:sequence>` is provided, its member elements map to additional data members that are present in the derived data contract.</span></span>

<span data-ttu-id="c9a37-418">Se um tipo derivado contiver um elemento com o mesmo nome que um elemento em um tipo base, a declaração de elemento duplicado é mapeado para um membro de dados com um nome que é gerado para serem exclusivos.</span><span class="sxs-lookup"><span data-stu-id="c9a37-418">If a derived type contains an element with the same name as an element in a base type, the duplicate element declaration maps to a data member with a name that is generated to be unique.</span></span> <span data-ttu-id="c9a37-419">Números inteiros positivos são adicionados ao nome do membro de dados ("member1", "membro2" e assim por diante) até encontra um nome exclusivo.</span><span class="sxs-lookup"><span data-stu-id="c9a37-419">Positive integer numbers are added to the data member name ("member1", "member2", and so on) until a unique name is found.</span></span> <span data-ttu-id="c9a37-420">Por outro lado:</span><span class="sxs-lookup"><span data-stu-id="c9a37-420">Conversely:</span></span>

- <span data-ttu-id="c9a37-421">Se um contrato de dados derivado tem um membro com o mesmo nome e tipo de dados como um membro de dados em um contrato de dados base, `DataContractSerializer` gera este elemento correspondente no tipo derivado.</span><span class="sxs-lookup"><span data-stu-id="c9a37-421">If a derived data contract has a data member with the same name and type as a data member in a base data contract, `DataContractSerializer` generates this corresponding element in the derived type.</span></span>

- <span data-ttu-id="c9a37-422">Se um contrato de dados derivado tem um membro de dados com o mesmo nome como um membro de dados em um contrato de dados base, um tipo diferente, mas o `DataContractSerializer` importa um esquema com um elemento do tipo `xs:anyType` em declarações de tipo derivado e de tipo base.</span><span class="sxs-lookup"><span data-stu-id="c9a37-422">If a derived data contract has a data member with the same name as a data member in a base data contract but a different type, the `DataContractSerializer` imports a schema with an element of the type `xs:anyType` in both base type and derived type declarations.</span></span> <span data-ttu-id="c9a37-423">O nome do tipo original é preservado no `xs:annotations/xs:appInfo/ser:ActualType/@Name`.</span><span class="sxs-lookup"><span data-stu-id="c9a37-423">The original type name is preserved in `xs:annotations/xs:appInfo/ser:ActualType/@Name`.</span></span>

<span data-ttu-id="c9a37-424">Ambas as variações podem levar a um esquema com um modelo de conteúdo ambíguo, depende da ordem dos membros de dados respectivo.</span><span class="sxs-lookup"><span data-stu-id="c9a37-424">Both variations may lead to a schema with an ambiguous content model, which depends on the order of the respective data members.</span></span>

## <a name="typeprimitive-mapping"></a><span data-ttu-id="c9a37-425">Mapeamento de tipo/primitivo</span><span class="sxs-lookup"><span data-stu-id="c9a37-425">Type/primitive mapping</span></span>

<span data-ttu-id="c9a37-426">O `DataContractSerializer` usa o seguinte mapeamento para tipos primitivos do esquema XML.</span><span class="sxs-lookup"><span data-stu-id="c9a37-426">The `DataContractSerializer` uses the following mapping for XML Schema primitive types.</span></span>

|<span data-ttu-id="c9a37-427">Tipo XSD</span><span class="sxs-lookup"><span data-stu-id="c9a37-427">XSD type</span></span>|<span data-ttu-id="c9a37-428">Tipo .NET</span><span class="sxs-lookup"><span data-stu-id="c9a37-428">.NET type</span></span>|
|--------------|---------------|
|`anyType`|<span data-ttu-id="c9a37-429"><xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="c9a37-429"><xref:System.Object>.</span></span>|
|`anySimpleType`|<span data-ttu-id="c9a37-430"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="c9a37-430"><xref:System.String>.</span></span>|
|`duration`|<span data-ttu-id="c9a37-431"><xref:System.TimeSpan>.</span><span class="sxs-lookup"><span data-stu-id="c9a37-431"><xref:System.TimeSpan>.</span></span>|
|`dateTime`|<span data-ttu-id="c9a37-432"><xref:System.DateTime>.</span><span class="sxs-lookup"><span data-stu-id="c9a37-432"><xref:System.DateTime>.</span></span>|
|`dateTimeOffset`|<span data-ttu-id="c9a37-433"><xref:System.DateTime> e <xref:System.TimeSpan> para o deslocamento.</span><span class="sxs-lookup"><span data-stu-id="c9a37-433"><xref:System.DateTime> and <xref:System.TimeSpan> for the offset.</span></span> <span data-ttu-id="c9a37-434">Consulte abaixo de serialização de DateTimeOffset.</span><span class="sxs-lookup"><span data-stu-id="c9a37-434">See DateTimeOffset Serialization below.</span></span>|
|`time`|<span data-ttu-id="c9a37-435"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="c9a37-435"><xref:System.String>.</span></span>|
|`date`|<span data-ttu-id="c9a37-436"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="c9a37-436"><xref:System.String>.</span></span>|
|`gYearMonth`|<span data-ttu-id="c9a37-437"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="c9a37-437"><xref:System.String>.</span></span>|
|`gYear`|<span data-ttu-id="c9a37-438"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="c9a37-438"><xref:System.String>.</span></span>|
|`gMonthDay`|<span data-ttu-id="c9a37-439"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="c9a37-439"><xref:System.String>.</span></span>|
|`gDay`|<span data-ttu-id="c9a37-440"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="c9a37-440"><xref:System.String>.</span></span>|
|`gMonth`|<span data-ttu-id="c9a37-441"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="c9a37-441"><xref:System.String>.</span></span>|
|`boolean`|<xref:System.Boolean>|
|`base64Binary`|<span data-ttu-id="c9a37-442">Matriz <xref:System.Byte>.</span><span class="sxs-lookup"><span data-stu-id="c9a37-442"><xref:System.Byte> array.</span></span>|
|`hexBinary`|<span data-ttu-id="c9a37-443"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="c9a37-443"><xref:System.String>.</span></span>|
|`float`|<span data-ttu-id="c9a37-444"><xref:System.Single>.</span><span class="sxs-lookup"><span data-stu-id="c9a37-444"><xref:System.Single>.</span></span>|
|`double`|<span data-ttu-id="c9a37-445"><xref:System.Double>.</span><span class="sxs-lookup"><span data-stu-id="c9a37-445"><xref:System.Double>.</span></span>|
|`anyURI`|<span data-ttu-id="c9a37-446"><xref:System.Uri>.</span><span class="sxs-lookup"><span data-stu-id="c9a37-446"><xref:System.Uri>.</span></span>|
|`QName`|<span data-ttu-id="c9a37-447"><xref:System.Xml.XmlQualifiedName>.</span><span class="sxs-lookup"><span data-stu-id="c9a37-447"><xref:System.Xml.XmlQualifiedName>.</span></span>|
|`string`|<span data-ttu-id="c9a37-448"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="c9a37-448"><xref:System.String>.</span></span>|
|`normalizedString`|<span data-ttu-id="c9a37-449"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="c9a37-449"><xref:System.String>.</span></span>|
|`token`|<span data-ttu-id="c9a37-450"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="c9a37-450"><xref:System.String>.</span></span>|
|`language`|<span data-ttu-id="c9a37-451"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="c9a37-451"><xref:System.String>.</span></span>|
|`Name`|<span data-ttu-id="c9a37-452"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="c9a37-452"><xref:System.String>.</span></span>|
|`NCName`|<span data-ttu-id="c9a37-453"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="c9a37-453"><xref:System.String>.</span></span>|
|`ID`|<span data-ttu-id="c9a37-454"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="c9a37-454"><xref:System.String>.</span></span>|
|`IDREF`|<span data-ttu-id="c9a37-455"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="c9a37-455"><xref:System.String>.</span></span>|
|`IDREFS`|<span data-ttu-id="c9a37-456"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="c9a37-456"><xref:System.String>.</span></span>|
|`ENTITY`|<span data-ttu-id="c9a37-457"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="c9a37-457"><xref:System.String>.</span></span>|
|`ENTITIES`|<span data-ttu-id="c9a37-458"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="c9a37-458"><xref:System.String>.</span></span>|
|`NMTOKEN`|<span data-ttu-id="c9a37-459"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="c9a37-459"><xref:System.String>.</span></span>|
|`NMTOKENS`|<span data-ttu-id="c9a37-460"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="c9a37-460"><xref:System.String>.</span></span>|
|`decimal`|<span data-ttu-id="c9a37-461"><xref:System.Decimal>.</span><span class="sxs-lookup"><span data-stu-id="c9a37-461"><xref:System.Decimal>.</span></span>|
|`integer`|<span data-ttu-id="c9a37-462"><xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="c9a37-462"><xref:System.Int64>.</span></span>|
|`nonPositiveInteger`|<span data-ttu-id="c9a37-463"><xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="c9a37-463"><xref:System.Int64>.</span></span>|
|`negativeInteger`|<span data-ttu-id="c9a37-464"><xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="c9a37-464"><xref:System.Int64>.</span></span>|
|`long`|<span data-ttu-id="c9a37-465"><xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="c9a37-465"><xref:System.Int64>.</span></span>|
|`int`|<span data-ttu-id="c9a37-466"><xref:System.Int32>.</span><span class="sxs-lookup"><span data-stu-id="c9a37-466"><xref:System.Int32>.</span></span>|
|`short`|<span data-ttu-id="c9a37-467"><xref:System.Int16>.</span><span class="sxs-lookup"><span data-stu-id="c9a37-467"><xref:System.Int16>.</span></span>|
|`Byte`|<span data-ttu-id="c9a37-468"><xref:System.SByte>.</span><span class="sxs-lookup"><span data-stu-id="c9a37-468"><xref:System.SByte>.</span></span>|
|`nonNegativeInteger`|<span data-ttu-id="c9a37-469"><xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="c9a37-469"><xref:System.Int64>.</span></span>|
|`unsignedLong`|<span data-ttu-id="c9a37-470"><xref:System.UInt64>.</span><span class="sxs-lookup"><span data-stu-id="c9a37-470"><xref:System.UInt64>.</span></span>|
|`unsignedInt`|<span data-ttu-id="c9a37-471"><xref:System.UInt32>.</span><span class="sxs-lookup"><span data-stu-id="c9a37-471"><xref:System.UInt32>.</span></span>|
|`unsignedShort`|<span data-ttu-id="c9a37-472"><xref:System.UInt16>.</span><span class="sxs-lookup"><span data-stu-id="c9a37-472"><xref:System.UInt16>.</span></span>|
|`unsignedByte`|<span data-ttu-id="c9a37-473"><xref:System.Byte>.</span><span class="sxs-lookup"><span data-stu-id="c9a37-473"><xref:System.Byte>.</span></span>|
|`positiveInteger`|<span data-ttu-id="c9a37-474"><xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="c9a37-474"><xref:System.Int64>.</span></span>|

## <a name="iserializable-types-mapping"></a><span data-ttu-id="c9a37-475">Mapeamento de tipos iSerializable</span><span class="sxs-lookup"><span data-stu-id="c9a37-475">ISerializable types mapping</span></span>

<span data-ttu-id="c9a37-476">No .NET Framework versão 1.0, <xref:System.Runtime.Serialization.ISerializable> foi introduzido como um mecanismo geral para serializar objetos para a transferência de dados ou de persistência.</span><span class="sxs-lookup"><span data-stu-id="c9a37-476">In .NET Framework version 1.0, <xref:System.Runtime.Serialization.ISerializable> was introduced as a general mechanism to serialize objects for persistence or data transfer.</span></span> <span data-ttu-id="c9a37-477">Há muitos tipos do .NET Framework que implementam `ISerializable` e que podem ser passados entre aplicativos.</span><span class="sxs-lookup"><span data-stu-id="c9a37-477">There are many .NET Framework types that implement `ISerializable` and that can be passed between applications.</span></span> <span data-ttu-id="c9a37-478"><xref:System.Runtime.Serialization.DataContractSerializer> Naturalmente, fornece suporte para `ISerializable` classes.</span><span class="sxs-lookup"><span data-stu-id="c9a37-478"><xref:System.Runtime.Serialization.DataContractSerializer> naturally provides support for `ISerializable` classes.</span></span> <span data-ttu-id="c9a37-479">O `DataContractSerializer` mapeia `ISerializable` tipos de esquema de implementação que diferem apenas pelo QName (nome qualificado) do tipo e são efetivamente as coleções de propriedade.</span><span class="sxs-lookup"><span data-stu-id="c9a37-479">The `DataContractSerializer` maps `ISerializable` implementation schema types that differ only by the QName (qualified name) of the type and are effectively property collections.</span></span> <span data-ttu-id="c9a37-480">Por exemplo, o `DataContractSerializer` mapeia <xref:System.Exception> para o seguinte tipo XSD no `http://schemas.datacontract.org/2004/07/System` namespace.</span><span class="sxs-lookup"><span data-stu-id="c9a37-480">For example, the `DataContractSerializer` maps <xref:System.Exception> to the following XSD type in the `http://schemas.datacontract.org/2004/07/System` namespace.</span></span>

```xml
<xs:complexType name="Exception">
 <xs:sequence>
  <xs:any minOccurs="0" maxOccurs="unbounded"
      namespace="##local" processContents="skip"/>
 </xs:sequence>
 <xs:attribute ref="ser:FactoryType"/>
</xs:complexType>
```

<span data-ttu-id="c9a37-481">O atributo opcional `ser:FactoryType` declarado na serialização de contrato de dados de esquema faz referência a uma classe de fábrica que pode desserializar o tipo.</span><span class="sxs-lookup"><span data-stu-id="c9a37-481">The optional attribute `ser:FactoryType` declared in the Data Contract Serialization schema references a factory class that can deserialize the type.</span></span> <span data-ttu-id="c9a37-482">A classe de fábrica deve ser parte da coleção de tipos conhecidos a `DataContractSerializer` da instância que está sendo usado.</span><span class="sxs-lookup"><span data-stu-id="c9a37-482">The factory class must be part of the known types collection of the `DataContractSerializer` instance being used.</span></span> <span data-ttu-id="c9a37-483">Para obter mais informações sobre tipos conhecidos, consulte [tipos conhecidos de contrato de dados](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="c9a37-483">For more information about known types, see [Data Contract Known Types](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span>

## <a name="datacontract-serialization-schema"></a><span data-ttu-id="c9a37-484">Esquema de serialização DataContract</span><span class="sxs-lookup"><span data-stu-id="c9a37-484">DataContract Serialization Schema</span></span>

<span data-ttu-id="c9a37-485">Um número de esquemas exportados pelo `DataContractSerializer` usar tipos de elementos e atributos de um namespace especial de serialização do contrato de dados:</span><span class="sxs-lookup"><span data-stu-id="c9a37-485">A number of schemas exported by the `DataContractSerializer` use types, elements, and attributes from a special Data Contract Serialization namespace:</span></span>

`http://schemas.microsoft.com/2003/10/Serialization`

<span data-ttu-id="c9a37-486">A seguir está uma declaração de esquema de serialização do contrato de dados completa.</span><span class="sxs-lookup"><span data-stu-id="c9a37-486">The following is a complete Data Contract Serialization schema declaration.</span></span>

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

<span data-ttu-id="c9a37-487">O exemplo a seguir deve ser observados:</span><span class="sxs-lookup"><span data-stu-id="c9a37-487">The following should be noted:</span></span>

- <span data-ttu-id="c9a37-488">`ser:char` é introduzido para representar caracteres Unicode do tipo <xref:System.Char>.</span><span class="sxs-lookup"><span data-stu-id="c9a37-488">`ser:char` is introduced to represent Unicode characters of type <xref:System.Char>.</span></span>

- <span data-ttu-id="c9a37-489">O `valuespace` dos `xs:duration` é reduzida a um conjunto ordenado para que ele pode ser mapeado para um <xref:System.TimeSpan>.</span><span class="sxs-lookup"><span data-stu-id="c9a37-489">The `valuespace` of `xs:duration` is reduced to an ordered set so that it can be mapped to a <xref:System.TimeSpan>.</span></span>

- <span data-ttu-id="c9a37-490">`FactoryType` é usado em esquemas exportadas de tipos que são derivados de <xref:System.Runtime.Serialization.ISerializable>.</span><span class="sxs-lookup"><span data-stu-id="c9a37-490">`FactoryType` is used in schemas exported from types that are derived from <xref:System.Runtime.Serialization.ISerializable>.</span></span>

## <a name="importing-non-datacontract-schemas"></a><span data-ttu-id="c9a37-491">Importando esquemas não DataContract</span><span class="sxs-lookup"><span data-stu-id="c9a37-491">Importing non-DataContract schemas</span></span>

<span data-ttu-id="c9a37-492">`DataContractSerializer` tem o `ImportXmlTypes` opção para permitir que a importação de esquemas que não estão em conformidade com o `DataContractSerializer` perfil XSD (consulte a <xref:System.Runtime.Serialization.XsdDataContractImporter.Options%2A> propriedade).</span><span class="sxs-lookup"><span data-stu-id="c9a37-492">`DataContractSerializer` has the `ImportXmlTypes` option to allow import of schemas that do not conform to the `DataContractSerializer` XSD profile (see the <xref:System.Runtime.Serialization.XsdDataContractImporter.Options%2A> property).</span></span> <span data-ttu-id="c9a37-493">Definir essa opção como `true` permite a aceitação dos tipos de esquema não conformes e mapeando-os para a implementação a seguir <xref:System.Xml.Serialization.IXmlSerializable> encapsulando uma matriz de <xref:System.Xml.XmlNode> (difere apenas o nome de classe).</span><span class="sxs-lookup"><span data-stu-id="c9a37-493">Setting this option to `true` enables acceptance of non-conforming schema types and mapping them to the following implementation, <xref:System.Xml.Serialization.IXmlSerializable> wrapping an array of <xref:System.Xml.XmlNode> (only the class name differs).</span></span>

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

## <a name="datetimeoffset-serialization"></a><span data-ttu-id="c9a37-494">Serialização de DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="c9a37-494">DateTimeOffset Serialization</span></span>

<span data-ttu-id="c9a37-495">O <xref:System.DateTimeOffset> não é tratado como um tipo primitivo.</span><span class="sxs-lookup"><span data-stu-id="c9a37-495">The <xref:System.DateTimeOffset> is not treated as a primitive type.</span></span> <span data-ttu-id="c9a37-496">Em vez disso, ele é serializado como um elemento complexo com duas partes.</span><span class="sxs-lookup"><span data-stu-id="c9a37-496">Instead, it is serialized as a complex element with two parts.</span></span> <span data-ttu-id="c9a37-497">A primeira parte representa a hora de data e a segunda parte representa o deslocamento de data hora.</span><span class="sxs-lookup"><span data-stu-id="c9a37-497">The first part represents the date time, and the second part represents the offset from the date time.</span></span> <span data-ttu-id="c9a37-498">Um exemplo de um valor DateTimeOffset serializado é mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="c9a37-498">An example of a serialized DateTimeOffset value is shown in the following code.</span></span>

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

<span data-ttu-id="c9a37-499">O esquema é da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="c9a37-499">The schema is as follows.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="c9a37-500">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c9a37-500">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- <xref:System.Runtime.Serialization.XsdDataContractImporter>
- [<span data-ttu-id="c9a37-501">Usando contratos de dados</span><span class="sxs-lookup"><span data-stu-id="c9a37-501">Using Data Contracts</span></span>](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
