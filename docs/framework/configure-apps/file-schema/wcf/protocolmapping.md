---
title: '&lt;ProtocolMapping&gt;'
ms.date: 03/30/2017
ms.assetid: 5076644b-1f33-4f26-9488-87de9fcda04c
ms.openlocfilehash: 4afdaaa62c1ac3241eb7382d0995bed51bde73e2
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltprotocolmappinggt"></a><span data-ttu-id="5b5b4-102">&lt;ProtocolMapping&gt;</span><span class="sxs-lookup"><span data-stu-id="5b5b4-102">&lt;protocolMapping&gt;</span></span>
<span data-ttu-id="5b5b4-103">Representa uma seção de configuração para definir um conjunto de mapeamento de padrão de protocolo entre esquemas de protocolo de transporte (por exemplo, http, net.tcp, NET. pipe, etc.) e as associações do WCF.</span><span class="sxs-lookup"><span data-stu-id="5b5b4-103">Represents a configuration section for defining a set of default protocol mapping between transport protocol schemes (e.g., http, net.tcp, net.pipe, etc.) and WCF bindings.</span></span> <span data-ttu-id="5b5b4-104">Durante a criação de pontos de extremidade padrão em tempo de execução, o Windows Communication Foundation (WCF) examina os mapeamentos configurados e decide em qual associação a ser usado para um determinado com base em endereço.</span><span class="sxs-lookup"><span data-stu-id="5b5b4-104">When creating default endpoints at runtime, Windows Communication Foundation (WCF) looks at the configured mappings and decides on which binding to use for a particular based address.</span></span>  
  
 <span data-ttu-id="5b5b4-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="5b5b4-105">\<system.serviceModel></span></span>  
<span data-ttu-id="5b5b4-106">\<protocolMapping ></span><span class="sxs-lookup"><span data-stu-id="5b5b4-106">\<protocolMapping></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b5b4-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5b5b4-107">Syntax</span></span>  
  
```xml
   <protocolMapping>    <add binding="String"         bindingConfiguration="String"         scheme="http/net.msmq/net.pipe/net.tcp"/></protocolMapping>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5b5b4-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="5b5b4-108">Attributes and Elements</span></span>  
 <span data-ttu-id="5b5b4-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="5b5b4-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5b5b4-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="5b5b4-110">Attributes</span></span>  
 <span data-ttu-id="5b5b4-111">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="5b5b4-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5b5b4-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="5b5b4-112">Child Elements</span></span>  
  
|<span data-ttu-id="5b5b4-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="5b5b4-113">Element</span></span>|<span data-ttu-id="5b5b4-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="5b5b4-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5b5b4-115">\<Filtros ></span><span class="sxs-lookup"><span data-stu-id="5b5b4-115">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|<span data-ttu-id="5b5b4-116">Contém um mapeamento de protocolo padrão entre um esquema de protocolo de transporte (por exemplo, http, net.tcp, NET. pipe, etc.) e uma associação WCF.</span><span class="sxs-lookup"><span data-stu-id="5b5b4-116">Contains a default protocol mapping between a transport protocol scheme (e.g., http, net.tcp, net.pipe, etc.) and a WCF binding.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5b5b4-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="5b5b4-117">Parent Elements</span></span>  
  
|<span data-ttu-id="5b5b4-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="5b5b4-118">Element</span></span>|<span data-ttu-id="5b5b4-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="5b5b4-119">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5b5b4-120">sistema.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="5b5b4-120">system.ServiceModel</span></span>|<span data-ttu-id="5b5b4-121">O elemento raiz de todos os elementos de configuração do WCF.</span><span class="sxs-lookup"><span data-stu-id="5b5b4-121">The root element of all WCF configuration elements.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="5b5b4-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5b5b4-122">Example</span></span>  
 <span data-ttu-id="5b5b4-123">O exemplo de configuração a seguir mostra o mapeamento de padrão de protocolo no arquivo Machine. config.</span><span class="sxs-lookup"><span data-stu-id="5b5b4-123">The following configuration example shows the default protocol mapping in the machine.config file.</span></span> <span data-ttu-id="5b5b4-124">Você pode substituir esse mapeamento padrão no nível do computador, modificando o arquivo Machine. config.</span><span class="sxs-lookup"><span data-stu-id="5b5b4-124">You can override this default mapping at the machine level by modifying the machine.config file.</span></span> <span data-ttu-id="5b5b4-125">Ou, se você apenas deseja substituí-la dentro do escopo de um aplicativo, você pode substituir esta seção dentro de seu arquivo de configuração do aplicativo e alterar o mapeamento para esquemas de protocolo individual.</span><span class="sxs-lookup"><span data-stu-id="5b5b4-125">Or if you would only like to override it within the scope of an application, you can override this section within your application configuration file and change the mapping for individual protocol schemes.</span></span>  
  
```xml  
<protocolMapping>  
        <add scheme="http" binding="basicHttpBinding"/>  
        <add scheme="net.tcp" binding="netTcpBinding"/>  
        <add scheme="net.pipe" binding="netNamedPipeBinding"/>  
        <add scheme="net.msmq" binding="netMsmqBinding"/>  
</protocolMapping>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5b5b4-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5b5b4-126">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ProtocolMappingSection?displayProperty=nameWithType>       
 <xref:System.ServiceModel.Configuration.ProtocolMappingElement?displayProperty=nameWithType>    
