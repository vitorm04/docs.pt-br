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
ms.openlocfilehash: 4341b1fcd3762e5aa55f0ba988f7f49d4b5cacd6
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201766"
---
# <a name="nameentry-element"></a><span data-ttu-id="bc9f1-102">Elemento \<nameEntry></span><span class="sxs-lookup"><span data-stu-id="bc9f1-102">\<nameEntry> Element</span></span>

<span data-ttu-id="bc9f1-103">Mapeia um nome de classe para um nome de algoritmo amigável, o que permite que uma classe tenha vários nomes amigáveis.</span><span class="sxs-lookup"><span data-stu-id="bc9f1-103">Maps a class name to a friendly algorithm name, which allows one class to have many friendly names.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoNameMapping>**](cryptonamemapping-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<nameEntry>**  
  
## <a name="syntax"></a><span data-ttu-id="bc9f1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bc9f1-104">Syntax</span></span>  
  
```xml  
<nameEntry name="friendly name" Class="class name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bc9f1-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="bc9f1-105">Attributes and Elements</span></span>  

 <span data-ttu-id="bc9f1-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="bc9f1-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bc9f1-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="bc9f1-107">Attributes</span></span>  
  
|<span data-ttu-id="bc9f1-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="bc9f1-108">Attribute</span></span>|<span data-ttu-id="bc9f1-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="bc9f1-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="bc9f1-110">**name**</span><span class="sxs-lookup"><span data-stu-id="bc9f1-110">**name**</span></span>|<span data-ttu-id="bc9f1-111">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="bc9f1-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="bc9f1-112">Especifica o nome amigável do algoritmo que a classe de criptografia implementa.</span><span class="sxs-lookup"><span data-stu-id="bc9f1-112">Specifies the friendly name of the algorithm that the cryptography class implements.</span></span>|  
|<span data-ttu-id="bc9f1-113">**class**</span><span class="sxs-lookup"><span data-stu-id="bc9f1-113">**class**</span></span>|<span data-ttu-id="bc9f1-114">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="bc9f1-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="bc9f1-115">Especifica o valor do atributo **Name** no [\<cryptoClass>](cryptoclass-element.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="bc9f1-115">Specifies the value for the **name** attribute in the [\<cryptoClass>](cryptoclass-element.md) element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bc9f1-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="bc9f1-116">Child Elements</span></span>  

 <span data-ttu-id="bc9f1-117">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="bc9f1-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bc9f1-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="bc9f1-118">Parent Elements</span></span>  
  
|<span data-ttu-id="bc9f1-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="bc9f1-119">Element</span></span>|<span data-ttu-id="bc9f1-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="bc9f1-120">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="bc9f1-121">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="bc9f1-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.web`|<span data-ttu-id="bc9f1-122">Especifica o elemento raiz para a seção de configuração ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="bc9f1-122">Specifies the root element for the ASP.NET configuration section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bc9f1-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="bc9f1-123">Remarks</span></span>  

 <span data-ttu-id="bc9f1-124">O atributo **Name** pode ser o nome de uma das classes abstratas encontradas no <xref:System.Security.Cryptography> namespace.</span><span class="sxs-lookup"><span data-stu-id="bc9f1-124">The **name** attribute can be the name of one of the abstract classes found in the <xref:System.Security.Cryptography> namespace.</span></span> <span data-ttu-id="bc9f1-125">Quando você chama o método **Create** em uma classe de criptografia abstrata, o nome da classe abstrata é passado para o <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A> método.</span><span class="sxs-lookup"><span data-stu-id="bc9f1-125">When you call the **Create** method on an abstract cryptography class, the abstract class name is passed to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A> method.</span></span> <span data-ttu-id="bc9f1-126">**CreateFromName** retorna uma instância do tipo indicado pelo atributo de **classe** .</span><span class="sxs-lookup"><span data-stu-id="bc9f1-126">**CreateFromName** returns an instance of the type indicated by the **class** attribute.</span></span> <span data-ttu-id="bc9f1-127">Se o atributo **Name** for um nome curto, como RSA, você poderá usar esse nome ao chamar o método **CreateFromName** .</span><span class="sxs-lookup"><span data-stu-id="bc9f1-127">If the **name** attribute is a short name, such as RSA, you can use that name when calling the **CreateFromName** method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bc9f1-128">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bc9f1-128">Example</span></span>  

 <span data-ttu-id="bc9f1-129">O exemplo a seguir mostra como usar o **\<nameEntry>** elemento para fazer referência a uma classe de criptografia e configurar o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="bc9f1-129">The following example shows how to use the **\<nameEntry>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="bc9f1-130">Em seguida, você pode passar a cadeia de caracteres "RSA" para o <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> método e usar o <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> método para retornar um `MyCryptoRSAClass` objeto.</span><span class="sxs-lookup"><span data-stu-id="bc9f1-130">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="bc9f1-131">Veja também</span><span class="sxs-lookup"><span data-stu-id="bc9f1-131">See also</span></span>

- [<span data-ttu-id="bc9f1-132">Esquema do arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="bc9f1-132">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="bc9f1-133">Esquema de configurações de criptografia</span><span class="sxs-lookup"><span data-stu-id="bc9f1-133">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="bc9f1-134">Serviços criptográficos</span><span class="sxs-lookup"><span data-stu-id="bc9f1-134">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="bc9f1-135">Configurando classes de criptografia</span><span class="sxs-lookup"><span data-stu-id="bc9f1-135">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
