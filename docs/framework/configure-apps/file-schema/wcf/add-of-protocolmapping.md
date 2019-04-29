---
title: <add> de <protocolMapping>
ms.date: 03/30/2017
ms.assetid: 08e62249-1641-41d1-91b1-66d7b46244e4
ms.openlocfilehash: 85d09c920de2ca1ab4971551ff98ea58c4492f44
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61704486"
---
# <a name="add-of-protocolmapping"></a><span data-ttu-id="a7453-102">\<Adicionar > de \<protocolMapping ></span><span class="sxs-lookup"><span data-stu-id="a7453-102">\<add> of \<protocolMapping></span></span>
<span data-ttu-id="a7453-103">Representa um mapeamento de protocolo padrão entre um esquema de protocolo de transporte (por exemplo, http, NET. TCP, NET. pipe, etc.) e uma associação do Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="a7453-103">Represents a default protocol mapping between a transport protocol scheme (e.g., http, net.tcp, net.pipe, etc.) and a Windows Communication Foundation (WCF) binding.</span></span> <span data-ttu-id="a7453-104">Durante a criação de pontos de extremidade padrão em tempo de execução, o WCF analisa os mapeamentos configurados e decide em qual associação a ser usado para um determinado endereço de base.</span><span class="sxs-lookup"><span data-stu-id="a7453-104">When creating default endpoints at runtime, WCF looks at the configured mappings and decides on which binding to use for a particular based address.</span></span>  
  
 <span data-ttu-id="a7453-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="a7453-105">\<system.serviceModel></span></span>  
<span data-ttu-id="a7453-106">\<protocolMapping></span><span class="sxs-lookup"><span data-stu-id="a7453-106">\<protocolMapping></span></span>  
<span data-ttu-id="a7453-107">\<add></span><span class="sxs-lookup"><span data-stu-id="a7453-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7453-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a7453-108">Syntax</span></span>  
  
```xml  
<protocolMapping>
  <add binding="String"
       bindingConfiguration="String"
       scheme="http/net.msmq/net.pipe/net.tcp" />
</protocolMapping>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a7453-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="a7453-109">Attributes and Elements</span></span>  
 <span data-ttu-id="a7453-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="a7453-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a7453-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="a7453-111">Attributes</span></span>  
  
|<span data-ttu-id="a7453-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="a7453-112">Element</span></span>|<span data-ttu-id="a7453-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="a7453-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a7453-114">associação</span><span class="sxs-lookup"><span data-stu-id="a7453-114">binding</span></span>|<span data-ttu-id="a7453-115">Uma cadeia de caracteres que especifica o tipo de associação a ser usado para um ponto de extremidade durante a criação do ponto de extremidade padrão.</span><span class="sxs-lookup"><span data-stu-id="a7453-115">A string that specifies the type of binding to be used for an endpoint during default endpoint creation.</span></span>|  
|<span data-ttu-id="a7453-116">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="a7453-116">bindingConfiguration</span></span>|<span data-ttu-id="a7453-117">Uma cadeia de caracteres que especifica o nome da seção de configuração de associação a ser referenciado.</span><span class="sxs-lookup"><span data-stu-id="a7453-117">A string that specifies the name of the binding configuration section to be referenced.</span></span>|  
|<span data-ttu-id="a7453-118">esquema</span><span class="sxs-lookup"><span data-stu-id="a7453-118">scheme</span></span>|<span data-ttu-id="a7453-119">O esquema de protocolo de transporte a ser usado para o ponto de extremidade padrão.</span><span class="sxs-lookup"><span data-stu-id="a7453-119">The transport protocol scheme to be used for the default endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a7453-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="a7453-120">Child Elements</span></span>  
 <span data-ttu-id="a7453-121">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="a7453-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a7453-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="a7453-122">Parent Elements</span></span>  
  
|<span data-ttu-id="a7453-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="a7453-123">Element</span></span>|<span data-ttu-id="a7453-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="a7453-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a7453-125">\<protocolMapping></span><span class="sxs-lookup"><span data-stu-id="a7453-125">\<protocolMapping></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/protocolmapping.md)|<span data-ttu-id="a7453-126">Representa uma seção de configuração para definir mapeamentos de protocolo padrão entre esquemas de protocolo de transporte (por exemplo, http, NET. TCP, NET. pipe, etc.) e associações do Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="a7453-126">Represents a configuration section for defining default protocol mappings between transport protocol schemes (e.g., http, net.tcp, net.pipe, etc.) and Windows Communication Foundation (WCF) bindings.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="a7453-127">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a7453-127">Example</span></span>  
 <span data-ttu-id="a7453-128">O exemplo de configuração a seguir mostra o mapeamento de protocolo padrão no arquivo Machine. config.</span><span class="sxs-lookup"><span data-stu-id="a7453-128">The following configuration example shows the default protocol mapping in the machine.config file.</span></span> <span data-ttu-id="a7453-129">Você pode substituir esse mapeamento padrão no nível do computador, modificando o arquivo Machine. config.</span><span class="sxs-lookup"><span data-stu-id="a7453-129">You can override this default mapping at the machine level by modifying the machine.config file.</span></span> <span data-ttu-id="a7453-130">Ou, se você quiser apenas substituí-la dentro do escopo de um aplicativo, você pode substituir essa seção dentro de seu arquivo de configuração de aplicativo e alterar o mapeamento para esquemas de protocolo individual.</span><span class="sxs-lookup"><span data-stu-id="a7453-130">Or if you would only like to override it within the scope of an application, you can override this section within your application configuration file and change the mapping for individual protocol schemes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a7453-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a7453-131">See also</span></span>

- <xref:System.ServiceModel.Configuration.ProtocolMappingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Configuration.ProtocolMappingElement?displayProperty=nameWithType>
