---
title: Elemento <generatePublisherEvidence>
ms.date: 03/30/2017
helpviewer_keywords:
- generatePublisherEvidence element
- <generatePublisherEvidence> element
ms.assetid: 7d208f50-e8d5-4a42-bc1a-1cf3590706a8
ms.openlocfilehash: c2ba4a7244b7849e28eac38fb34a2cdd0d1f1048
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "81645353"
---
# <a name="generatepublisherevidence-element"></a><span data-ttu-id="13ed5-102">Elemento \<generatePublisherEvidence></span><span class="sxs-lookup"><span data-stu-id="13ed5-102">\<generatePublisherEvidence> Element</span></span>
<span data-ttu-id="13ed5-103">Especifica se o tempo de execução cria <xref:System.Security.Policy.Publisher> evidências para a CAS (segurança de acesso do código).</span><span class="sxs-lookup"><span data-stu-id="13ed5-103">Specifies whether the runtime creates <xref:System.Security.Policy.Publisher> evidence for code access security (CAS).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<generatePublisherEvidence>**  
  
## <a name="syntax"></a><span data-ttu-id="13ed5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="13ed5-104">Syntax</span></span>  
  
```xml  
<generatePublisherEvidence
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="13ed5-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="13ed5-105">Attributes and Elements</span></span>  
 <span data-ttu-id="13ed5-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="13ed5-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="13ed5-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="13ed5-107">Attributes</span></span>  
  
|<span data-ttu-id="13ed5-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="13ed5-108">Attribute</span></span>|<span data-ttu-id="13ed5-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="13ed5-109">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="13ed5-110">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="13ed5-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="13ed5-111">Especifica se o tempo de execução cria <xref:System.Security.Policy.Publisher> evidências.</span><span class="sxs-lookup"><span data-stu-id="13ed5-111">Specifies whether the runtime creates <xref:System.Security.Policy.Publisher> evidence.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="13ed5-112">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="13ed5-112">enabled Attribute</span></span>  
  
|<span data-ttu-id="13ed5-113">Valor</span><span class="sxs-lookup"><span data-stu-id="13ed5-113">Value</span></span>|<span data-ttu-id="13ed5-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="13ed5-114">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="13ed5-115">Não cria <xref:System.Security.Policy.Publisher> evidências.</span><span class="sxs-lookup"><span data-stu-id="13ed5-115">Does not create <xref:System.Security.Policy.Publisher> evidence.</span></span>|  
|`true`|<span data-ttu-id="13ed5-116">Cria <xref:System.Security.Policy.Publisher> evidências.</span><span class="sxs-lookup"><span data-stu-id="13ed5-116">Creates <xref:System.Security.Policy.Publisher> evidence.</span></span> <span data-ttu-id="13ed5-117">Este é o padrão.</span><span class="sxs-lookup"><span data-stu-id="13ed5-117">This is the default.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="13ed5-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="13ed5-118">Child Elements</span></span>  
 <span data-ttu-id="13ed5-119">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="13ed5-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="13ed5-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="13ed5-120">Parent Elements</span></span>  
  
|<span data-ttu-id="13ed5-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="13ed5-121">Element</span></span>|<span data-ttu-id="13ed5-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="13ed5-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="13ed5-123">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="13ed5-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="13ed5-124">Contém informações sobre opções de inicialização do runtime.</span><span class="sxs-lookup"><span data-stu-id="13ed5-124">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="13ed5-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="13ed5-125">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="13ed5-126">No .NET Framework 4 e posterior, esse elemento não tem nenhum efeito sobre os tempos de carregamento do assembly.</span><span class="sxs-lookup"><span data-stu-id="13ed5-126">In the .NET Framework 4 and later, this element has no effect on assembly load times.</span></span> <span data-ttu-id="13ed5-127">Para obter mais informações, consulte a seção "simplificação da política de segurança" em [alterações de segurança](https://docs.microsoft.com/previous-versions/dotnet/framework/security/security-changes).</span><span class="sxs-lookup"><span data-stu-id="13ed5-127">For more information, see the "Security Policy Simplification" section in [Security Changes](https://docs.microsoft.com/previous-versions/dotnet/framework/security/security-changes).</span></span>  
  
 <span data-ttu-id="13ed5-128">O Common Language Runtime (CLR) tenta verificar a assinatura Authenticode no tempo de carregamento para criar <xref:System.Security.Policy.Publisher> evidências para o assembly.</span><span class="sxs-lookup"><span data-stu-id="13ed5-128">The common language runtime (CLR) tries to verify the Authenticode signature at load time to create <xref:System.Security.Policy.Publisher> evidence for the assembly.</span></span> <span data-ttu-id="13ed5-129">No entanto, por padrão, a maioria dos aplicativos não precisa de <xref:System.Security.Policy.Publisher> evidências.</span><span class="sxs-lookup"><span data-stu-id="13ed5-129">However, by default, most applications do not need <xref:System.Security.Policy.Publisher> evidence.</span></span> <span data-ttu-id="13ed5-130">A política de CAS padrão não depende do <xref:System.Security.Policy.PublisherMembershipCondition> .</span><span class="sxs-lookup"><span data-stu-id="13ed5-130">Standard CAS policy does not rely on the <xref:System.Security.Policy.PublisherMembershipCondition>.</span></span> <span data-ttu-id="13ed5-131">Você deve evitar o custo de inicialização desnecessário associado à verificação da assinatura do Publicador, a menos que seu aplicativo seja executado em um computador com uma política de CAS personalizada ou que pretenda atender às demandas de <xref:System.Security.Permissions.PublisherIdentityPermission> em um ambiente de confiança parcial.</span><span class="sxs-lookup"><span data-stu-id="13ed5-131">You should avoid the unnecessary startup cost associated with verifying the publisher signature unless your application executes on a computer with custom CAS policy, or is intending to satisfy demands for <xref:System.Security.Permissions.PublisherIdentityPermission> in a partial-trust environment.</span></span> <span data-ttu-id="13ed5-132">(As demandas de permissões de identidade sempre tiveram sucesso em um ambiente de confiança total.)</span><span class="sxs-lookup"><span data-stu-id="13ed5-132">(Demands for identity permissions always succeed in a full-trust environment.)</span></span>  
  
> [!NOTE]
> <span data-ttu-id="13ed5-133">Recomendamos que os serviços usem o `<generatePublisherEvidence>` elemento para melhorar o desempenho de inicialização.</span><span class="sxs-lookup"><span data-stu-id="13ed5-133">We recommend that services use the `<generatePublisherEvidence>` element to improve startup performance.</span></span>  <span data-ttu-id="13ed5-134">O uso desse elemento também pode ajudar a evitar atrasos que podem causar um tempo limite e o cancelamento da inicialização do serviço.</span><span class="sxs-lookup"><span data-stu-id="13ed5-134">Using this element can also help avoid delays that can cause a time-out and the cancellation of the service startup.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="13ed5-135">Arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="13ed5-135">Configuration File</span></span>  
 <span data-ttu-id="13ed5-136">Esse elemento só pode ser usado no arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="13ed5-136">This element can be used only in the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="13ed5-137">Exemplo</span><span class="sxs-lookup"><span data-stu-id="13ed5-137">Example</span></span>  
 <span data-ttu-id="13ed5-138">O exemplo a seguir mostra como usar o `<generatePublisherEvidence>` elemento para desabilitar a verificação da política de editor de CAS para um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="13ed5-138">The following example shows how to use the `<generatePublisherEvidence>` element to disable checking for CAS publisher policy for an application.</span></span>  
  
```xml  
<configuration>  
    <runtime>  
        <generatePublisherEvidence enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="13ed5-139">Confira também</span><span class="sxs-lookup"><span data-stu-id="13ed5-139">See also</span></span>

- [<span data-ttu-id="13ed5-140">Esquema de configurações do runtime</span><span class="sxs-lookup"><span data-stu-id="13ed5-140">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="13ed5-141">Esquema do arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="13ed5-141">Configuration File Schema</span></span>](../index.md)
