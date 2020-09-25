---
title: Elemento <PreferComInsteadOfManagedRemoting>
ms.date: 03/30/2017
helpviewer_keywords:
- <PreferComInsteadOfManagedRemoting> element
- PreferComInsteadOfManagedRemoting element
ms.assetid: a279a42a-c415-4e79-88cf-64244ebda613
ms.openlocfilehash: 2fb0d94f91d28f9d9d4f247411d273f786f7b63b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91195279"
---
# <a name="prefercominsteadofmanagedremoting-element"></a><span data-ttu-id="092f7-102">Elemento \<PreferComInsteadOfManagedRemoting></span><span class="sxs-lookup"><span data-stu-id="092f7-102">\<PreferComInsteadOfManagedRemoting> Element</span></span>

<span data-ttu-id="092f7-103">Especifica se o tempo de execução usará a interoperabilidade COM em vez de comunicação remota para todas as chamadas entre limites de domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="092f7-103">Specifies whether the runtime will use COM interop instead of remoting for all calls across application domain boundaries.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<PreferComInsteadOfManagedRemoting>**  
  
## <a name="syntax"></a><span data-ttu-id="092f7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="092f7-104">Syntax</span></span>  
  
```xml  
<PreferComInsteadOfManagedRemoting enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="092f7-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="092f7-105">Attributes and Elements</span></span>  

 <span data-ttu-id="092f7-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="092f7-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="092f7-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="092f7-107">Attributes</span></span>  
  
|<span data-ttu-id="092f7-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="092f7-108">Attribute</span></span>|<span data-ttu-id="092f7-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="092f7-109">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="092f7-110">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="092f7-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="092f7-111">Indica se o tempo de execução usará a interoperabilidade COM em vez da comunicação remota entre os limites do domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="092f7-111">Indicates whether the runtime will use COM interop instead of remoting across application domain boundaries.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="092f7-112">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="092f7-112">enabled Attribute</span></span>  
  
|<span data-ttu-id="092f7-113">Valor</span><span class="sxs-lookup"><span data-stu-id="092f7-113">Value</span></span>|<span data-ttu-id="092f7-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="092f7-114">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="092f7-115">O tempo de execução usará a comunicação remota entre os limites do domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="092f7-115">The runtime will use remoting across application domain boundaries.</span></span> <span data-ttu-id="092f7-116">Esse é o padrão.</span><span class="sxs-lookup"><span data-stu-id="092f7-116">This is the default.</span></span>|  
|`true`|<span data-ttu-id="092f7-117">O tempo de execução usará a interoperabilidade COM entre limites de domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="092f7-117">The runtime will use COM interop across application domain boundaries.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="092f7-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="092f7-118">Child Elements</span></span>  

 <span data-ttu-id="092f7-119">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="092f7-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="092f7-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="092f7-120">Parent Elements</span></span>  
  
|<span data-ttu-id="092f7-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="092f7-121">Element</span></span>|<span data-ttu-id="092f7-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="092f7-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="092f7-123">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="092f7-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="092f7-124">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="092f7-124">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="092f7-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="092f7-125">Remarks</span></span>  

 <span data-ttu-id="092f7-126">Quando você define o `enabled` atributo como `true` , o tempo de execução se comporta da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="092f7-126">When you set the `enabled` attribute to `true`, the runtime behaves as follows:</span></span>  
  
- <span data-ttu-id="092f7-127">O tempo de execução não chama [IUnknown:: QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) para uma interface [IManagedObject](../../../unmanaged-api/hosting/imanagedobject-interface.md) quando uma interface [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) entra no domínio por meio de uma interface com.</span><span class="sxs-lookup"><span data-stu-id="092f7-127">The runtime does not call [IUnknown::QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) for an [IManagedObject](../../../unmanaged-api/hosting/imanagedobject-interface.md) interface when an [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) interface enters the domain through a COM interface.</span></span> <span data-ttu-id="092f7-128">Em vez disso, ele constrói um RCW ( [Runtime Callable Wrapper](../../../../standard/native-interop/runtime-callable-wrapper.md) ) em volta do objeto.</span><span class="sxs-lookup"><span data-stu-id="092f7-128">Instead, it constructs a [Runtime Callable Wrapper](../../../../standard/native-interop/runtime-callable-wrapper.md) (RCW) around the object.</span></span>  
  
- <span data-ttu-id="092f7-129">O tempo de execução retorna E_NOINTERFACE quando recebe uma `QueryInterface` chamada para uma interface [IManagedObject](../../../unmanaged-api/hosting/imanagedobject-interface.md) para qualquer CCW ( [com callable wrapper](../../../../standard/native-interop/com-callable-wrapper.md) ) criado nesse domínio.</span><span class="sxs-lookup"><span data-stu-id="092f7-129">The runtime returns E_NOINTERFACE when it receives a `QueryInterface` call for an [IManagedObject](../../../unmanaged-api/hosting/imanagedobject-interface.md) interface for any [COM Callable Wrapper](../../../../standard/native-interop/com-callable-wrapper.md) (CCW) that has been created in this domain.</span></span>  
  
 <span data-ttu-id="092f7-130">Esses dois comportamentos garantem que todas as chamadas sobre interfaces COM entre objetos gerenciados entre os limites de domínio do aplicativo usem a interoperabilidade com e COM em vez de comunicação remota.</span><span class="sxs-lookup"><span data-stu-id="092f7-130">These two behaviors ensure that all calls over COM interfaces between managed objects across application domain boundaries use COM and COM interop instead of remoting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="092f7-131">Exemplo</span><span class="sxs-lookup"><span data-stu-id="092f7-131">Example</span></span>  

 <span data-ttu-id="092f7-132">O exemplo a seguir mostra como especificar que o tempo de execução deve usar a interoperabilidade COM entre limites de isolamento:</span><span class="sxs-lookup"><span data-stu-id="092f7-132">The following example shows how to specify that the runtime should use COM interop across isolation boundaries:</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <PreferComInsteadOfManagedRemoting enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="092f7-133">Veja também</span><span class="sxs-lookup"><span data-stu-id="092f7-133">See also</span></span>

- [<span data-ttu-id="092f7-134">Esquema de configurações do runtime</span><span class="sxs-lookup"><span data-stu-id="092f7-134">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="092f7-135">Esquema do arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="092f7-135">Configuration File Schema</span></span>](../index.md)
