---
title: '&lt;disableCommitThreadStack&gt; elemento'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/disableCommitThreadStack
- http://schemas.microsoft.com/.NetConfiguration/v2.0#disableCommitThreadStack
helpviewer_keywords:
- <disableCommitThreadStack> element
- disableCommitThreadStack element
ms.assetid: 3559d46a-7640-4c72-9a11-7e980768929e
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8d74566b71501cf21081ac894048bb1c29e0ad94
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ltdisablecommitthreadstackgt-element"></a><span data-ttu-id="d542e-102">&lt;disableCommitThreadStack&gt; elemento</span><span class="sxs-lookup"><span data-stu-id="d542e-102">&lt;disableCommitThreadStack&gt; Element</span></span>
<span data-ttu-id="d542e-103">Especifica se a pilha do thread completo é confirmada quando um thread é iniciado.</span><span class="sxs-lookup"><span data-stu-id="d542e-103">Specifies whether the full thread stack is committed when a thread is started.</span></span>  
  
 <span data-ttu-id="d542e-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="d542e-104">\<configuration></span></span>  
<span data-ttu-id="d542e-105">\<tempo de execução ></span><span class="sxs-lookup"><span data-stu-id="d542e-105">\<runtime></span></span>  
<span data-ttu-id="d542e-106">\<disableCommitThreadStack ></span><span class="sxs-lookup"><span data-stu-id="d542e-106">\<disableCommitThreadStack></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d542e-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d542e-107">Syntax</span></span>  
  
```xml  
<disableCommitThreadStack enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d542e-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="d542e-108">Attributes and Elements</span></span>  
 <span data-ttu-id="d542e-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="d542e-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d542e-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="d542e-110">Attributes</span></span>  
  
|<span data-ttu-id="d542e-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="d542e-111">Attribute</span></span>|<span data-ttu-id="d542e-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="d542e-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d542e-113">Habilitado</span><span class="sxs-lookup"><span data-stu-id="d542e-113">enabled</span></span>|<span data-ttu-id="d542e-114">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="d542e-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="d542e-115">Especifica se a confirmação a pilha do thread completa na inicialização do thread (o comportamento padrão) está desabilitado.</span><span class="sxs-lookup"><span data-stu-id="d542e-115">Specifies whether committing the full thread stack on thread startup (the default behavior) is disabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="d542e-116">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="d542e-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="d542e-117">Valor</span><span class="sxs-lookup"><span data-stu-id="d542e-117">Value</span></span>|<span data-ttu-id="d542e-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="d542e-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d542e-119">0</span><span class="sxs-lookup"><span data-stu-id="d542e-119">0</span></span>|<span data-ttu-id="d542e-120">Não desabilite o comportamento padrão do common language runtime, que é confirmar a pilha do thread completo quando um thread é iniciado.</span><span class="sxs-lookup"><span data-stu-id="d542e-120">Do not disable the default behavior of the common language runtime, which is to commit the full thread stack when a thread is started.</span></span>|  
|<span data-ttu-id="d542e-121">1</span><span class="sxs-lookup"><span data-stu-id="d542e-121">1</span></span>|<span data-ttu-id="d542e-122">Desabilite o comportamento padrão do common language runtime, que é confirmar a pilha do thread completo quando um thread é iniciado.</span><span class="sxs-lookup"><span data-stu-id="d542e-122">Disable the default behavior of the common language runtime, which is to commit the full thread stack when a thread is started.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d542e-123">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="d542e-123">Child Elements</span></span>  
 <span data-ttu-id="d542e-124">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="d542e-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d542e-125">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="d542e-125">Parent Elements</span></span>  
  
|<span data-ttu-id="d542e-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="d542e-126">Element</span></span>|<span data-ttu-id="d542e-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="d542e-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="d542e-128">O elemento raiz em cada arquivo de configuração usado pelo common language runtime e [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] aplicativos.</span><span class="sxs-lookup"><span data-stu-id="d542e-128">The root element in every configuration file used by the common language runtime and [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] applications.</span></span>|  
|`runtime`|<span data-ttu-id="d542e-129">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="d542e-129">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d542e-130">Comentários</span><span class="sxs-lookup"><span data-stu-id="d542e-130">Remarks</span></span>  
 <span data-ttu-id="d542e-131">É o comportamento padrão do common language runtime confirmar a pilha do thread completo quando um thread é iniciado.</span><span class="sxs-lookup"><span data-stu-id="d542e-131">The default behavior of the common language runtime is to commit the full thread stack when a thread is started.</span></span> <span data-ttu-id="d542e-132">Se um grande número de threads deve ser criado em um servidor que tem memória limitada, e a maioria desses threads usará muito pouco espaço de pilha, o servidor pode executar melhor se o common language runtime não confirma a pilha do thread completo imediatamente quando um thread é st arted.</span><span class="sxs-lookup"><span data-stu-id="d542e-132">If a large number of threads must be created on a server that has limited memory, and most of those threads will use very little stack space, the server might perform better if the common language runtime does not commit the full thread stack immediately when a thread is started.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d542e-133">Os hosts gerenciados podem usar o `STARTUP_DISABLE_COMMITTHREADSTACK` sinalizador de inicialização no [STARTUP_FLAGS](../../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) enumeração para obter o mesmo resultado.</span><span class="sxs-lookup"><span data-stu-id="d542e-133">Unmanaged hosts can use the `STARTUP_DISABLE_COMMITTHREADSTACK` startup flag in the [STARTUP_FLAGS](../../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) enumeration to accomplish the same result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d542e-134">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d542e-134">Example</span></span>  
 <span data-ttu-id="d542e-135">O exemplo a seguir mostra como desabilitar o comportamento padrão do common language runtime, que é preciso confirmar a pilha do thread completa na inicialização do thread.</span><span class="sxs-lookup"><span data-stu-id="d542e-135">The following example shows how to disable the default behavior of the common language runtime, which is to commit the full thread stack on thread startup.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <disableCommitThreadStack enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d542e-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d542e-136">See Also</span></span>  
 [<span data-ttu-id="d542e-137">Esquema de configurações do tempo de execução</span><span class="sxs-lookup"><span data-stu-id="d542e-137">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="d542e-138">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="d542e-138">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
