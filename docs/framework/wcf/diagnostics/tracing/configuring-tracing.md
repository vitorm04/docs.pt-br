---
title: Configurando o rastreamento
ms.date: 03/30/2017
helpviewer_keywords:
- tracing [WCF]
ms.assetid: 82922010-e8b3-40eb-98c4-10fc05c6d65d
ms.openlocfilehash: f80d89d66253df310395cdfa3139e8765da24edb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54584906"
---
# <a name="configuring-tracing"></a>Configurando o rastreamento
Este tópico descreve como você pode habilitar o rastreamento, configurar origens de rastreamento para emitir rastreamentos e definir níveis de rastreamento, rastreamento de atividades do conjunto e propagação para dar suporte à correlação de rastreamento de ponta a ponta e definir ouvintes de rastreamento para acessar rastreamentos.  
  
 Para obter recomendações de configurações de rastreamento no ambiente de produção ou depuração, consulte [as configurações recomendadas para rastreamento e registro em log de mensagem](../../../../../docs/framework/wcf/diagnostics/tracing/recommended-settings-for-tracing-and-message-logging.md).  
  
> [!IMPORTANT]
>  No Windows 8, você deve executar seu aplicativo com privilégios elevados (Executar como administrador) para seu aplicativo gerar logs de rastreamento.  
  
## <a name="enabling-tracing"></a>A habilitação do rastreamento  
 Windows Communication Foundation (WCF) gera os seguintes dados para o rastreamento de diagnóstico:  
  
-   Rastreamentos para as etapas do processo em todos os componentes de aplicativos, como chamadas de operação, o código exceções, avisos e outros eventos de processamento significativo.  
  
-   Eventos de erro do Windows quando o recurso de rastreamento funciona incorretamente. Ver [log de eventos](../../../../../docs/framework/wcf/diagnostics/event-logging/index.md).  
  
 Rastreamento do WCF baseia-se na parte superior da <xref:System.Diagnostics>. Para usar o rastreamento, você deve definir fontes de rastreamento no arquivo de configuração ou no código. O WCF define uma origem de rastreamento para cada assembly do WCF. O `System.ServiceModel` origem de rastreamento é a origem de rastreamento do WCF mais geral e registra as etapas de processamento em toda a pilha de comunicação do WCF de transporte entrar/sair para inserir/deixar o código do usuário. O `System.ServiceModel.MessageLogging` origem de rastreamento registra todas as mensagens que fluem através do sistema.  
  
 O rastreamento não está habilitado por padrão. Para ativar o rastreamento, você deve criar um ouvinte de rastreamento e defina um nível de rastreamento que não seja "Desativado" para a origem de rastreamento selecionado na configuração; Caso contrário, o WCF não gera qualquer rastreamentos. Se você não especificar um ouvinte, o rastreamento está desabilitado automaticamente. Se um ouvinte é definido, mas nenhum nível for especificado, o nível é definido como "Desativado" por padrão, o que significa que nenhum rastreamento é emitido.  
  
 Se você usar pontos de extensibilidade do WCF, como chamadores de operação personalizado, você deve emitir seus próprios rastreamentos. Isso ocorre porque se você implementar um ponto de extensibilidade, o WCF não pode emitir os rastreamentos padrão no caminho padrão. Se você não implementar o suporte a rastreamento manual por emitindo rastreamentos, você não pode ver os rastreamentos que você espera.  
  
 Você pode configurar o rastreamento editando o arquivo de configuração do aplicativo — o Web. config para aplicativos hospedados na Web ou Appname.exe.config para aplicativos auto-hospedados. O exemplo a seguir é um exemplo de tal edição. Para obter mais informações sobre essas configurações, consulte a seção "Configurar ouvintes de rastreamento para rastreamentos consumir".  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <sources>  
            <source name="System.ServiceModel"   
                    switchValue="Information, ActivityTracing"  
                    propagateActivity="true">  
            <listeners>  
               <add name="traceListener"   
                   type="System.Diagnostics.XmlWriterTraceListener"   
                   initializeData= "c:\log\Traces.svclog" />  
            </listeners>  
         </source>  
      </sources>  
   </system.diagnostics>  
</configuration>  
```  
  
> [!NOTE]
>  Para editar o arquivo de configuração de um projeto de serviço do WCF no Visual Studio, clique com botão direito o arquivo de configuração do aplicativo — o Web. config para aplicativos hospedados na Web ou Appname.exe.config para o aplicativo hospedado internamente no **Gerenciador de soluções** . Em seguida, escolha o **Editar configuração WCF** item de menu de contexto. Isso inicia o [ferramenta de Editor de configuração (SvcConfigEditor.exe)](../../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md), que permite que você modifique as definições de configuração para os serviços WCF usando uma interface gráfica do usuário.  
  
## <a name="configuring-trace-sources-to-emit-traces"></a>Configurando fontes de rastreamento para emitir rastreamentos  
 O WCF define uma origem de rastreamento para cada assembly. Rastreamentos gerados dentro de um assembly são acessados pelos ouvintes definidos para essa fonte. As seguintes fontes de rastreamento são definidas:  
  
-   System.ServiceModel: Registra todos os estágios do processamento de WCF, sempre que a configuração é lida, uma mensagem é processada no transporte, segurança de processamento, uma mensagem é enviada no código do usuário e assim por diante.  
  
-   System.ServiceModel.MessageLogging: Registra todas as mensagens que fluem através do sistema.  
  
-   System.IdentityModel.  
  
-   System.ServiceModel.Activation.  
  
-   System.IO.Log: Registro em log para a interface do .NET Framework para o Common Log arquivo CLFS (sistema).  
  
-   System.Runtime.Serialization: Logs quando objetos são lidos ou gravados.  
  
-   CardSpace.  
  
 Você pode configurar cada origem de rastreamento para usar o mesmo ouvinte (compartilhado), conforme indicado no exemplo de configuração a seguir.  
  
```xml  
<configuration>  
    <system.diagnostics>  
        <sources>  
            <source name="System.ServiceModel"   
                    switchValue="Information, ActivityTracing"  
                    propagateActivity="true">  
                <listeners>  
                    <add name="xml" />  
                </listeners>  
            </source>  
            <source name="CardSpace">  
                <listeners>  
                    <add name="xml" />  
                </listeners>  
            </source>  
            <source name="System.IO.Log">  
                <listeners>  
                    <add name="xml" />  
                </listeners>  
            </source>  
            <source name="System.Runtime.Serialization">  
                <listeners>  
                    <add name="xml" />  
                </listeners>  
            </source>  
            <source name="System.IdentityModel">  
                <listeners>  
                    <add name="xml" />  
                </listeners>  
            </source>  
        </sources>  
  
        <sharedListeners>  
            <add name="xml"  
                 type="System.Diagnostics.XmlWriterTraceListener"  
                 initializeData="c:\log\Traces.svclog" />  
        </sharedListeners>  
    </system.diagnostics>  
</configuration>  
```  
  
 Além disso, você pode adicionar fontes de rastreamento definidos pelo usuário, como demonstrado pelo exemplo a seguir, para emitir rastreamentos de código do usuário.  
  
```xml  
<system.diagnostics>  
   <sources>  
       <source name="UserTraceSource" switchValue="Warning, ActivityTracing" >  
          <listeners>  
              <add name="xml"  
                 type="System.Diagnostics.XmlWriterTraceListener"  
                 initializeData="C:\logs\UserTraces.svclog" />  
          </listeners>  
       </source>  
   </sources>  
   <trace autoflush="true" />   
</system.diagnostics>  
```  
  
 Para obter mais informações sobre como criar fontes de rastreamento definidos pelo usuário, consulte [estendendo rastreamento](../../../../../docs/framework/wcf/samples/extending-tracing.md).  
  
## <a name="configuring-trace-listeners-to-consume-traces"></a>Configurar ouvintes de rastreamento para rastreamentos de consumir  
 No tempo de execução WCF feeds de dados de rastreamento para os ouvintes que processam os dados. O WCF fornece vários ouvintes predefinidos para <xref:System.Diagnostics>, que diferem no formato usado para a saída. Você também pode adicionar tipos de ouvinte personalizado.  
  
 Você pode usar `add` para especificar o nome e o tipo do ouvinte de rastreamento que deseja usar. Em nosso exemplo de configuração, nomeamos o ouvinte `traceListener` e adicionado o ouvinte de rastreamento padrão do .NET Framework (`System.Diagnostics.XmlWriterTraceListener`) como o tipo que queremos usar. Você pode adicionar qualquer número de ouvintes de rastreamento para cada fonte. Se o ouvinte de rastreamento emite o rastreamento em um arquivo, você deve especificar o local do arquivo de saída e o nome no arquivo de configuração. Isso é feito definindo `initializeData` para o nome do arquivo para esse ouvinte. Se você não especificar um nome de arquivo, um nome de arquivo aleatório é gerado com base no tipo de ouvinte usado. Se <xref:System.Diagnostics.XmlWriterTraceListener> for usado, será gerado um nome de arquivo sem extensão. Se você implementar um ouvinte personalizado, você também pode usar esse atributo para receber dados de inicialização que não seja um nome de arquivo. Por exemplo, você pode especificar um identificador de banco de dados para esse atributo.  
  
 Você pode configurar um ouvinte de rastreamento personalizado para enviar os rastreamentos durante a transmissão, por exemplo, um banco de dados remoto. Como um implantador de aplicativo, você deve aplicar o controle de acesso apropriadas em logs de rastreamento no computador remoto.  
  
 Você também pode configurar um ouvinte de rastreamento programaticamente. Para obter mais informações, confira [Como: Criar e inicializar ouvintes de rastreamento](https://go.microsoft.com/fwlink/?LinkId=94648) e [criando um TraceListener personalizado](https://go.microsoft.com/fwlink/?LinkId=96239).  
  
> [!CAUTION]
>  Porque `System.Diagnostics.XmlWriterTraceListener` é não é thread-safe, a origem de rastreamento pode bloquear recursos exclusivamente na saída de rastreamentos. Quando vários threads de saída de rastreamentos em uma origem de rastreamento configurado para usar este ouvinte, pode ocorrer a contenção de recursos, que resulta em um problema de desempenho significativa. Para resolver esse problema, você deve implementar um ouvinte personalizado que é thread-safe.  
  
## <a name="trace-level"></a>Nível de rastreamento:  
 O nível de rastreamento é controlado pelo `switchValue` Definir origem de rastreamento. Os níveis de rastreamento disponíveis são descritos na tabela a seguir.  
  
|Nível de rastreamento:|Natureza dos eventos rastreados|Conteúdo dos eventos rastreados|Eventos rastreados|Destino do usuário|  
|-----------------|----------------------------------|-----------------------------------|--------------------|-----------------|  
|Off|N/D|N/D|Nenhum rastreamento é emitido.|N/D|  
|Crítico|"Negativo" eventos: eventos que indicam um processamento inesperado ou uma condição de erro.||Exceções sem tratamento, incluindo os seguintes são registradas:<br /><br /> -OutOfMemoryException<br />-ThreadAbortException (o CLR chama qualquer ThreadAbortExceptionHandler)<br />-StackOverflowException (não pode ser detectada)<br />-   ConfigurationErrorsException<br />-   SEHException<br />– Início aplicativo erros<br />-Eventos Failfast<br />-Paradas do sistema<br />-Mensagens suspeitas: mensagem rastreamentos que fazem com que o aplicativo falhe.|Administradores<br /><br /> Desenvolvedores de aplicativos|  
|Erro|"Negativo" eventos: eventos que indicam um processamento inesperado ou uma condição de erro.|Processamento inesperado aconteceu. O aplicativo não pôde executar uma tarefa, conforme o esperado. No entanto, o aplicativo está ainda em execução.|Todas as exceções são registradas.|Administradores<br /><br /> Desenvolvedores de aplicativos|  
|Aviso|"Negativo" eventos: eventos que indicam um processamento inesperado ou uma condição de erro.|Um possível problema ocorreu, ou pode ocorrer, mas o aplicativo ainda funcione corretamente. No entanto, talvez não continue a funcionar corretamente.|-O aplicativo está recebendo mais solicitações do que permitir que suas configurações de limitação.<br />-A fila de recebimento está perto de sua capacidade máxima de configurado.<br />-Tempo limite foi excedido.<br />-Credenciais são rejeitadas.|Administradores<br /><br /> Desenvolvedores de aplicativos|  
|Informações|"Positivos" eventos: eventos que marcam marcos bem-sucedida|Marcos importantes e bem-sucedido de execução do aplicativo, independentemente se o aplicativo está funcionando corretamente ou não.|Em geral, são geradas mensagens úteis para monitorar e diagnosticar o status do sistema, medir o desempenho ou criação de perfil. Você pode usar essas informações para o gerenciamento de desempenho e planejamento de capacidade:<br /><br /> -Canais são criados.<br />-Ponto de extremidade ouvintes são criados.<br />-Mensagem de transporte de insere/folhas.<br />-Token de segurança é recuperado.<br />-Configuração é lida.|Administradores<br /><br /> Desenvolvedores de aplicativos<br /><br /> Desenvolvedores de produtos.|  
|Detalhado|"Positivos" eventos: eventos que marcam marcos bem-sucedida.|Eventos de nível baixo para o código do usuário e a manutenção são emitidos.|Em geral, você pode usar esse nível para a otimização de depuração ou de aplicativo.<br /><br /> -Cabeçalho de mensagem compreendidos.|Administradores<br /><br /> Desenvolvedores de aplicativos<br /><br /> Desenvolvedores de produtos.|  
|ActivityTracing||Eventos de fluxo entre atividades de processamento e componentes.|Esse nível permite que os administradores e desenvolvedores correlacionem aplicativos no mesmo domínio do aplicativo:<br /><br /> -Rastreamentos de limites de atividades, como iniciar/parar.<br />-Rastreamentos de transferências.|Todos|  
|Todos||Aplicativo pode funcionar corretamente. Todos os eventos são emitidos.|Todos os eventos anteriores.|Todos|  
  
 Os níveis do detalhado para crítico são empilhados umas sobre as outras, ou seja, cada nível de rastreamento inclui todos os níveis acima dele, exceto o nível de Off. Por exemplo, um ouvinte está escutando em nível de aviso recebe rastreamentos crítico, erro e aviso. O nível All inclui eventos de modo detalhado para eventos de rastreamento crítico e a atividade.  
  
> [!CAUTION]
>  Os níveis de informações, detalhado e ActivityTracing geram vários rastreamentos, que pode afetar negativamente a taxa de transferência de mensagem se você tiver usado todos os recursos disponíveis no computador.  
  
## <a name="configuring-activity-tracing-and-propagation-for-correlation"></a>Configurando o rastreamento de atividades e propagação para correlação  
 O `activityTracing` valor especificado para o `switchValue` atributo é usado para habilitar o rastreamento de atividade, que emite rastreamentos de limites de atividade e transferências em pontos de extremidade.  
  
> [!NOTE]
>  Quando você usa determinados recursos de extensibilidade no WCF, você pode receber um <xref:System.NullReferenceException> quando o rastreamento de atividades está habilitado. Para corrigir esse problema, verifique o arquivo de configuração do seu aplicativo e certifique-se de que o `switchValue` de atributo para a origem do rastreamento não é definida como `activityTracing`.  
  
 O `propagateActivity` atributo indica se a atividade deve ser propagada para outros pontos de extremidade que participam de troca de mensagens. Ao definir esse valor como `true`, você pode colocar arquivos de rastreamento gerados por dois pontos de extremidade e observar como um conjunto de rastreamentos em um ponto de extremidade flui para um conjunto de rastreamentos em outro ponto de extremidade.  
  
 Para obter mais informações sobre rastreamento de atividades e propagação, consulte [propagação](../../../../../docs/framework/wcf/diagnostics/tracing/propagation.md).  
  
 Ambos `propagateActivity` e `ActivityTracing` valores boolianos se aplicam a TraceSource a System. ServiceModel. O `ActivityTracing` valor também se aplica a qualquer fonte de rastreamento, incluindo aqueles definidos pelo usuário ou WCF.  
  
 Não é possível usar o `propagateActivity` atributo com fontes de rastreamento definidos pelo usuário. Para a propagação de ID de atividade de código de usuário, verifique se você não definir ServiceModel `ActivityTracing`, ao mesmo tempo, ServiceModel `propagateActivity` atributo definido como `true`.  
  
## <a name="see-also"></a>Consulte também
- [Rastreamento](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [Administração e diagnósticos](../../../../../docs/framework/wcf/diagnostics/index.md)
- [Como: Criar e inicializar ouvintes de rastreamento](https://go.microsoft.com/fwlink/?LinkId=94648)
- [Criando um TraceListener personalizado](https://go.microsoft.com/fwlink/?LinkId=96239)
