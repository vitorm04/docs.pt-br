---
title: '&lt;oidEntry&gt; elemento'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/oidMap/oidEntry
- http://schemas.microsoft.com/.NetConfiguration/v2.0#oidEntry
helpviewer_keywords:
- <oidEntry> element
- oidEntry element
ms.assetid: 22fb88b0-bf27-489c-9ca0-e65950ac136c
author: mcleblanc
ms.author: markl
ms.openlocfilehash: c5be6ef95693f274e5cb2002e5642d5e58a7661a
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47206158"
---
# <a name="ltoidentrygt-element"></a><span data-ttu-id="9e795-102">&lt;oidEntry&gt; elemento</span><span class="sxs-lookup"><span data-stu-id="9e795-102">&lt;oidEntry&gt; Element</span></span>
<span data-ttu-id="9e795-103">Mapeia um OID (identificador de objeto) do ASN.1 para um nome amigável.</span><span class="sxs-lookup"><span data-stu-id="9e795-103">Maps an ASN.1 object identifier (OID) to a friendly name.</span></span>  
  
 <span data-ttu-id="9e795-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="9e795-104">\<configuration></span></span>  
<span data-ttu-id="9e795-105">\<mscorlib ></span><span class="sxs-lookup"><span data-stu-id="9e795-105">\<mscorlib></span></span>  
<span data-ttu-id="9e795-106">\<cryptographySettings ></span><span class="sxs-lookup"><span data-stu-id="9e795-106">\<cryptographySettings></span></span>  
<span data-ttu-id="9e795-107">\<oidMap ></span><span class="sxs-lookup"><span data-stu-id="9e795-107">\<oidMap></span></span>  
<span data-ttu-id="9e795-108">\<oidEntry ></span><span class="sxs-lookup"><span data-stu-id="9e795-108">\<oidEntry></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e795-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9e795-109">Syntax</span></span>  
  
```xml  
<oidEntry OID="object identifier number" name="friendly name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9e795-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="9e795-110">Attributes and Elements</span></span>  
 <span data-ttu-id="9e795-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="9e795-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9e795-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="9e795-112">Attributes</span></span>  
  
|<span data-ttu-id="9e795-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="9e795-113">Attribute</span></span>|<span data-ttu-id="9e795-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="9e795-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9e795-115">**OID**</span><span class="sxs-lookup"><span data-stu-id="9e795-115">**OID**</span></span>|<span data-ttu-id="9e795-116">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="9e795-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="9e795-117">Especifica o OID do ASN.1 correspondente para o algoritmo implementado por sua classe.</span><span class="sxs-lookup"><span data-stu-id="9e795-117">Specifies the ASN.1 OID corresponding to the algorithm implemented by your class.</span></span>|  
|<span data-ttu-id="9e795-118">**name**</span><span class="sxs-lookup"><span data-stu-id="9e795-118">**name**</span></span>|<span data-ttu-id="9e795-119">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="9e795-119">Required attribute.</span></span><br /><br /> <span data-ttu-id="9e795-120">Especifica o valor para o **nome** atributo na [ \<nameEntry >](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md) marca.</span><span class="sxs-lookup"><span data-stu-id="9e795-120">Specifies the value for the **name** attribute in the [\<nameEntry>](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md) tag.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9e795-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="9e795-121">Child Elements</span></span>  
 <span data-ttu-id="9e795-122">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="9e795-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9e795-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="9e795-123">Parent Elements</span></span>  
  
|<span data-ttu-id="9e795-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="9e795-124">Element</span></span>|<span data-ttu-id="9e795-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="9e795-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="9e795-126">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9e795-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="9e795-127">Contém configurações de criptografia.</span><span class="sxs-lookup"><span data-stu-id="9e795-127">Contains cryptography settings.</span></span>|  
|`mscorlib`|<span data-ttu-id="9e795-128">Contém o `cryptographySettings` elemento.</span><span class="sxs-lookup"><span data-stu-id="9e795-128">Contains the `cryptographySettings` element.</span></span>|  
|`oidMap`|<span data-ttu-id="9e795-129">Contém mapeamentos OID (identificador) de objeto do ASN.1 para classes.</span><span class="sxs-lookup"><span data-stu-id="9e795-129">Contains ASN.1 object identifier (OID) mappings to classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9e795-130">Comentários</span><span class="sxs-lookup"><span data-stu-id="9e795-130">Remarks</span></span>  
 <span data-ttu-id="9e795-131">Identificadores de objeto do ASN.1 identificam algoritmos em alguns formatos de criptografia.</span><span class="sxs-lookup"><span data-stu-id="9e795-131">ASN.1 object identifiers identify algorithms in some cryptographic formats.</span></span> <span data-ttu-id="9e795-132">Mapeie os identificadores de objeto para nomes amigáveis para os algoritmos que você deseja identificar.</span><span class="sxs-lookup"><span data-stu-id="9e795-132">Map object identifiers to friendly names for the algorithms you want to identify.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9e795-133">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9e795-133">Example</span></span>  
 <span data-ttu-id="9e795-134">O exemplo a seguir mostra como usar o  **\<oidEntry >** elemento para mapear um identificador de objeto para o algoritmo de hash RIPEMD-160 para uma implementação do algoritmo hash.</span><span class="sxs-lookup"><span data-stu-id="9e795-134">The following example shows how to use the **\<oidEntry>** element to map an object identifier for the RIPEMD-160 hash algorithm to an implementation of that hash algorithm.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9e795-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9e795-135">See Also</span></span>  
 [<span data-ttu-id="9e795-136">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="9e795-136">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="9e795-137">Esquema de configurações de criptografia</span><span class="sxs-lookup"><span data-stu-id="9e795-137">Cryptography Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)  
 [<span data-ttu-id="9e795-138">Serviços criptográficos</span><span class="sxs-lookup"><span data-stu-id="9e795-138">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)  
 [<span data-ttu-id="9e795-139">Configurando classes de criptografia</span><span class="sxs-lookup"><span data-stu-id="9e795-139">Configuring Cryptography Classes</span></span>](../../../../../docs/framework/configure-apps/configure-cryptography-classes.md)  
 [<span data-ttu-id="9e795-140">Mapeando identificadores de objeto para algoritmos de criptografia</span><span class="sxs-lookup"><span data-stu-id="9e795-140">Mapping Object Identifiers to Cryptography Algorithms</span></span>](../../../../../docs/framework/configure-apps/map-object-identifiers-to-cryptography-algorithms.md)
