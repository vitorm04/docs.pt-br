---
title: Elemento <generatePublisherEvidence>
ms.date: 03/30/2017
helpviewer_keywords:
- generatePublisherEvidence element
- <generatePublisherEvidence> element
ms.assetid: 7d208f50-e8d5-4a42-bc1a-1cf3590706a8
ms.openlocfilehash: c2ba4a7244b7849e28eac38fb34a2cdd0d1f1048
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645353"
---
# <a name="generatepublisherevidence-element"></a><span data-ttu-id="bf8af-102">\<Elemento generatePublisherEvidence ></span><span class="sxs-lookup"><span data-stu-id="bf8af-102">\<generatePublisherEvidence> Element</span></span>
<span data-ttu-id="bf8af-103">Especifica se o tempo <xref:System.Security.Policy.Publisher> de execução cria evidências para o segurança de acesso ao código (CAS).</span><span class="sxs-lookup"><span data-stu-id="bf8af-103">Specifies whether the runtime creates <xref:System.Security.Policy.Publisher> evidence for code access security (CAS).</span></span>  
  
<span data-ttu-id="bf8af-104">[**\<>de configuração**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="bf8af-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="bf8af-105">&nbsp;&nbsp;[**\<>de tempo de execução**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="bf8af-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="bf8af-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<gerar>de evidências do Publisher**</span><span class="sxs-lookup"><span data-stu-id="bf8af-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<generatePublisherEvidence>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf8af-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bf8af-107">Syntax</span></span>  
  
```xml  
<generatePublisherEvidence
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bf8af-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="bf8af-108">Attributes and Elements</span></span>  
 <span data-ttu-id="bf8af-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="bf8af-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bf8af-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="bf8af-110">Attributes</span></span>  
  
|<span data-ttu-id="bf8af-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="bf8af-111">Attribute</span></span>|<span data-ttu-id="bf8af-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="bf8af-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="bf8af-113">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="bf8af-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="bf8af-114">Especifica se o tempo <xref:System.Security.Policy.Publisher> de execução cria evidências.</span><span class="sxs-lookup"><span data-stu-id="bf8af-114">Specifies whether the runtime creates <xref:System.Security.Policy.Publisher> evidence.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="bf8af-115">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="bf8af-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="bf8af-116">Valor</span><span class="sxs-lookup"><span data-stu-id="bf8af-116">Value</span></span>|<span data-ttu-id="bf8af-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="bf8af-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="bf8af-118">Não cria <xref:System.Security.Policy.Publisher> evidências.</span><span class="sxs-lookup"><span data-stu-id="bf8af-118">Does not create <xref:System.Security.Policy.Publisher> evidence.</span></span>|  
|`true`|<span data-ttu-id="bf8af-119">Cria <xref:System.Security.Policy.Publisher> evidências.</span><span class="sxs-lookup"><span data-stu-id="bf8af-119">Creates <xref:System.Security.Policy.Publisher> evidence.</span></span> <span data-ttu-id="bf8af-120">Esse é o padrão.</span><span class="sxs-lookup"><span data-stu-id="bf8af-120">This is the default.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bf8af-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="bf8af-121">Child Elements</span></span>  
 <span data-ttu-id="bf8af-122">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="bf8af-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bf8af-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="bf8af-123">Parent Elements</span></span>  
  
|<span data-ttu-id="bf8af-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="bf8af-124">Element</span></span>|<span data-ttu-id="bf8af-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="bf8af-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="bf8af-126">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="bf8af-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="bf8af-127">Contém informações sobre opções de inicialização do runtime.</span><span class="sxs-lookup"><span data-stu-id="bf8af-127">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bf8af-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="bf8af-128">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bf8af-129">No Quadro .NET 4 e posterior, este elemento não tem efeito nos tempos de carga de montagem.</span><span class="sxs-lookup"><span data-stu-id="bf8af-129">In the .NET Framework 4 and later, this element has no effect on assembly load times.</span></span> <span data-ttu-id="bf8af-130">Para obter mais informações, consulte a seção "Simplificação de políticas de segurança" em [Alterações de Segurança](https://docs.microsoft.com/previous-versions/dotnet/framework/security/security-changes).</span><span class="sxs-lookup"><span data-stu-id="bf8af-130">For more information, see the "Security Policy Simplification" section in [Security Changes](https://docs.microsoft.com/previous-versions/dotnet/framework/security/security-changes).</span></span>  
  
 <span data-ttu-id="bf8af-131">O tempo de execução do idioma comum (CLR) tenta <xref:System.Security.Policy.Publisher> verificar a assinatura Authenticode na hora da carga para criar evidências para a montagem.</span><span class="sxs-lookup"><span data-stu-id="bf8af-131">The common language runtime (CLR) tries to verify the Authenticode signature at load time to create <xref:System.Security.Policy.Publisher> evidence for the assembly.</span></span> <span data-ttu-id="bf8af-132">No entanto, por padrão, <xref:System.Security.Policy.Publisher> a maioria dos aplicativos não precisa de provas.</span><span class="sxs-lookup"><span data-stu-id="bf8af-132">However, by default, most applications do not need <xref:System.Security.Policy.Publisher> evidence.</span></span> <span data-ttu-id="bf8af-133">A política CAS padrão <xref:System.Security.Policy.PublisherMembershipCondition>não depende do .</span><span class="sxs-lookup"><span data-stu-id="bf8af-133">Standard CAS policy does not rely on the <xref:System.Security.Policy.PublisherMembershipCondition>.</span></span> <span data-ttu-id="bf8af-134">Você deve evitar o custo de inicialização desnecessário associado à verificação da assinatura do editor, a <xref:System.Security.Permissions.PublisherIdentityPermission> menos que seu aplicativo seja executado em um computador com política CAS personalizada ou esteja pretendendo satisfazer demandas em um ambiente de confiança parcial.</span><span class="sxs-lookup"><span data-stu-id="bf8af-134">You should avoid the unnecessary startup cost associated with verifying the publisher signature unless your application executes on a computer with custom CAS policy, or is intending to satisfy demands for <xref:System.Security.Permissions.PublisherIdentityPermission> in a partial-trust environment.</span></span> <span data-ttu-id="bf8af-135">(Demandas por permissões de identidade sempre têm sucesso em um ambiente de confiança total.)</span><span class="sxs-lookup"><span data-stu-id="bf8af-135">(Demands for identity permissions always succeed in a full-trust environment.)</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bf8af-136">Recomendamos que os `<generatePublisherEvidence>` serviços usem o elemento para melhorar o desempenho da inicialização.</span><span class="sxs-lookup"><span data-stu-id="bf8af-136">We recommend that services use the `<generatePublisherEvidence>` element to improve startup performance.</span></span>  <span data-ttu-id="bf8af-137">O uso desse elemento também pode ajudar a evitar atrasos que podem causar um intervalo e o cancelamento da inicialização do serviço.</span><span class="sxs-lookup"><span data-stu-id="bf8af-137">Using this element can also help avoid delays that can cause a time-out and the cancellation of the service startup.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="bf8af-138">Arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="bf8af-138">Configuration File</span></span>  
 <span data-ttu-id="bf8af-139">Este elemento só pode ser usado no arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="bf8af-139">This element can be used only in the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bf8af-140">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bf8af-140">Example</span></span>  
 <span data-ttu-id="bf8af-141">O exemplo a seguir `<generatePublisherEvidence>` mostra como usar o elemento para desativar a verificação da política do editor CAS para um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="bf8af-141">The following example shows how to use the `<generatePublisherEvidence>` element to disable checking for CAS publisher policy for an application.</span></span>  
  
```xml  
<configuration>  
    <runtime>  
        <generatePublisherEvidence enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="bf8af-142">Confira também</span><span class="sxs-lookup"><span data-stu-id="bf8af-142">See also</span></span>

- [<span data-ttu-id="bf8af-143">Esquema de configurações em tempo de execução</span><span class="sxs-lookup"><span data-stu-id="bf8af-143">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="bf8af-144">Esquema de arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="bf8af-144">Configuration File Schema</span></span>](../index.md)
