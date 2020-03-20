---
title: <Directives> (.NET Nativo)
ms.date: 03/30/2017
ms.assetid: 444846f3-48d5-4341-a43e-69f7221389eb
ms.openlocfilehash: 49c1aaf005b80a6c1c1fa382eebc2cb0dbfa4be7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181053"
---
# <a name="directives-element-net-native"></a><span data-ttu-id="89a0f-102">\<Diretrizes> Elemento (.NET Nativo)</span><span class="sxs-lookup"><span data-stu-id="89a0f-102">\<Directives> Element (.NET Native)</span></span>
<span data-ttu-id="89a0f-103">O elemento raiz em cada arquivo de diretivas de tempo de execução para .NET Native.</span><span class="sxs-lookup"><span data-stu-id="89a0f-103">The root element in every runtime directives file for .NET Native.</span></span>  
  
 `<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">`
  
## <a name="syntax"></a><span data-ttu-id="89a0f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="89a0f-104">Syntax</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <!-- child elements -->
</Directives>  
```  
  
## <a name="attributes"></a><span data-ttu-id="89a0f-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="89a0f-105">Attributes</span></span>  
  
|<span data-ttu-id="89a0f-106">Atributo</span><span class="sxs-lookup"><span data-stu-id="89a0f-106">Attribute</span></span>|<span data-ttu-id="89a0f-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="89a0f-107">Description</span></span>|  
|---------------|-----------------|  
|`xmlns`|<span data-ttu-id="89a0f-108">O namespace XML.</span><span class="sxs-lookup"><span data-stu-id="89a0f-108">The XML namespace.</span></span> <span data-ttu-id="89a0f-109">Seu valor é sempre **"http://schemas.microsoft.com/netfx/2013/01/metadata.**</span><span class="sxs-lookup"><span data-stu-id="89a0f-109">Its value is always **"http://schemas.microsoft.com/netfx/2013/01/metadata"**.</span></span>|  
  
## <a name="child-elements"></a><span data-ttu-id="89a0f-110">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="89a0f-110">Child elements</span></span>  
  
|<span data-ttu-id="89a0f-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="89a0f-111">Element</span></span>|<span data-ttu-id="89a0f-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="89a0f-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="89a0f-113">\<>de aplicação</span><span class="sxs-lookup"><span data-stu-id="89a0f-113">\<Application></span></span>](application-element-net-native.md)|<span data-ttu-id="89a0f-114">Serve como um contêiner para os tipos amplos de aplicativos cujos metadados estão disponíveis para reflexão.</span><span class="sxs-lookup"><span data-stu-id="89a0f-114">Serves as a container for application-wide types and type members whose metadata is available for reflection.</span></span>|  
|[<span data-ttu-id="89a0f-115">\<>da biblioteca</span><span class="sxs-lookup"><span data-stu-id="89a0f-115">\<Library></span></span>](library-element-net-native.md)|<span data-ttu-id="89a0f-116">Define o assembly cujos tipos de filho e membros de tipo necessitam de metadados no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="89a0f-116">Defines the assembly whose child types and type members require metadata at run time.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="89a0f-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="89a0f-117">Remarks</span></span>  
 <span data-ttu-id="89a0f-118">Cada arquivo de diretivas de runtime pode conter somente um elemento `<Directives>`.</span><span class="sxs-lookup"><span data-stu-id="89a0f-118">Each runtime directives file can contain only one `<Directives>` element.</span></span>  
  
 <span data-ttu-id="89a0f-119">O `<Directives>` elemento pode conter elemento sem zero ou um [ \<aplicativo>,](application-element-net-native.md) e zero, um ou mais [ \<](library-element-net-native.md) elementos de>de Biblioteca.</span><span class="sxs-lookup"><span data-stu-id="89a0f-119">The `<Directives>` element can contain zero or one [\<Application>](application-element-net-native.md) element, and zero, one, or more [\<Library>](library-element-net-native.md) elements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89a0f-120">Confira também</span><span class="sxs-lookup"><span data-stu-id="89a0f-120">See also</span></span>

- [<span data-ttu-id="89a0f-121">Referência do arquivo de configuração das diretivas de runtime (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="89a0f-121">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="89a0f-122">Elementos da diretiva de runtime</span><span class="sxs-lookup"><span data-stu-id="89a0f-122">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
