---
title: Elemento <nameEntry>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#nameEntry
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping/nameEntry
helpviewer_keywords:
- <nameEntry> element
- nameEntry element
ms.assetid: 7d7535e9-4b4a-4b8c-82e2-e40dff5a7821
ms.openlocfilehash: 9270552245b3867f0f09741ded3f9da6a8b6c135
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664264"
---
# <a name="nameentry-element"></a><span data-ttu-id="17f60-102">\<Elemento de > nameEntry</span><span class="sxs-lookup"><span data-stu-id="17f60-102">\<nameEntry> Element</span></span>
<span data-ttu-id="17f60-103">Mapeia um nome de classe para um nome de algoritmo amigável, o que permite que uma classe tenha vários nomes amigáveis.</span><span class="sxs-lookup"><span data-stu-id="17f60-103">Maps a class name to a friendly algorithm name, which allows one class to have many friendly names.</span></span>  
  
 <span data-ttu-id="17f60-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="17f60-104">\<configuration></span></span>  
<span data-ttu-id="17f60-105">\<mscorlib></span><span class="sxs-lookup"><span data-stu-id="17f60-105">\<mscorlib></span></span>  
<span data-ttu-id="17f60-106">\<cryptographySettings></span><span class="sxs-lookup"><span data-stu-id="17f60-106">\<cryptographySettings></span></span>  
<span data-ttu-id="17f60-107">\<cryptoNameMapping></span><span class="sxs-lookup"><span data-stu-id="17f60-107">\<cryptoNameMapping></span></span>  
<span data-ttu-id="17f60-108">\<nameEntry></span><span class="sxs-lookup"><span data-stu-id="17f60-108">\<nameEntry></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17f60-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="17f60-109">Syntax</span></span>  
  
```xml  
<nameEntry name="friendly name" Class="class name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="17f60-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="17f60-110">Attributes and Elements</span></span>  
 <span data-ttu-id="17f60-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="17f60-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="17f60-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="17f60-112">Attributes</span></span>  
  
|<span data-ttu-id="17f60-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="17f60-113">Attribute</span></span>|<span data-ttu-id="17f60-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="17f60-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="17f60-115">**name**</span><span class="sxs-lookup"><span data-stu-id="17f60-115">**name**</span></span>|<span data-ttu-id="17f60-116">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="17f60-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="17f60-117">Especifica o nome amigável do algoritmo que a classe de criptografia implementa.</span><span class="sxs-lookup"><span data-stu-id="17f60-117">Specifies the friendly name of the algorithm that the cryptography class implements.</span></span>|  
|<span data-ttu-id="17f60-118">**class**</span><span class="sxs-lookup"><span data-stu-id="17f60-118">**class**</span></span>|<span data-ttu-id="17f60-119">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="17f60-119">Required attribute.</span></span><br /><br /> <span data-ttu-id="17f60-120">Especifica o valor do atributo **Name** no [ \<elemento > cryptoClass](cryptoclass-element.md) .</span><span class="sxs-lookup"><span data-stu-id="17f60-120">Specifies the value for the **name** attribute in the [\<cryptoClass>](cryptoclass-element.md) element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="17f60-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="17f60-121">Child Elements</span></span>  
 <span data-ttu-id="17f60-122">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="17f60-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="17f60-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="17f60-123">Parent Elements</span></span>  
  
|<span data-ttu-id="17f60-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="17f60-124">Element</span></span>|<span data-ttu-id="17f60-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="17f60-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="17f60-126">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="17f60-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.web`|<span data-ttu-id="17f60-127">Especifica o elemento raiz para a seção de configuração ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="17f60-127">Specifies the root element for the ASP.NET configuration section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="17f60-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="17f60-128">Remarks</span></span>  
 <span data-ttu-id="17f60-129">O atributo **Name** pode ser o nome de uma das classes abstratas encontradas no <xref:System.Security.Cryptography> namespace.</span><span class="sxs-lookup"><span data-stu-id="17f60-129">The **name** attribute can be the name of one of the abstract classes found in the <xref:System.Security.Cryptography> namespace.</span></span> <span data-ttu-id="17f60-130">Quando você chama o método **Create** em uma classe de criptografia abstrata, o nome da classe abstrata é passado <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A> para o método.</span><span class="sxs-lookup"><span data-stu-id="17f60-130">When you call the **Create** method on an abstract cryptography class, the abstract class name is passed to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A> method.</span></span> <span data-ttu-id="17f60-131">CreateFromName retorna uma instância do tipo indicado pelo atributo de **classe** .</span><span class="sxs-lookup"><span data-stu-id="17f60-131">**CreateFromName** returns an instance of the type indicated by the **class** attribute.</span></span> <span data-ttu-id="17f60-132">Se o atributo **Name** for um nome curto, como RSA, você poderá usar esse nome ao chamar o método CreateFromName.</span><span class="sxs-lookup"><span data-stu-id="17f60-132">If the **name** attribute is a short name, such as RSA, you can use that name when calling the **CreateFromName** method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="17f60-133">Exemplo</span><span class="sxs-lookup"><span data-stu-id="17f60-133">Example</span></span>  
 <span data-ttu-id="17f60-134">O exemplo a seguir mostra como usar o  **\<elemento > nameEntry** para fazer referência a uma classe de criptografia e configurar o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="17f60-134">The following example shows how to use the **\<nameEntry>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="17f60-135">Em seguida, você pode passar a cadeia de caracteres " <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> RSA" para o <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> método e usar o `MyCryptoRSAClass` método para retornar um objeto.</span><span class="sxs-lookup"><span data-stu-id="17f60-135">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="17f60-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="17f60-136">See also</span></span>

- [<span data-ttu-id="17f60-137">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="17f60-137">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="17f60-138">Esquema de configurações de criptografia</span><span class="sxs-lookup"><span data-stu-id="17f60-138">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="17f60-139">Serviços criptográficos</span><span class="sxs-lookup"><span data-stu-id="17f60-139">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)
- [<span data-ttu-id="17f60-140">Configurando classes de criptografia</span><span class="sxs-lookup"><span data-stu-id="17f60-140">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
