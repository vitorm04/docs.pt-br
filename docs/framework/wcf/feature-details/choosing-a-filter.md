---
title: Escolhendo um filtro
ms.date: 03/30/2017
ms.assetid: 67ab5af9-b9d9-4300-b3b1-41abb5a1fd10
ms.openlocfilehash: bc3bba9a2b00b35f3e0cff1786ea98cfa881f311
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43743132"
---
# <a name="choosing-a-filter"></a><span data-ttu-id="1947a-102">Escolhendo um filtro</span><span class="sxs-lookup"><span data-stu-id="1947a-102">Choosing a Filter</span></span>
<span data-ttu-id="1947a-103">Ao configurar o serviço de roteamento, é importante selecionar os filtros de mensagem correta e configurá-los para que você possa fazer as correspondências exatas nas mensagens recebidas.</span><span class="sxs-lookup"><span data-stu-id="1947a-103">When configuring the Routing Service, it is important to select correct message filters and configure them to allow you to make exact matches against the messages you receive.</span></span> <span data-ttu-id="1947a-104">Se os filtros que você seleciona são excessivamente amplas em suas correspondências ou estão configurados incorretamente, mensagens são roteadas incorretamente.</span><span class="sxs-lookup"><span data-stu-id="1947a-104">If the filters you select are overly broad in their matches or are incorrectly configured, messages are routed incorrectly.</span></span> <span data-ttu-id="1947a-105">Se os filtros são muito restritivos, você não pode ter nenhuma rota válida disponível para algumas de suas mensagens.</span><span class="sxs-lookup"><span data-stu-id="1947a-105">If the filters are too restrictive, you may not have any valid routes available for some of your messages.</span></span>  
  
## <a name="filter-types"></a><span data-ttu-id="1947a-106">Tipos de filtro</span><span class="sxs-lookup"><span data-stu-id="1947a-106">Filter Types</span></span>  
 <span data-ttu-id="1947a-107">Ao selecionar os filtros que são usados pelo serviço de roteamento, é importante que você compreenda o funcionamento de cada filtro, bem como quais informações estão disponíveis como parte das mensagens de entrada.</span><span class="sxs-lookup"><span data-stu-id="1947a-107">When selecting the filters that are used by the Routing Service, it is important that you understand how each filter works as well as what information is available as part of the incoming messages.</span></span> <span data-ttu-id="1947a-108">Por exemplo, se todas as mensagens são recebidas ao longo do mesmo ponto de extremidade, os filtros de endereço e EndpointName não são úteis porque todas as mensagens coincidam com estes filtros.</span><span class="sxs-lookup"><span data-stu-id="1947a-108">For instance, if all messages are received over the same endpoint, the Address and EndpointName filters are not useful because all messages match these filters.</span></span>  
  
### <a name="action"></a><span data-ttu-id="1947a-109">Ação</span><span class="sxs-lookup"><span data-stu-id="1947a-109">Action</span></span>  
 <span data-ttu-id="1947a-110">O filtro de ação inspeciona o <xref:System.ServiceModel.Channels.MessageHeaders.Action%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="1947a-110">The Action filter inspects the <xref:System.ServiceModel.Channels.MessageHeaders.Action%2A> property.</span></span> <span data-ttu-id="1947a-111">Se o conteúdo do cabeçalho da ação na mensagem corresponde ao valor de dados do filtro especificado na configuração do filtro e, em seguida, retorna esse filtro `true`.</span><span class="sxs-lookup"><span data-stu-id="1947a-111">If the contents of the Action header in the message match the filter data value specified in the filter configuration, then this filter returns `true`.</span></span> <span data-ttu-id="1947a-112">O exemplo a seguir define uma `FilterElement` que usa o filtro de ação para corresponder as mensagens com um cabeçalho de ação que contém um valor de "http://namespace/contract/operation/".</span><span class="sxs-lookup"><span data-stu-id="1947a-112">The following example defines a `FilterElement` that uses the Action filter to match messages with an action header that contains a value of "http://namespace/contract/operation/".</span></span>  
  
```xml  
<filter name="action1" filterType="Action" filterData="http://namespace/contract/operation/" />  
```  
  
```csharp  
ActionMessageFilter action1 = new ActionMessageFilter(new string[] { "http://namespace/contract/operation" });  
```  
  
 <span data-ttu-id="1947a-113">Esse filtro deve ser usado ao rotear mensagens que contêm um cabeçalho de ação exclusivo.</span><span class="sxs-lookup"><span data-stu-id="1947a-113">This filter should be used when routing messages that contain a unique Action header.</span></span>  
  
### <a name="endpointaddress"></a><span data-ttu-id="1947a-114">EndpointAddress</span><span class="sxs-lookup"><span data-stu-id="1947a-114">EndpointAddress</span></span>  
 <span data-ttu-id="1947a-115">O filtro EndpointAddress inspeciona o EndpointAddress que a mensagem foi recebida no.</span><span class="sxs-lookup"><span data-stu-id="1947a-115">The EndpointAddress filter inspects the EndpointAddress that the message was received on.</span></span> <span data-ttu-id="1947a-116">Se o endereço que a mensagem chega ao exatamente corresponde ao endereço de filtro especificado na configuração do filtro e, em seguida, retorna esse filtro `true`.</span><span class="sxs-lookup"><span data-stu-id="1947a-116">If the address that the message arrives at exactly matches the filter address specified in the filter configuration, then this filter returns `true`.</span></span> <span data-ttu-id="1947a-117">O exemplo a seguir define uma `FilterElement` que usa o filtro de endereço para correspondência de todas as mensagens endereçadas a "http://\<nome do host > / vdir/s.svc/b".</span><span class="sxs-lookup"><span data-stu-id="1947a-117">The following example defines a `FilterElement` that uses the Address filter to match any messages addressed to "http://\<hostname>/vdir/s.svc/b".</span></span>  
  
```xml  
<filter name="address1" filterType="EndpointAddress" filterData="http://host/vdir/s.svc/b" />  
```  
  
```csharp  
EndpointAddressMessageFilter address1 = new EndpointAddressMessageFilter(new EndpointAddress("http://host/vdir/s.svc/b"), false);  
```  
  
> [!NOTE]
>  <span data-ttu-id="1947a-118">É importante observar que a parte do nome de host de um endereço pode diferir com base em se o cliente usa o nome de domínio totalmente qualificado, o nome NetBIOS, o endereço IP ou outro nome.</span><span class="sxs-lookup"><span data-stu-id="1947a-118">It is important to note that the host name portion of an address can differ based on whether the client uses the fully qualified domain name, NetBIOS name, IP address, or other name.</span></span> <span data-ttu-id="1947a-119">Como os valores de diferentes podem referir-se para o mesmo host, o comportamento padrão para essa comparação é não usar a parte do nome de host do endereço ao executar correspondências.</span><span class="sxs-lookup"><span data-stu-id="1947a-119">Because differing values can refer to the same host, the default behavior for this comparison is to not use the host name portion of the address when performing matches.</span></span>  
>   
>  <span data-ttu-id="1947a-120">Esse comportamento pode ser modificado para permitir a comparação avaliar o nome do host ao configurar o serviço de roteamento por meio de programação.</span><span class="sxs-lookup"><span data-stu-id="1947a-120">This behavior can be modified to allow the comparison to evaluate the host name when configuring the Routing Service programmatically.</span></span>  
  
 <span data-ttu-id="1947a-121">Esse filtro deve ser usado quando as mensagens de entrada endereçadas para um endereço exclusivo.</span><span class="sxs-lookup"><span data-stu-id="1947a-121">This filter should be used when the incoming messages are addressed to a unique address.</span></span>  
  
### <a name="endpointaddressprefix"></a><span data-ttu-id="1947a-122">EndpointAddressPrefix</span><span class="sxs-lookup"><span data-stu-id="1947a-122">EndpointAddressPrefix</span></span>  
 <span data-ttu-id="1947a-123">O filtro EndpointAddressPrefix é semelhante ao filtro EndpointAddress.</span><span class="sxs-lookup"><span data-stu-id="1947a-123">The EndpointAddressPrefix filter is similar to the EndpointAddress filter.</span></span> <span data-ttu-id="1947a-124">O filtro EndpointAddressPrefix inspeciona o EndpointAddress que a mensagem foi recebida no.</span><span class="sxs-lookup"><span data-stu-id="1947a-124">The EndpointAddressPrefix filter inspects the EndpointAddress that the message was received on.</span></span> <span data-ttu-id="1947a-125">No entanto o filtro EndpointAddressPrefix atua como um caractere curinga por correspondência de endereços que começam com o valor especificado na configuração de filtro.</span><span class="sxs-lookup"><span data-stu-id="1947a-125">However the EndpointAddressPrefix filter acts as a wildcard by matching addresses that begin with the value specified in the filter configuration.</span></span> <span data-ttu-id="1947a-126">O exemplo a seguir define uma `FilterElement` que usa o filtro de EndpointAddressPrefix para corresponder a todas as mensagens endereçadas a "http://\<nome do host > / vdir \*".</span><span class="sxs-lookup"><span data-stu-id="1947a-126">The following example defines a `FilterElement` that uses the EndpointAddressPrefix filter to match any messages addressed to "http://\<hostname>/vdir\*".</span></span>  
  
```xml  
<filter name="prefix1" filterType="EndpointAddressPrefix" filterData="http://host/vdir" />  
```  
  
```csharp  
PrefixEndpointAddressMessageFilter prefix1 = new PrefixEndpointAddressMessageFilter(new EndpointAddress("http://host/vdir/s.svc/b"), false);  
```  
  
> [!NOTE]
>  <span data-ttu-id="1947a-127">É importante observar que a parte do nome de host de um endereço pode diferir com base em se o cliente usa o nome de domínio totalmente qualificado, o nome NetBIOS, o endereço IP ou outro nome.</span><span class="sxs-lookup"><span data-stu-id="1947a-127">It is important to note that the host name portion of an address can differ based on whether the client uses the fully qualified domain name, NetBIOS name, IP address, or other name.</span></span> <span data-ttu-id="1947a-128">Como os valores de diferentes podem referir-se para o mesmo host, o comportamento padrão para essa comparação é não usar a parte do nome de host do endereço ao executar correspondências.</span><span class="sxs-lookup"><span data-stu-id="1947a-128">Because differing values can refer to the same host, the default behavior for this comparison is to not use the host name portion of the address when performing matches.</span></span>  
  
 <span data-ttu-id="1947a-129">Esse filtro deve ser usado ao rotear mensagens de entrada que compartilham um prefixo de endereço comum.</span><span class="sxs-lookup"><span data-stu-id="1947a-129">This filter should be used when routing incoming messages that share a common address prefix.</span></span>  
  
### <a name="and"></a><span data-ttu-id="1947a-130">AND</span><span class="sxs-lookup"><span data-stu-id="1947a-130">AND</span></span>  
 <span data-ttu-id="1947a-131">O filtro AND não filtra diretamente em um valor dentro de uma mensagem, mas permite que você combine os dois outros filtros para criar uma `AND` condição em que ambos os filtros devem corresponder a mensagem antes que o filtro e é avaliada como `true`.</span><span class="sxs-lookup"><span data-stu-id="1947a-131">The AND filter does not directly filter on a value within a message, but allows you to combine two other filters to create an `AND` condition where both filters must match the message before the AND filter evaluates to `true`.</span></span> <span data-ttu-id="1947a-132">Isso permite que você crie filtros complexos que correspondem somente se correspondem a todos os filtros de subpropriedades.</span><span class="sxs-lookup"><span data-stu-id="1947a-132">This allows you to create complex filters that only match if all the sub-filters match.</span></span> <span data-ttu-id="1947a-133">O exemplo a seguir define um filtro de endereço e um filtro de ação e, em seguida, define um filtro e que é avaliada uma mensagem com base nos filtros de endereço e a ação.</span><span class="sxs-lookup"><span data-stu-id="1947a-133">The following example defines an address filter and an action filter, and then defines an AND filter that evaluates a message against both the address and action filters.</span></span> <span data-ttu-id="1947a-134">Se o endereço e os filtros de ação corresponderem, o filtro AND retornará `true`.</span><span class="sxs-lookup"><span data-stu-id="1947a-134">If both the address and the action filters match, then the AND filter returns `true`.</span></span>  
  
```xml  
<filter name="address1" filterType="AddressPrefix" filterData="http://host/vdir"/>  
<filter name="action1" filterType="Action" filterData="http://namespace/contract/operation/"/>  
<filter name="and1" filterType="And" filter1="address1" filter2="action1" />  
```  
  
```csharp  
EndpointAddressMessageFilter address1 = new EndpointAddressMessageFilter(new EndpointAddress("http://host/vdir/s.svc/b"), false);  
ActionMessageFilter action1 = new ActionMessageFilter(new string[] { "http://namespace/contract/operation" });  
StrictAndMessageFilter and1=new StrictAndMessageFilter(address1, action1);  
```  
  
 <span data-ttu-id="1947a-135">Esse filtro deve ser usado quando é necessário combinar a lógica de vários filtros para determinar quando uma correspondência deve ser feita.</span><span class="sxs-lookup"><span data-stu-id="1947a-135">This filter should be used when you must combine the logic from multiple filters to determine when a match should be made.</span></span> <span data-ttu-id="1947a-136">Por exemplo, se você tiver vários destinos que devem receber somente determinadas combinações de ações e mensagens para endereços específicos, você pode usar um filtro AND para combinar os filtros de ação e o endereço necessário.</span><span class="sxs-lookup"><span data-stu-id="1947a-136">For example, if you have multiple destinations that must receive only certain combinations of actions and messages to particular addresses, you can use an AND filter to combine the necessary Action and Address filters.</span></span>  
  
### <a name="custom"></a><span data-ttu-id="1947a-137">Personalizado</span><span class="sxs-lookup"><span data-stu-id="1947a-137">Custom</span></span>  
 <span data-ttu-id="1947a-138">Ao selecionar o tipo de filtro personalizado, você deve fornecer um valor de customType que contém o tipo do assembly que contém o **MessageFilter** implementação a ser usado para esse filtro.</span><span class="sxs-lookup"><span data-stu-id="1947a-138">When selecting the Custom filter type, you must provide a customType value that contains the type of the assembly that contains the **MessageFilter** implementation to be used for this filter.</span></span> <span data-ttu-id="1947a-139">Além disso, filterData deve conter todos os valores que o filtro personalizado pode exigir de sua avaliação de mensagens.</span><span class="sxs-lookup"><span data-stu-id="1947a-139">Additionally, filterData must contain any values that the custom filter may require in its evaluation of messages.</span></span> <span data-ttu-id="1947a-140">O exemplo a seguir define uma `FilterElement` que usa o `CustomAssembly.MyCustomMsgFilter` implementação de MessageFilter.</span><span class="sxs-lookup"><span data-stu-id="1947a-140">The following example defines a `FilterElement` that uses the `CustomAssembly.MyCustomMsgFilter` MessageFilter implementation.</span></span>  
  
```xml  
<filter name="custom1" filterType="Custom" customType="CustomAssembly.MyCustomMsgFilter, CustomAssembly" filterData="Custom Data" />  
```  
  
```csharp  
MyCustomMsgFilter custom1=new MyCustomMsgFilter("Custom Data");  
```  
  
 <span data-ttu-id="1947a-141">Se você precisa executar lógica correspondente personalizada em relação a uma mensagem que não é coberta pelos filtros fornecidos com [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)], você deve criar um filtro personalizado que é uma implementação do **MessageFilter** classe.</span><span class="sxs-lookup"><span data-stu-id="1947a-141">If you need to perform custom matching logic against a message that is not covered by the filters provided with [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)], you must create a custom filter that is an implementation of the **MessageFilter** class.</span></span> <span data-ttu-id="1947a-142">Por exemplo, você pode criar um filtro personalizado, que compara um campo na mensagem de entrada em relação a uma lista de valores conhecidos fornecido para o filtro como configuração, ou que faz o hash de um elemento de mensagem específica e, em seguida, examina esse valor para determinar se o filtro deve retornar `true` ou `false`.</span><span class="sxs-lookup"><span data-stu-id="1947a-142">For example, you might create a custom filter that compares a field in the incoming message against a list of known values given to the filter as configuration, or that hashes a particular message element and then examines that value to determine whether the filter should return `true` or `false`.</span></span>  
  
### <a name="endpointname"></a><span data-ttu-id="1947a-143">EndpointName</span><span class="sxs-lookup"><span data-stu-id="1947a-143">EndpointName</span></span>  
 <span data-ttu-id="1947a-144">O filtro EndpointName inspeciona o nome do ponto de extremidade que recebeu a mensagem.</span><span class="sxs-lookup"><span data-stu-id="1947a-144">The EndpointName filter inspects the name of the endpoint that received the message.</span></span> <span data-ttu-id="1947a-145">O exemplo a seguir define uma `FilterElement` que usa o filtro de EndpointName para rotear mensagens recebidas em "SvcEndpoint".</span><span class="sxs-lookup"><span data-stu-id="1947a-145">The following example defines a `FilterElement` that uses the EndpointName filter to route messages received on the "SvcEndpoint".</span></span>  
  
```xml  
<filter name="name1" filterType="Endpoint" filterData="SvcEndpoint" />  
```  
  
```csharp  
EndpointNameMessageFilter name1 = new EndpointNameMessageFilter("SvcEndpoint");  
```  
  
 <span data-ttu-id="1947a-146">Esse filtro é útil quando o serviço de roteamento expõe mais de um ponto de extremidade de serviço nomeado.</span><span class="sxs-lookup"><span data-stu-id="1947a-146">This filter is useful when the Routing Service exposes more than one named service endpoint.</span></span> <span data-ttu-id="1947a-147">Por exemplo, você pode expor os dois pontos de extremidade usados pelo serviço de roteamento para receber mensagens. um é usado por clientes de prioridade que exigem processamento de suas mensagens, enquanto outro ponto de extremidade em tempo real recebe mensagens que não são tempo minúsculas.</span><span class="sxs-lookup"><span data-stu-id="1947a-147">For example, you might expose two endpoints that the Routing Service uses to receive messages; one is used by priority customers who require real-time processing of their messages, while the other endpoint receives messages that are not time sensitive.</span></span>  
  
 <span data-ttu-id="1947a-148">Embora muitas vezes você pode usar completo endereço de correspondência para determinar qual ponto de extremidade foi recebida uma mensagem, usando o nome do ponto de extremidade definido em vez disso, é um atalho conveniente que geralmente é menos sujeita a erros, especialmente ao configurar um serviço de roteamento usando uma configuração arquivo (em que os nomes de ponto de extremidade são um atributo necessário).</span><span class="sxs-lookup"><span data-stu-id="1947a-148">While you can often use full address matching to determine which endpoint a message was received on, using the defined endpoint name instead is a convenient shortcut that is often less error prone, especially when configuring a Routing Service using a configuration file (where endpoint names are a required attribute).</span></span>  
  
### <a name="matchall"></a><span data-ttu-id="1947a-149">MatchAll</span><span class="sxs-lookup"><span data-stu-id="1947a-149">MatchAll</span></span>  
 <span data-ttu-id="1947a-150">O filtro de MatchAll corresponde a qualquer mensagem recebida.</span><span class="sxs-lookup"><span data-stu-id="1947a-150">The MatchAll filter matches any received message.</span></span> <span data-ttu-id="1947a-151">É útil se você sempre deve rotear todas as mensagens recebidas para um ponto de extremidade específico, como um serviço de registro em log que armazena uma cópia de todas as mensagens recebidas.</span><span class="sxs-lookup"><span data-stu-id="1947a-151">It is useful if you must always route all received messages to a specific endpoint, such as a logging service that stores a copy of all received messages.</span></span> <span data-ttu-id="1947a-152">O exemplo a seguir define uma `FilterElement` que usa o filtro de MatchAll.</span><span class="sxs-lookup"><span data-stu-id="1947a-152">The following example defines a `FilterElement` that uses the MatchAll filter.</span></span>  
  
```xml  
<filter name="matchAll1" filterType="MatchAll" />  
```  
  
```csharp  
MatchAllMessageFilter matchAll1 = new MatchAllMessageFilter();  
```  
  
### <a name="xpath"></a><span data-ttu-id="1947a-153">XPath</span><span class="sxs-lookup"><span data-stu-id="1947a-153">XPath</span></span>  
 <span data-ttu-id="1947a-154">O filtro XPath permite que você especifique uma consulta XPath que é usada para inspecionar um elemento específico dentro da mensagem.</span><span class="sxs-lookup"><span data-stu-id="1947a-154">The XPath filter allows you to specify an XPath query that is used to inspect a specific element within the message.</span></span> <span data-ttu-id="1947a-155">A filtragem de XPath é uma opção de filtragem poderosa que permite que você inspecione diretamente qualquer entrada endereçável de XML dentro da mensagem; No entanto, ele exige que você tenha conhecimento específico da estrutura das mensagens que você está recebendo.</span><span class="sxs-lookup"><span data-stu-id="1947a-155">XPath filtering is a powerful filtering option that allows you to directly inspect any XML addressable entry within the message; however it requires that you have specific knowledge of the structure of the messages that you are receiving.</span></span> <span data-ttu-id="1947a-156">O exemplo a seguir define uma `FilterElement` que usa o filtro XPath para inspecionar a mensagem para um elemento denominado "element" dentro do namespace referenciado pelo prefixo de namespace "ns".</span><span class="sxs-lookup"><span data-stu-id="1947a-156">The following example defines a `FilterElement` that uses the XPath filter to inspect the message for an element named "element" within the namespace referenced by the "ns" namespace prefix.</span></span>  
  
```xml  
<filter name="xpath1" filterType="XPath" filterData="//ns:element" />  
```  
  
```csharp  
XPathMessageFilter xpath1=new XPathMessageFilter("//ns:element");  
```  
  
 <span data-ttu-id="1947a-157">Esse filtro é útil se você souber que as mensagens que você está recebendo contêm um valor específico.</span><span class="sxs-lookup"><span data-stu-id="1947a-157">This filter is useful if you know that the messages you are receiving contain a specific value.</span></span> <span data-ttu-id="1947a-158">Por exemplo, se você estiver hospedando as duas versões do mesmo serviço e você souber que as mensagens endereçadas para a versão mais recente do serviço contenham um valor exclusivo em um cabeçalho personalizado, você pode criar um filtro que usa o XPath para navegar para esse cabeçalho e compara a valor de pré-instalação ENT no cabeçalho para outro fornecido na configuração de filtro para determinar se o filtro corresponde.</span><span class="sxs-lookup"><span data-stu-id="1947a-158">For example, if you are hosting two versions of the same service and you know that messages addressed to the newer version of the service contain a unique value in a custom header, you can create a filter that uses XPath to navigate to this header and compares the value present in the header to another given in the filter configuration to determine if the filter matches.</span></span>  
  
 <span data-ttu-id="1947a-159">Como as consultas XPath geralmente contêm namespaces exclusivos, que geralmente são longos ou valores de cadeia de caracteres complexa, o filtro XPath permite que você use a tabela de namespace para definir os prefixos exclusivos para seus namespaces.</span><span class="sxs-lookup"><span data-stu-id="1947a-159">Because XPath queries often contain unique namespaces, which are often lengthy or complex string values, the XPath filter allows you to use the namespace table to define unique prefixes for your namespaces.</span></span> <span data-ttu-id="1947a-160">Para obter mais informações sobre a tabela de namespace, consulte [filtros de mensagem](../../../../docs/framework/wcf/feature-details/message-filters.md).</span><span class="sxs-lookup"><span data-stu-id="1947a-160">For more information about the namespace table, see [Message Filters](../../../../docs/framework/wcf/feature-details/message-filters.md).</span></span>  
  
 <span data-ttu-id="1947a-161">Para obter mais informações sobre a criação de consultas XPath, consulte [sintaxe XPath](https://go.microsoft.com/fwlink/?LinkId=164592).</span><span class="sxs-lookup"><span data-stu-id="1947a-161">For more information about designing XPath queries, see [XPath Syntax](https://go.microsoft.com/fwlink/?LinkId=164592).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1947a-162">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1947a-162">See Also</span></span>  
 [<span data-ttu-id="1947a-163">Filtros de mensagem</span><span class="sxs-lookup"><span data-stu-id="1947a-163">Message Filters</span></span>](../../../../docs/framework/wcf/feature-details/message-filters.md)  
 [<span data-ttu-id="1947a-164">Como usar filtros</span><span class="sxs-lookup"><span data-stu-id="1947a-164">How To: Use Filters</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-filters.md)
