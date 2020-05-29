---
title: <Directives> (.NET Nativo)
ms.date: 03/30/2017
ms.assetid: 444846f3-48d5-4341-a43e-69f7221389eb
ms.openlocfilehash: 0c6ebb8954e80f3f6dc6733f0e9d76094477689b
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2020
ms.locfileid: "84202377"
---
# <a name="directives-element-net-native"></a><span data-ttu-id="fe81b-102">\<Directives> (.NET Nativo)</span><span class="sxs-lookup"><span data-stu-id="fe81b-102">\<Directives> Element (.NET Native)</span></span>
<span data-ttu-id="fe81b-103">O elemento raiz em cada arquivo de diretivas de tempo de execução para .NET Native.</span><span class="sxs-lookup"><span data-stu-id="fe81b-103">The root element in every runtime directives file for .NET Native.</span></span>  
  
 `<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">`
  
## <a name="syntax"></a><span data-ttu-id="fe81b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fe81b-104">Syntax</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <!-- child elements -->
</Directives>  
```  
  
## <a name="attributes"></a><span data-ttu-id="fe81b-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="fe81b-105">Attributes</span></span>  
  
|<span data-ttu-id="fe81b-106">Atributo</span><span class="sxs-lookup"><span data-stu-id="fe81b-106">Attribute</span></span>|<span data-ttu-id="fe81b-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="fe81b-107">Description</span></span>|  
|---------------|-----------------|  
|`xmlns`|<span data-ttu-id="fe81b-108">O namespace XML.</span><span class="sxs-lookup"><span data-stu-id="fe81b-108">The XML namespace.</span></span> <span data-ttu-id="fe81b-109">Seu valor é sempre `http://schemas.microsoft.com/netfx/2013/01/metadata` .</span><span class="sxs-lookup"><span data-stu-id="fe81b-109">Its value is always `http://schemas.microsoft.com/netfx/2013/01/metadata`.</span></span>|  
  
## <a name="child-elements"></a><span data-ttu-id="fe81b-110">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="fe81b-110">Child elements</span></span>  
  
|<span data-ttu-id="fe81b-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="fe81b-111">Element</span></span>|<span data-ttu-id="fe81b-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="fe81b-112">Description</span></span>|  
|-------------|-----------------|  
|[\<Application>](application-element-net-native.md)|<span data-ttu-id="fe81b-113">Serve como um contêiner para os tipos amplos de aplicativos cujos metadados estão disponíveis para reflexão.</span><span class="sxs-lookup"><span data-stu-id="fe81b-113">Serves as a container for application-wide types and type members whose metadata is available for reflection.</span></span>|  
|[\<Library>](library-element-net-native.md)|<span data-ttu-id="fe81b-114">Define o assembly cujos tipos de filho e membros de tipo necessitam de metadados no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="fe81b-114">Defines the assembly whose child types and type members require metadata at run time.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fe81b-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="fe81b-115">Remarks</span></span>  
 <span data-ttu-id="fe81b-116">Cada arquivo de diretivas de runtime pode conter somente um elemento `<Directives>`.</span><span class="sxs-lookup"><span data-stu-id="fe81b-116">Each runtime directives file can contain only one `<Directives>` element.</span></span>  
  
 <span data-ttu-id="fe81b-117">O `<Directives>` elemento pode conter zero ou um [\<Application>](application-element-net-native.md) elemento e zero, um ou mais [\<Library>](library-element-net-native.md) elementos.</span><span class="sxs-lookup"><span data-stu-id="fe81b-117">The `<Directives>` element can contain zero or one [\<Application>](application-element-net-native.md) element, and zero, one, or more [\<Library>](library-element-net-native.md) elements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe81b-118">Veja também</span><span class="sxs-lookup"><span data-stu-id="fe81b-118">See also</span></span>

- [<span data-ttu-id="fe81b-119">Referência do arquivo de configuração das diretivas de runtime (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="fe81b-119">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="fe81b-120">Elementos da diretiva de runtime</span><span class="sxs-lookup"><span data-stu-id="fe81b-120">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
