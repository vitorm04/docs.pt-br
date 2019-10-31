---
title: Elemento <enforceFIPSPolicy>
ms.date: 03/30/2017
helpviewer_keywords:
- enforceFIPSPolicy element
- FIPS
- <enforceFIPSPolicy> element
- Federal Information Processing Standards (FIPS)
ms.assetid: c35509c4-35cf-43c0-bb47-75e4208aa24e
ms.openlocfilehash: 0d6dd291a24928487a040c0427f058dee80bf836
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73117382"
---
# <a name="enforcefipspolicy-element"></a><span data-ttu-id="53bd9-102">\<elemento de > enforceFIPSPolicy</span><span class="sxs-lookup"><span data-stu-id="53bd9-102">\<enforceFIPSPolicy> Element</span></span>
<span data-ttu-id="53bd9-103">Especifica se deve-se impor um requisito de configuração do computador em que os algoritmos de criptografia devem estar em conformidade com o FIPS (padrão norte-americano de processamento de informações).</span><span class="sxs-lookup"><span data-stu-id="53bd9-103">Specifies whether to enforce a computer configuration requirement that cryptographic algorithms must comply with the Federal Information Processing Standards (FIPS).</span></span>  
  
<span data-ttu-id="53bd9-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="53bd9-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="53bd9-105">&nbsp; &nbsp;[ **\<runtime >** ](runtime-element.md) </span><span class="sxs-lookup"><span data-stu-id="53bd9-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="53bd9-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<enforceFIPSPolicy >**</span><span class="sxs-lookup"><span data-stu-id="53bd9-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<enforceFIPSPolicy>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53bd9-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="53bd9-107">Syntax</span></span>  
  
```xml  
<enforceFIPSPolicy enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="53bd9-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="53bd9-108">Attributes and Elements</span></span>  
 <span data-ttu-id="53bd9-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="53bd9-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="53bd9-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="53bd9-110">Attributes</span></span>  
  
|<span data-ttu-id="53bd9-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="53bd9-111">Attribute</span></span>|<span data-ttu-id="53bd9-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="53bd9-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="53bd9-113">habilitado</span><span class="sxs-lookup"><span data-stu-id="53bd9-113">enabled</span></span>|<span data-ttu-id="53bd9-114">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="53bd9-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="53bd9-115">Especifica se é necessário habilitar a imposição de um requisito de configuração de computador que os algoritmos criptográficos devem ser compatíveis com o FIPS.</span><span class="sxs-lookup"><span data-stu-id="53bd9-115">Specifies whether to enable the enforcement of a computer configuration requirement that cryptographic algorithms must be compliant with FIPS.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="53bd9-116">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="53bd9-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="53bd9-117">Valor</span><span class="sxs-lookup"><span data-stu-id="53bd9-117">Value</span></span>|<span data-ttu-id="53bd9-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="53bd9-118">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="53bd9-119">Se o computador estiver configurado para exigir que os algoritmos criptográficos sejam compatíveis com FIPS, esse requisito será imposto.</span><span class="sxs-lookup"><span data-stu-id="53bd9-119">If your computer is configured to require cryptographic algorithms to be FIPS compliant, that requirement is enforced.</span></span> <span data-ttu-id="53bd9-120">Se uma classe implementa um algoritmo que não está em conformidade com o FIPS, os construtores ou os métodos de `Create` para essa classe geram exceções quando são executados nesse computador.</span><span class="sxs-lookup"><span data-stu-id="53bd9-120">If a class implements an algorithm that is not compliant with FIPS, the constructors or `Create` methods for that class throw exceptions when they are run on that computer.</span></span> <span data-ttu-id="53bd9-121">Esse é o padrão.</span><span class="sxs-lookup"><span data-stu-id="53bd9-121">This is the default.</span></span>|  
|`false`|<span data-ttu-id="53bd9-122">Os algoritmos de criptografia usados pelo aplicativo não precisam ser compatíveis com o FIPS, independentemente da configuração do computador.</span><span class="sxs-lookup"><span data-stu-id="53bd9-122">Cryptographic algorithms that are used by the application are not required to be compliant with FIPS, regardless of computer configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="53bd9-123">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="53bd9-123">Child Elements</span></span>  
 <span data-ttu-id="53bd9-124">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="53bd9-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="53bd9-125">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="53bd9-125">Parent Elements</span></span>  
  
|<span data-ttu-id="53bd9-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="53bd9-126">Element</span></span>|<span data-ttu-id="53bd9-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="53bd9-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="53bd9-128">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="53bd9-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="53bd9-129">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="53bd9-129">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="53bd9-130">Comentários</span><span class="sxs-lookup"><span data-stu-id="53bd9-130">Remarks</span></span>  
 <span data-ttu-id="53bd9-131">A partir do .NET Framework 2,0, a criação de classes que implementam algoritmos de criptografia é controlada pela configuração do computador.</span><span class="sxs-lookup"><span data-stu-id="53bd9-131">Starting with the .NET Framework 2.0, the creation of classes that implement cryptographic algorithms is controlled by the configuration of the computer.</span></span> <span data-ttu-id="53bd9-132">Se o computador estiver configurado para exigir que os algoritmos sejam compatíveis com o FIPS e uma classe implementar um algoritmo que não seja compatível com o FIPS, qualquer tentativa de criar uma instância dessa classe gerará uma exceção.</span><span class="sxs-lookup"><span data-stu-id="53bd9-132">If the computer is configured to require algorithms to be compliant with FIPS, and a class implements an algorithm that is not compliant with FIPS, any attempt to create an instance of that class throws an exception.</span></span> <span data-ttu-id="53bd9-133">Os construtores lançam uma exceção de <xref:System.InvalidOperationException> e `Create` métodos lançam uma exceção <xref:System.Reflection.TargetInvocationException> com uma exceção de <xref:System.InvalidOperationException> interna.</span><span class="sxs-lookup"><span data-stu-id="53bd9-133">Constructors throw an <xref:System.InvalidOperationException> exception, and `Create` methods throw a <xref:System.Reflection.TargetInvocationException> exception with an inner <xref:System.InvalidOperationException> exception.</span></span>  
  
 <span data-ttu-id="53bd9-134">Se seu aplicativo for executado em computadores cujas configurações exigem conformidade com o FIPS e seu aplicativo usa um algoritmo que não é compatível com o FIPS, você pode usar esse elemento em seu arquivo de configuração para impedir que o Common Language Runtime (CLR) imposição de conformidade com FIPS.</span><span class="sxs-lookup"><span data-stu-id="53bd9-134">If your application runs on computers whose configurations require compliance with FIPS, and your application uses an algorithm that is not compliant with FIPS, you can use this element in your configuration file to prevent the common language runtime (CLR) from enforcing FIPS compliance.</span></span> <span data-ttu-id="53bd9-135">Esse elemento foi introduzido no .NET Framework 2,0 Service Pack 1.</span><span class="sxs-lookup"><span data-stu-id="53bd9-135">This element was introduced in the .NET Framework 2.0 Service Pack 1.</span></span>  
  
## <a name="example"></a><span data-ttu-id="53bd9-136">Exemplo</span><span class="sxs-lookup"><span data-stu-id="53bd9-136">Example</span></span>  
 <span data-ttu-id="53bd9-137">O exemplo a seguir mostra como impedir que o CLR imponha a conformidade com o FIPS.</span><span class="sxs-lookup"><span data-stu-id="53bd9-137">The following example shows how to prevent the CLR from enforcing FIPS compliance.</span></span>  
  
```xml  
<configuration>  
    <runtime>  
        <enforceFIPSPolicy enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="53bd9-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="53bd9-138">See also</span></span>

- [<span data-ttu-id="53bd9-139">Esquema de configurações do tempo de execução</span><span class="sxs-lookup"><span data-stu-id="53bd9-139">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="53bd9-140">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="53bd9-140">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="53bd9-141">Modelo de criptografia</span><span class="sxs-lookup"><span data-stu-id="53bd9-141">Cryptography Model</span></span>](../../../../standard/security/cryptography-model.md)
