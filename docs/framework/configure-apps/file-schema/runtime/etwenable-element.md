---
title: Elemento <etwEnable>
ms.date: 03/30/2017
helpviewer_keywords:
- etwEnable element
- <etwEnable> element
ms.assetid: 29dde982-6d8b-4099-8867-ad0d7733f6dc
ms.openlocfilehash: 14cea171a4a25e148ea32f75a8ef09b83a4ec8ad
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73117394"
---
# <a name="etwenable-element"></a><span data-ttu-id="9f0a1-102">Elemento \<etwEnable></span><span class="sxs-lookup"><span data-stu-id="9f0a1-102">\<etwEnable> Element</span></span>
<span data-ttu-id="9f0a1-103">Especifica se deseja-se habilitar o rastreamento de eventos para Windows (ETW) para eventos de Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="9f0a1-103">Specifies whether to enable event tracing for Windows (ETW) for common language runtime events.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<etwEnabled>**  
  
## <a name="syntax"></a><span data-ttu-id="9f0a1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9f0a1-104">Syntax</span></span>  
  
```xml  
<etwEnable enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9f0a1-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="9f0a1-105">Attributes and Elements</span></span>  
 <span data-ttu-id="9f0a1-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="9f0a1-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9f0a1-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="9f0a1-107">Attributes</span></span>  
  
|<span data-ttu-id="9f0a1-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="9f0a1-108">Attribute</span></span>|<span data-ttu-id="9f0a1-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="9f0a1-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9f0a1-110">Habilitado</span><span class="sxs-lookup"><span data-stu-id="9f0a1-110">enabled</span></span>|<span data-ttu-id="9f0a1-111">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="9f0a1-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="9f0a1-112">Especifica se o ETW deve ser habilitado.</span><span class="sxs-lookup"><span data-stu-id="9f0a1-112">Specifies whether ETW should be enabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="9f0a1-113">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="9f0a1-113">enabled Attribute</span></span>  
  
|<span data-ttu-id="9f0a1-114">Valor</span><span class="sxs-lookup"><span data-stu-id="9f0a1-114">Value</span></span>|<span data-ttu-id="9f0a1-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="9f0a1-115">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="9f0a1-116">true</span><span class="sxs-lookup"><span data-stu-id="9f0a1-116">true</span></span>|<span data-ttu-id="9f0a1-117">Habilite o ETW.</span><span class="sxs-lookup"><span data-stu-id="9f0a1-117">Enable ETW.</span></span> <span data-ttu-id="9f0a1-118">Esse é o padrão para versões do Windows começando com os sistemas operacionais Windows Vista e Windows Server 2008.</span><span class="sxs-lookup"><span data-stu-id="9f0a1-118">This is the default for versions of Windows beginning with the Windows Vista and Windows Server 2008 operating systems.</span></span>|  
|<span data-ttu-id="9f0a1-119">false</span><span class="sxs-lookup"><span data-stu-id="9f0a1-119">false</span></span>|<span data-ttu-id="9f0a1-120">Desabilite o ETW.</span><span class="sxs-lookup"><span data-stu-id="9f0a1-120">Disable ETW.</span></span> <span data-ttu-id="9f0a1-121">Esse é o padrão para versões anteriores do Windows.</span><span class="sxs-lookup"><span data-stu-id="9f0a1-121">This is the default for earlier versions of Windows.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9f0a1-122">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="9f0a1-122">Child Elements</span></span>  
 <span data-ttu-id="9f0a1-123">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="9f0a1-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9f0a1-124">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="9f0a1-124">Parent Elements</span></span>  
  
|<span data-ttu-id="9f0a1-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="9f0a1-125">Element</span></span>|<span data-ttu-id="9f0a1-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="9f0a1-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="9f0a1-127">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9f0a1-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="9f0a1-128">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="9f0a1-128">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9f0a1-129">Comentários</span><span class="sxs-lookup"><span data-stu-id="9f0a1-129">Remarks</span></span>  
 <span data-ttu-id="9f0a1-130">A partir do Windows Vista, o ETW é habilitado por padrão.</span><span class="sxs-lookup"><span data-stu-id="9f0a1-130">Beginning with Windows Vista, ETW is enabled by default.</span></span> <span data-ttu-id="9f0a1-131">Use este elemento para desabilitar o ETW para um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9f0a1-131">Use this element to disable ETW for an application.</span></span> <span data-ttu-id="9f0a1-132">Em versões anteriores do Windows, use esse elemento para habilitar o ETW para um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9f0a1-132">In earlier versions of Windows, use this element to enable ETW for an application.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9f0a1-133">O ETW pode ser habilitado ou desabilitado globalmente em um servidor usando uma configuração de registro.</span><span class="sxs-lookup"><span data-stu-id="9f0a1-133">ETW can be enabled or disabled globally on a server by using a registry setting.</span></span> <span data-ttu-id="9f0a1-134">Consulte [controlando o log de .NET Framework](../../../performance/controlling-logging.md).</span><span class="sxs-lookup"><span data-stu-id="9f0a1-134">See [Controlling .NET Framework Logging](../../../performance/controlling-logging.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9f0a1-135">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9f0a1-135">Example</span></span>  
 <span data-ttu-id="9f0a1-136">O exemplo a seguir mostra como habilitar o rastreamento ETW para um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9f0a1-136">The following example shows how to enable ETW tracing for an application.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <etwEnable enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9f0a1-137">Confira também</span><span class="sxs-lookup"><span data-stu-id="9f0a1-137">See also</span></span>

- [<span data-ttu-id="9f0a1-138">Esquema de configurações do runtime</span><span class="sxs-lookup"><span data-stu-id="9f0a1-138">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="9f0a1-139">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="9f0a1-139">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="9f0a1-140">Controlando o registro em log no .NET Framework</span><span class="sxs-lookup"><span data-stu-id="9f0a1-140">Controlling .NET Framework Logging</span></span>](../../../performance/controlling-logging.md)
