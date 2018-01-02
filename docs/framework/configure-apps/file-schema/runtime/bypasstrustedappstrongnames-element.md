---
title: '&lt;bypassTrustedAppStrongNames&gt; elemento'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- strong-name bypass feature
- bypassTrustedAppStrongNames element
- strong-named assemblies, loading into trusted application domains
- <bypassTrustedAppStrongNames> element
ms.assetid: 71b2ebf6-3843-41e2-ad52-ffa5cd083a40
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0343aef083076249325b9577f90964d066867f24
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltbypasstrustedappstrongnamesgt-element"></a><span data-ttu-id="c9f5d-102">&lt;bypassTrustedAppStrongNames&gt; elemento</span><span class="sxs-lookup"><span data-stu-id="c9f5d-102">&lt;bypassTrustedAppStrongNames&gt; Element</span></span>
<span data-ttu-id="c9f5d-103">Especifica se deve ignorar a validação de nomes fortes em assemblies de confiança total que são carregados em uma confiança total <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="c9f5d-103">Specifies whether to bypass the validation of strong names on full-trust assemblies that are loaded into a full-trust <xref:System.AppDomain>.</span></span>  
  
 <span data-ttu-id="c9f5d-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="c9f5d-104">\<configuration></span></span>  
<span data-ttu-id="c9f5d-105">\<tempo de execução ></span><span class="sxs-lookup"><span data-stu-id="c9f5d-105">\<runtime></span></span>  
<span data-ttu-id="c9f5d-106">\<bypassTrustedAppStrongNames ></span><span class="sxs-lookup"><span data-stu-id="c9f5d-106">\<bypassTrustedAppStrongNames></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9f5d-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c9f5d-107">Syntax</span></span>  
  
```xml  
<bypassTrustedAppStrongNames    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c9f5d-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="c9f5d-108">Attributes and Elements</span></span>  
 <span data-ttu-id="c9f5d-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="c9f5d-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c9f5d-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="c9f5d-110">Attributes</span></span>  
  
|<span data-ttu-id="c9f5d-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="c9f5d-111">Attribute</span></span>|<span data-ttu-id="c9f5d-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="c9f5d-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="c9f5d-113">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="c9f5d-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="c9f5d-114">Especifica se o recurso de desvio que evita a validação de nomes fortes para assemblies de confiança total está habilitado.</span><span class="sxs-lookup"><span data-stu-id="c9f5d-114">Specifies whether the bypass feature that avoids validating strong names for full-trust assemblies is enabled.</span></span> <span data-ttu-id="c9f5d-115">Quando esse recurso está habilitado, nomes fortes não são validados exatidão quando o assembly é carregado.</span><span class="sxs-lookup"><span data-stu-id="c9f5d-115">When this feature is enabled, strong names are not validated for correctness when the assembly is loaded.</span></span> <span data-ttu-id="c9f5d-116">O padrão é `true`.</span><span class="sxs-lookup"><span data-stu-id="c9f5d-116">The default is `true`.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="c9f5d-117">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="c9f5d-117">enabled Attribute</span></span>  
  
|<span data-ttu-id="c9f5d-118">Valor</span><span class="sxs-lookup"><span data-stu-id="c9f5d-118">Value</span></span>|<span data-ttu-id="c9f5d-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="c9f5d-119">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="c9f5d-120">Assinaturas de nome forte em assemblies de confiança total não são validadas quando os assemblies são carregados em uma confiança total <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="c9f5d-120">Strong-name signatures on full-trust assemblies are not validated when the assemblies are loaded into a full-trust <xref:System.AppDomain>.</span></span> <span data-ttu-id="c9f5d-121">Esse é o padrão.</span><span class="sxs-lookup"><span data-stu-id="c9f5d-121">This is the default.</span></span>|  
|`false`|<span data-ttu-id="c9f5d-122">Assinaturas de nome forte em assemblies de confiança total são validadas quando os assemblies são carregados em uma confiança total <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="c9f5d-122">Strong-name signatures on full-trust assemblies are validated when the assemblies are loaded into a full-trust <xref:System.AppDomain>.</span></span> <span data-ttu-id="c9f5d-123">A assinatura de nome forte é verificada apenas para correção de assinatura; ele não é comparado com outro nome de alta segurança para uma correspondência.</span><span class="sxs-lookup"><span data-stu-id="c9f5d-123">The strong-name signature is checked only for signature correctness; it is not compared to another strong name for a match.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c9f5d-124">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="c9f5d-124">Child Elements</span></span>  
 <span data-ttu-id="c9f5d-125">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="c9f5d-125">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c9f5d-126">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="c9f5d-126">Parent Elements</span></span>  
  
|<span data-ttu-id="c9f5d-127">Elemento</span><span class="sxs-lookup"><span data-stu-id="c9f5d-127">Element</span></span>|<span data-ttu-id="c9f5d-128">Descrição</span><span class="sxs-lookup"><span data-stu-id="c9f5d-128">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="c9f5d-129">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c9f5d-129">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="c9f5d-130">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="c9f5d-130">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c9f5d-131">Comentários</span><span class="sxs-lookup"><span data-stu-id="c9f5d-131">Remarks</span></span>  
 <span data-ttu-id="c9f5d-132">O recurso de desvio de nome forte evita a sobrecarga de verificação de assinatura de nome forte de assemblies de confiança total.</span><span class="sxs-lookup"><span data-stu-id="c9f5d-132">The strong-name bypass feature avoids the overhead of strong-name signature verification of full-trust assemblies.</span></span>  
  
 <span data-ttu-id="c9f5d-133">O recurso de desvio se aplica a qualquer assembly que está assinado com um nome forte e que tem as seguintes características:</span><span class="sxs-lookup"><span data-stu-id="c9f5d-133">The bypass feature applies to any assembly that is signed with a strong name and that has the following characteristics:</span></span>  
  
-   <span data-ttu-id="c9f5d-134">Totalmente confiável sem o <xref:System.Security.Policy.StrongName> evidência (por exemplo, tem `MyComputer` evidência de zona).</span><span class="sxs-lookup"><span data-stu-id="c9f5d-134">Fully trusted without the <xref:System.Security.Policy.StrongName> evidence (for example, has `MyComputer` zone evidence).</span></span>  
  
-   <span data-ttu-id="c9f5d-135">Carregado em um <xref:System.AppDomain> totalmente confiável.</span><span class="sxs-lookup"><span data-stu-id="c9f5d-135">Loaded into a fully trusted <xref:System.AppDomain>.</span></span>  
  
-   <span data-ttu-id="c9f5d-136">Carregado de um local sob a propriedade <xref:System.AppDomainSetup.ApplicationBase%2A> desse <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="c9f5d-136">Loaded from a location under the <xref:System.AppDomainSetup.ApplicationBase%2A> property of that <xref:System.AppDomain>.</span></span>  
  
-   <span data-ttu-id="c9f5d-137">Não assinado com atraso.</span><span class="sxs-lookup"><span data-stu-id="c9f5d-137">Not delay-signed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c9f5d-138">Se o recurso de desvio foi desativado para todos os aplicativos no computador usando uma chave do registro, essa configuração do arquivo de configuração não terá efeito.</span><span class="sxs-lookup"><span data-stu-id="c9f5d-138">If the bypass feature has been turned off for all applications on the computer by using a registry key, this configuration file setting has no effect.</span></span> <span data-ttu-id="c9f5d-139">Para obter mais informações, consulte [como: desabilitar o recurso de desvio de nome forte](../../../../../docs/framework/app-domains/how-to-disable-the-strong-name-bypass-feature.md).</span><span class="sxs-lookup"><span data-stu-id="c9f5d-139">For more information, see [How to: Disable the Strong-Name Bypass Feature](../../../../../docs/framework/app-domains/how-to-disable-the-strong-name-bypass-feature.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c9f5d-140">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c9f5d-140">Example</span></span>  
 <span data-ttu-id="c9f5d-141">O exemplo a seguir mostra como especificar o comportamento que valida a assinatura de nome forte em assemblies de confiança total.</span><span class="sxs-lookup"><span data-stu-id="c9f5d-141">The following example shows how to specify the behavior that validates the strong-name signature on full-trust assemblies.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <bypassTrustedAppStrongNames enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c9f5d-142">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c9f5d-142">See Also</span></span>  
 [<span data-ttu-id="c9f5d-143">Esquema de configurações do tempo de execução</span><span class="sxs-lookup"><span data-stu-id="c9f5d-143">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="c9f5d-144">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="c9f5d-144">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="c9f5d-145">Como desabilitar o recurso de desvio de nome forte</span><span class="sxs-lookup"><span data-stu-id="c9f5d-145">How to: Disable the Strong-Name Bypass Feature</span></span>](../../../../../docs/framework/app-domains/how-to-disable-the-strong-name-bypass-feature.md)
