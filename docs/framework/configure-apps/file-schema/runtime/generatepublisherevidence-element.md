---
title: Elemento <generatePublisherEvidence>
ms.date: 03/30/2017
helpviewer_keywords:
- generatePublisherEvidence element
- <generatePublisherEvidence> element
ms.assetid: 7d208f50-e8d5-4a42-bc1a-1cf3590706a8
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a5314fe5927abf2d3855acb45c763507ab6cb3c8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920758"
---
# <a name="generatepublisherevidence-element"></a><span data-ttu-id="de1e6-102">\<Elemento de > generatePublisherEvidence</span><span class="sxs-lookup"><span data-stu-id="de1e6-102">\<generatePublisherEvidence> Element</span></span>
<span data-ttu-id="de1e6-103">Especifica se o tempo de <xref:System.Security.Policy.Publisher> execução cria evidências para a CAS (segurança de acesso do código).</span><span class="sxs-lookup"><span data-stu-id="de1e6-103">Specifies whether the runtime creates <xref:System.Security.Policy.Publisher> evidence for code access security (CAS).</span></span>  
  
 <span data-ttu-id="de1e6-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="de1e6-104">\<configuration></span></span>  
<span data-ttu-id="de1e6-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="de1e6-105">\<runtime></span></span>  
<span data-ttu-id="de1e6-106">\<> generatePublisherEvidence</span><span class="sxs-lookup"><span data-stu-id="de1e6-106">\<generatePublisherEvidence></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de1e6-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="de1e6-107">Syntax</span></span>  
  
```xml  
<generatePublisherEvidence    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="de1e6-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="de1e6-108">Attributes and Elements</span></span>  
 <span data-ttu-id="de1e6-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="de1e6-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="de1e6-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="de1e6-110">Attributes</span></span>  
  
|<span data-ttu-id="de1e6-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="de1e6-111">Attribute</span></span>|<span data-ttu-id="de1e6-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="de1e6-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="de1e6-113">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="de1e6-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="de1e6-114">Especifica se o tempo de <xref:System.Security.Policy.Publisher> execução cria evidências.</span><span class="sxs-lookup"><span data-stu-id="de1e6-114">Specifies whether the runtime creates <xref:System.Security.Policy.Publisher> evidence.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="de1e6-115">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="de1e6-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="de1e6-116">Valor</span><span class="sxs-lookup"><span data-stu-id="de1e6-116">Value</span></span>|<span data-ttu-id="de1e6-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="de1e6-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="de1e6-118">Não cria <xref:System.Security.Policy.Publisher> evidências.</span><span class="sxs-lookup"><span data-stu-id="de1e6-118">Does not create <xref:System.Security.Policy.Publisher> evidence.</span></span>|  
|`true`|<span data-ttu-id="de1e6-119">Cria <xref:System.Security.Policy.Publisher> evidências.</span><span class="sxs-lookup"><span data-stu-id="de1e6-119">Creates <xref:System.Security.Policy.Publisher> evidence.</span></span> <span data-ttu-id="de1e6-120">Esse é o padrão.</span><span class="sxs-lookup"><span data-stu-id="de1e6-120">This is the default.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="de1e6-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="de1e6-121">Child Elements</span></span>  
 <span data-ttu-id="de1e6-122">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="de1e6-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="de1e6-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="de1e6-123">Parent Elements</span></span>  
  
|<span data-ttu-id="de1e6-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="de1e6-124">Element</span></span>|<span data-ttu-id="de1e6-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="de1e6-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="de1e6-126">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="de1e6-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="de1e6-127">Contém informações sobre opções de inicialização do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="de1e6-127">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="de1e6-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="de1e6-128">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="de1e6-129">No .NET Framework 4 e posterior, esse elemento não tem nenhum efeito sobre os tempos de carregamento do assembly.</span><span class="sxs-lookup"><span data-stu-id="de1e6-129">In the .NET Framework 4 and later, this element has no effect on assembly load times.</span></span> <span data-ttu-id="de1e6-130">Para obter mais informações, consulte a seção "simplificação da política de segurança" em [alterações de segurança](../../../security/security-changes.md).</span><span class="sxs-lookup"><span data-stu-id="de1e6-130">For more information, see the "Security Policy Simplification" section in [Security Changes](../../../security/security-changes.md).</span></span>  
  
 <span data-ttu-id="de1e6-131">O Common Language Runtime (CLR) tenta verificar a assinatura Authenticode no tempo de carregamento para criar <xref:System.Security.Policy.Publisher> evidências para o assembly.</span><span class="sxs-lookup"><span data-stu-id="de1e6-131">The common language runtime (CLR) tries to verify the Authenticode signature at load time to create <xref:System.Security.Policy.Publisher> evidence for the assembly.</span></span> <span data-ttu-id="de1e6-132">No entanto, por padrão, a maioria dos <xref:System.Security.Policy.Publisher> aplicativos não precisa de evidências.</span><span class="sxs-lookup"><span data-stu-id="de1e6-132">However, by default, most applications do not need <xref:System.Security.Policy.Publisher> evidence.</span></span> <span data-ttu-id="de1e6-133">A política de CAS padrão não depende do <xref:System.Security.Policy.PublisherMembershipCondition>.</span><span class="sxs-lookup"><span data-stu-id="de1e6-133">Standard CAS policy does not rely on the <xref:System.Security.Policy.PublisherMembershipCondition>.</span></span> <span data-ttu-id="de1e6-134">Você deve evitar o custo de inicialização desnecessário associado à verificação da assinatura do Publicador, a menos que seu aplicativo seja executado em um computador com uma política de CAS personalizada ou que <xref:System.Security.Permissions.PublisherIdentityPermission> pretenda atender às demandas de em um ambiente de confiança parcial.</span><span class="sxs-lookup"><span data-stu-id="de1e6-134">You should avoid the unnecessary startup cost associated with verifying the publisher signature unless your application executes on a computer with custom CAS policy, or is intending to satisfy demands for <xref:System.Security.Permissions.PublisherIdentityPermission> in a partial-trust environment.</span></span> <span data-ttu-id="de1e6-135">(As demandas de permissões de identidade sempre tiveram sucesso em um ambiente de confiança total.)</span><span class="sxs-lookup"><span data-stu-id="de1e6-135">(Demands for identity permissions always succeed in a full-trust environment.)</span></span>  
  
> [!NOTE]
> <span data-ttu-id="de1e6-136">Recomendamos que os serviços usem `<generatePublisherEvidence>` o elemento para melhorar o desempenho de inicialização.</span><span class="sxs-lookup"><span data-stu-id="de1e6-136">We recommend that services use the `<generatePublisherEvidence>` element to improve startup performance.</span></span>  <span data-ttu-id="de1e6-137">O uso desse elemento também pode ajudar a evitar atrasos que podem causar um tempo limite e o cancelamento da inicialização do serviço.</span><span class="sxs-lookup"><span data-stu-id="de1e6-137">Using this element can also help avoid delays that can cause a time-out and the cancellation of the service startup.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="de1e6-138">Arquivo de Configuração</span><span class="sxs-lookup"><span data-stu-id="de1e6-138">Configuration File</span></span>  
 <span data-ttu-id="de1e6-139">Esse elemento só pode ser usado no arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="de1e6-139">This element can be used only in the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="de1e6-140">Exemplo</span><span class="sxs-lookup"><span data-stu-id="de1e6-140">Example</span></span>  
 <span data-ttu-id="de1e6-141">O exemplo a seguir mostra como usar o `<generatePublisherEvidence>` elemento para desabilitar a verificação da política de editor de CAS para um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="de1e6-141">The following example shows how to use the `<generatePublisherEvidence>` element to disable checking for CAS publisher policy for an application.</span></span>  
  
```xml  
<configuration>  
    <runtime>  
        <generatePublisherEvidence enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="de1e6-142">Consulte também</span><span class="sxs-lookup"><span data-stu-id="de1e6-142">See also</span></span>

- [<span data-ttu-id="de1e6-143">Esquema de configurações do tempo de execução</span><span class="sxs-lookup"><span data-stu-id="de1e6-143">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="de1e6-144">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="de1e6-144">Configuration File Schema</span></span>](../index.md)
