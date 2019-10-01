---
title: Elemento <oidEntry>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/oidMap/oidEntry
- http://schemas.microsoft.com/.NetConfiguration/v2.0#oidEntry
helpviewer_keywords:
- <oidEntry> element
- oidEntry element
ms.assetid: 22fb88b0-bf27-489c-9ca0-e65950ac136c
ms.openlocfilehash: eed2a4d06906d2928be62aed20a75484c3eea946
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699763"
---
# <a name="oidentry-element"></a><span data-ttu-id="e4746-102">\<oidEntry > elemento</span><span class="sxs-lookup"><span data-stu-id="e4746-102">\<oidEntry> Element</span></span>
<span data-ttu-id="e4746-103">Mapeia um OID (identificador de objeto) do ASN.1 para um nome amigável.</span><span class="sxs-lookup"><span data-stu-id="e4746-103">Maps an ASN.1 object identifier (OID) to a friendly name.</span></span>  
  
[<span data-ttu-id="e4746-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="e4746-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="e4746-105">&nbsp; @ no__t-1[ **\<mscorlib >** ](mscorlib-element-for-cryptography-settings.md)</span><span class="sxs-lookup"><span data-stu-id="e4746-105">&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)</span></span>  
<span data-ttu-id="e4746-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<cryptographySettings >** ](cryptographysettings-element.md)</span><span class="sxs-lookup"><span data-stu-id="e4746-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)</span></span>  
<span data-ttu-id="e4746-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5[ **\<oidMap >** ](oidmap-element.md)</span><span class="sxs-lookup"><span data-stu-id="e4746-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<oidMap>**](oidmap-element.md)</span></span>  
<span data-ttu-id="e4746-108">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 **\<oidEntry >**</span><span class="sxs-lookup"><span data-stu-id="e4746-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<oidEntry>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4746-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e4746-109">Syntax</span></span>  
  
```xml  
<oidEntry OID="object identifier number" name="friendly name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e4746-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="e4746-110">Attributes and Elements</span></span>  
 <span data-ttu-id="e4746-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="e4746-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e4746-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="e4746-112">Attributes</span></span>  
  
|<span data-ttu-id="e4746-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="e4746-113">Attribute</span></span>|<span data-ttu-id="e4746-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="e4746-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e4746-115">**OID**</span><span class="sxs-lookup"><span data-stu-id="e4746-115">**OID**</span></span>|<span data-ttu-id="e4746-116">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="e4746-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="e4746-117">Especifica a OID ASN. 1 correspondente ao algoritmo implementado pela sua classe.</span><span class="sxs-lookup"><span data-stu-id="e4746-117">Specifies the ASN.1 OID corresponding to the algorithm implemented by your class.</span></span>|  
|<span data-ttu-id="e4746-118">**name**</span><span class="sxs-lookup"><span data-stu-id="e4746-118">**name**</span></span>|<span data-ttu-id="e4746-119">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="e4746-119">Required attribute.</span></span><br /><br /> <span data-ttu-id="e4746-120">Especifica o valor do atributo **Name** na marca de [> \<nameEntry](nameentry-element.md) .</span><span class="sxs-lookup"><span data-stu-id="e4746-120">Specifies the value for the **name** attribute in the [\<nameEntry>](nameentry-element.md) tag.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e4746-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="e4746-121">Child Elements</span></span>  
 <span data-ttu-id="e4746-122">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="e4746-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e4746-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="e4746-123">Parent Elements</span></span>  
  
|<span data-ttu-id="e4746-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="e4746-124">Element</span></span>|<span data-ttu-id="e4746-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="e4746-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="e4746-126">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e4746-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="e4746-127">Contém configurações de criptografia.</span><span class="sxs-lookup"><span data-stu-id="e4746-127">Contains cryptography settings.</span></span>|  
|`mscorlib`|<span data-ttu-id="e4746-128">Contém o `cryptographySettings` elemento.</span><span class="sxs-lookup"><span data-stu-id="e4746-128">Contains the `cryptographySettings` element.</span></span>|  
|`oidMap`|<span data-ttu-id="e4746-129">Contém mapeamentos de OID (identificador de objeto) ASN para classes.</span><span class="sxs-lookup"><span data-stu-id="e4746-129">Contains ASN.1 object identifier (OID) mappings to classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e4746-130">Comentários</span><span class="sxs-lookup"><span data-stu-id="e4746-130">Remarks</span></span>  
 <span data-ttu-id="e4746-131">Os identificadores de objeto ASN. 1 identificam algoritmos em alguns formatos criptográficos.</span><span class="sxs-lookup"><span data-stu-id="e4746-131">ASN.1 object identifiers identify algorithms in some cryptographic formats.</span></span> <span data-ttu-id="e4746-132">Mapeie identificadores de objeto para nomes amigáveis para os algoritmos que você deseja identificar.</span><span class="sxs-lookup"><span data-stu-id="e4746-132">Map object identifiers to friendly names for the algorithms you want to identify.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e4746-133">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e4746-133">Example</span></span>  
 <span data-ttu-id="e4746-134">O exemplo a seguir mostra como usar o elemento **\<oidEntry >** para mapear um identificador de objeto para o algoritmo de hash RIPEMD-160 para uma implementação desse algoritmo de hash.</span><span class="sxs-lookup"><span data-stu-id="e4746-134">The following example shows how to use the **\<oidEntry>** element to map an object identifier for the RIPEMD-160 hash algorithm to an implementation of that hash algorithm.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e4746-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e4746-135">See also</span></span>

- [<span data-ttu-id="e4746-136">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="e4746-136">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="e4746-137">Esquema de configurações de criptografia</span><span class="sxs-lookup"><span data-stu-id="e4746-137">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="e4746-138">Serviços criptográficos</span><span class="sxs-lookup"><span data-stu-id="e4746-138">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="e4746-139">Configurando classes de criptografia</span><span class="sxs-lookup"><span data-stu-id="e4746-139">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
- [<span data-ttu-id="e4746-140">Mapeando identificadores de objeto para algoritmos de criptografia</span><span class="sxs-lookup"><span data-stu-id="e4746-140">Mapping Object Identifiers to Cryptography Algorithms</span></span>](../../map-object-identifiers-to-cryptography-algorithms.md)
