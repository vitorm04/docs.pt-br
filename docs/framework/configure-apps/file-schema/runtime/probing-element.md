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
ms.openlocfilehash: e9e48ea97e1b70fef7fcc78a113e18c5fec23b7c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73115857"
---
# <a name="probing-element"></a><span data-ttu-id="58305-102">Elemento de > de investigação de \<</span><span class="sxs-lookup"><span data-stu-id="58305-102">\<probing> Element</span></span>
<span data-ttu-id="58305-103">Especifica subdiretórios base do aplicativo para a Common Language Runtime Pesquisar ao carregar assemblies.</span><span class="sxs-lookup"><span data-stu-id="58305-103">Specifies application base subdirectories for the common language runtime to search when loading assemblies.</span></span>  
  
<span data-ttu-id="58305-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="58305-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="58305-105">&nbsp; &nbsp;[ **\<runtime >** ](runtime-element.md) </span><span class="sxs-lookup"><span data-stu-id="58305-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="58305-106">&nbsp; &nbsp; &nbsp; &nbsp;[ **\<assemblyBinding**](assemblybinding-element-for-runtime.md) > </span><span class="sxs-lookup"><span data-stu-id="58305-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)</span></span>\
<span data-ttu-id="58305-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**investigação >**</span><span class="sxs-lookup"><span data-stu-id="58305-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<probing>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58305-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="58305-108">Syntax</span></span>  
  
```xml  
<probing privatePath="paths"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="58305-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="58305-109">Attributes and Elements</span></span>  
 <span data-ttu-id="58305-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="58305-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="58305-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="58305-111">Attributes</span></span>  
  
|<span data-ttu-id="58305-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="58305-112">Attribute</span></span>|<span data-ttu-id="58305-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="58305-113">Description</span></span>|  
|---------------|-----------------|  
|`privatePath`|<span data-ttu-id="58305-114">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="58305-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="58305-115">Especifica subdiretórios do diretório base do aplicativo que pode conter assemblies.</span><span class="sxs-lookup"><span data-stu-id="58305-115">Specifies subdirectories of the application's base directory that might contain assemblies.</span></span> <span data-ttu-id="58305-116">Delimite cada subdiretório com um ponto e vírgula.</span><span class="sxs-lookup"><span data-stu-id="58305-116">Delimit each subdirectory with a semicolon.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="58305-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="58305-117">Child Elements</span></span>  

<span data-ttu-id="58305-118">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="58305-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="58305-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="58305-119">Parent Elements</span></span>  
  
|<span data-ttu-id="58305-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="58305-120">Element</span></span>|<span data-ttu-id="58305-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="58305-121">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="58305-122">Contém informações sobre o redirecionamento de versão e os locais dos assemblies.</span><span class="sxs-lookup"><span data-stu-id="58305-122">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="58305-123">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="58305-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="58305-124">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="58305-124">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="58305-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="58305-125">Example</span></span>  
 <span data-ttu-id="58305-126">O exemplo a seguir mostra como especificar subdiretórios base do aplicativo em que o tempo de execução deve pesquisar assemblies.</span><span class="sxs-lookup"><span data-stu-id="58305-126">The following example shows how to specify application base subdirectories the runtime should search for assemblies.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <probing privatePath="bin;bin2\subbin;bin3"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="58305-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="58305-127">See also</span></span>

- [<span data-ttu-id="58305-128">Esquema de configurações de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="58305-128">Runtime settings schema</span></span>](index.md)
- [<span data-ttu-id="58305-129">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="58305-129">Configuration file schema</span></span>](../index.md)
- [<span data-ttu-id="58305-130">Especificar o local de um assembly</span><span class="sxs-lookup"><span data-stu-id="58305-130">Specify an assembly's location</span></span>](../../../../standard/assembly/location.md)
- [<span data-ttu-id="58305-131">Como o tempo de execução localiza assemblies</span><span class="sxs-lookup"><span data-stu-id="58305-131">How the runtime locates assemblies</span></span>](../../../deployment/how-the-runtime-locates-assemblies.md)
