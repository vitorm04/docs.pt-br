---
title: 'Como: depurar serviços e aplicativos baseados em declarações usando o rastreamento do WIF'
ms.date: 03/30/2017
ms.assetid: 3d51ba59-3adb-4ca4-bd33-5027531af687
author: BrucePerlerMS
ms.openlocfilehash: effd670a4d0e12f0bca10301fabc361c73e03328
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64625873"
---
# <a name="how-to-debug-claims-aware-applications-and-services-using-wif-tracing"></a>Como: depurar serviços e aplicativos baseados em declarações usando o rastreamento do WIF
## <a name="applies-to"></a>Aplica-se a  
  
- Microsoft® Windows® Identity Foundation (WIF)  
  
- Ferramenta Visualizador de Rastreamento de Serviço (SvcTraceViewer.exe)  
  
- Solução de problemas e depuração de aplicativos do WIF  
  
## <a name="summary"></a>Resumo  
 Estas Instruções descrevem as etapas necessárias para configurar o rastreamento do WIF, coletar logs de rastreamento e analisar os logs de rastreamento usando a ferramenta Visualizador de Rastreamento. Fornecem um mapeamento geral para entradas de rastreamento para as ações necessárias para solucionar problemas relacionados ao WIF.  
  
## <a name="contents"></a>Conteúdo  
  
- Objetivos  
  
- Resumo das etapas  
  
- Etapa 1 – Configurar o rastreamento do WIF usando o arquivo de configuração Web.config  
  
- Etapa 2 – Analisar arquivos de rastreamento do WIF usando a ferramenta Visualizador de Rastreamento  
  
- Etapa 3 – Identificar soluções para corrigir problemas relacionados ao WIF  
  
- Itens relacionados  
  
## <a name="objectives"></a>Objetivos  
  
- Configure o rastreamento do WIF.  
  
- Exiba os logs de rastreamento na ferramenta Visualizador de Rastreamento.  
  
- Identifique problemas relacionados ao WIF nos logs de rastreamento.  
  
- Aplique ações corretivas aos problemas relacionados ao WIF encontrados nos logs de rastreamento.  
  
## <a name="summary-of-steps"></a>Resumo das etapas  
  
- Etapa 1 – Configurar o rastreamento do WIF usando o arquivo de configuração Web.config  
  
- Etapa 2 – Analisar arquivos de rastreamento do WIF usando a ferramenta Visualizador de Rastreamento  
  
- Etapa 3 – Identificar soluções para corrigir problemas relacionados ao WIF  
  
## <a name="step-1--configure-wif-tracing-using-webconfig-configuration-file"></a>Etapa 1 – Configurar o rastreamento do WIF usando o arquivo de configuração Web.config  
 Nesta etapa, você adicionará alterações às seções de configuração no arquivo *Web.config* que permitem que o WIF rastreie seus eventos e armazene-os em um log de rastreamento.  
  
#### <a name="to-configure-wif-tracing-using-webconfig-configuration-file"></a>Para configurar o rastreamento do WIF usando o arquivo de configuração Web.config  
  
1. Abra o arquivo de configuração **Web.config** ou **App.config** raiz no editor do Visual Studio clicando duas vezes nele no **Gerenciador de Soluções**. Se a solução não tiver o arquivo de configuração **Web.config** ou **App.config**, adicione-o clicando com o botão direito do mouse na solução no **Gerenciador de Soluções**, clicando em **Adicionar** e, em seguida, clicando em **Novo Item...**. Na caixa de diálogo **Novo Item**, selecione **Arquivo de Configuração de Aplicativo** para **App.config** ou **Arquivo de Configuração da Web** para **Web.config** na lista e clique em **OK**.  
  
2. Adicione as entradas de configuração semelhantes à seguinte ao arquivo de configuração dentro do nó **\<configuration>** no final do arquivo de configuração:  
  
    ```xml  
    <system.diagnostics>  
        <sources>  
            <source name="System.IdentityModel" switchValue="Verbose">  
                <listeners>  
                    <add name="xml" type="System.Diagnostics.XmlWriterTraceListener" initializeData="WIFTrace.e2e"/>  
                </listeners>  
            </source>  
        </sources>  
        <trace autoflush="true"/>  
    </system.diagnostics>  
    ```  
  
3. A configuração acima instrui o WIF a gerar eventos de rastreamento detalhados e registrá-los no arquivo *WIFTrace.e2e*. Para obter uma lista completa de valores para o **switchValue** switch, consulte a tabela de nível de rastreamento encontrada no seguinte tópico: [Configurando o rastreamento](../wcf/diagnostics/tracing/configuring-tracing.md).  
  
## <a name="step-2--analyze-wif-trace-files-using-trace-viewer-tool"></a>Etapa 2 – Analisar arquivos de rastreamento do WIF usando a ferramenta Visualizador de Rastreamento  
 Nesta etapa, você usará a ferramenta Visualizador de Rastreamento (SvcTraceViewer.exe) para analisar os logs de rastreamento do WIF.  
  
#### <a name="to-analyze-wif-trace-logs-using-trace-viewer-tool-svctraceviewerexe"></a>Para analisar os logs de rastreamento do WIF usando a ferramenta Visualizador de Rastreamento (SvcTraceViewer.exe)  
  
1. A ferramenta Visualizador de Rastreamento (SvcTraceViewer.exe) é fornecida como parte do SDK do Windows. Se você ainda não tiver instalado o SDK do Windows, você pode baixá-lo aqui: [Windows SDK](https://www.microsoft.com/download/en/details.aspx?id=8279).  
  
2. Execute a ferramenta Visualizador de Rastreamento (SvcTraceViewer.exe). Normalmente, ele está disponível na pasta **Bin** do caminho de instalação.  
  
3. Abra o arquivo de log de rastreamento do WIF, por exemplo, WIFTrace.e2e, selecionando a opção **Arquivo**, **Abrir...** no menu ou usando o atalho **Ctrl+O**. O arquivo de log de rastreamento é aberto na ferramenta Visualizador de Rastreamento.  
  
4. Examine as entradas na guia **Atividade**. Cada entrada deve conter um número de atividade, o número de rastreamentos registrados, a duração da atividade e seus carimbos de data/hora de início e término.  
  
5. Clique na guia **Atividade**. Você deverá ver entradas de rastreamento detalhadas na área principal da ferramenta. Use o **nível** lista suspensa no menu para filtrar um nível específico de rastreamentos, por exemplo: **Todos os**, **aviso**, **erros**, **informações**, etc.  
  
6. Clique nas entradas de rastreamento específicas para examinar os detalhes na área inferior da ferramenta. Os detalhes podem ser exibidos usando a exibição **Formatado** e **XML**, escolhendo as guias correspondentes.  
  
## <a name="step-3--identify-solutions-to-fix-wif-related-issues"></a>Etapa 3 – Identificar soluções para corrigir problemas relacionados ao WIF  
 Nesta etapa, você pode identificar soluções para problemas relacionados ao WIF identificados usando o log de rastreamento do WIF e a ferramenta Visualizador de Rastreamento. Elas descreve o mapeamento geral de exceções relacionadas ao WIF para possíveis soluções ou as ações necessárias para solucionar o problema.  
  
#### <a name="to-identify-solutions-to-fix-wif-related-issues"></a>Para identificar soluções para corrigir problemas relacionados ao WIF  
  
1. Examine a tabela a seguir de exceções do WIF e as ações necessárias para corrigir os problemas.  
  
|**ID de erro**|**Mensagem de erro**|**Ação necessária para corrigir o erro**|  
|-|-|-|  
|ID4175|O emissor do token de segurança não foi reconhecido pelo IssuerNameRegistry.  Para aceitar tokens de segurança desse emissor, configure o IssuerNameRegistry para retornar um nome válido para esse emissor.|Esse erro pode ser causado pela ação de copiar uma impressão digital do snap-in do MMC e colá-la no arquivo *Web.config*. Especificamente, você pode obter um caractere extra não imprimível na cadeia de texto ao copiar da janela de propriedades do certificado. Esse caractere extra faz com que a correspondência da impressão digital falhe. O procedimento para copiar corretamente a impressão digital pode ser encontrado em [logon único baseado em declarações-para a Web e o Microsoft Azure](https://docs.microsoft.com/previous-versions/msp-n-p/ff359102%28v=pandp.10%29).|  
  
## <a name="related-items"></a>Itens relacionados  
  
- [Usando o Visualizador de Rastreamento de Serviço para exibir rastreamentos correlacionados e solucionar problemas](../wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)
