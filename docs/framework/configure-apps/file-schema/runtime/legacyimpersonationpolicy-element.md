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
ms.openlocfilehash: 5e43ead278ecd4049014f4000a2f056b2190f7e5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154096"
---
# <a name="legacyimpersonationpolicy-element"></a><span data-ttu-id="d37ba-102">\<elemento de> de representação de representação legado</span><span class="sxs-lookup"><span data-stu-id="d37ba-102">\<legacyImpersonationPolicy> Element</span></span>
<span data-ttu-id="d37ba-103">Especifica que a identidade do Windows não flua entre pontos assíncronos, independentemente das configurações de fluxo para o contexto de execução no thread atual.</span><span class="sxs-lookup"><span data-stu-id="d37ba-103">Specifies that the Windows identity does not flow across asynchronous points, regardless of the flow settings for the execution context on the current thread.</span></span>  
  
<span data-ttu-id="d37ba-104">[**\<>de configuração**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="d37ba-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="d37ba-105">&nbsp;&nbsp;[**\<>de tempo de execução**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="d37ba-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="d37ba-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<legadoRepresentaçãoPolítica>**</span><span class="sxs-lookup"><span data-stu-id="d37ba-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<legacyImpersonationPolicy>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d37ba-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d37ba-107">Syntax</span></span>  
  
```xml  
<legacyImpersonationPolicy
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d37ba-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="d37ba-108">Attributes and Elements</span></span>  
 <span data-ttu-id="d37ba-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="d37ba-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d37ba-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="d37ba-110">Attributes</span></span>  
  
|<span data-ttu-id="d37ba-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="d37ba-111">Attribute</span></span>|<span data-ttu-id="d37ba-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="d37ba-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="d37ba-113">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="d37ba-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="d37ba-114">Especifica que <xref:System.Security.Principal.WindowsIdentity> o fluxo não flui através de pontos <xref:System.Threading.ExecutionContext> assíncronos, independentemente das configurações de fluxo no segmento atual.</span><span class="sxs-lookup"><span data-stu-id="d37ba-114">Specifies that the <xref:System.Security.Principal.WindowsIdentity> does not flow across asynchronous points, regardless of the <xref:System.Threading.ExecutionContext> flow settings on the current thread.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="d37ba-115">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="d37ba-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="d37ba-116">Valor</span><span class="sxs-lookup"><span data-stu-id="d37ba-116">Value</span></span>|<span data-ttu-id="d37ba-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="d37ba-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="d37ba-118"><xref:System.Security.Principal.WindowsIdentity>flui através de pontos assíncronos, dependendo das <xref:System.Threading.ExecutionContext> configurações de fluxo para o segmento atual.</span><span class="sxs-lookup"><span data-stu-id="d37ba-118"><xref:System.Security.Principal.WindowsIdentity> flows across asynchronous points depending upon the <xref:System.Threading.ExecutionContext> flow settings for the current thread.</span></span> <span data-ttu-id="d37ba-119">Esse é o padrão.</span><span class="sxs-lookup"><span data-stu-id="d37ba-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="d37ba-120"><xref:System.Security.Principal.WindowsIdentity>não flui através de pontos assíncronos, independentemente das <xref:System.Threading.ExecutionContext> configurações de fluxo no segmento atual.</span><span class="sxs-lookup"><span data-stu-id="d37ba-120"><xref:System.Security.Principal.WindowsIdentity> does not flow across asynchronous points, regardless of the <xref:System.Threading.ExecutionContext> flow settings on the current thread.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d37ba-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="d37ba-121">Child Elements</span></span>  
 <span data-ttu-id="d37ba-122">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="d37ba-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d37ba-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="d37ba-123">Parent Elements</span></span>  
  
|<span data-ttu-id="d37ba-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="d37ba-124">Element</span></span>|<span data-ttu-id="d37ba-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="d37ba-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="d37ba-126">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d37ba-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="d37ba-127">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="d37ba-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d37ba-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="d37ba-128">Remarks</span></span>  
 <span data-ttu-id="d37ba-129">Nas versões .NET Framework 1.0 <xref:System.Security.Principal.WindowsIdentity> e 1.1, o fluxo não flui em nenhum ponto assíncrono definido pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="d37ba-129">In the .NET Framework versions 1.0 and 1.1, the <xref:System.Security.Principal.WindowsIdentity> does not flow across any user-defined asynchronous points.</span></span> <span data-ttu-id="d37ba-130">Começando com a versão 2.0 do <xref:System.Threading.ExecutionContext> .NET Framework, há um objeto que contém informações sobre o segmento em execução atualmente, e ele flui através de pontos assíncronos dentro de um domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d37ba-130">Starting with the .NET Framework version 2.0, there is an <xref:System.Threading.ExecutionContext> object that contains information about the currently executing thread, and it flows across asynchronous points within an application domain.</span></span> <span data-ttu-id="d37ba-131">O <xref:System.Security.Principal.WindowsIdentity> está incluído neste contexto de execução e, portanto, também flui através dos pontos assíncronos, o que significa que se existe um contexto de personificação, ele fluirá também.</span><span class="sxs-lookup"><span data-stu-id="d37ba-131">The <xref:System.Security.Principal.WindowsIdentity> is included in this execution context and therefore also flows across the asynchronous points, which means that if an impersonation context exists, it will flow as well.</span></span>  
  
 <span data-ttu-id="d37ba-132">Começando com o .NET Framework 2.0, você pode usar o `<legacyImpersonationPolicy>` elemento para especificar que <xref:System.Security.Principal.WindowsIdentity> não flui entre pontos assíncronos.</span><span class="sxs-lookup"><span data-stu-id="d37ba-132">Starting with the .NET Framework 2.0, you can use the `<legacyImpersonationPolicy>` element to specify that  <xref:System.Security.Principal.WindowsIdentity> does not flow across asynchronous points.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d37ba-133">O tempo de execução da linguagem comum (CLR) está ciente das operações de personificação realizadas usando apenas código gerenciado, não de personificação realizada fora do código gerenciado, como através da invocação da plataforma para código não gerenciado ou através de chamadas diretas para funções Win32.</span><span class="sxs-lookup"><span data-stu-id="d37ba-133">The common language runtime (CLR) is aware of impersonation operations performed using only managed code, not of impersonation performed outside of managed code, such as through platform invoke to unmanaged code or through direct calls to Win32 functions.</span></span> <span data-ttu-id="d37ba-134">Somente objetos gerenciados <xref:System.Security.Principal.WindowsIdentity> podem fluir através de `alwaysFlowImpersonationPolicy` pontos assíncronos, a menos que o elemento tenha sido definido como verdadeiro ().`<alwaysFlowImpersonationPolicy enabled="true"/>`</span><span class="sxs-lookup"><span data-stu-id="d37ba-134">Only managed <xref:System.Security.Principal.WindowsIdentity> objects can flow across asynchronous points, unless the `alwaysFlowImpersonationPolicy` element has been set to true (`<alwaysFlowImpersonationPolicy enabled="true"/>`).</span></span> <span data-ttu-id="d37ba-135">Definir `alwaysFlowImpersonationPolicy` o elemento como verdadeiro especifica que a identidade do Windows sempre flui através de pontos assíncronos, independentemente de como a personificação foi realizada.</span><span class="sxs-lookup"><span data-stu-id="d37ba-135">Setting the `alwaysFlowImpersonationPolicy` element to true specifies that the Windows identity always flows across asynchronous points, regardless of how impersonation was performed.</span></span> <span data-ttu-id="d37ba-136">Para obter mais informações sobre a representação não gerenciada em pontos assíncronos, consulte [ \<alwaysFlowImpersonationPolicy> Element](alwaysflowimpersonationpolicy-element.md).</span><span class="sxs-lookup"><span data-stu-id="d37ba-136">For more information on flowing unmanaged impersonation across asynchronous points, see [\<alwaysFlowImpersonationPolicy> Element](alwaysflowimpersonationpolicy-element.md).</span></span>  
  
 <span data-ttu-id="d37ba-137">Você pode alterar esse comportamento padrão de duas outras maneiras:</span><span class="sxs-lookup"><span data-stu-id="d37ba-137">You can alter this default behavior in two other ways:</span></span>  
  
1. <span data-ttu-id="d37ba-138">Em código gerenciado por segmento.</span><span class="sxs-lookup"><span data-stu-id="d37ba-138">In managed code on a per-thread basis.</span></span>  
  
     <span data-ttu-id="d37ba-139">Você pode suprimir o fluxo por segmento modificando <xref:System.Threading.ExecutionContext> as configurações <xref:System.Security.SecurityContext> <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType> usando <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> o <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>método ou método .</span><span class="sxs-lookup"><span data-stu-id="d37ba-139">You can suppress the flow on a per-thread basis by modifying the <xref:System.Threading.ExecutionContext> and <xref:System.Security.SecurityContext> settings by using the <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>, <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType> or <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> method.</span></span>  
  
2. <span data-ttu-id="d37ba-140">Na chamada para a interface de hospedagem não gerenciada para carregar o tempo de execução do idioma comum (CLR).</span><span class="sxs-lookup"><span data-stu-id="d37ba-140">In the call to the unmanaged hosting interface to load the common language runtime (CLR).</span></span>  
  
     <span data-ttu-id="d37ba-141">Se uma interface de hospedagem não gerenciada (em vez de um executável gerenciado simples) for usada para carregar o CLR, você poderá especificar um sinalizador especial na chamada para a função [CorBindToRuntimeEx.](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)</span><span class="sxs-lookup"><span data-stu-id="d37ba-141">If an unmanaged hosting interface (instead of a simple managed executable) is used to load the CLR, you can specify a special flag in the call to the [CorBindToRuntimeEx Function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) function.</span></span> <span data-ttu-id="d37ba-142">Para habilitar o modo de compatibilidade `flags` para todo o processo, defina o parâmetro para [corBindToRuntimeEx function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) para STARTUP_LEGACY_IMPERSONATION.</span><span class="sxs-lookup"><span data-stu-id="d37ba-142">To enable the compatibility mode for the entire process, set the `flags` parameter for [CorBindToRuntimeEx Function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) to STARTUP_LEGACY_IMPERSONATION.</span></span>  
  
 <span data-ttu-id="d37ba-143">Para obter mais informações, consulte o [ \<elemento de> alwaysFlowImpersonationPolicy](alwaysflowimpersonationpolicy-element.md).</span><span class="sxs-lookup"><span data-stu-id="d37ba-143">For more information, see the [\<alwaysFlowImpersonationPolicy> Element](alwaysflowimpersonationpolicy-element.md).</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="d37ba-144">Arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="d37ba-144">Configuration File</span></span>  
 <span data-ttu-id="d37ba-145">Em um aplicativo .NET Framework, esse elemento só pode ser usado no arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d37ba-145">In a .NET Framework application, this element can be used only in the application configuration file.</span></span>  
  
 <span data-ttu-id="d37ba-146">Para um aplicativo ASP.NET, o fluxo de personificação pode ser configurado no \<diretório aspnet.config encontrado no diretório Windows Folder>\Microsoft.NET\Framework\vx.xxxx.</span><span class="sxs-lookup"><span data-stu-id="d37ba-146">For an ASP.NET application, the impersonation flow can be configured in the aspnet.config file found in the \<Windows Folder>\Microsoft.NET\Framework\vx.x.xxxx directory.</span></span>  
  
 <span data-ttu-id="d37ba-147">ASP.NET por padrão desativa o fluxo de personificação no arquivo aspnet.config usando as seguintes configurações:</span><span class="sxs-lookup"><span data-stu-id="d37ba-147">ASP.NET by default disables the impersonation flow in the aspnet.config file by using the following configuration settings:</span></span>  
  
``` xml
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
      <alwaysFlowImpersonationPolicy enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="d37ba-148">Em ASP.NET, se você quiser permitir o fluxo de personificação, em vez disso, você deve usar explicitamente as seguintes configurações:</span><span class="sxs-lookup"><span data-stu-id="d37ba-148">In ASP.NET, if you want to allow the flow of impersonation instead, you must explicitly use the following configuration settings:</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="false"/>  
      <alwaysFlowImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="example"></a><span data-ttu-id="d37ba-149">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d37ba-149">Example</span></span>  
 <span data-ttu-id="d37ba-150">O exemplo a seguir mostra como especificar o comportamento legado que não flui a identidade do Windows em pontos assíncronos.</span><span class="sxs-lookup"><span data-stu-id="d37ba-150">The following example shows how to specify the legacy behavior that does not flow the Windows identity across asynchronous points.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d37ba-151">Confira também</span><span class="sxs-lookup"><span data-stu-id="d37ba-151">See also</span></span>

- [<span data-ttu-id="d37ba-152">Esquema de configurações do runtime</span><span class="sxs-lookup"><span data-stu-id="d37ba-152">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="d37ba-153">Esquema de arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="d37ba-153">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="d37ba-154">\<alwaysFlowImpersonationPolicy> Element</span><span class="sxs-lookup"><span data-stu-id="d37ba-154">\<alwaysFlowImpersonationPolicy> Element</span></span>](alwaysflowimpersonationpolicy-element.md)
