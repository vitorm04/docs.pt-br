---
title: Elemento <legacyImpersonationPolicy>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#legacyImpersonationPolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/legacyImpersonationPolicy
helpviewer_keywords:
- <legacyImpersonationPolicy> element
- legacyImpersonationPolicy element
ms.assetid: 6e00af10-42f3-4235-8415-1bb2db78394e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4cf997c8ff13e0a6a4664ea3b538ac0def1baacf
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663633"
---
# <a name="legacyimpersonationpolicy-element"></a><span data-ttu-id="b9681-102">\<Elemento de > legacyImpersonationPolicy</span><span class="sxs-lookup"><span data-stu-id="b9681-102">\<legacyImpersonationPolicy> Element</span></span>
<span data-ttu-id="b9681-103">Especifica que a identidade do Windows não flua entre pontos assíncronos, independentemente das configurações de fluxo para o contexto de execução no thread atual.</span><span class="sxs-lookup"><span data-stu-id="b9681-103">Specifies that the Windows identity does not flow across asynchronous points, regardless of the flow settings for the execution context on the current thread.</span></span>  
  
 <span data-ttu-id="b9681-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="b9681-104">\<configuration></span></span>  
<span data-ttu-id="b9681-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="b9681-105">\<runtime></span></span>  
<span data-ttu-id="b9681-106">\<legacyImpersonationPolicy></span><span class="sxs-lookup"><span data-stu-id="b9681-106">\<legacyImpersonationPolicy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9681-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b9681-107">Syntax</span></span>  
  
```xml  
<legacyImpersonationPolicy    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b9681-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="b9681-108">Attributes and Elements</span></span>  
 <span data-ttu-id="b9681-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="b9681-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b9681-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="b9681-110">Attributes</span></span>  
  
|<span data-ttu-id="b9681-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="b9681-111">Attribute</span></span>|<span data-ttu-id="b9681-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="b9681-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="b9681-113">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="b9681-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="b9681-114">Especifica que o <xref:System.Security.Principal.WindowsIdentity> não flui em pontos assíncronos, independentemente <xref:System.Threading.ExecutionContext> das configurações de fluxo no thread atual.</span><span class="sxs-lookup"><span data-stu-id="b9681-114">Specifies that the <xref:System.Security.Principal.WindowsIdentity> does not flow across asynchronous points, regardless of the <xref:System.Threading.ExecutionContext> flow settings on the current thread.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="b9681-115">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="b9681-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="b9681-116">Valor</span><span class="sxs-lookup"><span data-stu-id="b9681-116">Value</span></span>|<span data-ttu-id="b9681-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="b9681-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="b9681-118"><xref:System.Security.Principal.WindowsIdentity>flui entre pontos assíncronos, dependendo <xref:System.Threading.ExecutionContext> das configurações de fluxo do thread atual.</span><span class="sxs-lookup"><span data-stu-id="b9681-118"><xref:System.Security.Principal.WindowsIdentity> flows across asynchronous points depending upon the <xref:System.Threading.ExecutionContext> flow settings for the current thread.</span></span> <span data-ttu-id="b9681-119">Esse é o padrão.</span><span class="sxs-lookup"><span data-stu-id="b9681-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="b9681-120"><xref:System.Security.Principal.WindowsIdentity>não flui em pontos assíncronos, independentemente das <xref:System.Threading.ExecutionContext> configurações de fluxo no thread atual.</span><span class="sxs-lookup"><span data-stu-id="b9681-120"><xref:System.Security.Principal.WindowsIdentity> does not flow across asynchronous points, regardless of the <xref:System.Threading.ExecutionContext> flow settings on the current thread.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b9681-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="b9681-121">Child Elements</span></span>  
 <span data-ttu-id="b9681-122">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="b9681-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b9681-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="b9681-123">Parent Elements</span></span>  
  
|<span data-ttu-id="b9681-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="b9681-124">Element</span></span>|<span data-ttu-id="b9681-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="b9681-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="b9681-126">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b9681-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="b9681-127">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="b9681-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b9681-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="b9681-128">Remarks</span></span>  
 <span data-ttu-id="b9681-129">No .NET Framework versões 1,0 e 1,1, o <xref:System.Security.Principal.WindowsIdentity> não flui em nenhum ponto assíncrono definido pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="b9681-129">In the .NET Framework versions 1.0 and 1.1, the <xref:System.Security.Principal.WindowsIdentity> does not flow across any user-defined asynchronous points.</span></span> <span data-ttu-id="b9681-130">A partir do .NET Framework versão 2,0, há um <xref:System.Threading.ExecutionContext> objeto que contém informações sobre o thread em execução no momento e ele flui entre pontos assíncronos dentro de um domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b9681-130">Starting with the .NET Framework version 2.0, there is an <xref:System.Threading.ExecutionContext> object that contains information about the currently executing thread, and it flows across asynchronous points within an application domain.</span></span> <span data-ttu-id="b9681-131">O <xref:System.Security.Principal.WindowsIdentity> é incluído nesse contexto de execução e, portanto, também flui pelos pontos assíncronos, o que significa que, se existir um contexto de representação, ele fluirá também.</span><span class="sxs-lookup"><span data-stu-id="b9681-131">The <xref:System.Security.Principal.WindowsIdentity> is included in this execution context and therefore also flows across the asynchronous points, which means that if an impersonation context exists, it will flow as well.</span></span>  
  
 <span data-ttu-id="b9681-132">Começando com o .NET Framework 2,0, você pode usar o `<legacyImpersonationPolicy>` elemento para especificar que <xref:System.Security.Principal.WindowsIdentity> não flui em pontos assíncronos.</span><span class="sxs-lookup"><span data-stu-id="b9681-132">Starting with the .NET Framework 2.0, you can use the `<legacyImpersonationPolicy>` element to specify that  <xref:System.Security.Principal.WindowsIdentity> does not flow across asynchronous points.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b9681-133">O Common Language Runtime (CLR) reconhece as operações de representação executadas usando apenas código gerenciado, não a representação executada fora do código gerenciado, como por meio de invocação de plataforma para código não gerenciado ou por meio de chamadas diretas para funções do Win32.</span><span class="sxs-lookup"><span data-stu-id="b9681-133">The common language runtime (CLR) is aware of impersonation operations performed using only managed code, not of impersonation performed outside of managed code, such as through platform invoke to unmanaged code or through direct calls to Win32 functions.</span></span> <span data-ttu-id="b9681-134">Somente os <xref:System.Security.Principal.WindowsIdentity> objetos gerenciados podem fluir entre pontos assíncronos, a menos que o `alwaysFlowImpersonationPolicy` elemento`<alwaysFlowImpersonationPolicy enabled="true"/>`tenha sido definido como true ().</span><span class="sxs-lookup"><span data-stu-id="b9681-134">Only managed <xref:System.Security.Principal.WindowsIdentity> objects can flow across asynchronous points, unless the `alwaysFlowImpersonationPolicy` element has been set to true (`<alwaysFlowImpersonationPolicy enabled="true"/>`).</span></span> <span data-ttu-id="b9681-135">Definir o `alwaysFlowImpersonationPolicy` elemento como true Especifica que a identidade do Windows sempre fluirá entre pontos assíncronos, independentemente de como a representação foi executada.</span><span class="sxs-lookup"><span data-stu-id="b9681-135">Setting the `alwaysFlowImpersonationPolicy` element to true specifies that the Windows identity always flows across asynchronous points, regardless of how impersonation was performed.</span></span> <span data-ttu-id="b9681-136">Para obter mais informações sobre como fluir a representação não gerenciada em pontos assíncronos, consulte [ \<alwaysFlowImpersonationPolicy > Element](alwaysflowimpersonationpolicy-element.md).</span><span class="sxs-lookup"><span data-stu-id="b9681-136">For more information on flowing unmanaged impersonation across asynchronous points, see [\<alwaysFlowImpersonationPolicy> Element](alwaysflowimpersonationpolicy-element.md).</span></span>  
  
 <span data-ttu-id="b9681-137">Você pode alterar esse comportamento padrão de duas maneiras:</span><span class="sxs-lookup"><span data-stu-id="b9681-137">You can alter this default behavior in two other ways:</span></span>  
  
1. <span data-ttu-id="b9681-138">Em código gerenciado por thread.</span><span class="sxs-lookup"><span data-stu-id="b9681-138">In managed code on a per-thread basis.</span></span>  
  
     <span data-ttu-id="b9681-139">Você pode suprimir o fluxo por <xref:System.Threading.ExecutionContext> thread modificando as configurações e <xref:System.Security.SecurityContext> usando o <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>método, <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType> ou <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="b9681-139">You can suppress the flow on a per-thread basis by modifying the <xref:System.Threading.ExecutionContext> and <xref:System.Security.SecurityContext> settings by using the <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>, <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType> or <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> method.</span></span>  
  
2. <span data-ttu-id="b9681-140">Na chamada à interface de hospedagem não gerenciada para carregar o Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="b9681-140">In the call to the unmanaged hosting interface to load the common language runtime (CLR).</span></span>  
  
     <span data-ttu-id="b9681-141">Se uma interface de hospedagem não gerenciada (em vez de um executável gerenciado simples) for usada para carregar o CLR, você poderá especificar um sinalizador especial na chamada para a função de [função CorBindToRuntimeEx](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) .</span><span class="sxs-lookup"><span data-stu-id="b9681-141">If an unmanaged hosting interface (instead of a simple managed executable) is used to load the CLR, you can specify a special flag in the call to the [CorBindToRuntimeEx Function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) function.</span></span> <span data-ttu-id="b9681-142">Para habilitar o modo de compatibilidade para todo o processo, defina `flags` o parâmetro para a [função CorBindToRuntimeEx](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) como STARTUP_LEGACY_IMPERSONATION.</span><span class="sxs-lookup"><span data-stu-id="b9681-142">To enable the compatibility mode for the entire process, set the `flags` parameter for [CorBindToRuntimeEx Function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) to STARTUP_LEGACY_IMPERSONATION.</span></span>  
  
 <span data-ttu-id="b9681-143">Para obter mais informações, consulte o [ \<elemento alwaysFlowImpersonationPolicy >](alwaysflowimpersonationpolicy-element.md).</span><span class="sxs-lookup"><span data-stu-id="b9681-143">For more information, see the [\<alwaysFlowImpersonationPolicy> Element](alwaysflowimpersonationpolicy-element.md).</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="b9681-144">Arquivo de Configuração</span><span class="sxs-lookup"><span data-stu-id="b9681-144">Configuration File</span></span>  
 <span data-ttu-id="b9681-145">Em um aplicativo .NET Framework, esse elemento pode ser usado somente no arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b9681-145">In a .NET Framework application, this element can be used only in the application configuration file.</span></span>  
  
 <span data-ttu-id="b9681-146">Para um aplicativo ASP.net, o fluxo de representação pode ser configurado no arquivo Aspnet. config encontrado na pasta \<do Windows > diretório \Microsoft.NET\Framework\vx.x.xxxx.</span><span class="sxs-lookup"><span data-stu-id="b9681-146">For an ASP.NET application, the impersonation flow can be configured in the aspnet.config file found in the \<Windows Folder>\Microsoft.NET\Framework\vx.x.xxxx directory.</span></span>  
  
 <span data-ttu-id="b9681-147">O ASP.NET, por padrão, desabilita o fluxo de representação no arquivo Aspnet. config usando as seguintes definições de configuração:</span><span class="sxs-lookup"><span data-stu-id="b9681-147">ASP.NET by default disables the impersonation flow in the aspnet.config file by using the following configuration settings:</span></span>  
  
``` xml
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
      <alwaysFlowImpersonationPolicy enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="b9681-148">Em ASP.NET, se você quiser permitir o fluxo de representação em vez disso, deverá usar explicitamente as seguintes definições de configuração:</span><span class="sxs-lookup"><span data-stu-id="b9681-148">In ASP.NET, if you want to allow the flow of impersonation instead, you must explicitly use the following configuration settings:</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="false"/>  
      <alwaysFlowImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="example"></a><span data-ttu-id="b9681-149">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b9681-149">Example</span></span>  
 <span data-ttu-id="b9681-150">O exemplo a seguir mostra como especificar o comportamento herdado que não flui a identidade do Windows entre pontos assíncronos.</span><span class="sxs-lookup"><span data-stu-id="b9681-150">The following example shows how to specify the legacy behavior that does not flow the Windows identity across asynchronous points.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b9681-151">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b9681-151">See also</span></span>

- [<span data-ttu-id="b9681-152">Esquema de configurações do tempo de execução</span><span class="sxs-lookup"><span data-stu-id="b9681-152">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="b9681-153">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="b9681-153">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="b9681-154">\<Elemento de > alwaysFlowImpersonationPolicy</span><span class="sxs-lookup"><span data-stu-id="b9681-154">\<alwaysFlowImpersonationPolicy> Element</span></span>](alwaysflowimpersonationpolicy-element.md)
