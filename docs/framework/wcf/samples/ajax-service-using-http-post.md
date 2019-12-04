---
title: Serviço AJAX utilizando HTTP POST
ms.date: 03/30/2017
ms.assetid: 1ac80f20-ac1c-4ed1-9850-7e49569ff44e
ms.openlocfilehash: 560739c576965d597010a6885b53c7905aaeb8e7
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716189"
---
# <a name="ajax-service-using-http-post"></a>Serviço AJAX utilizando HTTP POST

Este exemplo demonstra como usar o Windows Communication Foundation (WCF) para criar um serviço de JavaScript e XML (AJAX) assíncrono do ASP.NET que usa HTTP POST. Um serviço AJAX é aquele que você pode acessar usando o código básico do JavaScript de um cliente de navegador da Web. Este exemplo baseia-se no exemplo [básico de serviço AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md) ; a única diferença entre os dois exemplos é o uso de HTTP POST em vez de HTTP GET.

O suporte ao AJAX no Windows Communication Foundation (WCF) é otimizado para uso com o ASP.NET AJAX por meio do controle de `ScriptManager`. Para obter um exemplo de como usar o WCF com o ASP.NET AJAX, consulte os [exemplos do AJAX](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).

> [!NOTE]
> O procedimento de instalação e as instruções de Build para este exemplo estão localizados no final deste tópico.

O serviço no exemplo a seguir é um serviço WCF sem código específico do AJAX.

Se o atributo <xref:System.ServiceModel.Web.WebInvokeAttribute> for aplicado em uma operação ou o atributo <xref:System.ServiceModel.Web.WebGetAttribute> não for aplicado, o verbo HTTP padrão ("POST") será usado. Solicitações POST são mais difíceis de construir que solicitações GET, mas não são armazenadas em cache; Use solicitações POST para todas as operações em que o Caching não é apropriado.

```csharp
[ServiceContract(Namespace = "PostAjaxService")]
public interface ICalculator
{
    [WebInvoke]
    double Add(double n1, double n2);
    //Other operations omitted…
}
```

Crie um ponto de extremidade AJAX no serviço usando o <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, assim como no exemplo de serviço básico AJAX.

Ao contrário das solicitações GET, não é possível invocar serviços POST do navegador. Por exemplo, navegar até `http://localhost/ServiceModelSamples/service.svc/Add?n1=100&n2=200` resulta em um erro, pois o serviço de POSTAgem espera que os parâmetros `n1` e `n2` sejam enviados no corpo da mensagem no formato JSON, e não na URL.

A página da Web do cliente PostAjaxClientPage. aspx contém o código ASP.NET para invocar o serviço sempre que o usuário clicar em um dos botões de operação na página. O serviço responde da mesma maneira que no exemplo de [serviço AJAX básico](../../../../docs/framework/wcf/samples/basic-ajax-service.md) , com a solicitação get.

> [!IMPORTANT]
> Os exemplos podem mais ser instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] amostras. Este exemplo está localizado no seguinte diretório.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\PostAjaxService`

## <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo

1. Certifique-se de executar as instruções de instalação do [procedimento de configuração única para os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).

2. Crie a solução PostAjaxService. sln, conforme descrito em [criando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).

3. Navegue até `http://localhost/ServiceModelSamples/PostAjaxClientPage.aspx` (não abra PostAjaxClientPage. aspx no navegador do diretório do projeto).
