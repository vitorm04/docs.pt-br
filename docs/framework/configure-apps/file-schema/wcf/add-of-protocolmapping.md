---
title: <add> de <protocolMapping>
ms.date: 03/30/2017
ms.assetid: 08e62249-1641-41d1-91b1-66d7b46244e4
ms.openlocfilehash: 46ba21b65f524f88bfce81739f0cd73040a2ad45
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91205003"
---
# <a name="add-of-protocolmapping"></a><span data-ttu-id="7a62e-102">\<add> de \<protocolMapping></span><span class="sxs-lookup"><span data-stu-id="7a62e-102">\<add> of \<protocolMapping></span></span>

<span data-ttu-id="7a62e-103">Representa um mapeamento de protocolo padrão entre um esquema de protocolo de transporte (por exemplo, http, net. TCP, net. pipe, etc.) e uma associação de Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="7a62e-103">Represents a default protocol mapping between a transport protocol scheme (e.g., http, net.tcp, net.pipe, etc.) and a Windows Communication Foundation (WCF) binding.</span></span> <span data-ttu-id="7a62e-104">Ao criar pontos de extremidade padrão em tempo de execução, o WCF examina os mapeamentos configurados e decide qual associação usar para um endereço baseado em particular.</span><span class="sxs-lookup"><span data-stu-id="7a62e-104">When creating default endpoints at runtime, WCF looks at the configured mappings and decides on which binding to use for a particular based address.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<protocolMapping>**](protocolmapping.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="7a62e-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7a62e-105">Syntax</span></span>  
  
```xml  
<protocolMapping>
  <add binding="String"
       bindingConfiguration="String"
       scheme="http/net.msmq/net.pipe/net.tcp" />
</protocolMapping>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7a62e-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="7a62e-106">Attributes and Elements</span></span>  

 <span data-ttu-id="7a62e-107">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="7a62e-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7a62e-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="7a62e-108">Attributes</span></span>  
  
|<span data-ttu-id="7a62e-109">Elemento</span><span class="sxs-lookup"><span data-stu-id="7a62e-109">Element</span></span>|<span data-ttu-id="7a62e-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="7a62e-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7a62e-111">associação</span><span class="sxs-lookup"><span data-stu-id="7a62e-111">binding</span></span>|<span data-ttu-id="7a62e-112">Uma cadeia de caracteres que especifica o tipo de associação a ser usada para um ponto de extremidade durante a criação do ponto de extremidade padrão.</span><span class="sxs-lookup"><span data-stu-id="7a62e-112">A string that specifies the type of binding to be used for an endpoint during default endpoint creation.</span></span>|  
|<span data-ttu-id="7a62e-113">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="7a62e-113">bindingConfiguration</span></span>|<span data-ttu-id="7a62e-114">Uma cadeia de caracteres que especifica o nome da seção de configuração de associação a ser referenciada.</span><span class="sxs-lookup"><span data-stu-id="7a62e-114">A string that specifies the name of the binding configuration section to be referenced.</span></span>|  
|<span data-ttu-id="7a62e-115">scheme</span><span class="sxs-lookup"><span data-stu-id="7a62e-115">scheme</span></span>|<span data-ttu-id="7a62e-116">O esquema do protocolo de transporte a ser usado para o ponto de extremidade padrão.</span><span class="sxs-lookup"><span data-stu-id="7a62e-116">The transport protocol scheme to be used for the default endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7a62e-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="7a62e-117">Child Elements</span></span>  

 <span data-ttu-id="7a62e-118">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="7a62e-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7a62e-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="7a62e-119">Parent Elements</span></span>  
  
|<span data-ttu-id="7a62e-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="7a62e-120">Element</span></span>|<span data-ttu-id="7a62e-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="7a62e-121">Description</span></span>|  
|-------------|-----------------|  
|[\<protocolMapping>](protocolmapping.md)|<span data-ttu-id="7a62e-122">Representa uma seção de configuração para definir mapeamentos de protocolo padrão entre esquemas de protocolo de transporte (por exemplo, http, net. TCP, net. pipe, etc.) e associações de Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="7a62e-122">Represents a configuration section for defining default protocol mappings between transport protocol schemes (e.g., http, net.tcp, net.pipe, etc.) and Windows Communication Foundation (WCF) bindings.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="7a62e-123">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7a62e-123">Example</span></span>  

 <span data-ttu-id="7a62e-124">O exemplo de configuração a seguir mostra o mapeamento de protocolo padrão no arquivo de machine.config.</span><span class="sxs-lookup"><span data-stu-id="7a62e-124">The following configuration example shows the default protocol mapping in the machine.config file.</span></span> <span data-ttu-id="7a62e-125">Você pode substituir esse mapeamento padrão no nível do computador modificando o arquivo de machine.config.</span><span class="sxs-lookup"><span data-stu-id="7a62e-125">You can override this default mapping at the machine level by modifying the machine.config file.</span></span> <span data-ttu-id="7a62e-126">Ou, se você quiser apenas substituí-lo no escopo de um aplicativo, poderá substituir esta seção no arquivo de configuração do aplicativo e alterar o mapeamento para esquemas de protocolo individuais.</span><span class="sxs-lookup"><span data-stu-id="7a62e-126">Or if you would only like to override it within the scope of an application, you can override this section within your application configuration file and change the mapping for individual protocol schemes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7a62e-127">Confira também</span><span class="sxs-lookup"><span data-stu-id="7a62e-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.ProtocolMappingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Configuration.ProtocolMappingElement?displayProperty=nameWithType>
