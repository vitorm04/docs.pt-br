---
title: Elemento <etwEnable>
ms.date: 03/30/2017
helpviewer_keywords:
- etwEnable element
- <etwEnable> element
ms.assetid: 29dde982-6d8b-4099-8867-ad0d7733f6dc
ms.openlocfilehash: 1c3e42dfbc2c27841ed065e90bad24575e4fb2b1
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91178262"
---
# <a name="etwenable-element"></a><span data-ttu-id="4803c-102">Elemento \<etwEnable></span><span class="sxs-lookup"><span data-stu-id="4803c-102">\<etwEnable> Element</span></span>

<span data-ttu-id="4803c-103">Especifica se deseja-se habilitar o rastreamento de eventos para Windows (ETW) para eventos de Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="4803c-103">Specifies whether to enable event tracing for Windows (ETW) for common language runtime events.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<etwEnabled>**  
  
## <a name="syntax"></a><span data-ttu-id="4803c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4803c-104">Syntax</span></span>  
  
```xml  
<etwEnable enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4803c-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="4803c-105">Attributes and Elements</span></span>  

 <span data-ttu-id="4803c-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="4803c-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4803c-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="4803c-107">Attributes</span></span>  
  
|<span data-ttu-id="4803c-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="4803c-108">Attribute</span></span>|<span data-ttu-id="4803c-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="4803c-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4803c-110">Habilitado</span><span class="sxs-lookup"><span data-stu-id="4803c-110">enabled</span></span>|<span data-ttu-id="4803c-111">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="4803c-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="4803c-112">Especifica se o ETW deve ser habilitado.</span><span class="sxs-lookup"><span data-stu-id="4803c-112">Specifies whether ETW should be enabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="4803c-113">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="4803c-113">enabled Attribute</span></span>  
  
|<span data-ttu-id="4803c-114">Valor</span><span class="sxs-lookup"><span data-stu-id="4803c-114">Value</span></span>|<span data-ttu-id="4803c-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="4803c-115">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="4803c-116">true</span><span class="sxs-lookup"><span data-stu-id="4803c-116">true</span></span>|<span data-ttu-id="4803c-117">Habilite o ETW.</span><span class="sxs-lookup"><span data-stu-id="4803c-117">Enable ETW.</span></span> <span data-ttu-id="4803c-118">Esse é o padrão para versões do Windows começando com os sistemas operacionais Windows Vista e Windows Server 2008.</span><span class="sxs-lookup"><span data-stu-id="4803c-118">This is the default for versions of Windows beginning with the Windows Vista and Windows Server 2008 operating systems.</span></span>|  
|<span data-ttu-id="4803c-119">false</span><span class="sxs-lookup"><span data-stu-id="4803c-119">false</span></span>|<span data-ttu-id="4803c-120">Desabilite o ETW.</span><span class="sxs-lookup"><span data-stu-id="4803c-120">Disable ETW.</span></span> <span data-ttu-id="4803c-121">Esse é o padrão para versões anteriores do Windows.</span><span class="sxs-lookup"><span data-stu-id="4803c-121">This is the default for earlier versions of Windows.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4803c-122">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="4803c-122">Child Elements</span></span>  

 <span data-ttu-id="4803c-123">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="4803c-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4803c-124">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="4803c-124">Parent Elements</span></span>  
  
|<span data-ttu-id="4803c-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="4803c-125">Element</span></span>|<span data-ttu-id="4803c-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="4803c-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="4803c-127">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4803c-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="4803c-128">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="4803c-128">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4803c-129">Comentários</span><span class="sxs-lookup"><span data-stu-id="4803c-129">Remarks</span></span>  

 <span data-ttu-id="4803c-130">A partir do Windows Vista, o ETW é habilitado por padrão.</span><span class="sxs-lookup"><span data-stu-id="4803c-130">Beginning with Windows Vista, ETW is enabled by default.</span></span> <span data-ttu-id="4803c-131">Use este elemento para desabilitar o ETW para um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4803c-131">Use this element to disable ETW for an application.</span></span> <span data-ttu-id="4803c-132">Em versões anteriores do Windows, use esse elemento para habilitar o ETW para um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4803c-132">In earlier versions of Windows, use this element to enable ETW for an application.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4803c-133">O ETW pode ser habilitado ou desabilitado globalmente em um servidor usando uma configuração de registro.</span><span class="sxs-lookup"><span data-stu-id="4803c-133">ETW can be enabled or disabled globally on a server by using a registry setting.</span></span> <span data-ttu-id="4803c-134">Consulte [controlando o log de .NET Framework](../../../performance/controlling-logging.md).</span><span class="sxs-lookup"><span data-stu-id="4803c-134">See [Controlling .NET Framework Logging](../../../performance/controlling-logging.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4803c-135">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4803c-135">Example</span></span>  

 <span data-ttu-id="4803c-136">O exemplo a seguir mostra como habilitar o rastreamento ETW para um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4803c-136">The following example shows how to enable ETW tracing for an application.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <etwEnable enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4803c-137">Veja também</span><span class="sxs-lookup"><span data-stu-id="4803c-137">See also</span></span>

- [<span data-ttu-id="4803c-138">Esquema de configurações do runtime</span><span class="sxs-lookup"><span data-stu-id="4803c-138">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="4803c-139">Esquema do arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="4803c-139">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="4803c-140">Controlando o registro em log no .NET Framework</span><span class="sxs-lookup"><span data-stu-id="4803c-140">Controlling .NET Framework Logging</span></span>](../../../performance/controlling-logging.md)
