---
title: Serviço AJAX sem configuração
ms.date: 03/30/2017
ms.assetid: e6db7acd-5679-45d4-b98a-8449c6873838
ms.openlocfilehash: f722eac27fadbd772b85a638c3c9171c2783a8b5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54582168"
---
# <a name="ajax-service-without-configuration"></a>Serviço AJAX sem configuração
Este exemplo demonstra como usar o Windows Communication Foundation (WCF) para criar um serviço básico de ASP.NET Asynchronous JavaScript and XML (AJAX) (um serviço que você pode acessar por meio de código JavaScript de um cliente de navegador da Web) sem usar qualquer configuração Configurações. O serviço usa a sintaxe especial no arquivo. svc para habilitar automaticamente um ponto de extremidade do AJAX.  
  
 Suporte a AJAX no WCF é otimizado para uso com o ASP.NET AJAX por meio de `ScriptManager` controle. Para obter um exemplo de como usar o WCF com o ASP.NET AJAX, consulte o [amostras do Ajax](https://msdn.microsoft.com/library/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e).  
  
> [!NOTE]
>  As instruções de procedimento e compilação de configuração para este exemplo estão localizadas no final deste tópico.  
  
 Este exemplo tem como base o serviço AJAX utilizando HTTP POST. Conforme descrito na [serviço básico do AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md) amostra, <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> é usado para hospedar o serviço.  

```svc
<%ServiceHost  
    language=c#  
    Debug="true"  
    Service="Microsoft.Ajax.Samples.CalculatorService  
    Factory="System.ServiceModel.Activation.WebScriptServiceHostFactory"  
%>  
```

 <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> adiciona automaticamente um <xref:System.ServiceModel.Description.WebScriptEndpoint> para o serviço. Se nenhuma alteração de configuração precisa ser feitas para o ponto de extremidade, o `<system.ServiceModel>` seção pode ser completamente removida do arquivo Web. config para o serviço. O arquivo Web. config contém algumas configurações do ASP.NET, que são usadas pelo ConfigFreeClientPage.aspx. Se esse não fosse o caso, todo o arquivo Web. config pode ser removido.  
  
> [!IMPORTANT]
>  Os exemplos podem mais ser instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\ConfigFreeAjaxService`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Certifique-se de que você execute as instruções contidas [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Compile a solução ConfigFreeAjaxService.sln, conforme descrito em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Navegue até `http://localhost/ServiceModelSamples/ConfigFreeClientPage.aspx` (não abrir ConfigFreeClientPage.aspx no navegador de dentro do diretório do projeto).  
  
> [!NOTE]
>  Ao executar este exemplo, certifique-se de que a autenticação anônima e autenticação do Windows não estão habilitados simultaneamente para a pasta ServiceModelSamples no IIS. Se esse for o caso, desabilite a autenticação do Windows. Depois de executar o exemplo, habilitar a autenticação do Windows e execute "iisreset".  
  
## <a name="see-also"></a>Consulte também
- [Serviço AJAX básico](../../../../docs/framework/wcf/samples/basic-ajax-service.md)
