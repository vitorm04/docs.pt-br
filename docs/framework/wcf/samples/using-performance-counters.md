---
title: Utilizando contadores de desempenho
ms.date: 03/30/2017
ms.assetid: 00a787af-1876-473c-a48d-f52b51e28a3f
ms.openlocfilehash: 7ffd9f5de5efb4be22968958246839e804daf23d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143571"
---
# <a name="using-performance-counters"></a>Utilizando contadores de desempenho
Esta amostra demonstra como acessar os contadores de desempenho da Windows Communication Foundation (WCF) e como criar contadores de desempenho definidos pelo usuário. Esta amostra é baseada no [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).  
  
> [!NOTE]
> O procedimento de configuração e as instruções de construção desta amostra estão localizados no final deste tópico.  
  
 Nesta amostra, o cliente chama os `ICalculator` quatro métodos do serviço. O cliente continua fazendo isso até que seja interrompido pelo usuário. O serviço permanece inalterado.  
  
 Os contadores de desempenho estão habilitados na seção de diagnóstico do arquivo Web.config para o serviço, conforme mostrado na configuração da amostra a seguir.  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <diagnostics performanceCounters="All" />
  </system.serviceModel>  
</configuration>  
```  
  
 Essa tarefa também pode ser feita usando a [Ferramenta de Editor de Configuração (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).  
  
 Quando os contadores de desempenho são ativados, todo o conjunto de contadores de desempenho WCF está habilitado para o serviço. O .NET Framework mantém automaticamente os `ServiceModelService` `ServiceModelEndpoint` dados `ServiceModelOperation`de desempenho em três níveis: e . Cada um desses níveis tem contadores de desempenho como "Chamadas", "Chamadas por Segundo" e "Chamadas de Segurança Não Autorizadas".  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Para construir a edição C# ou Visual Basic .NET da solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Para executar a amostra em uma configuração de computador único ou cruzado, siga as instruções em [Executar as amostras da Fundação](../../../../docs/framework/wcf/samples/running-the-samples.md)de Comunicação do Windows .  
  
### <a name="to-view-performance-data"></a>Para exibir dados de desempenho  
  
1. Inicie a ferramenta Monitor de Desempenho clicando `perfmon` em **Iniciar**, **Executar...**, digite e clique em **OK,** ou no Painel de Controle, selecione **Ferramentas Administrativas** e clique duas vezes em **Desempenho**.  
  
    > [!NOTE]
    > Você não pode adicionar contadores até que o código de amostra esteja em execução.  
  
2. Remova os contadores de desempenho listados selecionando-os e pressionando a tecla Excluir.  
  
3. Adicione contadores WCF clicando com o botão direito do mouse no painel de gráficos e selecionando **Add Counters**. Na caixa de diálogo **Adicionar contadores,** selecione **ServiceModelOperação 3.0.0.0, ServiceModelEndpoint 3.0.0.0 ou ServiceModelService 3.0.0.0** na caixa de lista de lista sosseleta do objeto Desempenho. Selecione os contadores que deseja exibir na lista.  
  
    > [!NOTE]
    > Não há contadores de desempenho WCF para um serviço se não houver serviços WCF em execução no computador.  
  
### <a name="to-use-the-configuration-editor-to-enable-counters"></a>Para usar o Editor de configuração para ativar contadores  
  
1. Abra uma instância do SvcConfigEditor.exe.  
  
2. No menu Arquivo, clique em **Abrir** e clique em **Config file...**.  
  
3. Navegue até a pasta de serviço do aplicativo de exemplo e abra o arquivo Web.config.  
  
4. Clique em **Diagnósticos** na árvore Configuração.  
  
5. Alternar **contador de desempenho** na janela **Diagnósticos** para mostrar 'Todos'.  
  
6. Salve o arquivo de configuração e saia do editor.  
  
> [!IMPORTANT]
> Os exemplos podem mais ser instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation). Este exemplo está localizado no seguinte diretório.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\PerfCounters`  
  
## <a name="see-also"></a>Confira também

- [AppFabric que monitora Exemplos](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))
