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
ms.openlocfilehash: 06e91ea6989dcdf0b2a179e7d6ce79b8d9aaff03
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73118348"
---
# <a name="alwaysflowimpersonationpolicy-element"></a><span data-ttu-id="8b4cd-102">\<elemento de > alwaysFlowImpersonationPolicy</span><span class="sxs-lookup"><span data-stu-id="8b4cd-102">\<alwaysFlowImpersonationPolicy> Element</span></span>
<span data-ttu-id="8b4cd-103">Especifica que a identidade do Windows sempre fluirá por pontos assíncronos, independentemente de como a representação tenha sido executada.</span><span class="sxs-lookup"><span data-stu-id="8b4cd-103">Specifies that the Windows identity always flows across asynchronous points, regardless of how impersonation was performed.</span></span>  
  
<span data-ttu-id="8b4cd-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="8b4cd-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="8b4cd-105">&nbsp; &nbsp;[ **\<runtime >** ](runtime-element.md) </span><span class="sxs-lookup"><span data-stu-id="8b4cd-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="8b4cd-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<alwaysFlowImpersonationPolicy >** </span><span class="sxs-lookup"><span data-stu-id="8b4cd-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<alwaysFlowImpersonationPolicy>**</span></span>\  
  
## <a name="syntax"></a><span data-ttu-id="8b4cd-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8b4cd-107">Syntax</span></span>  
  
```xml  
<alwaysFlowImpersonationPolicy    
  enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8b4cd-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="8b4cd-108">Attributes and Elements</span></span>  
 <span data-ttu-id="8b4cd-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="8b4cd-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8b4cd-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="8b4cd-110">Attributes</span></span>  
  
|<span data-ttu-id="8b4cd-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="8b4cd-111">Attribute</span></span>|<span data-ttu-id="8b4cd-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="8b4cd-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="8b4cd-113">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="8b4cd-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="8b4cd-114">Indica se a identidade do Windows flui entre pontos assíncronos.</span><span class="sxs-lookup"><span data-stu-id="8b4cd-114">Indicates whether the Windows identity flows across asynchronous points.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="8b4cd-115">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="8b4cd-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="8b4cd-116">Valor</span><span class="sxs-lookup"><span data-stu-id="8b4cd-116">Value</span></span>|<span data-ttu-id="8b4cd-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="8b4cd-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="8b4cd-118">A identidade do Windows não flui em pontos assíncronos, a menos que a representação seja executada por meio de métodos gerenciados, como <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A>.</span><span class="sxs-lookup"><span data-stu-id="8b4cd-118">The Windows identity does not flow across asynchronous points, unless the impersonation is performed through managed methods such as <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A>.</span></span> <span data-ttu-id="8b4cd-119">Esse é o padrão.</span><span class="sxs-lookup"><span data-stu-id="8b4cd-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="8b4cd-120">A identidade do Windows sempre flui entre pontos assíncronos, independentemente de como a representação foi executada.</span><span class="sxs-lookup"><span data-stu-id="8b4cd-120">The Windows identity always flows across asynchronous points, regardless of how impersonation was performed.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8b4cd-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="8b4cd-121">Child Elements</span></span>  
 <span data-ttu-id="8b4cd-122">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="8b4cd-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8b4cd-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="8b4cd-123">Parent Elements</span></span>  
  
|<span data-ttu-id="8b4cd-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="8b4cd-124">Element</span></span>|<span data-ttu-id="8b4cd-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="8b4cd-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="8b4cd-126">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8b4cd-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="8b4cd-127">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="8b4cd-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8b4cd-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="8b4cd-128">Remarks</span></span>  
 <span data-ttu-id="8b4cd-129">No .NET Framework versões 1,0 e 1,1, a identidade do Windows não flui entre pontos assíncronos.</span><span class="sxs-lookup"><span data-stu-id="8b4cd-129">In the .NET Framework versions 1.0 and 1.1, the Windows identity does not flow across asynchronous points.</span></span> <span data-ttu-id="8b4cd-130">Na versão .NET Framework 2,0, há um objeto <xref:System.Threading.ExecutionContext> que contém informações sobre o thread em execução no momento e o flui entre pontos assíncronos dentro de um domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8b4cd-130">In the .NET Framework version 2.0, there is an <xref:System.Threading.ExecutionContext> object that contains information about the currently executing thread, and flows it across asynchronous points within an application domain.</span></span> <span data-ttu-id="8b4cd-131">O <xref:System.Security.Principal.WindowsIdentity> também flui como parte das informações que fluem pelos pontos assíncronos, desde que a representação tenha sido obtida usando métodos gerenciados, como <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> e não por outros meios, como invocação de plataforma para métodos nativos.</span><span class="sxs-lookup"><span data-stu-id="8b4cd-131">The <xref:System.Security.Principal.WindowsIdentity> also flows as part of the information that flows across the asynchronous points, provided the impersonation was achieved using managed methods such as <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> and not through other means such as platform invoke to native methods.</span></span> <span data-ttu-id="8b4cd-132">Esse elemento é usado para especificar que a identidade do Windows flua entre pontos assíncronos, independentemente de como a representação foi obtida.</span><span class="sxs-lookup"><span data-stu-id="8b4cd-132">This element is used to specify that the Windows identity does flow across asynchronous points, regardless of how the impersonation was achieved.</span></span>  
  
 <span data-ttu-id="8b4cd-133">Você pode alterar esse comportamento padrão de duas maneiras:</span><span class="sxs-lookup"><span data-stu-id="8b4cd-133">You can alter this default behavior in two other ways:</span></span>  
  
1. <span data-ttu-id="8b4cd-134">Em código gerenciado por thread.</span><span class="sxs-lookup"><span data-stu-id="8b4cd-134">In managed code on a per-thread basis.</span></span>  
  
     <span data-ttu-id="8b4cd-135">Você pode suprimir o fluxo por thread, modificando as configurações de <xref:System.Threading.ExecutionContext> e <xref:System.Security.SecurityContext> usando o método <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>, <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType>ou <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8b4cd-135">You can suppress the flow on a per-thread basis by modifying the <xref:System.Threading.ExecutionContext> and <xref:System.Security.SecurityContext> settings by using the <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>, <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType>, or <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> method.</span></span>  
  
2. <span data-ttu-id="8b4cd-136">Na chamada à interface de hospedagem não gerenciada para carregar o Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="8b4cd-136">In the call to the unmanaged hosting interface to load the common language runtime (CLR).</span></span>  
  
     <span data-ttu-id="8b4cd-137">Se uma interface de hospedagem não gerenciada (em vez de um executável gerenciado simples) for usada para carregar o CLR, você poderá especificar um sinalizador especial na chamada para a função de [função CorBindToRuntimeEx](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) .</span><span class="sxs-lookup"><span data-stu-id="8b4cd-137">If an unmanaged hosting interface (instead of a simple managed executable) is used to load the CLR, you can specify a special flag in the call to the [CorBindToRuntimeEx Function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) function.</span></span> <span data-ttu-id="8b4cd-138">Para habilitar o modo de compatibilidade para todo o processo, defina o parâmetro `flags` para a [função CorBindToRuntimeEx](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) como `STARTUP_ALWAYSFLOW_IMPERSONATION`.</span><span class="sxs-lookup"><span data-stu-id="8b4cd-138">To enable the compatibility mode for the entire process, set the `flags` parameter for [CorBindToRuntimeEx Function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) to `STARTUP_ALWAYSFLOW_IMPERSONATION`.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="8b4cd-139">Arquivo de Configuração</span><span class="sxs-lookup"><span data-stu-id="8b4cd-139">Configuration File</span></span>  
 <span data-ttu-id="8b4cd-140">Em um aplicativo .NET Framework, esse elemento pode ser usado somente no arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8b4cd-140">In a .NET Framework application, this element can be used only in the application configuration file.</span></span>  
  
 <span data-ttu-id="8b4cd-141">Para um aplicativo ASP.NET, o fluxo de representação pode ser configurado no arquivo Aspnet. config encontrado na pasta \<Windows > diretório \Microsoft.NET\Framework\vx.x.xxxx.</span><span class="sxs-lookup"><span data-stu-id="8b4cd-141">For an ASP.NET application, the impersonation flow can be configured in the aspnet.config file found in the \<Windows Folder>\Microsoft.NET\Framework\vx.x.xxxx directory.</span></span>  
  
 <span data-ttu-id="8b4cd-142">O ASP.NET, por padrão, desabilita o fluxo de representação no arquivo Aspnet. config usando as seguintes definições de configuração:</span><span class="sxs-lookup"><span data-stu-id="8b4cd-142">ASP.NET by default disables the impersonation flow in the aspnet.config file by using the following configuration settings:</span></span>  
  
```xml
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
      <alwaysFlowImpersonationPolicy enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="8b4cd-143">Em ASP.NET, se você quiser permitir o fluxo de representação em vez disso, deverá usar explicitamente as seguintes definições de configuração:</span><span class="sxs-lookup"><span data-stu-id="8b4cd-143">In ASP.NET, if you want to allow the flow of impersonation instead, you must explicitly use the following configuration settings:</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="false"/>  
      <alwaysFlowImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="example"></a><span data-ttu-id="8b4cd-144">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8b4cd-144">Example</span></span>  
 <span data-ttu-id="8b4cd-145">O exemplo a seguir mostra como especificar que a identidade do Windows flui entre pontos assíncronos, mesmo quando a representação é obtida por meio de meios diferentes dos métodos gerenciados.</span><span class="sxs-lookup"><span data-stu-id="8b4cd-145">The following example shows how to specify that the Windows identity flows across asynchronous points, even when the impersonation is achieved through means other than managed methods.</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <alwaysFlowImpersonationPolicy enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8b4cd-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8b4cd-146">See also</span></span>

- [<span data-ttu-id="8b4cd-147">Esquema de configurações do tempo de execução</span><span class="sxs-lookup"><span data-stu-id="8b4cd-147">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="8b4cd-148">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="8b4cd-148">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="8b4cd-149">\<elemento de > legacyImpersonationPolicy</span><span class="sxs-lookup"><span data-stu-id="8b4cd-149">\<legacyImpersonationPolicy> Element</span></span>](legacyimpersonationpolicy-element.md)
