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
# <a name="custom-filters"></a>Filtros personalizados
Os filtros personalizados permitem definir a lógica de correspondência que não pode ser realizada usando os filtros de mensagem fornecidos pelo sistema. Por exemplo, você pode criar um filtro personalizado que hashes um elemento de mensagem específico e, em seguida, examina o valor para determinar se o filtro deve retornar verdadeiro ou falso.  
  
## <a name="implementation"></a>Implementação  
 Um filtro personalizado é <xref:System.ServiceModel.Dispatcher.MessageFilter> uma implementação da classe base abstrata. Ao implementar seu filtro personalizado, o construtor pode, opcionalmente, aceitar um único parâmetro de seqüência. Este parâmetro contém as informações de configuração que são passadas ao construtor MessageFilter para fornecer quaisquer valores ou configuração que o filtro precise em tempo de execução para executar correspondências. Por exemplo, isso pode ser usado para fornecer um valor que o filtro procura dentro da mensagem que está sendo avaliada. O exemplo a seguir demonstra uma implementação básica de um filtro de mensagem personalizado que aceita um parâmetro de string:  
  
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
> Em uma implementação real, o método Match(s) contém lógica que examinará a mensagem para determinar se esse filtro de mensagem deve retornar **verdadeiro** ou **falso**.  
  
### <a name="performance"></a>Desempenho  
 Ao implementar um filtro personalizado, é importante levar em consideração o tempo máximo necessário para que o filtro complete a avaliação de uma mensagem. Uma vez que uma mensagem pode ser avaliada contra vários filtros antes de uma correspondência ser encontrada, é importante garantir que a solicitação do cliente não tenha tempo até que todos os filtros possam ser avaliados. Portanto, um filtro personalizado deve conter apenas o código necessário para avaliar o conteúdo ou atributos de uma mensagem, a fim de determinar se corresponde aos critérios do filtro.  
  
 Em geral, você deve evitar o seguinte ao implementar um filtro personalizado:  
  
- IO, como salvar dados em disco ou em um banco de dados.  
  
- Processamento desnecessário, como looping sobre vários registros em um documento.  
  
- Bloquear operações, como chamadas que envolvem a obtenção de um bloqueio de recursos compartilhados ou a realização de operações contra um banco de dados.  
  
 Antes de usar um filtro personalizado em um ambiente de produção, você deve executar testes de desempenho para determinar o tempo médio que o filtro leva para avaliar uma mensagem. Quando combinado com o tempo médio de processamento dos outros filtros usados na tabela de filtros, isso permitirá determinar com precisão o valor máximo de tempo limite que deve ser especificado pelo aplicativo cliente.  
  
## <a name="usage"></a>Uso  
 Para usar seu filtro personalizado com o Serviço de Roteamento, você deve adicioná-lo à tabela do filtro especificando uma nova entrada de filtro do tipo "Personalizado", o nome de tipo totalmente qualificado do filtro de mensagem e o nome do seu conjunto.  Como em outros Filtros de Mensagem, você pode especificar o filtro de stringData que será passado para o construtor do seu filtro personalizado.  
  
 Os exemplos a seguir demonstram o uso de um filtro personalizado com o Serviço de Roteamento:  
  
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
