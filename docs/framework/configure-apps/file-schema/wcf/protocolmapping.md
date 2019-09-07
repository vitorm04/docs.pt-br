---
title: <protocolMapping>
ms.date: 03/30/2017
ms.assetid: 5076644b-1f33-4f26-9488-87de9fcda04c
ms.openlocfilehash: be4224ef1a8b17653df8123aaf89e105a496355a
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400015"
---
# <a name="protocolmapping"></a><span data-ttu-id="4b63c-101">\<> protocolMapping</span><span class="sxs-lookup"><span data-stu-id="4b63c-101">\<protocolMapping></span></span>
<span data-ttu-id="4b63c-102">Representa uma seção de configuração para definir um conjunto de mapeamentos de protocolo padrão entre esquemas de protocolo de transporte (por exemplo, http, net. TCP, net. pipe, etc.) e associações do WCF.</span><span class="sxs-lookup"><span data-stu-id="4b63c-102">Represents a configuration section for defining a set of default protocol mapping between transport protocol schemes (e.g., http, net.tcp, net.pipe, etc.) and WCF bindings.</span></span> <span data-ttu-id="4b63c-103">Ao criar pontos de extremidade padrão em tempo de execução, Windows Communication Foundation (WCF) examina os mapeamentos configurados e decide qual associação usar para um endereço baseado em particular.</span><span class="sxs-lookup"><span data-stu-id="4b63c-103">When creating default endpoints at runtime, Windows Communication Foundation (WCF) looks at the configured mappings and decides on which binding to use for a particular based address.</span></span>  
  
<span data-ttu-id="4b63c-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="4b63c-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="4b63c-105">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="4b63c-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="4b63c-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<> protocolMapping**</span><span class="sxs-lookup"><span data-stu-id="4b63c-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<protocolMapping>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b63c-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4b63c-107">Syntax</span></span>  
  
```xml  
<protocolMapping>
  <add binding="String"
       bindingConfiguration="String"
       scheme="http/net.msmq/net.pipe/net.tcp" />
</protocolMapping>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4b63c-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="4b63c-108">Attributes and Elements</span></span>  
 <span data-ttu-id="4b63c-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="4b63c-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4b63c-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="4b63c-110">Attributes</span></span>  
 <span data-ttu-id="4b63c-111">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="4b63c-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="4b63c-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="4b63c-112">Child Elements</span></span>  
  
|<span data-ttu-id="4b63c-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="4b63c-113">Element</span></span>|<span data-ttu-id="4b63c-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="4b63c-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4b63c-115">\<filters></span><span class="sxs-lookup"><span data-stu-id="4b63c-115">\<filters></span></span>](filters-of-routing.md)|<span data-ttu-id="4b63c-116">Contém um mapeamento de protocolo padrão entre um esquema de protocolo de transporte (por exemplo, http, net. TCP, net. pipe, etc.) e uma associação do WCF.</span><span class="sxs-lookup"><span data-stu-id="4b63c-116">Contains a default protocol mapping between a transport protocol scheme (e.g., http, net.tcp, net.pipe, etc.) and a WCF binding.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4b63c-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="4b63c-117">Parent Elements</span></span>  
  
|<span data-ttu-id="4b63c-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="4b63c-118">Element</span></span>|<span data-ttu-id="4b63c-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="4b63c-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4b63c-120">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="4b63c-120">\<system.serviceModel></span></span>](system-servicemodel.md)|<span data-ttu-id="4b63c-121">O elemento raiz de todos os elementos de configuração do WCF.</span><span class="sxs-lookup"><span data-stu-id="4b63c-121">The root element of all WCF configuration elements.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="4b63c-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4b63c-122">Example</span></span>  
 <span data-ttu-id="4b63c-123">O exemplo de configuração a seguir mostra o mapeamento de protocolo padrão no arquivo Machine. config.</span><span class="sxs-lookup"><span data-stu-id="4b63c-123">The following configuration example shows the default protocol mapping in the machine.config file.</span></span> <span data-ttu-id="4b63c-124">Você pode substituir esse mapeamento padrão no nível do computador modificando o arquivo Machine. config.</span><span class="sxs-lookup"><span data-stu-id="4b63c-124">You can override this default mapping at the machine level by modifying the machine.config file.</span></span> <span data-ttu-id="4b63c-125">Ou, se você quiser apenas substituí-lo no escopo de um aplicativo, poderá substituir esta seção no arquivo de configuração do aplicativo e alterar o mapeamento para esquemas de protocolo individuais.</span><span class="sxs-lookup"><span data-stu-id="4b63c-125">Or if you would only like to override it within the scope of an application, you can override this section within your application configuration file and change the mapping for individual protocol schemes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4b63c-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4b63c-126">See also</span></span>

- <xref:System.ServiceModel.Configuration.ProtocolMappingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Configuration.ProtocolMappingElement?displayProperty=nameWithType>
