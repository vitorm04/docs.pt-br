---
title: Utilizando contadores de desempenho
ms.date: 03/30/2017
ms.assetid: 00a787af-1876-473c-a48d-f52b51e28a3f
ms.openlocfilehash: 8784b4a481b8313d370aad1d8f265dcb44ab3ed6
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33807313"
---
# <a name="using-performance-counters"></a>Utilizando contadores de desempenho
Este exemplo demonstra como acessar os contadores de desempenho do Windows Communication Foundation (WCF) e como criar contadores de desempenho definidos pelo usuário. Este exemplo se baseia o [Introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md).  
  
> [!NOTE]
>  As instruções de procedimento e a compilação de configuração para este exemplo estão localizadas no final deste tópico.  
  
 Neste exemplo, o cliente chama os quatro métodos do `ICalculator` service. O cliente continua até que ele seja interrompido pelo usuário. O serviço permanecerá inalterado.  
  
 Contadores de desempenho estão habilitados na seção de diagnóstico do arquivo Web. config para o serviço, conforme mostrado no exemplo de configuração.  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <diagnostics performanceCounters="All" />   
  </system.serviceModel>  
</configuration>  
```  
  
 Essa tarefa também pode ser feita usando o [ferramenta Configuration Editor (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).  
  
 Quando os contadores de desempenho estão habilitados, o conjunto completo de contadores de desempenho do WCF está habilitado para o serviço. O .NET Framework mantém automaticamente os dados de desempenho em três níveis: `ServiceModelService`, `ServiceModelEndpoint` e `ServiceModelOperation`. Cada um desses níveis tem contadores de desempenho, como "chamadas de", "Chamadas por segundo" e "Chamadas de segurança não autorizado".  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Para compilar o c# ou Visual Basic .NET edição da solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
### <a name="to-view-performance-data"></a>Para exibir dados de desempenho  
  
1.  Inicie a ferramenta de Monitor de desempenho clicando **iniciar**, **executar...** , digite `perfmon` e clique em **Okey,** ou, no painel de controle, selecione **ferramentas administrativas** e clique duas vezes em **desempenho**.  
  
    > [!NOTE]
    >  Não é possível adicionar contadores, até que o código de exemplo está em execução.  
  
2.  Remova os contadores de desempenho listados selecionando-os e pressionando a tecla Delete.  
  
3.  Adicionar contadores WCF, clicando duas vezes no painel gráfico e selecionando **adicionar contadores**. No **adicionar contadores** caixa de diálogo, selecione **ServiceModelOperation 3.0.0.0, ServiceModelEndpoint 3.0.0.0 ou ServiceModelService 3.0.0.0** no objeto de desempenho lista caixa suspensa. Selecione os contadores que você deseja exibir na lista.  
  
    > [!NOTE]
    >  Não há nenhum contador de desempenho para um serviço WCF se não houver nenhum serviço WCF em execução no computador.  
  
### <a name="to-use-the-configuration-editor-to-enable-counters"></a>Para usar o Editor de configuração para habilitar os contadores  
  
1.  Abra uma instância do SvcConfigEditor.exe.  
  
2.  No menu Arquivo, clique em **abrir** e, em seguida, clique em **arquivo de configuração...** .  
  
3.  Navegue até a pasta do serviço do aplicativo de exemplo e abra o arquivo Web. config.  
  
4.  Clique em **diagnóstico** na árvore de configuração.  
  
5.  Ativar/desativar **contador de desempenho** no **diagnóstico** janela Mostrar 'Todos'.  
  
6.  Salve o arquivo de configuração e saia do editor.  
  
> [!IMPORTANT]
>  Os exemplos podem mais ser instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\PerfCounters`  
  
## <a name="see-also"></a>Consulte também  
 [Exemplos de monitoramento do AppFabric](http://go.microsoft.com/fwlink/?LinkId=193959)
