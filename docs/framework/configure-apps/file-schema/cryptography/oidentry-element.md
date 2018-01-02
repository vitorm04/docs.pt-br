---
title: '&lt;oidEntry&gt; elemento'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/oidMap/oidEntry
- http://schemas.microsoft.com/.NetConfiguration/v2.0#oidEntry
helpviewer_keywords:
- <oidEntry> element
- oidEntry element
ms.assetid: 22fb88b0-bf27-489c-9ca0-e65950ac136c
caps.latest.revision: "11"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 2d6dfe38f8e632a31f7a20191678f1fff7fd88ee
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltoidentrygt-element"></a><span data-ttu-id="23e85-102">&lt;oidEntry&gt; elemento</span><span class="sxs-lookup"><span data-stu-id="23e85-102">&lt;oidEntry&gt; Element</span></span>
<span data-ttu-id="23e85-103">Mapeia um OID (identificador de objeto) do ASN.1 para um nome amigável.</span><span class="sxs-lookup"><span data-stu-id="23e85-103">Maps an ASN.1 object identifier (OID) to a friendly name.</span></span>  
  
 <span data-ttu-id="23e85-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="23e85-104">\<configuration></span></span>  
<span data-ttu-id="23e85-105">\<mscorlib ></span><span class="sxs-lookup"><span data-stu-id="23e85-105">\<mscorlib></span></span>  
<span data-ttu-id="23e85-106">\<cryptographySettings ></span><span class="sxs-lookup"><span data-stu-id="23e85-106">\<cryptographySettings></span></span>  
<span data-ttu-id="23e85-107">\<oidMap ></span><span class="sxs-lookup"><span data-stu-id="23e85-107">\<oidMap></span></span>  
<span data-ttu-id="23e85-108">\<oidEntry ></span><span class="sxs-lookup"><span data-stu-id="23e85-108">\<oidEntry></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23e85-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="23e85-109">Syntax</span></span>  
  
```xml  
<oidEntry OID="object identifier number" name="friendly name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="23e85-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="23e85-110">Attributes and Elements</span></span>  
 <span data-ttu-id="23e85-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="23e85-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="23e85-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="23e85-112">Attributes</span></span>  
  
|<span data-ttu-id="23e85-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="23e85-113">Attribute</span></span>|<span data-ttu-id="23e85-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="23e85-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="23e85-115">**OID**</span><span class="sxs-lookup"><span data-stu-id="23e85-115">**OID**</span></span>|<span data-ttu-id="23e85-116">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="23e85-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="23e85-117">Especifica o ASN. 1 OID correspondente para o algoritmo implementado por sua classe.</span><span class="sxs-lookup"><span data-stu-id="23e85-117">Specifies the ASN.1 OID corresponding to the algorithm implemented by your class.</span></span>|  
|<span data-ttu-id="23e85-118">**name**</span><span class="sxs-lookup"><span data-stu-id="23e85-118">**name**</span></span>|<span data-ttu-id="23e85-119">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="23e85-119">Required attribute.</span></span><br /><br /> <span data-ttu-id="23e85-120">Especifica o valor para o **nome** atributo o [ \<nameEntry >](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md) marca.</span><span class="sxs-lookup"><span data-stu-id="23e85-120">Specifies the value for the **name** attribute in the [\<nameEntry>](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md) tag.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="23e85-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="23e85-121">Child Elements</span></span>  
 <span data-ttu-id="23e85-122">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="23e85-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="23e85-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="23e85-123">Parent Elements</span></span>  
  
|<span data-ttu-id="23e85-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="23e85-124">Element</span></span>|<span data-ttu-id="23e85-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="23e85-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="23e85-126">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="23e85-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="23e85-127">Contém configurações de criptografia.</span><span class="sxs-lookup"><span data-stu-id="23e85-127">Contains cryptography settings.</span></span>|  
|`mscorlib`|<span data-ttu-id="23e85-128">Contém o `cryptographySettings` elemento.</span><span class="sxs-lookup"><span data-stu-id="23e85-128">Contains the `cryptographySettings` element.</span></span>|  
|`oidMap`|<span data-ttu-id="23e85-129">Contém mapeamentos OID (identificador) de objeto ASN. 1 para classes.</span><span class="sxs-lookup"><span data-stu-id="23e85-129">Contains ASN.1 object identifier (OID) mappings to classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="23e85-130">Comentários</span><span class="sxs-lookup"><span data-stu-id="23e85-130">Remarks</span></span>  
 <span data-ttu-id="23e85-131">Identificadores de objeto ASN. 1 identificam algoritmos em alguns formatos de criptografia.</span><span class="sxs-lookup"><span data-stu-id="23e85-131">ASN.1 object identifiers identify algorithms in some cryptographic formats.</span></span> <span data-ttu-id="23e85-132">Mapeie os identificadores de objeto para nomes amigáveis para os algoritmos que você deseja identificar.</span><span class="sxs-lookup"><span data-stu-id="23e85-132">Map object identifiers to friendly names for the algorithms you want to identify.</span></span>  
  
## <a name="example"></a><span data-ttu-id="23e85-133">Exemplo</span><span class="sxs-lookup"><span data-stu-id="23e85-133">Example</span></span>  
 <span data-ttu-id="23e85-134">O exemplo a seguir mostra como usar o  **\<oidEntry >** elemento para mapear um identificador de objeto para o algoritmo de hash de 160 RIPEMD para uma implementação do algoritmo de hash.</span><span class="sxs-lookup"><span data-stu-id="23e85-134">The following example shows how to use the **\<oidEntry>** element to map an object identifier for the RIPEMD-160 hash algorithm to an implementation of that hash algorithm.</span></span>  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass   MyCrypto="MyCryptoClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="RIPEMD-160" class="MyCrypto"/>  
         </cryptoNameMapping>  
         <oidMap>  
            <oidEntry OID="1.3.36.3.2.1"   name="MyCryptoClass"/>  
         </oidMap>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="23e85-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="23e85-135">See Also</span></span>  
 [<span data-ttu-id="23e85-136">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="23e85-136">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="23e85-137">Esquema de configurações de criptografia</span><span class="sxs-lookup"><span data-stu-id="23e85-137">Cryptography Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)  
 [<span data-ttu-id="23e85-138">Serviços criptográficos</span><span class="sxs-lookup"><span data-stu-id="23e85-138">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)  
 [<span data-ttu-id="23e85-139">Configurando classes de criptografia</span><span class="sxs-lookup"><span data-stu-id="23e85-139">Configuring Cryptography Classes</span></span>](../../../../../docs/framework/configure-apps/configure-cryptography-classes.md)  
 [<span data-ttu-id="23e85-140">Mapeando identificadores de objeto para algoritmos de criptografia</span><span class="sxs-lookup"><span data-stu-id="23e85-140">Mapping Object Identifiers to Cryptography Algorithms</span></span>](../../../../../docs/framework/configure-apps/map-object-identifiers-to-cryptography-algorithms.md)
