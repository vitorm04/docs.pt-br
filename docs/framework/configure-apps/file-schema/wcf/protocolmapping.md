---
title: <protocolMapping>
ms.date: 03/30/2017
ms.assetid: 5076644b-1f33-4f26-9488-87de9fcda04c
ms.openlocfilehash: 0a79aa18c74ddb8ec47f02620d16d391b4a36b68
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91162290"
---
# \<protocolMapping>

<span data-ttu-id="f161a-101">Representa uma seção de configuração para definir um conjunto de mapeamentos de protocolo padrão entre esquemas de protocolo de transporte (por exemplo, http, net. TCP, net. pipe, etc.) e associações do WCF.</span><span class="sxs-lookup"><span data-stu-id="f161a-101">Represents a configuration section for defining a set of default protocol mapping between transport protocol schemes (e.g., http, net.tcp, net.pipe, etc.) and WCF bindings.</span></span> <span data-ttu-id="f161a-102">Ao criar pontos de extremidade padrão em tempo de execução, Windows Communication Foundation (WCF) examina os mapeamentos configurados e decide qual associação usar para um endereço baseado em particular.</span><span class="sxs-lookup"><span data-stu-id="f161a-102">When creating default endpoints at runtime, Windows Communication Foundation (WCF) looks at the configured mappings and decides on which binding to use for a particular based address.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<protocolMapping>**  
  
## <a name="syntax"></a><span data-ttu-id="f161a-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="f161a-103">Syntax</span></span>  
  
```xml  
<protocolMapping>
  <add binding="String"
       bindingConfiguration="String"
       scheme="http/net.msmq/net.pipe/net.tcp" />
</protocolMapping>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f161a-104">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="f161a-104">Attributes and Elements</span></span>  

 <span data-ttu-id="f161a-105">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="f161a-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f161a-106">Atributos</span><span class="sxs-lookup"><span data-stu-id="f161a-106">Attributes</span></span>  

 <span data-ttu-id="f161a-107">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="f161a-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f161a-108">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="f161a-108">Child Elements</span></span>  
  
|<span data-ttu-id="f161a-109">Elemento</span><span class="sxs-lookup"><span data-stu-id="f161a-109">Element</span></span>|<span data-ttu-id="f161a-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="f161a-110">Description</span></span>|  
|-------------|-----------------|  
|[\<filters>](filters-of-routing.md)|<span data-ttu-id="f161a-111">Contém um mapeamento de protocolo padrão entre um esquema de protocolo de transporte (por exemplo, http, net. TCP, net. pipe, etc.) e uma associação do WCF.</span><span class="sxs-lookup"><span data-stu-id="f161a-111">Contains a default protocol mapping between a transport protocol scheme (e.g., http, net.tcp, net.pipe, etc.) and a WCF binding.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f161a-112">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="f161a-112">Parent Elements</span></span>  
  
|<span data-ttu-id="f161a-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="f161a-113">Element</span></span>|<span data-ttu-id="f161a-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="f161a-114">Description</span></span>|  
|-------------|-----------------|  
|[\<system.serviceModel>](system-servicemodel.md)|<span data-ttu-id="f161a-115">O elemento raiz de todos os elementos de configuração do WCF.</span><span class="sxs-lookup"><span data-stu-id="f161a-115">The root element of all WCF configuration elements.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="f161a-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f161a-116">Example</span></span>  

 <span data-ttu-id="f161a-117">O exemplo de configuração a seguir mostra o mapeamento de protocolo padrão no arquivo de machine.config.</span><span class="sxs-lookup"><span data-stu-id="f161a-117">The following configuration example shows the default protocol mapping in the machine.config file.</span></span> <span data-ttu-id="f161a-118">Você pode substituir esse mapeamento padrão no nível do computador modificando o arquivo de machine.config.</span><span class="sxs-lookup"><span data-stu-id="f161a-118">You can override this default mapping at the machine level by modifying the machine.config file.</span></span> <span data-ttu-id="f161a-119">Ou, se você quiser apenas substituí-lo no escopo de um aplicativo, poderá substituir esta seção no arquivo de configuração do aplicativo e alterar o mapeamento para esquemas de protocolo individuais.</span><span class="sxs-lookup"><span data-stu-id="f161a-119">Or if you would only like to override it within the scope of an application, you can override this section within your application configuration file and change the mapping for individual protocol schemes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f161a-120">Confira também</span><span class="sxs-lookup"><span data-stu-id="f161a-120">See also</span></span>

- <xref:System.ServiceModel.Configuration.ProtocolMappingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Configuration.ProtocolMappingElement?displayProperty=nameWithType>
