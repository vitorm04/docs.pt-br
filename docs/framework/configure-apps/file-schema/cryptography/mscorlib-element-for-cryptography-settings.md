---
title: Elemento <mscorlib> para configurações de criptografia
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#mscorlib
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib
helpviewer_keywords:
- mscorlib element
- <mscorlib> element
ms.assetid: d549668f-31f1-4b92-8021-a9135c09ca3c
ms.openlocfilehash: 4e2159cda5f35b5795804dede09ec17d07d71b23
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699742"
---
# <a name="mscorlib-element-for-cryptography-settings"></a><span data-ttu-id="54b2e-102">\<mscorlib > elemento para configurações de criptografia</span><span class="sxs-lookup"><span data-stu-id="54b2e-102">\<mscorlib> Element for Cryptography Settings</span></span>
<span data-ttu-id="54b2e-103">Contém o [elemento \<cryptographySettings >](cryptographysettings-element.md).</span><span class="sxs-lookup"><span data-stu-id="54b2e-103">Contains the [\<cryptographySettings> element](cryptographysettings-element.md).</span></span>  
  
[<span data-ttu-id="54b2e-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="54b2e-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="54b2e-105">&nbsp; @ no__t-1 **\<mscorlib >**</span><span class="sxs-lookup"><span data-stu-id="54b2e-105">&nbsp;&nbsp;**\<mscorlib>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54b2e-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="54b2e-106">Syntax</span></span>  
  
```xml  
      <mscorlib>   
</mscorlib>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="54b2e-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="54b2e-107">Attributes and Elements</span></span>  
 <span data-ttu-id="54b2e-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="54b2e-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="54b2e-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="54b2e-109">Attributes</span></span>  
 <span data-ttu-id="54b2e-110">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="54b2e-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="54b2e-111">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="54b2e-111">Child Elements</span></span>  
  
|<span data-ttu-id="54b2e-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="54b2e-112">Element</span></span>|<span data-ttu-id="54b2e-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="54b2e-113">Description</span></span>|  
|-------------|-----------------|  
|`cryptographySettings`|<span data-ttu-id="54b2e-114">Contém configurações de criptografia.</span><span class="sxs-lookup"><span data-stu-id="54b2e-114">Contains cryptography settings.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="54b2e-115">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="54b2e-115">Parent Elements</span></span>  
  
|<span data-ttu-id="54b2e-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="54b2e-116">Element</span></span>|<span data-ttu-id="54b2e-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="54b2e-117">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="54b2e-118">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="54b2e-118">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="54b2e-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="54b2e-119">Example</span></span>  
 <span data-ttu-id="54b2e-120">O exemplo a seguir mostra como usar o elemento **\<mscorlib >** para fazer referência a uma classe de criptografia e configurar o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="54b2e-120">The following example shows how to use the **\<mscorlib>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="54b2e-121">Em seguida, você pode passar a cadeia de caracteres "RSA" para o método <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> e usar o método <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> para retornar um objeto `MyCryptoRSAClass`.</span><span class="sxs-lookup"><span data-stu-id="54b2e-121">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="54b2e-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="54b2e-122">See also</span></span>

- <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A>
- <xref:System.Security.Cryptography>
- [<span data-ttu-id="54b2e-123">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="54b2e-123">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="54b2e-124">Esquema de configurações de criptografia</span><span class="sxs-lookup"><span data-stu-id="54b2e-124">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="54b2e-125">Serviços criptográficos</span><span class="sxs-lookup"><span data-stu-id="54b2e-125">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="54b2e-126">Configurando classes de criptografia</span><span class="sxs-lookup"><span data-stu-id="54b2e-126">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
