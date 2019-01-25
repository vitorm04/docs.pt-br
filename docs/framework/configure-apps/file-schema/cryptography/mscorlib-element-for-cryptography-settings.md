---
title: '&lt;mscorlib&gt; elemento para configurações de criptografia'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#mscorlib
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib
helpviewer_keywords:
- mscorlib element
- <mscorlib> element
ms.assetid: d549668f-31f1-4b92-8021-a9135c09ca3c
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 0615a68add60b02a875921b1abb3776267db1731
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54527582"
---
# <a name="ltmscorlibgt-element-for-cryptography-settings"></a><span data-ttu-id="5a263-102">&lt;mscorlib&gt; elemento para configurações de criptografia</span><span class="sxs-lookup"><span data-stu-id="5a263-102">&lt;mscorlib&gt; Element for Cryptography Settings</span></span>
<span data-ttu-id="5a263-103">Contém o [ \<cryptographySettings > elemento](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptographysettings-element.md).</span><span class="sxs-lookup"><span data-stu-id="5a263-103">Contains the [\<cryptographySettings> element](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptographysettings-element.md).</span></span>  
  
 <span data-ttu-id="5a263-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="5a263-104">\<configuration></span></span>  
<span data-ttu-id="5a263-105">\<mscorlib></span><span class="sxs-lookup"><span data-stu-id="5a263-105">\<mscorlib></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a263-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5a263-106">Syntax</span></span>  
  
```xml  
      <mscorlib>   
</mscorlib>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5a263-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="5a263-107">Attributes and Elements</span></span>  
 <span data-ttu-id="5a263-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="5a263-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5a263-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="5a263-109">Attributes</span></span>  
 <span data-ttu-id="5a263-110">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="5a263-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5a263-111">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="5a263-111">Child Elements</span></span>  
  
|<span data-ttu-id="5a263-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="5a263-112">Element</span></span>|<span data-ttu-id="5a263-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="5a263-113">Description</span></span>|  
|-------------|-----------------|  
|`cryptographySettings`|<span data-ttu-id="5a263-114">Contém configurações de criptografia.</span><span class="sxs-lookup"><span data-stu-id="5a263-114">Contains cryptography settings.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5a263-115">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="5a263-115">Parent Elements</span></span>  
  
|<span data-ttu-id="5a263-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="5a263-116">Element</span></span>|<span data-ttu-id="5a263-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="5a263-117">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="5a263-118">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5a263-118">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="5a263-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5a263-119">Example</span></span>  
 <span data-ttu-id="5a263-120">O exemplo a seguir mostra como usar o  **\<mscorlib >** elemento para fazer referência a uma classe de criptografia e configurar o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="5a263-120">The following example shows how to use the **\<mscorlib>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="5a263-121">Em seguida, você pode passar a cadeia de caracteres "RSA" para o <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> método e o uso de <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> método para retornar um `MyCryptoRSAClass` objeto.</span><span class="sxs-lookup"><span data-stu-id="5a263-121">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5a263-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5a263-122">See also</span></span>
- <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A>
- <xref:System.Security.Cryptography>
- [<span data-ttu-id="5a263-123">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="5a263-123">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="5a263-124">Esquema de configurações de criptografia</span><span class="sxs-lookup"><span data-stu-id="5a263-124">Cryptography Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)
- [<span data-ttu-id="5a263-125">Serviços criptográficos</span><span class="sxs-lookup"><span data-stu-id="5a263-125">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)
- [<span data-ttu-id="5a263-126">Configurando classes de criptografia</span><span class="sxs-lookup"><span data-stu-id="5a263-126">Configuring Cryptography Classes</span></span>](../../../../../docs/framework/configure-apps/configure-cryptography-classes.md)
