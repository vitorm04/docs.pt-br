---
title: Elemento <legacyCorruptedStateExceptionsPolicy>
ms.date: 03/30/2017
helpviewer_keywords:
- <legacyCorruptedStateExceptionsPolicy> element
- legacyCorruptedStateExceptionsPolicy element
ms.assetid: e0a55ddc-bfa8-4f3e-ac14-d1fc3330e4bb
ms.openlocfilehash: f36e27a1b85cff2ba8c7e838bace37890a5aa760
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91151201"
---
# <a name="legacycorruptedstateexceptionspolicy-element"></a><span data-ttu-id="d0822-102">Elemento \<legacyCorruptedStateExceptionsPolicy></span><span class="sxs-lookup"><span data-stu-id="d0822-102">\<legacyCorruptedStateExceptionsPolicy> Element</span></span>

<span data-ttu-id="d0822-103">Especifica se o Common Language Runtime permite que o código gerenciado Capture violações de acesso e outras exceções de estado corrompidas.</span><span class="sxs-lookup"><span data-stu-id="d0822-103">Specifies whether the common language runtime allows managed code to catch access violations and other corrupted state exceptions.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<legacyCorruptedStateExceptionsPolicy>**  
  
## <a name="syntax"></a><span data-ttu-id="d0822-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="d0822-104">Syntax</span></span>  
  
```xml  
<legacyCorruptedStateExceptionsPolicy enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d0822-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="d0822-105">Attributes and Elements</span></span>  

 <span data-ttu-id="d0822-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="d0822-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d0822-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="d0822-107">Attributes</span></span>  
  
|<span data-ttu-id="d0822-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="d0822-108">Attribute</span></span>|<span data-ttu-id="d0822-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="d0822-109">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="d0822-110">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="d0822-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="d0822-111">Especifica que o aplicativo irá detectar falhas de exceção de estado corrompido, como violações de acesso.</span><span class="sxs-lookup"><span data-stu-id="d0822-111">Specifies that the application will catch corrupting state exception failures such as access violations.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="d0822-112">Atributo habilitado</span><span class="sxs-lookup"><span data-stu-id="d0822-112">enabled Attribute</span></span>  
  
|<span data-ttu-id="d0822-113">Valor</span><span class="sxs-lookup"><span data-stu-id="d0822-113">Value</span></span>|<span data-ttu-id="d0822-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="d0822-114">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="d0822-115">O aplicativo não detectará falhas de exceção de estado corrompido, como violações de acesso.</span><span class="sxs-lookup"><span data-stu-id="d0822-115">The application will not catch corrupting state exception failures such as access violations.</span></span> <span data-ttu-id="d0822-116">Este é o padrão.</span><span class="sxs-lookup"><span data-stu-id="d0822-116">This is the default.</span></span>|  
|`true`|<span data-ttu-id="d0822-117">O aplicativo detectará falhas de exceção de estado corrompido, como violações de acesso.</span><span class="sxs-lookup"><span data-stu-id="d0822-117">The application will catch corrupting state exception failures such as access violations.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d0822-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="d0822-118">Child Elements</span></span>  

 <span data-ttu-id="d0822-119">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="d0822-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d0822-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="d0822-120">Parent Elements</span></span>  
  
|<span data-ttu-id="d0822-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="d0822-121">Element</span></span>|<span data-ttu-id="d0822-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="d0822-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="d0822-123">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d0822-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="d0822-124">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="d0822-124">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d0822-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="d0822-125">Remarks</span></span>  

 <span data-ttu-id="d0822-126">No .NET Framework versão 3,5 e anteriores, o Common Language Runtime permitia código gerenciado para capturar exceções que foram geradas por Estados de processo corrompidos.</span><span class="sxs-lookup"><span data-stu-id="d0822-126">In the .NET Framework version 3.5 and earlier, the common language runtime allowed managed code to catch exceptions that were raised by corrupted process states.</span></span> <span data-ttu-id="d0822-127">Uma violação de acesso é um exemplo desse tipo de exceção.</span><span class="sxs-lookup"><span data-stu-id="d0822-127">An access violation is an example of this type of exception.</span></span>  
  
 <span data-ttu-id="d0822-128">A partir do .NET Framework 4, o código gerenciado não captura mais esses tipos de exceções em `catch` blocos.</span><span class="sxs-lookup"><span data-stu-id="d0822-128">Starting with the .NET Framework 4, managed code no longer catches these types of exceptions in `catch` blocks.</span></span> <span data-ttu-id="d0822-129">No entanto, você pode substituir essa alteração e manter a manipulação de exceções de estado corrompidas de duas maneiras:</span><span class="sxs-lookup"><span data-stu-id="d0822-129">However, you can override this change and maintain the handling of corrupted state exceptions in two ways:</span></span>  
  
- <span data-ttu-id="d0822-130">Defina o `<legacyCorruptedStateExceptionsPolicy>` atributo do elemento `enabled` como `true` .</span><span class="sxs-lookup"><span data-stu-id="d0822-130">Set the `<legacyCorruptedStateExceptionsPolicy>` element's `enabled` attribute to `true`.</span></span> <span data-ttu-id="d0822-131">Essa configuração é aplicada processwide e afeta todos os métodos.</span><span class="sxs-lookup"><span data-stu-id="d0822-131">This configuration setting is applied processwide and affects all methods.</span></span>  
  
 <span data-ttu-id="d0822-132">- ou -</span><span class="sxs-lookup"><span data-stu-id="d0822-132">-or-</span></span>  
  
- <span data-ttu-id="d0822-133">Aplique o <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute?displayProperty=nameWithType> atributo ao método que contém o bloco de exceções `catch` .</span><span class="sxs-lookup"><span data-stu-id="d0822-133">Apply the <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute?displayProperty=nameWithType> attribute to the method that contains the exceptions `catch` block.</span></span>  
  
 <span data-ttu-id="d0822-134">Este elemento de configuração está disponível apenas no .NET Framework 4 e posterior.</span><span class="sxs-lookup"><span data-stu-id="d0822-134">This configuration element is available only in the .NET Framework 4 and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d0822-135">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d0822-135">Example</span></span>  

 <span data-ttu-id="d0822-136">O exemplo a seguir mostra como especificar que o aplicativo deve reverter para o comportamento antes do .NET Framework 4 e capturar todas as falhas de exceção de estado corrompido.</span><span class="sxs-lookup"><span data-stu-id="d0822-136">The following example shows how to specify that the application should revert to the behavior before the .NET Framework 4, and catch all corrupting state exception failures.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <legacyCorruptedStateExceptionsPolicy enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d0822-137">Confira também</span><span class="sxs-lookup"><span data-stu-id="d0822-137">See also</span></span>

- <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute>
- [<span data-ttu-id="d0822-138">Esquema de configurações do runtime</span><span class="sxs-lookup"><span data-stu-id="d0822-138">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="d0822-139">Esquema do arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="d0822-139">Configuration File Schema</span></span>](../index.md)
