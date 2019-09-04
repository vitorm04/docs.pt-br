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
ms.openlocfilehash: 0253c3ced52b575097fe5d18abb8ce188c0164fb
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252690"
---
# <a name="developmentmode-element"></a><span data-ttu-id="63eb0-102">\<Elemento de > developmentmode</span><span class="sxs-lookup"><span data-stu-id="63eb0-102">\<developmentMode> Element</span></span>
<span data-ttu-id="63eb0-103">Especifica se o tempo de execução pesquisa por assemblies em diretórios especificados pela variável de ambiente DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="63eb0-103">Specifies whether the runtime searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>  
  
<span data-ttu-id="63eb0-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="63eb0-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="63eb0-105">&nbsp;&nbsp;[ **\<> de tempo de execução**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="63eb0-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="63eb0-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<developmentMode>**</span><span class="sxs-lookup"><span data-stu-id="63eb0-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<developmentMode>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63eb0-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="63eb0-107">Syntax</span></span>  
  
```xml  
<developmentMode developerInstallation="true | false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="63eb0-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="63eb0-108">Attributes and Elements</span></span>  
 <span data-ttu-id="63eb0-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="63eb0-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="63eb0-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="63eb0-110">Attributes</span></span>  
  
|<span data-ttu-id="63eb0-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="63eb0-111">Attribute</span></span>|<span data-ttu-id="63eb0-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="63eb0-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="63eb0-113">**developerInstallation**</span><span class="sxs-lookup"><span data-stu-id="63eb0-113">**developerInstallation**</span></span>|<span data-ttu-id="63eb0-114">Especifica se o tempo de execução pesquisa por assemblies em diretórios especificados pela variável de ambiente DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="63eb0-114">Specifies whether the runtime searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>|  
  
## <a name="developerinstallation-attribute"></a><span data-ttu-id="63eb0-115">Atributo developerInstallation</span><span class="sxs-lookup"><span data-stu-id="63eb0-115">developerInstallation Attribute</span></span>  
  
|<span data-ttu-id="63eb0-116">Valor</span><span class="sxs-lookup"><span data-stu-id="63eb0-116">Value</span></span>|<span data-ttu-id="63eb0-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="63eb0-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="63eb0-118">**true**</span><span class="sxs-lookup"><span data-stu-id="63eb0-118">**true**</span></span>|<span data-ttu-id="63eb0-119">Pesquisa assemblies em diretórios especificados pela variável de ambiente DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="63eb0-119">Searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>|  
|<span data-ttu-id="63eb0-120">**false**</span><span class="sxs-lookup"><span data-stu-id="63eb0-120">**false**</span></span>|<span data-ttu-id="63eb0-121">Não pesquisa assemblies em diretórios especificados pela variável de ambiente DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="63eb0-121">Does not search for assemblies in directories specified by the DEVPATH environment variable.</span></span> <span data-ttu-id="63eb0-122">Este é o padrão</span><span class="sxs-lookup"><span data-stu-id="63eb0-122">This is the default</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="63eb0-123">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="63eb0-123">Child Elements</span></span>  
 <span data-ttu-id="63eb0-124">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="63eb0-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="63eb0-125">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="63eb0-125">Parent Elements</span></span>  
  
|<span data-ttu-id="63eb0-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="63eb0-126">Element</span></span>|<span data-ttu-id="63eb0-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="63eb0-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="63eb0-128">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="63eb0-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="63eb0-129">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="63eb0-129">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="63eb0-130">Comentários</span><span class="sxs-lookup"><span data-stu-id="63eb0-130">Remarks</span></span>  
 <span data-ttu-id="63eb0-131">Use essa configuração somente no momento do desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="63eb0-131">Use this setting only at development time.</span></span> <span data-ttu-id="63eb0-132">O tempo de execução não verifica as versões em assemblies de nome forte encontrados no DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="63eb0-132">The runtime does not check the versions on strong-named assemblies found in the DEVPATH.</span></span> <span data-ttu-id="63eb0-133">Ele simplesmente usa o primeiro assembly que encontra.</span><span class="sxs-lookup"><span data-stu-id="63eb0-133">It simply uses the first assembly it finds.</span></span>  
  
## <a name="example"></a><span data-ttu-id="63eb0-134">Exemplo</span><span class="sxs-lookup"><span data-stu-id="63eb0-134">Example</span></span>  
 <span data-ttu-id="63eb0-135">O exemplo a seguir mostra como fazer com que o tempo de execução procure por assemblies em diretórios especificados pela variável de ambiente DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="63eb0-135">The following example shows how to cause the runtime to search for assemblies in directories specified by the DEVPATH environment variable.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <developmentMode developerInstallation="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="63eb0-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="63eb0-136">See also</span></span>

- [<span data-ttu-id="63eb0-137">Esquema de configurações do tempo de execução</span><span class="sxs-lookup"><span data-stu-id="63eb0-137">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="63eb0-138">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="63eb0-138">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="63eb0-139">Como: Localizar assemblies usando DEVPATH</span><span class="sxs-lookup"><span data-stu-id="63eb0-139">How to: Locate Assemblies by Using DEVPATH</span></span>](../../how-to-locate-assemblies-by-using-devpath.md)
