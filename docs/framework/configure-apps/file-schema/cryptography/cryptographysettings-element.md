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
ms.openlocfilehash: 3c3513c05485550202f2fc5bcae1faabb0e75d47
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201805"
---
# <a name="cryptographysettings-element"></a><span data-ttu-id="21781-102">Elemento \<cryptographySettings></span><span class="sxs-lookup"><span data-stu-id="21781-102">\<cryptographySettings> Element</span></span>

<span data-ttu-id="21781-103">Contém configurações de criptografia.</span><span class="sxs-lookup"><span data-stu-id="21781-103">Contains cryptography settings.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<cryptographySettings>**

## <a name="syntax"></a><span data-ttu-id="21781-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="21781-104">Syntax</span></span>  
  
```xml  
      <cryptographySettings>
</cryptographySettings>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="21781-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="21781-105">Attributes and Elements</span></span>  

 <span data-ttu-id="21781-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="21781-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="21781-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="21781-107">Attributes</span></span>  

 <span data-ttu-id="21781-108">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="21781-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="21781-109">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="21781-109">Child Elements</span></span>  
  
|<span data-ttu-id="21781-110">Elemento</span><span class="sxs-lookup"><span data-stu-id="21781-110">Element</span></span>|<span data-ttu-id="21781-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="21781-111">Description</span></span>|  
|-------------|-----------------|  
|[\<cryptoNameMapping>](cryptonamemapping-element.md)|<span data-ttu-id="21781-112">Contém mapeamentos de classes para nomes amigáveis.</span><span class="sxs-lookup"><span data-stu-id="21781-112">Contains mappings of classes to friendly names.</span></span>|  
|[\<oidMap>](oidmap-element.md)|<span data-ttu-id="21781-113">Contém mapeamentos de OID (identificador de objeto) ASN para classes.</span><span class="sxs-lookup"><span data-stu-id="21781-113">Contains ASN.1 object identifier (OID) mappings to classes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="21781-114">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="21781-114">Parent Elements</span></span>  
  
|<span data-ttu-id="21781-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="21781-115">Element</span></span>|<span data-ttu-id="21781-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="21781-116">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="21781-117">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="21781-117">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`mscorlib`|<span data-ttu-id="21781-118">Contém o `cryptographySettings` elemento.</span><span class="sxs-lookup"><span data-stu-id="21781-118">Contains the `cryptographySettings` element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="21781-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="21781-119">Example</span></span>  

 <span data-ttu-id="21781-120">O exemplo a seguir mostra como usar o **\<cryptographySettings>** elemento para conter mapeamentos de nome de criptografia e mapeamentos de OID.</span><span class="sxs-lookup"><span data-stu-id="21781-120">The following example shows how use the **\<cryptographySettings>** element to contain cryptography name mappings and OID mappings.</span></span> <span data-ttu-id="21781-121">Este exemplo configura o tempo de execução para que <xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType> o retorne um `MyHashClass` objeto e a `MyCryptoClass` classe seja mapeada para o identificador de objeto 1.3.36.2.1.</span><span class="sxs-lookup"><span data-stu-id="21781-121">This example configures the runtime so that <xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType> returns a `MyHashClass` object and the `MyCryptoClass` class maps to the object identifier 1.3.36.2.1.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="21781-122">Veja também</span><span class="sxs-lookup"><span data-stu-id="21781-122">See also</span></span>

- [<span data-ttu-id="21781-123">Esquema do arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="21781-123">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="21781-124">Esquema de configurações de criptografia</span><span class="sxs-lookup"><span data-stu-id="21781-124">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="21781-125">Serviços criptográficos</span><span class="sxs-lookup"><span data-stu-id="21781-125">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
