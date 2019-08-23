---
title: Serviço AJAX básico
ms.date: 03/30/2017
ms.assetid: d66d0c91-0109-45a0-a901-f3e4667c2465
ms.openlocfilehash: 2d3770630df693093b05868f00c409f8245f858b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925245"
---
# <a name="basic-ajax-service"></a>Serviço AJAX básico
Este exemplo demonstra como usar o Windows Communication Foundation (WCF) para criar um serviço básico de JavaScript e XML (AJAX) ASP.NET assíncrono (um serviço que você pode acessar usando código JavaScript de um cliente de navegador da Web). O serviço usa o <xref:System.ServiceModel.Web.WebGetAttribute> atributo para garantir que o serviço responda às solicitações HTTP Get e esteja configurado para usar o formato de dados JavaScript Object Notation (JSON) para respostas.  
  
 O suporte ao AJAX no WCF é otimizado para uso com o `ScriptManager` ASP.NET AJAX por meio do controle. Para obter um exemplo de como usar o WCF com o ASP.NET AJAX, consulte os [exemplos do AJAX](ajax.md).  
  
> [!NOTE]
> Os procedimentos de instalação e as instruções de compilação para esse exemplo estão localizadas no final deste tópico.  
  
 No código a seguir, o <xref:System.ServiceModel.Web.WebGetAttribute> atributo é aplicado `Add` à operação para garantir que o serviço responda às solicitações HTTP Get. O código usa GET para simplificação (você pode construir uma solicitação HTTP GET de qualquer navegador da Web). Você também pode usar GET para habilitar o Caching. HTTP post é o padrão na ausência do `WebGetAttribute` atributo.  

```csharp
[ServiceContract(Namespace = "SimpleAjaxService")]
public interface ICalculator
{
    [WebGet]
    double Add(double n1, double n2);
    //Other operations omitted…
}
```

 O arquivo. svc de exemplo <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>usa, que adiciona <xref:System.ServiceModel.Description.WebScriptEndpoint> um ponto de extremidade padrão ao serviço. O ponto de extremidade é configurado em um endereço vazio relativo ao arquivo. svc. Isso significa que o endereço do serviço é `http://localhost/ServiceModelSamples/service.svc`, sem nenhum sufixo adicional além do nome da operação.  

```svc
<%@ServiceHost language="C#" Debug="true" Service="Microsoft.Samples.SimpleAjaxService.CalculatorService" Factory="System.ServiceModel.Activation.WebScriptServiceHostFactory" %>
```

 O <xref:System.ServiceModel.Description.WebScriptEndpoint> é pré-configurado para tornar o serviço acessível de uma página de cliente do ASP.NET AJAX. A seção a seguir no Web. config pode ser usada para fazer alterações de configuração adicionais no ponto de extremidade. Ela poderá ser removida se nenhuma alteração extra for necessária.  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>  
    <webScriptEndpoint>  
      <!-- Use this element to configure the endpoint -->  
      <standardEndpoint name=""  />  
    </webScriptEndpoint>  
  </standardEndpoints>  
</system.serviceModel>  
```  
  
 O <xref:System.ServiceModel.Description.WebScriptEndpoint> define o formato de dados padrão para o serviço para JSON em vez de XML. Para invocar o serviço, navegue `http://localhost/ServiceModelSamples/service.svc/Add?n1=100&n2=200` até depois de concluir as etapas de configuração e compilação mostradas mais adiante neste tópico. Essa funcionalidade de teste é habilitada pelo uso de uma solicitação HTTP GET.  
  
 A página da Web do cliente SimpleAjaxClientPage. aspx contém o código ASP.NET para invocar o serviço sempre que o usuário clicar em um dos botões de operação na página. O `ScriptManager` controle é usado para tornar um proxy para o serviço acessível por meio de JavaScript.  

```aspx-csharp
<asp:ScriptManager ID="ScriptManager" runat="server">  
    <Services>  
        <asp:ServiceReference Path="service.svc" />  
    </Services>  
</asp:ScriptManager>  
```

 O proxy local é instanciado e as operações são invocadas usando o código JavaScript a seguir.  

```javascript
// Code for extracting arguments n1 and n2 omitted…  
// Instantiate a service proxy  
var proxy = new SimpleAjaxService.ICalculator();  
// Code for selecting operation omitted…  
proxy.Add(parseFloat(n1), parseFloat(n2), onSuccess, onFail, null);  
```

 Se a chamada de serviço for bem sucedido, o código `onSuccess` invocará o manipulador e o resultado da operação será exibido em uma caixa de texto.  

```javascript
function onSuccess(mathResult){  
     document.getElementById("result").value = mathResult;  
}
```

> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) [!INCLUDE[wf1](../../../../includes/wf1-md.md)] e exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\SimpleAjaxService`  
