---
title: '@ServiceHost'
ms.date: 03/30/2017
ms.assetid: 96ba6967-00f2-422f-9aa7-15de4d33ebf3
ms.openlocfilehash: 730b1188a95d0e35d7431d43884e867e5520585e
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/20/2018
ms.locfileid: "46471243"
---
# <a name="servicehost"></a>\@ServiceHost
Associa a fábrica usada para produzir o host de serviço com o serviço hospedado e outros aspectos de programação necessários para acessar ou compilar o código de hospedagem fornecido no arquivo. svc.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
<% @ServiceHost   
Service = "Service, ServiceNamespace"   
Factory = "Factory, FactoryNamespace"  
Debug = "Debug"  
Language = "Language"   
CodeBehind = "CodeBehind"%>  
```  
  
## <a name="attributes"></a>Atributos  
  
#### <a name="service"></a>Serviço  
 O nome do tipo CLR do serviço hospedado. Isso deve ser um nome qualificado de um tipo que implementa um ou mais dos contatos de serviço.  
  
#### <a name="factory"></a>fábrica  
 O nome do tipo CLR da fábrica de host de serviço usado para instanciar o host de serviço. Esse atributo é opcional. Se não for especificado, o padrão <xref:System.ServiceModel.Activation.ServiceHostFactory> é usado, que retorna uma instância de <xref:System.ServiceModel.ServiceHost>.  
  
#### <a name="debug"></a>Depurar  
 Indica se o serviço do Windows Communication Foundation (WCF) deve ser compilado com símbolos de depuração. `true` Se o serviço do WCF deve ser compilado com símbolos de depuração; Caso contrário, `false`.  
  
#### <a name="language"></a>Idioma  
 Especifica o idioma usado ao compilar todo o código embutido dentro do arquivo (. svc). Os valores podem representar qualquer. Linguagens com suporte do NET, incluindo c#, VB e JS, que se referem à linguagem c#, Visual Basic .NET e JScript .NET, respectivamente. Esse atributo é opcional.  
  
#### <a name="codebehind"></a>Code-behind  
 Especifica o arquivo de origem que implementa o serviço Web XML, quando a classe que implementa o serviço Web XML não reside no mesmo arquivo e não foi compilada em um assembly e colocada no diretório \Bin.  
  
## <a name="remarks"></a>Comentários  
 O <xref:System.ServiceModel.ServiceHost> usado para hospedar o serviço é um ponto de extensibilidade dentro do modelo de programação do Windows Communication Foundation (WCF). Um padrão de fábrica é usado para instanciar o <xref:System.ServiceModel.ServiceHost> porque ele é, potencialmente, um tipo polimórfico que o ambiente de hospedagem não deve instanciar diretamente.  
  
 A implementação padrão usa <xref:System.ServiceModel.Activation.ServiceHostFactory> para criar uma instância de <xref:System.ServiceModel.ServiceHost>. Mas você pode fornecer sua própria fábrica (um que retorna o seu host derivada), especificando o nome do tipo CLR da sua implementação de fábrica na [ @ServiceHost ](../../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) diretiva.  
  
 Para usar fábrica do host de serviço personalizado próprio em vez do alocador padrão, basta fornecer o nome do tipo de [ @ServiceHost ](../../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) diretiva da seguinte maneira:  
  
```xml  
<% @ServiceHost Factory="DerivedFactory" Service="MyService" %>  
```  
  
 Mantenha as implementações de fábrica o mais leves possível. Se você tiver muita lógica personalizada, seu código é mais reutilizável se você colocar essa lógica dentro de seu host, em vez de dentro de fábrica.  
  
 Por exemplo, para habilitar um ponto de extremidade habilitados para AJAX `MyService`, especifique o <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> para o valor da `Factory` atributo, em vez do padrão <xref:System.ServiceModel.Activation.ServiceHostFactory>, no [ @ServiceHost ](../../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) diretiva como como mostrado no exemplo a seguir.  
  
## <a name="example"></a>Exemplo  
  
```  
<% @ServiceHost   
Service="MyService"  
Language="C#"  
Debug="true"  
Factory="WebScriptServiceHostFactory"  
%>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Host de serviço personalizado](../../../../../docs/framework/wcf/samples/custom-service-host.md)
