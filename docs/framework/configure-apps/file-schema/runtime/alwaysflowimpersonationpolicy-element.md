---
title: Elemento <alwaysFlowImpersonationPolicy>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/alwaysFlowImpersonationPolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#alwaysFlowImpersonationPolicy
helpviewer_keywords:
- alwaysFlowImpersonationPolicy element
- <alwaysFlowImpersonationPolicy> element
ms.assetid: ee622801-9e46-470b-85ab-88c4b1dd2ee1
ms.openlocfilehash: 7c8ac37932a528ff0f000cbaab49124dec51b88c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154477"
---
# <a name="alwaysflowimpersonationpolicy-element"></a><span data-ttu-id="bf19b-102">\<alwaysFlowImpersonationPolicy> Element</span><span class="sxs-lookup"><span data-stu-id="bf19b-102">\<alwaysFlowImpersonationPolicy> Element</span></span>
<span data-ttu-id="bf19b-103">Especifica que a identidade do Windows sempre fluirá por pontos assíncronos, independentemente de como a representação tenha sido executada.</span><span class="sxs-lookup"><span data-stu-id="bf19b-103">Specifies that the Windows identity always flows across asynchronous points, regardless of how impersonation was performed.</span></span>  
  
<span data-ttu-id="bf19b-104">[**\<>de configuração**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="bf19b-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="bf19b-105">&nbsp;&nbsp;[**\<>de tempo de execução**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="bf19b-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="bf19b-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<alwaysFlowPersonionPolicy>**</span><span class="sxs-lookup"><span data-stu-id="bf19b-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<alwaysFlowImpersonationPolicy>**</span></span>\  
  
## <a name="syntax"></a><span data-ttu-id="bf19b-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bf19b-107">Syntax</span></span>  
  
```xml  
<alwaysFlowImpersonationPolicy
  enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bf19b-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="bf19b-108">Attributes and Elements</span></span>  
 <span data-ttu-id="bf19b-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="bf19b-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bf19b-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="bf19b-110">Attributes</span></span>  
  
|<span data-ttu-id="bf19b-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="bf19b-111">Attribute</span></span>|<span data-ttu-id="bf19b-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="bf19b-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="bf19b-113">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="bf19b-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="bf19b-114">Indica se a identidade do Windows flui através de pontos assíncronos.</span><span class="sxs-lookup"><span data-stu-id="bf19b-114">Indicates whether the Windows identity flows across asynchronous points.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="bf19b-115">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="bf19b-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="bf19b-116">Valor</span><span class="sxs-lookup"><span data-stu-id="bf19b-116">Value</span></span>|<span data-ttu-id="bf19b-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="bf19b-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="bf19b-118">A identidade do Windows não flui através de pontos assíncronos, a <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A>menos que a personificação seja realizada através de métodos gerenciados como .</span><span class="sxs-lookup"><span data-stu-id="bf19b-118">The Windows identity does not flow across asynchronous points, unless the impersonation is performed through managed methods such as <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A>.</span></span> <span data-ttu-id="bf19b-119">Esse é o padrão.</span><span class="sxs-lookup"><span data-stu-id="bf19b-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="bf19b-120">A identidade do Windows sempre flui através de pontos assíncronos, independentemente de como a representação foi realizada.</span><span class="sxs-lookup"><span data-stu-id="bf19b-120">The Windows identity always flows across asynchronous points, regardless of how impersonation was performed.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bf19b-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="bf19b-121">Child Elements</span></span>  
 <span data-ttu-id="bf19b-122">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="bf19b-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bf19b-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="bf19b-123">Parent Elements</span></span>  
  
|<span data-ttu-id="bf19b-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="bf19b-124">Element</span></span>|<span data-ttu-id="bf19b-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="bf19b-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="bf19b-126">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="bf19b-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="bf19b-127">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="bf19b-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bf19b-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="bf19b-128">Remarks</span></span>  
 <span data-ttu-id="bf19b-129">Nas versões .NET Framework 1.0 e 1.1, a identidade do Windows não flui através de pontos assíncronos.</span><span class="sxs-lookup"><span data-stu-id="bf19b-129">In the .NET Framework versions 1.0 and 1.1, the Windows identity does not flow across asynchronous points.</span></span> <span data-ttu-id="bf19b-130">Na versão 2.0 do .NET <xref:System.Threading.ExecutionContext> Framework, há um objeto que contém informações sobre o segmento em execução atualmente e flui-os através de pontos assíncronos dentro de um domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="bf19b-130">In the .NET Framework version 2.0, there is an <xref:System.Threading.ExecutionContext> object that contains information about the currently executing thread, and flows it across asynchronous points within an application domain.</span></span> <span data-ttu-id="bf19b-131">O <xref:System.Security.Principal.WindowsIdentity> fluxo também flui como parte das informações que fluem através dos pontos assíncronos, <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> desde que a personificação tenha sido alcançada usando métodos gerenciados como e não por outros meios, como a invocação da plataforma para métodos nativos.</span><span class="sxs-lookup"><span data-stu-id="bf19b-131">The <xref:System.Security.Principal.WindowsIdentity> also flows as part of the information that flows across the asynchronous points, provided the impersonation was achieved using managed methods such as <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> and not through other means such as platform invoke to native methods.</span></span> <span data-ttu-id="bf19b-132">Este elemento é usado para especificar que a identidade do Windows flui através de pontos assíncronos, independentemente de como a personificação foi alcançada.</span><span class="sxs-lookup"><span data-stu-id="bf19b-132">This element is used to specify that the Windows identity does flow across asynchronous points, regardless of how the impersonation was achieved.</span></span>  
  
 <span data-ttu-id="bf19b-133">Você pode alterar esse comportamento padrão de duas outras maneiras:</span><span class="sxs-lookup"><span data-stu-id="bf19b-133">You can alter this default behavior in two other ways:</span></span>  
  
1. <span data-ttu-id="bf19b-134">Em código gerenciado por segmento.</span><span class="sxs-lookup"><span data-stu-id="bf19b-134">In managed code on a per-thread basis.</span></span>  
  
     <span data-ttu-id="bf19b-135">Você pode suprimir o fluxo por segmento modificando <xref:System.Threading.ExecutionContext> as configurações <xref:System.Security.SecurityContext> <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType>usando <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> o <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>método , ou método.</span><span class="sxs-lookup"><span data-stu-id="bf19b-135">You can suppress the flow on a per-thread basis by modifying the <xref:System.Threading.ExecutionContext> and <xref:System.Security.SecurityContext> settings by using the <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>, <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType>, or <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> method.</span></span>  
  
2. <span data-ttu-id="bf19b-136">Na chamada para a interface de hospedagem não gerenciada para carregar o tempo de execução do idioma comum (CLR).</span><span class="sxs-lookup"><span data-stu-id="bf19b-136">In the call to the unmanaged hosting interface to load the common language runtime (CLR).</span></span>  
  
     <span data-ttu-id="bf19b-137">Se uma interface de hospedagem não gerenciada (em vez de um executável gerenciado simples) for usada para carregar o CLR, você poderá especificar um sinalizador especial na chamada para a função [CorBindToRuntimeEx.](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)</span><span class="sxs-lookup"><span data-stu-id="bf19b-137">If an unmanaged hosting interface (instead of a simple managed executable) is used to load the CLR, you can specify a special flag in the call to the [CorBindToRuntimeEx Function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) function.</span></span> <span data-ttu-id="bf19b-138">Para habilitar o modo de compatibilidade `flags` para todo o processo, defina `STARTUP_ALWAYSFLOW_IMPERSONATION`o parâmetro para [CorBindToRuntimeEx Function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) para .</span><span class="sxs-lookup"><span data-stu-id="bf19b-138">To enable the compatibility mode for the entire process, set the `flags` parameter for [CorBindToRuntimeEx Function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) to `STARTUP_ALWAYSFLOW_IMPERSONATION`.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="bf19b-139">Arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="bf19b-139">Configuration File</span></span>  
 <span data-ttu-id="bf19b-140">Em um aplicativo .NET Framework, esse elemento só pode ser usado no arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="bf19b-140">In a .NET Framework application, this element can be used only in the application configuration file.</span></span>  
  
 <span data-ttu-id="bf19b-141">Para um aplicativo ASP.NET, o fluxo de personificação pode ser configurado no \<diretório aspnet.config encontrado no diretório Windows Folder>\Microsoft.NET\Framework\vx.xxxx.</span><span class="sxs-lookup"><span data-stu-id="bf19b-141">For an ASP.NET application, the impersonation flow can be configured in the aspnet.config file found in the \<Windows Folder>\Microsoft.NET\Framework\vx.x.xxxx directory.</span></span>  
  
 <span data-ttu-id="bf19b-142">ASP.NET por padrão desativa o fluxo de personificação no arquivo aspnet.config usando as seguintes configurações:</span><span class="sxs-lookup"><span data-stu-id="bf19b-142">ASP.NET by default disables the impersonation flow in the aspnet.config file by using the following configuration settings:</span></span>  
  
```xml
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
      <alwaysFlowImpersonationPolicy enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="bf19b-143">Em ASP.NET, se você quiser permitir o fluxo de personificação, em vez disso, você deve usar explicitamente as seguintes configurações:</span><span class="sxs-lookup"><span data-stu-id="bf19b-143">In ASP.NET, if you want to allow the flow of impersonation instead, you must explicitly use the following configuration settings:</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="false"/>  
      <alwaysFlowImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="example"></a><span data-ttu-id="bf19b-144">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bf19b-144">Example</span></span>  
 <span data-ttu-id="bf19b-145">O exemplo a seguir mostra como especificar que a identidade do Windows flui através de pontos assíncronos, mesmo quando a personificação é alcançada através de meios diferentes dos métodos gerenciados.</span><span class="sxs-lookup"><span data-stu-id="bf19b-145">The following example shows how to specify that the Windows identity flows across asynchronous points, even when the impersonation is achieved through means other than managed methods.</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <alwaysFlowImpersonationPolicy enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="bf19b-146">Confira também</span><span class="sxs-lookup"><span data-stu-id="bf19b-146">See also</span></span>

- [<span data-ttu-id="bf19b-147">Esquema de configurações do runtime</span><span class="sxs-lookup"><span data-stu-id="bf19b-147">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="bf19b-148">Esquema de arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="bf19b-148">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="bf19b-149">\<elemento de> de representação de representação legado</span><span class="sxs-lookup"><span data-stu-id="bf19b-149">\<legacyImpersonationPolicy> Element</span></span>](legacyimpersonationpolicy-element.md)
