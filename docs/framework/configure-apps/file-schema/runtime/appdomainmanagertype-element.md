---
title: Elemento <appDomainManagerType>
ms.date: 03/30/2017
helpviewer_keywords:
- appDomainManagerType element
- <appDomainManagerType> element
ms.assetid: ae8d5a7e-e7f7-47f7-98d9-455cc243a322
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5b535ba67ab05dabd7e0a23e79692bbf69e25b55
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663918"
---
# <a name="appdomainmanagertype-element"></a><span data-ttu-id="e3e55-102">\<Elemento de > appDomainManagerType</span><span class="sxs-lookup"><span data-stu-id="e3e55-102">\<appDomainManagerType> Element</span></span>
<span data-ttu-id="e3e55-103">Especifica o tipo que serve como o gerenciador de domínio do aplicativo para o domínio do aplicativo padrão.</span><span class="sxs-lookup"><span data-stu-id="e3e55-103">Specifies the type that serves as the application domain manager for the default application domain.</span></span>  
  
 <span data-ttu-id="e3e55-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="e3e55-104">\<configuration></span></span>  
<span data-ttu-id="e3e55-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="e3e55-105">\<runtime></span></span>  
<span data-ttu-id="e3e55-106">\<appDomainManagerType></span><span class="sxs-lookup"><span data-stu-id="e3e55-106">\<appDomainManagerType></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3e55-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e3e55-107">Syntax</span></span>  
  
```xml  
<appDomainManagerAssembly   
   value="type name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e3e55-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="e3e55-108">Attributes and Elements</span></span>  
 <span data-ttu-id="e3e55-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="e3e55-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e3e55-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="e3e55-110">Attributes</span></span>  
  
|<span data-ttu-id="e3e55-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="e3e55-111">Attribute</span></span>|<span data-ttu-id="e3e55-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="e3e55-112">Description</span></span>|  
|---------------|-----------------|  
|`value`|<span data-ttu-id="e3e55-113">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="e3e55-113">Required attribute.</span></span> <span data-ttu-id="e3e55-114">Especifica o nome do tipo, incluindo o namespace, que serve como o Gerenciador de domínio do aplicativo para o domínio de aplicativo padrão no processo.</span><span class="sxs-lookup"><span data-stu-id="e3e55-114">Specifies the name of the type, including the namespace, that serves as the application domain manager for the default application domain in the process.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e3e55-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="e3e55-115">Child Elements</span></span>  
 <span data-ttu-id="e3e55-116">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="e3e55-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e3e55-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="e3e55-117">Parent Elements</span></span>  
  
|<span data-ttu-id="e3e55-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="e3e55-118">Element</span></span>|<span data-ttu-id="e3e55-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="e3e55-119">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="e3e55-120">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e3e55-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="e3e55-121">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="e3e55-121">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e3e55-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="e3e55-122">Remarks</span></span>  
 <span data-ttu-id="e3e55-123">Para especificar o tipo de Gerenciador de domínio do aplicativo, você deve especificar esse elemento e o elemento de [ \<> appDomainManagerAssembly](appdomainmanagerassembly-element.md) .</span><span class="sxs-lookup"><span data-stu-id="e3e55-123">To specify the type of the application domain manager, you must specify both this element and the [\<appDomainManagerAssembly>](appdomainmanagerassembly-element.md) element.</span></span> <span data-ttu-id="e3e55-124">Se um desses elementos não for especificado, o outro será ignorado.</span><span class="sxs-lookup"><span data-stu-id="e3e55-124">If either of these elements is not specified, the other is ignored.</span></span>  
  
 <span data-ttu-id="e3e55-125">Quando o domínio de aplicativo padrão for carregado <xref:System.TypeLoadException> , será gerado se o tipo especificado não existir no assembly especificado pelo elemento de [ \<> appDomainManagerAssembly](appdomainmanagerassembly-element.md) ; e o processo não for iniciado.</span><span class="sxs-lookup"><span data-stu-id="e3e55-125">When the default application domain is loaded, <xref:System.TypeLoadException> is thrown if the specified type does not exist in the assembly that is specified by the [\<appDomainManagerAssembly>](appdomainmanagerassembly-element.md) element; and the process fails to start.</span></span>  
  
 <span data-ttu-id="e3e55-126">Quando você especifica o tipo de Gerenciador de domínio do aplicativo para o domínio de aplicativo padrão, outros domínios de aplicativo criados a partir do domínio de aplicativo padrão herdam o tipo de Gerenciador de domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e3e55-126">When you specify the application domain manager type for the default application domain, other application domains created from the default application domain inherit the application domain manager type.</span></span> <span data-ttu-id="e3e55-127">Use as <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> propriedades <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> e para especificar um tipo de Gerenciador de domínio de aplicativo diferente para um novo domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e3e55-127">Use the <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> and <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> properties to specify a different application domain manager type for a new application domain.</span></span>  
  
 <span data-ttu-id="e3e55-128">A especificação do tipo de Gerenciador de domínio do aplicativo exige que o aplicativo tenha confiança total.</span><span class="sxs-lookup"><span data-stu-id="e3e55-128">Specifying the application domain manager type requires the application to have full trust.</span></span> <span data-ttu-id="e3e55-129">(Por exemplo, um aplicativo em execução na área de trabalho tem confiança total.) Se o aplicativo não tiver confiança total, um <xref:System.TypeLoadException> será lançado.</span><span class="sxs-lookup"><span data-stu-id="e3e55-129">(For example, an application running on the desktop has full trust.) If the application does not have full trust, a <xref:System.TypeLoadException> is thrown.</span></span>  
  
 <span data-ttu-id="e3e55-130">O formato do tipo e do namespace é o mesmo formato usado para a <xref:System.Type.FullName%2A?displayProperty=nameWithType> propriedade.</span><span class="sxs-lookup"><span data-stu-id="e3e55-130">The format of the type and namespace is the same format that is used for the <xref:System.Type.FullName%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="e3e55-131">Este elemento de configuração está disponível apenas no .NET Framework 4 e posterior.</span><span class="sxs-lookup"><span data-stu-id="e3e55-131">This configuration element is available only in the .NET Framework 4 and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e3e55-132">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e3e55-132">Example</span></span>  
 <span data-ttu-id="e3e55-133">O exemplo a seguir mostra como especificar que o Gerenciador de domínio do aplicativo para o domínio de aplicativo padrão de um `MyMgr` processo é o `AdMgrExample` tipo no assembly.</span><span class="sxs-lookup"><span data-stu-id="e3e55-133">The following example shows how to specify that the application domain manager for the default application domain of a process is the `MyMgr` type in the `AdMgrExample` assembly.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainManagerType value="MyMgr" />  
      <appDomainManagerAssembly   
         value="AdMgrExample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6856bccf150f00b3" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e3e55-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e3e55-134">See also</span></span>

- <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType>
- <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType>
- [<span data-ttu-id="e3e55-135">\<Elemento de > appDomainManagerAssembly</span><span class="sxs-lookup"><span data-stu-id="e3e55-135">\<appDomainManagerAssembly> Element</span></span>](appdomainmanagerassembly-element.md)
- [<span data-ttu-id="e3e55-136">Esquema de configurações do tempo de execução</span><span class="sxs-lookup"><span data-stu-id="e3e55-136">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="e3e55-137">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="e3e55-137">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="e3e55-138">Método SetAppDomainManagerType</span><span class="sxs-lookup"><span data-stu-id="e3e55-138">SetAppDomainManagerType Method</span></span>](../../../unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)
