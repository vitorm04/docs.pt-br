---
title: JSONP
ms.date: 03/30/2017
ms.assetid: c13b4d7b-dac7-4ffd-9f84-765c903511e1
ms.openlocfilehash: 6b5b42285539c2334bccaa04e1ba179d2cf0046c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183569"
---
# <a name="jsonp"></a>JSONP
Esta amostra demonstra como apoiar json com preenchimento (JSONP) em serviços WCF REST. JSONP é uma convenção usada para invocar scripts de domínio cruzado gerando tags de script no documento atual. O resultado é retornado em uma função de retorno de chamada especificada. O JSONP baseia-se na `<script src="http://..." >` ideia de que tags como podem avaliar scripts de qualquer domínio e o script recuperado por essas tags é avaliado dentro de um escopo no qual outras funções podem já ser definidas.

## <a name="demonstrates"></a>Demonstra
 Scripting de domínio cruzado com JSONP.

## <a name="discussion"></a>Discussão
 A amostra inclui uma página da Web que adiciona dinamicamente um bloco de script após a página ter sido renderizada no navegador. Este bloco de script soca um serviço `GetCustomer`WCF REST que tem uma única operação, . O serviço WCF REST retorna o nome e endereço de um cliente embrulhado em um nome de função de retorno de chamada. Quando o serviço WCF REST responde, a função de retorno de chamada na página da Web é invocada com os dados do cliente e a função de retorno de chamada exibe os dados na página da Web. A injeção da tag de script e a execução da função de retorno de chamada são automaticamente manuseadas pelo ASP.NET controle AJAX ScriptManager. O padrão de uso é o mesmo que todos os proxies ajax ASP.NET, com a adição de uma linha para habilitar JSONP, como mostrado no código a seguir:

```csharp
var proxy = new JsonpAjaxService.CustomerService();
proxy.set_enableJsonp(true);
proxy.GetCustomer(onSuccess, onFail, null);
```

 A página da Web pode chamar o serviço <xref:System.ServiceModel.Description.WebScriptEndpoint> WCF REST porque o serviço está usando o conjunto com `crossDomainScriptAccessEnabled` `true`. Ambas as configurações são feitas no arquivo Web.config o \<elemento system.serviceModel>.

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

 O ScriptManager gerencia a interação com o serviço e oculta a complexidade de implementar manualmente o acesso JSONP. Quando `crossDomainScriptAccessEnabled` é `true` definido e o formato de resposta para uma operação é JSON, a infra-estrutura WCF inspeciona o URI da solicitação de um parâmetro de seqüência de consulta de chamada e envolve a resposta JSON com o valor do parâmetro de string de consulta de chamada. Na amostra, a página da Web chama o serviço WCF REST com o seguinte URI.

```http
http://localhost:33695/CustomerService/GetCustomer?callback=Sys._json0
```

 Como o parâmetro de seqüência de `JsonPCallback`seqüeique de chamada de chamada tem um valor de , o serviço WCF retorna uma resposta JSONP mostrada no exemplo a seguir.

```json
Sys._json0({"__type":"Customer:#Microsoft.Samples.Jsonp","Address":"1 Example Way","Name":"Bob"});
```

 Esta resposta JSONP inclui os dados do cliente formatados como JSON, embrulhados com o nome da função de retorno de chamada que a página da Web solicitou. O ScriptManager executará esse retorno de chamada usando uma tag de script para realizar a solicitação de domínio cruzado e, em seguida, passará o resultado para o manipulador onSuccess que foi passado para a operação GetCustomer do proxy ASP.NET a AJAX.

 A amostra consiste em dois ASP.NET aplicações web: uma contém apenas um serviço WCF e outra contém a página web .aspx, que chama o serviço. Ao executar a solução, o Visual Studio 2012 hospedará os dois sites em diferentes portas, o que cria um ambiente onde o serviço e o cliente vivem em diferentes domínios.

> [!IMPORTANT]
> Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation). Este exemplo está localizado no seguinte diretório.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\AJAX\JSONP`  
  
#### <a name="to-run-the-sample"></a>Para executar a amostra  
  
1. Abra a solução para a amostra JSONP.  
  
2. Pressione F5 `http://localhost:26648/JSONPClientPage.aspx` para iniciar no navegador.  
  
3. Observe que após as cargas da página, as entradas de texto para "Nome" e "Endereço" são preenchidas por valores.  Esses valores foram fornecidos a partir de uma chamada para o serviço WCF depois que o navegador terminou de renderizar a página.
