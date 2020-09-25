---
title: Elemento <appDomainManagerAssembly>
ms.date: 03/30/2017
helpviewer_keywords:
- <appDomainManagerAssembly> element
- appDomainManagerAssembly element
ms.assetid: c7c56e39-a700-44f5-b94e-411bfce339d9
ms.openlocfilehash: 1716b11106775bed2c0d6ccb62e8d5b032b6e8be
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91176130"
---
# <a name="appdomainmanagerassembly-element"></a><span data-ttu-id="e7e85-102">Elemento \<appDomainManagerAssembly></span><span class="sxs-lookup"><span data-stu-id="e7e85-102">\<appDomainManagerAssembly> Element</span></span>

<span data-ttu-id="e7e85-103">Especifica o assembly que fornece o gerenciador do domínio do aplicativo para o domínio do aplicativo padrão no processo.</span><span class="sxs-lookup"><span data-stu-id="e7e85-103">Specifies the assembly that provides the application domain manager for the default application domain in the process.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<appDomainManagerAssembly>**  
  
## <a name="syntax"></a><span data-ttu-id="e7e85-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e7e85-104">Syntax</span></span>  
  
```xml  
<appDomainManagerAssembly
   value="assembly display name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e7e85-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="e7e85-105">Attributes and Elements</span></span>  

 <span data-ttu-id="e7e85-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="e7e85-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e7e85-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="e7e85-107">Attributes</span></span>  
  
|<span data-ttu-id="e7e85-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="e7e85-108">Attribute</span></span>|<span data-ttu-id="e7e85-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="e7e85-109">Description</span></span>|  
|---------------|-----------------|  
|`value`|<span data-ttu-id="e7e85-110">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="e7e85-110">Required attribute.</span></span> <span data-ttu-id="e7e85-111">Especifica o nome de exibição do assembly que fornece o Gerenciador de domínio do aplicativo para o domínio de aplicativo padrão no processo.</span><span class="sxs-lookup"><span data-stu-id="e7e85-111">Specifies the display name of the assembly that provides the application domain manager for the default application domain in the process.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e7e85-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="e7e85-112">Child Elements</span></span>  

 <span data-ttu-id="e7e85-113">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="e7e85-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e7e85-114">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="e7e85-114">Parent Elements</span></span>  
  
|<span data-ttu-id="e7e85-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="e7e85-115">Element</span></span>|<span data-ttu-id="e7e85-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="e7e85-116">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="e7e85-117">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e7e85-117">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="e7e85-118">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="e7e85-118">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e7e85-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="e7e85-119">Remarks</span></span>  

 <span data-ttu-id="e7e85-120">Para especificar o tipo de Gerenciador de domínio do aplicativo, você deve especificar esse elemento e o [\<appDomainManagerType>](appdomainmanagertype-element.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="e7e85-120">To specify the type of the application domain manager, you must specify both this element and the [\<appDomainManagerType>](appdomainmanagertype-element.md) element.</span></span> <span data-ttu-id="e7e85-121">Se um desses elementos não for especificado, o outro será ignorado.</span><span class="sxs-lookup"><span data-stu-id="e7e85-121">If either of these elements is not specified, the other is ignored.</span></span>  
  
 <span data-ttu-id="e7e85-122">Quando o domínio de aplicativo padrão for carregado, <xref:System.TypeLoadException> será gerado se o assembly especificado não existir ou se o assembly não contiver o tipo especificado pelo [\<appDomainManagerType>](appdomainmanagertype-element.md) elemento; e o processo não for iniciado.</span><span class="sxs-lookup"><span data-stu-id="e7e85-122">When the default application domain is loaded, <xref:System.TypeLoadException> is thrown if the specified assembly does not exist or if the assembly does not contain the type specified by the [\<appDomainManagerType>](appdomainmanagertype-element.md) element; and the process fails to start.</span></span> <span data-ttu-id="e7e85-123">Se o assembly for encontrado, mas as informações de versão não corresponderem, um <xref:System.IO.FileLoadException> será lançado.</span><span class="sxs-lookup"><span data-stu-id="e7e85-123">If the assembly is found but the version information does not match, a <xref:System.IO.FileLoadException> is thrown.</span></span>  
  
 <span data-ttu-id="e7e85-124">Quando você especifica o tipo de Gerenciador de domínio do aplicativo para o domínio de aplicativo padrão, outros domínios de aplicativo criados a partir do domínio de aplicativo padrão herdam o tipo de Gerenciador de domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e7e85-124">When you specify the application domain manager type for the default application domain, other application domains created from the default application domain inherit the application domain manager type.</span></span> <span data-ttu-id="e7e85-125">Use as <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> Propriedades e para especificar um tipo de Gerenciador de domínio de aplicativo diferente para um novo domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e7e85-125">Use the <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> and <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> properties to specify a different application domain manager type for a new application domain.</span></span>  
  
 <span data-ttu-id="e7e85-126">A especificação do tipo de Gerenciador de domínio do aplicativo exige que o aplicativo tenha confiança total.</span><span class="sxs-lookup"><span data-stu-id="e7e85-126">Specifying the application domain manager type requires the application to have full trust.</span></span> <span data-ttu-id="e7e85-127">(Por exemplo, um aplicativo em execução na área de trabalho tem confiança total.) Se o aplicativo não tiver confiança total, um <xref:System.TypeLoadException> será lançado.</span><span class="sxs-lookup"><span data-stu-id="e7e85-127">(For example, an application running on the desktop has full trust.) If the application does not have full trust, a <xref:System.TypeLoadException> is thrown.</span></span>  
  
 <span data-ttu-id="e7e85-128">Para o formato do nome de exibição do assembly, consulte a <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> propriedade.</span><span class="sxs-lookup"><span data-stu-id="e7e85-128">For the format of the assembly display name, see the <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="e7e85-129">Este elemento de configuração está disponível apenas no .NET Framework 4 e posterior.</span><span class="sxs-lookup"><span data-stu-id="e7e85-129">This configuration element is available only in the .NET Framework 4 and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e7e85-130">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e7e85-130">Example</span></span>  

 <span data-ttu-id="e7e85-131">O exemplo a seguir mostra como especificar que o Gerenciador de domínio do aplicativo para o domínio de aplicativo padrão de um processo é o `MyMgr` tipo no `AdMgrExample` assembly.</span><span class="sxs-lookup"><span data-stu-id="e7e85-131">The following example shows how to specify that the application domain manager for the default application domain of a process is the `MyMgr` type in the `AdMgrExample` assembly.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainManagerType value="MyMgr" />  
      <appDomainManagerAssembly
         value="AdMgrExample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6856bccf150f00b3" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e7e85-132">Confira também</span><span class="sxs-lookup"><span data-stu-id="e7e85-132">See also</span></span>

- <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType>
- <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType>
- [<span data-ttu-id="e7e85-133">\<appDomainManagerType> Elementos</span><span class="sxs-lookup"><span data-stu-id="e7e85-133">\<appDomainManagerType> Element</span></span>](appdomainmanagertype-element.md)
- [<span data-ttu-id="e7e85-134">Esquema de configurações do runtime</span><span class="sxs-lookup"><span data-stu-id="e7e85-134">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="e7e85-135">Esquema do arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="e7e85-135">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="e7e85-136">Método SetAppDomainManagerType</span><span class="sxs-lookup"><span data-stu-id="e7e85-136">SetAppDomainManagerType Method</span></span>](../../../unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)
