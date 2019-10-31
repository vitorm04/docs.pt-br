---
title: Elemento <legacyCorruptedStateExceptionsPolicy>
ms.date: 03/30/2017
helpviewer_keywords:
- <legacyCorruptedStateExceptionsPolicy> element
- legacyCorruptedStateExceptionsPolicy element
ms.assetid: e0a55ddc-bfa8-4f3e-ac14-d1fc3330e4bb
ms.openlocfilehash: d1d29a37999a01f3e370897a1052f4f94435a218
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73116454"
---
# <a name="legacycorruptedstateexceptionspolicy-element"></a><span data-ttu-id="4574c-102">\<elemento de > legacyCorruptedStateExceptionsPolicy</span><span class="sxs-lookup"><span data-stu-id="4574c-102">\<legacyCorruptedStateExceptionsPolicy> Element</span></span>
<span data-ttu-id="4574c-103">Especifica se o Common Language Runtime permite que o código gerenciado Capture violações de acesso e outras exceções de estado corrompidas.</span><span class="sxs-lookup"><span data-stu-id="4574c-103">Specifies whether the common language runtime allows managed code to catch access violations and other corrupted state exceptions.</span></span>  
  
<span data-ttu-id="4574c-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="4574c-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="4574c-105">&nbsp; &nbsp;[ **\<runtime >** ](runtime-element.md) </span><span class="sxs-lookup"><span data-stu-id="4574c-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="4574c-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<legacyCorruptedStateExceptionsPolicy >**</span><span class="sxs-lookup"><span data-stu-id="4574c-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<legacyCorruptedStateExceptionsPolicy>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4574c-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4574c-107">Syntax</span></span>  
  
```xml  
<legacyCorruptedStateExceptionsPolicy enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4574c-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="4574c-108">Attributes and Elements</span></span>  
 <span data-ttu-id="4574c-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="4574c-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4574c-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="4574c-110">Attributes</span></span>  
  
|<span data-ttu-id="4574c-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="4574c-111">Attribute</span></span>|<span data-ttu-id="4574c-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="4574c-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="4574c-113">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="4574c-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="4574c-114">Especifica que o aplicativo irá detectar falhas de exceção de estado corrompido, como violações de acesso.</span><span class="sxs-lookup"><span data-stu-id="4574c-114">Specifies that the application will catch corrupting state exception failures such as access violations.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="4574c-115">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="4574c-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="4574c-116">Valor</span><span class="sxs-lookup"><span data-stu-id="4574c-116">Value</span></span>|<span data-ttu-id="4574c-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="4574c-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="4574c-118">O aplicativo não detectará falhas de exceção de estado corrompido, como violações de acesso.</span><span class="sxs-lookup"><span data-stu-id="4574c-118">The application will not catch corrupting state exception failures such as access violations.</span></span> <span data-ttu-id="4574c-119">Esse é o padrão.</span><span class="sxs-lookup"><span data-stu-id="4574c-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="4574c-120">O aplicativo detectará falhas de exceção de estado corrompido, como violações de acesso.</span><span class="sxs-lookup"><span data-stu-id="4574c-120">The application will catch corrupting state exception failures such as access violations.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4574c-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="4574c-121">Child Elements</span></span>  
 <span data-ttu-id="4574c-122">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="4574c-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4574c-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="4574c-123">Parent Elements</span></span>  
  
|<span data-ttu-id="4574c-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="4574c-124">Element</span></span>|<span data-ttu-id="4574c-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="4574c-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="4574c-126">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4574c-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="4574c-127">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="4574c-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4574c-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="4574c-128">Remarks</span></span>  
 <span data-ttu-id="4574c-129">No .NET Framework versão 3,5 e anteriores, o Common Language Runtime permitia código gerenciado para capturar exceções que foram geradas por Estados de processo corrompidos.</span><span class="sxs-lookup"><span data-stu-id="4574c-129">In the .NET Framework version 3.5 and earlier, the common language runtime allowed managed code to catch exceptions that were raised by corrupted process states.</span></span> <span data-ttu-id="4574c-130">Uma violação de acesso é um exemplo desse tipo de exceção.</span><span class="sxs-lookup"><span data-stu-id="4574c-130">An access violation is an example of this type of exception.</span></span>  
  
 <span data-ttu-id="4574c-131">A partir do .NET Framework 4, o código gerenciado não captura mais esses tipos de exceções em blocos de `catch`.</span><span class="sxs-lookup"><span data-stu-id="4574c-131">Starting with the .NET Framework 4, managed code no longer catches these types of exceptions in `catch` blocks.</span></span> <span data-ttu-id="4574c-132">No entanto, você pode substituir essa alteração e manter a manipulação de exceções de estado corrompidas de duas maneiras:</span><span class="sxs-lookup"><span data-stu-id="4574c-132">However, you can override this change and maintain the handling of corrupted state exceptions in two ways:</span></span>  
  
- <span data-ttu-id="4574c-133">Defina o atributo de `enabled` do elemento de `<legacyCorruptedStateExceptionsPolicy>` como `true`.</span><span class="sxs-lookup"><span data-stu-id="4574c-133">Set the `<legacyCorruptedStateExceptionsPolicy>` element's `enabled` attribute to `true`.</span></span> <span data-ttu-id="4574c-134">Essa configuração é aplicada processwide e afeta todos os métodos.</span><span class="sxs-lookup"><span data-stu-id="4574c-134">This configuration setting is applied processwide and affects all methods.</span></span>  
  
 <span data-ttu-id="4574c-135">\- ou -</span><span class="sxs-lookup"><span data-stu-id="4574c-135">-or-</span></span>  
  
- <span data-ttu-id="4574c-136">Aplique o atributo <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute?displayProperty=nameWithType> ao método que contém as exceções `catch` bloco.</span><span class="sxs-lookup"><span data-stu-id="4574c-136">Apply the <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute?displayProperty=nameWithType> attribute to the method that contains the exceptions `catch` block.</span></span>  
  
 <span data-ttu-id="4574c-137">Este elemento de configuração está disponível apenas no .NET Framework 4 e posterior.</span><span class="sxs-lookup"><span data-stu-id="4574c-137">This configuration element is available only in the .NET Framework 4 and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4574c-138">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4574c-138">Example</span></span>  
 <span data-ttu-id="4574c-139">O exemplo a seguir mostra como especificar que o aplicativo deve reverter para o comportamento antes do .NET Framework 4 e capturar todas as falhas de exceção de estado corrompido.</span><span class="sxs-lookup"><span data-stu-id="4574c-139">The following example shows how to specify that the application should revert to the behavior before the .NET Framework 4, and catch all corrupting state exception failures.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <legacyCorruptedStateExceptionsPolicy enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4574c-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4574c-140">See also</span></span>

- <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute>
- [<span data-ttu-id="4574c-141">Esquema de configurações do tempo de execução</span><span class="sxs-lookup"><span data-stu-id="4574c-141">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="4574c-142">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="4574c-142">Configuration File Schema</span></span>](../index.md)
