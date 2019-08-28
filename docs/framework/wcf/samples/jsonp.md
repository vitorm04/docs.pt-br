---
title: JSONP
ms.date: 03/30/2017
ms.assetid: c13b4d7b-dac7-4ffd-9f84-765c903511e1
ms.openlocfilehash: 9f24ccb5ba14e0b43f0e3f911a1672db5821d228
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70039550"
---
# <a name="jsonp"></a>JSONP
Este exemplo demonstra como dar suporte a JSON com preenchimento (JSONP) nos serviços REST do WCF. JSONP é uma convenção usada para invocar scripts entre domínios, gerando marcas de script no documento atual. O resultado é retornado em uma função de retorno de chamada especificada. O JSONP é baseado na ideia de que marcas como `<script src="http://..." >` o podem avaliar scripts de qualquer domínio e o script recuperado por essas marcas é avaliado em um escopo no qual outras funções já podem estar definidas.

## <a name="demonstrates"></a>Demonstra
 Script entre domínios com o JSONP.

## <a name="discussion"></a>Discussão
 O exemplo inclui uma página da Web que adiciona dinamicamente um bloco de script depois que a página é processada no navegador. Esse bloco de script chama um serviço REST do WCF que tem uma única `GetCustomer`operação,. O serviço REST do WCF retorna o nome e o endereço do cliente encapsulados em um nome de função de retorno de chamada. Quando o serviço REST do WCF responde, a função de retorno de chamada na página da Web é invocada com os dados do cliente e a função de retorno de chamada exibe os dados na página da Web. A injeção da marca de script e a execução da função de retorno de chamada é manipulada automaticamente pelo controle ScriptManager do ASP.NET AJAX. O padrão de uso é o mesmo que todos os proxies AJAX do ASP.NET, com a adição de uma linha para habilitar o JSONP, conforme mostrado no código a seguir:

```csharp
var proxy = new JsonpAjaxService.CustomerService();
proxy.set_enableJsonp(true);
proxy.GetCustomer(onSuccess, onFail, null);
```

 A página da Web pode chamar o serviço REST do WCF porque o serviço está <xref:System.ServiceModel.Description.WebScriptEndpoint> usando `crossDomainScriptAccessEnabled` o com `true`definido como. Essas duas configurações são feitas no arquivo \<Web. config no elemento System. ServiceModel >.

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

 O ScriptManager gerencia a interação com o serviço e oculta a complexidade de implementar manualmente o acesso JSONP. Quando `crossDomainScriptAccessEnabled` é definido como `true` e o formato de resposta para uma operação é JSON, a infraestrutura do WCF inspeciona o URI da solicitação de um parâmetro de cadeia de caracteres de consulta de retorno de chamada e encapsula a resposta JSON com o valor da cadeia de caracteres de consulta de retorno de chamada meter. No exemplo, a página da Web chama o serviço REST do WCF com o URI a seguir.

```
http://localhost:33695/CustomerService/GetCustomer?callback=Sys._json0
```

 Como o parâmetro de cadeia de caracteres de consulta de `JsonPCallback`retorno de chamada tem um valor de, o serviço WCF retorna uma resposta JSONP mostrada no exemplo a seguir.

```
Sys._json0({"__type":"Customer:#Microsoft.Samples.Jsonp","Address":"1 Example Way","Name":"Bob"});
```

 Essa resposta JSONP inclui os dados do cliente formatados como JSON, encapsulados com o nome da função de retorno de chamada que a página da Web solicitou. O ScriptManager executará esse retorno de chamada usando uma marca de script para realizar a solicitação entre domínios e, em seguida, passará o resultado para o manipulador OnSuccess que foi passado para a operação GetCustomer do proxy AJAX ASP.NET.

 O exemplo consiste em dois aplicativos Web ASP.NET: um contém apenas um serviço WCF, e outro contém a página do Web. aspx, que chama o serviço. Ao executar a solução, o Visual Studio 2012 hospedará os dois sites em portas diferentes, o que cria um ambiente em que o serviço e o cliente residem em domínios diferentes.

> [!IMPORTANT]
> Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) [!INCLUDE[wf1](../../../../includes/wf1-md.md)] e exemplos. Este exemplo está localizado no seguinte diretório.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\AJAX\JSONP`  
  
#### <a name="to-run-the-sample"></a>Para executar a amostra  
  
1. Abra a solução para o exemplo JSONP.  
  
2. Pressione F5 para iniciar `http://localhost:26648/JSONPClientPage.aspx` no navegador.  
  
3. Observe que, depois que a página é carregada, as entradas de texto para "nome" e "endereço" são preenchidas por valores.  Esses valores foram fornecidos de uma chamada para o serviço WCF depois que o navegador terminar de renderizar a página.
