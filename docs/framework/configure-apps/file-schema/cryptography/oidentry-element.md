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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "74088542"
---
# <a name="oidentry-element"></a><span data-ttu-id="86013-102">Elemento \<oidEntry></span><span class="sxs-lookup"><span data-stu-id="86013-102">\<oidEntry> Element</span></span>
<span data-ttu-id="86013-103">Mapeia um OID (identificador de objeto) do ASN.1 para um nome amigável.</span><span class="sxs-lookup"><span data-stu-id="86013-103">Maps an ASN.1 object identifier (OID) to a friendly name.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<oidMap>**](oidmap-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<oidEntry>**

## <a name="syntax"></a><span data-ttu-id="86013-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="86013-104">Syntax</span></span>  
  
```xml  
<oidEntry OID="object identifier number" name="friendly name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="86013-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="86013-105">Attributes and Elements</span></span>  
 <span data-ttu-id="86013-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="86013-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="86013-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="86013-107">Attributes</span></span>  
  
|<span data-ttu-id="86013-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="86013-108">Attribute</span></span>|<span data-ttu-id="86013-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="86013-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="86013-110">**OIDs**</span><span class="sxs-lookup"><span data-stu-id="86013-110">**OID**</span></span>|<span data-ttu-id="86013-111">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="86013-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="86013-112">Especifica a OID ASN. 1 correspondente ao algoritmo implementado pela sua classe.</span><span class="sxs-lookup"><span data-stu-id="86013-112">Specifies the ASN.1 OID corresponding to the algorithm implemented by your class.</span></span>|  
|<span data-ttu-id="86013-113">**name**</span><span class="sxs-lookup"><span data-stu-id="86013-113">**name**</span></span>|<span data-ttu-id="86013-114">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="86013-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="86013-115">Especifica o valor para o atributo **Name** na [\<nameEntry>](nameentry-element.md) marca.</span><span class="sxs-lookup"><span data-stu-id="86013-115">Specifies the value for the **name** attribute in the [\<nameEntry>](nameentry-element.md) tag.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="86013-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="86013-116">Child Elements</span></span>  
 <span data-ttu-id="86013-117">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="86013-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="86013-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="86013-118">Parent Elements</span></span>  
  
|<span data-ttu-id="86013-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="86013-119">Element</span></span>|<span data-ttu-id="86013-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="86013-120">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="86013-121">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="86013-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="86013-122">Contém configurações de criptografia.</span><span class="sxs-lookup"><span data-stu-id="86013-122">Contains cryptography settings.</span></span>|  
|`mscorlib`|<span data-ttu-id="86013-123">Contém o `cryptographySettings` elemento.</span><span class="sxs-lookup"><span data-stu-id="86013-123">Contains the `cryptographySettings` element.</span></span>|  
|`oidMap`|<span data-ttu-id="86013-124">Contém mapeamentos de OID (identificador de objeto) ASN para classes.</span><span class="sxs-lookup"><span data-stu-id="86013-124">Contains ASN.1 object identifier (OID) mappings to classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="86013-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="86013-125">Remarks</span></span>  
 <span data-ttu-id="86013-126">Os identificadores de objeto ASN. 1 identificam algoritmos em alguns formatos criptográficos.</span><span class="sxs-lookup"><span data-stu-id="86013-126">ASN.1 object identifiers identify algorithms in some cryptographic formats.</span></span> <span data-ttu-id="86013-127">Mapeie identificadores de objeto para nomes amigáveis para os algoritmos que você deseja identificar.</span><span class="sxs-lookup"><span data-stu-id="86013-127">Map object identifiers to friendly names for the algorithms you want to identify.</span></span>  
  
## <a name="example"></a><span data-ttu-id="86013-128">Exemplo</span><span class="sxs-lookup"><span data-stu-id="86013-128">Example</span></span>  
 <span data-ttu-id="86013-129">O exemplo a seguir mostra como usar o **\<oidEntry>** elemento para mapear um identificador de objeto para o algoritmo de hash RIPEMD-160 para uma implementação desse algoritmo de hash.</span><span class="sxs-lookup"><span data-stu-id="86013-129">The following example shows how to use the **\<oidEntry>** element to map an object identifier for the RIPEMD-160 hash algorithm to an implementation of that hash algorithm.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="86013-130">Confira também</span><span class="sxs-lookup"><span data-stu-id="86013-130">See also</span></span>

- [<span data-ttu-id="86013-131">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="86013-131">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="86013-132">Esquema de configurações de criptografia</span><span class="sxs-lookup"><span data-stu-id="86013-132">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="86013-133">Serviços de Criptografia</span><span class="sxs-lookup"><span data-stu-id="86013-133">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="86013-134">Configurando classes de criptografia</span><span class="sxs-lookup"><span data-stu-id="86013-134">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
- [<span data-ttu-id="86013-135">Mapeando identificadores de objeto para algoritmos de criptografia</span><span class="sxs-lookup"><span data-stu-id="86013-135">Mapping Object Identifiers to Cryptography Algorithms</span></span>](../../map-object-identifiers-to-cryptography-algorithms.md)
