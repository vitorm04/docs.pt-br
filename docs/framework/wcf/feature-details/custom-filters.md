---
title: Filtros personalizados
ms.date: 03/30/2017
ms.assetid: 97cf247d-be0a-4057-bba9-3be5c45029d5
ms.openlocfilehash: 4140a944ed195e1defc1a0677d8e26ff4ff85beb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61857214"
---
# <a name="custom-filters"></a>Filtros personalizados
Filtros personalizados permitem que você defina a lógica de correspondência que não pode ser realizada usando os filtros de mensagem fornecida pelo sistema. Por exemplo, você pode criar um filtro personalizado que faz o hash de um elemento de mensagem específica e, em seguida, examina o valor para determinar se o filtro deve retornar true ou false.  
  
## <a name="implementation"></a>Implementação  
 Um filtro personalizado é uma implementação do <xref:System.ServiceModel.Dispatcher.MessageFilter> classe base abstrata. Ao implementar seu filtro personalizado, o construtor, opcionalmente, pode aceitar um parâmetro de cadeia de caracteres único. Este parâmetro contém as informações de configuração que são passadas para o construtor de MessageFilter para fornecer corresponde a todos os valores ou configuração que o filtro precisa em tempo de execução para realizar. Por exemplo, isso pode ser usado para fornecer um valor que o filtro procura dentro da mensagem que está sendo avaliada. O exemplo a seguir demonstra uma implementação básica de um filtro de mensagem personalizado que aceita um parâmetro de cadeia de caracteres:  
  
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
>  Em uma implementação real, os métodos de correspondência contém a lógica que examinará a mensagem para determinar se o filtro de mensagens deve retornar **verdadeira** ou **falso**.  
  
### <a name="performance"></a>Desempenho  
 Ao implementar um filtro personalizado, é importante levar em consideração o comprimento máximo de tempo necessário para o filtro concluir a avaliação de uma mensagem. Uma vez que uma mensagem pode ser avaliada em relação a vários filtros antes que uma correspondência for encontrada, é importante garantir que a solicitação do cliente não expira antes que todos os filtros podem ser avaliados. Portanto, um filtro personalizado deve conter somente o código necessário para avaliar o conteúdo ou atributos de uma mensagem para determinar se ele corresponde aos critérios de filtro.  
  
 Em geral, você deve evitar o seguinte ao implementar um filtro personalizado:  
  
-   E/s, como salvar dados em disco ou um banco de dados.  
  
-   Desnecessária de processamento, como looping através de vários registros em um documento.  
  
-   Operações de bloqueio, como chamadas que envolvem a obtenção de um bloqueio em recursos compartilhados ou realização de pesquisas em relação a um banco de dados.  
  
 Antes de usar um filtro personalizado em um ambiente de produção, você deve executar testes de desempenho para determinar a duração média de tempo que o filtro usa para avaliar uma mensagem. Quando combinado com o tempo médio de processamento dos filtros usados na tabela de filtros, isso permitirá que você determine com precisão o valor de tempo limite máximo deve ser especificado pelo aplicativo cliente.  
  
## <a name="usage"></a>Uso  
 Para usar seu filtro personalizado com o serviço de roteamento, você deve adicioná-lo à tabela de filtro especificando uma nova entrada de filtro do tipo "Custom", o nome do tipo totalmente qualificado do filtro de mensagem e o nome do seu assembly.  Assim como acontece com outros MessageFilters, você pode especificar o filterData de cadeia de caracteres que será passado ao construtor do seu filtro personalizado.  
  
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
