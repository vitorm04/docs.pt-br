---
title: '&lt;legacyCorruptedStateExceptionsPolicy&gt; elemento'
ms.date: 03/30/2017
helpviewer_keywords:
- <legacyCorruptedStateExceptionsPolicy> element
- legacyCorruptedStateExceptionsPolicy element
ms.assetid: e0a55ddc-bfa8-4f3e-ac14-d1fc3330e4bb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 14b8940fa0c5c7ceb4a14fdd0f40867c7be9f65e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54737709"
---
# <a name="ltlegacycorruptedstateexceptionspolicygt-element"></a><span data-ttu-id="55b27-102">&lt;legacyCorruptedStateExceptionsPolicy&gt; elemento</span><span class="sxs-lookup"><span data-stu-id="55b27-102">&lt;legacyCorruptedStateExceptionsPolicy&gt; Element</span></span>
<span data-ttu-id="55b27-103">Especifica se o common language runtime permite código gerenciado detecte violações de acesso e outras exceções de estado corrompido.</span><span class="sxs-lookup"><span data-stu-id="55b27-103">Specifies whether the common language runtime allows managed code to catch access violations and other corrupted state exceptions.</span></span>  
  
 <span data-ttu-id="55b27-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="55b27-104">\<configuration></span></span>  
<span data-ttu-id="55b27-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="55b27-105">\<runtime></span></span>  
<span data-ttu-id="55b27-106">\<legacyCorruptedStateExceptionsPolicy></span><span class="sxs-lookup"><span data-stu-id="55b27-106">\<legacyCorruptedStateExceptionsPolicy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55b27-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="55b27-107">Syntax</span></span>  
  
```xml  
<legacyCorruptedStateExceptionsPolicy enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="55b27-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="55b27-108">Attributes and Elements</span></span>  
 <span data-ttu-id="55b27-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="55b27-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="55b27-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="55b27-110">Attributes</span></span>  
  
|<span data-ttu-id="55b27-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="55b27-111">Attribute</span></span>|<span data-ttu-id="55b27-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="55b27-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="55b27-113">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="55b27-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="55b27-114">Especifica que o aplicativo irá capturar corrompendo falhas de exceção de estado, como violações de acesso.</span><span class="sxs-lookup"><span data-stu-id="55b27-114">Specifies that the application will catch corrupting state exception failures such as access violations.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="55b27-115">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="55b27-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="55b27-116">Valor</span><span class="sxs-lookup"><span data-stu-id="55b27-116">Value</span></span>|<span data-ttu-id="55b27-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="55b27-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="55b27-118">O aplicativo não capturará corrompendo falhas de exceção de estado, como violações de acesso.</span><span class="sxs-lookup"><span data-stu-id="55b27-118">The application will not catch corrupting state exception failures such as access violations.</span></span> <span data-ttu-id="55b27-119">Esse é o padrão.</span><span class="sxs-lookup"><span data-stu-id="55b27-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="55b27-120">O aplicativo irá capturar corrompendo falhas de exceção de estado, como violações de acesso.</span><span class="sxs-lookup"><span data-stu-id="55b27-120">The application will catch corrupting state exception failures such as access violations.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="55b27-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="55b27-121">Child Elements</span></span>  
 <span data-ttu-id="55b27-122">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="55b27-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="55b27-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="55b27-123">Parent Elements</span></span>  
  
|<span data-ttu-id="55b27-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="55b27-124">Element</span></span>|<span data-ttu-id="55b27-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="55b27-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="55b27-126">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="55b27-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="55b27-127">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="55b27-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="55b27-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="55b27-128">Remarks</span></span>  
 <span data-ttu-id="55b27-129">No .NET Framework versão 3.5 e anteriores, o common language runtime permitido código gerenciado capturar exceções que foram geradas por estados de processo corrompido.</span><span class="sxs-lookup"><span data-stu-id="55b27-129">In the .NET Framework version 3.5 and earlier, the common language runtime allowed managed code to catch exceptions that were raised by corrupted process states.</span></span> <span data-ttu-id="55b27-130">Uma violação de acesso é um exemplo desse tipo de exceção.</span><span class="sxs-lookup"><span data-stu-id="55b27-130">An access violation is an example of this type of exception.</span></span>  
  
 <span data-ttu-id="55b27-131">Começando com o [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)]gerenciado código não captura esses tipos de exceções em `catch` blocos.</span><span class="sxs-lookup"><span data-stu-id="55b27-131">Starting with the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], managed code no longer catches these types of exceptions in `catch` blocks.</span></span> <span data-ttu-id="55b27-132">No entanto, você pode substituir essa alteração e manter o tratamento de exceções de estado corrompido de duas maneiras:</span><span class="sxs-lookup"><span data-stu-id="55b27-132">However, you can override this change and maintain the handling of corrupted state exceptions in two ways:</span></span>  
  
-   <span data-ttu-id="55b27-133">Defina as `<legacyCorruptedStateExceptionsPolicy>` do elemento `enabled` atributo `true`.</span><span class="sxs-lookup"><span data-stu-id="55b27-133">Set the `<legacyCorruptedStateExceptionsPolicy>` element's `enabled` attribute to `true`.</span></span> <span data-ttu-id="55b27-134">Essa configuração é aplicada processwide e afeta todos os métodos.</span><span class="sxs-lookup"><span data-stu-id="55b27-134">This configuration setting is applied processwide and affects all methods.</span></span>  
  
 <span data-ttu-id="55b27-135">-ou-</span><span class="sxs-lookup"><span data-stu-id="55b27-135">-or-</span></span>  
  
-   <span data-ttu-id="55b27-136">Aplicar a <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute?displayProperty=nameWithType> de atributo para o método que contém as exceções `catch` bloco.</span><span class="sxs-lookup"><span data-stu-id="55b27-136">Apply the <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute?displayProperty=nameWithType> attribute to the method that contains the exceptions `catch` block.</span></span>  
  
 <span data-ttu-id="55b27-137">Este elemento de configuração está disponível apenas no [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] e versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="55b27-137">This configuration element is available only in the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="55b27-138">Exemplo</span><span class="sxs-lookup"><span data-stu-id="55b27-138">Example</span></span>  
 <span data-ttu-id="55b27-139">O exemplo a seguir mostra como especificar que o aplicativo deve ser revertido para o comportamento antes do [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]e detectar corrompam todas as falhas de exceção de estado.</span><span class="sxs-lookup"><span data-stu-id="55b27-139">The following example shows how to specify that the application should revert to the behavior before the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], and catch all corrupting state exception failures.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <legacyCorruptedStateExceptionsPolicy enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="55b27-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="55b27-140">See also</span></span>
- <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute>
- [<span data-ttu-id="55b27-141">Esquema de configurações do tempo de execução</span><span class="sxs-lookup"><span data-stu-id="55b27-141">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="55b27-142">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="55b27-142">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
