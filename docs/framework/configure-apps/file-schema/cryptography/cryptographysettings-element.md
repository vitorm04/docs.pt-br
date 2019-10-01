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
ms.openlocfilehash: 96a8c9accc56274b5cc13dc2a871165857b3a2d9
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699816"
---
# <a name="cryptographysettings-element"></a><span data-ttu-id="87c41-102">\<cryptographySettings > elemento</span><span class="sxs-lookup"><span data-stu-id="87c41-102">\<cryptographySettings> Element</span></span>
<span data-ttu-id="87c41-103">Contém configurações de criptografia.</span><span class="sxs-lookup"><span data-stu-id="87c41-103">Contains cryptography settings.</span></span>  
  
[<span data-ttu-id="87c41-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="87c41-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="87c41-105">&nbsp; @ no__t-1[ **\<mscorlib >** ](mscorlib-element-for-cryptography-settings.md)</span><span class="sxs-lookup"><span data-stu-id="87c41-105">&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)</span></span>  
<span data-ttu-id="87c41-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 **\<cryptographySettings >**</span><span class="sxs-lookup"><span data-stu-id="87c41-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<cryptographySettings>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87c41-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="87c41-107">Syntax</span></span>  
  
```xml  
      <cryptographySettings>   
</cryptographySettings>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="87c41-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="87c41-108">Attributes and Elements</span></span>  
 <span data-ttu-id="87c41-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="87c41-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="87c41-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="87c41-110">Attributes</span></span>  
 <span data-ttu-id="87c41-111">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="87c41-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="87c41-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="87c41-112">Child Elements</span></span>  
  
|<span data-ttu-id="87c41-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="87c41-113">Element</span></span>|<span data-ttu-id="87c41-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="87c41-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="87c41-115">\<cryptoNameMapping></span><span class="sxs-lookup"><span data-stu-id="87c41-115">\<cryptoNameMapping></span></span>](cryptonamemapping-element.md)|<span data-ttu-id="87c41-116">Contém mapeamentos de classes para nomes amigáveis.</span><span class="sxs-lookup"><span data-stu-id="87c41-116">Contains mappings of classes to friendly names.</span></span>|  
|[<span data-ttu-id="87c41-117">\<oidMap></span><span class="sxs-lookup"><span data-stu-id="87c41-117">\<oidMap></span></span>](oidmap-element.md)|<span data-ttu-id="87c41-118">Contém mapeamentos de OID (identificador de objeto) ASN para classes.</span><span class="sxs-lookup"><span data-stu-id="87c41-118">Contains ASN.1 object identifier (OID) mappings to classes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="87c41-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="87c41-119">Parent Elements</span></span>  
  
|<span data-ttu-id="87c41-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="87c41-120">Element</span></span>|<span data-ttu-id="87c41-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="87c41-121">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="87c41-122">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="87c41-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`mscorlib`|<span data-ttu-id="87c41-123">Contém o `cryptographySettings` elemento.</span><span class="sxs-lookup"><span data-stu-id="87c41-123">Contains the `cryptographySettings` element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="87c41-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="87c41-124">Example</span></span>  
 <span data-ttu-id="87c41-125">O exemplo a seguir mostra como usar o elemento **\<cryptographySettings >** para conter mapeamentos de nome de criptografia e mapeamentos de OID.</span><span class="sxs-lookup"><span data-stu-id="87c41-125">The following example shows how use the **\<cryptographySettings>** element to contain cryptography name mappings and OID mappings.</span></span> <span data-ttu-id="87c41-126">Este exemplo configura o tempo de execução para que <xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType> retorne um objeto `MyHashClass` e a classe `MyCryptoClass` seja mapeada para o identificador de objeto 1.3.36.2.1.</span><span class="sxs-lookup"><span data-stu-id="87c41-126">This example configures the runtime so that <xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType> returns a `MyHashClass` object and the `MyCryptoClass` class maps to the object identifier 1.3.36.2.1.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="87c41-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="87c41-127">See also</span></span>

- [<span data-ttu-id="87c41-128">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="87c41-128">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="87c41-129">Esquema de configurações de criptografia</span><span class="sxs-lookup"><span data-stu-id="87c41-129">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="87c41-130">Serviços criptográficos</span><span class="sxs-lookup"><span data-stu-id="87c41-130">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
