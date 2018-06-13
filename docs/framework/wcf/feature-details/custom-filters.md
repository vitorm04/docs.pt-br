---
title: Filtros personalizados
ms.date: 03/30/2017
ms.assetid: 97cf247d-be0a-4057-bba9-3be5c45029d5
ms.openlocfilehash: 4140a944ed195e1defc1a0677d8e26ff4ff85beb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33489749"
---
# <a name="custom-filters"></a><span data-ttu-id="30a96-102">Filtros personalizados</span><span class="sxs-lookup"><span data-stu-id="30a96-102">Custom Filters</span></span>
<span data-ttu-id="30a96-103">Filtros personalizados permitem que você definir a lógica de correspondência que não pode ser feita usando os filtros de mensagem fornecida pelo sistema.</span><span class="sxs-lookup"><span data-stu-id="30a96-103">Custom filters allow you to define matching logic that cannot be accomplished using the system-provided message filters.</span></span> <span data-ttu-id="30a96-104">Por exemplo, você pode criar um filtro personalizado que realiza hash de um elemento de mensagem específica e, em seguida, examina o valor para determinar se o filtro deve retornar true ou false.</span><span class="sxs-lookup"><span data-stu-id="30a96-104">For example, you might create a custom filter that hashes a particular message element and then examines the value to determine whether the filter should return true or false.</span></span>  
  
## <a name="implementation"></a><span data-ttu-id="30a96-105">Implementação</span><span class="sxs-lookup"><span data-stu-id="30a96-105">Implementation</span></span>  
 <span data-ttu-id="30a96-106">Um filtro personalizado é uma implementação de <xref:System.ServiceModel.Dispatcher.MessageFilter> classe base abstrata.</span><span class="sxs-lookup"><span data-stu-id="30a96-106">A custom filter is an implementation of the <xref:System.ServiceModel.Dispatcher.MessageFilter> abstract base class.</span></span> <span data-ttu-id="30a96-107">Ao implementar seu filtro personalizado, o construtor opcionalmente pode aceitar um parâmetro de cadeia de caracteres único.</span><span class="sxs-lookup"><span data-stu-id="30a96-107">When implementing your custom filter, the constructor can optionally accept a single string parameter.</span></span> <span data-ttu-id="30a96-108">Este parâmetro contém as informações de configuração que são transmitidas ao construtor MessageFilter para fornecer qualquer configuração que precisa de filtro em tempo de execução para executar ou valores corresponde.</span><span class="sxs-lookup"><span data-stu-id="30a96-108">This parameter contains the configuration information that is passed to the MessageFilter constructor in order to provide any values or configuration that the filter needs at runtime in order to perform matches.</span></span> <span data-ttu-id="30a96-109">Por exemplo, isso pode ser usado para fornecer um valor que o filtro procura dentro da mensagem que está sendo avaliada.</span><span class="sxs-lookup"><span data-stu-id="30a96-109">For example, this might be used to provide a value that the filter looks for within the message being evaluated.</span></span> <span data-ttu-id="30a96-110">O exemplo a seguir demonstra uma implementação básica de um filtro de mensagem personalizada que aceita um parâmetro de cadeia de caracteres:</span><span class="sxs-lookup"><span data-stu-id="30a96-110">The following example demonstrates a basic implementation of a custom message filter that accepts a string parameter:</span></span>  
  
```csharp  
public class MyMessageFilter: MessageFilter  
{  
    string filterData;  
    public MyMessageFilter(string filterData)  
    {  
        if(string.IsNullOrEmpty(filterData)  
            throw new ArgumentNullException("filterData");  
        this.filterData=filterData;  
    }  
    public override bool Match(System.ServiceModel.Channels.Message message)  
    {  
        ...  
        return retValue;  
    }  
    public override bool Match(System.ServiceModel.Channels.MessageBuffer buffer)  
    {  
        ...  
        return retValue;  
    }  
}  
```  
  
> [!NOTE]
>  <span data-ttu-id="30a96-111">Em uma implementação real, o método de correspondência contém a lógica que examinará a mensagem para determinar se o filtro de mensagens deve retornar **true** ou **false**.</span><span class="sxs-lookup"><span data-stu-id="30a96-111">In an actual implementation, the Match method(s) contains logic that will examine the message to determine if this message filter should return **true** or **false**.</span></span>  
  
### <a name="performance"></a><span data-ttu-id="30a96-112">Desempenho</span><span class="sxs-lookup"><span data-stu-id="30a96-112">Performance</span></span>  
 <span data-ttu-id="30a96-113">Ao implementar um filtro personalizado, é importante levar em consideração o comprimento máximo de tempo necessário para o filtro concluir a avaliação de uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="30a96-113">When implementing a custom filter, it is important to take into consideration the maximum length of time required for the filter to complete the evaluation of a message.</span></span> <span data-ttu-id="30a96-114">Como uma mensagem pode ser avaliada em vários filtros antes de uma correspondência for encontrada, é importante garantir que a solicitação do cliente não expira antes que todos os filtros podem ser avaliados.</span><span class="sxs-lookup"><span data-stu-id="30a96-114">Since a message may be evaluated against multiple filters before a match is found, it is important to ensure that the client request does not time out before all filters can be evaluated.</span></span> <span data-ttu-id="30a96-115">Portanto, um filtro personalizado deve conter apenas o código necessário para avaliar o conteúdo ou os atributos de uma mensagem para determinar se ele corresponde aos critérios de filtro.</span><span class="sxs-lookup"><span data-stu-id="30a96-115">Therefore a custom filter should contain only the code necessary to evaluate the contents or attributes of a message in order to determine if it matches the filter criteria.</span></span>  
  
 <span data-ttu-id="30a96-116">Em geral, você deve evitar o seguinte ao implementar um filtro personalizado:</span><span class="sxs-lookup"><span data-stu-id="30a96-116">In general, you should avoid the following when implementing a custom filter:</span></span>  
  
-   <span data-ttu-id="30a96-117">E/s, como salvar dados em disco ou um banco de dados.</span><span class="sxs-lookup"><span data-stu-id="30a96-117">IO, such as saving data to disk or to a database.</span></span>  
  
-   <span data-ttu-id="30a96-118">Desnecessária de processamento, como um loop através de vários registros em um documento.</span><span class="sxs-lookup"><span data-stu-id="30a96-118">Unnecessary processing, such as looping over multiple records in a document.</span></span>  
  
-   <span data-ttu-id="30a96-119">Bloqueio de operações, como chamadas que envolvam obter um bloqueio em recursos compartilhados ou executar pesquisas em relação a um banco de dados.</span><span class="sxs-lookup"><span data-stu-id="30a96-119">Blocking operations, such as calls that involve obtaining a lock on shared resources or performing lookups against a database.</span></span>  
  
 <span data-ttu-id="30a96-120">Antes de usar um filtro personalizado em um ambiente de produção, você deve executar testes de desempenho para determinar a duração média de tempo que leva o filtro para avaliar uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="30a96-120">Before using a custom filter in a production environment, you should run performance tests to determine the average length of time that the filter takes to evaluate a message.</span></span> <span data-ttu-id="30a96-121">Quando combinado com o tempo médio de processamento dos filtros usados na tabela de filtros, isso permitirá que você precisa determinar o valor de tempo limite máximo deve ser especificado pelo aplicativo cliente.</span><span class="sxs-lookup"><span data-stu-id="30a96-121">When combined with the average processing time of the other filters used in the filter table, this will allow you to accurately determine the maximum timeout value that should be specified by the client application.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="30a96-122">Uso</span><span class="sxs-lookup"><span data-stu-id="30a96-122">Usage</span></span>  
 <span data-ttu-id="30a96-123">Para usar o filtro personalizado com o serviço de roteamento, adicione-a tabela de filtros, especificando uma nova entrada de filtro do tipo "Custom", o nome de tipo totalmente qualificado do filtro de mensagem e o nome do seu assembly.</span><span class="sxs-lookup"><span data-stu-id="30a96-123">In order to use your custom filter with the Routing Service, you must add it to the filter table by specifying a new filter entry of type "Custom," the fully qualified type name of the message filter, and the name of your assembly.</span></span>  <span data-ttu-id="30a96-124">Assim como acontece com outros MessageFilters, você pode especificar o filterData de cadeia de caracteres que será passada para o construtor do seu filtro personalizado.</span><span class="sxs-lookup"><span data-stu-id="30a96-124">As with other MessageFilters, you can specify the string filterData that will be passed to your custom filter’s constructor.</span></span>  
  
 <span data-ttu-id="30a96-125">Os exemplos a seguir demonstram o uso de um filtro personalizado com o serviço de roteamento:</span><span class="sxs-lookup"><span data-stu-id="30a96-125">The following examples demonstrate using a custom filter with the Routing Service:</span></span>  
  
```xml  
<!--ROUTING SECTION -->  
<routing>  
  <filters>  
    <filter name="CustomFilter1" filterType="Custom"   
            customType="CustomAssembly.MyMessageFilter,   
            CustomAssembly" filterData="custom data" />  
  </filters>  
  <filterTables>  
    <table name="routingTable1">  
      <filters>  
        <add filterName="CustomFilter1" endpointName="CalculatorService" />  
      </filters>  
    </table>  
  </filterTables>  
</routing>  
```  
  
```csharp  
RoutingConfiguration rc = new RoutingConfiguration();  
List<ServiceEndpoint> endpointList = new List<ServiceEndpoint>();  
endpointList.Add(client);  
rc.FilterTable.Add(new MyMessageFilter("CustomData"), endpointList);  
```
