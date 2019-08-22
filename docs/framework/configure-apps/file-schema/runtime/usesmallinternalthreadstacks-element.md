---
title: Elemento <UseSmallInternalThreadStacks>
ms.date: 03/30/2017
helpviewer_keywords:
- UseSmallInternalThreadStacks element
- <UseSmallInternalThreadStacks> element
ms.assetid: 1e3f6ec0-1cac-4e1c-9c81-17d948ae5874
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 74678089bb1b19295983064eb7ad54fbf0a1e361
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663384"
---
# <a name="usesmallinternalthreadstacks-element"></a><span data-ttu-id="39f98-102">\<Elemento de > UseSmallInternalThreadStacks</span><span class="sxs-lookup"><span data-stu-id="39f98-102">\<UseSmallInternalThreadStacks> Element</span></span>
<span data-ttu-id="39f98-103">Solicita que o Common Language Runtime (CLR) reduza o uso de memória especificando tamanhos de pilha explícitos ao criar determinados threads que ele usa internamente, em vez de usar o tamanho de pilha padrão para esses threads.</span><span class="sxs-lookup"><span data-stu-id="39f98-103">Requests that the common language runtime (CLR) reduce memory use by specifying explicit stack sizes when it creates certain threads that it uses internally, instead of using the default stack size for those threads.</span></span>  
  
 <span data-ttu-id="39f98-104">\<Elemento de > de configuração</span><span class="sxs-lookup"><span data-stu-id="39f98-104">\<configuration> Element</span></span>  
<span data-ttu-id="39f98-105">\<Elemento de > de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="39f98-105">\<runtime> Element</span></span>  
<span data-ttu-id="39f98-106">\<Elemento de > UseSmallInternalThreadStacks</span><span class="sxs-lookup"><span data-stu-id="39f98-106">\<UseSmallInternalThreadStacks> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39f98-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="39f98-107">Syntax</span></span>  
  
```xml  
<UseSmallInternalThreadStacks enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="39f98-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="39f98-108">Attributes and Elements</span></span>  
 <span data-ttu-id="39f98-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="39f98-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="39f98-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="39f98-110">Attributes</span></span>  
  
|<span data-ttu-id="39f98-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="39f98-111">Attribute</span></span>|<span data-ttu-id="39f98-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="39f98-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="39f98-113">habilitado</span><span class="sxs-lookup"><span data-stu-id="39f98-113">enabled</span></span>|<span data-ttu-id="39f98-114">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="39f98-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="39f98-115">Especifica se deve-se solicitar que o CLR use tamanhos de pilha explícitos em vez do tamanho de pilha padrão quando ele cria determinados threads que ele usa internamente.</span><span class="sxs-lookup"><span data-stu-id="39f98-115">Specifies whether to request that the CLR use explicit stack sizes instead of the default stack size when it creates certain threads that it uses internally.</span></span> <span data-ttu-id="39f98-116">Os tamanhos de pilha explícitos são menores do que o tamanho de pilha padrão de 1 MB.</span><span class="sxs-lookup"><span data-stu-id="39f98-116">The explicit stack sizes are smaller than the default stack size of 1 MB.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="39f98-117">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="39f98-117">enabled Attribute</span></span>  
  
|<span data-ttu-id="39f98-118">Valor</span><span class="sxs-lookup"><span data-stu-id="39f98-118">Value</span></span>|<span data-ttu-id="39f98-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="39f98-119">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="39f98-120">true</span><span class="sxs-lookup"><span data-stu-id="39f98-120">true</span></span>|<span data-ttu-id="39f98-121">Solicitar tamanhos de pilha explícitos.</span><span class="sxs-lookup"><span data-stu-id="39f98-121">Request explicit stack sizes.</span></span>|  
|<span data-ttu-id="39f98-122">false</span><span class="sxs-lookup"><span data-stu-id="39f98-122">false</span></span>|<span data-ttu-id="39f98-123">Use o tamanho de pilha padrão.</span><span class="sxs-lookup"><span data-stu-id="39f98-123">Use the default stack size.</span></span> <span data-ttu-id="39f98-124">Esse é o padrão para o .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="39f98-124">This is the default for the .NET Framework 4.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="39f98-125">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="39f98-125">Child Elements</span></span>  
 <span data-ttu-id="39f98-126">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="39f98-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="39f98-127">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="39f98-127">Parent Elements</span></span>  
  
|<span data-ttu-id="39f98-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="39f98-128">Element</span></span>|<span data-ttu-id="39f98-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="39f98-129">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="39f98-130">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="39f98-130">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="39f98-131">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="39f98-131">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="39f98-132">Comentários</span><span class="sxs-lookup"><span data-stu-id="39f98-132">Remarks</span></span>  
 <span data-ttu-id="39f98-133">Esse elemento de configuração é usado para solicitar o uso reduzido de memória virtual em um processo, pois os tamanhos de thread explícitos usados pelo CLR para seus threads internos, se a solicitação for respeitada, serão menores do que o tamanho padrão.</span><span class="sxs-lookup"><span data-stu-id="39f98-133">This configuration element is used to request reduced virtual memory use in a process, because the explicit thread sizes that the CLR uses for its internal threads, if the request is honored, are smaller than the default size.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="39f98-134">Esse elemento de configuração é uma solicitação para o CLR em vez de um requisito absoluto.</span><span class="sxs-lookup"><span data-stu-id="39f98-134">This configuration element is a request to the CLR rather than an absolute requirement.</span></span> <span data-ttu-id="39f98-135">No .NET Framework 4, a solicitação é respeitada apenas para a arquitetura x86.</span><span class="sxs-lookup"><span data-stu-id="39f98-135">In the .NET Framework 4, the request is honored only for the x86 architecture.</span></span> <span data-ttu-id="39f98-136">Esse elemento pode ser ignorado completamente em versões futuras do CLR, ou substituído por tamanhos de pilha explícitos que são sempre usados para threads internos selecionados.</span><span class="sxs-lookup"><span data-stu-id="39f98-136">This element might be ignored completely in future versions of the CLR, or replaced by explicit stack sizes that are always used for selected internal threads.</span></span>  
  
 <span data-ttu-id="39f98-137">A especificação desse elemento de configuração compensa a confiabilidade para uso menor de memória virtual se o CLR honrar a solicitação, porque tamanhos de pilha menores poderiam potencialmente causar estouros de pilha mais prováveis.</span><span class="sxs-lookup"><span data-stu-id="39f98-137">Specifying this configuration element trades reliability for smaller virtual memory use if the CLR honors the request, because smaller stack sizes could potentially make stack overflows more likely.</span></span>  
  
## <a name="example"></a><span data-ttu-id="39f98-138">Exemplo</span><span class="sxs-lookup"><span data-stu-id="39f98-138">Example</span></span>  
 <span data-ttu-id="39f98-139">O exemplo a seguir mostra como solicitar que o CLR use tamanhos de pilha explícitos para determinados threads que ele usa internamente.</span><span class="sxs-lookup"><span data-stu-id="39f98-139">The following example shows how to request that the CLR use explicit stack sizes for certain threads that it uses internally.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <UseSmallInternalThreadStacks enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="39f98-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="39f98-140">See also</span></span>

- [<span data-ttu-id="39f98-141">Esquema de configurações do tempo de execução</span><span class="sxs-lookup"><span data-stu-id="39f98-141">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="39f98-142">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="39f98-142">Configuration File Schema</span></span>](../index.md)
