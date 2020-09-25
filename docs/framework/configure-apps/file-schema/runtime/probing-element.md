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
ms.openlocfilehash: 1435ee8ea887b5d7d3e785eef0f25ffed14b1b97
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91195266"
---
# <a name="probing-element"></a><span data-ttu-id="87d89-102">Elemento \<probing></span><span class="sxs-lookup"><span data-stu-id="87d89-102">\<probing> Element</span></span>

<span data-ttu-id="87d89-103">Especifica subdiretórios base do aplicativo para a Common Language Runtime Pesquisar ao carregar assemblies.</span><span class="sxs-lookup"><span data-stu-id="87d89-103">Specifies application base subdirectories for the common language runtime to search when loading assemblies.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<probing>**  
  
## <a name="syntax"></a><span data-ttu-id="87d89-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="87d89-104">Syntax</span></span>  
  
```xml  
<probing privatePath="paths"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="87d89-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="87d89-105">Attributes and Elements</span></span>  

 <span data-ttu-id="87d89-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="87d89-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="87d89-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="87d89-107">Attributes</span></span>  
  
|<span data-ttu-id="87d89-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="87d89-108">Attribute</span></span>|<span data-ttu-id="87d89-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="87d89-109">Description</span></span>|  
|---------------|-----------------|  
|`privatePath`|<span data-ttu-id="87d89-110">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="87d89-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="87d89-111">Especifica subdiretórios do diretório base do aplicativo que pode conter assemblies.</span><span class="sxs-lookup"><span data-stu-id="87d89-111">Specifies subdirectories of the application's base directory that might contain assemblies.</span></span> <span data-ttu-id="87d89-112">Delimite cada subdiretório com um ponto e vírgula.</span><span class="sxs-lookup"><span data-stu-id="87d89-112">Delimit each subdirectory with a semicolon.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="87d89-113">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="87d89-113">Child Elements</span></span>  

<span data-ttu-id="87d89-114">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="87d89-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="87d89-115">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="87d89-115">Parent Elements</span></span>  
  
|<span data-ttu-id="87d89-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="87d89-116">Element</span></span>|<span data-ttu-id="87d89-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="87d89-117">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="87d89-118">Contém informações sobre o redirecionamento de versão e os locais dos assemblies.</span><span class="sxs-lookup"><span data-stu-id="87d89-118">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="87d89-119">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="87d89-119">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="87d89-120">Contém informações sobre associação do assembly e coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="87d89-120">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="87d89-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="87d89-121">Example</span></span>  

 <span data-ttu-id="87d89-122">O exemplo a seguir mostra como especificar subdiretórios base do aplicativo em que o tempo de execução deve pesquisar assemblies.</span><span class="sxs-lookup"><span data-stu-id="87d89-122">The following example shows how to specify application base subdirectories the runtime should search for assemblies.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <probing privatePath="bin;bin2\subbin;bin3"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="87d89-123">Veja também</span><span class="sxs-lookup"><span data-stu-id="87d89-123">See also</span></span>

- [<span data-ttu-id="87d89-124">Esquema de configurações de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="87d89-124">Runtime settings schema</span></span>](index.md)
- [<span data-ttu-id="87d89-125">Esquema do arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="87d89-125">Configuration file schema</span></span>](../index.md)
- [<span data-ttu-id="87d89-126">Especificar o local de um assembly</span><span class="sxs-lookup"><span data-stu-id="87d89-126">Specify an assembly's location</span></span>](../../../../standard/assembly/location.md)
- [<span data-ttu-id="87d89-127">Como o tempo de execução localiza assemblies</span><span class="sxs-lookup"><span data-stu-id="87d89-127">How the runtime locates assemblies</span></span>](../../../deployment/how-the-runtime-locates-assemblies.md)
