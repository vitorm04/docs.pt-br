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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73117626"
---
# <a name="developmentmode-element"></a><span data-ttu-id="16a8d-102">Elemento \<developmentMode></span><span class="sxs-lookup"><span data-stu-id="16a8d-102">\<developmentMode> Element</span></span>
<span data-ttu-id="16a8d-103">Especifica se o runtime pesquisa por assemblies em diretórios especificados pela variável de ambiente DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="16a8d-103">Specifies whether the runtime searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<developmentMode>**  
  
## <a name="syntax"></a><span data-ttu-id="16a8d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="16a8d-104">Syntax</span></span>  
  
```xml  
<developmentMode developerInstallation="true | false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="16a8d-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="16a8d-105">Attributes and Elements</span></span>  
 <span data-ttu-id="16a8d-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="16a8d-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="16a8d-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="16a8d-107">Attributes</span></span>  
  
|<span data-ttu-id="16a8d-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="16a8d-108">Attribute</span></span>|<span data-ttu-id="16a8d-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="16a8d-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="16a8d-110">**developerInstallation**</span><span class="sxs-lookup"><span data-stu-id="16a8d-110">**developerInstallation**</span></span>|<span data-ttu-id="16a8d-111">Especifica se o runtime pesquisa por assemblies em diretórios especificados pela variável de ambiente DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="16a8d-111">Specifies whether the runtime searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>|  
  
## <a name="developerinstallation-attribute"></a><span data-ttu-id="16a8d-112">Atributo developerInstallation</span><span class="sxs-lookup"><span data-stu-id="16a8d-112">developerInstallation Attribute</span></span>  
  
|<span data-ttu-id="16a8d-113">Valor</span><span class="sxs-lookup"><span data-stu-id="16a8d-113">Value</span></span>|<span data-ttu-id="16a8d-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="16a8d-114">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="16a8d-115">**true**</span><span class="sxs-lookup"><span data-stu-id="16a8d-115">**true**</span></span>|<span data-ttu-id="16a8d-116">Pesquisa assemblies em diretórios especificados pela variável de ambiente DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="16a8d-116">Searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>|  
|<span data-ttu-id="16a8d-117">**false**</span><span class="sxs-lookup"><span data-stu-id="16a8d-117">**false**</span></span>|<span data-ttu-id="16a8d-118">Não pesquisa assemblies em diretórios especificados pela variável de ambiente DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="16a8d-118">Does not search for assemblies in directories specified by the DEVPATH environment variable.</span></span> <span data-ttu-id="16a8d-119">Esse é o padrão.</span><span class="sxs-lookup"><span data-stu-id="16a8d-119">This is the default</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="16a8d-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="16a8d-120">Child Elements</span></span>  
 <span data-ttu-id="16a8d-121">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="16a8d-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="16a8d-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="16a8d-122">Parent Elements</span></span>  
  
|<span data-ttu-id="16a8d-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="16a8d-123">Element</span></span>|<span data-ttu-id="16a8d-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="16a8d-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="16a8d-125">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="16a8d-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="16a8d-126">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="16a8d-126">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="16a8d-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="16a8d-127">Remarks</span></span>  
 <span data-ttu-id="16a8d-128">Use essa configuração somente no momento do desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="16a8d-128">Use this setting only at development time.</span></span> <span data-ttu-id="16a8d-129">O tempo de execução não verifica as versões em assemblies de nome forte encontrados no DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="16a8d-129">The runtime does not check the versions on strong-named assemblies found in the DEVPATH.</span></span> <span data-ttu-id="16a8d-130">Ele simplesmente usa o primeiro assembly que encontra.</span><span class="sxs-lookup"><span data-stu-id="16a8d-130">It simply uses the first assembly it finds.</span></span>  
  
## <a name="example"></a><span data-ttu-id="16a8d-131">Exemplo</span><span class="sxs-lookup"><span data-stu-id="16a8d-131">Example</span></span>  
 <span data-ttu-id="16a8d-132">O exemplo a seguir mostra como fazer com que o tempo de execução procure por assemblies em diretórios especificados pela variável de ambiente DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="16a8d-132">The following example shows how to cause the runtime to search for assemblies in directories specified by the DEVPATH environment variable.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <developmentMode developerInstallation="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="16a8d-133">Confira também</span><span class="sxs-lookup"><span data-stu-id="16a8d-133">See also</span></span>

- [<span data-ttu-id="16a8d-134">Esquema de configurações do runtime</span><span class="sxs-lookup"><span data-stu-id="16a8d-134">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="16a8d-135">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="16a8d-135">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="16a8d-136">Como: Localizar assemblies usando DEVPATH</span><span class="sxs-lookup"><span data-stu-id="16a8d-136">How to: Locate Assemblies by Using DEVPATH</span></span>](../../how-to-locate-assemblies-by-using-devpath.md)
