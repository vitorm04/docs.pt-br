---
title: Elemento <disableCommitThreadStack>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/disableCommitThreadStack
- http://schemas.microsoft.com/.NetConfiguration/v2.0#disableCommitThreadStack
helpviewer_keywords:
- <disableCommitThreadStack> element
- disableCommitThreadStack element
ms.assetid: 3559d46a-7640-4c72-9a11-7e980768929e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4b1f55f056ef1aed4a5eff655650cefe778c97ae
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663791"
---
# <a name="disablecommitthreadstack-element"></a><span data-ttu-id="e1bc9-102">\<Elemento de > disableCommitThreadStack</span><span class="sxs-lookup"><span data-stu-id="e1bc9-102">\<disableCommitThreadStack> Element</span></span>
<span data-ttu-id="e1bc9-103">Especifica se a pilha de threads completa é confirmada quando um thread é iniciado.</span><span class="sxs-lookup"><span data-stu-id="e1bc9-103">Specifies whether the full thread stack is committed when a thread is started.</span></span>  
  
 <span data-ttu-id="e1bc9-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="e1bc9-104">\<configuration></span></span>  
<span data-ttu-id="e1bc9-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="e1bc9-105">\<runtime></span></span>  
<span data-ttu-id="e1bc9-106">\<disableCommitThreadStack></span><span class="sxs-lookup"><span data-stu-id="e1bc9-106">\<disableCommitThreadStack></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1bc9-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e1bc9-107">Syntax</span></span>  
  
```xml  
<disableCommitThreadStack enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e1bc9-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="e1bc9-108">Attributes and Elements</span></span>  
 <span data-ttu-id="e1bc9-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="e1bc9-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e1bc9-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="e1bc9-110">Attributes</span></span>  
  
|<span data-ttu-id="e1bc9-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="e1bc9-111">Attribute</span></span>|<span data-ttu-id="e1bc9-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="e1bc9-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e1bc9-113">habilitado</span><span class="sxs-lookup"><span data-stu-id="e1bc9-113">enabled</span></span>|<span data-ttu-id="e1bc9-114">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="e1bc9-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="e1bc9-115">Especifica se a confirmação da pilha de threads completa na inicialização do thread (o comportamento padrão) está desabilitada.</span><span class="sxs-lookup"><span data-stu-id="e1bc9-115">Specifies whether committing the full thread stack on thread startup (the default behavior) is disabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="e1bc9-116">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="e1bc9-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="e1bc9-117">Valor</span><span class="sxs-lookup"><span data-stu-id="e1bc9-117">Value</span></span>|<span data-ttu-id="e1bc9-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="e1bc9-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e1bc9-119">0</span><span class="sxs-lookup"><span data-stu-id="e1bc9-119">0</span></span>|<span data-ttu-id="e1bc9-120">Não desabilite o comportamento padrão do Common Language Runtime, que é confirmar a pilha de threads completa quando um thread é iniciado.</span><span class="sxs-lookup"><span data-stu-id="e1bc9-120">Do not disable the default behavior of the common language runtime, which is to commit the full thread stack when a thread is started.</span></span>|  
|<span data-ttu-id="e1bc9-121">1</span><span class="sxs-lookup"><span data-stu-id="e1bc9-121">1</span></span>|<span data-ttu-id="e1bc9-122">Desabilite o comportamento padrão do Common Language Runtime, que é confirmar a pilha de threads completa quando um thread é iniciado.</span><span class="sxs-lookup"><span data-stu-id="e1bc9-122">Disable the default behavior of the common language runtime, which is to commit the full thread stack when a thread is started.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e1bc9-123">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="e1bc9-123">Child Elements</span></span>  
 <span data-ttu-id="e1bc9-124">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="e1bc9-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e1bc9-125">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="e1bc9-125">Parent Elements</span></span>  
  
|<span data-ttu-id="e1bc9-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="e1bc9-126">Element</span></span>|<span data-ttu-id="e1bc9-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="e1bc9-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="e1bc9-128">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e1bc9-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="e1bc9-129">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="e1bc9-129">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e1bc9-130">Comentários</span><span class="sxs-lookup"><span data-stu-id="e1bc9-130">Remarks</span></span>  
 <span data-ttu-id="e1bc9-131">O comportamento padrão da Common Language Runtime é confirmar a pilha de threads completa quando um thread é iniciado.</span><span class="sxs-lookup"><span data-stu-id="e1bc9-131">The default behavior of the common language runtime is to commit the full thread stack when a thread is started.</span></span> <span data-ttu-id="e1bc9-132">Se um grande número de threads precisar ser criado em um servidor com memória limitada e a maioria desses threads usarem muito pouco espaço de pilha, o servidor poderá executar melhor se o Common Language Runtime não confirmar a pilha de thread completa imediatamente quando um thread for St iniciado.</span><span class="sxs-lookup"><span data-stu-id="e1bc9-132">If a large number of threads must be created on a server that has limited memory, and most of those threads will use very little stack space, the server might perform better if the common language runtime does not commit the full thread stack immediately when a thread is started.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e1bc9-133">Os hosts não gerenciados podem `STARTUP_DISABLE_COMMITTHREADSTACK` usar o sinalizador de inicialização na enumeração [STARTUP_FLAGS](../../../unmanaged-api/hosting/startup-flags-enumeration.md) para realizar o mesmo resultado.</span><span class="sxs-lookup"><span data-stu-id="e1bc9-133">Unmanaged hosts can use the `STARTUP_DISABLE_COMMITTHREADSTACK` startup flag in the [STARTUP_FLAGS](../../../unmanaged-api/hosting/startup-flags-enumeration.md) enumeration to accomplish the same result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e1bc9-134">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e1bc9-134">Example</span></span>  
 <span data-ttu-id="e1bc9-135">O exemplo a seguir mostra como desabilitar o comportamento padrão do Common Language Runtime, que é confirmar a pilha de threads completa na inicialização do thread.</span><span class="sxs-lookup"><span data-stu-id="e1bc9-135">The following example shows how to disable the default behavior of the common language runtime, which is to commit the full thread stack on thread startup.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <disableCommitThreadStack enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e1bc9-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e1bc9-136">See also</span></span>

- [<span data-ttu-id="e1bc9-137">Esquema de configurações do tempo de execução</span><span class="sxs-lookup"><span data-stu-id="e1bc9-137">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="e1bc9-138">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="e1bc9-138">Configuration File Schema</span></span>](../index.md)
