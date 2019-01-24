---
title: '&lt;UseSmallInternalThreadStacks&gt; elemento'
ms.date: 03/30/2017
helpviewer_keywords:
- UseSmallInternalThreadStacks element
- <UseSmallInternalThreadStacks> element
ms.assetid: 1e3f6ec0-1cac-4e1c-9c81-17d948ae5874
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ed128cc2ddec3c599932cd5a82364d1cf6642cde
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54505231"
---
# <a name="ltusesmallinternalthreadstacksgt-element"></a><span data-ttu-id="b2125-102">&lt;UseSmallInternalThreadStacks&gt; elemento</span><span class="sxs-lookup"><span data-stu-id="b2125-102">&lt;UseSmallInternalThreadStacks&gt; Element</span></span>
<span data-ttu-id="b2125-103">Usam solicitações que o common language runtime (CLR) reduzir a memória com a especificação de tamanhos de pilha explícito ao criar certos threads que ele usa internamente, em vez de usar o tamanho da pilha padrão para esses threads.</span><span class="sxs-lookup"><span data-stu-id="b2125-103">Requests that the common language runtime (CLR) reduce memory use by specifying explicit stack sizes when it creates certain threads that it uses internally, instead of using the default stack size for those threads.</span></span>  
  
 <span data-ttu-id="b2125-104">\<Configuração > elemento</span><span class="sxs-lookup"><span data-stu-id="b2125-104">\<configuration> Element</span></span>  
<span data-ttu-id="b2125-105">\<tempo de execução > elemento</span><span class="sxs-lookup"><span data-stu-id="b2125-105">\<runtime> Element</span></span>  
<span data-ttu-id="b2125-106">\<UseSmallInternalThreadStacks > elemento</span><span class="sxs-lookup"><span data-stu-id="b2125-106">\<UseSmallInternalThreadStacks> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2125-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b2125-107">Syntax</span></span>  
  
```xml  
<UseSmallInternalThreadStacks enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b2125-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="b2125-108">Attributes and Elements</span></span>  
 <span data-ttu-id="b2125-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="b2125-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b2125-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="b2125-110">Attributes</span></span>  
  
|<span data-ttu-id="b2125-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="b2125-111">Attribute</span></span>|<span data-ttu-id="b2125-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="b2125-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b2125-113">habilitado</span><span class="sxs-lookup"><span data-stu-id="b2125-113">enabled</span></span>|<span data-ttu-id="b2125-114">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="b2125-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="b2125-115">Especifica se deve solicitar que os tamanhos de pilha explícito de uso do CLR em vez do tamanho da pilha padrão ao criar certos threads que ele usa internamente.</span><span class="sxs-lookup"><span data-stu-id="b2125-115">Specifies whether to request that the CLR use explicit stack sizes instead of the default stack size when it creates certain threads that it uses internally.</span></span> <span data-ttu-id="b2125-116">Os tamanhos de pilha explícito são menores que o tamanho da pilha padrão de 1 MB.</span><span class="sxs-lookup"><span data-stu-id="b2125-116">The explicit stack sizes are smaller than the default stack size of 1 MB.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="b2125-117">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="b2125-117">enabled Attribute</span></span>  
  
|<span data-ttu-id="b2125-118">Valor</span><span class="sxs-lookup"><span data-stu-id="b2125-118">Value</span></span>|<span data-ttu-id="b2125-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="b2125-119">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b2125-120">true</span><span class="sxs-lookup"><span data-stu-id="b2125-120">true</span></span>|<span data-ttu-id="b2125-121">Tamanhos de pilha explícito de solicitação.</span><span class="sxs-lookup"><span data-stu-id="b2125-121">Request explicit stack sizes.</span></span>|  
|<span data-ttu-id="b2125-122">false</span><span class="sxs-lookup"><span data-stu-id="b2125-122">false</span></span>|<span data-ttu-id="b2125-123">Use o tamanho da pilha padrão.</span><span class="sxs-lookup"><span data-stu-id="b2125-123">Use the default stack size.</span></span> <span data-ttu-id="b2125-124">Esse é o padrão para o [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b2125-124">This is the default for the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)].</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b2125-125">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="b2125-125">Child Elements</span></span>  
 <span data-ttu-id="b2125-126">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="b2125-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b2125-127">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="b2125-127">Parent Elements</span></span>  
  
|<span data-ttu-id="b2125-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="b2125-128">Element</span></span>|<span data-ttu-id="b2125-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="b2125-129">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="b2125-130">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b2125-130">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="b2125-131">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="b2125-131">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b2125-132">Comentários</span><span class="sxs-lookup"><span data-stu-id="b2125-132">Remarks</span></span>  
 <span data-ttu-id="b2125-133">Este elemento de configuração é usado para solicitar o uso de memória reduzido de virtual em um processo, porque os tamanhos de thread explícitos que o CLR usa para seus threads internos, se a solicitação é atendida, são menores do que o tamanho padrão.</span><span class="sxs-lookup"><span data-stu-id="b2125-133">This configuration element is used to request reduced virtual memory use in a process, because the explicit thread sizes that the CLR uses for its internal threads, if the request is honored, are smaller than the default size.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b2125-134">Este elemento de configuração é uma solicitação para o CLR em vez de um requisito absoluto.</span><span class="sxs-lookup"><span data-stu-id="b2125-134">This configuration element is a request to the CLR rather than an absolute requirement.</span></span> <span data-ttu-id="b2125-135">No [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], a solicitação é atendida somente para x86 arquitetura.</span><span class="sxs-lookup"><span data-stu-id="b2125-135">In the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], the request is honored only for the x86 architecture.</span></span> <span data-ttu-id="b2125-136">Esse elemento pode ser completamente ignorado em versões futuras do CLR ou substituído pelos tamanhos de pilha explícito que são sempre usados para threads internos selecionados.</span><span class="sxs-lookup"><span data-stu-id="b2125-136">This element might be ignored completely in future versions of the CLR, or replaced by explicit stack sizes that are always used for selected internal threads.</span></span>  
  
 <span data-ttu-id="b2125-137">Especificando a que este elemento de configuração negocia confiabilidade para menor uso de memória virtual se o CLR honra a solicitação, porque os tamanhos menores de pilha poderiam potencialmente tornar pilha estoura mais provável.</span><span class="sxs-lookup"><span data-stu-id="b2125-137">Specifying this configuration element trades reliability for smaller virtual memory use if the CLR honors the request, because smaller stack sizes could potentially make stack overflows more likely.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b2125-138">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b2125-138">Example</span></span>  
 <span data-ttu-id="b2125-139">O exemplo a seguir mostra como solicitar que a pilha explícita de uso do CLR para determinados tamanhos de threads que ele usa internamente.</span><span class="sxs-lookup"><span data-stu-id="b2125-139">The following example shows how to request that the CLR use explicit stack sizes for certain threads that it uses internally.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <UseSmallInternalThreadStacks enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b2125-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b2125-140">See also</span></span>
- [<span data-ttu-id="b2125-141">Esquema de configurações do tempo de execução</span><span class="sxs-lookup"><span data-stu-id="b2125-141">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="b2125-142">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="b2125-142">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
