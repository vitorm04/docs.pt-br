---
title: <legacyImpersonationPolicy> Elemento
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
ms.openlocfilehash: c39ee551dde19d87a75403f3db7433d1ef829f3b
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59333984"
---
# <a name="legacyimpersonationpolicy-element"></a><span data-ttu-id="0ea6f-102">\<legacyImpersonationPolicy > elemento</span><span class="sxs-lookup"><span data-stu-id="0ea6f-102">\<legacyImpersonationPolicy> Element</span></span>
<span data-ttu-id="0ea6f-103">Especifica que a identidade do Windows não flua entre pontos assíncronos, independentemente das configurações de fluxo para o contexto de execução no thread atual.</span><span class="sxs-lookup"><span data-stu-id="0ea6f-103">Specifies that the Windows identity does not flow across asynchronous points, regardless of the flow settings for the execution context on the current thread.</span></span>  
  
 <span data-ttu-id="0ea6f-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="0ea6f-104">\<configuration></span></span>  
<span data-ttu-id="0ea6f-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="0ea6f-105">\<runtime></span></span>  
<span data-ttu-id="0ea6f-106">\<legacyImpersonationPolicy></span><span class="sxs-lookup"><span data-stu-id="0ea6f-106">\<legacyImpersonationPolicy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ea6f-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0ea6f-107">Syntax</span></span>  
  
```xml  
<legacyImpersonationPolicy    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0ea6f-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="0ea6f-108">Attributes and Elements</span></span>  
 <span data-ttu-id="0ea6f-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="0ea6f-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0ea6f-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="0ea6f-110">Attributes</span></span>  
  
|<span data-ttu-id="0ea6f-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="0ea6f-111">Attribute</span></span>|<span data-ttu-id="0ea6f-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ea6f-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="0ea6f-113">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="0ea6f-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="0ea6f-114">Especifica que o <xref:System.Security.Principal.WindowsIdentity> não flua entre pontos assíncronos, independentemente do <xref:System.Threading.ExecutionContext> configurações no thread atual de fluxo.</span><span class="sxs-lookup"><span data-stu-id="0ea6f-114">Specifies that the <xref:System.Security.Principal.WindowsIdentity> does not flow across asynchronous points, regardless of the <xref:System.Threading.ExecutionContext> flow settings on the current thread.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="0ea6f-115">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="0ea6f-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="0ea6f-116">Valor</span><span class="sxs-lookup"><span data-stu-id="0ea6f-116">Value</span></span>|<span data-ttu-id="0ea6f-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ea6f-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<xref:System.Security.Principal.WindowsIdentity> <span data-ttu-id="0ea6f-118">fluxos entre pontos assíncronos de acordo com o <xref:System.Threading.ExecutionContext> configurações para o thread atual de fluxo.</span><span class="sxs-lookup"><span data-stu-id="0ea6f-118">flows across asynchronous points depending upon the <xref:System.Threading.ExecutionContext> flow settings for the current thread.</span></span> <span data-ttu-id="0ea6f-119">Esse é o padrão.</span><span class="sxs-lookup"><span data-stu-id="0ea6f-119">This is the default.</span></span>|  
|`true`|<xref:System.Security.Principal.WindowsIdentity> <span data-ttu-id="0ea6f-120">não flua entre pontos assíncronos, independentemente do <xref:System.Threading.ExecutionContext> configurações no thread atual de fluxo.</span><span class="sxs-lookup"><span data-stu-id="0ea6f-120">does not flow across asynchronous points, regardless of the <xref:System.Threading.ExecutionContext> flow settings on the current thread.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0ea6f-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="0ea6f-121">Child Elements</span></span>  
 <span data-ttu-id="0ea6f-122">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="0ea6f-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0ea6f-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="0ea6f-123">Parent Elements</span></span>  
  
|<span data-ttu-id="0ea6f-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="0ea6f-124">Element</span></span>|<span data-ttu-id="0ea6f-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="0ea6f-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="0ea6f-126">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0ea6f-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="0ea6f-127">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="0ea6f-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0ea6f-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="0ea6f-128">Remarks</span></span>  
 <span data-ttu-id="0ea6f-129">Nas versões do .NET Framework 1.0 e 1.1, o <xref:System.Security.Principal.WindowsIdentity> não flua entre quaisquer pontos assíncronos definidos pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="0ea6f-129">In the .NET Framework versions 1.0 and 1.1, the <xref:System.Security.Principal.WindowsIdentity> does not flow across any user-defined asynchronous points.</span></span> <span data-ttu-id="0ea6f-130">Começando com o .NET Framework versão 2.0, há um <xref:System.Threading.ExecutionContext> objeto que contém informações sobre o thread em execução no momento e ele flua entre pontos assíncronos dentro de um domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0ea6f-130">Starting with the .NET Framework version 2.0, there is an <xref:System.Threading.ExecutionContext> object that contains information about the currently executing thread, and it flows across asynchronous points within an application domain.</span></span> <span data-ttu-id="0ea6f-131">O <xref:System.Security.Principal.WindowsIdentity> está incluído neste contexto de execução e, portanto, também flui entre pontos assíncronos, que significa que se um contexto de representação existir, ele fará o fluxo também.</span><span class="sxs-lookup"><span data-stu-id="0ea6f-131">The <xref:System.Security.Principal.WindowsIdentity> is included in this execution context and therefore also flows across the asynchronous points, which means that if an impersonation context exists, it will flow as well.</span></span>  
  
 <span data-ttu-id="0ea6f-132">Começando com o .NET Framework 2.0, você pode usar o `<legacyImpersonationPolicy>` elemento para especificar que <xref:System.Security.Principal.WindowsIdentity> não flua entre pontos assíncronos.</span><span class="sxs-lookup"><span data-stu-id="0ea6f-132">Starting with the .NET Framework 2.0, you can use the `<legacyImpersonationPolicy>` element to specify that  <xref:System.Security.Principal.WindowsIdentity> does not flow across asynchronous points.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0ea6f-133">O common language runtime (CLR) está ciente da representação de invocação de operações executadas usando apenas código gerenciado, não de representação executada fora do código gerenciado, como por meio de plataforma para código não gerenciado ou por meio de chamadas diretas a funções do Win32.</span><span class="sxs-lookup"><span data-stu-id="0ea6f-133">The common language runtime (CLR) is aware of impersonation operations performed using only managed code, not of impersonation performed outside of managed code, such as through platform invoke to unmanaged code or through direct calls to Win32 functions.</span></span> <span data-ttu-id="0ea6f-134">Somente gerenciado <xref:System.Security.Principal.WindowsIdentity> objetos possam fluir entre pontos assíncronos, a menos que o `alwaysFlowImpersonationPolicy` elemento tiver sido definido como true (`<alwaysFlowImpersonationPolicy enabled="true"/>`).</span><span class="sxs-lookup"><span data-stu-id="0ea6f-134">Only managed <xref:System.Security.Principal.WindowsIdentity> objects can flow across asynchronous points, unless the `alwaysFlowImpersonationPolicy` element has been set to true (`<alwaysFlowImpersonationPolicy enabled="true"/>`).</span></span> <span data-ttu-id="0ea6f-135">Definindo o `alwaysFlowImpersonationPolicy` elemento como true especifica que a identidade do Windows sempre fluirá por pontos assíncronos, independentemente de como a representação foi executada.</span><span class="sxs-lookup"><span data-stu-id="0ea6f-135">Setting the `alwaysFlowImpersonationPolicy` element to true specifies that the Windows identity always flows across asynchronous points, regardless of how impersonation was performed.</span></span> <span data-ttu-id="0ea6f-136">Para obter mais informações sobre o fluxo não gerenciados a representação entre pontos assíncronos, consulte [ \<alwaysFlowImpersonationPolicy > elemento](../../../../../docs/framework/configure-apps/file-schema/runtime/alwaysflowimpersonationpolicy-element.md).</span><span class="sxs-lookup"><span data-stu-id="0ea6f-136">For more information on flowing unmanaged impersonation across asynchronous points, see [\<alwaysFlowImpersonationPolicy> Element](../../../../../docs/framework/configure-apps/file-schema/runtime/alwaysflowimpersonationpolicy-element.md).</span></span>  
  
 <span data-ttu-id="0ea6f-137">Você pode alterar esse comportamento padrão de outras duas maneiras:</span><span class="sxs-lookup"><span data-stu-id="0ea6f-137">You can alter this default behavior in two other ways:</span></span>  
  
1. <span data-ttu-id="0ea6f-138">No código gerenciado em uma base por thread.</span><span class="sxs-lookup"><span data-stu-id="0ea6f-138">In managed code on a per-thread basis.</span></span>  
  
     <span data-ttu-id="0ea6f-139">Você pode suprimir o fluxo em uma base por thread, modificando o <xref:System.Threading.ExecutionContext> e <xref:System.Security.SecurityContext> as configurações usando o <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>, <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType> ou <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> método.</span><span class="sxs-lookup"><span data-stu-id="0ea6f-139">You can suppress the flow on a per-thread basis by modifying the <xref:System.Threading.ExecutionContext> and <xref:System.Security.SecurityContext> settings by using the <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>, <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType> or <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> method.</span></span>  
  
2. <span data-ttu-id="0ea6f-140">Na chamada para a interface de hospedagem não gerenciada para carregar o common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="0ea6f-140">In the call to the unmanaged hosting interface to load the common language runtime (CLR).</span></span>  
  
     <span data-ttu-id="0ea6f-141">Se uma interface de hospedagem não gerenciada (em vez de um executável gerenciado simple) é usada para carregar o CLR, você pode especificar um sinalizador especial na chamada para o [função CorBindToRuntimeEx](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) função.</span><span class="sxs-lookup"><span data-stu-id="0ea6f-141">If an unmanaged hosting interface (instead of a simple managed executable) is used to load the CLR, you can specify a special flag in the call to the [CorBindToRuntimeEx Function](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) function.</span></span> <span data-ttu-id="0ea6f-142">Para habilitar o modo de compatibilidade para todo o processo, defina as `flags` parâmetro para [função CorBindToRuntimeEx](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) para STARTUP_LEGACY_IMPERSONATION.</span><span class="sxs-lookup"><span data-stu-id="0ea6f-142">To enable the compatibility mode for the entire process, set the `flags` parameter for [CorBindToRuntimeEx Function](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) to STARTUP_LEGACY_IMPERSONATION.</span></span>  
  
 <span data-ttu-id="0ea6f-143">Para obter mais informações, consulte o [ \<alwaysFlowImpersonationPolicy > elemento](../../../../../docs/framework/configure-apps/file-schema/runtime/alwaysflowimpersonationpolicy-element.md).</span><span class="sxs-lookup"><span data-stu-id="0ea6f-143">For more information, see the [\<alwaysFlowImpersonationPolicy> Element](../../../../../docs/framework/configure-apps/file-schema/runtime/alwaysflowimpersonationpolicy-element.md).</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="0ea6f-144">Arquivo de Configuração</span><span class="sxs-lookup"><span data-stu-id="0ea6f-144">Configuration File</span></span>  
 <span data-ttu-id="0ea6f-145">Em um aplicativo do .NET Framework, esse elemento pode ser usado apenas no arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0ea6f-145">In a .NET Framework application, this element can be used only in the application configuration file.</span></span>  
  
 <span data-ttu-id="0ea6f-146">Para um aplicativo ASP.NET, o fluxo de representação pode ser configurado no arquivo ASPNET config localizado no \<pasta Windows > \Microsoft.NET\Framework\vx.x.xxxx directory.</span><span class="sxs-lookup"><span data-stu-id="0ea6f-146">For an ASP.NET application, the impersonation flow can be configured in the aspnet.config file found in the \<Windows Folder>\Microsoft.NET\Framework\vx.x.xxxx directory.</span></span>  
  
 <span data-ttu-id="0ea6f-147">ASP.NET por padrão desabilita o fluxo de representação no arquivo ASPNET config usando as seguintes configurações:</span><span class="sxs-lookup"><span data-stu-id="0ea6f-147">ASP.NET by default disables the impersonation flow in the aspnet.config file by using the following configuration settings:</span></span>  
  
``` xml
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
      <alwaysFlowImpersonationPolicy enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="0ea6f-148">No ASP.NET, se você quiser permitir o fluxo de representação em vez disso, você deve usar explicitamente as seguintes configurações:</span><span class="sxs-lookup"><span data-stu-id="0ea6f-148">In ASP.NET, if you want to allow the flow of impersonation instead, you must explicitly use the following configuration settings:</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="false"/>  
      <alwaysFlowImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="example"></a><span data-ttu-id="0ea6f-149">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ea6f-149">Example</span></span>  
 <span data-ttu-id="0ea6f-150">O exemplo a seguir mostra como especificar o comportamento herdado que não passa a identidade do Windows entre pontos assíncronos.</span><span class="sxs-lookup"><span data-stu-id="0ea6f-150">The following example shows how to specify the legacy behavior that does not flow the Windows identity across asynchronous points.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0ea6f-151">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ea6f-151">See also</span></span>

- [<span data-ttu-id="0ea6f-152">Esquema de configurações do tempo de execução</span><span class="sxs-lookup"><span data-stu-id="0ea6f-152">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="0ea6f-153">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="0ea6f-153">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="0ea6f-154">\<alwaysFlowImpersonationPolicy > elemento</span><span class="sxs-lookup"><span data-stu-id="0ea6f-154">\<alwaysFlowImpersonationPolicy> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/alwaysflowimpersonationpolicy-element.md)
