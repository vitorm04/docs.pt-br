---
title: Elemento <cryptoNameMapping>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#cryptoNameMapping
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping
helpviewer_keywords:
- <cryptoNameMapping> element
- cryptoNameMapping element
ms.assetid: c59c9494-149b-4ce6-b38d-371f896ae85c
ms.openlocfilehash: 9ffae33a3c8a06d6cfcabf5a58b7d72baeda79c5
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201792"
---
# <a name="cryptonamemapping-element"></a><span data-ttu-id="4dcbd-102">Elemento \<cryptoNameMapping></span><span class="sxs-lookup"><span data-stu-id="4dcbd-102">\<cryptoNameMapping> Element</span></span>

<span data-ttu-id="4dcbd-103">Contém mapeamentos de classes para nomes amigáveis.</span><span class="sxs-lookup"><span data-stu-id="4dcbd-103">Contains mappings of classes to friendly names.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cryptoNameMapping>**

## <a name="syntax"></a><span data-ttu-id="4dcbd-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4dcbd-104">Syntax</span></span>  
  
```xml  
      <cryptoNameMapping>
</cryptoNameMapping>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4dcbd-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="4dcbd-105">Attributes and Elements</span></span>  

 <span data-ttu-id="4dcbd-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="4dcbd-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4dcbd-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="4dcbd-107">Attributes</span></span>  

 <span data-ttu-id="4dcbd-108">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="4dcbd-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="4dcbd-109">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="4dcbd-109">Child Elements</span></span>  
  
|<span data-ttu-id="4dcbd-110">Elemento</span><span class="sxs-lookup"><span data-stu-id="4dcbd-110">Element</span></span>|<span data-ttu-id="4dcbd-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="4dcbd-111">Description</span></span>|  
|-------------|-----------------|  
|`cryptoClasses`|<span data-ttu-id="4dcbd-112">Contém uma lista de classes de criptografia que têm um mapeamento para um nome amigável no **\<nameEntry>** elemento.</span><span class="sxs-lookup"><span data-stu-id="4dcbd-112">Contains a list of cryptography classes that have a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|`nameEntry`|<span data-ttu-id="4dcbd-113">Mapeia um nome de classe para um nome de algoritmo amigável, o que permite que uma classe tenha vários nomes amigáveis.</span><span class="sxs-lookup"><span data-stu-id="4dcbd-113">Maps a class name to a friendly algorithm name, which allows one class to have many friendly names.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4dcbd-114">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="4dcbd-114">Parent Elements</span></span>  
  
|<span data-ttu-id="4dcbd-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="4dcbd-115">Element</span></span>|<span data-ttu-id="4dcbd-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="4dcbd-116">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="4dcbd-117">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4dcbd-117">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="4dcbd-118">Contém configurações de criptografia.</span><span class="sxs-lookup"><span data-stu-id="4dcbd-118">Contains cryptography settings.</span></span>|  
|`cryptoNameMapping`|<span data-ttu-id="4dcbd-119">Contém mapeamentos de classes para nomes amigáveis.</span><span class="sxs-lookup"><span data-stu-id="4dcbd-119">Contains mappings of classes to friendly names.</span></span>|  
|`mscorlib`|<span data-ttu-id="4dcbd-120">Contém o \<cryptographySettings> elemento.</span><span class="sxs-lookup"><span data-stu-id="4dcbd-120">Contains the \<cryptographySettings> element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="4dcbd-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4dcbd-121">Example</span></span>  

 <span data-ttu-id="4dcbd-122">O exemplo a seguir mostra como usar o **\<cryptoNameMapping>** elemento para fazer referência a uma classe de criptografia e configurar o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="4dcbd-122">The following example shows how to use the **\<cryptoNameMapping>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="4dcbd-123">Em seguida, você pode passar a cadeia de caracteres "RSA" para o <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> método e usar o <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> método para retornar um `MyCryptoRSAClass` objeto.</span><span class="sxs-lookup"><span data-stu-id="4dcbd-123">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass   MyCryptoRSA="MyCryptoRSAClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="RSA" class="MyCryptoRSA"/>  
            <nameEntry name="System.Security.Cryptography.AsymmetricAlgorithm"  
                       class="MyCryptoRSA"/>  
         </cryptoNameMapping>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4dcbd-124">Veja também</span><span class="sxs-lookup"><span data-stu-id="4dcbd-124">See also</span></span>

- [<span data-ttu-id="4dcbd-125">Esquema do arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="4dcbd-125">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="4dcbd-126">Esquema de configurações de criptografia</span><span class="sxs-lookup"><span data-stu-id="4dcbd-126">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="4dcbd-127">Serviços criptográficos</span><span class="sxs-lookup"><span data-stu-id="4dcbd-127">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="4dcbd-128">Configurando classes de criptografia</span><span class="sxs-lookup"><span data-stu-id="4dcbd-128">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
