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
ms.openlocfilehash: a28eaf68fe1e6ab3f26592eee5ae2d0f2e7a3256
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79155161"
---
# <a name="oidmap-element"></a><span data-ttu-id="54c89-102">Elemento \<oidMap></span><span class="sxs-lookup"><span data-stu-id="54c89-102">\<oidMap> Element</span></span>
<span data-ttu-id="54c89-103">Contém mapeamentos de OID (identificador de objeto) ASN para classes.</span><span class="sxs-lookup"><span data-stu-id="54c89-103">Contains ASN.1 object identifier (OID) mappings to classes.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<oidMap>**

## <a name="syntax"></a><span data-ttu-id="54c89-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="54c89-104">Syntax</span></span>  
  
```xml  
<oidMap>
</oidMap>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="54c89-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="54c89-105">Attributes and Elements</span></span>  
 <span data-ttu-id="54c89-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="54c89-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="54c89-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="54c89-107">Attributes</span></span>  
 <span data-ttu-id="54c89-108">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="54c89-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="54c89-109">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="54c89-109">Child Elements</span></span>  
  
|<span data-ttu-id="54c89-110">Elemento</span><span class="sxs-lookup"><span data-stu-id="54c89-110">Element</span></span>|<span data-ttu-id="54c89-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="54c89-111">Description</span></span>|  
|-------------|-----------------|  
|[\<oidEntry>](oidentry-element.md)|<span data-ttu-id="54c89-112">Mapeia uma OID ASN. 1 para um nome amigável.</span><span class="sxs-lookup"><span data-stu-id="54c89-112">Maps an ASN.1 OID to a friendly name.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="54c89-113">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="54c89-113">Parent Elements</span></span>  
  
|<span data-ttu-id="54c89-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="54c89-114">Element</span></span>|<span data-ttu-id="54c89-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="54c89-115">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="54c89-116">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="54c89-116">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="54c89-117">Contém configurações de criptografia.</span><span class="sxs-lookup"><span data-stu-id="54c89-117">Contains cryptography settings.</span></span>|  
|`mscorlib`|<span data-ttu-id="54c89-118">Contém o `cryptographySettings` elemento.</span><span class="sxs-lookup"><span data-stu-id="54c89-118">Contains the `cryptographySettings` element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="54c89-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="54c89-119">Example</span></span>  
 <span data-ttu-id="54c89-120">O exemplo a seguir mostra como usar o **\<oidMap>** elemento para conter um mapeamento de um OID para o algoritmo de hash RIPEMD-160 para uma implementação desse algoritmo de hash.</span><span class="sxs-lookup"><span data-stu-id="54c89-120">The following example shows how to use the **\<oidMap>** element to contain a mapping of an OID for the RIPEMD-160 hash algorithm to an implementation of that hash algorithm.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="54c89-121">Confira também</span><span class="sxs-lookup"><span data-stu-id="54c89-121">See also</span></span>

- [<span data-ttu-id="54c89-122">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="54c89-122">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="54c89-123">Esquema de configurações de criptografia</span><span class="sxs-lookup"><span data-stu-id="54c89-123">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="54c89-124">Serviços de Criptografia</span><span class="sxs-lookup"><span data-stu-id="54c89-124">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="54c89-125">Configurando classes de criptografia</span><span class="sxs-lookup"><span data-stu-id="54c89-125">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
- [<span data-ttu-id="54c89-126">Mapeando identificadores de objeto para algoritmos de criptografia</span><span class="sxs-lookup"><span data-stu-id="54c89-126">Mapping Object Identifiers to Cryptography Algorithms</span></span>](../../map-object-identifiers-to-cryptography-algorithms.md)
