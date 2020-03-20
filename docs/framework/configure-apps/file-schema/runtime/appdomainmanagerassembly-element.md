---
title: Elemento <appDomainManagerAssembly>
ms.date: 03/30/2017
helpviewer_keywords:
- <appDomainManagerAssembly> element
- appDomainManagerAssembly element
ms.assetid: c7c56e39-a700-44f5-b94e-411bfce339d9
ms.openlocfilehash: 4c4ea35bff17a0e5188f26884e93cf77173a7df8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154415"
---
# <a name="appdomainmanagerassembly-element"></a><span data-ttu-id="a8c49-102">\<appDomainManagerO> Elemento</span><span class="sxs-lookup"><span data-stu-id="a8c49-102">\<appDomainManagerAssembly> Element</span></span>
<span data-ttu-id="a8c49-103">Especifica o assembly que fornece o gerenciador do domínio do aplicativo para o domínio do aplicativo padrão no processo.</span><span class="sxs-lookup"><span data-stu-id="a8c49-103">Specifies the assembly that provides the application domain manager for the default application domain in the process.</span></span>  
  
<span data-ttu-id="a8c49-104">[**\<>de configuração**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="a8c49-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="a8c49-105">&nbsp;&nbsp;[**\<>de tempo de execução**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="a8c49-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="a8c49-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<appDomainManager>**</span><span class="sxs-lookup"><span data-stu-id="a8c49-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<appDomainManagerAssembly>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8c49-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a8c49-107">Syntax</span></span>  
  
```xml  
<appDomainManagerAssembly
   value="assembly display name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a8c49-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="a8c49-108">Attributes and Elements</span></span>  
 <span data-ttu-id="a8c49-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="a8c49-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a8c49-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="a8c49-110">Attributes</span></span>  
  
|<span data-ttu-id="a8c49-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="a8c49-111">Attribute</span></span>|<span data-ttu-id="a8c49-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="a8c49-112">Description</span></span>|  
|---------------|-----------------|  
|`value`|<span data-ttu-id="a8c49-113">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="a8c49-113">Required attribute.</span></span> <span data-ttu-id="a8c49-114">Especifica o nome de exibição do conjunto que fornece o gerenciador de domínio do aplicativo para o domínio de aplicativo padrão no processo.</span><span class="sxs-lookup"><span data-stu-id="a8c49-114">Specifies the display name of the assembly that provides the application domain manager for the default application domain in the process.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a8c49-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="a8c49-115">Child Elements</span></span>  
 <span data-ttu-id="a8c49-116">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="a8c49-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a8c49-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="a8c49-117">Parent Elements</span></span>  
  
|<span data-ttu-id="a8c49-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="a8c49-118">Element</span></span>|<span data-ttu-id="a8c49-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="a8c49-119">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="a8c49-120">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a8c49-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="a8c49-121">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="a8c49-121">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a8c49-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="a8c49-122">Remarks</span></span>  
 <span data-ttu-id="a8c49-123">Para especificar o tipo do gerenciador de domínio do aplicativo, você deve especificar esse elemento e o [ \<elemento>do appDomainManagerType.](appdomainmanagertype-element.md)</span><span class="sxs-lookup"><span data-stu-id="a8c49-123">To specify the type of the application domain manager, you must specify both this element and the [\<appDomainManagerType>](appdomainmanagertype-element.md) element.</span></span> <span data-ttu-id="a8c49-124">Se um desses elementos não for especificado, o outro será ignorado.</span><span class="sxs-lookup"><span data-stu-id="a8c49-124">If either of these elements is not specified, the other is ignored.</span></span>  
  
 <span data-ttu-id="a8c49-125">Quando o domínio de aplicativo <xref:System.TypeLoadException> padrão é carregado, é jogado se o conjunto especificado não existir ou se o conjunto não contiver o tipo especificado pelo [ \<elemento appDomainManagerType>;](appdomainmanagertype-element.md) e o processo não começa.</span><span class="sxs-lookup"><span data-stu-id="a8c49-125">When the default application domain is loaded, <xref:System.TypeLoadException> is thrown if the specified assembly does not exist or if the assembly does not contain the type specified by the [\<appDomainManagerType>](appdomainmanagertype-element.md) element; and the process fails to start.</span></span> <span data-ttu-id="a8c49-126">Se o conjunto for encontrado, mas as <xref:System.IO.FileLoadException> informações da versão não coincidirem, um será lançado.</span><span class="sxs-lookup"><span data-stu-id="a8c49-126">If the assembly is found but the version information does not match, a <xref:System.IO.FileLoadException> is thrown.</span></span>  
  
 <span data-ttu-id="a8c49-127">Quando você especifica o tipo de gerenciador de domínio de aplicativo para o domínio de aplicativo padrão, outros domínios de aplicativo criados a partir do domínio do aplicativo padrão herdam o tipo de gerenciador de domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a8c49-127">When you specify the application domain manager type for the default application domain, other application domains created from the default application domain inherit the application domain manager type.</span></span> <span data-ttu-id="a8c49-128">Use <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> as <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> propriedades e as propriedades para especificar um tipo diferente de gerenciador de domínio de aplicativo para um novo domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a8c49-128">Use the <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> and <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> properties to specify a different application domain manager type for a new application domain.</span></span>  
  
 <span data-ttu-id="a8c49-129">Especificar o tipo de gerenciador de domínio do aplicativo requer que o aplicativo tenha total confiança.</span><span class="sxs-lookup"><span data-stu-id="a8c49-129">Specifying the application domain manager type requires the application to have full trust.</span></span> <span data-ttu-id="a8c49-130">(Por exemplo, um aplicativo em execução na área de trabalho tem total confiança.) Se o aplicativo não tiver <xref:System.TypeLoadException> total confiança, um é jogado.</span><span class="sxs-lookup"><span data-stu-id="a8c49-130">(For example, an application running on the desktop has full trust.) If the application does not have full trust, a <xref:System.TypeLoadException> is thrown.</span></span>  
  
 <span data-ttu-id="a8c49-131">Para obter o formato do nome <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> de exibição do conjunto, consulte a propriedade.</span><span class="sxs-lookup"><span data-stu-id="a8c49-131">For the format of the assembly display name, see the <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="a8c49-132">Este elemento de configuração está disponível apenas no .NET Framework 4 e posterior.</span><span class="sxs-lookup"><span data-stu-id="a8c49-132">This configuration element is available only in the .NET Framework 4 and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a8c49-133">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a8c49-133">Example</span></span>  
 <span data-ttu-id="a8c49-134">O exemplo a seguir mostra como especificar que o gerenciador `MyMgr` de domínio `AdMgrExample` do aplicativo para o domínio de aplicativo padrão de um processo é o tipo no conjunto.</span><span class="sxs-lookup"><span data-stu-id="a8c49-134">The following example shows how to specify that the application domain manager for the default application domain of a process is the `MyMgr` type in the `AdMgrExample` assembly.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainManagerType value="MyMgr" />  
      <appDomainManagerAssembly
         value="AdMgrExample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6856bccf150f00b3" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a8c49-135">Confira também</span><span class="sxs-lookup"><span data-stu-id="a8c49-135">See also</span></span>

- <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType>
- <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType>
- [<span data-ttu-id="a8c49-136">\<aplicativoDomainManagerType> Element</span><span class="sxs-lookup"><span data-stu-id="a8c49-136">\<appDomainManagerType> Element</span></span>](appdomainmanagertype-element.md)
- [<span data-ttu-id="a8c49-137">Esquema de configurações do runtime</span><span class="sxs-lookup"><span data-stu-id="a8c49-137">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="a8c49-138">Esquema de arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="a8c49-138">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="a8c49-139">Método SetAppDomainManagerType</span><span class="sxs-lookup"><span data-stu-id="a8c49-139">SetAppDomainManagerType Method</span></span>](../../../unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)
