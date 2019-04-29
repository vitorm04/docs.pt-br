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
ms.openlocfilehash: fdf840035150f08c894c984213af9a0abe6e95af
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61704759"
---
# <a name="developmentmode-element"></a><span data-ttu-id="43148-102">\<developmentMode > elemento</span><span class="sxs-lookup"><span data-stu-id="43148-102">\<developmentMode> Element</span></span>
<span data-ttu-id="43148-103">Especifica se o tempo de execução pesquisa por assemblies em diretórios especificados pela variável de ambiente DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="43148-103">Specifies whether the runtime searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>  
  
 <span data-ttu-id="43148-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="43148-104">\<configuration></span></span>  
<span data-ttu-id="43148-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="43148-105">\<runtime></span></span>  
<span data-ttu-id="43148-106">\<developmentMode></span><span class="sxs-lookup"><span data-stu-id="43148-106">\<developmentMode></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43148-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="43148-107">Syntax</span></span>  
  
```xml  
<developmentMode developerInstallation="true | false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="43148-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="43148-108">Attributes and Elements</span></span>  
 <span data-ttu-id="43148-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="43148-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="43148-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="43148-110">Attributes</span></span>  
  
|<span data-ttu-id="43148-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="43148-111">Attribute</span></span>|<span data-ttu-id="43148-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="43148-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="43148-113">**developerInstallation**</span><span class="sxs-lookup"><span data-stu-id="43148-113">**developerInstallation**</span></span>|<span data-ttu-id="43148-114">Especifica se o tempo de execução pesquisa por assemblies em diretórios especificados pela variável de ambiente DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="43148-114">Specifies whether the runtime searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>|  
  
## <a name="developerinstallation-attribute"></a><span data-ttu-id="43148-115">developerInstallation atributo</span><span class="sxs-lookup"><span data-stu-id="43148-115">developerInstallation Attribute</span></span>  
  
|<span data-ttu-id="43148-116">Valor</span><span class="sxs-lookup"><span data-stu-id="43148-116">Value</span></span>|<span data-ttu-id="43148-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="43148-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="43148-118">**true**</span><span class="sxs-lookup"><span data-stu-id="43148-118">**true**</span></span>|<span data-ttu-id="43148-119">Procura por assemblies em diretórios especificados pela variável de ambiente DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="43148-119">Searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>|  
|<span data-ttu-id="43148-120">**false**</span><span class="sxs-lookup"><span data-stu-id="43148-120">**false**</span></span>|<span data-ttu-id="43148-121">Não procura por assemblies em diretórios especificados pela variável de ambiente DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="43148-121">Does not search for assemblies in directories specified by the DEVPATH environment variable.</span></span> <span data-ttu-id="43148-122">Esse é o padrão</span><span class="sxs-lookup"><span data-stu-id="43148-122">This is the default</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="43148-123">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="43148-123">Child Elements</span></span>  
 <span data-ttu-id="43148-124">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="43148-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="43148-125">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="43148-125">Parent Elements</span></span>  
  
|<span data-ttu-id="43148-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="43148-126">Element</span></span>|<span data-ttu-id="43148-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="43148-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="43148-128">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="43148-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="43148-129">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="43148-129">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="43148-130">Comentários</span><span class="sxs-lookup"><span data-stu-id="43148-130">Remarks</span></span>  
 <span data-ttu-id="43148-131">Use essa configuração somente em tempo de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="43148-131">Use this setting only at development time.</span></span> <span data-ttu-id="43148-132">O tempo de execução não verifica as versões de assemblies de nome forte encontrados no DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="43148-132">The runtime does not check the versions on strong-named assemblies found in the DEVPATH.</span></span> <span data-ttu-id="43148-133">Ela simplesmente usa o assembly primeiro que ele localiza.</span><span class="sxs-lookup"><span data-stu-id="43148-133">It simply uses the first assembly it finds.</span></span>  
  
## <a name="example"></a><span data-ttu-id="43148-134">Exemplo</span><span class="sxs-lookup"><span data-stu-id="43148-134">Example</span></span>  
 <span data-ttu-id="43148-135">O exemplo a seguir mostra como fazer com que o tempo de execução pesquisa dos assemblies em diretórios especificados pela variável de ambiente DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="43148-135">The following example shows how to cause the runtime to search for assemblies in directories specified by the DEVPATH environment variable.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <developmentMode developerInstallation="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="43148-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="43148-136">See also</span></span>

- [<span data-ttu-id="43148-137">Esquema de configurações do tempo de execução</span><span class="sxs-lookup"><span data-stu-id="43148-137">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="43148-138">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="43148-138">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="43148-139">Como: Localizar Assemblies usando DEVPATH</span><span class="sxs-lookup"><span data-stu-id="43148-139">How to: Locate Assemblies by Using DEVPATH</span></span>](../../../../../docs/framework/configure-apps/how-to-locate-assemblies-by-using-devpath.md)
