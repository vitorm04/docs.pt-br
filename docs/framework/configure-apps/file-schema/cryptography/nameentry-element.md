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
ms.openlocfilehash: a339638587f8b544bbc1b0073553f6232ce09694
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699773"
---
# <a name="nameentry-element"></a><span data-ttu-id="21068-102">\<elemento de > nameEntry</span><span class="sxs-lookup"><span data-stu-id="21068-102">\<nameEntry> Element</span></span>
<span data-ttu-id="21068-103">Mapeia um nome de classe para um nome de algoritmo amigável, o que permite que uma classe tenha vários nomes amigáveis.</span><span class="sxs-lookup"><span data-stu-id="21068-103">Maps a class name to a friendly algorithm name, which allows one class to have many friendly names.</span></span>  
  
[<span data-ttu-id="21068-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="21068-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="21068-105">&nbsp;&nbsp;[ **\<mscorlib >** ](mscorlib-element-for-cryptography-settings.md)</span><span class="sxs-lookup"><span data-stu-id="21068-105">&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)</span></span>  
<span data-ttu-id="21068-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<cryptographySettings >** ](cryptographysettings-element.md)</span><span class="sxs-lookup"><span data-stu-id="21068-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)</span></span>  
<span data-ttu-id="21068-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<cryptoNameMapping >** ](cryptonamemapping-element.md)</span><span class="sxs-lookup"><span data-stu-id="21068-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoNameMapping>**](cryptonamemapping-element.md)</span></span>  
<span data-ttu-id="21068-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<nameEntry >**</span><span class="sxs-lookup"><span data-stu-id="21068-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<nameEntry>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21068-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="21068-109">Syntax</span></span>  
  
```xml  
<nameEntry name="friendly name" Class="class name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="21068-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="21068-110">Attributes and Elements</span></span>  
 <span data-ttu-id="21068-111">As seções a seguir descrevem os atributos, bem como os elementos filhos e pais.</span><span class="sxs-lookup"><span data-stu-id="21068-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="21068-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="21068-112">Attributes</span></span>  
  
|<span data-ttu-id="21068-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="21068-113">Attribute</span></span>|<span data-ttu-id="21068-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="21068-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="21068-115">**name**</span><span class="sxs-lookup"><span data-stu-id="21068-115">**name**</span></span>|<span data-ttu-id="21068-116">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="21068-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="21068-117">Especifica o nome amigável do algoritmo que a classe de criptografia implementa.</span><span class="sxs-lookup"><span data-stu-id="21068-117">Specifies the friendly name of the algorithm that the cryptography class implements.</span></span>|  
|<span data-ttu-id="21068-118">**class**</span><span class="sxs-lookup"><span data-stu-id="21068-118">**class**</span></span>|<span data-ttu-id="21068-119">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="21068-119">Required attribute.</span></span><br /><br /> <span data-ttu-id="21068-120">Especifica o valor do atributo **Name** no elemento [\<cryptoClass >](cryptoclass-element.md) .</span><span class="sxs-lookup"><span data-stu-id="21068-120">Specifies the value for the **name** attribute in the [\<cryptoClass>](cryptoclass-element.md) element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="21068-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="21068-121">Child Elements</span></span>  
 <span data-ttu-id="21068-122">None.</span><span class="sxs-lookup"><span data-stu-id="21068-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="21068-123">Elementos Pai</span><span class="sxs-lookup"><span data-stu-id="21068-123">Parent Elements</span></span>  
  
|<span data-ttu-id="21068-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="21068-124">Element</span></span>|<span data-ttu-id="21068-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="21068-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="21068-126">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="21068-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.web`|<span data-ttu-id="21068-127">Especifica o elemento raiz para a seção de configuração ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="21068-127">Specifies the root element for the ASP.NET configuration section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="21068-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="21068-128">Remarks</span></span>  
 <span data-ttu-id="21068-129">O atributo **Name** pode ser o nome de uma das classes abstratas encontradas no namespace <xref:System.Security.Cryptography>.</span><span class="sxs-lookup"><span data-stu-id="21068-129">The **name** attribute can be the name of one of the abstract classes found in the <xref:System.Security.Cryptography> namespace.</span></span> <span data-ttu-id="21068-130">Quando você chama o método **Create** em uma classe de criptografia abstrata, o nome da classe abstrata é passado para o método <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A>.</span><span class="sxs-lookup"><span data-stu-id="21068-130">When you call the **Create** method on an abstract cryptography class, the abstract class name is passed to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A> method.</span></span> <span data-ttu-id="21068-131">**CreateFromName** retorna uma instância do tipo indicado pelo atributo de **classe** .</span><span class="sxs-lookup"><span data-stu-id="21068-131">**CreateFromName** returns an instance of the type indicated by the **class** attribute.</span></span> <span data-ttu-id="21068-132">Se o atributo **Name** for um nome curto, como RSA, você poderá usar esse nome ao chamar o método **CreateFromName** .</span><span class="sxs-lookup"><span data-stu-id="21068-132">If the **name** attribute is a short name, such as RSA, you can use that name when calling the **CreateFromName** method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="21068-133">{1&gt;Exemplo&lt;1}</span><span class="sxs-lookup"><span data-stu-id="21068-133">Example</span></span>  
 <span data-ttu-id="21068-134">O exemplo a seguir mostra como usar o elemento **\<nameEntry >** para fazer referência a uma classe de criptografia e configurar o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="21068-134">The following example shows how to use the **\<nameEntry>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="21068-135">Em seguida, você pode passar a cadeia de caracteres "RSA" para o método <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> e usar o método <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> para retornar um objeto `MyCryptoRSAClass`.</span><span class="sxs-lookup"><span data-stu-id="21068-135">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="21068-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="21068-136">See also</span></span>

- [<span data-ttu-id="21068-137">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="21068-137">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="21068-138">Esquema de configurações de criptografia</span><span class="sxs-lookup"><span data-stu-id="21068-138">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="21068-139">Serviços criptográficos</span><span class="sxs-lookup"><span data-stu-id="21068-139">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="21068-140">Configurando classes de criptografia</span><span class="sxs-lookup"><span data-stu-id="21068-140">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
