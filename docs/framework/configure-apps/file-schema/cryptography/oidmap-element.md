---
title: Elemento <oidMap>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#oidMap
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/oidMap
helpviewer_keywords:
- <oidMap> element
- oidMap element
ms.assetid: 7f0c2246-c070-4748-b96a-2f66a296c539
ms.openlocfilehash: 80564c5895e08884f78a4ec7c955ecdb11126e35
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61705162"
---
# <a name="oidmap-element"></a><span data-ttu-id="39e8c-102">\<oidMap > elemento</span><span class="sxs-lookup"><span data-stu-id="39e8c-102">\<oidMap> Element</span></span>
<span data-ttu-id="39e8c-103">Contém mapeamentos OID (identificador) de objeto do ASN.1 para classes.</span><span class="sxs-lookup"><span data-stu-id="39e8c-103">Contains ASN.1 object identifier (OID) mappings to classes.</span></span>  
  
 <span data-ttu-id="39e8c-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="39e8c-104">\<configuration></span></span>  
<span data-ttu-id="39e8c-105">\<mscorlib></span><span class="sxs-lookup"><span data-stu-id="39e8c-105">\<mscorlib></span></span>  
<span data-ttu-id="39e8c-106">\<cryptographySettings></span><span class="sxs-lookup"><span data-stu-id="39e8c-106">\<cryptographySettings></span></span>  
<span data-ttu-id="39e8c-107">\<oidMap></span><span class="sxs-lookup"><span data-stu-id="39e8c-107">\<oidMap></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39e8c-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="39e8c-108">Syntax</span></span>  
  
```xml  
<oidMap>   
</oidMap>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="39e8c-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="39e8c-109">Attributes and Elements</span></span>  
 <span data-ttu-id="39e8c-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="39e8c-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="39e8c-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="39e8c-111">Attributes</span></span>  
 <span data-ttu-id="39e8c-112">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="39e8c-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="39e8c-113">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="39e8c-113">Child Elements</span></span>  
  
|<span data-ttu-id="39e8c-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="39e8c-114">Element</span></span>|<span data-ttu-id="39e8c-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="39e8c-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="39e8c-116">\<oidEntry></span><span class="sxs-lookup"><span data-stu-id="39e8c-116">\<oidEntry></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidentry-element.md)|<span data-ttu-id="39e8c-117">Mapeia um OID do ASN.1 para um nome amigável.</span><span class="sxs-lookup"><span data-stu-id="39e8c-117">Maps an ASN.1 OID to a friendly name.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="39e8c-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="39e8c-118">Parent Elements</span></span>  
  
|<span data-ttu-id="39e8c-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="39e8c-119">Element</span></span>|<span data-ttu-id="39e8c-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="39e8c-120">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="39e8c-121">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="39e8c-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="39e8c-122">Contém configurações de criptografia.</span><span class="sxs-lookup"><span data-stu-id="39e8c-122">Contains cryptography settings.</span></span>|  
|`mscorlib`|<span data-ttu-id="39e8c-123">Contém o `cryptographySettings` elemento.</span><span class="sxs-lookup"><span data-stu-id="39e8c-123">Contains the `cryptographySettings` element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="39e8c-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="39e8c-124">Example</span></span>  
 <span data-ttu-id="39e8c-125">O exemplo a seguir mostra como usar o  **\<oidMap >** elemento para conter um mapeamento de um OID do algoritmo de hash RIPEMD-160 para uma implementação do algoritmo hash.</span><span class="sxs-lookup"><span data-stu-id="39e8c-125">The following example shows how to use the **\<oidMap>** element to contain a mapping of an OID for the RIPEMD-160 hash algorithm to an implementation of that hash algorithm.</span></span>  
  
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
            <oidEntry OID="1.3.36.3.2.1"  name="MyCryptoClass"/>  
         </oidMap>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="39e8c-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="39e8c-126">See also</span></span>

- [<span data-ttu-id="39e8c-127">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="39e8c-127">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="39e8c-128">Esquema de configurações de criptografia</span><span class="sxs-lookup"><span data-stu-id="39e8c-128">Cryptography Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)
- [<span data-ttu-id="39e8c-129">Serviços criptográficos</span><span class="sxs-lookup"><span data-stu-id="39e8c-129">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)
- [<span data-ttu-id="39e8c-130">Configurando classes de criptografia</span><span class="sxs-lookup"><span data-stu-id="39e8c-130">Configuring Cryptography Classes</span></span>](../../../../../docs/framework/configure-apps/configure-cryptography-classes.md)
- [<span data-ttu-id="39e8c-131">Mapeando identificadores de objeto para algoritmos de criptografia</span><span class="sxs-lookup"><span data-stu-id="39e8c-131">Mapping Object Identifiers to Cryptography Algorithms</span></span>](../../../../../docs/framework/configure-apps/map-object-identifiers-to-cryptography-algorithms.md)
