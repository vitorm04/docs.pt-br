---
title: "Serviço de AJAX com exemplo de JSON e XML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8ea5860d-0c42-4ae9-941a-e07efdd8e29c
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 665e05907f837887a7dd0375e540b6e9167a820e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ajax-service-with-json-and-xml-sample"></a>Serviço de AJAX com exemplo de JSON e XML
Este exemplo demonstra como usar [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] para criar um serviço assíncrona AJAX JavaScript and XML () que retorna dados JSON JavaScript Object Notation () ou XML. Você pode acessar um serviço de AJAX usando código JavaScript de um cliente de navegador da Web. Este exemplo se baseia o [serviço AJAX básico](../../../../docs/framework/wcf/samples/basic-ajax-service.md) exemplo.  
  
 Ao contrário de outros exemplos de AJAX, este exemplo não usa o ASP.NET AJAX e o <xref:System.Web.UI.ScriptManager> controle. Com alguma configuração adicional, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] AJAX serviços podem ser acessados de qualquer página HTML por meio de JavaScript, e esse cenário é mostrado aqui. Para obter um exemplo do uso de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] com o ASP.NET AJAX, consulte [AJAX exemplos](http://msdn.microsoft.com/en-us/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e).  
  
 Este exemplo mostra como alternar o tipo de resposta de uma operação entre JSON e XML. Essa funcionalidade está disponível, independentemente se o serviço está configurado para ser acessado por ASP.NET AJAX ou por uma página de cliente HTML/JavaScript.  
  
> [!NOTE]
>  As instruções de procedimento e a compilação de configuração para este exemplo estão localizadas no final deste tópico.  
  
 Para habilitar o uso de clientes não - ASP.NET AJAX, use <xref:System.ServiceModel.Activation.WebServiceHostFactory> (não <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>) no arquivo. svc. <xref:System.ServiceModel.Activation.WebServiceHostFactory>Adiciona um <xref:System.ServiceModel.Description.WebHttpEndpoint> ponto de extremidade padrão para o serviço. O ponto de extremidade é configurado em um endereço vazio em relação ao arquivo. svc; Isso significa que o endereço do serviço é http://localhost/ServiceModelSamples/service.svc com nenhuma sufixos adicionais que não seja o nome da operação.  
  
```html  
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
  
 Os dados padrão de formato para <xref:System.ServiceModel.Description.WebHttpEndpoint> for XML, enquanto o formato de dados padrão para <xref:System.ServiceModel.Description.WebScriptEndpoint> é JSON. Para obter mais informações, consulte [criar serviços do WCF AJAX sem ASP.NET](../../../../docs/framework/wcf/feature-details/creating-wcf-ajax-services-without-aspnet.md).  
  
 O serviço no exemplo a seguir é um padrão [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço com duas operações. Ambas as operações requerem o <xref:System.ServiceModel.Web.WebMessageBodyStyle.Wrapped> estilo de corpo de <xref:System.ServiceModel.Web.WebGetAttribute> ou <xref:System.ServiceModel.Web.WebInvokeAttribute> atributos, que é específico para o `webHttp` comportamento e não possui a opção de formato de dados JSON/XML.  
  
```  
[OperationContract]  
[WebInvoke(ResponseFormat = WebMessageFormat.Xml, BodyStyle = WebMessageBodyStyle.Wrapped)]  
MathResult DoMathXml(double n1, double n2);  
```  
  
 O formato da resposta para a operação é especificado como XML, que é o padrão definindo para o [ \<webHttp >](../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md) comportamento. No entanto, é recomendável explicitamente especificar o formato da resposta.  
  
 Outra operação usa o `WebInvokeAttribute` de atributo e especifique explicitamente o JSON em vez de XML para a resposta.  
  
```  
[OperationContract]  
[WebInvoke(ResponseFormat = WebMessageFormat.Json, BodyStyle = WebMessageBodyStyle.Wrapped)]  
MathResult DoMathJson(double n1, double n2);  
```  
  
 Observe que, em ambos os casos, as operações retornam um tipo complexo, `MathResult`, que é um padrão [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] tipo de contrato de dados.  
  
 O cliente XmlAjaxClientPage.htm de página da Web contém código JavaScript que invoca uma das duas operações anteriores quando o usuário clica o **cálculos (retorno JSON)** ou **cálculos (retorno XML)**  botões na página. O código para chamar o serviço constrói um corpo JSON e a envia usando HTTP POST. A solicitação é criada manualmente em JavaScript, ao contrário de [serviço AJAX básico](../../../../docs/framework/wcf/samples/basic-ajax-service.md) exemplo e os outros exemplos usando ASP.NET AJAX.  
  
```  
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
  
 Quando o serviço responde, a resposta será exibida sem nenhum processamento adicional em uma caixa de texto na página. Isso é implementado para fins de demonstração permitir que você observar diretamente os formatos de dados XML e JSON usados.  
  
```  
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
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\AJAX\XmlAjaxService`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Compile a solução XmlAjaxService.sln conforme descrito em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Navegue até http://localhost/ServiceModelSamples/XmlAjaxClientPage.htm (não abrir XmlAjaxClientPage.htm no navegador do diretório do projeto).  
  
## <a name="see-also"></a>Consulte também  
 [Serviço AJAX utilizando HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md)
