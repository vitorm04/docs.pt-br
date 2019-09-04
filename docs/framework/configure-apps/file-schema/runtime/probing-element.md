---
title: Elemento <probing>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/probing
- http://schemas.microsoft.com/.NetConfiguration/v2.0#probing
helpviewer_keywords:
- <probing> element
- container tags, <probing> element
- probing element
ms.assetid: 09c80fc9-1ba5-4192-89f7-3a79b2e4b024
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 05634cb319ac69bd76e16e592ba59490b30c9c9d
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252395"
---
# <a name="probing-element"></a><span data-ttu-id="0c16e-102">\<Elemento de > de investigação</span><span class="sxs-lookup"><span data-stu-id="0c16e-102">\<probing> Element</span></span>
<span data-ttu-id="0c16e-103">Especifica subdiretórios base do aplicativo para a Common Language Runtime Pesquisar ao carregar assemblies.</span><span class="sxs-lookup"><span data-stu-id="0c16e-103">Specifies application base subdirectories for the common language runtime to search when loading assemblies.</span></span>  
  
<span data-ttu-id="0c16e-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="0c16e-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="0c16e-105">&nbsp;&nbsp;[ **\<> de tempo de execução**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="0c16e-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="0c16e-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> assemblyBinding**](assemblybinding-element-for-runtime.md)</span><span class="sxs-lookup"><span data-stu-id="0c16e-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)</span></span>\
<span data-ttu-id="0c16e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<probing>**</span><span class="sxs-lookup"><span data-stu-id="0c16e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<probing>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c16e-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0c16e-108">Syntax</span></span>  
  
```xml  
<probing privatePath="paths"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0c16e-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="0c16e-109">Attributes and Elements</span></span>  
 <span data-ttu-id="0c16e-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="0c16e-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0c16e-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="0c16e-111">Attributes</span></span>  
  
|<span data-ttu-id="0c16e-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="0c16e-112">Attribute</span></span>|<span data-ttu-id="0c16e-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="0c16e-113">Description</span></span>|  
|---------------|-----------------|  
|`privatePath`|<span data-ttu-id="0c16e-114">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="0c16e-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="0c16e-115">Especifica subdiretórios do diretório base do aplicativo que pode conter assemblies.</span><span class="sxs-lookup"><span data-stu-id="0c16e-115">Specifies subdirectories of the application's base directory that might contain assemblies.</span></span> <span data-ttu-id="0c16e-116">Delimite cada subdiretório com um ponto e vírgula.</span><span class="sxs-lookup"><span data-stu-id="0c16e-116">Delimit each subdirectory with a semicolon.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0c16e-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="0c16e-117">Child Elements</span></span>  

<span data-ttu-id="0c16e-118">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="0c16e-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0c16e-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="0c16e-119">Parent Elements</span></span>  
  
|<span data-ttu-id="0c16e-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="0c16e-120">Element</span></span>|<span data-ttu-id="0c16e-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="0c16e-121">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="0c16e-122">Contém informações sobre o redirecionamento de versão e os locais dos assemblies.</span><span class="sxs-lookup"><span data-stu-id="0c16e-122">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="0c16e-123">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0c16e-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="0c16e-124">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="0c16e-124">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="0c16e-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0c16e-125">Example</span></span>  
 <span data-ttu-id="0c16e-126">O exemplo a seguir mostra como especificar subdiretórios base do aplicativo em que o tempo de execução deve pesquisar assemblies.</span><span class="sxs-lookup"><span data-stu-id="0c16e-126">The following example shows how to specify application base subdirectories the runtime should search for assemblies.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <probing privatePath="bin;bin2\subbin;bin3"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0c16e-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0c16e-127">See also</span></span>

- [<span data-ttu-id="0c16e-128">Esquema de configurações do tempo de execução</span><span class="sxs-lookup"><span data-stu-id="0c16e-128">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="0c16e-129">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="0c16e-129">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="0c16e-130">Especificando o local de um assembly</span><span class="sxs-lookup"><span data-stu-id="0c16e-130">Specifying an Assembly's Location</span></span>](../../specify-assembly-location.md)
- [<span data-ttu-id="0c16e-131">Como o tempo de execução localiza assemblies</span><span class="sxs-lookup"><span data-stu-id="0c16e-131">How the Runtime Locates Assemblies</span></span>](../../../deployment/how-the-runtime-locates-assemblies.md)
