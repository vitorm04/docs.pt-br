---
title: '@ServiceHost'
ms.date: 03/30/2017
ms.assetid: 96ba6967-00f2-422f-9aa7-15de4d33ebf3
ms.openlocfilehash: dd3dd026749ccc299cd922b79dcae8ccbcc722d8
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73968821"
---
# <a name="servicehost"></a>\@ServiceHost
Associa a fábrica usada para produzir o host de serviço com o serviço a ser hospedado e outros aspectos de programação necessários para acessar ou compilar o código de hospedagem fornecido no arquivo. svc.  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<% @ServiceHost
Service = "Service, ServiceNamespace"
Factory = "Factory, FactoryNamespace"
Debug = "Debug"
Language = "Language"
CodeBehind = "CodeBehind"
%>
```  
  
## <a name="attributes"></a>Atributos  
  
#### <a name="service"></a>Serviço  
 O nome do tipo CLR do serviço hospedado. Deve ser um nome qualificado de um tipo que implementa um ou mais dos contatos de serviço.  
  
#### <a name="factory"></a>padrões  
 O nome do tipo CLR da fábrica do host de serviço usada para instanciar o host de serviço. Esse atributo é opcional. Se não for especificado, o <xref:System.ServiceModel.Activation.ServiceHostFactory> padrão será usado, que retorna uma instância de <xref:System.ServiceModel.ServiceHost>.  
  
#### <a name="debug"></a>Depurar  
 Indica se o serviço de Windows Communication Foundation (WCF) deve ser compilado com símbolos de depuração. `true` se o serviço WCF deve ser compilado com símbolos de depuração; caso contrário, `false`.  
  
#### <a name="language"></a>Idioma  
 Especifica o idioma usado ao compilar todo o código embutido no arquivo (. svc). Os valores podem representar qualquer. Linguagem com suporte .net, incluindo C#, VB e js, que se referem C#ao, Visual Basic .net e JScript .net, respectivamente. Esse atributo é opcional.  
  
#### <a name="codebehind"></a>Behind  
 Especifica o arquivo de origem que implementa o serviço Web XML, quando a classe que implementa o serviço Web XML não reside no mesmo arquivo e não foi compilada em um assembly e colocada no diretório \bin.  
  
## <a name="remarks"></a>Comentários  
 O <xref:System.ServiceModel.ServiceHost> usado para hospedar o serviço é um ponto de extensibilidade dentro do modelo de programação do Windows Communication Foundation (WCF). Um padrão de fábrica é usado para instanciar o <xref:System.ServiceModel.ServiceHost> porque ele é, potencialmente, um tipo polimórfico que o ambiente de hospedagem não deve instanciar diretamente.  
  
 A implementação padrão usa <xref:System.ServiceModel.Activation.ServiceHostFactory> para criar uma instância do <xref:System.ServiceModel.ServiceHost>. Mas você pode fornecer sua própria fábrica (uma que retorna o host derivado) especificando o nome do tipo CLR de sua implementação de fábrica na diretiva [\@ServiceHost](servicehost.md) .  
  
 Para usar sua própria fábrica de hosts de serviço personalizada em vez da fábrica padrão, basta fornecer o nome do tipo na diretiva de [@ServiceHost](servicehost.md) da seguinte maneira:  
  
```xml  
<% @ServiceHost Factory="DerivedFactory" Service="MyService" %>  
```  
  
 Mantenha as implementações de fábrica o mais leve possível. Se você tiver muita lógica personalizada, seu código será mais reutilizável se você colocar essa lógica dentro de seu host em vez de dentro da fábrica.  
  
 Por exemplo, para habilitar um ponto de extremidade habilitado para AJAX para `MyService`, especifique o <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> para o valor do atributo `Factory`, em vez do <xref:System.ServiceModel.Activation.ServiceHostFactory>padrão, na diretiva [@ServiceHost](servicehost.md) , conforme mostrado no exemplo a seguir.  
  
## <a name="example"></a>Exemplo  
  
```xml  
<% @ServiceHost
Service="MyService"  
Language="C#"  
Debug="true"  
Factory="WebScriptServiceHostFactory"  
%>  
```  
  
## <a name="see-also"></a>Consulte também

- [Host de serviço personalizado](../../../wcf/samples/custom-service-host.md)
