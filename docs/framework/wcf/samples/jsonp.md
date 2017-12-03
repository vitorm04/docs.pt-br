---
title: JSONP
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c13b4d7b-dac7-4ffd-9f84-765c903511e1
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f9a9355c223d3d37811383d52d64f0ac6ddeeaea
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="jsonp"></a>JSONP
Este exemplo demonstra como dar suporte a JSON com preenchimento (JSONP) em serviços WCF REST. JSONP é uma convenção usada para chamar scripts de domínio cruzado por gerar marcações de script no documento atual. O resultado é retornado em uma função de retorno de chamada especificada. JSONP baseia-se a ideia marcas como \<script src = "http:/ /..." > pode avaliar qualquer domínio de scripts e o script recuperado por essas marcas é avaliado em um escopo no qual outras funções já podem ser definidas.  
  
## <a name="demonstrates"></a>Demonstra  
 Entre domínios de script com JSONP.  
  
## <a name="discussion"></a>Discussão  
 O exemplo inclui uma página da Web que adiciona dinamicamente um bloco de script após a página foi renderizada no navegador. Este bloco de script chama um serviço WCF REST com uma única operação, `GetCustomer`. O serviço WCF REST retorna o nome e endereço encapsulado em um nome de função de retorno de chamada do cliente. Quando o serviço WCF REST responde, a função de retorno de chamada na página da Web é invocada com os dados do cliente e a função de retorno de chamada exibe os dados na página da Web. A inclusão da marca do script e a execução da função de retorno de chamada são tratados automaticamente pelo controle ScriptManager do ASP.NET AJAX. O padrão de uso é o mesmo que todos os proxies do ASP.NET AJAX, com a adição de uma linha para habilitar JSONP, conforme mostrado no código a seguir:  
  
```csharp  
var proxy = new JsonpAjaxService.CustomerService();  
proxy.set_enableJsonp(true);  
proxy.GetCustomer(onSuccess, onFail, null);  
```  
  
 A página da Web pode chamar o serviço WCF REST porque o serviço está usando o <xref:System.ServiceModel.Description.WebScriptEndpoint> com `crossDomainScriptAccessEnabled` definido como `true`. Ambas essas configurações são feitas no arquivo Web. config sob o \<System. ServiceModel > elemento.  
  
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
  
 ScriptManager gerencia a interação com o serviço e distância oculta a complexidade da implementação manualmente acesso JSONP. Quando `crossDomainScriptAccessEnabled` é definido como `true` e a resposta de formato para uma operação é JSON, o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] infraestrutura inspeciona o URI da solicitação de um parâmetro de cadeia de caracteres de consulta de retorno de chamada e encapsula a resposta JSON com o valor da consulta de retorno de chamada parâmetro de cadeia de caracteres. No exemplo, a página da Web chama o serviço WCF REST com o URI a seguir.  
  
```  
http://localhost:33695/CustomerService/GetCustomer?callback=Sys._json0  
```  
  
 Porque o parâmetro de cadeia de caracteres de consulta de retorno de chamada tem um valor de `JsonPCallback`, o serviço WCF retorna uma resposta JSONP mostrada no exemplo a seguir.  
  
```  
Sys._json0({"__type":"Customer:#Microsoft.Samples.Jsonp","Address":"1 Example Way","Name":"Bob"});  
```  
  
 Essa resposta JSONP inclui os dados formatados como JSON, empacotado com o nome da função de retorno de chamada solicitou a página da Web do cliente. ScriptManager executar esse retorno de chamada usando uma marca de script para fazer a solicitação de domínio cruzado e, em seguida, passe o resultado para o manipulador de onSuccess que foi passado para a operação GetCustomer do proxy do ASP.NET AJAX.  
  
 O exemplo consiste em dois aplicativos da web ASP.NET: um contém apenas um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço e a outra contém a página da Web. aspx, que chama o serviço. Ao executar a solução, [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] hospedará os dois sites em portas diferentes, que cria um ambiente onde o serviço e o cliente residir em domínios diferentes.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\AJAX\JSONP`  
  
#### <a name="to-run-the-sample"></a>Para executar a amostra  
  
1.  Abra a solução do exemplo JSONP.  
  
2.  Pressione F5 para iniciar o HYPERLINK "http://localhost:26648/JSONPClientPage.aspx" http://localhost:26648/JSONPClientPage.aspx no navegador.  
  
3.  Observe que, depois que a página for carregada, as entradas de texto para "Nome" e "Address" são preenchidas por valores.  Esses valores foram fornecidos de uma chamada para o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço depois que o navegador concluído o processamento da página.
