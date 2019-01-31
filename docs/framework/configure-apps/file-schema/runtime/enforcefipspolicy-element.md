---
title: Elemento <enforceFIPSPolicy>
ms.date: 03/30/2017
helpviewer_keywords:
- enforceFIPSPolicy element
- FIPS
- <enforceFIPSPolicy> element
- Federal Information Processing Standards (FIPS)
ms.assetid: c35509c4-35cf-43c0-bb47-75e4208aa24e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1a4e5ba5ac1a5a3c08c351531efc84291925ba4b
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55267463"
---
# <a name="enforcefipspolicy-element"></a><span data-ttu-id="dab7e-102">\<enforceFIPSPolicy > elemento</span><span class="sxs-lookup"><span data-stu-id="dab7e-102">\<enforceFIPSPolicy> Element</span></span>
<span data-ttu-id="dab7e-103">Especifica se deve-se impor um requisito de configuração do computador em que os algoritmos de criptografia devem estar em conformidade com o FIPS (padrão norte-americano de processamento de informações).</span><span class="sxs-lookup"><span data-stu-id="dab7e-103">Specifies whether to enforce a computer configuration requirement that cryptographic algorithms must comply with the Federal Information Processing Standards (FIPS).</span></span>  
  
 <span data-ttu-id="dab7e-104">\<Configuração > elemento</span><span class="sxs-lookup"><span data-stu-id="dab7e-104">\<configuration> Element</span></span>  
<span data-ttu-id="dab7e-105">\<tempo de execução > elemento</span><span class="sxs-lookup"><span data-stu-id="dab7e-105">\<runtime> Element</span></span>  
<span data-ttu-id="dab7e-106">\<enforceFIPSPolicy > elemento</span><span class="sxs-lookup"><span data-stu-id="dab7e-106">\<enforceFIPSPolicy> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dab7e-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="dab7e-107">Syntax</span></span>  
  
```xml  
<enforceFIPSPolicy enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dab7e-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="dab7e-108">Attributes and Elements</span></span>  
 <span data-ttu-id="dab7e-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="dab7e-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dab7e-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="dab7e-110">Attributes</span></span>  
  
|<span data-ttu-id="dab7e-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="dab7e-111">Attribute</span></span>|<span data-ttu-id="dab7e-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="dab7e-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="dab7e-113">habilitado</span><span class="sxs-lookup"><span data-stu-id="dab7e-113">enabled</span></span>|<span data-ttu-id="dab7e-114">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="dab7e-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="dab7e-115">Especifica se deseja habilitar a imposição de um requisito de configuração do computador que os algoritmos de criptografia devem ser compatíveis com FIPS.</span><span class="sxs-lookup"><span data-stu-id="dab7e-115">Specifies whether to enable the enforcement of a computer configuration requirement that cryptographic algorithms must be compliant with FIPS.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="dab7e-116">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="dab7e-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="dab7e-117">Valor</span><span class="sxs-lookup"><span data-stu-id="dab7e-117">Value</span></span>|<span data-ttu-id="dab7e-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="dab7e-118">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="dab7e-119">Se o computador está configurado para exigir que os algoritmos de criptografia seja compatível com FIPS, esse requisito é imposto.</span><span class="sxs-lookup"><span data-stu-id="dab7e-119">If your computer is configured to require cryptographic algorithms to be FIPS compliant, that requirement is enforced.</span></span> <span data-ttu-id="dab7e-120">Se uma classe implementa um algoritmo que não está em conformidade com FIPS, os construtores ou `Create` métodos dessa classe lançam exceções quando eles são executados no computador em questão.</span><span class="sxs-lookup"><span data-stu-id="dab7e-120">If a class implements an algorithm that is not compliant with FIPS, the constructors or `Create` methods for that class throw exceptions when they are run on that computer.</span></span> <span data-ttu-id="dab7e-121">Esse é o padrão.</span><span class="sxs-lookup"><span data-stu-id="dab7e-121">This is the default.</span></span>|  
|`false`|<span data-ttu-id="dab7e-122">Algoritmos de criptografia que são usados pelo aplicativo não são necessários para estar em conformidade com FIPS, independentemente da configuração do computador.</span><span class="sxs-lookup"><span data-stu-id="dab7e-122">Cryptographic algorithms that are used by the application are not required to be compliant with FIPS, regardless of computer configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dab7e-123">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="dab7e-123">Child Elements</span></span>  
 <span data-ttu-id="dab7e-124">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="dab7e-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="dab7e-125">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="dab7e-125">Parent Elements</span></span>  
  
|<span data-ttu-id="dab7e-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="dab7e-126">Element</span></span>|<span data-ttu-id="dab7e-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="dab7e-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="dab7e-128">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="dab7e-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="dab7e-129">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="dab7e-129">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dab7e-130">Comentários</span><span class="sxs-lookup"><span data-stu-id="dab7e-130">Remarks</span></span>  
 <span data-ttu-id="dab7e-131">Começando com o .NET Framework 2.0, a criação de classes que implementam algoritmos de criptografia é controlada pela configuração do computador.</span><span class="sxs-lookup"><span data-stu-id="dab7e-131">Starting with the .NET Framework 2.0, the creation of classes that implement cryptographic algorithms is controlled by the configuration of the computer.</span></span> <span data-ttu-id="dab7e-132">Se o computador está configurado para exigir que os algoritmos em conformidade com FIPS, e uma classe implementa um algoritmo que não está em conformidade com FIPS, qualquer tentativa de criar uma instância dessa classe gera uma exceção.</span><span class="sxs-lookup"><span data-stu-id="dab7e-132">If the computer is configured to require algorithms to be compliant with FIPS, and a class implements an algorithm that is not compliant with FIPS, any attempt to create an instance of that class throws an exception.</span></span> <span data-ttu-id="dab7e-133">Construtores lançar uma <xref:System.InvalidOperationException> exceção, e `Create` métodos geram uma <xref:System.Reflection.TargetInvocationException> exceção com uma interna <xref:System.InvalidOperationException> exceção.</span><span class="sxs-lookup"><span data-stu-id="dab7e-133">Constructors throw an <xref:System.InvalidOperationException> exception, and `Create` methods throw a <xref:System.Reflection.TargetInvocationException> exception with an inner <xref:System.InvalidOperationException> exception.</span></span>  
  
 <span data-ttu-id="dab7e-134">Se seu aplicativo é executado em computadores cujas configurações exigem a conformidade com FIPS, e seu aplicativo usa um algoritmo que não está em conformidade com FIPS, você pode usar esse elemento no arquivo de configuração para impedir que o common language runtime (CLR) do impor a conformidade com FIPS.</span><span class="sxs-lookup"><span data-stu-id="dab7e-134">If your application runs on computers whose configurations require compliance with FIPS, and your application uses an algorithm that is not compliant with FIPS, you can use this element in your configuration file to prevent the common language runtime (CLR) from enforcing FIPS compliance.</span></span> <span data-ttu-id="dab7e-135">Esse elemento foi introduzido no [!INCLUDE[net_v20SP1_long](../../../../../includes/net-v20sp1-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="dab7e-135">This element was introduced in the [!INCLUDE[net_v20SP1_long](../../../../../includes/net-v20sp1-long-md.md)].</span></span>  
  
## <a name="example"></a><span data-ttu-id="dab7e-136">Exemplo</span><span class="sxs-lookup"><span data-stu-id="dab7e-136">Example</span></span>  
 <span data-ttu-id="dab7e-137">O exemplo a seguir mostra como evitar que o CLR de impor a conformidade FIPS.</span><span class="sxs-lookup"><span data-stu-id="dab7e-137">The following example shows how to prevent the CLR from enforcing FIPS compliance.</span></span>  
  
```xml  
<configuration>  
    <runtime>  
        <enforceFIPSPolicy enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="dab7e-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dab7e-138">See also</span></span>
- [<span data-ttu-id="dab7e-139">Esquema de configurações do tempo de execução</span><span class="sxs-lookup"><span data-stu-id="dab7e-139">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="dab7e-140">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="dab7e-140">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="dab7e-141">Modelo de criptografia</span><span class="sxs-lookup"><span data-stu-id="dab7e-141">Cryptography Model</span></span>](../../../../../docs/standard/security/cryptography-model.md)
