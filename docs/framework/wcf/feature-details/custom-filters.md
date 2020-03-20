---
title: Filtros personalizados
ms.date: 03/30/2017
ms.assetid: 97cf247d-be0a-4057-bba9-3be5c45029d5
ms.openlocfilehash: ae020173544372c3ce097c8ac57e53f3fde37514
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185206"
---
# <a name="custom-filters"></a><span data-ttu-id="20002-102">Filtros personalizados</span><span class="sxs-lookup"><span data-stu-id="20002-102">Custom Filters</span></span>
<span data-ttu-id="20002-103">Os filtros personalizados permitem definir a lógica de correspondência que não pode ser realizada usando os filtros de mensagem fornecidos pelo sistema.</span><span class="sxs-lookup"><span data-stu-id="20002-103">Custom filters allow you to define matching logic that cannot be accomplished using the system-provided message filters.</span></span> <span data-ttu-id="20002-104">Por exemplo, você pode criar um filtro personalizado que hashes um elemento de mensagem específico e, em seguida, examina o valor para determinar se o filtro deve retornar verdadeiro ou falso.</span><span class="sxs-lookup"><span data-stu-id="20002-104">For example, you might create a custom filter that hashes a particular message element and then examines the value to determine whether the filter should return true or false.</span></span>  
  
## <a name="implementation"></a><span data-ttu-id="20002-105">Implementação</span><span class="sxs-lookup"><span data-stu-id="20002-105">Implementation</span></span>  
 <span data-ttu-id="20002-106">Um filtro personalizado é <xref:System.ServiceModel.Dispatcher.MessageFilter> uma implementação da classe base abstrata.</span><span class="sxs-lookup"><span data-stu-id="20002-106">A custom filter is an implementation of the <xref:System.ServiceModel.Dispatcher.MessageFilter> abstract base class.</span></span> <span data-ttu-id="20002-107">Ao implementar seu filtro personalizado, o construtor pode, opcionalmente, aceitar um único parâmetro de seqüência.</span><span class="sxs-lookup"><span data-stu-id="20002-107">When implementing your custom filter, the constructor can optionally accept a single string parameter.</span></span> <span data-ttu-id="20002-108">Este parâmetro contém as informações de configuração que são passadas ao construtor MessageFilter para fornecer quaisquer valores ou configuração que o filtro precise em tempo de execução para executar correspondências.</span><span class="sxs-lookup"><span data-stu-id="20002-108">This parameter contains the configuration information that is passed to the MessageFilter constructor in order to provide any values or configuration that the filter needs at runtime in order to perform matches.</span></span> <span data-ttu-id="20002-109">Por exemplo, isso pode ser usado para fornecer um valor que o filtro procura dentro da mensagem que está sendo avaliada.</span><span class="sxs-lookup"><span data-stu-id="20002-109">For example, this might be used to provide a value that the filter looks for within the message being evaluated.</span></span> <span data-ttu-id="20002-110">O exemplo a seguir demonstra uma implementação básica de um filtro de mensagem personalizado que aceita um parâmetro de string:</span><span class="sxs-lookup"><span data-stu-id="20002-110">The following example demonstrates a basic implementation of a custom message filter that accepts a string parameter:</span></span>  
  
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
> <span data-ttu-id="20002-111">Em uma implementação real, o método Match(s) contém lógica que examinará a mensagem para determinar se esse filtro de mensagem deve retornar **verdadeiro** ou **falso**.</span><span class="sxs-lookup"><span data-stu-id="20002-111">In an actual implementation, the Match method(s) contains logic that will examine the message to determine if this message filter should return **true** or **false**.</span></span>  
  
### <a name="performance"></a><span data-ttu-id="20002-112">Desempenho</span><span class="sxs-lookup"><span data-stu-id="20002-112">Performance</span></span>  
 <span data-ttu-id="20002-113">Ao implementar um filtro personalizado, é importante levar em consideração o tempo máximo necessário para que o filtro complete a avaliação de uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="20002-113">When implementing a custom filter, it is important to take into consideration the maximum length of time required for the filter to complete the evaluation of a message.</span></span> <span data-ttu-id="20002-114">Uma vez que uma mensagem pode ser avaliada contra vários filtros antes de uma correspondência ser encontrada, é importante garantir que a solicitação do cliente não tenha tempo até que todos os filtros possam ser avaliados.</span><span class="sxs-lookup"><span data-stu-id="20002-114">Since a message may be evaluated against multiple filters before a match is found, it is important to ensure that the client request does not time out before all filters can be evaluated.</span></span> <span data-ttu-id="20002-115">Portanto, um filtro personalizado deve conter apenas o código necessário para avaliar o conteúdo ou atributos de uma mensagem, a fim de determinar se corresponde aos critérios do filtro.</span><span class="sxs-lookup"><span data-stu-id="20002-115">Therefore a custom filter should contain only the code necessary to evaluate the contents or attributes of a message in order to determine if it matches the filter criteria.</span></span>  
  
 <span data-ttu-id="20002-116">Em geral, você deve evitar o seguinte ao implementar um filtro personalizado:</span><span class="sxs-lookup"><span data-stu-id="20002-116">In general, you should avoid the following when implementing a custom filter:</span></span>  
  
- <span data-ttu-id="20002-117">IO, como salvar dados em disco ou em um banco de dados.</span><span class="sxs-lookup"><span data-stu-id="20002-117">IO, such as saving data to disk or to a database.</span></span>  
  
- <span data-ttu-id="20002-118">Processamento desnecessário, como looping sobre vários registros em um documento.</span><span class="sxs-lookup"><span data-stu-id="20002-118">Unnecessary processing, such as looping over multiple records in a document.</span></span>  
  
- <span data-ttu-id="20002-119">Bloquear operações, como chamadas que envolvem a obtenção de um bloqueio de recursos compartilhados ou a realização de operações contra um banco de dados.</span><span class="sxs-lookup"><span data-stu-id="20002-119">Blocking operations, such as calls that involve obtaining a lock on shared resources or performing lookups against a database.</span></span>  
  
 <span data-ttu-id="20002-120">Antes de usar um filtro personalizado em um ambiente de produção, você deve executar testes de desempenho para determinar o tempo médio que o filtro leva para avaliar uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="20002-120">Before using a custom filter in a production environment, you should run performance tests to determine the average length of time that the filter takes to evaluate a message.</span></span> <span data-ttu-id="20002-121">Quando combinado com o tempo médio de processamento dos outros filtros usados na tabela de filtros, isso permitirá determinar com precisão o valor máximo de tempo limite que deve ser especificado pelo aplicativo cliente.</span><span class="sxs-lookup"><span data-stu-id="20002-121">When combined with the average processing time of the other filters used in the filter table, this will allow you to accurately determine the maximum timeout value that should be specified by the client application.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="20002-122">Uso</span><span class="sxs-lookup"><span data-stu-id="20002-122">Usage</span></span>  
 <span data-ttu-id="20002-123">Para usar seu filtro personalizado com o Serviço de Roteamento, você deve adicioná-lo à tabela do filtro especificando uma nova entrada de filtro do tipo "Personalizado", o nome de tipo totalmente qualificado do filtro de mensagem e o nome do seu conjunto.</span><span class="sxs-lookup"><span data-stu-id="20002-123">In order to use your custom filter with the Routing Service, you must add it to the filter table by specifying a new filter entry of type "Custom," the fully qualified type name of the message filter, and the name of your assembly.</span></span>  <span data-ttu-id="20002-124">Como em outros Filtros de Mensagem, você pode especificar o filtro de stringData que será passado para o construtor do seu filtro personalizado.</span><span class="sxs-lookup"><span data-stu-id="20002-124">As with other MessageFilters, you can specify the string filterData that will be passed to your custom filter’s constructor.</span></span>  
  
 <span data-ttu-id="20002-125">Os exemplos a seguir demonstram o uso de um filtro personalizado com o Serviço de Roteamento:</span><span class="sxs-lookup"><span data-stu-id="20002-125">The following examples demonstrate using a custom filter with the Routing Service:</span></span>  
  
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
