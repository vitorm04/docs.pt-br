---
title: '&lt;protocolMapping&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5076644b-1f33-4f26-9488-87de9fcda04c
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 769ca7b96c3671fdd1b154c99516778f7cbd542e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="ltprotocolmappinggt"></a><span data-ttu-id="9a3bf-102">&lt;protocolMapping&gt;</span><span class="sxs-lookup"><span data-stu-id="9a3bf-102">&lt;protocolMapping&gt;</span></span>
<span data-ttu-id="9a3bf-103">Representa uma seção de configuração para definir um conjunto de mapeamento de padrão de protocolo entre esquemas de protocolo de transporte (por exemplo, http, net.tcp, NET. pipe, etc.) e as associações do WCF.</span><span class="sxs-lookup"><span data-stu-id="9a3bf-103">Represents a configuration section for defining a set of default protocol mapping between transport protocol schemes (e.g., http, net.tcp, net.pipe, etc.) and WCF bindings.</span></span> <span data-ttu-id="9a3bf-104">Durante a criação de pontos de extremidade padrão em tempo de execução, [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] examina os mapeamentos configurados e decide em qual associação a ser usado para um determinado com base em endereço.</span><span class="sxs-lookup"><span data-stu-id="9a3bf-104">When creating default endpoints at runtime, [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] looks at the configured mappings and decides on which binding to use for a particular based address.</span></span>  
  
 <span data-ttu-id="9a3bf-105">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="9a3bf-105">\<system.serviceModel></span></span>  
<span data-ttu-id="9a3bf-106">\<protocolMapping ></span><span class="sxs-lookup"><span data-stu-id="9a3bf-106">\<protocolMapping></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a3bf-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9a3bf-107">Syntax</span></span>  
  
```xml
   <protocolMapping>    <add binding="String"         bindingConfiguration="String"         scheme="http/net.msmq/net.pipe/net.tcp"/></protocolMapping>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9a3bf-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="9a3bf-108">Attributes and Elements</span></span>  
 <span data-ttu-id="9a3bf-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="9a3bf-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9a3bf-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="9a3bf-110">Attributes</span></span>  
 <span data-ttu-id="9a3bf-111">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="9a3bf-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="9a3bf-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="9a3bf-112">Child Elements</span></span>  
  
|<span data-ttu-id="9a3bf-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="9a3bf-113">Element</span></span>|<span data-ttu-id="9a3bf-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="9a3bf-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9a3bf-115">\<Filtros ></span><span class="sxs-lookup"><span data-stu-id="9a3bf-115">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|<span data-ttu-id="9a3bf-116">Contém um mapeamento de protocolo padrão entre um esquema de protocolo de transporte (por exemplo, http, net.tcp, NET. pipe, etc.) e uma associação WCF.</span><span class="sxs-lookup"><span data-stu-id="9a3bf-116">Contains a default protocol mapping between a transport protocol scheme (e.g., http, net.tcp, net.pipe, etc.) and a WCF binding.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9a3bf-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="9a3bf-117">Parent Elements</span></span>  
  
|<span data-ttu-id="9a3bf-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="9a3bf-118">Element</span></span>|<span data-ttu-id="9a3bf-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="9a3bf-119">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9a3bf-120">sistema.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="9a3bf-120">system.ServiceModel</span></span>|<span data-ttu-id="9a3bf-121">O elemento raiz de todos os elementos de configuração do WCF.</span><span class="sxs-lookup"><span data-stu-id="9a3bf-121">The root element of all WCF configuration elements.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="9a3bf-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9a3bf-122">Example</span></span>  
 <span data-ttu-id="9a3bf-123">O exemplo de configuração a seguir mostra o mapeamento de padrão de protocolo no arquivo Machine. config.</span><span class="sxs-lookup"><span data-stu-id="9a3bf-123">The following configuration example shows the default protocol mapping in the machine.config file.</span></span> <span data-ttu-id="9a3bf-124">Você pode substituir esse mapeamento padrão no nível do computador, modificando o arquivo Machine. config.</span><span class="sxs-lookup"><span data-stu-id="9a3bf-124">You can override this default mapping at the machine level by modifying the machine.config file.</span></span> <span data-ttu-id="9a3bf-125">Ou, se você apenas deseja substituí-la dentro do escopo de um aplicativo, você pode substituir esta seção dentro de seu arquivo de configuração do aplicativo e alterar o mapeamento para esquemas de protocolo individual.</span><span class="sxs-lookup"><span data-stu-id="9a3bf-125">Or if you would only like to override it within the scope of an application, you can override this section within your application configuration file and change the mapping for individual protocol schemes.</span></span>  
  
```xml  
<protocolMapping>  
        <add scheme="http" binding="basicHttpBinding"/>  
        <add scheme="net.tcp" binding="netTcpBinding"/>  
        <add scheme="net.pipe" binding="netNamedPipeBinding"/>  
        <add scheme="net.msmq" binding="netMsmqBinding"/>  
</protocolMapping>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9a3bf-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9a3bf-126">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ProtocolMappingSection?displayProperty=nameWithType>       
 <xref:System.ServiceModel.Configuration.ProtocolMappingElement?displayProperty=nameWithType>    
