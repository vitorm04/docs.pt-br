---
title: Elemento <etwEnable>
ms.date: 03/30/2017
helpviewer_keywords:
- etwEnable element
- <etwEnable> element
ms.assetid: 29dde982-6d8b-4099-8867-ad0d7733f6dc
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cb4d0ed5b33170c40aacb32bebbf1b59ca659be4
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252613"
---
# <a name="etwenable-element"></a><span data-ttu-id="7c3ac-102">\<Elemento de > etwEnable</span><span class="sxs-lookup"><span data-stu-id="7c3ac-102">\<etwEnable> Element</span></span>
<span data-ttu-id="7c3ac-103">Especifica se deseja-se habilitar o rastreamento de eventos para Windows (ETW) para eventos de Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="7c3ac-103">Specifies whether to enable event tracing for Windows (ETW) for common language runtime events.</span></span>  
  
<span data-ttu-id="7c3ac-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="7c3ac-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="7c3ac-105">&nbsp;&nbsp;[ **\<> de tempo de execução**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="7c3ac-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="7c3ac-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<> etwEnabled**</span><span class="sxs-lookup"><span data-stu-id="7c3ac-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<etwEnabled>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c3ac-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7c3ac-107">Syntax</span></span>  
  
```xml  
<etwEnable enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7c3ac-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="7c3ac-108">Attributes and Elements</span></span>  
 <span data-ttu-id="7c3ac-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="7c3ac-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7c3ac-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="7c3ac-110">Attributes</span></span>  
  
|<span data-ttu-id="7c3ac-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="7c3ac-111">Attribute</span></span>|<span data-ttu-id="7c3ac-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="7c3ac-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7c3ac-113">enabled</span><span class="sxs-lookup"><span data-stu-id="7c3ac-113">enabled</span></span>|<span data-ttu-id="7c3ac-114">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="7c3ac-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="7c3ac-115">Especifica se o ETW deve ser habilitado.</span><span class="sxs-lookup"><span data-stu-id="7c3ac-115">Specifies whether ETW should be enabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="7c3ac-116">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="7c3ac-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="7c3ac-117">Valor</span><span class="sxs-lookup"><span data-stu-id="7c3ac-117">Value</span></span>|<span data-ttu-id="7c3ac-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="7c3ac-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="7c3ac-119">true</span><span class="sxs-lookup"><span data-stu-id="7c3ac-119">true</span></span>|<span data-ttu-id="7c3ac-120">Habilite o ETW.</span><span class="sxs-lookup"><span data-stu-id="7c3ac-120">Enable ETW.</span></span> <span data-ttu-id="7c3ac-121">Esse é o padrão para versões do Windows começando com os sistemas operacionais Windows Vista e Windows Server 2008.</span><span class="sxs-lookup"><span data-stu-id="7c3ac-121">This is the default for versions of Windows beginning with the Windows Vista and Windows Server 2008 operating systems.</span></span>|  
|<span data-ttu-id="7c3ac-122">false</span><span class="sxs-lookup"><span data-stu-id="7c3ac-122">false</span></span>|<span data-ttu-id="7c3ac-123">Desabilite o ETW.</span><span class="sxs-lookup"><span data-stu-id="7c3ac-123">Disable ETW.</span></span> <span data-ttu-id="7c3ac-124">Esse é o padrão para versões anteriores do Windows.</span><span class="sxs-lookup"><span data-stu-id="7c3ac-124">This is the default for earlier versions of Windows.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7c3ac-125">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="7c3ac-125">Child Elements</span></span>  
 <span data-ttu-id="7c3ac-126">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="7c3ac-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7c3ac-127">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="7c3ac-127">Parent Elements</span></span>  
  
|<span data-ttu-id="7c3ac-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="7c3ac-128">Element</span></span>|<span data-ttu-id="7c3ac-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="7c3ac-129">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="7c3ac-130">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7c3ac-130">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="7c3ac-131">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="7c3ac-131">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7c3ac-132">Comentários</span><span class="sxs-lookup"><span data-stu-id="7c3ac-132">Remarks</span></span>  
 <span data-ttu-id="7c3ac-133">A partir do Windows Vista, o ETW é habilitado por padrão.</span><span class="sxs-lookup"><span data-stu-id="7c3ac-133">Beginning with Windows Vista, ETW is enabled by default.</span></span> <span data-ttu-id="7c3ac-134">Use este elemento para desabilitar o ETW para um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7c3ac-134">Use this element to disable ETW for an application.</span></span> <span data-ttu-id="7c3ac-135">Em versões anteriores do Windows, use esse elemento para habilitar o ETW para um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7c3ac-135">In earlier versions of Windows, use this element to enable ETW for an application.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7c3ac-136">O ETW pode ser habilitado ou desabilitado globalmente em um servidor usando uma configuração de registro.</span><span class="sxs-lookup"><span data-stu-id="7c3ac-136">ETW can be enabled or disabled globally on a server by using a registry setting.</span></span> <span data-ttu-id="7c3ac-137">Consulte [controlando o log de .NET Framework](../../../performance/controlling-logging.md).</span><span class="sxs-lookup"><span data-stu-id="7c3ac-137">See [Controlling .NET Framework Logging](../../../performance/controlling-logging.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7c3ac-138">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7c3ac-138">Example</span></span>  
 <span data-ttu-id="7c3ac-139">O exemplo a seguir mostra como habilitar o rastreamento ETW para um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7c3ac-139">The following example shows how to enable ETW tracing for an application.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <etwEnable enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7c3ac-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7c3ac-140">See also</span></span>

- [<span data-ttu-id="7c3ac-141">Esquema de configurações do tempo de execução</span><span class="sxs-lookup"><span data-stu-id="7c3ac-141">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="7c3ac-142">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="7c3ac-142">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="7c3ac-143">Controlando o log no .NET Framework</span><span class="sxs-lookup"><span data-stu-id="7c3ac-143">Controlling .NET Framework Logging</span></span>](../../../performance/controlling-logging.md)
