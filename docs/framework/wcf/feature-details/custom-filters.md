---
title: Filtros personalizados
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 97cf247d-be0a-4057-bba9-3be5c45029d5
caps.latest.revision: "5"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: c9d0c81d715b2e876fe8144d4cff198f3321a22e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="custom-filters"></a>Filtros personalizados
Filtros personalizados permitem que você definir a lógica de correspondência que não pode ser feita usando os filtros de mensagem fornecida pelo sistema. Por exemplo, você pode criar um filtro personalizado que realiza hash de um elemento de mensagem específica e, em seguida, examina o valor para determinar se o filtro deve retornar true ou false.  
  
## <a name="implementation"></a>Implementação  
 Um filtro personalizado é uma implementação de <xref:System.ServiceModel.Dispatcher.MessageFilter> classe base abstrata. Ao implementar seu filtro personalizado, o construtor opcionalmente pode aceitar um parâmetro de cadeia de caracteres único. Este parâmetro contém as informações de configuração que são transmitidas ao construtor MessageFilter para fornecer qualquer configuração que precisa de filtro em tempo de execução para executar ou valores corresponde. Por exemplo, isso pode ser usado para fornecer um valor que o filtro procura dentro da mensagem que está sendo avaliada. O exemplo a seguir demonstra uma implementação básica de um filtro de mensagem personalizada que aceita um parâmetro de cadeia de caracteres:  
  
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
>  Em uma implementação real, o método de correspondência contém a lógica que examinará a mensagem para determinar se o filtro de mensagens deve retornar **true** ou **false**.  
  
### <a name="performance"></a>Desempenho  
 Ao implementar um filtro personalizado, é importante levar em consideração o comprimento máximo de tempo necessário para o filtro concluir a avaliação de uma mensagem. Como uma mensagem pode ser avaliada em vários filtros antes de uma correspondência for encontrada, é importante garantir que a solicitação do cliente não expira antes que todos os filtros podem ser avaliados. Portanto, um filtro personalizado deve conter apenas o código necessário para avaliar o conteúdo ou os atributos de uma mensagem para determinar se ele corresponde aos critérios de filtro.  
  
 Em geral, você deve evitar o seguinte ao implementar um filtro personalizado:  
  
-   E/s, como salvar dados em disco ou um banco de dados.  
  
-   Desnecessária de processamento, como um loop através de vários registros em um documento.  
  
-   Bloqueio de operações, como chamadas que envolvam obter um bloqueio em recursos compartilhados ou executar pesquisas em relação a um banco de dados.  
  
 Antes de usar um filtro personalizado em um ambiente de produção, você deve executar testes de desempenho para determinar a duração média de tempo que leva o filtro para avaliar uma mensagem. Quando combinado com o tempo médio de processamento dos filtros usados na tabela de filtros, isso permitirá que você precisa determinar o valor de tempo limite máximo deve ser especificado pelo aplicativo cliente.  
  
## <a name="usage"></a>Uso  
 Para usar o filtro personalizado com o serviço de roteamento, adicione-a tabela de filtros, especificando uma nova entrada de filtro do tipo "Custom", o nome de tipo totalmente qualificado do filtro de mensagem e o nome do seu assembly.  Assim como acontece com outros MessageFilters, você pode especificar o filterData de cadeia de caracteres que será passada para o construtor do seu filtro personalizado.  
  
 Os exemplos a seguir demonstram o uso de um filtro personalizado com o serviço de roteamento:  
  
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
