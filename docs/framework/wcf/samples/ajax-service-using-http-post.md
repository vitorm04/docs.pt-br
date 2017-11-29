---
title: "Serviço AJAX utilizando HTTP POST"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1ac80f20-ac1c-4ed1-9850-7e49569ff44e
caps.latest.revision: "28"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 004bb41ad1662ddd6518c25acc1cac36dda3339c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="ajax-service-using-http-post"></a>Serviço AJAX utilizando HTTP POST
Este exemplo demonstra como usar [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] para criar um [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] serviço JavaScript assíncrono e XML (AJAX) que usa o HTTP POST. Um serviço de AJAX é aquele que você pode acessar usando o código JavaScript básico de um cliente de navegador da Web. Este exemplo se baseia o [serviço AJAX básico](../../../../docs/framework/wcf/samples/basic-ajax-service.md) exemplo; a única diferença entre os dois exemplos é o uso de HTTP POST em vez de HTTP GET.  
  
 Suporte do AJAX no [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] é otimizado para uso com o ASP.NET AJAX por meio de `ScriptManager` controle. Para obter um exemplo do uso de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] com o ASP.NET AJAX, consulte o [Ajax exemplos](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).  
  
> [!NOTE]
>  As instruções de procedimento e a compilação de configuração para este exemplo estão localizadas no final deste tópico.  
  
 O serviço no exemplo a seguir está uma [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço sem nenhum código específico do AJAX.  
  
 Se o <xref:System.ServiceModel.Web.WebInvokeAttribute> atributo é aplicado em uma operação, ou o <xref:System.ServiceModel.Web.WebGetAttribute> atributo não é aplicado, o verbo HTTP padrão ("POST") é usado. As solicitações POST são mais difíceis de construir que as solicitações GET, mas eles não estão em cache; Use solicitações POST para todas as operações em que o cache não é apropriado.  
  
```  
[ServiceContract(Namespace = "PostAjaxService")]  
    public interface ICalculator  
    {        [WebInvoke]  
        double Add(double n1, double n2);  
        //Other operations omitted…  
    }  
```  
  
 Crie um ponto de extremidade do AJAX no serviço usando o <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, assim como o exemplo de serviço AJAX básico.  
  
 Ao contrário das solicitações GET, você não pode invocar serviços POST do navegador. Por exemplo, navegando para http://localhost/ServiceModelSamples/service.svc/Add?n1=100&n2=200 resulta em um erro, porque o serviço de POSTAGEM espera o `n1` e `n2` parâmetros para ser enviados no corpo da mensagem, no formato JSON — e não na URL.  
  
 O cliente PostAjaxClientPage.aspx de página da Web contém código para chamar o serviço sempre que o usuário clica em um dos botões de operação na página do ASP.NET. O serviço responde da mesma maneira como no [serviço AJAX básico](../../../../docs/framework/wcf/samples/basic-ajax-service.md) exemplo, com a solicitação de obtenção.  
  
> [!IMPORTANT]
>  Os exemplos podem mais ser instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\PostAjaxService`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Certifique-se de que você execute as instruções de instalação [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Compile a solução PostAjaxService.sln conforme descrito em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Navegue até http://localhost/ServiceModelSamples/PostAjaxClientPage.aspx (não abrir PostAjaxClientPage.aspx no navegador do diretório do projeto).  
  
## <a name="see-also"></a>Consulte também
