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
ms.openlocfilehash: 2fa32d64f3ce440981c5f26d731051a118ed9254
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252663"
---
# <a name="disablecommitthreadstack-element"></a><span data-ttu-id="0d45c-102">\<Elemento de > disableCommitThreadStack</span><span class="sxs-lookup"><span data-stu-id="0d45c-102">\<disableCommitThreadStack> Element</span></span>
<span data-ttu-id="0d45c-103">Especifica se a pilha de threads completa é confirmada quando um thread é iniciado.</span><span class="sxs-lookup"><span data-stu-id="0d45c-103">Specifies whether the full thread stack is committed when a thread is started.</span></span>  
  
<span data-ttu-id="0d45c-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="0d45c-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="0d45c-105">&nbsp;&nbsp;[ **\<> de tempo de execução**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="0d45c-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="0d45c-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<disableCommitThreadStack>**</span><span class="sxs-lookup"><span data-stu-id="0d45c-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<disableCommitThreadStack>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d45c-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0d45c-107">Syntax</span></span>  
  
```xml  
<disableCommitThreadStack enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0d45c-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="0d45c-108">Attributes and Elements</span></span>  
 <span data-ttu-id="0d45c-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="0d45c-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0d45c-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="0d45c-110">Attributes</span></span>  
  
|<span data-ttu-id="0d45c-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="0d45c-111">Attribute</span></span>|<span data-ttu-id="0d45c-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="0d45c-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0d45c-113">enabled</span><span class="sxs-lookup"><span data-stu-id="0d45c-113">enabled</span></span>|<span data-ttu-id="0d45c-114">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="0d45c-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="0d45c-115">Especifica se a confirmação da pilha de threads completa na inicialização do thread (o comportamento padrão) está desabilitada.</span><span class="sxs-lookup"><span data-stu-id="0d45c-115">Specifies whether committing the full thread stack on thread startup (the default behavior) is disabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="0d45c-116">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="0d45c-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="0d45c-117">Valor</span><span class="sxs-lookup"><span data-stu-id="0d45c-117">Value</span></span>|<span data-ttu-id="0d45c-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="0d45c-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0d45c-119">0</span><span class="sxs-lookup"><span data-stu-id="0d45c-119">0</span></span>|<span data-ttu-id="0d45c-120">Não desabilite o comportamento padrão do Common Language Runtime, que é confirmar a pilha de threads completa quando um thread é iniciado.</span><span class="sxs-lookup"><span data-stu-id="0d45c-120">Do not disable the default behavior of the common language runtime, which is to commit the full thread stack when a thread is started.</span></span>|  
|<span data-ttu-id="0d45c-121">1</span><span class="sxs-lookup"><span data-stu-id="0d45c-121">1</span></span>|<span data-ttu-id="0d45c-122">Desabilite o comportamento padrão do Common Language Runtime, que é confirmar a pilha de threads completa quando um thread é iniciado.</span><span class="sxs-lookup"><span data-stu-id="0d45c-122">Disable the default behavior of the common language runtime, which is to commit the full thread stack when a thread is started.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0d45c-123">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="0d45c-123">Child Elements</span></span>  
 <span data-ttu-id="0d45c-124">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="0d45c-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0d45c-125">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="0d45c-125">Parent Elements</span></span>  
  
|<span data-ttu-id="0d45c-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="0d45c-126">Element</span></span>|<span data-ttu-id="0d45c-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="0d45c-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="0d45c-128">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0d45c-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="0d45c-129">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="0d45c-129">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0d45c-130">Comentários</span><span class="sxs-lookup"><span data-stu-id="0d45c-130">Remarks</span></span>  
 <span data-ttu-id="0d45c-131">O comportamento padrão da Common Language Runtime é confirmar a pilha de threads completa quando um thread é iniciado.</span><span class="sxs-lookup"><span data-stu-id="0d45c-131">The default behavior of the common language runtime is to commit the full thread stack when a thread is started.</span></span> <span data-ttu-id="0d45c-132">Se um grande número de threads precisar ser criado em um servidor com memória limitada e a maioria desses threads usarem muito pouco espaço de pilha, o servidor poderá executar melhor se o Common Language Runtime não confirmar a pilha de thread completa imediatamente quando um thread for St iniciado.</span><span class="sxs-lookup"><span data-stu-id="0d45c-132">If a large number of threads must be created on a server that has limited memory, and most of those threads will use very little stack space, the server might perform better if the common language runtime does not commit the full thread stack immediately when a thread is started.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0d45c-133">Os hosts não gerenciados podem `STARTUP_DISABLE_COMMITTHREADSTACK` usar o sinalizador de inicialização na enumeração [STARTUP_FLAGS](../../../unmanaged-api/hosting/startup-flags-enumeration.md) para realizar o mesmo resultado.</span><span class="sxs-lookup"><span data-stu-id="0d45c-133">Unmanaged hosts can use the `STARTUP_DISABLE_COMMITTHREADSTACK` startup flag in the [STARTUP_FLAGS](../../../unmanaged-api/hosting/startup-flags-enumeration.md) enumeration to accomplish the same result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0d45c-134">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0d45c-134">Example</span></span>  
 <span data-ttu-id="0d45c-135">O exemplo a seguir mostra como desabilitar o comportamento padrão do Common Language Runtime, que é confirmar a pilha de threads completa na inicialização do thread.</span><span class="sxs-lookup"><span data-stu-id="0d45c-135">The following example shows how to disable the default behavior of the common language runtime, which is to commit the full thread stack on thread startup.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <disableCommitThreadStack enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0d45c-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0d45c-136">See also</span></span>

- [<span data-ttu-id="0d45c-137">Esquema de configurações do tempo de execução</span><span class="sxs-lookup"><span data-stu-id="0d45c-137">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="0d45c-138">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="0d45c-138">Configuration File Schema</span></span>](../index.md)
