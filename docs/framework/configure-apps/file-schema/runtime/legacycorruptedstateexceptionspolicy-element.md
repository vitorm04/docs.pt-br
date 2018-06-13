---
title: '&lt;legacyCorruptedStateExceptionsPolicy&gt; elemento'
ms.date: 03/30/2017
helpviewer_keywords:
- <legacyCorruptedStateExceptionsPolicy> element
- legacyCorruptedStateExceptionsPolicy element
ms.assetid: e0a55ddc-bfa8-4f3e-ac14-d1fc3330e4bb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6228aaf4c7da70337d9d1a99adcb78f71a0039b2
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32744610"
---
# <a name="ltlegacycorruptedstateexceptionspolicygt-element"></a><span data-ttu-id="99e05-102">&lt;legacyCorruptedStateExceptionsPolicy&gt; elemento</span><span class="sxs-lookup"><span data-stu-id="99e05-102">&lt;legacyCorruptedStateExceptionsPolicy&gt; Element</span></span>
<span data-ttu-id="99e05-103">Especifica se o common language runtime permite que o código gerenciado detectar violações de acesso e outras exceções de estado corrompido.</span><span class="sxs-lookup"><span data-stu-id="99e05-103">Specifies whether the common language runtime allows managed code to catch access violations and other corrupted state exceptions.</span></span>  
  
 <span data-ttu-id="99e05-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="99e05-104">\<configuration></span></span>  
<span data-ttu-id="99e05-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="99e05-105">\<runtime></span></span>  
<span data-ttu-id="99e05-106">\<legacyCorruptedStateExceptionsPolicy ></span><span class="sxs-lookup"><span data-stu-id="99e05-106">\<legacyCorruptedStateExceptionsPolicy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99e05-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="99e05-107">Syntax</span></span>  
  
```xml  
<legacyCorruptedStateExceptionsPolicy enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="99e05-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="99e05-108">Attributes and Elements</span></span>  
 <span data-ttu-id="99e05-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="99e05-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="99e05-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="99e05-110">Attributes</span></span>  
  
|<span data-ttu-id="99e05-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="99e05-111">Attribute</span></span>|<span data-ttu-id="99e05-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="99e05-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="99e05-113">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="99e05-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="99e05-114">Especifica que o aplicativo irá detectar a corrupção de falhas de exceção de estado, como violações de acesso.</span><span class="sxs-lookup"><span data-stu-id="99e05-114">Specifies that the application will catch corrupting state exception failures such as access violations.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="99e05-115">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="99e05-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="99e05-116">Valor</span><span class="sxs-lookup"><span data-stu-id="99e05-116">Value</span></span>|<span data-ttu-id="99e05-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="99e05-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="99e05-118">O aplicativo não capturará corrupção de falhas de exceção de estado, como violações de acesso.</span><span class="sxs-lookup"><span data-stu-id="99e05-118">The application will not catch corrupting state exception failures such as access violations.</span></span> <span data-ttu-id="99e05-119">Esse é o padrão.</span><span class="sxs-lookup"><span data-stu-id="99e05-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="99e05-120">O aplicativo irá detectar a corrupção de falhas de exceção de estado, como violações de acesso.</span><span class="sxs-lookup"><span data-stu-id="99e05-120">The application will catch corrupting state exception failures such as access violations.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="99e05-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="99e05-121">Child Elements</span></span>  
 <span data-ttu-id="99e05-122">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="99e05-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="99e05-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="99e05-123">Parent Elements</span></span>  
  
|<span data-ttu-id="99e05-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="99e05-124">Element</span></span>|<span data-ttu-id="99e05-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="99e05-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="99e05-126">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="99e05-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="99e05-127">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="99e05-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="99e05-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="99e05-128">Remarks</span></span>  
 <span data-ttu-id="99e05-129">No .NET Framework versão 3.5 e anteriores, o common language runtime permitido código gerenciado para capturar exceções que foram geradas pelo processo corrompido estados.</span><span class="sxs-lookup"><span data-stu-id="99e05-129">In the .NET Framework version 3.5 and earlier, the common language runtime allowed managed code to catch exceptions that were raised by corrupted process states.</span></span> <span data-ttu-id="99e05-130">Uma violação de acesso é um exemplo desse tipo de exceção.</span><span class="sxs-lookup"><span data-stu-id="99e05-130">An access violation is an example of this type of exception.</span></span>  
  
 <span data-ttu-id="99e05-131">Começando com o [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)]gerenciado código não captura esses tipos de exceções em `catch` blocos.</span><span class="sxs-lookup"><span data-stu-id="99e05-131">Starting with the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], managed code no longer catches these types of exceptions in `catch` blocks.</span></span> <span data-ttu-id="99e05-132">No entanto, você pode substituir essa alteração e manter o tratamento de exceções de estado corrompido de duas maneiras:</span><span class="sxs-lookup"><span data-stu-id="99e05-132">However, you can override this change and maintain the handling of corrupted state exceptions in two ways:</span></span>  
  
-   <span data-ttu-id="99e05-133">Definir o `<legacyCorruptedStateExceptionsPolicy>` do elemento `enabled` atributo `true`.</span><span class="sxs-lookup"><span data-stu-id="99e05-133">Set the `<legacyCorruptedStateExceptionsPolicy>` element's `enabled` attribute to `true`.</span></span> <span data-ttu-id="99e05-134">Esta configuração é aplicada processwide e afeta todos os métodos.</span><span class="sxs-lookup"><span data-stu-id="99e05-134">This configuration setting is applied processwide and affects all methods.</span></span>  
  
 <span data-ttu-id="99e05-135">-ou-</span><span class="sxs-lookup"><span data-stu-id="99e05-135">-or-</span></span>  
  
-   <span data-ttu-id="99e05-136">Aplicar o <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute?displayProperty=nameWithType> de atributo para o método que contém as exceções `catch` bloco.</span><span class="sxs-lookup"><span data-stu-id="99e05-136">Apply the <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute?displayProperty=nameWithType> attribute to the method that contains the exceptions `catch` block.</span></span>  
  
 <span data-ttu-id="99e05-137">Este elemento de configuração está disponível apenas no [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] e posterior.</span><span class="sxs-lookup"><span data-stu-id="99e05-137">This configuration element is available only in the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="99e05-138">Exemplo</span><span class="sxs-lookup"><span data-stu-id="99e05-138">Example</span></span>  
 <span data-ttu-id="99e05-139">O exemplo a seguir mostra como especificar que o aplicativo deve ser revertida para o comportamento antes do [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]e catch corrompido todas as falhas de exceção de estado.</span><span class="sxs-lookup"><span data-stu-id="99e05-139">The following example shows how to specify that the application should revert to the behavior before the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], and catch all corrupting state exception failures.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <legacyCorruptedStateExceptionsPolicy enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="99e05-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="99e05-140">See Also</span></span>  
 <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute>  
 [<span data-ttu-id="99e05-141">Esquema de configurações do tempo de execução</span><span class="sxs-lookup"><span data-stu-id="99e05-141">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="99e05-142">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="99e05-142">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
