---
title: Elemento <PreferComInsteadOfManagedRemoting>
ms.date: 03/30/2017
helpviewer_keywords:
- <PreferComInsteadOfManagedRemoting> element
- PreferComInsteadOfManagedRemoting element
ms.assetid: a279a42a-c415-4e79-88cf-64244ebda613
ms.openlocfilehash: 47c568a8d6e89a195414552b3db5953ee61d1e55
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73116011"
---
# <a name="prefercominsteadofmanagedremoting-element"></a><span data-ttu-id="9f9dd-102">\<elemento de > PreferComInsteadOfManagedRemoting</span><span class="sxs-lookup"><span data-stu-id="9f9dd-102">\<PreferComInsteadOfManagedRemoting> Element</span></span>
<span data-ttu-id="9f9dd-103">Especifica se o tempo de execução usará a interoperabilidade COM em vez de comunicação remota para todas as chamadas entre limites de domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9f9dd-103">Specifies whether the runtime will use COM interop instead of remoting for all calls across application domain boundaries.</span></span>  
  
<span data-ttu-id="9f9dd-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="9f9dd-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="9f9dd-105">&nbsp; &nbsp;[ **\<runtime >** ](runtime-element.md) </span><span class="sxs-lookup"><span data-stu-id="9f9dd-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="9f9dd-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<PreferComInsteadOfManagedRemoting >**</span><span class="sxs-lookup"><span data-stu-id="9f9dd-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<PreferComInsteadOfManagedRemoting>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f9dd-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9f9dd-107">Syntax</span></span>  
  
```xml  
<PreferComInsteadOfManagedRemoting enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9f9dd-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="9f9dd-108">Attributes and Elements</span></span>  
 <span data-ttu-id="9f9dd-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="9f9dd-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9f9dd-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="9f9dd-110">Attributes</span></span>  
  
|<span data-ttu-id="9f9dd-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="9f9dd-111">Attribute</span></span>|<span data-ttu-id="9f9dd-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="9f9dd-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="9f9dd-113">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="9f9dd-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="9f9dd-114">Indica se o tempo de execução usará a interoperabilidade COM em vez da comunicação remota entre os limites do domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9f9dd-114">Indicates whether the runtime will use COM interop instead of remoting across application domain boundaries.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="9f9dd-115">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="9f9dd-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="9f9dd-116">Valor</span><span class="sxs-lookup"><span data-stu-id="9f9dd-116">Value</span></span>|<span data-ttu-id="9f9dd-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="9f9dd-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="9f9dd-118">O tempo de execução usará a comunicação remota entre os limites do domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9f9dd-118">The runtime will use remoting across application domain boundaries.</span></span> <span data-ttu-id="9f9dd-119">Esse é o padrão.</span><span class="sxs-lookup"><span data-stu-id="9f9dd-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="9f9dd-120">O tempo de execução usará a interoperabilidade COM entre limites de domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9f9dd-120">The runtime will use COM interop across application domain boundaries.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9f9dd-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="9f9dd-121">Child Elements</span></span>  
 <span data-ttu-id="9f9dd-122">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="9f9dd-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9f9dd-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="9f9dd-123">Parent Elements</span></span>  
  
|<span data-ttu-id="9f9dd-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="9f9dd-124">Element</span></span>|<span data-ttu-id="9f9dd-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="9f9dd-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="9f9dd-126">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9f9dd-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="9f9dd-127">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="9f9dd-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9f9dd-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="9f9dd-128">Remarks</span></span>  
 <span data-ttu-id="9f9dd-129">Quando você define o atributo `enabled` como `true`, o tempo de execução se comporta da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="9f9dd-129">When you set the `enabled` attribute to `true`, the runtime behaves as follows:</span></span>  
  
- <span data-ttu-id="9f9dd-130">O tempo de execução não chama [IUnknown:: QueryInterface](https://go.microsoft.com/fwlink/?LinkID=144867) para uma interface [IManagedObject](../../../unmanaged-api/hosting/imanagedobject-interface.md) quando uma interface [IUnknown](https://go.microsoft.com/fwlink/?LinkId=148003) entra no domínio por meio de uma interface com.</span><span class="sxs-lookup"><span data-stu-id="9f9dd-130">The runtime does not call [IUnknown::QueryInterface](https://go.microsoft.com/fwlink/?LinkID=144867) for an [IManagedObject](../../../unmanaged-api/hosting/imanagedobject-interface.md) interface when an [IUnknown](https://go.microsoft.com/fwlink/?LinkId=148003) interface enters the domain through a COM interface.</span></span> <span data-ttu-id="9f9dd-131">Em vez disso, ele constrói um RCW ( [Runtime Callable Wrapper](../../../../standard/native-interop/runtime-callable-wrapper.md) ) em volta do objeto.</span><span class="sxs-lookup"><span data-stu-id="9f9dd-131">Instead, it constructs a [Runtime Callable Wrapper](../../../../standard/native-interop/runtime-callable-wrapper.md) (RCW) around the object.</span></span>  
  
- <span data-ttu-id="9f9dd-132">O tempo de execução retorna E_NOINTERFACE quando recebe uma chamada de `QueryInterface` para uma interface [IManagedObject](../../../unmanaged-api/hosting/imanagedobject-interface.md) para qualquer CCW ( [com callable wrapper](../../../../standard/native-interop/com-callable-wrapper.md) ) que tenha sido criado nesse domínio.</span><span class="sxs-lookup"><span data-stu-id="9f9dd-132">The runtime returns E_NOINTERFACE when it receives a `QueryInterface` call for an [IManagedObject](../../../unmanaged-api/hosting/imanagedobject-interface.md) interface for any [COM Callable Wrapper](../../../../standard/native-interop/com-callable-wrapper.md) (CCW) that has been created in this domain.</span></span>  
  
 <span data-ttu-id="9f9dd-133">Esses dois comportamentos garantem que todas as chamadas sobre interfaces COM entre objetos gerenciados entre os limites de domínio do aplicativo usem a interoperabilidade com e COM em vez de comunicação remota.</span><span class="sxs-lookup"><span data-stu-id="9f9dd-133">These two behaviors ensure that all calls over COM interfaces between managed objects across application domain boundaries use COM and COM interop instead of remoting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9f9dd-134">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9f9dd-134">Example</span></span>  
 <span data-ttu-id="9f9dd-135">O exemplo a seguir mostra como especificar que o tempo de execução deve usar a interoperabilidade COM entre limites de isolamento:</span><span class="sxs-lookup"><span data-stu-id="9f9dd-135">The following example shows how to specify that the runtime should use COM interop across isolation boundaries:</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <PreferComInsteadOfManagedRemoting enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9f9dd-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9f9dd-136">See also</span></span>

- [<span data-ttu-id="9f9dd-137">Esquema de configurações do tempo de execução</span><span class="sxs-lookup"><span data-stu-id="9f9dd-137">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="9f9dd-138">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="9f9dd-138">Configuration File Schema</span></span>](../index.md)
