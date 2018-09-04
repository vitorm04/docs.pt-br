---
title: Elemento &lt;Directives&gt; (.NET Nativo)
ms.date: 03/30/2017
ms.assetid: 444846f3-48d5-4341-a43e-69f7221389eb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8921d2841f9a7b4228ae3b8735d7047453f71bcb
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43556511"
---
# <a name="ltdirectivesgt-element-net-native"></a><span data-ttu-id="7c397-102">Elemento &lt;Directives&gt; (.NET Nativo)</span><span class="sxs-lookup"><span data-stu-id="7c397-102">&lt;Directives&gt; Element (.NET Native)</span></span>
<span data-ttu-id="7c397-103">O elemento raiz em cada arquivo de diretivas de tempo de execução para .NET nativo.</span><span class="sxs-lookup"><span data-stu-id="7c397-103">The root element in every runtime directives file for .NET Native.</span></span>  
  
 `<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">` 
  
## <a name="syntax"></a><span data-ttu-id="7c397-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7c397-104">Syntax</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <!-- child elements -->   
</Directives>  
```  
  
## <a name="attributes"></a><span data-ttu-id="7c397-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="7c397-105">Attributes</span></span>  
  
|<span data-ttu-id="7c397-106">Atributo</span><span class="sxs-lookup"><span data-stu-id="7c397-106">Attribute</span></span>|<span data-ttu-id="7c397-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="7c397-107">Description</span></span>|  
|---------------|-----------------|  
|`xmlns`|<span data-ttu-id="7c397-108">O namespace XML.</span><span class="sxs-lookup"><span data-stu-id="7c397-108">The XML namespace.</span></span> <span data-ttu-id="7c397-109">Seu valor é sempre **"http://schemas.microsoft.com/netfx/2013/01/metadata"**.</span><span class="sxs-lookup"><span data-stu-id="7c397-109">Its value is always **"http://schemas.microsoft.com/netfx/2013/01/metadata"**.</span></span>|  
  
## <a name="child-elements"></a><span data-ttu-id="7c397-110">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="7c397-110">Child elements</span></span>  
  
|<span data-ttu-id="7c397-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="7c397-111">Element</span></span>|<span data-ttu-id="7c397-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="7c397-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7c397-113">\<Application></span><span class="sxs-lookup"><span data-stu-id="7c397-113">\<Application></span></span>](../../../docs/framework/net-native/application-element-net-native.md)|<span data-ttu-id="7c397-114">Serve como um contêiner para os tipos amplos de aplicativos cujos metadados estão disponíveis para reflexão.</span><span class="sxs-lookup"><span data-stu-id="7c397-114">Serves as a container for application-wide types and type members whose metadata is available for reflection.</span></span>|  
|[<span data-ttu-id="7c397-115">\<Library></span><span class="sxs-lookup"><span data-stu-id="7c397-115">\<Library></span></span>](../../../docs/framework/net-native/library-element-net-native.md)|<span data-ttu-id="7c397-116">Define o assembly cujos tipos de filho e membros de tipo necessitam de metadados no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="7c397-116">Defines the assembly whose child types and type members require metadata at run time.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7c397-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="7c397-117">Remarks</span></span>  
 <span data-ttu-id="7c397-118">Cada arquivo de diretivas de tempo de execução pode conter somente um elemento `<Directives>`.</span><span class="sxs-lookup"><span data-stu-id="7c397-118">Each runtime directives file can contain only one `<Directives>` element.</span></span>  
  
 <span data-ttu-id="7c397-119">O elemento `<Directives>` pode conter zero ou um elemento [\<Application>](../../../docs/framework/net-native/application-element-net-native.md) e zero, um ou mais elementos [\<Library>](../../../docs/framework/net-native/library-element-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="7c397-119">The `<Directives>` element can contain zero or one [\<Application>](../../../docs/framework/net-native/application-element-net-native.md) element, and zero, one, or more [\<Library>](../../../docs/framework/net-native/library-element-net-native.md) elements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c397-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7c397-120">See Also</span></span>  
 [<span data-ttu-id="7c397-121">Referência do arquivo de configuração das diretivas de tempo de execução (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="7c397-121">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [<span data-ttu-id="7c397-122">Elementos da diretiva de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="7c397-122">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)
