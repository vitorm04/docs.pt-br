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
ms.openlocfilehash: fe6de09213c6f980e8eb205a318aae50033b2a84
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155226"
---
# <a name="cryptographysettings-element"></a><span data-ttu-id="9b27c-102">\<criptografiaConfigurações> Elemento</span><span class="sxs-lookup"><span data-stu-id="9b27c-102">\<cryptographySettings> Element</span></span>
<span data-ttu-id="9b27c-103">Contém configurações de criptografia.</span><span class="sxs-lookup"><span data-stu-id="9b27c-103">Contains cryptography settings.</span></span>  

<span data-ttu-id="9b27c-104">[**\<>de configuração**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="9b27c-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="9b27c-105">&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)</span><span class="sxs-lookup"><span data-stu-id="9b27c-105">&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)</span></span>\
<span data-ttu-id="9b27c-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<criptografiaConfigurações>**</span><span class="sxs-lookup"><span data-stu-id="9b27c-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<cryptographySettings>**</span></span>

## <a name="syntax"></a><span data-ttu-id="9b27c-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9b27c-107">Syntax</span></span>  
  
```xml  
      <cryptographySettings>
</cryptographySettings>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9b27c-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="9b27c-108">Attributes and Elements</span></span>  
 <span data-ttu-id="9b27c-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="9b27c-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9b27c-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="9b27c-110">Attributes</span></span>  
 <span data-ttu-id="9b27c-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="9b27c-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="9b27c-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="9b27c-112">Child Elements</span></span>  
  
|<span data-ttu-id="9b27c-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="9b27c-113">Element</span></span>|<span data-ttu-id="9b27c-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="9b27c-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9b27c-115">\<>de mapeamento de nomes de cripto</span><span class="sxs-lookup"><span data-stu-id="9b27c-115">\<cryptoNameMapping></span></span>](cryptonamemapping-element.md)|<span data-ttu-id="9b27c-116">Contém mapeamentos de classes para nomes amigáveis.</span><span class="sxs-lookup"><span data-stu-id="9b27c-116">Contains mappings of classes to friendly names.</span></span>|  
|[<span data-ttu-id="9b27c-117">\<oidMap></span><span class="sxs-lookup"><span data-stu-id="9b27c-117">\<oidMap></span></span>](oidmap-element.md)|<span data-ttu-id="9b27c-118">Contém mapeamentos do identificador de objeto ASN.1 (OID) para classes.</span><span class="sxs-lookup"><span data-stu-id="9b27c-118">Contains ASN.1 object identifier (OID) mappings to classes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9b27c-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="9b27c-119">Parent Elements</span></span>  
  
|<span data-ttu-id="9b27c-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="9b27c-120">Element</span></span>|<span data-ttu-id="9b27c-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="9b27c-121">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="9b27c-122">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9b27c-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`mscorlib`|<span data-ttu-id="9b27c-123">Contém `cryptographySettings` o elemento.</span><span class="sxs-lookup"><span data-stu-id="9b27c-123">Contains the `cryptographySettings` element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="9b27c-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9b27c-124">Example</span></span>  
 <span data-ttu-id="9b27c-125">O exemplo a seguir mostra como usar o \*\* \<elemento cryptographySettings>\*\* para conter mapeamentos de nomes de criptografia e mapeamentos oID.</span><span class="sxs-lookup"><span data-stu-id="9b27c-125">The following example shows how use the **\<cryptographySettings>** element to contain cryptography name mappings and OID mappings.</span></span> <span data-ttu-id="9b27c-126">Este exemplo configura o tempo <xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType> de `MyHashClass` execução `MyCryptoClass` para que o retorno de um objeto e os mapas de classe para o identificador de objeto 1.3.36.2.1.</span><span class="sxs-lookup"><span data-stu-id="9b27c-126">This example configures the runtime so that <xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType> returns a `MyHashClass` object and the `MyCryptoClass` class maps to the object identifier 1.3.36.2.1.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9b27c-127">Confira também</span><span class="sxs-lookup"><span data-stu-id="9b27c-127">See also</span></span>

- [<span data-ttu-id="9b27c-128">Esquema de arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="9b27c-128">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="9b27c-129">Esquema de configurações de criptografia</span><span class="sxs-lookup"><span data-stu-id="9b27c-129">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="9b27c-130">Serviços criptográficos</span><span class="sxs-lookup"><span data-stu-id="9b27c-130">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
