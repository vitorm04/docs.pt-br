---
title: Serviço AJAX básico
ms.date: 03/30/2017
ms.assetid: d66d0c91-0109-45a0-a901-f3e4667c2465
ms.openlocfilehash: 7a9529b79c9993e045e6bb28a7ad608f453a694e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54509981"
---
# <a name="basic-ajax-service"></a>Serviço AJAX básico
Este exemplo demonstra como usar o Windows Communication Foundation (WCF) para criar um serviço básico do ASP.NET Asynchronous JavaScript and XML (AJAX) (um serviço que você pode acessar usando código JavaScript de um cliente de navegador da Web). O serviço usa o <xref:System.ServiceModel.Web.WebGetAttribute> atributo para garantir que o serviço responde a solicitações HTTP GET e está configurado para usar o formato de dados de objeto notação JSON (JavaScript) para respostas.  
  
 Suporte a AJAX no WCF é otimizado para uso com o ASP.NET AJAX por meio de `ScriptManager` controle. Para obter um exemplo de como usar o WCF com o ASP.NET AJAX, consulte o [amostras do AJAX](https://msdn.microsoft.com/library/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e).  
  
> [!NOTE]
>  Os procedimentos de instalação e as instruções de compilação para esse exemplo estão localizadas no final deste tópico.  
  
 No código a seguir, o <xref:System.ServiceModel.Web.WebGetAttribute> atributo é aplicado a `Add` operação para garantir que o serviço responde a solicitações HTTP GET. O código usa GET para manter a simplicidade (você pode construir uma solicitação HTTP GET em qualquer navegador da Web). Você também pode usar GET para habilitar o cache. HTTP POST é o padrão na ausência do `WebGetAttribute` atributo.  

```csharp
[ServiceContract(Namespace = "SimpleAjaxService")]
public interface ICalculator
{
    [WebGet]
    double Add(double n1, double n2);
    //Other operations omitted…
}
```

 O arquivo. svc de amostra usa <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, que adiciona um <xref:System.ServiceModel.Description.WebScriptEndpoint> ponto de extremidade padrão para o serviço. O ponto de extremidade é configurado em um endereço relativo ao arquivo. svc em branco. Isso significa que o endereço do serviço é `http://localhost/ServiceModelSamples/service.svc`, com nenhum sufixos adicionais que não seja o nome da operação.  

```svc
<%@ServiceHost language="C#" Debug="true" Service="Microsoft.Samples.SimpleAjaxService.CalculatorService" Factory="System.ServiceModel.Activation.WebScriptServiceHostFactory" %>
```

 O <xref:System.ServiceModel.Description.WebScriptEndpoint> é pré-configurado para tornar o serviço acessível a partir de uma página de cliente ASP.NET AJAX. A seção a seguir no Web. config pode ser usada para fazer alterações de configuração adicionais para o ponto de extremidade. Ele pode ser removido se nenhuma alteração adicional é necessária.  
  
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
  
 O <xref:System.ServiceModel.Description.WebScriptEndpoint> define o formato de dados padrão para o serviço como JSON em vez de XML. Para invocar o serviço, navegue até `http://localhost/ServiceModelSamples/service.svc/Add?n1=100&n2=200` depois de concluir o conjunto de backup e criar etapas mostradas neste tópico. Essa funcionalidade de teste é habilitada pelo uso de uma solicitação HTTP GET.  
  
 O cliente SimpleAjaxClientPage.aspx de página da Web contém código ASP.NET para invocar o serviço sempre que o usuário clica em um dos botões de operação na página. O `ScriptManager` controle é usado para criar um proxy para o serviço acessível por meio de JavaScript.  

```aspx-csharp
<asp:ScriptManager ID="ScriptManager" runat="server">  
    <Services>  
        <asp:ServiceReference Path="service.svc" />  
    </Services>  
</asp:ScriptManager>  
```

 O proxy local é instanciado e as operações são invocadas usando o seguinte código JavaScript.  

```javascript
// Code for extracting arguments n1 and n2 omitted…  
// Instantiate a service proxy  
var proxy = new SimpleAjaxService.ICalculator();  
// Code for selecting operation omitted…  
proxy.Add(parseFloat(n1), parseFloat(n2), onSuccess, onFail, null);  
```

 Se a chamada de serviço for bem-sucedida, o código chama o `onSuccess` manipulador e o resultado da operação é exibido em uma caixa de texto.  

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
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\SimpleAjaxService`  
  
## <a name="see-also"></a>Consulte também
