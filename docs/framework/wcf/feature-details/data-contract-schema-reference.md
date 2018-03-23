---
title: Referência de esquema de contrato de dados
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- data contracts [WCF], schema reference
ms.assetid: 9ebb0ebe-8166-4c93-980a-7c8f1f38f7c0
caps.latest.revision: ''
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 57ccc812aab5df0a9acd99bdcde327d56e4bad8d
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/23/2018
---
# <a name="data-contract-schema-reference"></a><span data-ttu-id="f2c42-102">Referência de esquema de contrato de dados</span><span class="sxs-lookup"><span data-stu-id="f2c42-102">Data Contract Schema Reference</span></span>
<span data-ttu-id="f2c42-103">Este tópico descreve o subconjunto do esquema XML (XSD) usado pelo <xref:System.Runtime.Serialization.DataContractSerializer> para descrever o common language runtime (CLR) tipos de serialização de XML.</span><span class="sxs-lookup"><span data-stu-id="f2c42-103">This topic describes the subset of the XML Schema (XSD) used by <xref:System.Runtime.Serialization.DataContractSerializer> to describe common language runtime (CLR) types for XML serialization.</span></span>  
  
## <a name="datacontractserializer-mappings"></a><span data-ttu-id="f2c42-104">Mapeamentos de DataContractSerializer</span><span class="sxs-lookup"><span data-stu-id="f2c42-104">DataContractSerializer Mappings</span></span>  
 <span data-ttu-id="f2c42-105">O `DataContractSerializer` mapeia tipos CLR para XSD quando metadados exportado de um [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] usando um ponto de extremidade de metadados de serviço ou o [Ferramenta Utilitária de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="f2c42-105">The `DataContractSerializer` maps CLR types to XSD when metadata is exported from a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service using a metadata endpoint or the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="f2c42-106"> [O serializador de contrato de dados](../../../../docs/framework/wcf/feature-details/data-contract-serializer.md).</span><span class="sxs-lookup"><span data-stu-id="f2c42-106"> [Data Contract Serializer](../../../../docs/framework/wcf/feature-details/data-contract-serializer.md).</span></span>  
  
 <span data-ttu-id="f2c42-107">O `DataContractSerializer` também mapeia XSD para tipos CLR quando Svcutil.exe é usada para acessar documentos WSDL Web Services Description Language () ou XSD e gerar contratos de dados para serviços ou clientes.</span><span class="sxs-lookup"><span data-stu-id="f2c42-107">The `DataContractSerializer` also maps XSD to CLR types when Svcutil.exe is used to access Web Services Description Language (WSDL) or XSD documents and generate data contracts for services or clients.</span></span>  
  
 <span data-ttu-id="f2c42-108">Somente as instâncias de esquema XML que atendem aos requisitos mencionados neste documento podem ser mapeadas para tipos CLR usando `DataContractSerializer`.</span><span class="sxs-lookup"><span data-stu-id="f2c42-108">Only XML Schema instances that conform to requirements stated in this document can be mapped to CLR types using `DataContractSerializer`.</span></span>  
  
### <a name="support-levels"></a><span data-ttu-id="f2c42-109">Níveis de suporte</span><span class="sxs-lookup"><span data-stu-id="f2c42-109">Support Levels</span></span>  
 <span data-ttu-id="f2c42-110">O `DataContractSerializer` fornece os seguintes níveis de suporte para um determinado recurso de esquema XML:</span><span class="sxs-lookup"><span data-stu-id="f2c42-110">The `DataContractSerializer` provides the following levels of support for a given XML Schema feature:</span></span>  
  
-   <span data-ttu-id="f2c42-111">**Suporte para**.</span><span class="sxs-lookup"><span data-stu-id="f2c42-111">**Supported**.</span></span> <span data-ttu-id="f2c42-112">Não há mapeamento explícito de usar esse recurso CLR tipos ou atributos (ou ambos) `DataContractSerializer`.</span><span class="sxs-lookup"><span data-stu-id="f2c42-112">There is explicit mapping from this feature to CLR types or attributes (or both) using `DataContractSerializer`.</span></span>  
  
-   <span data-ttu-id="f2c42-113">**Ignored**.</span><span class="sxs-lookup"><span data-stu-id="f2c42-113">**Ignored**.</span></span> <span data-ttu-id="f2c42-114">O recurso é permitido em esquemas importadas pela `DataContractSerializer`, mas não tem nenhum efeito na geração de código.</span><span class="sxs-lookup"><span data-stu-id="f2c42-114">The feature is allowed in schemas imported by the `DataContractSerializer`, but has no effect on code generation.</span></span>  
  
-   <span data-ttu-id="f2c42-115">**Proibido**.</span><span class="sxs-lookup"><span data-stu-id="f2c42-115">**Forbidden**.</span></span> <span data-ttu-id="f2c42-116">O `DataContractSerializer` não oferece suporte à importação de um esquema usando o recurso.</span><span class="sxs-lookup"><span data-stu-id="f2c42-116">The `DataContractSerializer` does not support importing a schema using the feature.</span></span> <span data-ttu-id="f2c42-117">Por exemplo, Svcutil.exe, ao acessar um WSDL com um esquema que usa o recurso, volte a usar o <xref:System.Xml.Serialization.XmlSerializer> em vez disso.</span><span class="sxs-lookup"><span data-stu-id="f2c42-117">For example, Svcutil.exe, when accessing a WSDL with a schema that uses such a feature, falls back to using the <xref:System.Xml.Serialization.XmlSerializer> instead.</span></span> <span data-ttu-id="f2c42-118">Isso ocorre por padrão.</span><span class="sxs-lookup"><span data-stu-id="f2c42-118">This is by default.</span></span>  
  
## <a name="general-information"></a><span data-ttu-id="f2c42-119">Informações gerais</span><span class="sxs-lookup"><span data-stu-id="f2c42-119">General Information</span></span>  
  
-   <span data-ttu-id="f2c42-120">O namespace do esquema é descrito em [esquema XML](http://go.microsoft.com/fwlink/?LinkId=95475).</span><span class="sxs-lookup"><span data-stu-id="f2c42-120">The schema namespace is described at [XML Schema](http://go.microsoft.com/fwlink/?LinkId=95475).</span></span> <span data-ttu-id="f2c42-121">O prefixo "xs" é usado neste documento.</span><span class="sxs-lookup"><span data-stu-id="f2c42-121">The prefix "xs" is used in this document.</span></span>  
  
-   <span data-ttu-id="f2c42-122">Todos os atributos com um namespace do esquema não são ignorados.</span><span class="sxs-lookup"><span data-stu-id="f2c42-122">Any attributes with a non-schema namespace are ignored.</span></span>  
  
-   <span data-ttu-id="f2c42-123">Quaisquer anotações (exceto as descritas neste documento) são ignoradas.</span><span class="sxs-lookup"><span data-stu-id="f2c42-123">Any annotations (except for those described in this document) are ignored.</span></span>  
  
### <a name="xsschema-attributes"></a><span data-ttu-id="f2c42-124">\<xs: schema >: atributos</span><span class="sxs-lookup"><span data-stu-id="f2c42-124">\<xs:schema>: attributes</span></span>  
  
|<span data-ttu-id="f2c42-125">Atributo</span><span class="sxs-lookup"><span data-stu-id="f2c42-125">Attribute</span></span>|<span data-ttu-id="f2c42-126">DataContract</span><span class="sxs-lookup"><span data-stu-id="f2c42-126">DataContract</span></span>|  
|---------------|------------------|  
|`attributeFormDefault`|<span data-ttu-id="f2c42-127">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="f2c42-127">Ignored.</span></span>|  
|`blockDefault`|<span data-ttu-id="f2c42-128">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="f2c42-128">Ignored.</span></span>|  
|`elementFormDefault`|<span data-ttu-id="f2c42-129">Deve ser qualificado.</span><span class="sxs-lookup"><span data-stu-id="f2c42-129">Must be qualified.</span></span> <span data-ttu-id="f2c42-130">Todos os elementos devem ser qualificados para um esquema para serem suportados por `DataContractSerializer`.</span><span class="sxs-lookup"><span data-stu-id="f2c42-130">All elements must be qualified for a schema to be supported by `DataContractSerializer`.</span></span> <span data-ttu-id="f2c42-131">Isso pode ser feito configurando xs:schema/@elementFormDefault "qualified" ou definindo xs:element/@form como "qualified" na declaração de cada elemento individual.</span><span class="sxs-lookup"><span data-stu-id="f2c42-131">This can be accomplished by either setting xs:schema/@elementFormDefault to "qualified" or by setting xs:element/@form to "qualified" on each individual element declaration.</span></span>|  
|`finalDefault`|<span data-ttu-id="f2c42-132">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="f2c42-132">Ignored.</span></span>|  
|`Id`|<span data-ttu-id="f2c42-133">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="f2c42-133">Ignored.</span></span>|  
|`targetNamespace`|<span data-ttu-id="f2c42-134">Suporte e mapeado para o namespace de contrato de dados.</span><span class="sxs-lookup"><span data-stu-id="f2c42-134">Supported and mapped to the data contract namespace.</span></span> <span data-ttu-id="f2c42-135">Se esse atributo não for especificado, o namespace em branco será usado.</span><span class="sxs-lookup"><span data-stu-id="f2c42-135">If this attribute is not specified, the blank namespace is used.</span></span> <span data-ttu-id="f2c42-136">Não pode ser o namespace reservado http://schemas.microsoft.com/2003/10/Serialization/.</span><span class="sxs-lookup"><span data-stu-id="f2c42-136">Cannot be the reserved namespace http://schemas.microsoft.com/2003/10/Serialization/.</span></span>|  
|`version`|<span data-ttu-id="f2c42-137">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="f2c42-137">Ignored.</span></span>|  
  
### <a name="xsschema-contents"></a><span data-ttu-id="f2c42-138">\<xs:schema>: contents</span><span class="sxs-lookup"><span data-stu-id="f2c42-138">\<xs:schema>: contents</span></span>  
  
|<span data-ttu-id="f2c42-139">Conteúdo</span><span class="sxs-lookup"><span data-stu-id="f2c42-139">Contents</span></span>|<span data-ttu-id="f2c42-140">Esquema</span><span class="sxs-lookup"><span data-stu-id="f2c42-140">Schema</span></span>|  
|--------------|------------|  
|`include`|<span data-ttu-id="f2c42-141">Com suporte.</span><span class="sxs-lookup"><span data-stu-id="f2c42-141">Supported.</span></span> <span data-ttu-id="f2c42-142">`DataContractSerializer` dá suporte a xs: incluir e xs:import.</span><span class="sxs-lookup"><span data-stu-id="f2c42-142">`DataContractSerializer` supports xs:include and xs:import.</span></span> <span data-ttu-id="f2c42-143">No entanto, o Svcutil.exe restringe seguir `xs:include/@schemaLocation` e `xs:import/@location` referencia quando metadados é carregado de um arquivo local.</span><span class="sxs-lookup"><span data-stu-id="f2c42-143">However, Svcutil.exe restricts following `xs:include/@schemaLocation` and `xs:import/@location` references when metadata is loaded from a local file.</span></span> <span data-ttu-id="f2c42-144">A lista de arquivos de esquema deve ser passada por meio de um mecanismo fora de banda e não por `include` nesse caso; `include`documentos de esquema d são ignorados.</span><span class="sxs-lookup"><span data-stu-id="f2c42-144">The list of schema files must be passed through an out-of-band mechanism and not through `include` in this case; `include`d schema documents are ignored.</span></span>|  
|`redefine`|<span data-ttu-id="f2c42-145">Negado.</span><span class="sxs-lookup"><span data-stu-id="f2c42-145">Forbidden.</span></span> <span data-ttu-id="f2c42-146">O uso de `xs:redefine` é proibida pelo `DataContractSerializer` por motivos de segurança: `x:redefine` requer `schemaLocation` ser seguidas.</span><span class="sxs-lookup"><span data-stu-id="f2c42-146">The use of `xs:redefine` is forbidden by `DataContractSerializer` for security reasons: `x:redefine` requires `schemaLocation` to be followed.</span></span> <span data-ttu-id="f2c42-147">Em determinadas circunstâncias, Svcutil.exe usando DataContract restringe o uso de `schemaLocation`.</span><span class="sxs-lookup"><span data-stu-id="f2c42-147">In certain circumstances, Svcutil.exe using DataContract restricts use of `schemaLocation`.</span></span>|  
|`import`|<span data-ttu-id="f2c42-148">Com suporte.</span><span class="sxs-lookup"><span data-stu-id="f2c42-148">Supported.</span></span> <span data-ttu-id="f2c42-149">`DataContractSerializer` dá suporte a `xs:include` e `xs:import`.</span><span class="sxs-lookup"><span data-stu-id="f2c42-149">`DataContractSerializer` supports `xs:include` and `xs:import`.</span></span> <span data-ttu-id="f2c42-150">No entanto, o Svcutil.exe restringe seguir `xs:include/@schemaLocation` e `xs:import/@location` referencia quando metadados é carregado de um arquivo local.</span><span class="sxs-lookup"><span data-stu-id="f2c42-150">However, Svcutil.exe restricts following `xs:include/@schemaLocation` and `xs:import/@location` references when metadata is loaded from a local file.</span></span> <span data-ttu-id="f2c42-151">A lista de arquivos de esquema deve ser passada por meio de um mecanismo fora de banda e não por `include` nesse caso; `include`documentos de esquema d são ignorados.</span><span class="sxs-lookup"><span data-stu-id="f2c42-151">The list of schema files must be passed through an out-of-band mechanism and not through `include` in this case; `include`d schema documents are ignored.</span></span>|  
|`simpleType`|<span data-ttu-id="f2c42-152">Com suporte.</span><span class="sxs-lookup"><span data-stu-id="f2c42-152">Supported.</span></span> <span data-ttu-id="f2c42-153">Consulte o `xs:simpleType` seção.</span><span class="sxs-lookup"><span data-stu-id="f2c42-153">See the `xs:simpleType` section.</span></span>|  
|`complexType`|<span data-ttu-id="f2c42-154">Suporte de mapas para contratos de dados.</span><span class="sxs-lookup"><span data-stu-id="f2c42-154">Supported, maps to data contracts.</span></span> <span data-ttu-id="f2c42-155">Consulte o `xs:complexType` seção.</span><span class="sxs-lookup"><span data-stu-id="f2c42-155">See the `xs:complexType` section.</span></span>|  
|`group`|<span data-ttu-id="f2c42-156">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="f2c42-156">Ignored.</span></span> <span data-ttu-id="f2c42-157">`DataContractSerializer` não suporta o uso de `xs:group`, `xs:attributeGroup`, e `xs:attribute`.</span><span class="sxs-lookup"><span data-stu-id="f2c42-157">`DataContractSerializer` does not support use of `xs:group`, `xs:attributeGroup`, and `xs:attribute`.</span></span> <span data-ttu-id="f2c42-158">Essas declarações são ignoradas como filhos do `xs:schema`, mas não pode ser referenciado no `complexType` ou outras construções com suporte.</span><span class="sxs-lookup"><span data-stu-id="f2c42-158">These declarations are ignored as children of `xs:schema`, but cannot be referenced from within `complexType` or other supported constructs.</span></span>|  
|`attributeGroup`|<span data-ttu-id="f2c42-159">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="f2c42-159">Ignored.</span></span> <span data-ttu-id="f2c42-160">`DataContractSerializer` não suporta o uso de `xs:group`, `xs:attributeGroup`, e `xs:attribute`.</span><span class="sxs-lookup"><span data-stu-id="f2c42-160">`DataContractSerializer` does not support use of `xs:group`, `xs:attributeGroup`, and `xs:attribute`.</span></span> <span data-ttu-id="f2c42-161">Essas declarações são ignoradas como filhos do `xs:schema`, mas não pode ser referenciado no `complexType` ou outras construções com suporte.</span><span class="sxs-lookup"><span data-stu-id="f2c42-161">These declarations are ignored as children of `xs:schema`, but cannot be referenced from within `complexType` or other supported constructs.</span></span>|  
|`element`|<span data-ttu-id="f2c42-162">Com suporte.</span><span class="sxs-lookup"><span data-stu-id="f2c42-162">Supported.</span></span> <span data-ttu-id="f2c42-163">Consulte a declaração de elemento Global (Buições).</span><span class="sxs-lookup"><span data-stu-id="f2c42-163">See Global Element Declaration (GED).</span></span>|  
|`attribute`|<span data-ttu-id="f2c42-164">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="f2c42-164">Ignored.</span></span> <span data-ttu-id="f2c42-165">`DataContractSerializer` não suporta o uso de `xs:group`, `xs:attributeGroup`, e `xs:attribute`.</span><span class="sxs-lookup"><span data-stu-id="f2c42-165">`DataContractSerializer` does not support use of `xs:group`, `xs:attributeGroup`, and `xs:attribute`.</span></span> <span data-ttu-id="f2c42-166">Essas declarações são ignoradas como filhos do `xs:schema`, mas não pode ser referenciado no `complexType` ou outras construções com suporte.</span><span class="sxs-lookup"><span data-stu-id="f2c42-166">These declarations are ignored as children of `xs:schema`, but cannot be referenced from within `complexType` or other supported constructs.</span></span>|  
|`notation`|<span data-ttu-id="f2c42-167">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="f2c42-167">Ignored.</span></span>|  
  
## <a name="complex-types--xscomplextype"></a><span data-ttu-id="f2c42-168">Tipos complexos – \<xs:complexType ></span><span class="sxs-lookup"><span data-stu-id="f2c42-168">Complex Types – \<xs:complexType></span></span>  
  
### <a name="general-information"></a><span data-ttu-id="f2c42-169">Informações gerais</span><span class="sxs-lookup"><span data-stu-id="f2c42-169">General Information</span></span>  
 <span data-ttu-id="f2c42-170">Cada tipo complexo \<xs:complexType > é mapeado para um contrato de dados.</span><span class="sxs-lookup"><span data-stu-id="f2c42-170">Each complex type \<xs:complexType> maps to a data contract.</span></span>  
  
### <a name="xscomplextype-attributes"></a><span data-ttu-id="f2c42-171">\<xs:complexType >: atributos</span><span class="sxs-lookup"><span data-stu-id="f2c42-171">\<xs:complexType>: attributes</span></span>  
  
|<span data-ttu-id="f2c42-172">Atributo</span><span class="sxs-lookup"><span data-stu-id="f2c42-172">Attribute</span></span>|<span data-ttu-id="f2c42-173">Esquema</span><span class="sxs-lookup"><span data-stu-id="f2c42-173">Schema</span></span>|  
|---------------|------------|  
|`abstract`|<span data-ttu-id="f2c42-174">Deve ser false (padrão).</span><span class="sxs-lookup"><span data-stu-id="f2c42-174">Must be false (default).</span></span>|  
|`block`|<span data-ttu-id="f2c42-175">Negado.</span><span class="sxs-lookup"><span data-stu-id="f2c42-175">Forbidden.</span></span>|  
|`final`|<span data-ttu-id="f2c42-176">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="f2c42-176">Ignored.</span></span>|  
|`id`|<span data-ttu-id="f2c42-177">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="f2c42-177">Ignored.</span></span>|  
|`mixed`|<span data-ttu-id="f2c42-178">Deve ser false (padrão).</span><span class="sxs-lookup"><span data-stu-id="f2c42-178">Must be false (default).</span></span>|  
|`name`|<span data-ttu-id="f2c42-179">Suporte e mapeado para o nome do contrato de dados.</span><span class="sxs-lookup"><span data-stu-id="f2c42-179">Supported and mapped to the data contract name.</span></span> <span data-ttu-id="f2c42-180">Se houver pontos no nome, é feita uma tentativa para mapear o tipo para um tipo interno.</span><span class="sxs-lookup"><span data-stu-id="f2c42-180">If there are periods in the name, an attempt is made to map the type to an inner type.</span></span> <span data-ttu-id="f2c42-181">Por exemplo, um tipo complexo chamado `A.B` é mapeado para um contrato de dados tipo que é um tipo interno de um tipo com o nome de contrato de dados `A`, mas somente se o tipo de contrato de tal um tipo de dados existe.</span><span class="sxs-lookup"><span data-stu-id="f2c42-181">For example, a complex type named `A.B` maps to a data contract type that is an inner type of a type with the data contract name `A`, but only if such a data contract type exists.</span></span> <span data-ttu-id="f2c42-182">Mais de um nível de aninhamento é possível: por exemplo, `A.B.C` pode ser um tipo interno, mas somente se `A` e `A.B` existem.</span><span class="sxs-lookup"><span data-stu-id="f2c42-182">More than one level of nesting is possible: for example, `A.B.C` can be an inner type, but only if `A` and `A.B` both exist.</span></span>|  
  
### <a name="xscomplextype-contents"></a><span data-ttu-id="f2c42-183">\<xs:complexType>: contents</span><span class="sxs-lookup"><span data-stu-id="f2c42-183">\<xs:complexType>: contents</span></span>  
  
|<span data-ttu-id="f2c42-184">Conteúdo</span><span class="sxs-lookup"><span data-stu-id="f2c42-184">Contents</span></span>|<span data-ttu-id="f2c42-185">Esquema</span><span class="sxs-lookup"><span data-stu-id="f2c42-185">Schema</span></span>|  
|--------------|------------|  
|`simpleContent`|<span data-ttu-id="f2c42-186">As extensões são proibidas.</span><span class="sxs-lookup"><span data-stu-id="f2c42-186">Extensions are forbidden.</span></span><br /><br /> <span data-ttu-id="f2c42-187">Restrição só é permitida em `anySimpleType`.</span><span class="sxs-lookup"><span data-stu-id="f2c42-187">Restriction is allowed only from `anySimpleType`.</span></span>|  
|`complexContent`|<span data-ttu-id="f2c42-188">Com suporte.</span><span class="sxs-lookup"><span data-stu-id="f2c42-188">Supported.</span></span> <span data-ttu-id="f2c42-189">Consulte "Herança".</span><span class="sxs-lookup"><span data-stu-id="f2c42-189">See "Inheritance".</span></span>|  
|`group`|<span data-ttu-id="f2c42-190">Negado.</span><span class="sxs-lookup"><span data-stu-id="f2c42-190">Forbidden.</span></span>|  
|`all`|<span data-ttu-id="f2c42-191">Negado.</span><span class="sxs-lookup"><span data-stu-id="f2c42-191">Forbidden.</span></span>|  
|`choice`|<span data-ttu-id="f2c42-192">Proibido</span><span class="sxs-lookup"><span data-stu-id="f2c42-192">Forbidden</span></span>|  
|`sequence`|<span data-ttu-id="f2c42-193">Suporte de mapas para os membros de dados de um contrato de dados.</span><span class="sxs-lookup"><span data-stu-id="f2c42-193">Supported, maps to data members of a data contract.</span></span>|  
|`attribute`|<span data-ttu-id="f2c42-194">Proibido, mesmo que use = "prohibited" (com uma exceção).</span><span class="sxs-lookup"><span data-stu-id="f2c42-194">Forbidden, even if use="prohibited" (with one exception).</span></span> <span data-ttu-id="f2c42-195">Há suporte para apenas os atributos opcionais do namespace do esquema padrão de serialização.</span><span class="sxs-lookup"><span data-stu-id="f2c42-195">Only optional attributes from the Standard Serialization Schema namespace are supported.</span></span> <span data-ttu-id="f2c42-196">Eles não são mapeados para os membros de dados no modelo de programação de contrato de dados.</span><span class="sxs-lookup"><span data-stu-id="f2c42-196">They do not map to data members in the data contract programming model.</span></span> <span data-ttu-id="f2c42-197">Atualmente, apenas um desses atributos tem um significado e é discutido na seção de ISerializable.</span><span class="sxs-lookup"><span data-stu-id="f2c42-197">Currently, only one such attribute has meaning and is discussed in the ISerializable section.</span></span> <span data-ttu-id="f2c42-198">Todos os outros são ignorados.</span><span class="sxs-lookup"><span data-stu-id="f2c42-198">All others are ignored.</span></span>|  
|`attributeGroup`|<span data-ttu-id="f2c42-199">Negado.</span><span class="sxs-lookup"><span data-stu-id="f2c42-199">Forbidden.</span></span> <span data-ttu-id="f2c42-200">No [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] versão v1, `DataContractSerializer` ignora a presença de `attributeGroup` em `xs:complexType`.</span><span class="sxs-lookup"><span data-stu-id="f2c42-200">In the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] v1 release, `DataContractSerializer` ignores the presence of `attributeGroup` inside `xs:complexType`.</span></span>|  
|`anyAttribute`|<span data-ttu-id="f2c42-201">Negado.</span><span class="sxs-lookup"><span data-stu-id="f2c42-201">Forbidden.</span></span>|  
|<span data-ttu-id="f2c42-202">(vazio)</span><span class="sxs-lookup"><span data-stu-id="f2c42-202">(empty)</span></span>|<span data-ttu-id="f2c42-203">Mapeia para um contrato de dados com nenhum membro de dados.</span><span class="sxs-lookup"><span data-stu-id="f2c42-203">Maps to a data contract with no data members.</span></span>|  
  
### <a name="xssequence-in-a-complex-type-attributes"></a><span data-ttu-id="f2c42-204">\<xs: sequence > em um tipo complexo: atributos</span><span class="sxs-lookup"><span data-stu-id="f2c42-204">\<xs:sequence> in a complex type: attributes</span></span>  
  
|<span data-ttu-id="f2c42-205">Atributo</span><span class="sxs-lookup"><span data-stu-id="f2c42-205">Attribute</span></span>|<span data-ttu-id="f2c42-206">Esquema</span><span class="sxs-lookup"><span data-stu-id="f2c42-206">Schema</span></span>|  
|---------------|------------|  
|`id`|<span data-ttu-id="f2c42-207">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="f2c42-207">Ignored.</span></span>|  
|`maxOccurs`|<span data-ttu-id="f2c42-208">Deve ser 1 (padrão).</span><span class="sxs-lookup"><span data-stu-id="f2c42-208">Must be 1 (default).</span></span>|  
|`minOccurs`|<span data-ttu-id="f2c42-209">Deve ser 1 (padrão).</span><span class="sxs-lookup"><span data-stu-id="f2c42-209">Must be 1 (default).</span></span>|  
  
### <a name="xssequence-in-a-complex-type-contents"></a><span data-ttu-id="f2c42-210">\<xs: sequence > em um tipo complexo: conteúdo</span><span class="sxs-lookup"><span data-stu-id="f2c42-210">\<xs:sequence> in a complex type: contents</span></span>  
  
|<span data-ttu-id="f2c42-211">Conteúdo</span><span class="sxs-lookup"><span data-stu-id="f2c42-211">Contents</span></span>|<span data-ttu-id="f2c42-212">Esquema</span><span class="sxs-lookup"><span data-stu-id="f2c42-212">Schema</span></span>|  
|--------------|------------|  
|`element`|<span data-ttu-id="f2c42-213">Cada instância é mapeado para um membro de dados.</span><span class="sxs-lookup"><span data-stu-id="f2c42-213">Each instance maps to a data member.</span></span>|  
|`group`|<span data-ttu-id="f2c42-214">Negado.</span><span class="sxs-lookup"><span data-stu-id="f2c42-214">Forbidden.</span></span>|  
|`choice`|<span data-ttu-id="f2c42-215">Negado.</span><span class="sxs-lookup"><span data-stu-id="f2c42-215">Forbidden.</span></span>|  
|`sequence`|<span data-ttu-id="f2c42-216">Negado.</span><span class="sxs-lookup"><span data-stu-id="f2c42-216">Forbidden.</span></span>|  
|`any`|<span data-ttu-id="f2c42-217">Negado.</span><span class="sxs-lookup"><span data-stu-id="f2c42-217">Forbidden.</span></span>|  
|<span data-ttu-id="f2c42-218">(vazio)</span><span class="sxs-lookup"><span data-stu-id="f2c42-218">(empty)</span></span>|<span data-ttu-id="f2c42-219">Mapeia para um contrato de dados com nenhum membro de dados.</span><span class="sxs-lookup"><span data-stu-id="f2c42-219">Maps to a data contract with no data members.</span></span>|  
  
## <a name="elements--xselement"></a><span data-ttu-id="f2c42-220">Elementos – \<xs: element ></span><span class="sxs-lookup"><span data-stu-id="f2c42-220">Elements – \<xs:element></span></span>  
  
### <a name="general-information"></a><span data-ttu-id="f2c42-221">Informações gerais</span><span class="sxs-lookup"><span data-stu-id="f2c42-221">General Information</span></span>  
 <span data-ttu-id="f2c42-222">`<xs:element>` pode ocorrer nos seguintes contextos:</span><span class="sxs-lookup"><span data-stu-id="f2c42-222">`<xs:element>` can occur in the following contexts:</span></span>  
  
-   <span data-ttu-id="f2c42-223">Pode ocorrer dentro de um `<xs:sequence>`, que descreve um membro de dados de um contrato de dados (não coleta) regular.</span><span class="sxs-lookup"><span data-stu-id="f2c42-223">It can occur within an `<xs:sequence>`, which describes a data member of a regular (non-collection) data contract.</span></span> <span data-ttu-id="f2c42-224">Nesse caso, o `maxOccurs` atributo deve ser 1.</span><span class="sxs-lookup"><span data-stu-id="f2c42-224">In this case, the `maxOccurs` attribute must be 1.</span></span> <span data-ttu-id="f2c42-225">(Um valor de 0 não é permitido).</span><span class="sxs-lookup"><span data-stu-id="f2c42-225">(A value of 0 is not allowed).</span></span>  
  
-   <span data-ttu-id="f2c42-226">Pode ocorrer dentro de um `<xs:sequence>`, que descreve um membro de dados de um contrato de dados da coleção.</span><span class="sxs-lookup"><span data-stu-id="f2c42-226">It can occur within an `<xs:sequence>`, which describes a data member of a collection data contract.</span></span> <span data-ttu-id="f2c42-227">Nesse caso, o `maxOccurs` atributo deve ser maior que 1 ou "unbounded".</span><span class="sxs-lookup"><span data-stu-id="f2c42-227">In this case, the `maxOccurs` attribute must be greater than 1 or "unbounded".</span></span>  
  
-   <span data-ttu-id="f2c42-228">Pode ocorrer dentro de um `<xs:schema>` como uma declaração de elemento Global (Buições).</span><span class="sxs-lookup"><span data-stu-id="f2c42-228">It can occur within an `<xs:schema>` as a Global Element Declaration (GED).</span></span>  
  
### <a name="xselement-with-maxoccurs1-within-an-xssequence-data-members"></a><span data-ttu-id="f2c42-229">\<xs: element > com maxOccurs = 1 dentro de um \<xs: sequence > (membros de dados)</span><span class="sxs-lookup"><span data-stu-id="f2c42-229">\<xs:element> with maxOccurs=1 within an \<xs:sequence> (Data Members)</span></span>  
  
|<span data-ttu-id="f2c42-230">Atributo</span><span class="sxs-lookup"><span data-stu-id="f2c42-230">Attribute</span></span>|<span data-ttu-id="f2c42-231">Esquema</span><span class="sxs-lookup"><span data-stu-id="f2c42-231">Schema</span></span>|  
|---------------|------------|  
|`ref`|<span data-ttu-id="f2c42-232">Negado.</span><span class="sxs-lookup"><span data-stu-id="f2c42-232">Forbidden.</span></span>|  
|`name`|<span data-ttu-id="f2c42-233">Suporte, é mapeado para o nome do membro de dados.</span><span class="sxs-lookup"><span data-stu-id="f2c42-233">Supported, maps to the data member name.</span></span>|  
|`type`|<span data-ttu-id="f2c42-234">Mapeia para o membro de dados com suporte, digite.</span><span class="sxs-lookup"><span data-stu-id="f2c42-234">Supported, maps to the data member type.</span></span> <span data-ttu-id="f2c42-235">Para obter mais informações, consulte o mapeamento de tipo/primitivo.</span><span class="sxs-lookup"><span data-stu-id="f2c42-235">For more information, see Type/primitive mapping.</span></span> <span data-ttu-id="f2c42-236">Se não especificado (e o elemento não contém um tipo anônimo), `xs:anyType` será assumido.</span><span class="sxs-lookup"><span data-stu-id="f2c42-236">If not specified (and the element does not contain an anonymous type), `xs:anyType` is assumed.</span></span>|  
|`block`|<span data-ttu-id="f2c42-237">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="f2c42-237">Ignored.</span></span>|  
|`default`|<span data-ttu-id="f2c42-238">Negado.</span><span class="sxs-lookup"><span data-stu-id="f2c42-238">Forbidden.</span></span>|  
|`fixed`|<span data-ttu-id="f2c42-239">Negado.</span><span class="sxs-lookup"><span data-stu-id="f2c42-239">Forbidden.</span></span>|  
|`form`|<span data-ttu-id="f2c42-240">Deve ser qualificado.</span><span class="sxs-lookup"><span data-stu-id="f2c42-240">Must be qualified.</span></span> <span data-ttu-id="f2c42-241">Esse atributo pode ser definido por meio de `elementFormDefault` em `xs:schema`.</span><span class="sxs-lookup"><span data-stu-id="f2c42-241">This attribute can be set through `elementFormDefault` on `xs:schema`.</span></span>|  
|`id`|<span data-ttu-id="f2c42-242">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="f2c42-242">Ignored.</span></span>|  
|`maxOccurs`|<span data-ttu-id="f2c42-243">1</span><span class="sxs-lookup"><span data-stu-id="f2c42-243">1</span></span>|  
|`minOccurs`|<span data-ttu-id="f2c42-244">Mapeia para o <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> propriedade de um membro de dados (`IsRequired` é verdadeiro quando `minOccurs` é 1).</span><span class="sxs-lookup"><span data-stu-id="f2c42-244">Maps to the <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> property of a data member (`IsRequired` is true when `minOccurs` is 1).</span></span>|  
|`nillable`|<span data-ttu-id="f2c42-245">Mapeamento de tipo afeta.</span><span class="sxs-lookup"><span data-stu-id="f2c42-245">Affects type mapping.</span></span> <span data-ttu-id="f2c42-246">Consulte o mapeamento de tipo/primitivo.</span><span class="sxs-lookup"><span data-stu-id="f2c42-246">See Type/primitive mapping.</span></span>|  
  
### <a name="xselement-with-maxoccurs1-within-an-xssequence-collections"></a><span data-ttu-id="f2c42-247">\<xs: element > com maxOccurs > 1 dentro de um \<xs: sequence > (coleções)</span><span class="sxs-lookup"><span data-stu-id="f2c42-247">\<xs:element> with maxOccurs>1 within an \<xs:sequence> (Collections)</span></span>  
  
-   <span data-ttu-id="f2c42-248">Mapeia para um <xref:System.Runtime.Serialization.CollectionDataContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="f2c42-248">Maps to a <xref:System.Runtime.Serialization.CollectionDataContractAttribute>.</span></span>  
  
-   <span data-ttu-id="f2c42-249">Em tipos de coleção, xs: element somente uma é permitida dentro de um xs: sequence.</span><span class="sxs-lookup"><span data-stu-id="f2c42-249">In collection types, only one xs:element is allowed within an xs:sequence.</span></span>  
  
 <span data-ttu-id="f2c42-250">Coleções podem ser dos seguintes tipos:</span><span class="sxs-lookup"><span data-stu-id="f2c42-250">Collections can be of the following types:</span></span>  
  
-   <span data-ttu-id="f2c42-251">Coleções regulares (por exemplo, matrizes).</span><span class="sxs-lookup"><span data-stu-id="f2c42-251">Regular collections (for example, arrays).</span></span>  
  
-   <span data-ttu-id="f2c42-252">Coleções de dicionário (um valor de mapeamento; por exemplo, um <xref:System.Collections.Hashtable>).</span><span class="sxs-lookup"><span data-stu-id="f2c42-252">Dictionary collections (mapping one value to another; for example, a <xref:System.Collections.Hashtable>).</span></span>  
  
-   <span data-ttu-id="f2c42-253">É a única diferença entre um dicionário e uma matriz de um tipo de par chave/valor no modelo de programação gerado.</span><span class="sxs-lookup"><span data-stu-id="f2c42-253">The only difference between a dictionary and an array of a key/value pair type is in the generated programming model.</span></span> <span data-ttu-id="f2c42-254">Há um mecanismo de anotação de esquema que pode ser usado para indicar que um determinado tipo é uma coleção de dicionário.</span><span class="sxs-lookup"><span data-stu-id="f2c42-254">There is a schema annotation mechanism that can be used to indicate that a given type is a dictionary collection.</span></span>  
  
 <span data-ttu-id="f2c42-255">As regras para o `ref`, `block`, `default`, `fixed`, `form`, e `id` atributos são as mesmas para o caso de não coleção.</span><span class="sxs-lookup"><span data-stu-id="f2c42-255">The rules for the `ref`, `block`, `default`, `fixed`, `form`, and `id` attributes are the same as for the non-collection case.</span></span> <span data-ttu-id="f2c42-256">Outros atributos incluem aqueles na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="f2c42-256">Other attributes include those in the following table.</span></span>  
  
|<span data-ttu-id="f2c42-257">Atributo</span><span class="sxs-lookup"><span data-stu-id="f2c42-257">Attribute</span></span>|<span data-ttu-id="f2c42-258">Esquema</span><span class="sxs-lookup"><span data-stu-id="f2c42-258">Schema</span></span>|  
|---------------|------------|  
|`name`|<span data-ttu-id="f2c42-259">Com suporte, é mapeado para o <xref:System.Runtime.Serialization.CollectionDataContractAttribute.ItemName%2A> propriedade o `CollectionDataContractAttribute` atributo.</span><span class="sxs-lookup"><span data-stu-id="f2c42-259">Supported, maps to the <xref:System.Runtime.Serialization.CollectionDataContractAttribute.ItemName%2A> property in the `CollectionDataContractAttribute` attribute.</span></span>|  
|`type`|<span data-ttu-id="f2c42-260">Suporte, mapeia para o tipo armazenado na coleção.</span><span class="sxs-lookup"><span data-stu-id="f2c42-260">Supported, maps to the type stored in the collection.</span></span>|  
|`maxOccurs`|<span data-ttu-id="f2c42-261">Maior que 1 ou "unbounded".</span><span class="sxs-lookup"><span data-stu-id="f2c42-261">Greater than 1 or "unbounded".</span></span> <span data-ttu-id="f2c42-262">O esquema do controlador de domínio deve usar "unbounded".</span><span class="sxs-lookup"><span data-stu-id="f2c42-262">The DC schema should use "unbounded".</span></span>|  
|`minOccurs`|<span data-ttu-id="f2c42-263">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="f2c42-263">Ignored.</span></span>|  
|`nillable`|<span data-ttu-id="f2c42-264">Mapeamento de tipo afeta.</span><span class="sxs-lookup"><span data-stu-id="f2c42-264">Affects type mapping.</span></span> <span data-ttu-id="f2c42-265">Esse atributo é ignorado para coleções de dicionário.</span><span class="sxs-lookup"><span data-stu-id="f2c42-265">This attribute is ignored for dictionary collections.</span></span>|  
  
### <a name="xselement-within-an-xsschema-global-element-declaration"></a><span data-ttu-id="f2c42-266">\<xs: element > dentro de um \<xs: schema > declaração de elemento Global</span><span class="sxs-lookup"><span data-stu-id="f2c42-266">\<xs:element> within an \<xs:schema> Global Element Declaration</span></span>  
  
-   <span data-ttu-id="f2c42-267">Um Global elemento declaração (Buições) que tem o mesmo nome e namespace como um tipo no esquema, ou que define um tipo anônimo dentro do próprio, deve ser associado ao tipo.</span><span class="sxs-lookup"><span data-stu-id="f2c42-267">A Global Element Declaration (GED) that has the same name and namespace as a type in schema, or that defines an anonymous type inside itself, is said to be associated with the type.</span></span>  
  
-   <span data-ttu-id="f2c42-268">Exportação de esquema: GEDs associados são gerados para cada tipo gerado, simple e complexo.</span><span class="sxs-lookup"><span data-stu-id="f2c42-268">Schema export: associated GEDs are generated for every generated type, both simple and complex.</span></span>  
  
-   <span data-ttu-id="f2c42-269">Serialização/desserialização: GEDs associados são usados como elementos raiz para o tipo.</span><span class="sxs-lookup"><span data-stu-id="f2c42-269">Deserialization/serialization: associated GEDs are used as root elements for the type.</span></span>  
  
-   <span data-ttu-id="f2c42-270">Importação de esquema: GEDs associados não são necessários e são ignorados se elas seguirão as regras a seguir (a menos que definem tipos).</span><span class="sxs-lookup"><span data-stu-id="f2c42-270">Schema import: associated GEDs are not required and are ignored if they follow the following rules (unless they define types).</span></span>  
  
|<span data-ttu-id="f2c42-271">Atributo</span><span class="sxs-lookup"><span data-stu-id="f2c42-271">Attribute</span></span>|<span data-ttu-id="f2c42-272">Esquema</span><span class="sxs-lookup"><span data-stu-id="f2c42-272">Schema</span></span>|  
|---------------|------------|  
|`abstract`|<span data-ttu-id="f2c42-273">Deve ser falsa para GEDs associados.</span><span class="sxs-lookup"><span data-stu-id="f2c42-273">Must be false for associated GEDs.</span></span>|  
|`block`|<span data-ttu-id="f2c42-274">Proibido no GEDs associados.</span><span class="sxs-lookup"><span data-stu-id="f2c42-274">Forbidden in associated GEDs.</span></span>|  
|`default`|<span data-ttu-id="f2c42-275">Proibido no GEDs associados.</span><span class="sxs-lookup"><span data-stu-id="f2c42-275">Forbidden in associated GEDs.</span></span>|  
|`final`|<span data-ttu-id="f2c42-276">Deve ser falsa para GEDs associados.</span><span class="sxs-lookup"><span data-stu-id="f2c42-276">Must be false for associated GEDs.</span></span>|  
|`fixed`|<span data-ttu-id="f2c42-277">Proibido no GEDs associados.</span><span class="sxs-lookup"><span data-stu-id="f2c42-277">Forbidden in associated GEDs.</span></span>|  
|`id`|<span data-ttu-id="f2c42-278">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="f2c42-278">Ignored.</span></span>|  
|`name`|<span data-ttu-id="f2c42-279">Com suporte.</span><span class="sxs-lookup"><span data-stu-id="f2c42-279">Supported.</span></span> <span data-ttu-id="f2c42-280">Consulte a definição de GEDs associados.</span><span class="sxs-lookup"><span data-stu-id="f2c42-280">See the definition of associated GEDs.</span></span>|  
|`nillable`|<span data-ttu-id="f2c42-281">Deve ser verdadeiro para GEDs associados.</span><span class="sxs-lookup"><span data-stu-id="f2c42-281">Must be true for associated GEDs.</span></span>|  
|`substitutionGroup`|<span data-ttu-id="f2c42-282">Proibido no GEDs associados.</span><span class="sxs-lookup"><span data-stu-id="f2c42-282">Forbidden in associated GEDs.</span></span>|  
|`type`|<span data-ttu-id="f2c42-283">Suporte e devem corresponder o tipo associado para GEDs associados (a menos que o elemento contém um tipo anônimo).</span><span class="sxs-lookup"><span data-stu-id="f2c42-283">Supported, and must match the associated type for associated GEDs (unless the element contains an anonymous type).</span></span>|  
  
### <a name="xselement-contents"></a><span data-ttu-id="f2c42-284">\<xs: element >: conteúdo</span><span class="sxs-lookup"><span data-stu-id="f2c42-284">\<xs:element>: contents</span></span>  
  
|<span data-ttu-id="f2c42-285">Conteúdo</span><span class="sxs-lookup"><span data-stu-id="f2c42-285">Contents</span></span>|<span data-ttu-id="f2c42-286">Esquema</span><span class="sxs-lookup"><span data-stu-id="f2c42-286">Schema</span></span>|  
|--------------|------------|  
|`simpleType`|<span data-ttu-id="f2c42-287">Supported.\*</span><span class="sxs-lookup"><span data-stu-id="f2c42-287">Supported.\*</span></span>|  
|`complexType`|<span data-ttu-id="f2c42-288">Supported.\*</span><span class="sxs-lookup"><span data-stu-id="f2c42-288">Supported.\*</span></span>|  
|`unique`|<span data-ttu-id="f2c42-289">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="f2c42-289">Ignored.</span></span>|  
|`key`|<span data-ttu-id="f2c42-290">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="f2c42-290">Ignored.</span></span>|  
|`keyref`|<span data-ttu-id="f2c42-291">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="f2c42-291">Ignored.</span></span>|  
|<span data-ttu-id="f2c42-292">(blank)</span><span class="sxs-lookup"><span data-stu-id="f2c42-292">(blank)</span></span>|<span data-ttu-id="f2c42-293">Com suporte.</span><span class="sxs-lookup"><span data-stu-id="f2c42-293">Supported.</span></span>|  
  
 <span data-ttu-id="f2c42-294">\* Ao usar o `simpleType` e `complexType,` mapeamento para tipos anônimos é o mesmo para tipos não anônimo, exceto que não há nenhum contrato de dados anônimos e, portanto, um contrato de dados nomeado é criado, com um nome gerado derivado do nome do elemento.</span><span class="sxs-lookup"><span data-stu-id="f2c42-294">\* When using the `simpleType` and `complexType,` mapping for anonymous types is the same as for non-anonymous types, except that there is no anonymous data contracts, and so a named data contract is created, with a generated name derived from the element name.</span></span> <span data-ttu-id="f2c42-295">As regras para tipos anônimos estão na lista a seguir:</span><span class="sxs-lookup"><span data-stu-id="f2c42-295">The rules for anonymous types are in the following list:</span></span>  
  
-   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="f2c42-296"> detalhes de implementação: se o `xs:element` nome não contém pontos, o tipo anônimo é mapeado para um tipo interno do tipo de contrato de dados externa.</span><span class="sxs-lookup"><span data-stu-id="f2c42-296"> implementation detail: If the `xs:element` name does not contain periods, the anonymous type maps to an inner type of the outer data contract type.</span></span> <span data-ttu-id="f2c42-297">Se o nome contiver períodos, o tipo de contrato de dados resultante é independente (não um tipo interno).</span><span class="sxs-lookup"><span data-stu-id="f2c42-297">If the name contains periods, the resulting data contract type is independent (not an inner type).</span></span>  
  
-   <span data-ttu-id="f2c42-298">O nome do contrato de dados gerados de tipo interno é o nome do contrato de dados do tipo externo seguido por um período, o nome do elemento e a cadeia de caracteres "Type".</span><span class="sxs-lookup"><span data-stu-id="f2c42-298">The generated data contract name of the inner type is the data contract name of the outer type followed by a period, the name of the element, and the string "Type".</span></span>  
  
-   <span data-ttu-id="f2c42-299">Se um dado contrato com esse nome já existir, o nome é feito exclusivo, acrescentando "1", "2", "3", e assim por diante, até que um nome exclusivo é criado.</span><span class="sxs-lookup"><span data-stu-id="f2c42-299">If a data contract with such a name already exists, the name is made unique by appending "1", "2", "3", and so on until a unique name is created.</span></span>  
  
## <a name="simple-types---xssimpletype"></a><span data-ttu-id="f2c42-300">Simple Types - \<xs:simpleType></span><span class="sxs-lookup"><span data-stu-id="f2c42-300">Simple Types - \<xs:simpleType></span></span>  
  
### <a name="xssimpletype-attributes"></a><span data-ttu-id="f2c42-301">\<xs:simpleType >: atributos</span><span class="sxs-lookup"><span data-stu-id="f2c42-301">\<xs:simpleType>: attributes</span></span>  
  
|<span data-ttu-id="f2c42-302">Atributo</span><span class="sxs-lookup"><span data-stu-id="f2c42-302">Attribute</span></span>|<span data-ttu-id="f2c42-303">Esquema</span><span class="sxs-lookup"><span data-stu-id="f2c42-303">Schema</span></span>|  
|---------------|------------|  
|`final`|<span data-ttu-id="f2c42-304">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="f2c42-304">Ignored.</span></span>|  
|`id`|<span data-ttu-id="f2c42-305">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="f2c42-305">Ignored.</span></span>|  
|`name`|<span data-ttu-id="f2c42-306">Com suporte, mapeia para os dados de nome do contrato.</span><span class="sxs-lookup"><span data-stu-id="f2c42-306">Supported, maps to the data contract name.</span></span>|  
  
### <a name="xssimpletype-contents"></a><span data-ttu-id="f2c42-307">\<xs:simpleType>: contents</span><span class="sxs-lookup"><span data-stu-id="f2c42-307">\<xs:simpleType>: contents</span></span>  
  
|<span data-ttu-id="f2c42-308">Conteúdo</span><span class="sxs-lookup"><span data-stu-id="f2c42-308">Contents</span></span>|<span data-ttu-id="f2c42-309">Esquema</span><span class="sxs-lookup"><span data-stu-id="f2c42-309">Schema</span></span>|  
|--------------|------------|  
|`restriction`|<span data-ttu-id="f2c42-310">Com suporte.</span><span class="sxs-lookup"><span data-stu-id="f2c42-310">Supported.</span></span> <span data-ttu-id="f2c42-311">Mapeia para contratos de dados de enumeração.</span><span class="sxs-lookup"><span data-stu-id="f2c42-311">Maps to enumeration data contracts.</span></span> <span data-ttu-id="f2c42-312">Esse atributo é ignorado se ele não corresponder ao padrão de enumeração.</span><span class="sxs-lookup"><span data-stu-id="f2c42-312">This attribute is ignored if it does not match the enumeration pattern.</span></span> <span data-ttu-id="f2c42-313">Consulte o `xs:simpleType` seção de restrições.</span><span class="sxs-lookup"><span data-stu-id="f2c42-313">See the `xs:simpleType` restrictions section.</span></span>|  
|`list`|<span data-ttu-id="f2c42-314">Com suporte.</span><span class="sxs-lookup"><span data-stu-id="f2c42-314">Supported.</span></span> <span data-ttu-id="f2c42-315">Mapeia para contratos de dados de enumeração do sinalizador.</span><span class="sxs-lookup"><span data-stu-id="f2c42-315">Maps to flag enumeration data contracts.</span></span> <span data-ttu-id="f2c42-316">Consulte o `xs:simpleType` listas de seção.</span><span class="sxs-lookup"><span data-stu-id="f2c42-316">See the `xs:simpleType` lists section.</span></span>|  
|`union`|<span data-ttu-id="f2c42-317">Negado.</span><span class="sxs-lookup"><span data-stu-id="f2c42-317">Forbidden.</span></span>|  
  
### <a name="xsrestriction"></a><span data-ttu-id="f2c42-318">\<xs:restriction></span><span class="sxs-lookup"><span data-stu-id="f2c42-318">\<xs:restriction></span></span>  
  
-   <span data-ttu-id="f2c42-319">Restrições de tipo complexo têm suporte apenas para base = "`xs:anyType`".</span><span class="sxs-lookup"><span data-stu-id="f2c42-319">Complex type restrictions are supported only for base="`xs:anyType`".</span></span>  
  
-   <span data-ttu-id="f2c42-320">Restrições de tipo simples de `xs:string` que não têm qualquer facetas de restrição que `xs:enumeration` são mapeados para os contratos de dados de enumeração.</span><span class="sxs-lookup"><span data-stu-id="f2c42-320">Simple type restrictions of `xs:string` that do not have any restriction facets other than `xs:enumeration` are mapped to enumeration data contracts.</span></span>  
  
-   <span data-ttu-id="f2c42-321">Todas as outras restrições de tipo simples são mapeadas para os tipos que eles restringem o.</span><span class="sxs-lookup"><span data-stu-id="f2c42-321">All other simple type restrictions are mapped to the types they restrict.</span></span> <span data-ttu-id="f2c42-322">Por exemplo, uma restrição de `xs:int` é mapeado para um número inteiro, assim como `xs:int` does por si mesmo.</span><span class="sxs-lookup"><span data-stu-id="f2c42-322">For example, a restriction of `xs:int` maps to an integer, just as `xs:int` itself does.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="f2c42-323"> tipo primitivo mapeamento, consulte o mapeamento de tipo/primitivo.</span><span class="sxs-lookup"><span data-stu-id="f2c42-323"> primitive type mapping, see Type/primitive mapping.</span></span>  
  
### <a name="xsrestriction-attributes"></a><span data-ttu-id="f2c42-324">\<xs: Restriction >: atributos</span><span class="sxs-lookup"><span data-stu-id="f2c42-324">\<xs:restriction>: attributes</span></span>  
  
|<span data-ttu-id="f2c42-325">Atributo</span><span class="sxs-lookup"><span data-stu-id="f2c42-325">Attribute</span></span>|<span data-ttu-id="f2c42-326">Esquema</span><span class="sxs-lookup"><span data-stu-id="f2c42-326">Schema</span></span>|  
|---------------|------------|  
|`base`|<span data-ttu-id="f2c42-327">Deve ser um tipo simple com suporte ou `xs:anyType`.</span><span class="sxs-lookup"><span data-stu-id="f2c42-327">Must be a supported simple type or `xs:anyType`.</span></span>|  
|`id`|<span data-ttu-id="f2c42-328">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="f2c42-328">Ignored.</span></span>|  
  
### <a name="xsrestriction-for-all-other-cases-contents"></a><span data-ttu-id="f2c42-329">\<xs: Restriction > para todos os outros casos: conteúdo</span><span class="sxs-lookup"><span data-stu-id="f2c42-329">\<xs:restriction> for all other cases: contents</span></span>  
  
|<span data-ttu-id="f2c42-330">Conteúdo</span><span class="sxs-lookup"><span data-stu-id="f2c42-330">Contents</span></span>|<span data-ttu-id="f2c42-331">Esquema</span><span class="sxs-lookup"><span data-stu-id="f2c42-331">Schema</span></span>|  
|--------------|------------|  
|`simpleType`|<span data-ttu-id="f2c42-332">Se estiver presente, deve ser derivado de um tipo primitivo com suporte.</span><span class="sxs-lookup"><span data-stu-id="f2c42-332">If present, must be derived from a supported primitive type.</span></span>|  
|`minExclusive`|<span data-ttu-id="f2c42-333">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="f2c42-333">Ignored.</span></span>|  
|`minInclusive`|<span data-ttu-id="f2c42-334">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="f2c42-334">Ignored.</span></span>|  
|`maxExclusive`|<span data-ttu-id="f2c42-335">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="f2c42-335">Ignored.</span></span>|  
|`maxInclusive`|<span data-ttu-id="f2c42-336">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="f2c42-336">Ignored.</span></span>|  
|`totalDigits`|<span data-ttu-id="f2c42-337">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="f2c42-337">Ignored.</span></span>|  
|`fractionDigits`|<span data-ttu-id="f2c42-338">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="f2c42-338">Ignored.</span></span>|  
|`length`|<span data-ttu-id="f2c42-339">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="f2c42-339">Ignored.</span></span>|  
|`minLength`|<span data-ttu-id="f2c42-340">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="f2c42-340">Ignored.</span></span>|  
|`maxLength`|<span data-ttu-id="f2c42-341">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="f2c42-341">Ignored.</span></span>|  
|`enumeration`|<span data-ttu-id="f2c42-342">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="f2c42-342">Ignored.</span></span>|  
|`whiteSpace`|<span data-ttu-id="f2c42-343">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="f2c42-343">Ignored.</span></span>|  
|`pattern`|<span data-ttu-id="f2c42-344">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="f2c42-344">Ignored.</span></span>|  
|<span data-ttu-id="f2c42-345">(blank)</span><span class="sxs-lookup"><span data-stu-id="f2c42-345">(blank)</span></span>|<span data-ttu-id="f2c42-346">Com suporte.</span><span class="sxs-lookup"><span data-stu-id="f2c42-346">Supported.</span></span>|  
  
## <a name="enumeration"></a><span data-ttu-id="f2c42-347">Enumeração</span><span class="sxs-lookup"><span data-stu-id="f2c42-347">Enumeration</span></span>  
  
### <a name="xsrestriction-for-enumerations-attributes"></a><span data-ttu-id="f2c42-348">\<xs: Restriction > para enumerações: atributos</span><span class="sxs-lookup"><span data-stu-id="f2c42-348">\<xs:restriction> for enumerations: attributes</span></span>  
  
|<span data-ttu-id="f2c42-349">Atributo</span><span class="sxs-lookup"><span data-stu-id="f2c42-349">Attribute</span></span>|<span data-ttu-id="f2c42-350">Esquema</span><span class="sxs-lookup"><span data-stu-id="f2c42-350">Schema</span></span>|  
|---------------|------------|  
|`base`|<span data-ttu-id="f2c42-351">Se estiver presente, deve ser `xs:string`.</span><span class="sxs-lookup"><span data-stu-id="f2c42-351">If present, must be `xs:string`.</span></span>|  
|`id`|<span data-ttu-id="f2c42-352">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="f2c42-352">Ignored.</span></span>|  
  
### <a name="xsrestriction-for-enumerations-contents"></a><span data-ttu-id="f2c42-353">\<xs: Restriction > para enumerações: conteúdo</span><span class="sxs-lookup"><span data-stu-id="f2c42-353">\<xs:restriction> for enumerations: contents</span></span>  
  
|<span data-ttu-id="f2c42-354">Conteúdo</span><span class="sxs-lookup"><span data-stu-id="f2c42-354">Contents</span></span>|<span data-ttu-id="f2c42-355">Esquema</span><span class="sxs-lookup"><span data-stu-id="f2c42-355">Schema</span></span>|  
|--------------|------------|  
|`simpleType`|<span data-ttu-id="f2c42-356">Se estiver presente, deve ser uma restrição de enumeração suportada pelo contrato de dados (Esta seção).</span><span class="sxs-lookup"><span data-stu-id="f2c42-356">If present, must be an enumeration restriction supported by the data contract (this section).</span></span>|  
|`minExclusive`|<span data-ttu-id="f2c42-357">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="f2c42-357">Ignored.</span></span>|  
|`minInclusive`|<span data-ttu-id="f2c42-358">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="f2c42-358">Ignored.</span></span>|  
|`maxExclusive`|<span data-ttu-id="f2c42-359">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="f2c42-359">Ignored.</span></span>|  
|`maxInclusive`|<span data-ttu-id="f2c42-360">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="f2c42-360">Ignored.</span></span>|  
|`totalDigits`|<span data-ttu-id="f2c42-361">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="f2c42-361">Ignored.</span></span>|  
|`fractionDigits`|<span data-ttu-id="f2c42-362">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="f2c42-362">Ignored.</span></span>|  
|`length`|<span data-ttu-id="f2c42-363">Negado.</span><span class="sxs-lookup"><span data-stu-id="f2c42-363">Forbidden.</span></span>|  
|`minLength`|<span data-ttu-id="f2c42-364">Negado.</span><span class="sxs-lookup"><span data-stu-id="f2c42-364">Forbidden.</span></span>|  
|`maxLength`|<span data-ttu-id="f2c42-365">Negado.</span><span class="sxs-lookup"><span data-stu-id="f2c42-365">Forbidden.</span></span>|  
|`enumeration`|<span data-ttu-id="f2c42-366">Com suporte.</span><span class="sxs-lookup"><span data-stu-id="f2c42-366">Supported.</span></span> <span data-ttu-id="f2c42-367">Enumeração "id" será ignorada e "valor" é mapeado para o nome do valor no contrato de dados de enumeração.</span><span class="sxs-lookup"><span data-stu-id="f2c42-367">Enumeration "id" is ignored, and "value" maps to the value name in the enumeration data contract.</span></span>|  
|`whiteSpace`|<span data-ttu-id="f2c42-368">Negado.</span><span class="sxs-lookup"><span data-stu-id="f2c42-368">Forbidden.</span></span>|  
|`pattern`|<span data-ttu-id="f2c42-369">Negado.</span><span class="sxs-lookup"><span data-stu-id="f2c42-369">Forbidden.</span></span>|  
|<span data-ttu-id="f2c42-370">(vazio)</span><span class="sxs-lookup"><span data-stu-id="f2c42-370">(empty)</span></span>|<span data-ttu-id="f2c42-371">Suporte, mapeia para o tipo de enumeração vazia.</span><span class="sxs-lookup"><span data-stu-id="f2c42-371">Supported, maps to empty enumeration type.</span></span>|  
  
 <span data-ttu-id="f2c42-372">O código a seguir mostra uma classe de enumeração do c#.</span><span class="sxs-lookup"><span data-stu-id="f2c42-372">The following code shows a C# enumeration class.</span></span>  
  
```  
public enum MyEnum  
{  
   first = 3,  
   second = 4,  
   third =5  
```  
  
 <span data-ttu-id="f2c42-373">}</span><span class="sxs-lookup"><span data-stu-id="f2c42-373">}</span></span>  
  
 <span data-ttu-id="f2c42-374">Essa classe é mapeado para o esquema a seguir, o `DataContractSerializer`.</span><span class="sxs-lookup"><span data-stu-id="f2c42-374">This class maps to the following schema by the `DataContractSerializer`.</span></span> <span data-ttu-id="f2c42-375">Se os valores de enumeração iniciarem 1 `xs:annotation` blocos não são gerados.</span><span class="sxs-lookup"><span data-stu-id="f2c42-375">If enumeration values start from 1, `xs:annotation` blocks are not generated.</span></span>  
  
```xml  
<xs:simpleType name="MyEnum">  
<xs:restriction base="xs:string">  
 <xs:enumeration value="first">  
  <xs:annotation>  
   <xs:appinfo>  
    <EnumerationValue   
     xmlns="http://schemas.microsoft.com/2003/10/Serialization/">  
     3  
    </EnumerationValue>  
   </xs:appinfo>  
  </xs:annotation>  
 </xs:enumeration>  
 <xs:enumeration value="second">  
  <xs:annotation>  
   <xs:appinfo>  
    <EnumerationValue   
     xmlns="http://schemas.microsoft.com/2003/10/Serialization/">  
     4  
    </EnumerationValue>  
   </xs:appinfo>  
  </xs:annotation>  
 </xs:enumeration>  
</xs:restriction>  
</xs:simpleType>  
```  
  
### <a name="xslist"></a><span data-ttu-id="f2c42-376">\<xs:list></span><span class="sxs-lookup"><span data-stu-id="f2c42-376">\<xs:list></span></span>  
 <span data-ttu-id="f2c42-377">`DataContractSerializer` tipos de enumeração de mapas marcado com `System.FlagsAttribute` para `xs:list` derivado de `xs:string`.</span><span class="sxs-lookup"><span data-stu-id="f2c42-377">`DataContractSerializer` maps enumeration types marked with `System.FlagsAttribute` to `xs:list` derived from `xs:string`.</span></span> <span data-ttu-id="f2c42-378">Nenhum outro `xs:list` variações têm suporte.</span><span class="sxs-lookup"><span data-stu-id="f2c42-378">No other `xs:list` variations are supported.</span></span>  
  
### <a name="xslist-attributes"></a><span data-ttu-id="f2c42-379">\<Xs >: atributos</span><span class="sxs-lookup"><span data-stu-id="f2c42-379">\<xs:list>: attributes</span></span>  
  
|<span data-ttu-id="f2c42-380">Atributo</span><span class="sxs-lookup"><span data-stu-id="f2c42-380">Attribute</span></span>|<span data-ttu-id="f2c42-381">Esquema</span><span class="sxs-lookup"><span data-stu-id="f2c42-381">Schema</span></span>|  
|---------------|------------|  
|`itemType`|<span data-ttu-id="f2c42-382">Negado.</span><span class="sxs-lookup"><span data-stu-id="f2c42-382">Forbidden.</span></span>|  
|`id`|<span data-ttu-id="f2c42-383">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="f2c42-383">Ignored.</span></span>|  
  
### <a name="xslist-contents"></a><span data-ttu-id="f2c42-384">\<Xs >: conteúdo</span><span class="sxs-lookup"><span data-stu-id="f2c42-384">\<xs:list>: contents</span></span>  
  
|<span data-ttu-id="f2c42-385">Conteúdo</span><span class="sxs-lookup"><span data-stu-id="f2c42-385">Contents</span></span>|<span data-ttu-id="f2c42-386">Esquema</span><span class="sxs-lookup"><span data-stu-id="f2c42-386">Schema</span></span>|  
|--------------|------------|  
|`simpleType`|<span data-ttu-id="f2c42-387">Deve ser a restrição de `xs:string` usando `xs:enumeration` faceta.</span><span class="sxs-lookup"><span data-stu-id="f2c42-387">Must be restriction from `xs:string` using `xs:enumeration` facet.</span></span>|  
  
 <span data-ttu-id="f2c42-388">Se o valor de enumeração não segue uma potência de 2 progressão (padrão para sinalizadores), o valor é armazenado no `xs:annotation/xs:appInfo/ser:EnumerationValue` elemento.</span><span class="sxs-lookup"><span data-stu-id="f2c42-388">If enumeration value does not follow a power of 2 progression (default for Flags), the value is stored in the `xs:annotation/xs:appInfo/ser:EnumerationValue` element.</span></span>  
  
 <span data-ttu-id="f2c42-389">Por exemplo, o código a seguir indica um tipo de enumeração.</span><span class="sxs-lookup"><span data-stu-id="f2c42-389">For example, the following code flags an enumeration type.</span></span>  
  
```  
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
  
 <span data-ttu-id="f2c42-390">Esse tipo é mapeado para o esquema a seguir.</span><span class="sxs-lookup"><span data-stu-id="f2c42-390">This type maps to the following schema.</span></span>  
  
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
                <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Se  
rialization/">16</EnumerationValue>  
              </xs:appinfo>  
            </xs:annotation>  
          </xs:enumeration>  
          <xs:enumeration value="AuthWindowsLiveID">  
            <xs:annotation>  
              <xs:appinfo>  
                <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Se  
rialization/">64</EnumerationValue>  
              </xs:appinfo>  
            </xs:annotation>  
          </xs:enumeration>  
        </xs:restriction>  
      </xs:simpleType>  
    </xs:list>  
  </xs:simpleType>  
```  
  
## <a name="inheritance"></a><span data-ttu-id="f2c42-391">Herança</span><span class="sxs-lookup"><span data-stu-id="f2c42-391">Inheritance</span></span>  
  
### <a name="general-rules"></a><span data-ttu-id="f2c42-392">Regras gerais</span><span class="sxs-lookup"><span data-stu-id="f2c42-392">General rules</span></span>  
 <span data-ttu-id="f2c42-393">Um contrato de dados pode herdar de outro contrato de dados.</span><span class="sxs-lookup"><span data-stu-id="f2c42-393">A data contract can inherit from another data contract.</span></span> <span data-ttu-id="f2c42-394">Esses contratos de dados mapear para uma base e são derivados por tipos de extensão usando o `<xs:extension>` construção de esquema XML.</span><span class="sxs-lookup"><span data-stu-id="f2c42-394">Such data contracts map to a base and are derived by extension types using the `<xs:extension>` XML Schema construct.</span></span>  
  
 <span data-ttu-id="f2c42-395">Um contrato de dados não pode herdar de um contrato de dados da coleção.</span><span class="sxs-lookup"><span data-stu-id="f2c42-395">A data contract cannot inherit from a collection data contract.</span></span>  
  
 <span data-ttu-id="f2c42-396">Por exemplo, o código a seguir é um contrato de dados.</span><span class="sxs-lookup"><span data-stu-id="f2c42-396">For example, the following code is a data contract.</span></span>  
  
```  
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
  
 <span data-ttu-id="f2c42-397">Este contrato de dados é mapeado para a declaração de tipo de esquema XML a seguir.</span><span class="sxs-lookup"><span data-stu-id="f2c42-397">This data contract maps to the following XML Schema type declaration.</span></span>  
  
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
  
### <a name="xscomplexcontent-attributes"></a><span data-ttu-id="f2c42-398">\<xs:complexContent >: atributos</span><span class="sxs-lookup"><span data-stu-id="f2c42-398">\<xs:complexContent>: attributes</span></span>  
  
|<span data-ttu-id="f2c42-399">Atributo</span><span class="sxs-lookup"><span data-stu-id="f2c42-399">Attribute</span></span>|<span data-ttu-id="f2c42-400">Esquema</span><span class="sxs-lookup"><span data-stu-id="f2c42-400">Schema</span></span>|  
|---------------|------------|  
|`id`|<span data-ttu-id="f2c42-401">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="f2c42-401">Ignored.</span></span>|  
|`mixed`|<span data-ttu-id="f2c42-402">Deve ser false.</span><span class="sxs-lookup"><span data-stu-id="f2c42-402">Must be false.</span></span>|  
  
### <a name="xscomplexcontent-contents"></a><span data-ttu-id="f2c42-403">\<xs:complexContent >: conteúdo</span><span class="sxs-lookup"><span data-stu-id="f2c42-403">\<xs:complexContent>: contents</span></span>  
  
|<span data-ttu-id="f2c42-404">Conteúdo</span><span class="sxs-lookup"><span data-stu-id="f2c42-404">Contents</span></span>|<span data-ttu-id="f2c42-405">Esquema</span><span class="sxs-lookup"><span data-stu-id="f2c42-405">Schema</span></span>|  
|--------------|------------|  
|`restriction`|<span data-ttu-id="f2c42-406">Proibido, exceto quando base = "`xs:anyType`".</span><span class="sxs-lookup"><span data-stu-id="f2c42-406">Forbidden, except when base="`xs:anyType`".</span></span> <span data-ttu-id="f2c42-407">O segundo é equivalente a colocar o conteúdo do `xs:restriction` diretamente sob o contêiner do `xs:complexContent`.</span><span class="sxs-lookup"><span data-stu-id="f2c42-407">The latter is equivalent to placing the content of the `xs:restriction` directly under the container of the `xs:complexContent`.</span></span>|  
|`extension`|<span data-ttu-id="f2c42-408">Com suporte.</span><span class="sxs-lookup"><span data-stu-id="f2c42-408">Supported.</span></span> <span data-ttu-id="f2c42-409">Mapeia a herança de contrato de dados.</span><span class="sxs-lookup"><span data-stu-id="f2c42-409">Maps to data contract inheritance.</span></span>|  
  
### <a name="xsextension-in-xscomplexcontent-attributes"></a><span data-ttu-id="f2c42-410">\<xs: Extension > em \<xs:complexContent >: atributos</span><span class="sxs-lookup"><span data-stu-id="f2c42-410">\<xs:extension> in \<xs:complexContent>: attributes</span></span>  
  
|<span data-ttu-id="f2c42-411">Atributo</span><span class="sxs-lookup"><span data-stu-id="f2c42-411">Attribute</span></span>|<span data-ttu-id="f2c42-412">Esquema</span><span class="sxs-lookup"><span data-stu-id="f2c42-412">Schema</span></span>|  
|---------------|------------|  
|`id`|<span data-ttu-id="f2c42-413">Ignorado.</span><span class="sxs-lookup"><span data-stu-id="f2c42-413">Ignored.</span></span>|  
|`base`|<span data-ttu-id="f2c42-414">Com suporte.</span><span class="sxs-lookup"><span data-stu-id="f2c42-414">Supported.</span></span> <span data-ttu-id="f2c42-415">Mapeia para o contrato de dados base de tipo que esse tipo herda do.</span><span class="sxs-lookup"><span data-stu-id="f2c42-415">Maps to the base data contract type that this type inherits from.</span></span>|  
  
### <a name="xsextension-in-xscomplexcontent-contents"></a><span data-ttu-id="f2c42-416">\<xs: Extension > em \<xs:complexContent >: conteúdo</span><span class="sxs-lookup"><span data-stu-id="f2c42-416">\<xs:extension> in \<xs:complexContent>: contents</span></span>  
 <span data-ttu-id="f2c42-417">As regras são os mesmos para `<xs:complexType>` conteúdo.</span><span class="sxs-lookup"><span data-stu-id="f2c42-417">The rules are the same as for `<xs:complexType>` contents.</span></span>  
  
 <span data-ttu-id="f2c42-418">Se um `<xs:sequence>` for fornecido, o membro de elementos são mapeados para os membros de dados adicionais que estão presentes no contrato de dados derivado.</span><span class="sxs-lookup"><span data-stu-id="f2c42-418">If an `<xs:sequence>` is provided, its member elements map to additional data members that are present in the derived data contract.</span></span>  
  
 <span data-ttu-id="f2c42-419">Se um tipo derivado contém um elemento com o mesmo nome que um elemento em um tipo base, a declaração de elemento duplicado mapeado para um membro de dados com um nome que é gerado para serem exclusivos.</span><span class="sxs-lookup"><span data-stu-id="f2c42-419">If a derived type contains an element with the same name as an element in a base type, the duplicate element declaration maps to a data member with a name that is generated to be unique.</span></span> <span data-ttu-id="f2c42-420">Números inteiros positivos são adicionados para o nome do membro de dados ("membro1", "membro2" e assim por diante) até encontra um nome exclusivo.</span><span class="sxs-lookup"><span data-stu-id="f2c42-420">Positive integer numbers are added to the data member name ("member1", "member2", and so on) until a unique name is found.</span></span> <span data-ttu-id="f2c42-421">Por outro lado:</span><span class="sxs-lookup"><span data-stu-id="f2c42-421">Conversely:</span></span>  
  
-   <span data-ttu-id="f2c42-422">Se um contrato de dados derivado tem um membro com o mesmo nome e tipo de dados como um membro de dados em um contrato de dados base, `DataContractSerializer` gera este elemento correspondente no tipo derivado.</span><span class="sxs-lookup"><span data-stu-id="f2c42-422">If a derived data contract has a data member with the same name and type as a data member in a base data contract, `DataContractSerializer` generates this corresponding element in the derived type.</span></span>  
  
-   <span data-ttu-id="f2c42-423">Se um contrato de dados derivado tem um membro de dados com o mesmo nome como um membro de dados em um contrato de dados base, mas um tipo diferente, o `DataContractSerializer` importa um esquema com um elemento do tipo `xs:anyType` no tipo base e declarações de tipo derivado.</span><span class="sxs-lookup"><span data-stu-id="f2c42-423">If a derived data contract has a data member with the same name as a data member in a base data contract but a different type, the `DataContractSerializer` imports a schema with an element of the type `xs:anyType` in both base type and derived type declarations.</span></span> <span data-ttu-id="f2c42-424">O nome do tipo original é preservado na `xs:annotations/xs:appInfo/ser:ActualType/@Name`.</span><span class="sxs-lookup"><span data-stu-id="f2c42-424">The original type name is preserved in `xs:annotations/xs:appInfo/ser:ActualType/@Name`.</span></span>  
  
 <span data-ttu-id="f2c42-425">Ambas as variações podem levar a um esquema com um modelo de conteúdo ambíguo, depende da ordem de membros do respectivos dados.</span><span class="sxs-lookup"><span data-stu-id="f2c42-425">Both variations may lead to a schema with an ambiguous content model, which depends on the order of the respective data members.</span></span>  
  
## <a name="typeprimitive-mapping"></a><span data-ttu-id="f2c42-426">Mapeamento de tipo/primitivo</span><span class="sxs-lookup"><span data-stu-id="f2c42-426">Type/primitive mapping</span></span>  
 <span data-ttu-id="f2c42-427">O `DataContractSerializer` usa o seguinte mapeamento para tipos primitivos do esquema XML.</span><span class="sxs-lookup"><span data-stu-id="f2c42-427">The `DataContractSerializer` uses the following mapping for XML Schema primitive types.</span></span>  
  
|<span data-ttu-id="f2c42-428">Tipo XSD</span><span class="sxs-lookup"><span data-stu-id="f2c42-428">XSD type</span></span>|<span data-ttu-id="f2c42-429">Tipo .NET</span><span class="sxs-lookup"><span data-stu-id="f2c42-429">.NET type</span></span>|  
|--------------|---------------|  
|`anyType`|<span data-ttu-id="f2c42-430"><xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="f2c42-430"><xref:System.Object>.</span></span>|  
|`anySimpleType`|<span data-ttu-id="f2c42-431"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="f2c42-431"><xref:System.String>.</span></span>|  
|`duration`|<span data-ttu-id="f2c42-432"><xref:System.TimeSpan>.</span><span class="sxs-lookup"><span data-stu-id="f2c42-432"><xref:System.TimeSpan>.</span></span>|  
|`dateTime`|<span data-ttu-id="f2c42-433"><xref:System.DateTime>.</span><span class="sxs-lookup"><span data-stu-id="f2c42-433"><xref:System.DateTime>.</span></span>|  
|`dateTimeOffset`|<span data-ttu-id="f2c42-434"><xref:System.DateTime> e <xref:System.TimeSpan> para o deslocamento.</span><span class="sxs-lookup"><span data-stu-id="f2c42-434"><xref:System.DateTime> and <xref:System.TimeSpan> for the offset.</span></span> <span data-ttu-id="f2c42-435">Consulte abaixo de serialização de DateTimeOffset.</span><span class="sxs-lookup"><span data-stu-id="f2c42-435">See DateTimeOffset Serialization below.</span></span>|  
|`time`|<span data-ttu-id="f2c42-436"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="f2c42-436"><xref:System.String>.</span></span>|  
|`date`|<span data-ttu-id="f2c42-437"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="f2c42-437"><xref:System.String>.</span></span>|  
|`gYearMonth`|<span data-ttu-id="f2c42-438"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="f2c42-438"><xref:System.String>.</span></span>|  
|`gYear`|<span data-ttu-id="f2c42-439"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="f2c42-439"><xref:System.String>.</span></span>|  
|`gMonthDay`|<span data-ttu-id="f2c42-440"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="f2c42-440"><xref:System.String>.</span></span>|  
|`gDay`|<span data-ttu-id="f2c42-441"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="f2c42-441"><xref:System.String>.</span></span>|  
|`gMonth`|<span data-ttu-id="f2c42-442"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="f2c42-442"><xref:System.String>.</span></span>|  
|`boolean`|<xref:System.Boolean>|  
|`base64Binary`|<span data-ttu-id="f2c42-443">Matriz <xref:System.Byte>.</span><span class="sxs-lookup"><span data-stu-id="f2c42-443"><xref:System.Byte> array.</span></span>|  
|`hexBinary`|<span data-ttu-id="f2c42-444"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="f2c42-444"><xref:System.String>.</span></span>|  
|`float`|<span data-ttu-id="f2c42-445"><xref:System.Single>.</span><span class="sxs-lookup"><span data-stu-id="f2c42-445"><xref:System.Single>.</span></span>|  
|`double`|<span data-ttu-id="f2c42-446"><xref:System.Double>.</span><span class="sxs-lookup"><span data-stu-id="f2c42-446"><xref:System.Double>.</span></span>|  
|`anyURI`|<span data-ttu-id="f2c42-447"><xref:System.Uri>.</span><span class="sxs-lookup"><span data-stu-id="f2c42-447"><xref:System.Uri>.</span></span>|  
|`QName`|<span data-ttu-id="f2c42-448"><xref:System.Xml.XmlQualifiedName>.</span><span class="sxs-lookup"><span data-stu-id="f2c42-448"><xref:System.Xml.XmlQualifiedName>.</span></span>|  
|`string`|<span data-ttu-id="f2c42-449"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="f2c42-449"><xref:System.String>.</span></span>|  
|`normalizedString`|<span data-ttu-id="f2c42-450"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="f2c42-450"><xref:System.String>.</span></span>|  
|`token`|<span data-ttu-id="f2c42-451"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="f2c42-451"><xref:System.String>.</span></span>|  
|`language`|<span data-ttu-id="f2c42-452"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="f2c42-452"><xref:System.String>.</span></span>|  
|`Name`|<span data-ttu-id="f2c42-453"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="f2c42-453"><xref:System.String>.</span></span>|  
|`NCName`|<span data-ttu-id="f2c42-454"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="f2c42-454"><xref:System.String>.</span></span>|  
|`ID`|<span data-ttu-id="f2c42-455"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="f2c42-455"><xref:System.String>.</span></span>|  
|`IDREF`|<span data-ttu-id="f2c42-456"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="f2c42-456"><xref:System.String>.</span></span>|  
|`IDREFS`|<span data-ttu-id="f2c42-457"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="f2c42-457"><xref:System.String>.</span></span>|  
|`ENTITY`|<span data-ttu-id="f2c42-458"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="f2c42-458"><xref:System.String>.</span></span>|  
|`ENTITIES`|<span data-ttu-id="f2c42-459"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="f2c42-459"><xref:System.String>.</span></span>|  
|`NMTOKEN`|<span data-ttu-id="f2c42-460"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="f2c42-460"><xref:System.String>.</span></span>|  
|`NMTOKENS`|<span data-ttu-id="f2c42-461"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="f2c42-461"><xref:System.String>.</span></span>|  
|`decimal`|<span data-ttu-id="f2c42-462"><xref:System.Decimal>.</span><span class="sxs-lookup"><span data-stu-id="f2c42-462"><xref:System.Decimal>.</span></span>|  
|`integer`|<span data-ttu-id="f2c42-463"><xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="f2c42-463"><xref:System.Int64>.</span></span>|  
|`nonPositiveInteger`|<span data-ttu-id="f2c42-464"><xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="f2c42-464"><xref:System.Int64>.</span></span>|  
|`negativeInteger`|<span data-ttu-id="f2c42-465"><xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="f2c42-465"><xref:System.Int64>.</span></span>|  
|`long`|<span data-ttu-id="f2c42-466"><xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="f2c42-466"><xref:System.Int64>.</span></span>|  
|`int`|<span data-ttu-id="f2c42-467"><xref:System.Int32>.</span><span class="sxs-lookup"><span data-stu-id="f2c42-467"><xref:System.Int32>.</span></span>|  
|`short`|<span data-ttu-id="f2c42-468"><xref:System.Int16>.</span><span class="sxs-lookup"><span data-stu-id="f2c42-468"><xref:System.Int16>.</span></span>|  
|`Byte`|<span data-ttu-id="f2c42-469"><xref:System.SByte>.</span><span class="sxs-lookup"><span data-stu-id="f2c42-469"><xref:System.SByte>.</span></span>|  
|`nonNegativeInteger`|<span data-ttu-id="f2c42-470"><xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="f2c42-470"><xref:System.Int64>.</span></span>|  
|`unsignedLong`|<span data-ttu-id="f2c42-471"><xref:System.UInt64>.</span><span class="sxs-lookup"><span data-stu-id="f2c42-471"><xref:System.UInt64>.</span></span>|  
|`unsignedInt`|<span data-ttu-id="f2c42-472"><xref:System.UInt32>.</span><span class="sxs-lookup"><span data-stu-id="f2c42-472"><xref:System.UInt32>.</span></span>|  
|`unsignedShort`|<span data-ttu-id="f2c42-473"><xref:System.UInt16>.</span><span class="sxs-lookup"><span data-stu-id="f2c42-473"><xref:System.UInt16>.</span></span>|  
|`unsignedByte`|<span data-ttu-id="f2c42-474"><xref:System.Byte>.</span><span class="sxs-lookup"><span data-stu-id="f2c42-474"><xref:System.Byte>.</span></span>|  
|`positiveInteger`|<span data-ttu-id="f2c42-475"><xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="f2c42-475"><xref:System.Int64>.</span></span>|  
  
## <a name="iserializable-types-mapping"></a><span data-ttu-id="f2c42-476">Mapeamento de tipos iSerializable</span><span class="sxs-lookup"><span data-stu-id="f2c42-476">ISerializable types mapping</span></span>  
 <span data-ttu-id="f2c42-477">Em [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] versão 1.0, `ISerializable` foi introduzida como um mecanismo geral para serializar objetos para transferência de dados ou de persistência.</span><span class="sxs-lookup"><span data-stu-id="f2c42-477">In [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] version 1.0, `ISerializable` was introduced as a general mechanism to serialize objects for persistence or data transfer.</span></span> <span data-ttu-id="f2c42-478">Existem várias [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] tipos que implementam `ISerializable` e que podem ser transmitidos entre aplicativos.</span><span class="sxs-lookup"><span data-stu-id="f2c42-478">There are many [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] types that implement `ISerializable` and that can be passed between applications.</span></span> <span data-ttu-id="f2c42-479">`DataContractSerializer` Naturalmente, fornece suporte para `ISerializable` classes.</span><span class="sxs-lookup"><span data-stu-id="f2c42-479">`DataContractSerializer` naturally provides support for `ISerializable` classes.</span></span> <span data-ttu-id="f2c42-480">O `DataContractSerializer` mapeia `ISerializable` tipos de esquema de implementação que diferem somente por QName (nome qualificado) do tipo e efetivamente são coleções de propriedade.</span><span class="sxs-lookup"><span data-stu-id="f2c42-480">The `DataContractSerializer` maps `ISerializable` implementation schema types that differ only by the QName (qualified name) of the type and are effectively property collections.</span></span> <span data-ttu-id="f2c42-481">Por exemplo, o `DataContractSerializer` mapeia <xref:System.Exception> para o seguinte tipo XSD no http://schemas.datacontract.org/2004/07/System namespace.</span><span class="sxs-lookup"><span data-stu-id="f2c42-481">For example, the `DataContractSerializer` maps <xref:System.Exception> to the following XSD type in the http://schemas.datacontract.org/2004/07/System namespace.</span></span>  
  
```xml  
<xs:complexType name="Exception">  
 <xs:sequence>  
  <xs:any minOccurs="0" maxOccurs="unbounded"   
      namespace="##local" processContents="skip"/>  
 </xs:sequence>  
 <xs:attribute ref="ser:FactoryType"/>  
</xs:complexType>  
```  
  
 <span data-ttu-id="f2c42-482">O atributo opcional `ser:FactoryType` declarado na serialização de contrato de dados de esquema faz referência a uma classe de fábrica que pode desserializar o tipo.</span><span class="sxs-lookup"><span data-stu-id="f2c42-482">The optional attribute `ser:FactoryType` declared in the Data Contract Serialization schema references a factory class that can deserialize the type.</span></span> <span data-ttu-id="f2c42-483">A classe de fábrica deve ser parte da coleção de tipos conhecidos a `DataContractSerializer` instância que está sendo usado.</span><span class="sxs-lookup"><span data-stu-id="f2c42-483">The factory class must be part of the known types collection of the `DataContractSerializer` instance being used.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="f2c42-484"> tipos conhecidos, consulte [tipos conhecidos de contrato de dados](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="f2c42-484"> known types, see [Data Contract Known Types](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span>  
  
## <a name="datacontract-serialization-schema"></a><span data-ttu-id="f2c42-485">Esquema de serialização de DataContract</span><span class="sxs-lookup"><span data-stu-id="f2c42-485">DataContract Serialization Schema</span></span>  
 <span data-ttu-id="f2c42-486">Um número de esquemas exportados pelo `DataContractSerializer` usar tipos de elementos e atributos de um namespace de serialização de contrato de dados especial:</span><span class="sxs-lookup"><span data-stu-id="f2c42-486">A number of schemas exported by the `DataContractSerializer` use types, elements, and attributes from a special Data Contract Serialization namespace:</span></span>  
  
 http://schemas.microsoft.com/2003/10/Serialization  
  
 <span data-ttu-id="f2c42-487">A seguir está uma declaração de esquema de serialização de contrato de dados completa.</span><span class="sxs-lookup"><span data-stu-id="f2c42-487">The following is a complete Data Contract Serialization schema declaration.</span></span>  
  
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
  
 <span data-ttu-id="f2c42-488">O exemplo a seguir deve ser observados:</span><span class="sxs-lookup"><span data-stu-id="f2c42-488">The following should be noted:</span></span>  
  
-   <span data-ttu-id="f2c42-489">`ser:char` é introduzido para representar caracteres Unicode do tipo <xref:System.Char>.</span><span class="sxs-lookup"><span data-stu-id="f2c42-489">`ser:char` is introduced to represent Unicode characters of type <xref:System.Char>.</span></span>  
  
-   <span data-ttu-id="f2c42-490">O `valuespace` de `xs:duration` é reduzida a um conjunto ordenado para que ele pode ser mapeado para um <xref:System.TimeSpan>.</span><span class="sxs-lookup"><span data-stu-id="f2c42-490">The `valuespace` of `xs:duration` is reduced to an ordered set so that it can be mapped to a <xref:System.TimeSpan>.</span></span>  
  
-   <span data-ttu-id="f2c42-491">`FactoryType` é usado em esquemas exportadas de tipos que são derivados de <xref:System.Runtime.Serialization.ISerializable>.</span><span class="sxs-lookup"><span data-stu-id="f2c42-491">`FactoryType` is used in schemas exported from types that are derived from <xref:System.Runtime.Serialization.ISerializable>.</span></span>  
  
## <a name="importing-non-datacontract-schemas"></a><span data-ttu-id="f2c42-492">Importando esquemas não DataContract</span><span class="sxs-lookup"><span data-stu-id="f2c42-492">Importing non-DataContract schemas</span></span>  
 <span data-ttu-id="f2c42-493">`DataContractSerializer` tem o `ImportXmlTypes` opção para permitir que a importação de esquemas que não está de acordo com o `DataContractSerializer` perfil XSD (consulte o <xref:System.Runtime.Serialization.XsdDataContractImporter.Options%2A> propriedade).</span><span class="sxs-lookup"><span data-stu-id="f2c42-493">`DataContractSerializer` has the `ImportXmlTypes` option to allow import of schemas that do not conform to the `DataContractSerializer` XSD profile (see the <xref:System.Runtime.Serialization.XsdDataContractImporter.Options%2A> property).</span></span> <span data-ttu-id="f2c42-494">Definir essa opção como `true` habilita a aceitação dos tipos de esquema não conformes e mapeando-os para a implementação a seguir, <xref:System.Xml.Serialization.IXmlSerializable> quebra automática de uma matriz de <xref:System.Xml.XmlNode> (somente o nome da classe difere).</span><span class="sxs-lookup"><span data-stu-id="f2c42-494">Setting this option to `true` enables acceptance of non-conforming schema types and mapping them to the following implementation, <xref:System.Xml.Serialization.IXmlSerializable> wrapping an array of <xref:System.Xml.XmlNode> (only the class name differs).</span></span>  
  
```  
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
  
## <a name="datetimeoffset-serialization"></a><span data-ttu-id="f2c42-495">Serialização de DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="f2c42-495">DateTimeOffset Serialization</span></span>  
 <span data-ttu-id="f2c42-496">O <xref:System.DateTimeOffset> não é tratado como um tipo primitivo.</span><span class="sxs-lookup"><span data-stu-id="f2c42-496">The <xref:System.DateTimeOffset> is not treated as a primitive type.</span></span> <span data-ttu-id="f2c42-497">Em vez disso, ele é serializado como um elemento complexo com duas partes.</span><span class="sxs-lookup"><span data-stu-id="f2c42-497">Instead, it is serialized as a complex element with two parts.</span></span> <span data-ttu-id="f2c42-498">A primeira parte representa a data, hora e a segunda parte representa o deslocamento de data hora.</span><span class="sxs-lookup"><span data-stu-id="f2c42-498">The first part represents the date time, and the second part represents the offset from the date time.</span></span> <span data-ttu-id="f2c42-499">Um exemplo de um valor DateTimeOffset serializado é mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="f2c42-499">An example of a serialized DateTimeOffset value is shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="f2c42-500">O esquema é da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="f2c42-500">The schema is as follows.</span></span>  
  
```xml  
<xs:schema targetNamespace="http://schemas.datacontract.org/2004/07/System">  
   <xs:complexType name="DateTimeOffset">  
      <xs:sequence minOccurs="1" maxOccurs="1">  
         <xs:element name="DateTime" type="xs:dateTime"  
         minOccurs="1" maxOccurs="1" />  
         <xs:elementname="OffsetMinutes" type="xs:short"  
         minOccurs="1" maxOccurs="1" />  
      </xs:sequence>  
   </xs:complexType>  
</xs:schema>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f2c42-501">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f2c42-501">See Also</span></span>  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 <xref:System.Runtime.Serialization.DataContractAttribute>  
 <xref:System.Runtime.Serialization.DataMemberAttribute>  
 <xref:System.Runtime.Serialization.XsdDataContractImporter>  
 [<span data-ttu-id="f2c42-502">Usando contratos de dados</span><span class="sxs-lookup"><span data-stu-id="f2c42-502">Using Data Contracts</span></span>](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
