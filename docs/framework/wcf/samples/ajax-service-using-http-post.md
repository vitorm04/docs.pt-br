---
title: Serviço AJAX utilizando HTTP POST
ms.date: 03/30/2017
ms.assetid: 1ac80f20-ac1c-4ed1-9850-7e49569ff44e
ms.openlocfilehash: 2fb98e38956719608517caa0e7eeaebd14df8d95
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2019
ms.locfileid: "65882143"
---
# <a name="ajax-service-using-http-post"></a>Serviço AJAX utilizando HTTP POST
Este exemplo demonstra como usar o Windows Communication Foundation (WCF) para criar um serviço ASP.NET Asynchronous JavaScript and XML (AJAX) que usa o HTTP POST. Um serviço AJAX é aquele que você pode acessar usando o código JavaScript básico de um cliente de navegador da Web. Este exemplo se baseia a [serviço de AJAX básico](../../../../docs/framework/wcf/samples/basic-ajax-service.md) exemplo; a única diferença entre os dois exemplos é o uso de HTTP POST em vez de HTTP GET.  
  
 Suporte a AJAX no Windows Communication Foundation (WCF) é otimizado para uso com o ASP.NET AJAX por meio de `ScriptManager` controle. Para obter um exemplo de como usar o WCF com o ASP.NET AJAX, consulte o [amostras do Ajax](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).  
  
> [!NOTE]
>  As instruções de procedimento e compilação de configuração para este exemplo estão localizadas no final deste tópico.  
  
 O serviço no exemplo a seguir é um serviço WCF, sem nenhum código específico do AJAX.  
  
 Se o <xref:System.ServiceModel.Web.WebInvokeAttribute> atributo é aplicado em uma operação, ou o <xref:System.ServiceModel.Web.WebGetAttribute> atributo não for aplicado, o verbo HTTP padrão ("POST") é usado. As solicitações POST são mais difíceis de construir que as solicitações GET, mas eles não estão em cache; Use solicitações POST para todas as operações em que o cache não é apropriado.  

```csharp
[ServiceContract(Namespace = "PostAjaxService")]  
public interface ICalculator  
{
    [WebInvoke]  
    double Add(double n1, double n2);  
    //Other operations omitted…  
}
```

 Criar um ponto de extremidade do AJAX no serviço usando o <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, assim como no exemplo de serviço básico do AJAX.  
  
 Ao contrário de solicitações GET, você não pode chamar serviços POST do navegador. Por exemplo, navegando até `http://localhost/ServiceModelSamples/service.svc/Add?n1=100&n2=200` resulta em um erro, porque o serviço de POSTAGEM espera que o `n1` e `n2` parâmetros a serem enviados no corpo da mensagem no formato JSON e não na URL.  
  
 O cliente PostAjaxClientPage.aspx de página da Web contém código ASP.NET para invocar o serviço sempre que o usuário clica em um dos botões de operação na página. O serviço responde da mesma forma como na [serviço de AJAX básico](../../../../docs/framework/wcf/samples/basic-ajax-service.md) exemplo, com a solicitação GET.  
  
> [!IMPORTANT]
>  Os exemplos podem mais ser instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\PostAjaxService`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Certifique-se de que você execute as instruções de instalação [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Compile a solução PostAjaxService.sln, conforme descrito em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Navegue até `http://localhost/ServiceModelSamples/PostAjaxClientPage.aspx` (não abrir PostAjaxClientPage.aspx no navegador do diretório do projeto).
