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
ms.openlocfilehash: 9316f026a807b6ad36014157061f67bdbd7d3d18
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91149433"
---
# <a name="alwaysflowimpersonationpolicy-element"></a><span data-ttu-id="33e8a-102">Elemento \<alwaysFlowImpersonationPolicy></span><span class="sxs-lookup"><span data-stu-id="33e8a-102">\<alwaysFlowImpersonationPolicy> Element</span></span>

<span data-ttu-id="33e8a-103">Especifica que a identidade do Windows sempre fluirá por pontos assíncronos, independentemente de como a representação tenha sido executada.</span><span class="sxs-lookup"><span data-stu-id="33e8a-103">Specifies that the Windows identity always flows across asynchronous points, regardless of how impersonation was performed.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<alwaysFlowImpersonationPolicy>**\  
  
## <a name="syntax"></a><span data-ttu-id="33e8a-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="33e8a-104">Syntax</span></span>  
  
```xml  
<alwaysFlowImpersonationPolicy
  enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="33e8a-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="33e8a-105">Attributes and Elements</span></span>  

 <span data-ttu-id="33e8a-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="33e8a-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="33e8a-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="33e8a-107">Attributes</span></span>  
  
|<span data-ttu-id="33e8a-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="33e8a-108">Attribute</span></span>|<span data-ttu-id="33e8a-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="33e8a-109">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="33e8a-110">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="33e8a-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="33e8a-111">Indica se a identidade do Windows flui entre pontos assíncronos.</span><span class="sxs-lookup"><span data-stu-id="33e8a-111">Indicates whether the Windows identity flows across asynchronous points.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="33e8a-112">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="33e8a-112">enabled Attribute</span></span>  
  
|<span data-ttu-id="33e8a-113">Valor</span><span class="sxs-lookup"><span data-stu-id="33e8a-113">Value</span></span>|<span data-ttu-id="33e8a-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="33e8a-114">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="33e8a-115">A identidade do Windows não flui em pontos assíncronos, a menos que a representação seja executada por meio de métodos gerenciados, como <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> .</span><span class="sxs-lookup"><span data-stu-id="33e8a-115">The Windows identity does not flow across asynchronous points, unless the impersonation is performed through managed methods such as <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A>.</span></span> <span data-ttu-id="33e8a-116">Este é o padrão.</span><span class="sxs-lookup"><span data-stu-id="33e8a-116">This is the default.</span></span>|  
|`true`|<span data-ttu-id="33e8a-117">A identidade do Windows sempre flui entre pontos assíncronos, independentemente de como a representação foi executada.</span><span class="sxs-lookup"><span data-stu-id="33e8a-117">The Windows identity always flows across asynchronous points, regardless of how impersonation was performed.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="33e8a-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="33e8a-118">Child Elements</span></span>  

 <span data-ttu-id="33e8a-119">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="33e8a-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="33e8a-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="33e8a-120">Parent Elements</span></span>  
  
|<span data-ttu-id="33e8a-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="33e8a-121">Element</span></span>|<span data-ttu-id="33e8a-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="33e8a-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="33e8a-123">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="33e8a-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="33e8a-124">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="33e8a-124">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="33e8a-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="33e8a-125">Remarks</span></span>  

 <span data-ttu-id="33e8a-126">No .NET Framework versões 1,0 e 1,1, a identidade do Windows não flui entre pontos assíncronos.</span><span class="sxs-lookup"><span data-stu-id="33e8a-126">In the .NET Framework versions 1.0 and 1.1, the Windows identity does not flow across asynchronous points.</span></span> <span data-ttu-id="33e8a-127">No .NET Framework versão 2,0, há um <xref:System.Threading.ExecutionContext> objeto que contém informações sobre o thread em execução no momento e o flui entre pontos assíncronos dentro de um domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="33e8a-127">In the .NET Framework version 2.0, there is an <xref:System.Threading.ExecutionContext> object that contains information about the currently executing thread, and flows it across asynchronous points within an application domain.</span></span> <span data-ttu-id="33e8a-128">O <xref:System.Security.Principal.WindowsIdentity> também flui como parte das informações que fluem pelos pontos assíncronos, desde que a representação tenha sido obtida usando métodos gerenciados, como <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> e não por outros meios, como invocação de plataforma para métodos nativos.</span><span class="sxs-lookup"><span data-stu-id="33e8a-128">The <xref:System.Security.Principal.WindowsIdentity> also flows as part of the information that flows across the asynchronous points, provided the impersonation was achieved using managed methods such as <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> and not through other means such as platform invoke to native methods.</span></span> <span data-ttu-id="33e8a-129">Esse elemento é usado para especificar que a identidade do Windows flua entre pontos assíncronos, independentemente de como a representação foi obtida.</span><span class="sxs-lookup"><span data-stu-id="33e8a-129">This element is used to specify that the Windows identity does flow across asynchronous points, regardless of how the impersonation was achieved.</span></span>  
  
 <span data-ttu-id="33e8a-130">Você pode alterar esse comportamento padrão de duas maneiras:</span><span class="sxs-lookup"><span data-stu-id="33e8a-130">You can alter this default behavior in two other ways:</span></span>  
  
1. <span data-ttu-id="33e8a-131">Em código gerenciado por thread.</span><span class="sxs-lookup"><span data-stu-id="33e8a-131">In managed code on a per-thread basis.</span></span>  
  
     <span data-ttu-id="33e8a-132">Você pode suprimir o fluxo por thread modificando as <xref:System.Threading.ExecutionContext> <xref:System.Security.SecurityContext> configurações e usando o <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType> <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType> método, ou <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="33e8a-132">You can suppress the flow on a per-thread basis by modifying the <xref:System.Threading.ExecutionContext> and <xref:System.Security.SecurityContext> settings by using the <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>, <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType>, or <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> method.</span></span>  
  
2. <span data-ttu-id="33e8a-133">Na chamada à interface de hospedagem não gerenciada para carregar o Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="33e8a-133">In the call to the unmanaged hosting interface to load the common language runtime (CLR).</span></span>  
  
     <span data-ttu-id="33e8a-134">Se uma interface de hospedagem não gerenciada (em vez de um executável gerenciado simples) for usada para carregar o CLR, você poderá especificar um sinalizador especial na chamada para a função de [função CorBindToRuntimeEx](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) .</span><span class="sxs-lookup"><span data-stu-id="33e8a-134">If an unmanaged hosting interface (instead of a simple managed executable) is used to load the CLR, you can specify a special flag in the call to the [CorBindToRuntimeEx Function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) function.</span></span> <span data-ttu-id="33e8a-135">Para habilitar o modo de compatibilidade para todo o processo, defina o `flags` parâmetro para a [função CorBindToRuntimeEx](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) como `STARTUP_ALWAYSFLOW_IMPERSONATION` .</span><span class="sxs-lookup"><span data-stu-id="33e8a-135">To enable the compatibility mode for the entire process, set the `flags` parameter for [CorBindToRuntimeEx Function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) to `STARTUP_ALWAYSFLOW_IMPERSONATION`.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="33e8a-136">Arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="33e8a-136">Configuration File</span></span>  

 <span data-ttu-id="33e8a-137">Em um aplicativo .NET Framework, esse elemento pode ser usado somente no arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="33e8a-137">In a .NET Framework application, this element can be used only in the application configuration file.</span></span>  
  
 <span data-ttu-id="33e8a-138">Para um aplicativo ASP.NET, o fluxo de representação pode ser configurado no arquivo de aspnet.config encontrado no \<Windows Folder> diretório \Microsoft.NET\Framework\vx.x.xxxx.</span><span class="sxs-lookup"><span data-stu-id="33e8a-138">For an ASP.NET application, the impersonation flow can be configured in the aspnet.config file found in the \<Windows Folder>\Microsoft.NET\Framework\vx.x.xxxx directory.</span></span>  
  
 <span data-ttu-id="33e8a-139">O ASP.NET, por padrão, desabilita o fluxo de representação no arquivo de aspnet.config usando as seguintes definições de configuração:</span><span class="sxs-lookup"><span data-stu-id="33e8a-139">ASP.NET by default disables the impersonation flow in the aspnet.config file by using the following configuration settings:</span></span>  
  
```xml
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
      <alwaysFlowImpersonationPolicy enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="33e8a-140">Em ASP.NET, se você quiser permitir o fluxo de representação em vez disso, deverá usar explicitamente as seguintes definições de configuração:</span><span class="sxs-lookup"><span data-stu-id="33e8a-140">In ASP.NET, if you want to allow the flow of impersonation instead, you must explicitly use the following configuration settings:</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="false"/>  
      <alwaysFlowImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="example"></a><span data-ttu-id="33e8a-141">Exemplo</span><span class="sxs-lookup"><span data-stu-id="33e8a-141">Example</span></span>  

 <span data-ttu-id="33e8a-142">O exemplo a seguir mostra como especificar que a identidade do Windows flui entre pontos assíncronos, mesmo quando a representação é obtida por meio de meios diferentes dos métodos gerenciados.</span><span class="sxs-lookup"><span data-stu-id="33e8a-142">The following example shows how to specify that the Windows identity flows across asynchronous points, even when the impersonation is achieved through means other than managed methods.</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <alwaysFlowImpersonationPolicy enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="33e8a-143">Confira também</span><span class="sxs-lookup"><span data-stu-id="33e8a-143">See also</span></span>

- [<span data-ttu-id="33e8a-144">Esquema de configurações do runtime</span><span class="sxs-lookup"><span data-stu-id="33e8a-144">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="33e8a-145">Esquema do arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="33e8a-145">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="33e8a-146">\<legacyImpersonationPolicy> Elementos</span><span class="sxs-lookup"><span data-stu-id="33e8a-146">\<legacyImpersonationPolicy> Element</span></span>](legacyimpersonationpolicy-element.md)
