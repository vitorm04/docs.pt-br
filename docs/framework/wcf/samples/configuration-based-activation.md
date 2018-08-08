---
title: Ativação com base em configuração
ms.date: 03/30/2017
ms.assetid: 21bb762e-c43e-4b0c-887b-5e434d665838
ms.openlocfilehash: 3ac4edd2a51e4ed8a5c0b7e73d7d1afa31334c33
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33809908"
---
# <a name="configuration-based-activation"></a>Ativação com base em configuração
Este exemplo demonstra como ativar serviços Windows Communication Foundation (WCF) sem a necessidade de um arquivo. svc.  
  
> [!IMPORTANT]
>  Os exemplos podem mais ser instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\ConfigBasedActivation`  
  
## <a name="sample-details"></a>Detalhes de exemplo  
 Neste exemplo, o cliente é o cliente de teste do WCF e o serviço está hospedado no IIS.  
  
> [!NOTE]
>  As instruções de instalação e compilação para este exemplo estão localizadas no final deste tópico.  
  
### <a name="activation-of-services-without-requiring-a-svc-file"></a>Ativação de serviços sem a necessidade de um arquivo. svc  
 Em [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)], um arquivo. svc foi necessário para um serviço de ativação. Isso causa sobrecarga de gerenciamento adicionais, um arquivo adicional foi necessário para ser implantado e mantido junto com o aplicativo. Com o lançamento do [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)], os componentes de ativação podem ser configurados usando o arquivo de configuração do aplicativo.  
  
 [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)] apresenta um novo elemento de configuração (<xref:System.ServiceModel.Configuration.ServiceActivationElement>), além de <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection> do arquivo de configuração do aplicativo. O <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection> coleção aceita uma coleção de serviços para ativar, conforme mostrado no exemplo de código a seguir.  
  
```xml  
<serviceActivations>  
   <add relativeAddress="Calculator.svc" service="Microsoft.ServiceModel.Samples.CalculatorService" />  
  
<serviceActivations>  
```  
  
 Observação a fazer é que a configuração é bem parecida com a configuração de arquivos. svc. É um atributo adicional que é apresentado a `relativeAddress` que fornece o endereço do serviço. O endereço relativo também é o caminho virtual para o serviço. O host recupera o arquivo Web. config do arquivo a partir de `virtualPath` local, se presente; caso contrário, o host pesquisará seu recursivamente da pasta pai.  
  
> [!NOTE]
>  Este exemplo requer a função de hospedagem no IIS.  
  
#### <a name="to-use-this-sample"></a>Para usar este exemplo  
  
1.  Usando [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], abra o arquivo Service.csproj.  
  
2.  Para criar a solução, pressione CTRL+SHIFT+B.  
  
3.  Teste o serviço executando WCFTestClient.exe.  
  
4.  Usando [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], navegue até a pasta de 10.0\Common7\IDE %SystemDrive%\Program Files\Microsoft Visual Studio.  
  
5.  Execução WcfTestClient.exe.  
  
6.  Defina o endereço MEX do serviço.  
  
7.  Pressione CTRL + SHIFT + A para definir o endereço do serviço.  
  
8.  Definir o endereço http://localhost/ServiceModelSamples/Calculator.svc.  
  
9. Executar o `Add` operação. Definir o valor no `n1` parâmetro para o valor 10 e definido no `n2` parâmetro para 15.  
  
10. Pressione **invocar**.  
  
     O resultado esperado é 25.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Para compilar o c# ou Visual Basic .NET edição da solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Após a solução foi criada, execute bat para configurar o aplicativo ServiceModelSamples no IIS. O diretório ServiceModelSamples agora deve aparecer como um aplicativo do IIS.  
  
4.  Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="see-also"></a>Consulte também  
 [Exemplos de persistência e hospedagem de AppFabric](http://go.microsoft.com/fwlink/?LinkId=193961)
