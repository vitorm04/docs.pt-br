---
title: '&lt;generatePublisherEvidence&gt; elemento'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- generatePublisherEvidence element
- <generatePublisherEvidence> element
ms.assetid: 7d208f50-e8d5-4a42-bc1a-1cf3590706a8
caps.latest.revision: "21"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 78293c396687f9c0c99ffdfbe94cf1f3c548289d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ltgeneratepublisherevidencegt-element"></a><span data-ttu-id="d2250-102">&lt;generatePublisherEvidence&gt; elemento</span><span class="sxs-lookup"><span data-stu-id="d2250-102">&lt;generatePublisherEvidence&gt; Element</span></span>
<span data-ttu-id="d2250-103">Especifica se o tempo de execução cria <xref:System.Security.Policy.Publisher> evidência de segurança de acesso ao código (CAS).</span><span class="sxs-lookup"><span data-stu-id="d2250-103">Specifies whether the runtime creates <xref:System.Security.Policy.Publisher> evidence for code access security (CAS).</span></span>  
  
 <span data-ttu-id="d2250-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="d2250-104">\<configuration></span></span>  
<span data-ttu-id="d2250-105">\<tempo de execução ></span><span class="sxs-lookup"><span data-stu-id="d2250-105">\<runtime></span></span>  
<span data-ttu-id="d2250-106">\<generatePublisherEvidence ></span><span class="sxs-lookup"><span data-stu-id="d2250-106">\<generatePublisherEvidence></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2250-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d2250-107">Syntax</span></span>  
  
```xml  
<generatePublisherEvidence    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d2250-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="d2250-108">Attributes and Elements</span></span>  
 <span data-ttu-id="d2250-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="d2250-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d2250-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="d2250-110">Attributes</span></span>  
  
|<span data-ttu-id="d2250-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="d2250-111">Attribute</span></span>|<span data-ttu-id="d2250-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="d2250-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="d2250-113">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="d2250-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="d2250-114">Especifica se o tempo de execução cria <xref:System.Security.Policy.Publisher> evidência.</span><span class="sxs-lookup"><span data-stu-id="d2250-114">Specifies whether the runtime creates <xref:System.Security.Policy.Publisher> evidence.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="d2250-115">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="d2250-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="d2250-116">Valor</span><span class="sxs-lookup"><span data-stu-id="d2250-116">Value</span></span>|<span data-ttu-id="d2250-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="d2250-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="d2250-118">Não criar <xref:System.Security.Policy.Publisher> evidência.</span><span class="sxs-lookup"><span data-stu-id="d2250-118">Does not create <xref:System.Security.Policy.Publisher> evidence.</span></span>|  
|`true`|<span data-ttu-id="d2250-119">Cria <xref:System.Security.Policy.Publisher> evidência.</span><span class="sxs-lookup"><span data-stu-id="d2250-119">Creates <xref:System.Security.Policy.Publisher> evidence.</span></span> <span data-ttu-id="d2250-120">Esse é o padrão.</span><span class="sxs-lookup"><span data-stu-id="d2250-120">This is the default.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d2250-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="d2250-121">Child Elements</span></span>  
 <span data-ttu-id="d2250-122">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="d2250-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d2250-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="d2250-123">Parent Elements</span></span>  
  
|<span data-ttu-id="d2250-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="d2250-124">Element</span></span>|<span data-ttu-id="d2250-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="d2250-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="d2250-126">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d2250-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="d2250-127">Contém informações sobre opções de inicialização do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="d2250-127">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d2250-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="d2250-128">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d2250-129">No [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] e versões posteriores, esse elemento não tem efeito sobre os tempos de carregamento de assembly.</span><span class="sxs-lookup"><span data-stu-id="d2250-129">In the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] and later, this element has no effect on assembly load times.</span></span> <span data-ttu-id="d2250-130">Para obter mais informações, consulte a seção "Simplificação de política de segurança" [alterações de segurança](../../../../../docs/framework/security/security-changes.md).</span><span class="sxs-lookup"><span data-stu-id="d2250-130">For more information, see the "Security Policy Simplification" section in [Security Changes](../../../../../docs/framework/security/security-changes.md).</span></span>  
  
 <span data-ttu-id="d2250-131">O common language runtime (CLR) tenta verificar a assinatura Authenticode em tempo de carga para criar <xref:System.Security.Policy.Publisher> evidência para o assembly.</span><span class="sxs-lookup"><span data-stu-id="d2250-131">The common language runtime (CLR) tries to verify the Authenticode signature at load time to create <xref:System.Security.Policy.Publisher> evidence for the assembly.</span></span> <span data-ttu-id="d2250-132">No entanto, por padrão, a maioria dos aplicativos não precisarem <xref:System.Security.Policy.Publisher> evidência.</span><span class="sxs-lookup"><span data-stu-id="d2250-132">However, by default, most applications do not need <xref:System.Security.Policy.Publisher> evidence.</span></span> <span data-ttu-id="d2250-133">Política de CAS padrão não depende de <xref:System.Security.Policy.PublisherMembershipCondition>.</span><span class="sxs-lookup"><span data-stu-id="d2250-133">Standard CAS policy does not rely on the <xref:System.Security.Policy.PublisherMembershipCondition>.</span></span> <span data-ttu-id="d2250-134">Você deve evitar o custo de inicialização desnecessários associado ao verificar a assinatura do publicador, a menos que seu aplicativo é executado em um computador com a política de CAS personalizada ou é destinado atender às demandas de <xref:System.Security.Permissions.PublisherIdentityPermission> em um ambiente de confiança parcial.</span><span class="sxs-lookup"><span data-stu-id="d2250-134">You should avoid the unnecessary startup cost associated with verifying the publisher signature unless your application executes on a computer with custom CAS policy, or is intending to satisfy demands for <xref:System.Security.Permissions.PublisherIdentityPermission> in a partial-trust environment.</span></span> <span data-ttu-id="d2250-135">(Demandas de permissões de identidade sempre terá êxito em um ambiente de confiança total).</span><span class="sxs-lookup"><span data-stu-id="d2250-135">(Demands for identity permissions always succeed in a full-trust environment.)</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d2250-136">É recomendável que serviços usam o `<generatePublisherEvidence>` elemento para melhorar o desempenho de inicialização.</span><span class="sxs-lookup"><span data-stu-id="d2250-136">We recommend that services use the `<generatePublisherEvidence>` element to improve startup performance.</span></span>  <span data-ttu-id="d2250-137">Usar esse elemento também pode ajudar a evitar atrasos que podem causar um tempo limite e o cancelamento da inicialização do serviço.</span><span class="sxs-lookup"><span data-stu-id="d2250-137">Using this element can also help avoid delays that can cause a time-out and the cancellation of the service startup.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="d2250-138">Arquivo de Configuração</span><span class="sxs-lookup"><span data-stu-id="d2250-138">Configuration File</span></span>  
 <span data-ttu-id="d2250-139">Esse elemento pode ser usado apenas no arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d2250-139">This element can be used only in the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d2250-140">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d2250-140">Example</span></span>  
 <span data-ttu-id="d2250-141">O exemplo a seguir mostra como usar o `<generatePublisherEvidence>` elemento para desabilitar a verificação de política de editor de autoridades de certificação para um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d2250-141">The following example shows how to use the `<generatePublisherEvidence>` element to disable checking for CAS publisher policy for an application.</span></span>  
  
```xml  
<configuration>  
    <runtime>  
        <generatePublisherEvidence enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d2250-142">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d2250-142">See Also</span></span>  
 [<span data-ttu-id="d2250-143">Esquema de configurações do tempo de execução</span><span class="sxs-lookup"><span data-stu-id="d2250-143">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="d2250-144">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="d2250-144">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
