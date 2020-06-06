---
title: Elemento <appDomainManagerType>
ms.date: 03/30/2017
helpviewer_keywords:
- appDomainManagerType element
- <appDomainManagerType> element
ms.assetid: ae8d5a7e-e7f7-47f7-98d9-455cc243a322
ms.openlocfilehash: 8eb6129b3fafaeb81a94d5a4078e41a16583a226
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154414"
---
# <a name="appdomainmanagertype-element"></a><span data-ttu-id="a5a5b-102">Elemento \<appDomainManagerType></span><span class="sxs-lookup"><span data-stu-id="a5a5b-102">\<appDomainManagerType> Element</span></span>
<span data-ttu-id="a5a5b-103">Especifica o tipo que serve como o gerenciador de domínio do aplicativo para o domínio do aplicativo padrão.</span><span class="sxs-lookup"><span data-stu-id="a5a5b-103">Specifies the type that serves as the application domain manager for the default application domain.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<appDomainManagerType>**  
  
## <a name="syntax"></a><span data-ttu-id="a5a5b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a5a5b-104">Syntax</span></span>  
  
```xml  
<appDomainManagerAssembly
   value="type name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a5a5b-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="a5a5b-105">Attributes and Elements</span></span>  
 <span data-ttu-id="a5a5b-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="a5a5b-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a5a5b-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="a5a5b-107">Attributes</span></span>  
  
|<span data-ttu-id="a5a5b-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="a5a5b-108">Attribute</span></span>|<span data-ttu-id="a5a5b-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="a5a5b-109">Description</span></span>|  
|---------------|-----------------|  
|`value`|<span data-ttu-id="a5a5b-110">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="a5a5b-110">Required attribute.</span></span> <span data-ttu-id="a5a5b-111">Especifica o nome do tipo, incluindo o namespace, que serve como o Gerenciador de domínio do aplicativo para o domínio de aplicativo padrão no processo.</span><span class="sxs-lookup"><span data-stu-id="a5a5b-111">Specifies the name of the type, including the namespace, that serves as the application domain manager for the default application domain in the process.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a5a5b-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="a5a5b-112">Child Elements</span></span>  
 <span data-ttu-id="a5a5b-113">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="a5a5b-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a5a5b-114">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="a5a5b-114">Parent Elements</span></span>  
  
|<span data-ttu-id="a5a5b-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="a5a5b-115">Element</span></span>|<span data-ttu-id="a5a5b-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="a5a5b-116">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="a5a5b-117">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a5a5b-117">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="a5a5b-118">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="a5a5b-118">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a5a5b-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="a5a5b-119">Remarks</span></span>  
 <span data-ttu-id="a5a5b-120">Para especificar o tipo de Gerenciador de domínio do aplicativo, você deve especificar esse elemento e o [\<appDomainManagerAssembly>](appdomainmanagerassembly-element.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="a5a5b-120">To specify the type of the application domain manager, you must specify both this element and the [\<appDomainManagerAssembly>](appdomainmanagerassembly-element.md) element.</span></span> <span data-ttu-id="a5a5b-121">Se um desses elementos não for especificado, o outro será ignorado.</span><span class="sxs-lookup"><span data-stu-id="a5a5b-121">If either of these elements is not specified, the other is ignored.</span></span>  
  
 <span data-ttu-id="a5a5b-122">Quando o domínio de aplicativo padrão for carregado, <xref:System.TypeLoadException> será gerado se o tipo especificado não existir no assembly especificado pelo [\<appDomainManagerAssembly>](appdomainmanagerassembly-element.md) elemento; e o processo não for iniciado.</span><span class="sxs-lookup"><span data-stu-id="a5a5b-122">When the default application domain is loaded, <xref:System.TypeLoadException> is thrown if the specified type does not exist in the assembly that is specified by the [\<appDomainManagerAssembly>](appdomainmanagerassembly-element.md) element; and the process fails to start.</span></span>  
  
 <span data-ttu-id="a5a5b-123">Quando você especifica o tipo de Gerenciador de domínio do aplicativo para o domínio de aplicativo padrão, outros domínios de aplicativo criados a partir do domínio de aplicativo padrão herdam o tipo de Gerenciador de domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a5a5b-123">When you specify the application domain manager type for the default application domain, other application domains created from the default application domain inherit the application domain manager type.</span></span> <span data-ttu-id="a5a5b-124">Use as <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> Propriedades e para especificar um tipo de Gerenciador de domínio de aplicativo diferente para um novo domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a5a5b-124">Use the <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> and <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> properties to specify a different application domain manager type for a new application domain.</span></span>  
  
 <span data-ttu-id="a5a5b-125">A especificação do tipo de Gerenciador de domínio do aplicativo exige que o aplicativo tenha confiança total.</span><span class="sxs-lookup"><span data-stu-id="a5a5b-125">Specifying the application domain manager type requires the application to have full trust.</span></span> <span data-ttu-id="a5a5b-126">(Por exemplo, um aplicativo em execução na área de trabalho tem confiança total.) Se o aplicativo não tiver confiança total, um <xref:System.TypeLoadException> será lançado.</span><span class="sxs-lookup"><span data-stu-id="a5a5b-126">(For example, an application running on the desktop has full trust.) If the application does not have full trust, a <xref:System.TypeLoadException> is thrown.</span></span>  
  
 <span data-ttu-id="a5a5b-127">O formato do tipo e do namespace é o mesmo formato usado para a <xref:System.Type.FullName%2A?displayProperty=nameWithType> propriedade.</span><span class="sxs-lookup"><span data-stu-id="a5a5b-127">The format of the type and namespace is the same format that is used for the <xref:System.Type.FullName%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="a5a5b-128">Este elemento de configuração está disponível apenas no .NET Framework 4 e posterior.</span><span class="sxs-lookup"><span data-stu-id="a5a5b-128">This configuration element is available only in the .NET Framework 4 and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a5a5b-129">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a5a5b-129">Example</span></span>  
 <span data-ttu-id="a5a5b-130">O exemplo a seguir mostra como especificar que o Gerenciador de domínio do aplicativo para o domínio de aplicativo padrão de um processo é o `MyMgr` tipo no `AdMgrExample` assembly.</span><span class="sxs-lookup"><span data-stu-id="a5a5b-130">The following example shows how to specify that the application domain manager for the default application domain of a process is the `MyMgr` type in the `AdMgrExample` assembly.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainManagerType value="MyMgr" />  
      <appDomainManagerAssembly
         value="AdMgrExample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6856bccf150f00b3" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a5a5b-131">Confira também</span><span class="sxs-lookup"><span data-stu-id="a5a5b-131">See also</span></span>

- <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType>
- <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType>
- [<span data-ttu-id="a5a5b-132">\<appDomainManagerAssembly>Elementos</span><span class="sxs-lookup"><span data-stu-id="a5a5b-132">\<appDomainManagerAssembly> Element</span></span>](appdomainmanagerassembly-element.md)
- [<span data-ttu-id="a5a5b-133">Esquema de configurações do runtime</span><span class="sxs-lookup"><span data-stu-id="a5a5b-133">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="a5a5b-134">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="a5a5b-134">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="a5a5b-135">Método SetAppDomainManagerType</span><span class="sxs-lookup"><span data-stu-id="a5a5b-135">SetAppDomainManagerType Method</span></span>](../../../unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)
