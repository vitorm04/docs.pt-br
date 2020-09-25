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
ms.openlocfilehash: f717f57fe8670b126ed1468713a2114aaa772762
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91198984"
---
# <a name="disablecommitthreadstack-element"></a><span data-ttu-id="00e69-102">Elemento \<disableCommitThreadStack></span><span class="sxs-lookup"><span data-stu-id="00e69-102">\<disableCommitThreadStack> Element</span></span>

<span data-ttu-id="00e69-103">Especifica se a pilha de threads completa é confirmada quando um thread é iniciado.</span><span class="sxs-lookup"><span data-stu-id="00e69-103">Specifies whether the full thread stack is committed when a thread is started.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<disableCommitThreadStack>**  
  
## <a name="syntax"></a><span data-ttu-id="00e69-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="00e69-104">Syntax</span></span>  
  
```xml  
<disableCommitThreadStack enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="00e69-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="00e69-105">Attributes and Elements</span></span>  

 <span data-ttu-id="00e69-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="00e69-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="00e69-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="00e69-107">Attributes</span></span>  
  
|<span data-ttu-id="00e69-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="00e69-108">Attribute</span></span>|<span data-ttu-id="00e69-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="00e69-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="00e69-110">Habilitado</span><span class="sxs-lookup"><span data-stu-id="00e69-110">enabled</span></span>|<span data-ttu-id="00e69-111">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="00e69-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="00e69-112">Especifica se a confirmação da pilha de threads completa na inicialização do thread (o comportamento padrão) está desabilitada.</span><span class="sxs-lookup"><span data-stu-id="00e69-112">Specifies whether committing the full thread stack on thread startup (the default behavior) is disabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="00e69-113">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="00e69-113">enabled Attribute</span></span>  
  
|<span data-ttu-id="00e69-114">Valor</span><span class="sxs-lookup"><span data-stu-id="00e69-114">Value</span></span>|<span data-ttu-id="00e69-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="00e69-115">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="00e69-116">0</span><span class="sxs-lookup"><span data-stu-id="00e69-116">0</span></span>|<span data-ttu-id="00e69-117">Não desabilite o comportamento padrão do Common Language Runtime, que é confirmar a pilha de threads completa quando um thread é iniciado.</span><span class="sxs-lookup"><span data-stu-id="00e69-117">Do not disable the default behavior of the common language runtime, which is to commit the full thread stack when a thread is started.</span></span>|  
|<span data-ttu-id="00e69-118">1</span><span class="sxs-lookup"><span data-stu-id="00e69-118">1</span></span>|<span data-ttu-id="00e69-119">Desabilite o comportamento padrão do Common Language Runtime, que é confirmar a pilha de threads completa quando um thread é iniciado.</span><span class="sxs-lookup"><span data-stu-id="00e69-119">Disable the default behavior of the common language runtime, which is to commit the full thread stack when a thread is started.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="00e69-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="00e69-120">Child Elements</span></span>  

 <span data-ttu-id="00e69-121">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="00e69-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="00e69-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="00e69-122">Parent Elements</span></span>  
  
|<span data-ttu-id="00e69-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="00e69-123">Element</span></span>|<span data-ttu-id="00e69-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="00e69-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="00e69-125">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="00e69-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="00e69-126">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="00e69-126">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="00e69-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="00e69-127">Remarks</span></span>  

 <span data-ttu-id="00e69-128">O comportamento padrão da Common Language Runtime é confirmar a pilha de threads completa quando um thread é iniciado.</span><span class="sxs-lookup"><span data-stu-id="00e69-128">The default behavior of the common language runtime is to commit the full thread stack when a thread is started.</span></span> <span data-ttu-id="00e69-129">Se um grande número de threads precisar ser criado em um servidor com memória limitada e a maioria desses threads usarem muito pouco espaço de pilha, o servidor poderá executar melhor se o Common Language Runtime não confirmar a pilha de thread completa imediatamente quando um thread for iniciado.</span><span class="sxs-lookup"><span data-stu-id="00e69-129">If a large number of threads must be created on a server that has limited memory, and most of those threads will use very little stack space, the server might perform better if the common language runtime does not commit the full thread stack immediately when a thread is started.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="00e69-130">Os hosts não gerenciados podem usar o `STARTUP_DISABLE_COMMITTHREADSTACK` sinalizador de inicialização na enumeração de [STARTUP_FLAGS](../../../unmanaged-api/hosting/startup-flags-enumeration.md) para realizar o mesmo resultado.</span><span class="sxs-lookup"><span data-stu-id="00e69-130">Unmanaged hosts can use the `STARTUP_DISABLE_COMMITTHREADSTACK` startup flag in the [STARTUP_FLAGS](../../../unmanaged-api/hosting/startup-flags-enumeration.md) enumeration to accomplish the same result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="00e69-131">Exemplo</span><span class="sxs-lookup"><span data-stu-id="00e69-131">Example</span></span>  

 <span data-ttu-id="00e69-132">O exemplo a seguir mostra como desabilitar o comportamento padrão do Common Language Runtime, que é confirmar a pilha de threads completa na inicialização do thread.</span><span class="sxs-lookup"><span data-stu-id="00e69-132">The following example shows how to disable the default behavior of the common language runtime, which is to commit the full thread stack on thread startup.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <disableCommitThreadStack enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="00e69-133">Veja também</span><span class="sxs-lookup"><span data-stu-id="00e69-133">See also</span></span>

- [<span data-ttu-id="00e69-134">Esquema de configurações do runtime</span><span class="sxs-lookup"><span data-stu-id="00e69-134">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="00e69-135">Esquema do arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="00e69-135">Configuration File Schema</span></span>](../index.md)
