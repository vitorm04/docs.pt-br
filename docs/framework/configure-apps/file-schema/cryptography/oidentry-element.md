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
ms.openlocfilehash: 4564cf59e3b6cfbdcd9dca06cd0f966d524834de
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088542"
---
# <a name="oidentry-element"></a><span data-ttu-id="1e8a5-102">\<elemento de > oidEntry</span><span class="sxs-lookup"><span data-stu-id="1e8a5-102">\<oidEntry> Element</span></span>
<span data-ttu-id="1e8a5-103">Mapeia um OID (identificador de objeto) do ASN.1 para um nome amigável.</span><span class="sxs-lookup"><span data-stu-id="1e8a5-103">Maps an ASN.1 object identifier (OID) to a friendly name.</span></span>  

<span data-ttu-id="1e8a5-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="1e8a5-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="1e8a5-105">&nbsp;&nbsp;[ **\<mscorlib >** ](mscorlib-element-for-cryptography-settings.md)</span><span class="sxs-lookup"><span data-stu-id="1e8a5-105">&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)</span></span>\
<span data-ttu-id="1e8a5-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<cryptographySettings >** ](cryptographysettings-element.md)</span><span class="sxs-lookup"><span data-stu-id="1e8a5-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)</span></span>\
<span data-ttu-id="1e8a5-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<oidMap >** ](oidmap-element.md)</span><span class="sxs-lookup"><span data-stu-id="1e8a5-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<oidMap>**](oidmap-element.md)</span></span>\
<span data-ttu-id="1e8a5-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<oidEntry >**</span><span class="sxs-lookup"><span data-stu-id="1e8a5-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<oidEntry>**</span></span>

## <a name="syntax"></a><span data-ttu-id="1e8a5-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1e8a5-109">Syntax</span></span>  
  
```xml  
<oidEntry OID="object identifier number" name="friendly name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1e8a5-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="1e8a5-110">Attributes and Elements</span></span>  
 <span data-ttu-id="1e8a5-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="1e8a5-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1e8a5-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="1e8a5-112">Attributes</span></span>  
  
|<span data-ttu-id="1e8a5-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="1e8a5-113">Attribute</span></span>|<span data-ttu-id="1e8a5-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="1e8a5-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1e8a5-115">**OIDs**</span><span class="sxs-lookup"><span data-stu-id="1e8a5-115">**OID**</span></span>|<span data-ttu-id="1e8a5-116">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="1e8a5-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="1e8a5-117">Especifica a OID ASN. 1 correspondente ao algoritmo implementado pela sua classe.</span><span class="sxs-lookup"><span data-stu-id="1e8a5-117">Specifies the ASN.1 OID corresponding to the algorithm implemented by your class.</span></span>|  
|<span data-ttu-id="1e8a5-118">**name**</span><span class="sxs-lookup"><span data-stu-id="1e8a5-118">**name**</span></span>|<span data-ttu-id="1e8a5-119">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="1e8a5-119">Required attribute.</span></span><br /><br /> <span data-ttu-id="1e8a5-120">Especifica o valor do atributo **Name** na marca [\<nameEntry >](nameentry-element.md) .</span><span class="sxs-lookup"><span data-stu-id="1e8a5-120">Specifies the value for the **name** attribute in the [\<nameEntry>](nameentry-element.md) tag.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1e8a5-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="1e8a5-121">Child Elements</span></span>  
 <span data-ttu-id="1e8a5-122">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="1e8a5-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1e8a5-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="1e8a5-123">Parent Elements</span></span>  
  
|<span data-ttu-id="1e8a5-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="1e8a5-124">Element</span></span>|<span data-ttu-id="1e8a5-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="1e8a5-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="1e8a5-126">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1e8a5-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="1e8a5-127">Contém configurações de criptografia.</span><span class="sxs-lookup"><span data-stu-id="1e8a5-127">Contains cryptography settings.</span></span>|  
|`mscorlib`|<span data-ttu-id="1e8a5-128">Contém o elemento `cryptographySettings`.</span><span class="sxs-lookup"><span data-stu-id="1e8a5-128">Contains the `cryptographySettings` element.</span></span>|  
|`oidMap`|<span data-ttu-id="1e8a5-129">Contém mapeamentos de OID (identificador de objeto) ASN para classes.</span><span class="sxs-lookup"><span data-stu-id="1e8a5-129">Contains ASN.1 object identifier (OID) mappings to classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1e8a5-130">Comentários</span><span class="sxs-lookup"><span data-stu-id="1e8a5-130">Remarks</span></span>  
 <span data-ttu-id="1e8a5-131">Os identificadores de objeto ASN. 1 identificam algoritmos em alguns formatos criptográficos.</span><span class="sxs-lookup"><span data-stu-id="1e8a5-131">ASN.1 object identifiers identify algorithms in some cryptographic formats.</span></span> <span data-ttu-id="1e8a5-132">Mapeie identificadores de objeto para nomes amigáveis para os algoritmos que você deseja identificar.</span><span class="sxs-lookup"><span data-stu-id="1e8a5-132">Map object identifiers to friendly names for the algorithms you want to identify.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1e8a5-133">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1e8a5-133">Example</span></span>  
 <span data-ttu-id="1e8a5-134">O exemplo a seguir mostra como usar o elemento **\<oidEntry >** para mapear um identificador de objeto para o algoritmo de hash RIPEMD-160 para uma implementação desse algoritmo de hash.</span><span class="sxs-lookup"><span data-stu-id="1e8a5-134">The following example shows how to use the **\<oidEntry>** element to map an object identifier for the RIPEMD-160 hash algorithm to an implementation of that hash algorithm.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1e8a5-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1e8a5-135">See also</span></span>

- [<span data-ttu-id="1e8a5-136">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="1e8a5-136">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="1e8a5-137">Esquema de configurações de criptografia</span><span class="sxs-lookup"><span data-stu-id="1e8a5-137">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="1e8a5-138">Serviços criptográficos</span><span class="sxs-lookup"><span data-stu-id="1e8a5-138">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="1e8a5-139">Configurando classes de criptografia</span><span class="sxs-lookup"><span data-stu-id="1e8a5-139">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
- [<span data-ttu-id="1e8a5-140">Mapeando identificadores de objeto para algoritmos de criptografia</span><span class="sxs-lookup"><span data-stu-id="1e8a5-140">Mapping Object Identifiers to Cryptography Algorithms</span></span>](../../map-object-identifiers-to-cryptography-algorithms.md)
