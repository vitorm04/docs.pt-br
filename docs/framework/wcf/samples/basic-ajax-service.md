---
title: "Serviço AJAX básico"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d66d0c91-0109-45a0-a901-f3e4667c2465
caps.latest.revision: "30"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 690d92e5c4107816c43efcd07cdaff2b8bc62e2c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="basic-ajax-service"></a>Serviço AJAX básico
Este exemplo demonstra como usar [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] para criar um serviço básico de JavaScript assíncrona do ASP.NET AJAX (and XML) (um serviço que você pode acessar usando o código JavaScript de um cliente de navegador da Web). O serviço usa o <xref:System.ServiceModel.Web.WebGetAttribute> atributo para garantir que o serviço responde a solicitações HTTP GET e está configurado para usar o formato de dados de objeto notação JSON (JavaScript) para respostas.  
  
 Suporte do AJAX no [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] é otimizado para uso com o ASP.NET AJAX por meio de `ScriptManager` controle. Para obter um exemplo do uso de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] com o ASP.NET AJAX, consulte o [AJAX exemplos](http://msdn.microsoft.com/en-us/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e).  
  
> [!NOTE]
>  Os procedimentos de instalação e as instruções de compilação para esse exemplo estão localizadas no final deste tópico.  
  
 No código a seguir, o <xref:System.ServiceModel.Web.WebGetAttribute> atributo é aplicado para o `Add` operação para garantir que o serviço responde a solicitações HTTP GET. O código usa GET para manter a simplicidade (você pode construir uma solicitação HTTP GET em qualquer navegador da Web). Você também pode usar GET para habilitar o cache. HTTP POST é o padrão na ausência de `WebGetAttribute` atributo.  
  
```  
[ServiceContract(Namespace = "SimpleAjaxService")]  
public interface ICalculator  
{  
  
    [WebGet]  
    double Add(double n1, double n2);  
    //Other operations omitted…  
}  
```  
  
 O arquivo. svc de exemplo usa <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, que adiciona um <xref:System.ServiceModel.Description.WebScriptEndpoint> ponto de extremidade padrão para o serviço. O ponto de extremidade é configurado em um endereço vazio em relação ao arquivo. svc. Isso significa que o endereço do serviço é http://localhost/ServiceModelSamples/service.svc com nenhuma sufixos adicionais que não seja o nome da operação.  
  
```  
<%@ServiceHost language="C#" Debug="true" Service="Microsoft.Samples.SimpleAjaxService.CalculatorService" Factory="System.ServiceModel.Activation.WebScriptServiceHostFactory" %>  
```  
  
 O <xref:System.ServiceModel.Description.WebScriptEndpoint> é pré-configurado para disponibilizar o serviço de uma página de cliente ASP.NET AJAX. A seção a seguir no Web. config pode ser usada para fazer alterações de configuração adicionais para o ponto de extremidade. Ele pode ser removido se nenhuma alteração adicional é necessária.  
  
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
  
 O <xref:System.ServiceModel.Description.WebScriptEndpoint> define o formato de dados padrão para o serviço em JSON em vez de XML. Para chamar o serviço, navegue até http://localhost/ServiceModelSamples/service.svc/Add?n1=100&n2=200 depois de concluir o conjunto de backup e criar etapas mostradas neste tópico. Essa funcionalidade de teste é habilitada pelo uso de uma solicitação HTTP GET.  
  
 O cliente SimpleAjaxClientPage.aspx de página da Web contém código para chamar o serviço sempre que o usuário clica em um dos botões de operação na página do ASP.NET. O `ScriptManager` controle é usado para disponibilizar um proxy para o serviço por meio de JavaScript.  
  
```  
<asp:ScriptManager ID="ScriptManager" runat="server">  
    <Services>  
        <asp:ServiceReference Path="service.svc" />  
    </Services>  
</asp:ScriptManager>  
```  
  
 O proxy local é instanciado e operações são invocadas usando o seguinte código JavaScript.  
  
```  
// Code for extracting arguments n1 and n2 omitted…  
// Instantiate a service proxy  
var proxy = new SimpleAjaxService.ICalculator();  
// Code for selecting operation omitted…  
proxy.Add(parseFloat(n1), parseFloat(n2), onSuccess, onFail, null);  
```  
  
 Se a chamada de serviço for bem-sucedida, o código chama o `onSuccess` manipulador e o resultado da operação é exibido na caixa de texto.  
  
```  
function onSuccess(mathResult){  
     document.getElementById("result").value = mathResult;  
}  
```  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\SimpleAjaxService`  
  
## <a name="see-also"></a>Consulte também
