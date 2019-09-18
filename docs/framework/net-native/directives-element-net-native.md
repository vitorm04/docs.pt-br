---
title: <Directives> (.NET Nativo)
ms.date: 03/30/2017
ms.assetid: 444846f3-48d5-4341-a43e-69f7221389eb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a9ec9a09e2fc03adbfcff0d7e69489e37da6e4a5
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71049876"
---
# <a name="directives-element-net-native"></a><span data-ttu-id="8172e-102">\<Elemento > de diretivas (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="8172e-102">\<Directives> Element (.NET Native)</span></span>
<span data-ttu-id="8172e-103">O elemento raiz em cada arquivo de diretivas de tempo de execução para .NET Native.</span><span class="sxs-lookup"><span data-stu-id="8172e-103">The root element in every runtime directives file for .NET Native.</span></span>  
  
 `<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">` 
  
## <a name="syntax"></a><span data-ttu-id="8172e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8172e-104">Syntax</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <!-- child elements -->   
</Directives>  
```  
  
## <a name="attributes"></a><span data-ttu-id="8172e-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="8172e-105">Attributes</span></span>  
  
|<span data-ttu-id="8172e-106">Atributo</span><span class="sxs-lookup"><span data-stu-id="8172e-106">Attribute</span></span>|<span data-ttu-id="8172e-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="8172e-107">Description</span></span>|  
|---------------|-----------------|  
|`xmlns`|<span data-ttu-id="8172e-108">O namespace XML.</span><span class="sxs-lookup"><span data-stu-id="8172e-108">The XML namespace.</span></span> <span data-ttu-id="8172e-109">Seu valor é sempre **"http://schemas.microsoft.com/netfx/2013/01/metadata"** .</span><span class="sxs-lookup"><span data-stu-id="8172e-109">Its value is always **"http://schemas.microsoft.com/netfx/2013/01/metadata"**.</span></span>|  
  
## <a name="child-elements"></a><span data-ttu-id="8172e-110">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="8172e-110">Child elements</span></span>  
  
|<span data-ttu-id="8172e-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="8172e-111">Element</span></span>|<span data-ttu-id="8172e-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="8172e-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8172e-113">\<Application></span><span class="sxs-lookup"><span data-stu-id="8172e-113">\<Application></span></span>](application-element-net-native.md)|<span data-ttu-id="8172e-114">Serve como um contêiner para os tipos amplos de aplicativos cujos metadados estão disponíveis para reflexão.</span><span class="sxs-lookup"><span data-stu-id="8172e-114">Serves as a container for application-wide types and type members whose metadata is available for reflection.</span></span>|  
|[<span data-ttu-id="8172e-115">\<Library></span><span class="sxs-lookup"><span data-stu-id="8172e-115">\<Library></span></span>](library-element-net-native.md)|<span data-ttu-id="8172e-116">Define o assembly cujos tipos de filho e membros de tipo necessitam de metadados no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="8172e-116">Defines the assembly whose child types and type members require metadata at run time.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8172e-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="8172e-117">Remarks</span></span>  
 <span data-ttu-id="8172e-118">Cada arquivo de diretivas de tempo de execução pode conter somente um elemento `<Directives>`.</span><span class="sxs-lookup"><span data-stu-id="8172e-118">Each runtime directives file can contain only one `<Directives>` element.</span></span>  
  
 <span data-ttu-id="8172e-119">O elemento `<Directives>` pode conter zero ou um elemento [\<Application>](application-element-net-native.md) e zero, um ou mais elementos [\<Library>](library-element-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="8172e-119">The `<Directives>` element can contain zero or one [\<Application>](application-element-net-native.md) element, and zero, one, or more [\<Library>](library-element-net-native.md) elements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8172e-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8172e-120">See also</span></span>

- [<span data-ttu-id="8172e-121">Referência do arquivo de configuração das diretivas de tempo de execução (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="8172e-121">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="8172e-122">Elementos da diretiva de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="8172e-122">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
