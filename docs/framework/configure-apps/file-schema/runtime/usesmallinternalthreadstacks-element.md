---
title: Elemento <UseSmallInternalThreadStacks>
ms.date: 03/30/2017
helpviewer_keywords:
- UseSmallInternalThreadStacks element
- <UseSmallInternalThreadStacks> element
ms.assetid: 1e3f6ec0-1cac-4e1c-9c81-17d948ae5874
ms.openlocfilehash: 4917b47e9e8196eabe691f74531d12308ef80311
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91174076"
---
# <a name="usesmallinternalthreadstacks-element"></a><span data-ttu-id="2b679-102">Elemento \<UseSmallInternalThreadStacks></span><span class="sxs-lookup"><span data-stu-id="2b679-102">\<UseSmallInternalThreadStacks> Element</span></span>

<span data-ttu-id="2b679-103">Solicita que o Common Language Runtime (CLR) reduza o uso de memória especificando tamanhos de pilha explícitos ao criar determinados threads que ele usa internamente, em vez de usar o tamanho de pilha padrão para esses threads.</span><span class="sxs-lookup"><span data-stu-id="2b679-103">Requests that the common language runtime (CLR) reduce memory use by specifying explicit stack sizes when it creates certain threads that it uses internally, instead of using the default stack size for those threads.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<UseSmallInternalThreadStacks>**  
  
## <a name="syntax"></a><span data-ttu-id="2b679-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2b679-104">Syntax</span></span>  
  
```xml  
<UseSmallInternalThreadStacks enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2b679-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="2b679-105">Attributes and Elements</span></span>  

 <span data-ttu-id="2b679-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="2b679-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2b679-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="2b679-107">Attributes</span></span>  
  
|<span data-ttu-id="2b679-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="2b679-108">Attribute</span></span>|<span data-ttu-id="2b679-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="2b679-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2b679-110">Habilitado</span><span class="sxs-lookup"><span data-stu-id="2b679-110">enabled</span></span>|<span data-ttu-id="2b679-111">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="2b679-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="2b679-112">Especifica se deve-se solicitar que o CLR use tamanhos de pilha explícitos em vez do tamanho de pilha padrão quando ele cria determinados threads que ele usa internamente.</span><span class="sxs-lookup"><span data-stu-id="2b679-112">Specifies whether to request that the CLR use explicit stack sizes instead of the default stack size when it creates certain threads that it uses internally.</span></span> <span data-ttu-id="2b679-113">Os tamanhos de pilha explícitos são menores do que o tamanho de pilha padrão de 1 MB.</span><span class="sxs-lookup"><span data-stu-id="2b679-113">The explicit stack sizes are smaller than the default stack size of 1 MB.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="2b679-114">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="2b679-114">enabled Attribute</span></span>  
  
|<span data-ttu-id="2b679-115">Valor</span><span class="sxs-lookup"><span data-stu-id="2b679-115">Value</span></span>|<span data-ttu-id="2b679-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="2b679-116">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="2b679-117">true</span><span class="sxs-lookup"><span data-stu-id="2b679-117">true</span></span>|<span data-ttu-id="2b679-118">Solicitar tamanhos de pilha explícitos.</span><span class="sxs-lookup"><span data-stu-id="2b679-118">Request explicit stack sizes.</span></span>|  
|<span data-ttu-id="2b679-119">false</span><span class="sxs-lookup"><span data-stu-id="2b679-119">false</span></span>|<span data-ttu-id="2b679-120">Use o tamanho de pilha padrão.</span><span class="sxs-lookup"><span data-stu-id="2b679-120">Use the default stack size.</span></span> <span data-ttu-id="2b679-121">Esse é o padrão para o .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="2b679-121">This is the default for the .NET Framework 4.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2b679-122">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="2b679-122">Child Elements</span></span>  

 <span data-ttu-id="2b679-123">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="2b679-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2b679-124">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="2b679-124">Parent Elements</span></span>  
  
|<span data-ttu-id="2b679-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="2b679-125">Element</span></span>|<span data-ttu-id="2b679-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="2b679-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="2b679-127">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2b679-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="2b679-128">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="2b679-128">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2b679-129">Comentários</span><span class="sxs-lookup"><span data-stu-id="2b679-129">Remarks</span></span>  

 <span data-ttu-id="2b679-130">Esse elemento de configuração é usado para solicitar o uso reduzido de memória virtual em um processo, pois os tamanhos de thread explícitos usados pelo CLR para seus threads internos, se a solicitação for respeitada, serão menores do que o tamanho padrão.</span><span class="sxs-lookup"><span data-stu-id="2b679-130">This configuration element is used to request reduced virtual memory use in a process, because the explicit thread sizes that the CLR uses for its internal threads, if the request is honored, are smaller than the default size.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="2b679-131">Esse elemento de configuração é uma solicitação para o CLR em vez de um requisito absoluto.</span><span class="sxs-lookup"><span data-stu-id="2b679-131">This configuration element is a request to the CLR rather than an absolute requirement.</span></span> <span data-ttu-id="2b679-132">No .NET Framework 4, a solicitação é respeitada apenas para a arquitetura x86.</span><span class="sxs-lookup"><span data-stu-id="2b679-132">In the .NET Framework 4, the request is honored only for the x86 architecture.</span></span> <span data-ttu-id="2b679-133">Esse elemento pode ser ignorado completamente em versões futuras do CLR, ou substituído por tamanhos de pilha explícitos que são sempre usados para threads internos selecionados.</span><span class="sxs-lookup"><span data-stu-id="2b679-133">This element might be ignored completely in future versions of the CLR, or replaced by explicit stack sizes that are always used for selected internal threads.</span></span>  
  
 <span data-ttu-id="2b679-134">A especificação desse elemento de configuração compensa a confiabilidade para uso menor de memória virtual se o CLR honrar a solicitação, porque tamanhos de pilha menores poderiam potencialmente causar estouros de pilha mais prováveis.</span><span class="sxs-lookup"><span data-stu-id="2b679-134">Specifying this configuration element trades reliability for smaller virtual memory use if the CLR honors the request, because smaller stack sizes could potentially make stack overflows more likely.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2b679-135">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2b679-135">Example</span></span>  

 <span data-ttu-id="2b679-136">O exemplo a seguir mostra como solicitar que o CLR use tamanhos de pilha explícitos para determinados threads que ele usa internamente.</span><span class="sxs-lookup"><span data-stu-id="2b679-136">The following example shows how to request that the CLR use explicit stack sizes for certain threads that it uses internally.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <UseSmallInternalThreadStacks enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2b679-137">Confira também</span><span class="sxs-lookup"><span data-stu-id="2b679-137">See also</span></span>

- [<span data-ttu-id="2b679-138">Esquema de configurações do runtime</span><span class="sxs-lookup"><span data-stu-id="2b679-138">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="2b679-139">Esquema do arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="2b679-139">Configuration File Schema</span></span>](../index.md)
