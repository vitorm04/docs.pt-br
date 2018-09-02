---
title: '&lt;requiredRuntime&gt; elemento'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#requiredRuntime
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup/requiredRuntime
helpviewer_keywords:
- requiredRuntime element
- <requiredRuntime> element
- container tags, <requiredRuntime> element
ms.assetid: 9fa1639e-beb8-43be-b7a4-12f7b229c34b
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: ac1e1f7bc36d8d2b12b99de2794bb0ba31ddbd7a
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43398726"
---
# <a name="ltrequiredruntimegt-element"></a><span data-ttu-id="c1e2d-102">&lt;requiredRuntime&gt; elemento</span><span class="sxs-lookup"><span data-stu-id="c1e2d-102">&lt;requiredRuntime&gt; Element</span></span>
<span data-ttu-id="c1e2d-103">Especifica que o aplicativo dá suporte apenas à versão 1.0 do Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="c1e2d-103">Specifies that the application supports only version 1.0 of the common language runtime.</span></span> <span data-ttu-id="c1e2d-104">Esse elemento foi preterido e não deve mais ser usado.</span><span class="sxs-lookup"><span data-stu-id="c1e2d-104">This element is deprecated and should no longer be used.</span></span> <span data-ttu-id="c1e2d-105">O [ `supportedRuntime` ](supportedruntime-element.md) elemento deve ser usado em vez disso.</span><span class="sxs-lookup"><span data-stu-id="c1e2d-105">The [`supportedRuntime`](supportedruntime-element.md) element should be used instead.</span></span>
  
 <span data-ttu-id="c1e2d-106">\<configuration></span><span class="sxs-lookup"><span data-stu-id="c1e2d-106">\<configuration></span></span>  
<span data-ttu-id="c1e2d-107">\<startup></span><span class="sxs-lookup"><span data-stu-id="c1e2d-107">\<startup></span></span>  
<span data-ttu-id="c1e2d-108">\<requiredRuntime></span><span class="sxs-lookup"><span data-stu-id="c1e2d-108">\<requiredRuntime></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1e2d-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c1e2d-109">Syntax</span></span>  
  
```xml  
   <requiredRuntime    
version="runtime version"  
safemode="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c1e2d-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="c1e2d-110">Attributes and Elements</span></span>  
 <span data-ttu-id="c1e2d-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="c1e2d-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c1e2d-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="c1e2d-112">Attributes</span></span>  
  
|<span data-ttu-id="c1e2d-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="c1e2d-113">Attribute</span></span>|<span data-ttu-id="c1e2d-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="c1e2d-114">Description</span></span>|  
|---------------|-----------------|  
|`version`|<span data-ttu-id="c1e2d-115">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="c1e2d-115">Optional attribute.</span></span><br /><br /> <span data-ttu-id="c1e2d-116">Um valor de cadeia de caracteres que especifica a versão do .NET Framework que oferece suporte a esse aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c1e2d-116">A string value that specifies the version of the .NET Framework that this application supports.</span></span> <span data-ttu-id="c1e2d-117">O valor de cadeia de caracteres deve corresponder ao nome de diretório encontrado na raiz de instalação do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c1e2d-117">The string value must match the directory name found under the .NET Framework installation root.</span></span> <span data-ttu-id="c1e2d-118">O conteúdo do valor de cadeia de caracteres não é analisado.</span><span class="sxs-lookup"><span data-stu-id="c1e2d-118">The contents of the string value are not parsed.</span></span>|  
|`safemode`|<span data-ttu-id="c1e2d-119">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="c1e2d-119">Optional attribute.</span></span><br /><br /> <span data-ttu-id="c1e2d-120">Especifica se o código de inicialização de tempo de execução procura o registro para determinar a versão de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="c1e2d-120">Specifies whether the runtime startup code searches the registry to determine the runtime version.</span></span>|  
  
## <a name="safemode-attribute"></a><span data-ttu-id="c1e2d-121">Atributo do modo de segurança</span><span class="sxs-lookup"><span data-stu-id="c1e2d-121">safemode Attribute</span></span>  
  
|<span data-ttu-id="c1e2d-122">Valor</span><span class="sxs-lookup"><span data-stu-id="c1e2d-122">Value</span></span>|<span data-ttu-id="c1e2d-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="c1e2d-123">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="c1e2d-124">O código de inicialização de tempo de execução examina o registro.</span><span class="sxs-lookup"><span data-stu-id="c1e2d-124">The runtime startup code looks in the registry.</span></span> <span data-ttu-id="c1e2d-125">Este é o valor padrão.</span><span class="sxs-lookup"><span data-stu-id="c1e2d-125">This is the default value.</span></span>|  
|`true`|<span data-ttu-id="c1e2d-126">O código de inicialização de tempo de execução não parece no registro.</span><span class="sxs-lookup"><span data-stu-id="c1e2d-126">The runtime startup code does not look in the registry.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c1e2d-127">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="c1e2d-127">Child Elements</span></span>  
 <span data-ttu-id="c1e2d-128">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="c1e2d-128">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c1e2d-129">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="c1e2d-129">Parent Elements</span></span>  
  
|<span data-ttu-id="c1e2d-130">Elemento</span><span class="sxs-lookup"><span data-stu-id="c1e2d-130">Element</span></span>|<span data-ttu-id="c1e2d-131">Descrição</span><span class="sxs-lookup"><span data-stu-id="c1e2d-131">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="c1e2d-132">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c1e2d-132">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`startup`|<span data-ttu-id="c1e2d-133">Contém o `<requiredRuntime>` elemento.</span><span class="sxs-lookup"><span data-stu-id="c1e2d-133">Contains the `<requiredRuntime>` element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c1e2d-134">Comentários</span><span class="sxs-lookup"><span data-stu-id="c1e2d-134">Remarks</span></span>  
 <span data-ttu-id="c1e2d-135">Os aplicativos criados para oferecer suporte somente à versão 1.0 do tempo de execução devem usar o `<requiredRuntime>` elemento.</span><span class="sxs-lookup"><span data-stu-id="c1e2d-135">Applications built to support only version 1.0 of the runtime must use the `<requiredRuntime>` element.</span></span> <span data-ttu-id="c1e2d-136">Aplicativos criados usando a versão 1.1 ou posterior do tempo de execução devem usar o `<supportedRuntime>` elemento.</span><span class="sxs-lookup"><span data-stu-id="c1e2d-136">Applications built using version 1.1 or later of the runtime must use the `<supportedRuntime>` element.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c1e2d-137">Se você usar o [CorBindToRuntimeByCfg](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md) para especificar o arquivo de configuração de função, você deve usar o `<requiredRuntime>` elemento para todas as versões do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="c1e2d-137">If you use the [CorBindToRuntimeByCfg](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md) function to specify the configuration file, you must use the `<requiredRuntime>` element for all versions of the runtime.</span></span> <span data-ttu-id="c1e2d-138">O `<supportedRuntime>` elemento é ignorado quando você usa [CorBindToRuntimeByCfg](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md).</span><span class="sxs-lookup"><span data-stu-id="c1e2d-138">The `<supportedRuntime>` element is ignored when you use [CorBindToRuntimeByCfg](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md).</span></span>  
  
 <span data-ttu-id="c1e2d-139">O `version` cadeia de caracteres do atributo deve corresponder ao nome de pasta de instalação para a versão especificada do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c1e2d-139">The `version` attribute string must match the installation folder name for the specified version of the .NET Framework.</span></span> <span data-ttu-id="c1e2d-140">Essa cadeia de caracteres não é interpretada.</span><span class="sxs-lookup"><span data-stu-id="c1e2d-140">This string is not interpreted.</span></span> <span data-ttu-id="c1e2d-141">Se o código de inicialização de tempo de execução não encontrar uma pasta correspondente, o tempo de execução não será carregado; o código de inicialização mostra uma mensagem de erro e o fecha.</span><span class="sxs-lookup"><span data-stu-id="c1e2d-141">If the runtime startup code does not find a matching folder, the runtime is not loaded; the startup code shows an error message and quits.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c1e2d-142">O código de inicialização para um aplicativo que está hospedado no Microsoft Internet Explorer ignorará o `<requiredRuntime>` elemento.</span><span class="sxs-lookup"><span data-stu-id="c1e2d-142">The startup code for an application that is hosted in Microsoft Internet Explorer ignores the `<requiredRuntime>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c1e2d-143">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c1e2d-143">Example</span></span>  
 <span data-ttu-id="c1e2d-144">O exemplo a seguir mostra como especificar a versão de tempo de execução em um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="c1e2d-144">The following example shows how to specify the runtime version in a configuration file.</span></span>  
  
```xml  
<configuration>  
   <startup>  
      <requiredRuntime version="v1.0.3705" safemode="true"/>  
   </startup>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c1e2d-145">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c1e2d-145">See Also</span></span>  
 [<span data-ttu-id="c1e2d-146">Esquema de configurações de inicialização</span><span class="sxs-lookup"><span data-stu-id="c1e2d-146">Startup Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/startup/index.md)  
 [<span data-ttu-id="c1e2d-147">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="c1e2d-147">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 <span data-ttu-id="c1e2d-148">[\<PaveOver> Specifying Which Runtime Version to Use](https://msdn.microsoft.com/library/c376208d-980d-42b4-865b-fbe0d9cc97c2) (PaveOver> Especificando a versão do tempo de execução a ser usada)</span><span class="sxs-lookup"><span data-stu-id="c1e2d-148">[\<PaveOver> Specifying Which Runtime Version to Use](https://msdn.microsoft.com/library/c376208d-980d-42b4-865b-fbe0d9cc97c2)</span></span>
