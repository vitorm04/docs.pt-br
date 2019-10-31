---
title: <Directives> (.NET Nativo)
ms.date: 03/30/2017
ms.assetid: 444846f3-48d5-4341-a43e-69f7221389eb
ms.openlocfilehash: abe2e7221e0afb984a6178b12fabc36ea24deb35
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128469"
---
# <a name="directives-element-net-native"></a><span data-ttu-id="dccb3-102">Elemento de > de diretivas de \<(.NET Native)</span><span class="sxs-lookup"><span data-stu-id="dccb3-102">\<Directives> Element (.NET Native)</span></span>
<span data-ttu-id="dccb3-103">O elemento raiz em cada arquivo de diretivas de tempo de execução para .NET Native.</span><span class="sxs-lookup"><span data-stu-id="dccb3-103">The root element in every runtime directives file for .NET Native.</span></span>  
  
 `<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">` 
  
## <a name="syntax"></a><span data-ttu-id="dccb3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="dccb3-104">Syntax</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <!-- child elements -->   
</Directives>  
```  
  
## <a name="attributes"></a><span data-ttu-id="dccb3-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="dccb3-105">Attributes</span></span>  
  
|<span data-ttu-id="dccb3-106">Atributo</span><span class="sxs-lookup"><span data-stu-id="dccb3-106">Attribute</span></span>|<span data-ttu-id="dccb3-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="dccb3-107">Description</span></span>|  
|---------------|-----------------|  
|`xmlns`|<span data-ttu-id="dccb3-108">O namespace XML.</span><span class="sxs-lookup"><span data-stu-id="dccb3-108">The XML namespace.</span></span> <span data-ttu-id="dccb3-109">Seu valor é sempre **"http://schemas.microsoft.com/netfx/2013/01/metadata"** .</span><span class="sxs-lookup"><span data-stu-id="dccb3-109">Its value is always **"http://schemas.microsoft.com/netfx/2013/01/metadata"**.</span></span>|  
  
## <a name="child-elements"></a><span data-ttu-id="dccb3-110">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="dccb3-110">Child elements</span></span>  
  
|<span data-ttu-id="dccb3-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="dccb3-111">Element</span></span>|<span data-ttu-id="dccb3-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="dccb3-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dccb3-113">\<Application></span><span class="sxs-lookup"><span data-stu-id="dccb3-113">\<Application></span></span>](application-element-net-native.md)|<span data-ttu-id="dccb3-114">Serve como um contêiner para os tipos amplos de aplicativos cujos metadados estão disponíveis para reflexão.</span><span class="sxs-lookup"><span data-stu-id="dccb3-114">Serves as a container for application-wide types and type members whose metadata is available for reflection.</span></span>|  
|[<span data-ttu-id="dccb3-115">\<Library></span><span class="sxs-lookup"><span data-stu-id="dccb3-115">\<Library></span></span>](library-element-net-native.md)|<span data-ttu-id="dccb3-116">Define o assembly cujos tipos de filho e membros de tipo necessitam de metadados no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="dccb3-116">Defines the assembly whose child types and type members require metadata at run time.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dccb3-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="dccb3-117">Remarks</span></span>  
 <span data-ttu-id="dccb3-118">Cada arquivo de diretivas de tempo de execução pode conter somente um elemento `<Directives>`.</span><span class="sxs-lookup"><span data-stu-id="dccb3-118">Each runtime directives file can contain only one `<Directives>` element.</span></span>  
  
 <span data-ttu-id="dccb3-119">O elemento `<Directives>` pode conter zero ou um elemento [\<Application>](application-element-net-native.md) e zero, um ou mais elementos [\<Library>](library-element-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="dccb3-119">The `<Directives>` element can contain zero or one [\<Application>](application-element-net-native.md) element, and zero, one, or more [\<Library>](library-element-net-native.md) elements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dccb3-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dccb3-120">See also</span></span>

- [<span data-ttu-id="dccb3-121">Referência do arquivo de configuração das diretivas de tempo de execução (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="dccb3-121">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="dccb3-122">Elementos da diretiva de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="dccb3-122">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
