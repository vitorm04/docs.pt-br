---
title: Como habilitar o rastreamento do WIF
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 271b6889-3454-46ff-96ab-9feb15e742ee
caps.latest.revision: "3"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 516e065bc360538e7b62807a5492c0c6c9d16e69
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-enable-wif-tracing"></a>Como habilitar o rastreamento do WIF
## <a name="applies-to"></a>Aplica-se a  
  
-   Microsoft® Windows® Identity Foundation (WIF)  
  
-   Web Forms do ASP.NET®  
  
## <a name="summary"></a>Resumo  
 Estas instruções fornecem procedimentos passo a passo detalhados para habilitar o rastreamento do WIF em um aplicativo ASP.NET. Elas também fornecem instruções para testar o aplicativo para verificar se o ouvinte de rastreamento e o registro estão funcionando corretamente. Essas instruções não têm tópicos de explicações detalhados para criar um STS (Serviço de Token de Segurança), e usa o STS de Desenvolvimento que vem com a Ferramenta de Identidade e Acesso. O STS de Desenvolvimento não efetua a autenticação real e destina-se somente a testes. Você precisará instalar a Ferramenta de Identidade e Acesso para concluir estas instruções. O download pode ser feito na seguinte localização: [Ferramenta de Identidade e Acesso](http://go.microsoft.com/fwlink/?LinkID=245849)  
  
> [!IMPORTANT]
>  Habilitar o rastreamento do WIF para aplicações passivas, ou seja, aplicativos que usam o protocolo Web Services Federation, pode expor o aplicativo a ataques de DoS (negação de serviço) ou à divulgação de informações para uma terceira parte mal-intencionada. Isso inclui RPs passivos e STSes passivos. Por esse motivo, é recomendável que você não habilite o rastreamento do WIF para RPs passivos ou STSes em um ambiente de produção.  
  
## <a name="contents"></a>Conteúdo  
  
-   Objetivos  
  
-   Visão Geral  
  
-   Resumo das etapas  
  
-   Etapa 1 – criar um aplicativo ASP.NET Web Forms simples e habilitar o rastreamento  
  
-   Etapa 2 – testar sua solução  
  
## <a name="objectives"></a>Objetivos  
  
-   Criar um aplicativo simples do ASP.NET que usa o WIF e o STS de desenvolvimento por meio da ferramenta de identidade e acesso  
  
-   Habilitar o rastreamento e verificar se ele está funcionando  
  
## <a name="overview"></a>Visão Geral  
 O rastreamento permite depurar e solucionar problemas de vários tipos de problemas com o WIF, incluindo tokens, cookies, declarações, mensagens de protocolo e muito mais. O rastreamento do WIF é semelhante ao rastreamento do WCF; por exemplo, você pode escolher o detalhamento dos rastreamentos para exibir tudo, desde mensagens críticas até todas as mensagens. Os rastreamentos do WIF podem ser gerados em arquivos **.xml** ou em arquivos **.svclog** que podem ser exibidos usando a ferramenta Visualizador de Rastreamento de Serviço. Essa ferramenta está localizada no diretório **bin** do caminho de instalação do SDK do Windows no seu computador, por exemplo: **C:\Program Files\Microsoft SDKs\Windows\v7.1\Bin\SvcTraceViewer.exe**.  
  
## <a name="summary-of-steps"></a>Resumo das etapas  
  
-   Etapa 1 – criar um aplicativo ASP.NET Web Forms simples e habilitar o rastreamento  
  
-   Etapa 2 – testar sua solução  
  
## <a name="step-1--create-a-simple-aspnet-web-forms-application-and-enable-tracing"></a>Etapa 1 – criar um aplicativo ASP.NET Web Forms simples e habilitar o rastreamento  
 Nesta etapa, você criará um novo aplicativo ASP.NET Web Forms e modificará o arquivo *Web.config* para habilitar o rastreamento.  
  
#### <a name="to-create-a-simple-aspnet-application"></a>Para criar um aplicativo ASP.NET simples  
  
1.  Inicie o Visual Studio, clique em **Arquivo**, **Novo** e, depois, em **Projeto**.  
  
2.  Na janela **Novo Projeto**, clique em **Aplicativo ASP.NET Web Forms**.  
  
3.  Em **Nome**, insira `TestApp` e pressione **OK**.  
  
4.  Clique com o botão direito do mouse no projeto **TestApp** em **Gerenciador de Soluções** e selecione **Identidade e Acesso**.  
  
5.  A janela **Identidade e Acesso** é exibida. Em **Provedores**, selecione **Testar o aplicativo com o STS de Desenvolvimento Local** e clique em **Aplicar**.  
  
6.  Crie uma nova pasta chamada **logs** na raiz da unidade **C:**, conforme mostrado: **C:\logs**  
  
7.  Adicione o elemento **\<System.Diagnostics>** a seguir para o arquivo de configuração *Web.config* imediatamente após o fechamento do elemento **\</configSections>**, conforme mostrado:  
  
    ```xml  
    <configuration>  
        <configSections>  
        …  
        </configSections>  
        <system.diagnostics>  
            <sources>  
                <source name="System.IdentityModel" switchValue="Verbose">  
                    <listeners>  
                        <add name="xml" type="System.Diagnostics.XmlWriterTraceListener" initializeData="C:\logs\WIF.xml" />  
                    </listeners>  
                </source>  
            </sources>  
            <trace autoflush="true" />  
        </system.diagnostics>  
    ```  
  
    > [!NOTE]
    >  O local do diretório especificado no atributo **initializeData** deve existir antes que o registro em log possa começar. Se o local não existir, nenhum log será criado.  
  
     As configurações acima habilitarão o rastreamento **Detalhado** do WIF e salvarão o log resultante para o arquivo **C:\logsWIF.xml**.  
  
## <a name="step-2--test-your-solution"></a>Etapa 2 – testar sua solução  
 Nesta etapa, você testará seu aplicativo ASP.NET habilitado para WIF para verificar se os logs estão sendo registrados.  
  
#### <a name="to-test-your-wif-enabled-aspnet-application-for-successful-tracing"></a>Para testar seu aplicativo ASP.NET habilitado para WIF visando um rastreamento bem-sucedido  
  
1.  Execute a solução pressionando a tecla **F5**. A Home Page ASP.NET padrão deverá ser apresentada a você e você deverá ser autenticado automaticamente com o nome de usuário *Terry*, que é o usuário padrão que é retornado pelo STS de desenvolvimento.  
  
2.  Feche a janela do navegador e, em seguida, navegue até a pasta **C:\logs**. Abra o arquivo **C:\logs\WIF.xml** usando um editor de texto.  
  
3.  Inspecione o arquivo **WIF.xml** e verifique se ele contém entradas começando com **\<E2ETraceEvent>**. Esses rastreamentos conterão elementos **\<TraceRecord>** com descrições para a atividade rastreada, tais como **Validando SecurityToken**.
