---
title: Elemento <cryptographySettings>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings
- http://schemas.microsoft.com/.NetConfiguration/v2.0#cryptographySettings
helpviewer_keywords:
- cryptographySettings element
- <cryptographySettings> element
ms.assetid: 6201b7da-bcb7-49f7-b9f5-ba1fe05573b9
ms.openlocfilehash: ec3a5a73caa901a21e22dbec7500af9153e01ef4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59164132"
---
# <a name="cryptographysettings-element"></a><span data-ttu-id="3025e-102">\<cryptographySettings > elemento</span><span class="sxs-lookup"><span data-stu-id="3025e-102">\<cryptographySettings> Element</span></span>
<span data-ttu-id="3025e-103">Contém configurações de criptografia.</span><span class="sxs-lookup"><span data-stu-id="3025e-103">Contains cryptography settings.</span></span>  
  
 <span data-ttu-id="3025e-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="3025e-104">\<configuration></span></span>  
<span data-ttu-id="3025e-105">\<mscorlib></span><span class="sxs-lookup"><span data-stu-id="3025e-105">\<mscorlib></span></span>  
<span data-ttu-id="3025e-106">\<cryptographySettings></span><span class="sxs-lookup"><span data-stu-id="3025e-106">\<cryptographySettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3025e-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3025e-107">Syntax</span></span>  
  
```xml  
      <cryptographySettings>   
</cryptographySettings>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3025e-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="3025e-108">Attributes and Elements</span></span>  
 <span data-ttu-id="3025e-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="3025e-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3025e-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="3025e-110">Attributes</span></span>  
 <span data-ttu-id="3025e-111">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="3025e-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="3025e-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="3025e-112">Child Elements</span></span>  
  
|<span data-ttu-id="3025e-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="3025e-113">Element</span></span>|<span data-ttu-id="3025e-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="3025e-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3025e-115">\<cryptoNameMapping></span><span class="sxs-lookup"><span data-stu-id="3025e-115">\<cryptoNameMapping></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptonamemapping-element.md)|<span data-ttu-id="3025e-116">Contém mapeamentos de classes para nomes amigáveis.</span><span class="sxs-lookup"><span data-stu-id="3025e-116">Contains mappings of classes to friendly names.</span></span>|  
|[<span data-ttu-id="3025e-117">\<oidMap></span><span class="sxs-lookup"><span data-stu-id="3025e-117">\<oidMap></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidmap-element.md)|<span data-ttu-id="3025e-118">Contém mapeamentos OID (identificador) de objeto do ASN.1 para classes.</span><span class="sxs-lookup"><span data-stu-id="3025e-118">Contains ASN.1 object identifier (OID) mappings to classes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3025e-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="3025e-119">Parent Elements</span></span>  
  
|<span data-ttu-id="3025e-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="3025e-120">Element</span></span>|<span data-ttu-id="3025e-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="3025e-121">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="3025e-122">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3025e-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`mscorlib`|<span data-ttu-id="3025e-123">Contém o `cryptographySettings` elemento.</span><span class="sxs-lookup"><span data-stu-id="3025e-123">Contains the `cryptographySettings` element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="3025e-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3025e-124">Example</span></span>  
 <span data-ttu-id="3025e-125">O exemplo a seguir mostra como usar o  **\<cryptographySettings >** elemento para conter os mapeamentos de nome de criptografia e mapeamentos OID.</span><span class="sxs-lookup"><span data-stu-id="3025e-125">The following example shows how use the **\<cryptographySettings>** element to contain cryptography name mappings and OID mappings.</span></span> <span data-ttu-id="3025e-126">Este exemplo configura o tempo de execução para que <xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType> retorna um `MyHashClass` objeto e o `MyCryptoClass` é mapeado para o identificador de objeto 1.3.36.2.1 de classe.</span><span class="sxs-lookup"><span data-stu-id="3025e-126">This example configures the runtime so that <xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType> returns a `MyHashClass` object and the `MyCryptoClass` class maps to the object identifier 1.3.36.2.1.</span></span>  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass   MyHash="MyHashClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
               <cryptoClass   MyCrypto="MyCryptoClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="System.Security.Cryptography.HashAlgorithm"  
                       class="MyHash"/>  
         </cryptoNameMapping>  
         <oidMap>  
            <oidEntry OID="1.3.36.3.2.1"   name="MyCryptoClass"/>  
         </oidMap>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3025e-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3025e-127">See also</span></span>

- [<span data-ttu-id="3025e-128">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="3025e-128">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="3025e-129">Esquema de configurações de criptografia</span><span class="sxs-lookup"><span data-stu-id="3025e-129">Cryptography Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)
- [<span data-ttu-id="3025e-130">Serviços criptográficos</span><span class="sxs-lookup"><span data-stu-id="3025e-130">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)
