---
title: Elemento <developmentMode>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/developmentMode
- http://schemas.microsoft.com/.NetConfiguration/v2.0#developmentMode
helpviewer_keywords:
- developmentMode element
- container tags, <developmentMode> element
- <developmentMode> element
ms.assetid: 60e79a8c-415a-497d-be29-b9d0fd9bdee3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 323bc5d18860c00609a92e33f4a2bd2c832b05a9
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55290063"
---
# <a name="developmentmode-element"></a><span data-ttu-id="5e39f-102">\<developmentMode > elemento</span><span class="sxs-lookup"><span data-stu-id="5e39f-102">\<developmentMode> Element</span></span>
<span data-ttu-id="5e39f-103">Especifica se o tempo de execução pesquisa por assemblies em diretórios especificados pela variável de ambiente DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="5e39f-103">Specifies whether the runtime searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>  
  
 <span data-ttu-id="5e39f-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="5e39f-104">\<configuration></span></span>  
<span data-ttu-id="5e39f-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="5e39f-105">\<runtime></span></span>  
<span data-ttu-id="5e39f-106">\<developmentMode></span><span class="sxs-lookup"><span data-stu-id="5e39f-106">\<developmentMode></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e39f-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5e39f-107">Syntax</span></span>  
  
```xml  
<developmentMode developerInstallation="true | false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5e39f-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="5e39f-108">Attributes and Elements</span></span>  
 <span data-ttu-id="5e39f-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="5e39f-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5e39f-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="5e39f-110">Attributes</span></span>  
  
|<span data-ttu-id="5e39f-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="5e39f-111">Attribute</span></span>|<span data-ttu-id="5e39f-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="5e39f-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5e39f-113">**developerInstallation**</span><span class="sxs-lookup"><span data-stu-id="5e39f-113">**developerInstallation**</span></span>|<span data-ttu-id="5e39f-114">Especifica se o tempo de execução pesquisa por assemblies em diretórios especificados pela variável de ambiente DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="5e39f-114">Specifies whether the runtime searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>|  
  
## <a name="developerinstallation-attribute"></a><span data-ttu-id="5e39f-115">developerInstallation atributo</span><span class="sxs-lookup"><span data-stu-id="5e39f-115">developerInstallation Attribute</span></span>  
  
|<span data-ttu-id="5e39f-116">Valor</span><span class="sxs-lookup"><span data-stu-id="5e39f-116">Value</span></span>|<span data-ttu-id="5e39f-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="5e39f-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="5e39f-118">**true**</span><span class="sxs-lookup"><span data-stu-id="5e39f-118">**true**</span></span>|<span data-ttu-id="5e39f-119">Procura por assemblies em diretórios especificados pela variável de ambiente DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="5e39f-119">Searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>|  
|<span data-ttu-id="5e39f-120">**false**</span><span class="sxs-lookup"><span data-stu-id="5e39f-120">**false**</span></span>|<span data-ttu-id="5e39f-121">Não procura por assemblies em diretórios especificados pela variável de ambiente DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="5e39f-121">Does not search for assemblies in directories specified by the DEVPATH environment variable.</span></span> <span data-ttu-id="5e39f-122">Esse é o padrão</span><span class="sxs-lookup"><span data-stu-id="5e39f-122">This is the default</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5e39f-123">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="5e39f-123">Child Elements</span></span>  
 <span data-ttu-id="5e39f-124">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="5e39f-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5e39f-125">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="5e39f-125">Parent Elements</span></span>  
  
|<span data-ttu-id="5e39f-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="5e39f-126">Element</span></span>|<span data-ttu-id="5e39f-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="5e39f-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="5e39f-128">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5e39f-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="5e39f-129">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="5e39f-129">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5e39f-130">Comentários</span><span class="sxs-lookup"><span data-stu-id="5e39f-130">Remarks</span></span>  
 <span data-ttu-id="5e39f-131">Use essa configuração somente em tempo de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="5e39f-131">Use this setting only at development time.</span></span> <span data-ttu-id="5e39f-132">O tempo de execução não verifica as versões de assemblies de nome forte encontrados no DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="5e39f-132">The runtime does not check the versions on strong-named assemblies found in the DEVPATH.</span></span> <span data-ttu-id="5e39f-133">Ela simplesmente usa o assembly primeiro que ele localiza.</span><span class="sxs-lookup"><span data-stu-id="5e39f-133">It simply uses the first assembly it finds.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5e39f-134">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5e39f-134">Example</span></span>  
 <span data-ttu-id="5e39f-135">O exemplo a seguir mostra como fazer com que o tempo de execução pesquisa dos assemblies em diretórios especificados pela variável de ambiente DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="5e39f-135">The following example shows how to cause the runtime to search for assemblies in directories specified by the DEVPATH environment variable.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <developmentMode developerInstallation="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5e39f-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5e39f-136">See also</span></span>
- [<span data-ttu-id="5e39f-137">Esquema de configurações do tempo de execução</span><span class="sxs-lookup"><span data-stu-id="5e39f-137">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="5e39f-138">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="5e39f-138">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="5e39f-139">Como: Localizar Assemblies usando DEVPATH</span><span class="sxs-lookup"><span data-stu-id="5e39f-139">How to: Locate Assemblies by Using DEVPATH</span></span>](../../../../../docs/framework/configure-apps/how-to-locate-assemblies-by-using-devpath.md)
