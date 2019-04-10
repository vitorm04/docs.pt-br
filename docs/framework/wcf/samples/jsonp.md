---
title: JSONP
ms.date: 03/30/2017
ms.assetid: c13b4d7b-dac7-4ffd-9f84-765c903511e1
ms.openlocfilehash: 37da57a000376f972cd6da9e04be46ddec1b7144
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59329655"
---
# <a name="jsonp"></a>JSONP
Este exemplo demonstra como dar suporte a JSON com preenchimento (JSONP) nos serviços REST do WCF. O JSONP é uma convenção usada para invocar scripts entre domínios por gerar marcações de script no documento atual. O resultado é retornado em uma função de retorno de chamada especificados. JSONP é baseado na ideia de que as marcas como `<script src="http://..." >` pode avaliar qualquer domínio de scripts e o script recuperado por essas marcas é avaliado dentro de um escopo em que as outras funções já podem ser definidas.

## <a name="demonstrates"></a>Demonstra
 Entre domínios scripts com o JSONP.

## <a name="discussion"></a>Discussão
 O exemplo inclui uma página da Web que adiciona dinamicamente um bloco de script depois que a página foi renderizada no navegador. Este bloco de script chama um serviço REST do WCF que tem uma única operação, `GetCustomer`. O serviço REST WCF retorna o nome e endereço encapsulado em um nome de função de retorno de chamada de um cliente. Quando o serviço REST WCF responde, a função de retorno de chamada na página da Web é invocada com os dados do cliente e a função de retorno de chamada exibe os dados na página da Web. A injeção da marca do script e a execução da função de retorno de chamada são tratados automaticamente pelo controle ScriptManager do AJAX ASP.NET. O padrão de uso é o mesmo que todos os proxies do ASP.NET AJAX, com a adição de uma linha para habilitar o JSONP, conforme mostrado no código a seguir:

```csharp
var proxy = new JsonpAjaxService.CustomerService();
proxy.set_enableJsonp(true);
proxy.GetCustomer(onSuccess, onFail, null);
```

 A página da Web pode chamar o serviço REST WCF porque o serviço está usando o <xref:System.ServiceModel.Description.WebScriptEndpoint> com `crossDomainScriptAccessEnabled` definido como `true`. Ambas essas configurações são feitas no arquivo Web. config sob o \<System. ServiceModel > elemento.

```xml
<system.serviceModel>
  <serviceHostingEnvironment aspNetCompatibilityEnabled="true"/>
  <standardEndpoints>
    <webScriptEndpoint>
      <standardEndpoint name="" crossDomainScriptAccessEnabled="true"/>
    </webScriptEndpoint>
  </standardEndpoints>
</system.serviceModel>
```

 ScriptManager gerencia a interação com o serviço e oculta a complexidade de implementar manualmente acesso JSONP. Quando `crossDomainScriptAccessEnabled` é definido como `true` e o formato da resposta para uma operação é JSON, a infraestrutura do WCF inspeciona o URI da solicitação para um parâmetro de cadeia de caracteres de consulta de retorno de chamada e encapsula a resposta JSON com o valor da cadeia de caracteres de consulta de retorno de chamada parâmetro. No exemplo, a página da Web chama o serviço de REST do WCF com o seguinte URI.

```
http://localhost:33695/CustomerService/GetCustomer?callback=Sys._json0
```

 Porque o parâmetro de cadeia de caracteres de consulta de retorno de chamada tem um valor de `JsonPCallback`, o serviço WCF retorna uma resposta JSONP mostrada no exemplo a seguir.

```
Sys._json0({"__type":"Customer:#Microsoft.Samples.Jsonp","Address":"1 Example Way","Name":"Bob"});
```

 Essa resposta JSONP inclui os dados formatados como JSON, empacotado com o nome da função de retorno de chamada que solicitou a página da Web do cliente. ScriptManager executará esse retorno de chamada usando uma marca de script para realizar a solicitação entre domínios e, em seguida, passe o resultado para o manipulador onSuccess que foi passado para a operação GetCustomer do proxy com o ASP.NET AJAX.

 O exemplo consiste em dois aplicativos de web do ASP.NET: um contém apenas um serviço WCF, e outra contém a página da Web. aspx, que chama o serviço. Ao executar a solução, o Visual Studio 2012 hospedará os dois sites em portas diferentes, que cria um ambiente em que o serviço e o cliente residem em domínios diferentes.

> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\AJAX\JSONP`  
  
#### <a name="to-run-the-sample"></a>Para executar a amostra  
  
1. Abra a solução do exemplo JSONP.  
  
2. Pressione F5 para iniciar `http://localhost:26648/JSONPClientPage.aspx` no navegador.  
  
3. Observe que, depois que a página for carregada, as entradas de texto para "Name" e "Address" são preenchidas por valores.  Esses valores foram fornecidos de uma chamada para o serviço WCF depois que o navegador concluída a renderização da página.
