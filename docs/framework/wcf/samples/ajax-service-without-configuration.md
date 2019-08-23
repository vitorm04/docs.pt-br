---
title: Serviço AJAX sem configuração
ms.date: 03/30/2017
ms.assetid: e6db7acd-5679-45d4-b98a-8449c6873838
ms.openlocfilehash: 24f07193b955e2b4877ac2e9302a7be0cd879676
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913353"
---
# <a name="ajax-service-without-configuration"></a>Serviço AJAX sem configuração
Este exemplo demonstra como usar o Windows Communication Foundation (WCF) para criar um serviço básico de JavaScript e XML (AJAX) ASP.NET assíncrono (um serviço que você pode acessar usando o código JavaScript de um cliente de navegador da Web) sem usar nenhuma configuração Configurações. O serviço usa uma sintaxe especial no arquivo. svc para habilitar automaticamente um ponto de extremidade AJAX.  
  
 O suporte ao AJAX no WCF é otimizado para uso com o `ScriptManager` ASP.NET AJAX por meio do controle. Para obter um exemplo de como usar o WCF com o ASP.NET AJAX, consulte os [exemplos do AJAX](ajax.md).  
  
> [!NOTE]
> O procedimento de instalação e as instruções de Build para este exemplo estão localizados no final deste tópico.  
  
 Este exemplo baseia-se no serviço AJAX usando HTTP POST. Conforme descrito no exemplo [básico de serviço AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md) , <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> é usado para hospedar o serviço.  

```svc
<%ServiceHost  
    language=c#  
    Debug="true"  
    Service="Microsoft.Ajax.Samples.CalculatorService  
    Factory="System.ServiceModel.Activation.WebScriptServiceHostFactory"  
%>  
```

 <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>adiciona automaticamente um <xref:System.ServiceModel.Description.WebScriptEndpoint> ao serviço. Se nenhuma alteração de configuração precisar ser feita no ponto de extremidade, `<system.ServiceModel>` a seção poderá ser completamente removida do arquivo Web. config para o serviço. O arquivo Web. config contém algumas configurações de ASP.NET, que são usadas pelo ConfigFreeClientPage. aspx. Se esse não for o caso, todo o arquivo Web. config poderá ser removido.  
  
> [!IMPORTANT]
>  Os exemplos podem mais ser instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) [!INCLUDE[wf1](../../../../includes/wf1-md.md)] e exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\ConfigFreeAjaxService`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Certifique-se de executar as instruções de instalação no [procedimento de configuração única para os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Crie a solução ConfigFreeAjaxService. sln, conforme descrito em [criando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Navegue até `http://localhost/ServiceModelSamples/ConfigFreeClientPage.aspx` (não abra ConfigFreeClientPage. aspx no navegador de dentro do diretório do projeto).  
  
> [!NOTE]
> Ao executar este exemplo, verifique se a autenticação anônima e a autenticação do Windows não estão habilitadas simultaneamente para a pasta ServiceModelSamples no IIS. Se esse for o caso, desabilite a autenticação do Windows. Depois de executar o exemplo, habilite a autenticação do Windows e execute "iisreset".  
  
## <a name="see-also"></a>Consulte também

- [Serviço AJAX básico](../../../../docs/framework/wcf/samples/basic-ajax-service.md)
