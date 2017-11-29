---
title: Elemento &lt;Directives&gt; (.NET Nativo)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 444846f3-48d5-4341-a43e-69f7221389eb
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a55048ea5b2889da82b10ac2a51865d945635143
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ltdirectivesgt-element-net-native"></a><span data-ttu-id="a3166-102">Elemento &lt;Directives&gt; (.NET Nativo)</span><span class="sxs-lookup"><span data-stu-id="a3166-102">&lt;Directives&gt; Element (.NET Native)</span></span>
<span data-ttu-id="a3166-103">O elemento raiz em todos os arquivos de diretivas de tempo de execução para [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a3166-103">The root element in every runtime directives file for [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span></span>  
  
 <span data-ttu-id="a3166-104">**\<Diretivas xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">**</span><span class="sxs-lookup"><span data-stu-id="a3166-104">**\<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3166-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a3166-105">Syntax</span></span>  
  
```xml  
      <Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <!-- child elements -->   
</Directives>  
```  
  
## <a name="attributes"></a><span data-ttu-id="a3166-106">Atributos</span><span class="sxs-lookup"><span data-stu-id="a3166-106">Attributes</span></span>  
  
|<span data-ttu-id="a3166-107">Atributo</span><span class="sxs-lookup"><span data-stu-id="a3166-107">Attribute</span></span>|<span data-ttu-id="a3166-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="a3166-108">Description</span></span>|  
|---------------|-----------------|  
|`xmlns`|<span data-ttu-id="a3166-109">O namespace XML.</span><span class="sxs-lookup"><span data-stu-id="a3166-109">The XML namespace.</span></span> <span data-ttu-id="a3166-110">Seu valor é sempre **“http://schemas.microsoft.com/netfx/2013/01/metadata”**.</span><span class="sxs-lookup"><span data-stu-id="a3166-110">Its value is always **"http://schemas.microsoft.com/netfx/2013/01/metadata"**.</span></span>|  
  
## <a name="child-elements"></a><span data-ttu-id="a3166-111">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="a3166-111">Child elements</span></span>  
  
|<span data-ttu-id="a3166-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="a3166-112">Element</span></span>|<span data-ttu-id="a3166-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="a3166-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a3166-114">\<Application></span><span class="sxs-lookup"><span data-stu-id="a3166-114">\<Application></span></span>](../../../docs/framework/net-native/application-element-net-native.md)|<span data-ttu-id="a3166-115">Serve como um contêiner para os tipos amplos de aplicativos cujos metadados estão disponíveis para reflexão.</span><span class="sxs-lookup"><span data-stu-id="a3166-115">Serves as a container for application-wide types and type members whose metadata is available for reflection.</span></span>|  
|[<span data-ttu-id="a3166-116">\<Library></span><span class="sxs-lookup"><span data-stu-id="a3166-116">\<Library></span></span>](../../../docs/framework/net-native/library-element-net-native.md)|<span data-ttu-id="a3166-117">Define o assembly cujos tipos de filho e membros de tipo necessitam de metadados no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="a3166-117">Defines the assembly whose child types and type members require metadata at run time.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a3166-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="a3166-118">Remarks</span></span>  
 <span data-ttu-id="a3166-119">Cada arquivo de diretivas de tempo de execução pode conter somente um elemento `<Directives>`.</span><span class="sxs-lookup"><span data-stu-id="a3166-119">Each runtime directives file can contain only one `<Directives>` element.</span></span>  
  
 <span data-ttu-id="a3166-120">O elemento `<Directives>` pode conter zero ou um elemento [\<Application>](../../../docs/framework/net-native/application-element-net-native.md) e zero, um ou mais elementos [\<Library>](../../../docs/framework/net-native/library-element-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="a3166-120">The `<Directives>` element can contain zero or one [\<Application>](../../../docs/framework/net-native/application-element-net-native.md) element, and zero, one, or more [\<Library>](../../../docs/framework/net-native/library-element-net-native.md) elements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3166-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a3166-121">See Also</span></span>  
 [<span data-ttu-id="a3166-122">Referência do arquivo de configuração das diretivas de tempo de execução (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="a3166-122">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [<span data-ttu-id="a3166-123">Elementos da diretiva de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="a3166-123">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)
