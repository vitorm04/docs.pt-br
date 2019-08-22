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
ms.openlocfilehash: 572a5856c9f92f105e727df1ecd8eb2e0a92fc09
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664277"
---
# <a name="cryptographysettings-element"></a><span data-ttu-id="8dabc-102">\<Elemento de > cryptographySettings</span><span class="sxs-lookup"><span data-stu-id="8dabc-102">\<cryptographySettings> Element</span></span>
<span data-ttu-id="8dabc-103">Contém configurações de criptografia.</span><span class="sxs-lookup"><span data-stu-id="8dabc-103">Contains cryptography settings.</span></span>  
  
 <span data-ttu-id="8dabc-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="8dabc-104">\<configuration></span></span>  
<span data-ttu-id="8dabc-105">\<mscorlib></span><span class="sxs-lookup"><span data-stu-id="8dabc-105">\<mscorlib></span></span>  
<span data-ttu-id="8dabc-106">\<cryptographySettings></span><span class="sxs-lookup"><span data-stu-id="8dabc-106">\<cryptographySettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8dabc-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8dabc-107">Syntax</span></span>  
  
```xml  
      <cryptographySettings>   
</cryptographySettings>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8dabc-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="8dabc-108">Attributes and Elements</span></span>  
 <span data-ttu-id="8dabc-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="8dabc-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8dabc-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="8dabc-110">Attributes</span></span>  
 <span data-ttu-id="8dabc-111">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="8dabc-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="8dabc-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="8dabc-112">Child Elements</span></span>  
  
|<span data-ttu-id="8dabc-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="8dabc-113">Element</span></span>|<span data-ttu-id="8dabc-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="8dabc-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8dabc-115">\<cryptoNameMapping></span><span class="sxs-lookup"><span data-stu-id="8dabc-115">\<cryptoNameMapping></span></span>](cryptonamemapping-element.md)|<span data-ttu-id="8dabc-116">Contém mapeamentos de classes para nomes amigáveis.</span><span class="sxs-lookup"><span data-stu-id="8dabc-116">Contains mappings of classes to friendly names.</span></span>|  
|[<span data-ttu-id="8dabc-117">\<oidMap></span><span class="sxs-lookup"><span data-stu-id="8dabc-117">\<oidMap></span></span>](oidmap-element.md)|<span data-ttu-id="8dabc-118">Contém mapeamentos de OID (identificador de objeto) ASN para classes.</span><span class="sxs-lookup"><span data-stu-id="8dabc-118">Contains ASN.1 object identifier (OID) mappings to classes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8dabc-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="8dabc-119">Parent Elements</span></span>  
  
|<span data-ttu-id="8dabc-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="8dabc-120">Element</span></span>|<span data-ttu-id="8dabc-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="8dabc-121">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="8dabc-122">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8dabc-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`mscorlib`|<span data-ttu-id="8dabc-123">Contém o `cryptographySettings` elemento.</span><span class="sxs-lookup"><span data-stu-id="8dabc-123">Contains the `cryptographySettings` element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="8dabc-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8dabc-124">Example</span></span>  
 <span data-ttu-id="8dabc-125">O exemplo a seguir mostra como usar o  **\<elemento cryptographySettings >** para conter mapeamentos de nome de criptografia e mapeamentos de OID.</span><span class="sxs-lookup"><span data-stu-id="8dabc-125">The following example shows how use the **\<cryptographySettings>** element to contain cryptography name mappings and OID mappings.</span></span> <span data-ttu-id="8dabc-126">Este exemplo configura o tempo de execução para que <xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType> o retorne um `MyHashClass` objeto `MyCryptoClass` e a classe seja mapeada para o identificador de objeto 1.3.36.2.1.</span><span class="sxs-lookup"><span data-stu-id="8dabc-126">This example configures the runtime so that <xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType> returns a `MyHashClass` object and the `MyCryptoClass` class maps to the object identifier 1.3.36.2.1.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8dabc-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8dabc-127">See also</span></span>

- [<span data-ttu-id="8dabc-128">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="8dabc-128">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="8dabc-129">Esquema de configurações de criptografia</span><span class="sxs-lookup"><span data-stu-id="8dabc-129">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="8dabc-130">Serviços criptográficos</span><span class="sxs-lookup"><span data-stu-id="8dabc-130">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)
