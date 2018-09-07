---
title: Ferramenta Visualizador de Rastreamento de Serviço (SvcTraceViewer.exe)
ms.date: 03/30/2017
ms.assetid: 9027efd3-df8d-47ed-8bcd-f53d55ed803c
ms.openlocfilehash: a03c459355f18ad30849113f353e35e97b6141ae
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "44048345"
---
# <a name="service-trace-viewer-tool-svctraceviewerexe"></a>Ferramenta Visualizador de Rastreamento de Serviço (SvcTraceViewer.exe)
Ferramenta de Visualizador de rastreamento de serviço do Windows Communication Foundation (WCF) ajuda você a analisar rastreamentos de diagnóstico que são gerados pelo WCF. Visualizador de rastreamento de serviço fornece uma maneira de mesclar facilmente, exibir e filtrar as mensagens de rastreamento no log de forma que você possa diagnosticar, reparar e verificar problemas de serviço do WCF.  
  
## <a name="configuring-tracing"></a>Configurando o rastreamento  
 Os rastreamentos de diagnóstico fornecem informações que mostram o que está acontecendo em toda a operação do seu aplicativo. Como o nome indica, você pode seguir as operações da origem ao destino, passando pelos pontos intermediários.  
  
 Você pode configurar o rastreamento usando o arquivo de configuração do aplicativo — o Web. config para aplicativos hospedados na Web, ou *Appname*. config para aplicativos auto-hospedados. A seguir está um exemplo:  
  
```xml  
<system.diagnostics>  
    <trace autoflush="true" />  
    <sources>  
            <source name="System.ServiceModel"   
                    switchValue="Information, ActivityTracing"  
                    propagateActivity="true">  
            <listeners>  
               <add name="sdt"   
                   type="System.Diagnostics.XmlWriterTraceListener"   
                   initializeData= "SdrConfigExample.e2e" />  
            </listeners>  
         </source>  
    </sources>  
</system.diagnostics>  
```  
  
 Nesse exemplo, o nome e o tipo do ouvinte de rastreamento são especificados. O ouvinte se chama `sdt`, e o ouvinte de rastreamento do .NET Framework padrão (System.Diagnostics.XmlWriterTraceListener) é adicionado como o tipo. O `initializeData` atributo é usado para definir o nome do arquivo de log para esse ouvinte ser `SdrConfigExample.e2e`. Para o arquivo de log, você pode substituir um nome de arquivo simples por um caminho totalmente qualificado.  
  
 O exemplo cria um arquivo no diretório raiz chamado SdrConfigExample.e2e. Quando você usa o Visualizador de rastreamento para abrir o arquivo, conforme descrito na seção "Abrindo e exibindo WCF arquivos de rastreamento", você pode ver todas as mensagens que foram enviadas.  
  
 O nível de rastreamento é controlado pela configuração `switchValue`. Os níveis de rastreamento disponíveis são descritos na tabela a seguir.  
  
|Nível de rastreamento:|Descrição|  
|-----------------|-----------------|  
|Crítico|-Registra em log entradas Fail-Fast e Log de eventos e informações de correlação de rastreamento. A seguir estão alguns exemplos de quando você poderá usar o nível Crítico:<br />-O AppDomain foi desativado devido a uma exceção sem tratamento.<br />-Seu aplicativo falha ao iniciar.<br />-A mensagem que causou a falha do processo MyApp.exe foi originada.|  
|Erro|-Registra em log todas as exceções. Você pode usar o nível Erro nas seguintes situações:<br />-Seu código falhou devido a uma exceção de conversão inválido.<br />-Uma exceção "Falha ao criar o ponto de extremidade" está causando a falha na inicialização do seu aplicativo.|  
|Aviso|-Existe uma condição que poderá resultar em um erro ou falha crítica. Você pode usar este nível nas seguintes situações:<br />-O aplicativo está recebendo mais solicitações que permite que suas configurações de limitação.<br />-A fila de recebimento está com 98% de sua capacidade configurada.|  
|Informações|-Mensagens úteis para monitorar e diagnosticar o status do sistema, medir o desempenho ou criação de perfil são geradas. É possível utilizar essas informações para o planejamento de capacidade e o gerenciamento de desempenho. Você pode usar este nível nas seguintes situações:<br />-Falha depois que a mensagem chegou ao AppDomain e foi desserializada.<br />-Uma falha ocorreu enquanto a associação HTTP estava sendo criada.|  
|Detalhado|Nível de depuração de rastreamento de código de usuário e de manutenção. Defina este nível quando:<br />-Você não tiver certeza qual método em seu código foi chamado quando a falha ocorreu.<br />-Você tem um ponto de extremidade incorreto configurado e o serviço falhou ao iniciar porque a entrada no repositório de reserva está bloqueada.|  
|ActivityTracing|Eventos de fluxo entre atividades de processamento e componentes.<br /><br /> Este nível permite que os administradores e desenvolvedores correlacionem aplicativos no mesmo domínio de aplicativos.<br /><br /> -Rastreamentos de limites de atividades: iniciar/parar.<br />-Rastreamentos de transferências.|  
  
 Você pode usar `add` para especificar o nome e o tipo do ouvinte de rastreamento que deseja usar. Na configuração de exemplo, o ouvinte é chamado de `sdt` e o ouvinte de rastreamento do .NET Framework padrão (`System.Diagnostics.XmlWriterTraceListener`) é adicionado como o tipo. Use `initializeData` para definir o nome do arquivo de log para esse ouvinte. Além disso, é possível substituir um nome de arquivo simples por um caminho totalmente qualificado.  
  
## <a name="using-the-service-trace-viewer-tool"></a>Usando a ferramenta Visualizador de Rastreamento de Serviço  
  
### <a name="opening-and-viewing-wcf-trace-files"></a>Abrindo e exibindo arquivos de rastreamento do WCF  
 O Visualizador de Rastreamento de Serviço oferece suporte a três tipos de arquivos:  
  
-   O arquivo (. svclog) de rastreamento do WCF  
  
-   Arquivo de rastreamento de eventos (.etl)  
  
-   Arquivo de rastreamento Crimson  
  
 O Visualizador de Rastreamento de Serviço permite que você abra qualquer arquivo de rastreamento com suporte, adicione e integre arquivos de rastreamento adicionais, ou abra e mescle um grupo de arquivos de rastreamento simultaneamente.  
  
##### <a name="to-open-a-trace-file"></a>Para abrir um arquivo de rastreamento  
  
1.  Iniciar o Visualizador de rastreamento de serviço usando uma janela de comando, navegue até o local de instalação do WCF (C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin) e, em seguida, digite `SvcTraceViewer.exe`.  
  
> [!NOTE]
>  A ferramenta Visualizador de Rastreamento de Serviço pode se associar a dois tipos de arquivos: .svclog e .stvproj. Você pode usar dois parâmetros na linha de comando para registrar e cancelar o registro das extensões de arquivo.  
>   
>  /register: registra a associação de extensões de arquivo ".svclog" e ".stvproj" com SvcTraceViewer.exe  
>   
>  /unregister: cancela o registro da associação de extensões de arquivo ".svclog" e ".stvproj" com SvcTraceViewer.exe  
  
1.  Quando o Visualizador de rastreamento de serviço é iniciado, clique em **arquivo** e, em seguida, aponte para **abrir**. Navegue até o local onde seus arquivos de rastreamento são armazenados.  
  
2.  Clique duas vezes no arquivo de rastreamento que deseja abrir.  
  
    > [!NOTE]
    >  Pressione a tecla SHIFT enquanto clica em vários arquivos de rastreamento para selecioná-los e abri-los simultaneamente. O Visualizador de Rastreamento de Serviço mescla o conteúdo de todos os arquivos e apresenta uma exibição. Por exemplo, você pode abrir arquivos de rastreamento do cliente e do serviço. Isso é útil quando você tiver habilitado o log de mensagens e a propagação de atividade na configuração. Dessa forma, é possível examinar a troca de mensagens entre o cliente e o serviço. Você também pode arrastar vários arquivos para o visualizador ou use o **projeto** guia. Consulte a seção Gerenciando projetos para obter mais detalhes.  
  
3.  Para adicionar arquivos de rastreamento extras à coleção que está aberta, clique em **arquivo** e, em seguida, aponte para **Add**. Na janela que é aberta, navegue até o local dos arquivos de rastreamento e clique duas vezes no arquivo que deseja adicionar.  
  
> [!CAUTION]
>  Não é recomendável carregar um arquivo de log de rastreamento maior que 200 MB. Se você tentar carregar um arquivo maior do que esse limite, o processo de carregamento poderá levar muito tempo, dependendo do recurso do computador. A ferramenta Visualizador de Rastreamento de Serviço talvez não responda por um longo tempo, ou poderá esgotar a memória do computador. Para evitar esse problema, é recomendável configurar um carregamento parcial. Para obter mais informações sobre como fazer isso, consulte a seção "Carregando arquivos de rastreamento grandes".  
  
#### <a name="event-tracing-and-crimson-tracing"></a>Rastreamento de eventos e rastreamento Crimson  
 O formato nativo do Visualizador é o formato de rastreamento de atividade que emite do WCF. Os rastreamentos emitidos em um formato diferente devem ser convertidos antes que o visualizador os exiba. Atualmente, além do formato de rastreamento de atividade, o visualizador oferece suporte ao rastreamento de eventos e ao rastreamento crimson.  
  
 Quando você abre um arquivo que não contém rastreamentos de atividade, o visualizador tenta converter o arquivo. Você deve especificar o nome e o local do arquivo que conterá os dados de rastreamento convertidos. Uma vez que os dados tenham sido convertidos, o visualizador exibirá o conteúdo do novo arquivo.  
  
> [!NOTE]
>  A conversão requer espaço em disco para armazenar os dados de rastreamento convertidos. Verifique se você tem espaço suficiente em disco disponível para armazenar os dados antes de iniciar uma conversão. Caso contrário, a conversão falhará.  
  
### <a name="managing-projects"></a>Gerenciando projetos  
 O visualizador oferece suporte a projetos para facilitar a exibição de vários arquivos de rastreamento. Por exemplo, se você tem um arquivo de rastreamento de cliente e um arquivo de rastreamento de serviço, pode adicioná-los a um projeto. Depois disso, cada vez que você abrir o projeto, todos os arquivos de rastreamento do projeto serão carregados simultaneamente.  
  
 Há duas maneiras de gerenciar projetos:  
  
-   No **arquivo** menu, você pode abrir, salvar e fechar projetos.  
  
-   No **projeto** guia, você pode adicionar arquivos a um projeto.  
  
### <a name="viewing-wcf-traces"></a>Exibindo rastreamentos do WCF  
 WCF emite rastreamentos usando o formato de rastreamento de atividade. No modelo de rastreamento de atividade, os rastreamentos individuais são agrupados em atividades de acordo com sua finalidade. O fluxo de controle lógico é transferido entre atividades. Por exemplo, durante o tempo de vida de um aplicativo, muitas "atividades de envio de mensagens" aparecem e desaparecem. Para obter mais informações sobre como exibir os rastreamentos e atividades e a interface do usuário do Visualizador de rastreamento de serviço muito, consulte [usando o Visualizador de rastreamento de serviço para exibir rastreamentos correlacionados e soluções de problemas](../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).  
  
#### <a name="switching-to-different-views"></a>Alternando entre diferentes exibições  
 O Visualizador de Rastreamento de Serviço fornece as exibições a seguir. Eles são exibidos como guias no painel à esquerda do visualizador e também podem ser acessados a partir de **exibição** menu.  
  
-   Exibição de atividade  
  
-   Exibição de projeto  
  
-   Exibição de mensagem  
  
-   Exibição de gráfico  
  
##### <a name="activity-view"></a>Exibição de atividade  
 Depois que os arquivos de rastreamento são abertos, você pode ver os rastreamentos agrupados em atividades e exibido na **atividade** exibição no painel esquerdo.  
  
 O **atividade** exibição mostra nomes de atividades, número de rastreamentos na atividade de tempo de duração, hora de início e hora de término.  
  
 Quando você clica em qualquer uma das atividades listadas, os rastreamentos dessa atividade são exibidos no painel de rastreamento à direita. É possível selecionar um rastreamento para exibir seus detalhes.  
  
 Você pode selecionar várias atividades pressionando a **Ctrl** ou **Shift** chave e clicando nas atividades desejadas. O painel de rastreamento exibe todos os rastreamentos das atividades selecionadas.  
  
 Você pode clicar duas vezes uma atividade para exibi-lo no **Graph** modo de exibição. A maneira alternativa é selecionar uma atividade e alternar para o **Graph** modo de exibição.  
  
> [!NOTE]
>  A atividade "000000000000" é uma atividade especial que não pode ser exibida no modo de gráfico. Como todas as outras atividades estão vinculadas a ela, a exibição dessa atividade tem um sério impacto de desempenho.  
  
 Você pode clicar no título da coluna para classificar a lista de atividades. As atividades que contêm rastreamentos de avisos têm um plano de fundo amarelo, e aquelas que contêm rastreamentos de erros têm um plano de fundo vermelho.  
  
 Existem diferentes tipos de atividades, e cada tipo corresponde a um ícone no lado esquerdo de cada atividade. Você pode consultar a seção Entendendo os ícones de rastreamento para ver seus significados.  
  
##### <a name="project-view"></a>Exibição de projeto  
 Esta exibição permite gerenciar arquivos de rastreamento no projeto atual. Consulte a seção Gerenciando projetos para obter mais detalhes.  
  
##### <a name="graph-view"></a>Exibição de gráfico  
 Um dos recursos mais poderosos do Visualizador de rastreamento de serviço é o **Graph** exibição, que exibe os dados de rastreamento para uma determinada atividade na forma de gráfico. A forma de gráfico permite que você veja as etapas de execução de eventos e as inter-relações entre várias atividades à medida que os dados se movem entre elas.  
  
 Para alternar para o **Graph** exibir, selecione uma atividade na **atividade** exibir e clique no **atividade** guia ou um rastreamento de log de mensagem no **mensagem**Modo de exibição. Se vários arquivos de rastreamento forem carregados e a atividade envolver rastreamentos de mais de um arquivo, todos os rastreamentos relevantes aparecerão na exibição de gráfico. Clicar duas vezes em atividades e rastreamentos de log de mensagens também levam você para o **Graph** modo de exibição.  
  
 Na **Graph** exibição, cada coluna vertical representa uma atividade, e cada bloco na coluna representa um rastreamento. As atividades são agrupadas por processo (ou thread). As setas pequenas entre as atividades representam transferências. As setas grandes entre os processos representam troca de mensagens. A atividade na seleção está sempre em amarelo.  
  
###### <a name="selecting-traces-in-the-graph"></a>Selecionando rastreamentos no gráfico  
  
1.  Clique em um bloco no gráfico.  
  
2.  Use as teclas para cima e para baixo para selecionar seus rastreamentos vizinhos.  
  
3.  Observe as informações de rastreamento no Painel de Rastreamento e no Painel de Detalhes.  
  
###### <a name="expanding-or-collapsing-activity-transfers"></a>Expandindo ou recolhendo transferências de atividades  
 É possível expandir transferências de atividades quando a atividade na seleção é transferida para outra atividade. O recurso permite que você siga as transferências.  
  
 Para expandir ou recolher transferências de atividades  
  
1.  Localize o rastreamento de transferência com um sinal "+" à esquerda do ícone de transferência.  
  
2.  Clique em "+" ou pressione **Ctrl** e "+" usando o teclado.  
  
3.  A próxima atividade aparece no grafo.  
  
4.  Um "-" aparece à esquerda do ícone de transferência. Clique o "-" assinar ou pressione Ctrl e "-", a transferência de atividade é recolhido.  
  
> [!NOTE]
>  Quando uma atividade contém várias transferências e você expande uma das transferências, as atividades que levam à nova atividade da atividade raiz são exibidas. Essas novas atividades aparecem no formulário recolhido. Se você quiser ver os detalhes dessas atividades, expanda-as verticalmente clicando no ícone de expansão no cabeçalho do gráfico.  
  
###### <a name="expanding-or-collapsing-activities-vertically"></a>Expandindo ou recolhendo atividades verticalmente  
 O visualizador oculta detalhes desnecessários no gráfico de atividades recolhendo atividades. Em uma atividade recolhida, os rastreamentos individuais não são exibidos. Somente o rastreamento de transferências é exibido. Se você quiser exibir todos os rastreamentos de uma atividade, expanda a atividade verticalmente clicando no símbolo de expansão da atividade no cabeçalho do gráfico.  
  
 Para expandir ou recolher atividades verticalmente  
  
1.  Clique no ícone "+" no cabeçalho da atividade para expandir a atividade verticalmente.  
  
2.  Observe que todos os rastreamentos são exibidos no gráfico.  
  
3.  Clique o "-" ícone no cabeçalho da atividade para recolhê-la verticalmente.  
  
4.  Observe que somente as transferências, os logs de mensagens e os rastreamentos de avisos e exceções são mostrados na atividade.  
  
###### <a name="options"></a>Opções  
 Você pode selecionar duas opções do **opção** menu no modo de exibição gráfico.  
  
-   Mostrar Rastreamentos de Limite de Atividade, que, quando desmarcada, ignora os rastreamentos de limite de atividade no gráfico.  
  
-   Mostrar Rastreamentos Detalhados que Não Sejam de Mensagens, que, quando desmarcada, ignora rastreamentos de nível de detalhe, exceto para rastreamentos de mensagens. Na maioria dos casos, os rastreamentos de nível de detalhe são menos importantes para análise. Essa opção é útil quando você não quer analisar rastreamentos de nível de detalhe e quer apenas se concentrar em rastreamentos mais importantes.  
  
###### <a name="layout-mode"></a>Modo de layout  
 O visualizador possui dois modos de Layout: **processo** e **Thread**. Essa configuração define a maior unidade de organização. O padrão é o modo de Layout **processo**, o que significa que as atividades são agrupadas por processos no gráfico.  
  
###### <a name="execution-list"></a>Lista de execução  
 Você pode selecionar o processo ou thread a ser exibido no gráfico nessa lista suspensa. Por exemplo, se você tiver arquivos de rastreamento de dois clientes (A e B) e um serviço abertos, e desejar exibir somente o serviço e o cliente A no gráfico, poderá desmarcar o cliente B na lista.  
  
#### <a name="viewing-trace-details"></a>Exibindo detalhes de rastreamento  
 Para exibir detalhes de um rastreamento, selecione um rastreamento no painel Rastreamento. Os detalhes são exibidos no painel Detalhes.  
  
##### <a name="trace-pane"></a>Painel Rastreamento  
 O painel superior direito no Visualizador de Rastreamento de Serviço é o painel Rastreamento. Ele lista todos os rastreamentos na atividade selecionada com informações extras, por exemplo, o nível de rastreamento, a ID do thread e o nome do processo.  
  
 Você pode copiar o XML bruto do rastreamento para a área de transferência clicando duas vezes um rastreamento e selecionando **copiar rastreamento na área de transferência**.  
  
##### <a name="detail-pane"></a>Painel Detalhes  
 O painel inferior esquerdo no Visualizador de Rastreamento de Serviço é o painel Detalhes. Ele fornece três guias para exibir detalhes do rastreamento.  
  
 O **formatado** exibição exibe as informações de forma mais organizada. Ela lista todos os elementos XML conhecidos em tabelas e árvores, facilitando a leitura e a compreensão das informações.  
  
 O **XML** exibição mostra o XML correspondente ao rastreamento selecionado. Ela oferece suporte a realce e sintaxe colorida. Quando você usa **localizar** para pesquisar cadeias de caracteres, ele destaca os resultados da pesquisa.  
  
 O **mensagem** exibição exibe a parte da mensagem do XML em rastreamentos de log de mensagem. Ela fica invisível quando você seleciona um rastreamento que não seja de mensagem.  
  
### <a name="filtering-wcf-traces"></a>Filtrando rastreamentos do WCF  
 Para facilitar a análise de rastreamentos, você pode filtrá-los da seguinte maneira:  
  
-   A barra de ferramentas de filtro fornece acesso a filtros predefinidos e personalizados. Ele pode ser habilitado por meio de **exibição** menu.  
  
-   O filtro predefinido do visualizador pode ser usado para filtrar seletivamente partes dos rastreamentos do WCF. Por padrão, ele é definido para permitir a passagem de todos os rastreamentos de infraestrutura. As configurações desse filtro são definidas na **opções de filtro** submenu **exibição** menu.  
  
-   Os filtros XPath personalizados oferecem aos usuários controle total sobre a filtragem. Eles podem ser definidos na **filtro personalizado** sob **exibição** menu.  
  
 Somente os rastreamentos que passam por todos os filtros são exibidos.  
  
#### <a name="using-the-filter-toolbar"></a>Usando a barra de ferramentas de filtro  
 A barra de ferramentas de filtro aparece na parte superior da ferramenta. Se não estiver presente, você pode ativá-la na **exibição** menu. A barra possui três componentes:  
  
-   Procurar por: **procure** define o assunto a ser procurado na operação de filtro. Por exemplo, se você desejar localizar todos os rastreamentos que foram emitidos no contexto do processo X, defina esse campo como X e o **pesquisar em** campo do nome do processo. Esse campo muda para um controle seletor DateTime quando um filtro baseado em hora é selecionado.  
  
-   Pesquisar em: esse campo define o tipo de filtro a ser aplicado.  
  
-   Nível: essa configuração define o nível de rastreamento mínimo permitido pelo filtro. Por exemplo, se o nível for definido como Erro e Acima, somente rastreamentos dos níveis Erro e Crítico serão exibidos. Esse filtro é combinado aos critérios especificados por Procurar e Pesquisar em.  
  
 O **filtrar agora** botão inicia a operação de filtro. Alguns filtros, principalmente quando são aplicados a um grande conjunto de dados, demoram para serem concluídos. Você pode cancelar a operação de filtro pressionando o **pare** botão que aparece na barra de status na **operações** menu.  
  
 O **clara** botão redefine filtros predefinidos e personalizados para permitir a passagem de todos os rastreamentos.  
  
#### <a name="filter-options"></a>Opções de filtro  
 O visualizador pode remover automaticamente os rastreamentos do WCF do modo de exibição. Ele pode remover seletivamente os rastreamentos emitidos por áreas específicas do WCF, por exemplo, remover transações relacionadas rastreamentos da exibição.  
  
 As configurações desse filtro são definidas na **opções de filtro** submenu **exibição** menu.  
  
#### <a name="custom-filters"></a>Filtros personalizados  
 Se você estiver familiarizado com a linguagem XPath, poderá usá-la para criar filtros personalizados para pesquisar os dados de rastreamento de qualquer elemento XML do seu interesse. Os filtros são acessíveis por meio da barra de ferramentas de filtro.  
  
 Os filtros personalizados podem incluir parâmetros. Você também pode importar filtros personalizados preexistentes.  
  
##### <a name="creating-a-custom-filter"></a>Criando um filtro personalizado  
 Os filtros podem ser criados de duas maneiras:  
  
###### <a name="creating-a-custom-filter-using-the-template-wizard"></a>Criando um filtro personalizado usando o assistente de modelo  
 Você pode clicar em um rastreamento existente e criar um filtro baseado na estrutura do rastreamento. Este exemplo cria um filtro personalizado baseado em ID de thread.  
  
1.  No painel de rastreamento na área de superior direita do visualizador, selecione um rastreamento que inclua o elemento pelo qual você deseja filtrar.  
  
2.  Clique o **criar filtro personalizado** botão localizado na parte superior do painel de rastreamento.  
  
3.  Na caixa de diálogo que aparece, digite um nome para o filtro. Neste exemplo, digite `Thread ID`. Você também pode fornecer uma descrição do seu filtro.  
  
4.  A exibição de árvore à esquerda exibe a estrutura do registro de rastreamento selecionado na etapa 1. Navegue até o elemento para o qual você deseja criar uma condição. Neste exemplo, navegue até o ThreadID a ser localizado no XPath: /E2ETraceEvent/System/Execution/@ThreadID nó. Clique duas vezes no atributo ThreadID na exibição de árvore. Isso cria uma expressão para o atributo no lado direito da caixa de diálogo.  
  
5.  Altere o campo de parâmetro para a condição ThreadID de nenhum para '{0}'. Esta etapa permite que o valor de ThreadID seja configurado quando o filtro é aplicado. (Consulte a seção Como aplicar um filtro.) Você pode definir até quatro parâmetros. As condições são combinadas com o operador OR.  
  
6.  Clique em **Okey** para criar o filtro.  
  
> [!NOTE]
>  Uma vez que um filtro tenha sido criado com o assistente de modelo, ele só poderá ser editado manualmente. Não é possível ativar o assistente para um filtro que foi criado anteriormente. Além disso, as condições de um filtro XPath criado no assistente de modelo são combinadas com o operador OR. Se você precisar de uma operação AND, poderá editar a expressão de filtro depois que ela for criada.  
  
###### <a name="creating-a-custom-filter-manually"></a>Criando um filtro personalizado manualmente  
 O menu Filtros Personalizados permite que você insira filtros XPath manualmente.  
  
1.  No menu Exibir, clique no **filtros personalizados** item de menu.  
  
2.  Na caixa de diálogo que aparece, clique em **novo.**  
  
3.  No mínimo, especifique um nome de filtro e a expressão XPath.  
  
4.  Clique em **OK**.  
  
###### <a name="applying-a-custom-filter"></a>Aplicando um filtro personalizado  
 Uma vez que um filtro personalizado tenha sido criado, ele fica acessível na barra de ferramentas de filtro. Selecione o filtro que você deseja aplicar na **pesquisar em** campo da barra de ferramentas de filtro. Para o exemplo anterior, selecione 'ID do Thread'.  
  
1.  Especifique o valor que você está procurando na **localizar** campo. Em nosso exemplo, digite a ID do thread que deseja pesquisar.  
  
2.  Clique em **filtrar agora**e observe o resultado da operação.  
  
 Se seu filtro usa vários parâmetros, insira-os usando ';' como um separador na **localizar** campo. Por exemplo, a cadeia de caracteres a seguir define 3 parâmetros: ‘1;findValue;text’. O visualizador aplica '1' para o {0} parâmetro do filtro. 'findValue' e 'text' são aplicadas aos {1} e {2} , respectivamente.  
  
###### <a name="sharing-custom-filters"></a>Compartilhando filtros personalizados  
 Os filtros personalizados podem ser compartilhados entre sessões e usuários diferentes. Você pode exportar os filtros para um arquivo de definição e importar esse arquivo em outro local.  
  
 Para importar um filtro personalizado:  
  
1.  No **modo de exibição** menu, clique em **filtros personalizados**.  
  
2.  Na caixa de diálogo que é aberta, clique o **importação** botão.  
  
3.  Navegue até o arquivo de filtro personalizado (. stvcf), clique no arquivo e clique no **abrir** botão.  
  
 Para exportar um filtro personalizado:  
  
1.  No menu Exibir, clique em **filtros personalizados**.  
  
2.  Na caixa de diálogo que é aberta, selecione o filtro que você deseja exportar.  
  
3.  Clique o **exportar** botão.  
  
4.  Especifique o nome e local do arquivo de definição de filtro personalizado (. stvcf) e clique no **salvar** botão.  
  
> [!NOTE]
>  Esses filtros personalizados podem apenas ser importados e exportados pelo Visualizador de Rastreamento de Serviço. Eles não podem ser lidos por outras ferramentas.  
  
### <a name="finding-data"></a>Localizando dados  
 O visualizador oferece as seguintes maneiras de localizar dados:  
  
-   A barra de ferramentas de localização fornece um acesso rápido às opções de localização mais comuns.  
  
-   A caixa de diálogo de localização fornece mais opções de localização. Ele pode ser acessado por meio de **editar** menu, ou o atalho de teclado Ctrl + F.  
  
 A barra de ferramentas de localização aparece na parte superior do visualizador. Se não estiver presente, você pode ativá-la na **exibição** menu. A barra possui dois componentes:  
  
-   Localizar: permite que você insira a palavra-chave de pesquisa.  
  
-   Examinar: permite que você insira o escopo da pesquisa. Você pode selecionar se deseja pesquisar em todas as atividades ou somente na atividade atual.  
  
 A caixa de diálogo de localização fornece duas opções adicionais:  
  
-   Localizar destino:  
  
    -   A opção de "dados de log brutos" pesquisa a palavra-chave em todos os dados brutos.  
  
    -   As opções "Texto XML" e "Atributo XML" pesquisam somente em elementos XML.  
  
    -   A opção "Mensagem registrada" pesquisa a palavra-chave somente nas mensagens.  
  
-   Ignorar atividade raiz: A pesquisa ignora os rastreamentos na atividade "000000000000". Isso melhora o desempenho em grandes arquivos de rastreamento quando a atividade raiz tem milhares de rastreamentos, dos quais a maioria são transferências.  
  
### <a name="navigating-traces"></a>Navegando em rastreamentos  
 Como os rastreamentos são registrados passo a passo durante o tempo de execução do aplicativo, a navegação em rastreamentos pode ajudá-lo a depurar seu aplicativo. O Visualizador de Rastreamento de Serviço fornece várias maneiras de navegar em rastreamentos.  
  
#### <a name="step-forward-or-backward"></a>Avançar ou retroceder  
 Se você considerar cada rastreamento como uma linha de código do programa, avanço é muito semelhante à "Depuração parcial" no IDE do Visual Studio Integrated Development ambiente (). A diferença é que você também pode retroceder nos rastreamentos. Avançar significa mover-se para o próximo rastreamento da atividade.  
  
-   Avançar: Use o **atividade** menus ou pressione "F10". Você também pode usar a tecla de direção "para baixo" no painel de rastreamento.  
  
-   Retroceder: Use o **atividade** menus ou pressione "F9". Você também pode usar a tecla de direção "para cima" no painel de rastreamento.  
  
> [!NOTE]
>  Isso pode levar você a uma atividade ocorrendo em um processo diferente ou mesmo em um computador diferente, pois as mensagens do WCF podem transportar IDs de atividade que abrangem computadores.  
  
#### <a name="follow-transfer"></a>Seguir transferência  
 Os rastreamentos de transferência são rastreamentos especiais no arquivo de rastreamento. Uma atividade pode fazer a transferência para outra atividade por um rastreamento de transferência. Por exemplo, "Atividade A" pode transferir para "Atividade B". Nesse caso, há um rastreamento de transferência no ícone de "Atividade A" com o nome "Para: atividade" e a transferência. Esse rastreamento de transferência é um link entre os dois rastreamentos. Na "Atividade B", também pode haver um rastreamento de transferência no final da atividade a ser transferido de volta à "Atividade A". Isso é semelhante às chamadas de função em programas: A chama B e, em seguida, B retorna.  
  
 "Seguir transferência" é semelhante a "Step into" em um depurador. Ele segue a transferência de A para B. Ele não tem nenhum efeito em outros rastreamentos.  
  
 Há duas maneiras de seguir uma transferência: pelo mouse ou pelo teclado:  
  
-   Pelo mouse: clique duas vezes no rastreamento de transferência no painel de rastreamento.  
  
-   Pelo teclado: Selecione um rastreamento de transferência e use "Seguir transferência" no **atividade** menus ou pressione "F11"  
  
> [!NOTE]
>  Em muitos casos, quando a atividade A transfere para a atividade B, a atividade A aguarda até que a atividade B transfira de volta à atividade A. Isso significa que a atividade A tem nenhum rastreamento registrado durante o período de quando a atividade B está ativamente rastreando. Entretanto, também é possível que a Atividade A não aguarde e continue a registrar rastreamentos. Também é possível que atividade B transfira de volta à atividade A. Portanto, as transferências de atividades são ainda diferentes de chamadas de função nesse sentido. Você pode entender melhor as transferências de atividades na exibição Gráfico.  
  
#### <a name="jump-to-next-or-previous-transfer"></a>Passar para a próxima transferência ou a anterior  
 Ao analisar a atividade atual, ou as atividades selecionadas quando várias atividades são selecionadas, você talvez queira localizar as atividades para as quais ela transfere. "Passar para a próxima transferência" permite que você localize o próximo rastreamento de transferência na atividade. Depois de encontrar o rastreamento de transferência, você pode usar "Seguir transferência" Step into a próxima atividade.  
  
-   Ir para a próxima transferência: Use o **atividade** menus ou pressione "Ctrl + F10".  
  
-   Ir para a transferência anterior: Use o **atividade** menu, ou pressione "Ctrl + F9".  
  
#### <a name="navigate-in-graph-view"></a>Navegar na exibição de gráfico  
 Embora seja semelhante à depuração navegando no painel de atividade e o painel de rastreamento, usando **Graph** exibição fornece uma melhor experiência no painel de navegação. Consulte a seção "Modo de exibição de gráfico" para obter mais informações.  
  
### <a name="loading-large-trace-files"></a>Carregando arquivos de rastreamento grandes  
 Os arquivos de rastreamento podem ser muito grandes. Por exemplo, se você ativar o rastreamento no nível "Detalhado", o arquivo de rastreamento resultante para a execução de alguns minutos poderá facilmente se centenas de megabytes ou ainda maior, dependendo do padrão de velocidade e a comunicação de rede.  
  
 Quando você abre um arquivo de rastreamento muito grande no Visualizador de Rastreamento de Serviço, o desempenho do sistema pode ser afetado negativamente. A velocidade de carregamento e o tempo de resposta após o carregamento podem ficar lentos. A velocidade real às vezes difere, dependendo da configuração do seu hardware. Na maioria de PCs, carregar um arquivo de rastreamento com mais de 200 M tem um sério impacto no desempenho. Para arquivos de rastreamentos maiores com mais de 1G, a ferramenta pode usar toda a memória disponível, ou parar de responder por um longo período.  
  
 Para evitar o carregamento lento e o tempo de resposta na análise de arquivos de rastreamento grandes, o Visualizador de rastreamento de serviço fornece um recurso chamado "Carregamento parcial", que carrega apenas uma pequena parte do rastreamento de cada vez. Por exemplo, você poderá ter um arquivo de rastreamento acima de 1 GB sendo executado por vários dias no servidor. Quando ocorrerem alguns erros e você quiser analisar o rastreamento, não precisará abrir o arquivo de rastreamento inteiro. Em vez disso, você poderá carregar os rastreamentos dentro de um determinado período de tempo em que o erro possa ter ocorrido. Como o escopo é menor, a ferramenta Visualizador de Rastreamento de Serviço pode carregar o arquivo mais rapidamente e você pode identificar os erros usando um conjunto de dados menor.  
  
#### <a name="enabling-partial-loading"></a>Habilitando o carregamento parcial  
 Você não precisa habilitar manualmente o carregamento parcial. Se o tamanho total do arquivo de rastreamento que você tenta carregar exceder 40 MB, o Visualizador de Rastreamento de Serviço automaticamente exibirá uma caixa de diálogo Carregamento Parcial, para que você selecione a parte que deseja carregar.  
  
> [!NOTE]
>  Como os rastreamentos podem não estar distribuídos de modo uniforme no intervalo de tempo, o período de tempo que você especificar na barra de ferramentas Carregamento Parcial talvez não seja proporcional ao tamanho do carregamento mostrado. O tamanho do carregamento real pode ser menor do que o Tamanho Estimado na caixa de diálogo de carregamento parcial.  
  
#### <a name="adjusting-partial-loading"></a>Ajustando o carregamento parcial  
 Depois de ter carregado parcialmente o arquivo de rastreamento, você talvez queira modificar o conjunto de dados que está sendo carregado. É possível fazer isso ajustando a barra de ferramentas Carregamento Parcial na parte superior do visualizador.  
  
1.  Mova a barra de ferramentas usando o mouse, ou insira os horários de Início e Término.  
  
2.  Clique o **ajustar** botão.  
  
## <a name="understanding-trace-icons"></a>Entendendo os ícones de rastreamento  
 A seguir está uma lista de ícones que a ferramenta Visualizador de rastreamento de serviço usa o **atividade** exibição, **Graph** modo de exibição e **rastreamento** painel para representar itens diferentes.  
  
> [!NOTE]
>  Alguns rastreamentos que não sejam categorizados (por exemplo, "uma mensagem é fechada") não têm nenhum ícone.  
  
### <a name="activity-tracing-traces"></a>Rastreamentos de atividades  
  
|Ícone|Descrição|  
|----------|-----------------|  
|![Rastreamento de aviso](../../../docs/framework/wcf/media/7457c4ed-8383-4ac7-bada-bcb27409da58.gif "7457c4ed-8383-4ac7-bada-bcb27409da58")|Rastreamento de aviso: um rastreamento que é emitido no nível de aviso.|  
|![Rastreamento de erro](../../../docs/framework/wcf/media/7d908807-4967-4f6d-9226-d52125db69ca.gif "7d908807-4967-4f6d-9226-d52125db69ca")|Rastreamento de erro: um rastreamento que é emitido no nível de erro.|  
|![Rastreamento de início da atividade:](../../../docs/framework/wcf/media/8a728f91-5f80-4a95-afe8-0b6acd6e0317.gif "8a728f91-5f80-4a95-afe8-0b6acd6e0317")|Rastreamento de início de atividade: um rastreamento que marca o início de uma atividade. Contém o nome da atividade. Como designer ou desenvolvedor de aplicativos, você deve definir um rastreamento de início de atividade por ID de atividade para cada processo ou thread.<br /><br /> Se a ID de atividade for propagada nas origens de rastreamento para a correlação de rastreamentos, você poderá consultar vários inícios para a mesma ID de atividade (um por origem de rastreamento). O rastreamento de início será emitido se ActivityTracing estiver habilitado para a origem de rastreamento.|  
|![Rastreamento de interrupção de atividade](../../../docs/framework/wcf/media/a0493e95-653e-4af8-84a4-4d09a400bc31.gif "a0493e95-653e-4af8-84a4-4d09a400bc31")|Rastreamento de interrupção de atividade: um rastreamento que marca o fim de uma atividade. . Contém o nome da atividade. Como designer ou desenvolvedor de aplicativos, você deve definir um rastreamento de interrupção de atividade por ID de atividade para cada origem de rastreamento. Nenhum rastreamento de uma determinada origem aparece após a interrupção de atividade emitida por essa origem de rastreamento, exceto se a granularidade do tempo de rastreamento não for suficientemente pequena. Quando isso acontece, dois rastreamentos com o mesmo tempo, incluindo uma interrupção, podem ser intercalados quando exibidos. Se a ID de atividade for propagada nas origens de rastreamento para a correlação de rastreamentos, você poderá consultar várias interrupções para a mesma ID de atividade (uma por origem de rastreamento). O rastreamento de interrupção será emitido se ActivityTracing estiver habilitado para a origem de rastreamento.|  
|![Rastreamento de suspensão de atividade](../../../docs/framework/wcf/media/6f7f4191-df2b-4592-8998-8379769e2d32.gif "6f7f4191-df2b-4592-8998-8379769e2d32")|Rastreamento de suspensão de atividade: um rastreamento que marca o tempo em que uma atividade está em pausa. Nenhum rastreamento é emitido em uma atividade suspensa até que a atividade seja retomada. Uma atividade suspensa indica que nenhum processamento está ocorrendo nela no escopo da origem de rastreamento. Os rastreamentos de suspensão/retomada são úteis para a criação de perfil. O rastreamento de suspensão será emitido se ActivityTracing estiver habilitado para a origem de rastreamento.|  
|![Rastreamento de retomada de atividade](../../../docs/framework/wcf/media/1060d9d2-c9c8-4e0a-9988-cdc2f7030f17.gif "1060d9d2-c9c8-4e0a-9988-cdc2f7030f17")|Rastreamento de retomada de atividade: um rastreamento que marca o tempo em que uma atividade é retomada após ter sido suspensa. Os rastreamentos podem ser emitidos novamente nessa atividade. Os rastreamentos de suspensão/retomada são úteis para a criação de perfil. O rastreamento de retomada será emitido se ActivityTracing estiver habilitado para a origem de rastreamento.|  
|![Transfer](../../../docs/framework/wcf/media/b2d9850e-f362-4ae5-bb8d-9f6f3ca036a5.gif "b2d9850e-f362-4ae5-bb8d-9f6f3ca036a5")|Transferência: um rastreamento que é emitido quando o fluxo de controle lógico é transferido de uma atividade para outra. A atividade de origem da transferência poderá continuar a executar o trabalho em paralelo à atividade de destino da transferência. O rastreamento de transferência será emitido se ActivityTracing estiver habilitado para a origem de rastreamento.|  
|![Transferir do](../../../docs/framework/wcf/media/1df215cb-b344-4f36-a20d-195999bda741.gif "1df215cb-b344-4f36-a20d-195999bda741")|Transferência de: um rastreamento que define uma transferência de outra atividade para a atividade atual.|  
|![Transferir para o](../../../docs/framework/wcf/media/74255b6e-7c47-46ef-8e53-870c76b04c3f.gif "74255b6e-7c47-46ef-8e53-870c76b04c3f")|Transferência para: um rastreamento que define uma transferência de fluxo de controle lógico da atividade atual para outra atividade.|  
  
### <a name="wcf-traces"></a>Rastreamentos do WCF  
  
|Ícone|Descrição|  
|----------|-----------------|  
|![Log de rastreamento de mensagem](../../../docs/framework/wcf/media/7c66e994-2476-4260-a0db-98948b9af197.gif "7c66e994-2476-4260-a0db-98948b9af197")|Log de rastreamento de mensagem: um rastreamento que é emitido quando uma mensagem WCF é registrada pelo recurso de log de mensagens, quando o `System.ServiceModel.MessageLogging` origem de rastreamento está habilitada. Clicar nesse rastreamento exibe a mensagem. Há quatro pontos de log configuráveis para uma mensagem: ServiceLevelSendRequest, TransportSend, TransportReceive e ServiceLevelReceiveRequest, o que também pode ser especificado pelo atributo `messageSource` no rastreamento de log de mensagens.|  
|![Rastreamento de mensagem recebida](../../../docs/framework/wcf/media/de4f586c-c5dd-41ec-b1c3-ac56b4dfa35c.gif "de4f586c-c5dd-41ec-b1c3-ac56b4dfa35c")|Rastreamento de mensagem recebida: um rastreamento que é emitido quando uma mensagem WCF é recebida, se o `System.ServiceModel` origem de rastreamento está habilitada no nível de informações ou detalhado. Esse rastreamento é essencial para exibir a seta de correlação da mensagem na atividade de **Graph** modo de exibição.|  
|![Rastreamento de mensagem enviada](../../../docs/framework/wcf/media/558943c4-17cf-4c12-9405-677e995ac387.gif "558943c4-17cf-4c12-9405-677e995ac387")|Rastreamento de mensagem enviada: um rastreamento que é emitido quando uma mensagem WCF será enviada se o `System.ServiceModel` origem de rastreamento está habilitada no nível de informações ou detalhado. Esse rastreamento é essencial para exibir a seta de correlação da mensagem na atividade de **Graph** modo de exibição.|  
  
### <a name="activities"></a>Atividades  
  
|Ícone|Descrição|  
|----------|-----------------|  
|![Atividade](../../../docs/framework/wcf/media/wcfc-defaultactivityc.gif "wcfc_defaultActivityc")|Atividade: indica que a atividade atual é uma atividade genérica.|  
|![Atividade raiz](../../../docs/framework/wcf/media/5dc8e0eb-1c32-4076-8c66-594935beaee9.gif "5dc8e0eb-1c32-4076-8c66-594935beaee9")|Atividade raiz: indica a atividade raiz de um processo.|  
  
### <a name="wcf-activities"></a>Atividades do WCF  
  
|Ícone|Descrição|  
|----------|-----------------|  
|![Atividade de ambiente](../../../docs/framework/wcf/media/29fa00ac-cf78-46e5-822d-56222fff61d1.gif "29fa00ac-cf78-46e5-822d-56222fff61d1")|Atividade de ambiente: uma atividade que cria, abre ou fecha um cliente ou host do WCF. Os erros que tiverem ocorrido durante essas fases aparecerão nesta atividade.|  
|![Atividade de escuta](../../../docs/framework/wcf/media/d7b135f6-ec7d-45d7-9913-037ab30e4c26.gif "d7b135f6-ec7d-45d7-9913-037ab30e4c26")|Atividade de escuta: uma atividade que registra em log os rastreamentos relacionados a um ouvinte. Dentro desta atividade, é possível exibir informações e solicitações de conexão do ouvinte.|  
|![Receber atividade de Bytes](../../../docs/framework/wcf/media/2f628580-b80f-45a7-925b-616c96426c0e.gif "2f628580-b80f-45a7-925b-616c96426c0e")|Atividade de recepção de bytes: uma atividade que agrupa todos os rastreamentos relacionados à recepção de bytes de entrada em uma conexão entre dois pontos de extremidade. Esta atividade é essencial na correlação com as atividades de transporte que propagam sua ID de atividade, como http.sys. Erros de conexão, como anulações, aparecerão nesta atividade.|  
|![Atividade de mensagem de processamento](../../../docs/framework/wcf/media/wcfc-executionactivityiconc.GIF "wcfc_ExecutionActivityIconc")|Processar a atividade de mensagem: uma atividade que agrupa rastreamentos relacionados à criação de uma mensagem WCF. Os erros devido a um envelope incorreto ou uma mensagem malformada aparecerão nesta atividade. Dentro desta atividade, podemos inspecionar cabeçalhos de mensagens para ver se uma ID de atividade foi propagada do chamador. Se isso acontecer, ao transferirmos para a atividade de processamento de ação (o próximo ícone), poderemos também atribuir a esta atividade a ID de atividade propagada para a correlação entre os rastreamentos do chamador e do receptor.|  
|![Log de rastreamento de mensagem](../../../docs/framework/wcf/media/7c66e994-2476-4260-a0db-98948b9af197.gif "7c66e994-2476-4260-a0db-98948b9af197")|Processar a atividade de ação: uma atividade que agrupa todos os rastreamentos relacionados a uma solicitação do WCF entre dois pontos de extremidade. Se `propagateActivity` estiver definido como `true` em ambos os pontos de extremidade na configuração, todos os rastreamentos de ambos os pontos de extremidade serão mesclados em uma única atividade para correlação direta. Tal atividade conterá erros devido ao processamento de segurança ou transporte, estendendo-se ao limite do código do usuário e à volta (se houver uma resposta).|  
|![Atividade de mensagem de processamento](../../../docs/framework/wcf/media/wcfc-executionactivityiconc.GIF "wcfc_ExecutionActivityIconc")|Atividade de execução de código de usuário: uma atividade que agrupa rastreamentos de código de usuário para processar uma solicitação.|  
  
## <a name="troubleshooting"></a>Solução de problemas  
 Se você não tiver permissão para gravar no registro, você obtém a mensagem de erro "O Visualizador de rastreamento do Microsoft Service não foi registrado no sistema" ao usar o "`svctraceviewer /register`" comando para registrar a ferramenta. Se isso ocorrer, você deverá fazer logon usando uma conta que tenha acesso de gravação no Registro.  
  
 Além disso, a ferramenta Visualizador de Rastreamento de Serviço grava algumas configurações (por exemplo, filtros personalizado e opções de filtro) no arquivo SvcTraceViewer.exe.settings em sua pasta de assembly. Se você não tiver permissão de leitura para o arquivo, ainda poderá iniciar a ferramenta, mas não poderá carregar as configurações.  
  
 Se você receber a mensagem de erro “Erro desconhecido ao processar um ou mais rastreamentos” ao abrir o arquivo .etl, ela significa que o formato de arquivo .etl é inválido.  
  
 Se você abrir um log de rastreamento criado em um sistema operacional árabe, poderá observar que o filtro de tempo não funciona. Por exemplo, o ano 2005 corresponde ao ano 1427 no calendário árabe. Porém, o intervalo de tempo aceito pelo filtro da ferramenta Visualizador de Rastreamento de Serviço não oferece suporte a uma data anterior a 1752. Isso indica que você não pode selecionar uma data correta no filtro. Para resolver esse problema, você pode criar um filtro personalizado (**Exibir/filtros personalizados**) usando uma expressão XPath para incluir um intervalo de tempo específico.  
  
## <a name="see-also"></a>Consulte também  
 [Usando o Visualizador de Rastreamento de Serviço para exibir rastreamentos correlacionados e solucionar problemas](../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)  
 [Configurando o rastreamento](../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)  
 [Rastreamento de atividades e propagação para correlação de rastreamento de ponta a ponta](https://msdn.microsoft.com/library/2c11a905-64f8-47b5-bae5-a74fc666137e)
