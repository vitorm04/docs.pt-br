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
ms.openlocfilehash: 4a062da31740edb8f0c7a4f4db8b09800c687587
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73117626"
---
# <a name="developmentmode-element"></a><span data-ttu-id="5d1e1-102">Elemento de > de desenvolvimento do \<</span><span class="sxs-lookup"><span data-stu-id="5d1e1-102">\<developmentMode> Element</span></span>
<span data-ttu-id="5d1e1-103">Especifica se o tempo de execução pesquisa por assemblies em diretórios especificados pela variável de ambiente DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="5d1e1-103">Specifies whether the runtime searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>  
  
<span data-ttu-id="5d1e1-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="5d1e1-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="5d1e1-105">&nbsp; &nbsp;[ **\<runtime >** ](runtime-element.md) </span><span class="sxs-lookup"><span data-stu-id="5d1e1-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="5d1e1-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<developmentmode >**</span><span class="sxs-lookup"><span data-stu-id="5d1e1-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<developmentMode>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d1e1-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5d1e1-107">Syntax</span></span>  
  
```xml  
<developmentMode developerInstallation="true | false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5d1e1-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="5d1e1-108">Attributes and Elements</span></span>  
 <span data-ttu-id="5d1e1-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="5d1e1-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5d1e1-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="5d1e1-110">Attributes</span></span>  
  
|<span data-ttu-id="5d1e1-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="5d1e1-111">Attribute</span></span>|<span data-ttu-id="5d1e1-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="5d1e1-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5d1e1-113">**developerInstallation**</span><span class="sxs-lookup"><span data-stu-id="5d1e1-113">**developerInstallation**</span></span>|<span data-ttu-id="5d1e1-114">Especifica se o tempo de execução pesquisa por assemblies em diretórios especificados pela variável de ambiente DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="5d1e1-114">Specifies whether the runtime searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>|  
  
## <a name="developerinstallation-attribute"></a><span data-ttu-id="5d1e1-115">Atributo developerInstallation</span><span class="sxs-lookup"><span data-stu-id="5d1e1-115">developerInstallation Attribute</span></span>  
  
|<span data-ttu-id="5d1e1-116">Valor</span><span class="sxs-lookup"><span data-stu-id="5d1e1-116">Value</span></span>|<span data-ttu-id="5d1e1-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="5d1e1-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="5d1e1-118">**true**</span><span class="sxs-lookup"><span data-stu-id="5d1e1-118">**true**</span></span>|<span data-ttu-id="5d1e1-119">Pesquisa assemblies em diretórios especificados pela variável de ambiente DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="5d1e1-119">Searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>|  
|<span data-ttu-id="5d1e1-120">**false**</span><span class="sxs-lookup"><span data-stu-id="5d1e1-120">**false**</span></span>|<span data-ttu-id="5d1e1-121">Não pesquisa assemblies em diretórios especificados pela variável de ambiente DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="5d1e1-121">Does not search for assemblies in directories specified by the DEVPATH environment variable.</span></span> <span data-ttu-id="5d1e1-122">Este é o padrão</span><span class="sxs-lookup"><span data-stu-id="5d1e1-122">This is the default</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5d1e1-123">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="5d1e1-123">Child Elements</span></span>  
 <span data-ttu-id="5d1e1-124">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="5d1e1-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5d1e1-125">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="5d1e1-125">Parent Elements</span></span>  
  
|<span data-ttu-id="5d1e1-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="5d1e1-126">Element</span></span>|<span data-ttu-id="5d1e1-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="5d1e1-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="5d1e1-128">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5d1e1-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="5d1e1-129">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="5d1e1-129">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5d1e1-130">Comentários</span><span class="sxs-lookup"><span data-stu-id="5d1e1-130">Remarks</span></span>  
 <span data-ttu-id="5d1e1-131">Use essa configuração somente no momento do desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="5d1e1-131">Use this setting only at development time.</span></span> <span data-ttu-id="5d1e1-132">O tempo de execução não verifica as versões em assemblies de nome forte encontrados no DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="5d1e1-132">The runtime does not check the versions on strong-named assemblies found in the DEVPATH.</span></span> <span data-ttu-id="5d1e1-133">Ele simplesmente usa o primeiro assembly que encontra.</span><span class="sxs-lookup"><span data-stu-id="5d1e1-133">It simply uses the first assembly it finds.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5d1e1-134">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5d1e1-134">Example</span></span>  
 <span data-ttu-id="5d1e1-135">O exemplo a seguir mostra como fazer com que o tempo de execução procure por assemblies em diretórios especificados pela variável de ambiente DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="5d1e1-135">The following example shows how to cause the runtime to search for assemblies in directories specified by the DEVPATH environment variable.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <developmentMode developerInstallation="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5d1e1-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5d1e1-136">See also</span></span>

- [<span data-ttu-id="5d1e1-137">Esquema de configurações do tempo de execução</span><span class="sxs-lookup"><span data-stu-id="5d1e1-137">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="5d1e1-138">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="5d1e1-138">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="5d1e1-139">Como localizar assemblies usando DEVPATH</span><span class="sxs-lookup"><span data-stu-id="5d1e1-139">How to: Locate Assemblies by Using DEVPATH</span></span>](../../how-to-locate-assemblies-by-using-devpath.md)
