---
title: Utilizando contadores de desempenho
ms.date: 03/30/2017
ms.assetid: 00a787af-1876-473c-a48d-f52b51e28a3f
ms.openlocfilehash: 787a3d08b463980721fb207d029057e14618db5e
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44131877"
---
# <a name="using-performance-counters"></a>Utilizando contadores de desempenho
Este exemplo demonstra como acessar os contadores de desempenho do Windows Communication Foundation (WCF) e como criar contadores de desempenho definidos pelo usuário. Este exemplo se baseia a [Introdução ao](../../../../docs/framework/wcf/samples/getting-started-sample.md).  
  
> [!NOTE]
>  As instruções de procedimento e compilação de configuração para este exemplo estão localizadas no final deste tópico.  
  
 Neste exemplo, o cliente chama os quatro métodos do `ICalculator` service. O cliente continua a fazer isso até que ela seja interrompida pelo usuário. O serviço permanece inalterado.  
  
 Contadores de desempenho estão habilitados na seção de diagnóstico do arquivo Web. config para o serviço, conforme mostrado no seguinte exemplo de configuração.  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <diagnostics performanceCounters="All" />   
  </system.serviceModel>  
</configuration>  
```  
  
 Essa tarefa também pode ser feita usando o [ferramenta de Editor de configuração (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).  
  
 Quando os contadores de desempenho estão habilitados, todo o conjunto de contadores de desempenho do WCF está habilitado para o serviço. O .NET Framework mantém automaticamente os dados de desempenho em três níveis: `ServiceModelService`, `ServiceModelEndpoint` e `ServiceModelOperation`. Cada um desses níveis possui contadores de desempenho como "Chamadas de", "Chamadas por segundo" e "Chamadas de segurança não autorizado".  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Para compilar a edição em C# ou Visual Basic .NET da solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
### <a name="to-view-performance-data"></a>Para exibir dados de desempenho  
  
1.  Inicie a ferramenta Monitor de desempenho clicando **inicie**, **executar...** , insira `perfmon` e clique em **Okey,** ou, no painel de controle, selecione **ferramentas administrativas** e clique duas vezes **desempenho**.  
  
    > [!NOTE]
    >  Não é possível adicionar contadores, até que o código de exemplo está em execução.  
  
2.  Remova os contadores de desempenho que são listados selecionando-os e pressionando a tecla Delete.  
  
3.  Adicionar contadores WCF clicando duas vezes no painel gráfico e selecionando **adicionar contadores**. No **adicionar contadores** caixa de diálogo, selecione **ServiceModelOperation 3.0.0.0, ServiceModelEndpoint 3.0.0.0 ou ServiceModelService 3.0.0.0** no objeto de desempenho caixa suspensa. Selecione os contadores que você deseja exibir na lista.  
  
    > [!NOTE]
    >  Não há nenhum contador de desempenho para um serviço WCF se não houver nenhum serviço WCF em execução no computador.  
  
### <a name="to-use-the-configuration-editor-to-enable-counters"></a>Para usar o Editor de configuração para habilitar os contadores  
  
1.  Abra uma instância da SvcConfigEditor.exe.  
  
2.  No menu Arquivo, clique em **aberto** e, em seguida, clique em **arquivo de configuração...** .  
  
3.  Navegue até a pasta de serviço do aplicativo de exemplo e abra o arquivo Web. config.  
  
4.  Clique em **diagnóstico** na árvore de configuração.  
  
5.  Ativar/desativar **contador de desempenho** na **diagnóstico** janela Mostrar 'Todos'.  
  
6.  Salve o arquivo de configuração e saia do editor.  
  
> [!IMPORTANT]
>  Os exemplos podem mais ser instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\PerfCounters`  
  
## <a name="see-also"></a>Consulte também  
 [AppFabric que monitora exemplos](https://go.microsoft.com/fwlink/?LinkId=193959)
