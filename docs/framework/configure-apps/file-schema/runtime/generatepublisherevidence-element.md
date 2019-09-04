---
title: Elemento <generatePublisherEvidence>
ms.date: 03/30/2017
helpviewer_keywords:
- generatePublisherEvidence element
- <generatePublisherEvidence> element
ms.assetid: 7d208f50-e8d5-4a42-bc1a-1cf3590706a8
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3dd3105e573d40ae234ba7e122f20566911124d4
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252535"
---
# <a name="generatepublisherevidence-element"></a><span data-ttu-id="e777b-102">\<Elemento de > generatePublisherEvidence</span><span class="sxs-lookup"><span data-stu-id="e777b-102">\<generatePublisherEvidence> Element</span></span>
<span data-ttu-id="e777b-103">Especifica se o tempo de <xref:System.Security.Policy.Publisher> execução cria evidências para a CAS (segurança de acesso do código).</span><span class="sxs-lookup"><span data-stu-id="e777b-103">Specifies whether the runtime creates <xref:System.Security.Policy.Publisher> evidence for code access security (CAS).</span></span>  
  
<span data-ttu-id="e777b-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="e777b-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="e777b-105">&nbsp;&nbsp;[ **\<> de tempo de execução**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="e777b-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="e777b-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<generatePublisherEvidence>**</span><span class="sxs-lookup"><span data-stu-id="e777b-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<generatePublisherEvidence>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e777b-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e777b-107">Syntax</span></span>  
  
```xml  
<generatePublisherEvidence    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e777b-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="e777b-108">Attributes and Elements</span></span>  
 <span data-ttu-id="e777b-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="e777b-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e777b-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="e777b-110">Attributes</span></span>  
  
|<span data-ttu-id="e777b-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="e777b-111">Attribute</span></span>|<span data-ttu-id="e777b-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="e777b-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="e777b-113">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="e777b-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="e777b-114">Especifica se o tempo de <xref:System.Security.Policy.Publisher> execução cria evidências.</span><span class="sxs-lookup"><span data-stu-id="e777b-114">Specifies whether the runtime creates <xref:System.Security.Policy.Publisher> evidence.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="e777b-115">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="e777b-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="e777b-116">Valor</span><span class="sxs-lookup"><span data-stu-id="e777b-116">Value</span></span>|<span data-ttu-id="e777b-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="e777b-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="e777b-118">Não cria <xref:System.Security.Policy.Publisher> evidências.</span><span class="sxs-lookup"><span data-stu-id="e777b-118">Does not create <xref:System.Security.Policy.Publisher> evidence.</span></span>|  
|`true`|<span data-ttu-id="e777b-119">Cria <xref:System.Security.Policy.Publisher> evidências.</span><span class="sxs-lookup"><span data-stu-id="e777b-119">Creates <xref:System.Security.Policy.Publisher> evidence.</span></span> <span data-ttu-id="e777b-120">Esse é o padrão.</span><span class="sxs-lookup"><span data-stu-id="e777b-120">This is the default.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e777b-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="e777b-121">Child Elements</span></span>  
 <span data-ttu-id="e777b-122">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="e777b-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e777b-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="e777b-123">Parent Elements</span></span>  
  
|<span data-ttu-id="e777b-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="e777b-124">Element</span></span>|<span data-ttu-id="e777b-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="e777b-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="e777b-126">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e777b-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="e777b-127">Contém informações sobre opções de inicialização do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="e777b-127">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e777b-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="e777b-128">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e777b-129">No .NET Framework 4 e posterior, esse elemento não tem nenhum efeito sobre os tempos de carregamento do assembly.</span><span class="sxs-lookup"><span data-stu-id="e777b-129">In the .NET Framework 4 and later, this element has no effect on assembly load times.</span></span> <span data-ttu-id="e777b-130">Para obter mais informações, consulte a seção "simplificação da política de segurança" em [alterações de segurança](../../../security/security-changes.md).</span><span class="sxs-lookup"><span data-stu-id="e777b-130">For more information, see the "Security Policy Simplification" section in [Security Changes](../../../security/security-changes.md).</span></span>  
  
 <span data-ttu-id="e777b-131">O Common Language Runtime (CLR) tenta verificar a assinatura Authenticode no tempo de carregamento para criar <xref:System.Security.Policy.Publisher> evidências para o assembly.</span><span class="sxs-lookup"><span data-stu-id="e777b-131">The common language runtime (CLR) tries to verify the Authenticode signature at load time to create <xref:System.Security.Policy.Publisher> evidence for the assembly.</span></span> <span data-ttu-id="e777b-132">No entanto, por padrão, a maioria dos <xref:System.Security.Policy.Publisher> aplicativos não precisa de evidências.</span><span class="sxs-lookup"><span data-stu-id="e777b-132">However, by default, most applications do not need <xref:System.Security.Policy.Publisher> evidence.</span></span> <span data-ttu-id="e777b-133">A política de CAS padrão não depende do <xref:System.Security.Policy.PublisherMembershipCondition>.</span><span class="sxs-lookup"><span data-stu-id="e777b-133">Standard CAS policy does not rely on the <xref:System.Security.Policy.PublisherMembershipCondition>.</span></span> <span data-ttu-id="e777b-134">Você deve evitar o custo de inicialização desnecessário associado à verificação da assinatura do Publicador, a menos que seu aplicativo seja executado em um computador com uma política de CAS personalizada ou que <xref:System.Security.Permissions.PublisherIdentityPermission> pretenda atender às demandas de em um ambiente de confiança parcial.</span><span class="sxs-lookup"><span data-stu-id="e777b-134">You should avoid the unnecessary startup cost associated with verifying the publisher signature unless your application executes on a computer with custom CAS policy, or is intending to satisfy demands for <xref:System.Security.Permissions.PublisherIdentityPermission> in a partial-trust environment.</span></span> <span data-ttu-id="e777b-135">(As demandas de permissões de identidade sempre tiveram sucesso em um ambiente de confiança total.)</span><span class="sxs-lookup"><span data-stu-id="e777b-135">(Demands for identity permissions always succeed in a full-trust environment.)</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e777b-136">Recomendamos que os serviços usem `<generatePublisherEvidence>` o elemento para melhorar o desempenho de inicialização.</span><span class="sxs-lookup"><span data-stu-id="e777b-136">We recommend that services use the `<generatePublisherEvidence>` element to improve startup performance.</span></span>  <span data-ttu-id="e777b-137">O uso desse elemento também pode ajudar a evitar atrasos que podem causar um tempo limite e o cancelamento da inicialização do serviço.</span><span class="sxs-lookup"><span data-stu-id="e777b-137">Using this element can also help avoid delays that can cause a time-out and the cancellation of the service startup.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="e777b-138">Arquivo de Configuração</span><span class="sxs-lookup"><span data-stu-id="e777b-138">Configuration File</span></span>  
 <span data-ttu-id="e777b-139">Esse elemento só pode ser usado no arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e777b-139">This element can be used only in the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e777b-140">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e777b-140">Example</span></span>  
 <span data-ttu-id="e777b-141">O exemplo a seguir mostra como usar o `<generatePublisherEvidence>` elemento para desabilitar a verificação da política de editor de CAS para um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e777b-141">The following example shows how to use the `<generatePublisherEvidence>` element to disable checking for CAS publisher policy for an application.</span></span>  
  
```xml  
<configuration>  
    <runtime>  
        <generatePublisherEvidence enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e777b-142">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e777b-142">See also</span></span>

- [<span data-ttu-id="e777b-143">Esquema de configurações do tempo de execução</span><span class="sxs-lookup"><span data-stu-id="e777b-143">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="e777b-144">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="e777b-144">Configuration File Schema</span></span>](../index.md)
