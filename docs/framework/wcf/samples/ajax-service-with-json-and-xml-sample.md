---
title: Serviço de AJAX com exemplo de JSON e XML
ms.date: 03/30/2017
ms.assetid: 8ea5860d-0c42-4ae9-941a-e07efdd8e29c
ms.openlocfilehash: 1beb89c11fccefec24ccbebc3fe30033a646718d
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43452684"
---
# <a name="ajax-service-with-json-and-xml-sample"></a>Serviço de AJAX com exemplo de JSON e XML
Este exemplo demonstra como usar o Windows Communication Foundation (WCF) para criar um serviço de Asynchronous JavaScript and XML (AJAX) que retorna dados de objeto notação JSON (JavaScript) ou XML. Você pode acessar um serviço AJAX usando código JavaScript de um cliente de navegador da Web. Este exemplo se baseia a [serviço de AJAX básico](../../../../docs/framework/wcf/samples/basic-ajax-service.md) exemplo.  
  
 Ao contrário de outros exemplos de AJAX, este exemplo usa o ASP.NET AJAX e o <xref:System.Web.UI.ScriptManager> controle. Com alguma configuração adicional, os serviços WCF AJAX podem ser acessados de qualquer página HTML por meio de JavaScript e este cenário é mostrado aqui. Para obter um exemplo de como usar o WCF com o ASP.NET AJAX, consulte [amostras do AJAX](https://msdn.microsoft.com/library/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e).  
  
 Este exemplo mostra como alternar o tipo de resposta de uma operação entre JSON e XML. Essa funcionalidade está disponível independentemente do serviço é configurado para ser acessado por ASP.NET AJAX ou por uma página de cliente HTML/JavaScript.  
  
> [!NOTE]
>  As instruções de procedimento e compilação de configuração para este exemplo estão localizadas no final deste tópico.  
  
 Para habilitar o uso de clientes do ASP.NET AJAX, use <xref:System.ServiceModel.Activation.WebServiceHostFactory> (não <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>) no arquivo. svc. <xref:System.ServiceModel.Activation.WebServiceHostFactory> Adiciona um <xref:System.ServiceModel.Description.WebHttpEndpoint> ponto de extremidade padrão para o serviço. O ponto de extremidade é configurado em um endereço relativo ao arquivo. svc; em branco Isso significa que o endereço do serviço é http://localhost/ServiceModelSamples/service.svc, com nenhum sufixos adicionais que não seja o nome da operação.  
  
```svc
<%@ServiceHost language="c#" Debug="true" Service="Microsoft.Samples.XmlAjaxService.CalculatorService" Factory="System.ServiceModel.Activation.WebServiceHostFactory" %>  
```  
  
 A seção a seguir no Web. config pode ser usada para fazer alterações de configuração adicionais para o ponto de extremidade. Ele pode ser removido se nenhuma alteração adicional é necessária.  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>  
    <webHttpEndpoint>  
      <!-- Use this element to configure the endpoint -->  
      <standardEndpoint name="" />  
    </webHttpEndpoint>  
  </standardEndpoints>  
</system.serviceModel>  
```  
  
 Os dados padrão de formato para <xref:System.ServiceModel.Description.WebHttpEndpoint> é XML, enquanto o formato de dados padrão para <xref:System.ServiceModel.Description.WebScriptEndpoint> é JSON. Para obter mais informações, consulte [criação de serviços do WCF AJAX sem ASP.NET](../../../../docs/framework/wcf/feature-details/creating-wcf-ajax-services-without-aspnet.md).  
  
 O serviço no exemplo a seguir é um serviço WCF padrão com duas operações. As duas operações requerem o <xref:System.ServiceModel.Web.WebMessageBodyStyle.Wrapped> estilo de corpo de <xref:System.ServiceModel.Web.WebGetAttribute> ou <xref:System.ServiceModel.Web.WebInvokeAttribute> atributos, que é específico para o `webHttp` comportamento e não tem influência sobre a opção de formato de dados JSON/XML.  

```csharp
[OperationContract]  
[WebInvoke(ResponseFormat = WebMessageFormat.Xml, BodyStyle = WebMessageBodyStyle.Wrapped)]  
MathResult DoMathXml(double n1, double n2);  
```

 O formato de resposta para a operação é especificado como XML, que é o padrão Configurando para o [ \<webHttp >](../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md) comportamento. No entanto, é recomendável explicitamente especificar o formato da resposta.  
  
 Outra operação usa o `WebInvokeAttribute` de atributos e especifica explicitamente o JSON em vez de XML para a resposta.  

```csharp
[OperationContract]  
[WebInvoke(ResponseFormat = WebMessageFormat.Json, BodyStyle = WebMessageBodyStyle.Wrapped)]  
MathResult DoMathJson(double n1, double n2);  
```

 Observe que, em ambos os casos, as operações retornam um tipo complexo, `MathResult`, que é um tipo de contrato de dados padrão do WCF.  
  
 O cliente XmlAjaxClientPage.htm de página da Web contém código JavaScript que invoca uma das duas operações anteriores quando o usuário clica o **executar o cálculo de (retorno JSON)** ou **executar cálculo (retorno XML)**  botões na página. O código para invocar o serviço constrói um corpo JSON e envia-o usando HTTP POST. A solicitação é criada manualmente em JavaScript, ao contrário do [serviço básico do AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md) exemplo e outros exemplos usando o ASP.NET AJAX.  

```csharp
// Create HTTP request  
var xmlHttp;  
// Request instantiation code omitted…  
// Result handler code omitted…  
  
// Build the operation URL  
var url = "service.svc/ajaxEndpoint/";  
url = url + operation;  
  
// Build the body of the JSON message  
var body = '{"n1":';  
body = body + document.getElementById("num1").value + ',"n2":';  
body = body + document.getElementById("num2").value + '}';  
  
// Send the HTTP request  
xmlHttp.open("POST", url, true);  
xmlHttp.setRequestHeader("Content-type", "application/json");  
xmlHttp.send(body);  
```

 Quando o serviço responde, a resposta é exibida sem nenhum processamento adicional em uma caixa de texto na página. Isso é implementado para fins de demonstração para que você possa observar diretamente os formatos de dados XML e JSON usados.  

```javascript
// Create result handler   
xmlHttp.onreadystatechange=function(){  
     if(xmlHttp.readyState == 4){  
          document.getElementById("result").value = xmlHttp.responseText;  
     }  
}  
```

> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\AJAX\XmlAjaxService`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Compile a solução XmlAjaxService.sln, conforme descrito em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Navegue até http://localhost/ServiceModelSamples/XmlAjaxClientPage.htm (não abrir XmlAjaxClientPage.htm no navegador do diretório do projeto).  
  
## <a name="see-also"></a>Consulte também  
 [Serviço AJAX utilizando HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md)
