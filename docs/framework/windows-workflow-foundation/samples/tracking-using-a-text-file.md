---
title: Controlar usando um arquivo de texto
ms.date: 03/30/2017
ms.assetid: 56a82682-73c2-4b91-a206-4d8bb12c561b
ms.openlocfilehash: aa59ab8304c68873c938f42fc585be883b234ecc
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2018
---
# <a name="tracking-using-a-text-file"></a>Controlar usando um arquivo de texto
Este exemplo demonstra como estender o controle no Windows Workflow Foundation (WF), criando um participante personalizado de controle. Os participantes de rastreamento são as classes do.NET Framework que recebem registros de rastreamento em tempo de execução que são emitidas. Você pode criar um participante de controle para transmitir os eventos de rastreamento a qualquer destino é necessário para sua situação. Por exemplo, o participante de rastreamento (ETW de rastreamento do Windows) é fornecido como parte de [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]. O participante de rastreamento neste exemplo grava os registros no formato XML para um arquivo de texto.  
  
## <a name="sample-details"></a>Detalhes de exemplo  
 Para otimizar a utilidade e robustez do seu participante de rastreamento, algumas etapas adicionais devem ser concluídas para conectar corretamente o participante de rastreamento em tempo de execução. A tabela a seguir descreve as classes usadas nesse exemplo para criar um participante de rastreamento que siga as práticas recomendadas.  
  
|Classe|Descrição|  
|-----------|-----------------|  
|`TextFileTrackingExtensionElement`|<xref:System.ServiceModel.Configuration.BehaviorExtensionElement> é usado para definir a seção de configuração usada para configurar o participante de rastreamento do arquivo de texto. Isso permite que os usuários especifiquem o destino do arquivo de log usando arquivos de configuração padrão do .NET Framework.|  
|`TextFileTrackingBehavior`|Comportamentos no WCF permitem aos usuários inserir extensões no tempo de execução. Esse comportamento adicionar o participante de rastreamento para o serviço quando inicia o serviço.|  
|`TextFileTrackingParticipant`|O participante de rastreamento que recebe participantes de rastreamento em tempo de execução e os armazena em um arquivo de log como XML.|  
  
## <a name="behavior-extension-elements-configuration"></a>Configuração de elementos de extensão do comportamento  
 Uma etapa é necessária mais para utilizar o elemento de extensão do comportamento descrito anteriormente usando arquivos de configuração do.NET Framework. A seguinte configuração deve ser colocada em arquivos de configuração onde a extensão deve ser usada.  
  
```xml  
<system.serviceModel>  
    <extensions>  
      <behaviorExtensions>  
        <add name="textFileTracking" type="Microsoft.Samples.TextFileTracking.TextFileTrackingExtensionElement, WFStockPriceApplication, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
      </behaviorExtensions>  
    </extensions>  
…  
  </system.serviceModel>  
```  
  
> [!NOTE]
>  Consulte o exemplo no arquivo web.config para um uso completo do exemplo de configuração dos elementos de extensão do comportamento.  
  
## <a name="custom-tracking-records"></a>Registros de rastreamento personalizadas  
 O arquivo de GetStockPrices.cs demonstra como criar registros personalizados de rastreamento de dentro de <xref:System.Activities.CodeActivity>. Procure esse registro ao executar o exemplo.  
  
#### <a name="to-use-this-sample"></a>Para usar este exemplo  
  
1.  Usando [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], abra o arquivo de solução de WFStockPriceApplication.sln.  
  
2.  Para criar a solução, pressione CTRL+SHIFT+B.  
  
3.  Para executar a solução, pressione CTRL+F5.  
  
     A janela do navegador abre e mostra a listagem de diretório para o aplicativo.  
  
4.  No navegador, clique StockPriceService.xamlx.  
  
5.  O navegador exibe o **StockPriceService** página, que contém o endereço de wsdl do serviço local. Copie este endereço.  
  
     Um exemplo do endereço local de serviço wsdl é http://localhost:53797/StockPriceService.xamlx?wsdl.  
  
6.  Usar [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], vá para a pasta de [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] (a pasta de instalação é %SystemDrive% \ program files \ Microsoft Visual Studio 10.0). Localize o Common7 \ IDE \ subfolder.  
  
7.  Clique duas vezes no arquivo de WcfTestClient.exe para iniciar a Test usuário.  
  
8.  No cliente de teste do WCF, selecione **Adicionar serviço...** do **arquivo** menu.  
  
9. Cole o URL que você copiou apenas na caixa de texto.  
  
10. Clique em **Okey** para fechar a caixa de diálogo.  
  
11. Testar o serviço usando a Test usuário.  
  
    1.  No cliente de teste do WCF, clique duas vezes em **GetStockPrice()** sob o **IStockPriceService** nó.  
  
         O **GetStockPrice()** método aparece no painel direito, com um parâmetro.  
  
    2.  Digite Contoso como o valor para o parâmetro.  
  
    3.  Clique em **invocar**.  
  
12. Consulte os eventos rastreadas no arquivo de log localizado no diretório de dados do aplicativo em %APPDATA% \ trackingRecords.log.  
  
    > [!NOTE]
    >  % APPDATA % é uma variável de ambiente que resolve para %SystemDrive%\Users\\< nome de usuário\>\appdata\roaming. na [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[lserver](../../../../includes/lserver-md.md)], ou Windows Server 2008.  
  
> [!IMPORTANT]
>  Os exemplos podem mais ser instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\TextFileTracking`  
  
## <a name="see-also"></a>Consulte também  
 [Exemplos de monitoramento do AppFabric](http://go.microsoft.com/fwlink/?LinkId=193959)
