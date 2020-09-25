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
ms.openlocfilehash: ddcabb831193baee30016f663f32d8562283d936
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91205016"
---
# <a name="developmentmode-element"></a><span data-ttu-id="cafcc-102">Elemento \<developmentMode></span><span class="sxs-lookup"><span data-stu-id="cafcc-102">\<developmentMode> Element</span></span>

<span data-ttu-id="cafcc-103">Especifica se o runtime pesquisa por assemblies em diretórios especificados pela variável de ambiente DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="cafcc-103">Specifies whether the runtime searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<developmentMode>**  
  
## <a name="syntax"></a><span data-ttu-id="cafcc-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cafcc-104">Syntax</span></span>  
  
```xml  
<developmentMode developerInstallation="true | false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cafcc-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="cafcc-105">Attributes and Elements</span></span>  

 <span data-ttu-id="cafcc-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="cafcc-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cafcc-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="cafcc-107">Attributes</span></span>  
  
|<span data-ttu-id="cafcc-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="cafcc-108">Attribute</span></span>|<span data-ttu-id="cafcc-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="cafcc-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cafcc-110">**developerInstallation**</span><span class="sxs-lookup"><span data-stu-id="cafcc-110">**developerInstallation**</span></span>|<span data-ttu-id="cafcc-111">Especifica se o runtime pesquisa por assemblies em diretórios especificados pela variável de ambiente DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="cafcc-111">Specifies whether the runtime searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>|  
  
## <a name="developerinstallation-attribute"></a><span data-ttu-id="cafcc-112">Atributo developerInstallation</span><span class="sxs-lookup"><span data-stu-id="cafcc-112">developerInstallation Attribute</span></span>  
  
|<span data-ttu-id="cafcc-113">Valor</span><span class="sxs-lookup"><span data-stu-id="cafcc-113">Value</span></span>|<span data-ttu-id="cafcc-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="cafcc-114">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="cafcc-115">**true**</span><span class="sxs-lookup"><span data-stu-id="cafcc-115">**true**</span></span>|<span data-ttu-id="cafcc-116">Pesquisa assemblies em diretórios especificados pela variável de ambiente DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="cafcc-116">Searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>|  
|<span data-ttu-id="cafcc-117">**false**</span><span class="sxs-lookup"><span data-stu-id="cafcc-117">**false**</span></span>|<span data-ttu-id="cafcc-118">Não pesquisa assemblies em diretórios especificados pela variável de ambiente DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="cafcc-118">Does not search for assemblies in directories specified by the DEVPATH environment variable.</span></span> <span data-ttu-id="cafcc-119">Esse é o padrão.</span><span class="sxs-lookup"><span data-stu-id="cafcc-119">This is the default</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cafcc-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="cafcc-120">Child Elements</span></span>  

 <span data-ttu-id="cafcc-121">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="cafcc-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cafcc-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="cafcc-122">Parent Elements</span></span>  
  
|<span data-ttu-id="cafcc-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="cafcc-123">Element</span></span>|<span data-ttu-id="cafcc-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="cafcc-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="cafcc-125">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="cafcc-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="cafcc-126">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="cafcc-126">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cafcc-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="cafcc-127">Remarks</span></span>  

 <span data-ttu-id="cafcc-128">Use essa configuração somente no momento do desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="cafcc-128">Use this setting only at development time.</span></span> <span data-ttu-id="cafcc-129">O tempo de execução não verifica as versões em assemblies de nome forte encontrados no DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="cafcc-129">The runtime does not check the versions on strong-named assemblies found in the DEVPATH.</span></span> <span data-ttu-id="cafcc-130">Ele simplesmente usa o primeiro assembly que encontra.</span><span class="sxs-lookup"><span data-stu-id="cafcc-130">It simply uses the first assembly it finds.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cafcc-131">Exemplo</span><span class="sxs-lookup"><span data-stu-id="cafcc-131">Example</span></span>  

 <span data-ttu-id="cafcc-132">O exemplo a seguir mostra como fazer com que o tempo de execução procure por assemblies em diretórios especificados pela variável de ambiente DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="cafcc-132">The following example shows how to cause the runtime to search for assemblies in directories specified by the DEVPATH environment variable.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <developmentMode developerInstallation="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="cafcc-133">Veja também</span><span class="sxs-lookup"><span data-stu-id="cafcc-133">See also</span></span>

- [<span data-ttu-id="cafcc-134">Esquema de configurações do runtime</span><span class="sxs-lookup"><span data-stu-id="cafcc-134">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="cafcc-135">Esquema do arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="cafcc-135">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="cafcc-136">Como: Localizar assemblies usando DEVPATH</span><span class="sxs-lookup"><span data-stu-id="cafcc-136">How to: Locate Assemblies by Using DEVPATH</span></span>](../../how-to-locate-assemblies-by-using-devpath.md)
