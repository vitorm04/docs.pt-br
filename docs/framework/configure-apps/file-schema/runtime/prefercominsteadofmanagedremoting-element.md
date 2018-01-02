---
title: '&lt;PreferComInsteadOfManagedRemoting&gt; elemento'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- <PreferComInsteadOfManagedRemoting> element
- PreferComInsteadOfManagedRemoting element
ms.assetid: a279a42a-c415-4e79-88cf-64244ebda613
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ad60d73e30bf02fd52f9c8f3bd707b571959bdd0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltprefercominsteadofmanagedremotinggt-element"></a><span data-ttu-id="484f2-102">&lt;PreferComInsteadOfManagedRemoting&gt; elemento</span><span class="sxs-lookup"><span data-stu-id="484f2-102">&lt;PreferComInsteadOfManagedRemoting&gt; Element</span></span>
<span data-ttu-id="484f2-103">Especifica se o tempo de execução usará interoperabilidade COM, em vez de comunicação remota para todas as chamadas entre limites de domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="484f2-103">Specifies whether the runtime will use COM interop instead of remoting for all calls across application domain boundaries.</span></span>  
  
 <span data-ttu-id="484f2-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="484f2-104">\<configuration></span></span>  
<span data-ttu-id="484f2-105">\<tempo de execução ></span><span class="sxs-lookup"><span data-stu-id="484f2-105">\<runtime></span></span>  
<span data-ttu-id="484f2-106">\<PreferComInsteadOfManagedRemoting ></span><span class="sxs-lookup"><span data-stu-id="484f2-106">\<PreferComInsteadOfManagedRemoting></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="484f2-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="484f2-107">Syntax</span></span>  
  
```xml  
<PreferComInsteadOfManagedRemoting enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="484f2-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="484f2-108">Attributes and Elements</span></span>  
 <span data-ttu-id="484f2-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="484f2-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="484f2-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="484f2-110">Attributes</span></span>  
  
|<span data-ttu-id="484f2-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="484f2-111">Attribute</span></span>|<span data-ttu-id="484f2-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="484f2-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="484f2-113">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="484f2-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="484f2-114">Indica se o tempo de execução usará a interoperabilidade COM, em vez de comunicação remota entre limites de domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="484f2-114">Indicates whether the runtime will use COM interop instead of remoting across application domain boundaries.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="484f2-115">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="484f2-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="484f2-116">Valor</span><span class="sxs-lookup"><span data-stu-id="484f2-116">Value</span></span>|<span data-ttu-id="484f2-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="484f2-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="484f2-118">O tempo de execução usará a comunicação remota entre limites de domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="484f2-118">The runtime will use remoting across application domain boundaries.</span></span> <span data-ttu-id="484f2-119">Esse é o padrão.</span><span class="sxs-lookup"><span data-stu-id="484f2-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="484f2-120">O tempo de execução usará a interoperabilidade entre limites de domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="484f2-120">The runtime will use COM interop across application domain boundaries.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="484f2-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="484f2-121">Child Elements</span></span>  
 <span data-ttu-id="484f2-122">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="484f2-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="484f2-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="484f2-123">Parent Elements</span></span>  
  
|<span data-ttu-id="484f2-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="484f2-124">Element</span></span>|<span data-ttu-id="484f2-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="484f2-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="484f2-126">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="484f2-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="484f2-127">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="484f2-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="484f2-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="484f2-128">Remarks</span></span>  
 <span data-ttu-id="484f2-129">Quando você define o `enabled` atributo `true`, o tempo de execução se comporta da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="484f2-129">When you set the `enabled` attribute to `true`, the runtime behaves as follows:</span></span>  
  
-   <span data-ttu-id="484f2-130">O tempo de execução não chama [IUnknown:: QueryInterface](http://go.microsoft.com/fwlink/?LinkID=144867) para um [IManagedObject](../../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md) interface quando um [IUnknown](http://go.microsoft.com/fwlink/?LinkId=148003) interface entra do domínio por meio de uma interface COM.</span><span class="sxs-lookup"><span data-stu-id="484f2-130">The runtime does not call [IUnknown::QueryInterface](http://go.microsoft.com/fwlink/?LinkID=144867) for an [IManagedObject](../../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md) interface when an [IUnknown](http://go.microsoft.com/fwlink/?LinkId=148003) interface enters the domain through a COM interface.</span></span> <span data-ttu-id="484f2-131">Em vez disso, ele cria um [Runtime Callable Wrapper](../../../../../docs/framework/interop/runtime-callable-wrapper.md) (RCW) em torno do objeto.</span><span class="sxs-lookup"><span data-stu-id="484f2-131">Instead, it constructs a [Runtime Callable Wrapper](../../../../../docs/framework/interop/runtime-callable-wrapper.md) (RCW) around the object.</span></span>  
  
-   <span data-ttu-id="484f2-132">O tempo de execução retorna E_NOINTERFACE quando ele recebe um `QueryInterface` pedir um [IManagedObject](../../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md) interface para qualquer [COM Callable Wrapper](../../../../../docs/framework/interop/com-callable-wrapper.md) (CCW) que foi criado neste domínio.</span><span class="sxs-lookup"><span data-stu-id="484f2-132">The runtime returns E_NOINTERFACE when it receives a `QueryInterface` call for an [IManagedObject](../../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md) interface for any [COM Callable Wrapper](../../../../../docs/framework/interop/com-callable-wrapper.md) (CCW) that has been created in this domain.</span></span>  
  
 <span data-ttu-id="484f2-133">Esses dois comportamentos Certifique-se de que todas as chamadas sobre COM interfaces entre objetos gerenciados em uso de limites de domínio de aplicativo COM e interoperabilidade COM, em vez de comunicação remota.</span><span class="sxs-lookup"><span data-stu-id="484f2-133">These two behaviors ensure that all calls over COM interfaces between managed objects across application domain boundaries use COM and COM interop instead of remoting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="484f2-134">Exemplo</span><span class="sxs-lookup"><span data-stu-id="484f2-134">Example</span></span>  
 <span data-ttu-id="484f2-135">O exemplo a seguir mostra como especificar que o tempo de execução deve usar COM interoperabilidade entre limites de isolamento:</span><span class="sxs-lookup"><span data-stu-id="484f2-135">The following example shows how to specify that the runtime should use COM interop across isolation boundaries:</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <PreferComInsteadOfManagedRemoting enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="484f2-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="484f2-136">See Also</span></span>  
 [<span data-ttu-id="484f2-137">Esquema de configurações do tempo de execução</span><span class="sxs-lookup"><span data-stu-id="484f2-137">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="484f2-138">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="484f2-138">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
