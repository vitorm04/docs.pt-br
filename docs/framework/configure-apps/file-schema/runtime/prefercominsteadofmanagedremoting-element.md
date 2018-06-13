---
title: '&lt;PreferComInsteadOfManagedRemoting&gt; elemento'
ms.date: 03/30/2017
helpviewer_keywords:
- <PreferComInsteadOfManagedRemoting> element
- PreferComInsteadOfManagedRemoting element
ms.assetid: a279a42a-c415-4e79-88cf-64244ebda613
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4cac4ebb46fabad49e2e4e6a7d566522ca027094
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32745468"
---
# <a name="ltprefercominsteadofmanagedremotinggt-element"></a><span data-ttu-id="07e3e-102">&lt;PreferComInsteadOfManagedRemoting&gt; elemento</span><span class="sxs-lookup"><span data-stu-id="07e3e-102">&lt;PreferComInsteadOfManagedRemoting&gt; Element</span></span>
<span data-ttu-id="07e3e-103">Especifica se o tempo de execução usará interoperabilidade COM, em vez de comunicação remota para todas as chamadas entre limites de domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="07e3e-103">Specifies whether the runtime will use COM interop instead of remoting for all calls across application domain boundaries.</span></span>  
  
 <span data-ttu-id="07e3e-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="07e3e-104">\<configuration></span></span>  
<span data-ttu-id="07e3e-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="07e3e-105">\<runtime></span></span>  
<span data-ttu-id="07e3e-106">\<PreferComInsteadOfManagedRemoting ></span><span class="sxs-lookup"><span data-stu-id="07e3e-106">\<PreferComInsteadOfManagedRemoting></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07e3e-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="07e3e-107">Syntax</span></span>  
  
```xml  
<PreferComInsteadOfManagedRemoting enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="07e3e-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="07e3e-108">Attributes and Elements</span></span>  
 <span data-ttu-id="07e3e-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="07e3e-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="07e3e-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="07e3e-110">Attributes</span></span>  
  
|<span data-ttu-id="07e3e-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="07e3e-111">Attribute</span></span>|<span data-ttu-id="07e3e-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="07e3e-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="07e3e-113">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="07e3e-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="07e3e-114">Indica se o tempo de execução usará a interoperabilidade COM, em vez de comunicação remota entre limites de domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="07e3e-114">Indicates whether the runtime will use COM interop instead of remoting across application domain boundaries.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="07e3e-115">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="07e3e-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="07e3e-116">Valor</span><span class="sxs-lookup"><span data-stu-id="07e3e-116">Value</span></span>|<span data-ttu-id="07e3e-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="07e3e-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="07e3e-118">O tempo de execução usará a comunicação remota entre limites de domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="07e3e-118">The runtime will use remoting across application domain boundaries.</span></span> <span data-ttu-id="07e3e-119">Esse é o padrão.</span><span class="sxs-lookup"><span data-stu-id="07e3e-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="07e3e-120">O tempo de execução usará a interoperabilidade entre limites de domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="07e3e-120">The runtime will use COM interop across application domain boundaries.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="07e3e-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="07e3e-121">Child Elements</span></span>  
 <span data-ttu-id="07e3e-122">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="07e3e-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="07e3e-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="07e3e-123">Parent Elements</span></span>  
  
|<span data-ttu-id="07e3e-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="07e3e-124">Element</span></span>|<span data-ttu-id="07e3e-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="07e3e-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="07e3e-126">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="07e3e-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="07e3e-127">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="07e3e-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="07e3e-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="07e3e-128">Remarks</span></span>  
 <span data-ttu-id="07e3e-129">Quando você define o `enabled` atributo `true`, o tempo de execução se comporta da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="07e3e-129">When you set the `enabled` attribute to `true`, the runtime behaves as follows:</span></span>  
  
-   <span data-ttu-id="07e3e-130">O tempo de execução não chama [IUnknown:: QueryInterface](http://go.microsoft.com/fwlink/?LinkID=144867) para um [IManagedObject](../../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md) interface quando um [IUnknown](http://go.microsoft.com/fwlink/?LinkId=148003) interface entra do domínio por meio de uma interface COM.</span><span class="sxs-lookup"><span data-stu-id="07e3e-130">The runtime does not call [IUnknown::QueryInterface](http://go.microsoft.com/fwlink/?LinkID=144867) for an [IManagedObject](../../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md) interface when an [IUnknown](http://go.microsoft.com/fwlink/?LinkId=148003) interface enters the domain through a COM interface.</span></span> <span data-ttu-id="07e3e-131">Em vez disso, ele cria um [Runtime Callable Wrapper](../../../../../docs/framework/interop/runtime-callable-wrapper.md) (RCW) em torno do objeto.</span><span class="sxs-lookup"><span data-stu-id="07e3e-131">Instead, it constructs a [Runtime Callable Wrapper](../../../../../docs/framework/interop/runtime-callable-wrapper.md) (RCW) around the object.</span></span>  
  
-   <span data-ttu-id="07e3e-132">O tempo de execução retorna E_NOINTERFACE quando ele recebe um `QueryInterface` pedir um [IManagedObject](../../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md) interface para qualquer [COM Callable Wrapper](../../../../../docs/framework/interop/com-callable-wrapper.md) (CCW) que foi criado neste domínio.</span><span class="sxs-lookup"><span data-stu-id="07e3e-132">The runtime returns E_NOINTERFACE when it receives a `QueryInterface` call for an [IManagedObject](../../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md) interface for any [COM Callable Wrapper](../../../../../docs/framework/interop/com-callable-wrapper.md) (CCW) that has been created in this domain.</span></span>  
  
 <span data-ttu-id="07e3e-133">Esses dois comportamentos Certifique-se de que todas as chamadas sobre COM interfaces entre objetos gerenciados em uso de limites de domínio de aplicativo COM e interoperabilidade COM, em vez de comunicação remota.</span><span class="sxs-lookup"><span data-stu-id="07e3e-133">These two behaviors ensure that all calls over COM interfaces between managed objects across application domain boundaries use COM and COM interop instead of remoting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="07e3e-134">Exemplo</span><span class="sxs-lookup"><span data-stu-id="07e3e-134">Example</span></span>  
 <span data-ttu-id="07e3e-135">O exemplo a seguir mostra como especificar que o tempo de execução deve usar COM interoperabilidade entre limites de isolamento:</span><span class="sxs-lookup"><span data-stu-id="07e3e-135">The following example shows how to specify that the runtime should use COM interop across isolation boundaries:</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <PreferComInsteadOfManagedRemoting enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="07e3e-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="07e3e-136">See Also</span></span>  
 [<span data-ttu-id="07e3e-137">Esquema de configurações do tempo de execução</span><span class="sxs-lookup"><span data-stu-id="07e3e-137">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="07e3e-138">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="07e3e-138">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
