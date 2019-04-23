---
title: <protocolMapping>
ms.date: 03/30/2017
ms.assetid: 5076644b-1f33-4f26-9488-87de9fcda04c
ms.openlocfilehash: e26044340bda84fe38b7e286edf833affa94b86c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59118203"
---
# <a name="protocolmapping"></a><span data-ttu-id="4acf4-101">\<protocolMapping></span><span class="sxs-lookup"><span data-stu-id="4acf4-101">\<protocolMapping></span></span>
<span data-ttu-id="4acf4-102">Representa uma seção de configuração para definir um conjunto padrão de mapeamento de protocolo entre esquemas de protocolo de transporte (por exemplo, http, NET. TCP, NET. pipe, etc.) e associações do WCF.</span><span class="sxs-lookup"><span data-stu-id="4acf4-102">Represents a configuration section for defining a set of default protocol mapping between transport protocol schemes (e.g., http, net.tcp, net.pipe, etc.) and WCF bindings.</span></span> <span data-ttu-id="4acf4-103">Durante a criação de pontos de extremidade padrão em tempo de execução, o Windows Communication Foundation (WCF) analisa os mapeamentos configurados e decide em qual associação a ser usado para um determinado endereço de base.</span><span class="sxs-lookup"><span data-stu-id="4acf4-103">When creating default endpoints at runtime, Windows Communication Foundation (WCF) looks at the configured mappings and decides on which binding to use for a particular based address.</span></span>  
  
[<span data-ttu-id="4acf4-104">**\<system.serviceModel>**</span><span class="sxs-lookup"><span data-stu-id="4acf4-104">**\<system.serviceModel>**</span></span>](system-servicemodel.md)  
<span data-ttu-id="4acf4-105">&nbsp;&nbsp;**\<protocolMapping>**</span><span class="sxs-lookup"><span data-stu-id="4acf4-105">&nbsp;&nbsp;**\<protocolMapping>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4acf4-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4acf4-106">Syntax</span></span>  
  
```xml  
<protocolMapping>
  <add binding="String"
       bindingConfiguration="String"
       scheme="http/net.msmq/net.pipe/net.tcp" />
</protocolMapping>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4acf4-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="4acf4-107">Attributes and Elements</span></span>  
 <span data-ttu-id="4acf4-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="4acf4-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4acf4-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="4acf4-109">Attributes</span></span>  
 <span data-ttu-id="4acf4-110">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="4acf4-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="4acf4-111">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="4acf4-111">Child Elements</span></span>  
  
|<span data-ttu-id="4acf4-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="4acf4-112">Element</span></span>|<span data-ttu-id="4acf4-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="4acf4-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4acf4-114">\<filters></span><span class="sxs-lookup"><span data-stu-id="4acf4-114">\<filters></span></span>](filters-of-routing.md)|<span data-ttu-id="4acf4-115">Contém um mapeamento de protocolo padrão entre um esquema de protocolo de transporte (por exemplo, http, NET. TCP, NET. pipe, etc.) e uma associação do WCF.</span><span class="sxs-lookup"><span data-stu-id="4acf4-115">Contains a default protocol mapping between a transport protocol scheme (e.g., http, net.tcp, net.pipe, etc.) and a WCF binding.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4acf4-116">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="4acf4-116">Parent Elements</span></span>  
  
|<span data-ttu-id="4acf4-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="4acf4-117">Element</span></span>|<span data-ttu-id="4acf4-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="4acf4-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4acf4-119">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="4acf4-119">\<system.serviceModel></span></span>](system-servicemodel.md)|<span data-ttu-id="4acf4-120">O elemento raiz de todos os elementos de configuração do WCF.</span><span class="sxs-lookup"><span data-stu-id="4acf4-120">The root element of all WCF configuration elements.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="4acf4-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4acf4-121">Example</span></span>  
 <span data-ttu-id="4acf4-122">O exemplo de configuração a seguir mostra o mapeamento de protocolo padrão no arquivo Machine. config.</span><span class="sxs-lookup"><span data-stu-id="4acf4-122">The following configuration example shows the default protocol mapping in the machine.config file.</span></span> <span data-ttu-id="4acf4-123">Você pode substituir esse mapeamento padrão no nível do computador, modificando o arquivo Machine. config.</span><span class="sxs-lookup"><span data-stu-id="4acf4-123">You can override this default mapping at the machine level by modifying the machine.config file.</span></span> <span data-ttu-id="4acf4-124">Ou, se você quiser apenas substituí-la dentro do escopo de um aplicativo, você pode substituir essa seção dentro de seu arquivo de configuração de aplicativo e alterar o mapeamento para esquemas de protocolo individual.</span><span class="sxs-lookup"><span data-stu-id="4acf4-124">Or if you would only like to override it within the scope of an application, you can override this section within your application configuration file and change the mapping for individual protocol schemes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4acf4-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4acf4-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.ProtocolMappingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Configuration.ProtocolMappingElement?displayProperty=nameWithType>
