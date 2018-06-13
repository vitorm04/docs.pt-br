---
title: '&lt;enforceFIPSPolicy&gt; elemento'
ms.date: 03/30/2017
helpviewer_keywords:
- enforceFIPSPolicy element
- FIPS
- <enforceFIPSPolicy> element
- Federal Information Processing Standards (FIPS)
ms.assetid: c35509c4-35cf-43c0-bb47-75e4208aa24e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9040bf2548964cf6df5f4fd87ee9f6d979c7df1e
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32746209"
---
# <a name="ltenforcefipspolicygt-element"></a><span data-ttu-id="fb779-102">&lt;enforceFIPSPolicy&gt; elemento</span><span class="sxs-lookup"><span data-stu-id="fb779-102">&lt;enforceFIPSPolicy&gt; Element</span></span>
<span data-ttu-id="fb779-103">Especifica se deve-se impor um requisito de configuração do computador em que os algoritmos de criptografia devem estar em conformidade com o FIPS (padrão norte-americano de processamento de informações).</span><span class="sxs-lookup"><span data-stu-id="fb779-103">Specifies whether to enforce a computer configuration requirement that cryptographic algorithms must comply with the Federal Information Processing Standards (FIPS).</span></span>  
  
 <span data-ttu-id="fb779-104">\<Configuração > elemento</span><span class="sxs-lookup"><span data-stu-id="fb779-104">\<configuration> Element</span></span>  
<span data-ttu-id="fb779-105">\<tempo de execução > elemento</span><span class="sxs-lookup"><span data-stu-id="fb779-105">\<runtime> Element</span></span>  
<span data-ttu-id="fb779-106">\<enforceFIPSPolicy > elemento</span><span class="sxs-lookup"><span data-stu-id="fb779-106">\<enforceFIPSPolicy> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb779-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fb779-107">Syntax</span></span>  
  
```xml  
<enforceFIPSPolicy enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fb779-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="fb779-108">Attributes and Elements</span></span>  
 <span data-ttu-id="fb779-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="fb779-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fb779-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="fb779-110">Attributes</span></span>  
  
|<span data-ttu-id="fb779-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="fb779-111">Attribute</span></span>|<span data-ttu-id="fb779-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="fb779-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fb779-113">habilitado</span><span class="sxs-lookup"><span data-stu-id="fb779-113">enabled</span></span>|<span data-ttu-id="fb779-114">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="fb779-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="fb779-115">Especifica se deseja habilitar a aplicação de um requisito de configuração do computador que os algoritmos de criptografia devem ser compatíveis com FIPS.</span><span class="sxs-lookup"><span data-stu-id="fb779-115">Specifies whether to enable the enforcement of a computer configuration requirement that cryptographic algorithms must be compliant with FIPS.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="fb779-116">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="fb779-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="fb779-117">Valor</span><span class="sxs-lookup"><span data-stu-id="fb779-117">Value</span></span>|<span data-ttu-id="fb779-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="fb779-118">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="fb779-119">Se o computador está configurado para exigir que os algoritmos de criptografia para ser compatível com FIPS, esse requisito é imposto.</span><span class="sxs-lookup"><span data-stu-id="fb779-119">If your computer is configured to require cryptographic algorithms to be FIPS compliant, that requirement is enforced.</span></span> <span data-ttu-id="fb779-120">Se uma classe implementa um algoritmo que não é compatível com FIPS, construtores ou `Create` métodos para essa classe lançam exceções quando eles são executados no computador.</span><span class="sxs-lookup"><span data-stu-id="fb779-120">If a class implements an algorithm that is not compliant with FIPS, the constructors or `Create` methods for that class throw exceptions when they are run on that computer.</span></span> <span data-ttu-id="fb779-121">Esse é o padrão.</span><span class="sxs-lookup"><span data-stu-id="fb779-121">This is the default.</span></span>|  
|`false`|<span data-ttu-id="fb779-122">Algoritmos de criptografia que são usados pelo aplicativo não são necessários para serem compatíveis com FIPS, independentemente da configuração do computador.</span><span class="sxs-lookup"><span data-stu-id="fb779-122">Cryptographic algorithms that are used by the application are not required to be compliant with FIPS, regardless of computer configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fb779-123">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="fb779-123">Child Elements</span></span>  
 <span data-ttu-id="fb779-124">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="fb779-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fb779-125">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="fb779-125">Parent Elements</span></span>  
  
|<span data-ttu-id="fb779-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="fb779-126">Element</span></span>|<span data-ttu-id="fb779-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="fb779-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="fb779-128">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="fb779-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="fb779-129">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="fb779-129">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fb779-130">Comentários</span><span class="sxs-lookup"><span data-stu-id="fb779-130">Remarks</span></span>  
 <span data-ttu-id="fb779-131">Começando com o .NET Framework 2.0, a criação de classes que implementam algoritmos de criptografia é controlada pela configuração do computador.</span><span class="sxs-lookup"><span data-stu-id="fb779-131">Starting with the .NET Framework 2.0, the creation of classes that implement cryptographic algorithms is controlled by the configuration of the computer.</span></span> <span data-ttu-id="fb779-132">Se o computador está configurado para exigir algoritmos compatíveis com FIPS, e uma classe implementa um algoritmo que não é compatível com FIPS, qualquer tentativa de criar uma instância dessa classe gera uma exceção.</span><span class="sxs-lookup"><span data-stu-id="fb779-132">If the computer is configured to require algorithms to be compliant with FIPS, and a class implements an algorithm that is not compliant with FIPS, any attempt to create an instance of that class throws an exception.</span></span> <span data-ttu-id="fb779-133">Construtores lançar um <xref:System.InvalidOperationException> exceção, e `Create` métodos lançam uma <xref:System.Reflection.TargetInvocationException> exceção com uma interna <xref:System.InvalidOperationException> exceção.</span><span class="sxs-lookup"><span data-stu-id="fb779-133">Constructors throw an <xref:System.InvalidOperationException> exception, and `Create` methods throw a <xref:System.Reflection.TargetInvocationException> exception with an inner <xref:System.InvalidOperationException> exception.</span></span>  
  
 <span data-ttu-id="fb779-134">Se seu aplicativo é executado nos computadores cujas configurações requerem a conformidade com FIPS, e seu aplicativo usa um algoritmo que não é compatível com FIPS, você pode usar esse elemento no arquivo de configuração para impedir que o common language runtime (CLR) do imposição de conformidade FIPS.</span><span class="sxs-lookup"><span data-stu-id="fb779-134">If your application runs on computers whose configurations require compliance with FIPS, and your application uses an algorithm that is not compliant with FIPS, you can use this element in your configuration file to prevent the common language runtime (CLR) from enforcing FIPS compliance.</span></span> <span data-ttu-id="fb779-135">Esse elemento foi introduzido no [!INCLUDE[net_v20SP1_long](../../../../../includes/net-v20sp1-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="fb779-135">This element was introduced in the [!INCLUDE[net_v20SP1_long](../../../../../includes/net-v20sp1-long-md.md)].</span></span>  
  
## <a name="example"></a><span data-ttu-id="fb779-136">Exemplo</span><span class="sxs-lookup"><span data-stu-id="fb779-136">Example</span></span>  
 <span data-ttu-id="fb779-137">O exemplo a seguir mostra como impedir que o CLR imposição de conformidade FIPS.</span><span class="sxs-lookup"><span data-stu-id="fb779-137">The following example shows how to prevent the CLR from enforcing FIPS compliance.</span></span>  
  
```xml  
<configuration>  
    <runtime>  
        <enforceFIPSPolicy enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="fb779-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fb779-138">See Also</span></span>  
 [<span data-ttu-id="fb779-139">Esquema de configurações do tempo de execução</span><span class="sxs-lookup"><span data-stu-id="fb779-139">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="fb779-140">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="fb779-140">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="fb779-141">Modelo de criptografia</span><span class="sxs-lookup"><span data-stu-id="fb779-141">Cryptography Model</span></span>](../../../../../docs/standard/security/cryptography-model.md)
