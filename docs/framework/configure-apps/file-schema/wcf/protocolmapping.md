---
title: <protocolMapping>
ms.date: 03/30/2017
ms.assetid: 5076644b-1f33-4f26-9488-87de9fcda04c
ms.openlocfilehash: 6ec17457c8742fdf17208c6588e0ab70ece7c42a
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55268660"
---
# <a name="protocolmapping"></a><span data-ttu-id="13e33-101">\<protocolMapping></span><span class="sxs-lookup"><span data-stu-id="13e33-101">\<protocolMapping></span></span>
<span data-ttu-id="13e33-102">Representa uma seção de configuração para definir um conjunto padrão de mapeamento de protocolo entre esquemas de protocolo de transporte (por exemplo, http, NET. TCP, NET. pipe, etc.) e associações do WCF.</span><span class="sxs-lookup"><span data-stu-id="13e33-102">Represents a configuration section for defining a set of default protocol mapping between transport protocol schemes (e.g., http, net.tcp, net.pipe, etc.) and WCF bindings.</span></span> <span data-ttu-id="13e33-103">Durante a criação de pontos de extremidade padrão em tempo de execução, o Windows Communication Foundation (WCF) analisa os mapeamentos configurados e decide em qual associação a ser usado para um determinado endereço de base.</span><span class="sxs-lookup"><span data-stu-id="13e33-103">When creating default endpoints at runtime, Windows Communication Foundation (WCF) looks at the configured mappings and decides on which binding to use for a particular based address.</span></span>  
  
[<span data-ttu-id="13e33-104">**\<system.serviceModel>**</span><span class="sxs-lookup"><span data-stu-id="13e33-104">**\<system.serviceModel>**</span></span>](system-servicemodel.md)  
<span data-ttu-id="13e33-105">&nbsp;&nbsp;**\<protocolMapping>**</span><span class="sxs-lookup"><span data-stu-id="13e33-105">&nbsp;&nbsp;**\<protocolMapping>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13e33-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="13e33-106">Syntax</span></span>  
  
```xml  
<protocolMapping>
  <add binding="String"
       bindingConfiguration="String"
       scheme="http/net.msmq/net.pipe/net.tcp" />
</protocolMapping>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="13e33-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="13e33-107">Attributes and Elements</span></span>  
 <span data-ttu-id="13e33-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="13e33-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="13e33-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="13e33-109">Attributes</span></span>  
 <span data-ttu-id="13e33-110">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="13e33-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="13e33-111">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="13e33-111">Child Elements</span></span>  
  
|<span data-ttu-id="13e33-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="13e33-112">Element</span></span>|<span data-ttu-id="13e33-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="13e33-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="13e33-114">\<filters></span><span class="sxs-lookup"><span data-stu-id="13e33-114">\<filters></span></span>](filters-of-routing.md)|<span data-ttu-id="13e33-115">Contém um mapeamento de protocolo padrão entre um esquema de protocolo de transporte (por exemplo, http, NET. TCP, NET. pipe, etc.) e uma associação do WCF.</span><span class="sxs-lookup"><span data-stu-id="13e33-115">Contains a default protocol mapping between a transport protocol scheme (e.g., http, net.tcp, net.pipe, etc.) and a WCF binding.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="13e33-116">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="13e33-116">Parent Elements</span></span>  
  
|<span data-ttu-id="13e33-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="13e33-117">Element</span></span>|<span data-ttu-id="13e33-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="13e33-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="13e33-119">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="13e33-119">\<system.serviceModel></span></span>](system-servicemodel.md)|<span data-ttu-id="13e33-120">O elemento raiz de todos os elementos de configuração do WCF.</span><span class="sxs-lookup"><span data-stu-id="13e33-120">The root element of all WCF configuration elements.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="13e33-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="13e33-121">Example</span></span>  
 <span data-ttu-id="13e33-122">O exemplo de configuração a seguir mostra o mapeamento de protocolo padrão no arquivo Machine. config.</span><span class="sxs-lookup"><span data-stu-id="13e33-122">The following configuration example shows the default protocol mapping in the machine.config file.</span></span> <span data-ttu-id="13e33-123">Você pode substituir esse mapeamento padrão no nível do computador, modificando o arquivo Machine. config.</span><span class="sxs-lookup"><span data-stu-id="13e33-123">You can override this default mapping at the machine level by modifying the machine.config file.</span></span> <span data-ttu-id="13e33-124">Ou, se você quiser apenas substituí-la dentro do escopo de um aplicativo, você pode substituir essa seção dentro de seu arquivo de configuração de aplicativo e alterar o mapeamento para esquemas de protocolo individual.</span><span class="sxs-lookup"><span data-stu-id="13e33-124">Or if you would only like to override it within the scope of an application, you can override this section within your application configuration file and change the mapping for individual protocol schemes.</span></span>  
  
```xml  
<protocolMapping>
  <add scheme="http"
       binding="basicHttpBinding" />
  <add scheme="net.tcp"
       binding="netTcpBinding" />
  <add scheme="net.pipe"
       binding="netNamedPipeBinding" />
  <add scheme="net.msmq"
       binding="netMsmqBinding" />
</protocolMapping>
```  
  
## <a name="see-also"></a><span data-ttu-id="13e33-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="13e33-125">See also</span></span>
- <xref:System.ServiceModel.Configuration.ProtocolMappingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Configuration.ProtocolMappingElement?displayProperty=nameWithType>
