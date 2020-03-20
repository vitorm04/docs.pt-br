---
title: Configurando o rastreamento
ms.date: 03/30/2017
helpviewer_keywords:
- tracing [WCF]
ms.assetid: 82922010-e8b3-40eb-98c4-10fc05c6d65d
ms.openlocfilehash: d8b216bf5497cf2a1faa2fa24ba1d8b3102f6f10
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185747"
---
# <a name="configuring-tracing"></a>Configurando o rastreamento
Este tópico descreve como você pode habilitar o rastreamento, configurar fontes de rastreamento para emitir vestígios e definir níveis de rastreamento, definir rastreamento de atividade e propagação para suportar correlação de rastreamento de ponta a ponta e definir os ouvintes de rastreamento para acessar vestígios.  
  
 Para obter recomendações de configurações de rastreamento no ambiente de produção ou depuração, consulte [As configurações recomendadas para rastreamento e registro de mensagens](../../../../../docs/framework/wcf/diagnostics/tracing/recommended-settings-for-tracing-and-message-logging.md).  
  
> [!IMPORTANT]
> No Windows 8, você deve executar seu aplicativo elevado (Executar como administrador) para que seu aplicativo gere registros de rastreamento.  
  
## <a name="enabling-tracing"></a>Habilitar o rastreamento  
 O Windows Communication Foundation (WCF) produz os seguintes dados para rastreamento de diagnóstico:  
  
- Rastreamentos para marcos de processo em todos os componentes dos aplicativos, como chamadas de operação, exceções de código, avisos e outros eventos de processamento significativos.  
  
- Eventos de erro do Windows quando o recurso de rastreamento não funciona. Consulte [O Registro de Eventos](../../../../../docs/framework/wcf/diagnostics/event-logging/index.md).  
  
 O rastreamento wcf é <xref:System.Diagnostics>construído em cima de . Para usar o rastreamento, você deve definir fontes de rastreamento no arquivo de configuração ou em código. O WCF define uma fonte de rastreamento para cada conjunto WCF. A `System.ServiceModel` fonte de rastreamento é a fonte de rastreamento mais geral do WCF e registra os marcos de processamento em toda a pilha de comunicação do WCF, desde a entrada/saída do transporte até a entrada/saída do código do usuário. A `System.ServiceModel.MessageLogging` fonte de rastreamento registra todas as mensagens que fluem pelo sistema.  
  
 O rastreamento não é habilitado por padrão. Para ativar o rastreamento, você deve criar um ouvinte de rastreamento e definir um nível de rastreamento diferente de "Off" para a fonte de rastreamento selecionada na configuração; caso contrário, o WCF não gera nenhum traço. Se você não especificar um ouvinte, o rastreamento será desativado automaticamente. Se um ouvinte for definido, mas nenhum nível for especificado, o nível será definido como "Off" por padrão, o que significa que nenhum traço é emitido.  
  
 Se você usar pontos de extensibilidade WCF, como invocadores de operação personalizados, você deve emitir seus próprios traços. Isso porque se você implementar um ponto de extensibilidade, o WCF não poderá mais emitir os traços padrão no caminho padrão. Se você não implementar suporte manual de rastreamento emitindo vestígios, você pode não ver os traços esperados.  
  
 Você pode configurar o rastreamento editando o arquivo de configuração do aplicativo — seja o Web.config para aplicativos hospedados na Web ou o Appname.exe.config para aplicativos auto-hospedados. O seguinte é um exemplo de tal edição. Para obter mais informações sobre essas configurações, consulte a seção "Configurando ouvintes de rastreamento para consumir vestígios".  
  
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
> Para editar o arquivo de configuração de um projeto de serviço WCF no Visual Studio, clique com o botão direito do mouse no arquivo de configuração do aplicativo — seja na Web.config para aplicativos hospedados na Web ou no Appname.exe.config para aplicativo auto-hospedado no **Solution Explorer**. Em seguida, escolha o item Editar o menu de contexto **de configuração do WCF.** Isso lança a [Ferramenta de Editor de Configuração (SvcConfigEditor.exe),](../../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)que permite modificar as configurações dos serviços WCF usando uma interface gráfica do usuário.  
  
## <a name="configuring-trace-sources-to-emit-traces"></a>Configurando fontes de rastreamento para emitir vestígios  
 O WCF define uma fonte de rastreamento para cada montagem. Os traços gerados dentro de uma montagem são acessados pelos ouvintes definidos para essa fonte. As seguintes fontes de rastreamento são definidas:  
  
- System.ServiceModel: Registra todas as etapas do processamento do WCF, sempre que a configuração é lida, uma mensagem é processada no transporte, processamento de segurança, uma mensagem é enviada no código do usuário, e assim por diante.  
  
- System.ServiceModel.MessageLogging: Registra todas as mensagens que fluem pelo sistema.  
  
- System.IdentityModel.  
  
- System.ServiceModel.Activation.  
  
- System.IO.Log: Registro para a interface .NET Framework para o CLFS (Common Log File System).  
  
- System.Runtime.Serialização: Registra quando os objetos são lidos ou gravados.  
  
- Cardspace.  
  
 Você pode configurar cada fonte de rastreamento para usar o mesmo ouvinte (compartilhado), conforme indicado no exemplo de configuração a seguir.  
  
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
  
 Além disso, você pode adicionar fontes de rastreamento definidas pelo usuário, como demonstrado pelo exemplo a seguir, para emitir traços de código do usuário.  
  
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
  
 Para obter mais informações sobre a criação de fontes de rastreamento definidas pelo usuário, consulte [Extending Tracing](../../../../../docs/framework/wcf/samples/extending-tracing.md).  
  
## <a name="configuring-trace-listeners-to-consume-traces"></a>Configurando rastreadores para consumir vestígios  
 Em tempo de execução, o WCF alimenta dados de rastreamento para os ouvintes que processam os dados. O WCF fornece vários <xref:System.Diagnostics>ouvintes predefinidos para , que diferem no formato que eles usam para a saída. Você também pode adicionar tipos de ouvintes personalizados.  
  
 Você pode usar `add` para especificar o nome e o tipo do ouvinte de rastreamento que deseja usar. Em nossa configuração de exemplo, nomeamos o Ouvinte `traceListener` e`System.Diagnostics.XmlWriterTraceListener`adicionamos o rastreador padrão .NET Framework ( ) como o tipo que queremos usar. Você pode adicionar qualquer número de ouvintes de rastreamento para cada fonte. Se o ouvinte de rastreamento emite o rastreamento para um arquivo, você deve especificar o local e o nome do arquivo de saída no arquivo de configuração. Isso é feito `initializeData` definindo o nome do arquivo para esse ouvinte. Se você não especificar um nome de arquivo, um nome de arquivo aleatório será gerado com base no tipo de ouvinte usado. Se <xref:System.Diagnostics.XmlWriterTraceListener> for usado, um nome de arquivo sem extensão será gerado. Se você implementar um ouvinte personalizado, você também poderá usar esse atributo para receber dados de inicialização que não sejam um nome de arquivo. Por exemplo, você pode especificar um identificador de banco de dados para este atributo.  
  
 Você pode configurar um ouvinte de rastreamento personalizado para enviar vestígios no fio, por exemplo, para um banco de dados remoto. Como implantador de aplicativos, você deve impor o controle de acesso adequado nos registros de rastreamento na máquina remota.  
  
 Você também pode configurar um ouvinte de rastreamento programáticamente. Para obter mais informações, [consulte Como: Criar e inicializar os rastreadores ouvintes](../../../debug-trace-profile/how-to-create-and-initialize-trace-listeners.md) e [criar um TraceListener personalizado](https://docs.microsoft.com/archive/msdn-magazine/2006/april/clr-inside-out-extending-system-diagnostics).  
  
> [!CAUTION]
> Como `System.Diagnostics.XmlWriterTraceListener` não é seguro para rosca, a fonte de rastreamento pode bloquear recursos exclusivamente ao fazer a saída de vestígios. Quando muitos segmentos de saída rastreiam uma fonte de rastreamento configurada para usar este ouvinte, pode ocorrer contenção de recursos, o que resulta em um problema de desempenho significativo. Para resolver esse problema, você deve implementar um ouvinte personalizado que seja seguro para threads.  
  
## <a name="trace-level"></a>Nível de rastreamento:  
 O nível de rastreamento `switchValue` é controlado pela configuração da fonte de rastreamento. Os níveis de rastreamento disponíveis são descritos na tabela a seguir.  
  
|Nível de rastreamento:|Natureza dos Eventos Rastreados|Conteúdo dos Eventos Rastreados|Eventos rastreados|Alvo do usuário|  
|-----------------|----------------------------------|-----------------------------------|--------------------|-----------------|  
|Desativado|N/D|N/D|Nenhum vestígio é emitido.|N/D|  
|Crítico|Eventos "negativos": eventos que indicam um processamento inesperado ou uma condição de erro.||Exceções não tratadas, incluindo as seguintes, são registradas:<br /><br /> - OutOfMemoryException<br />- ThreadAbortException (o CLR invoca qualquer ThreadAbortExceptionHandler)<br />- StackOverflowException (não pode ser capturado)<br />- ConfiguraçãoSDeexceto de erros<br />- SEHException<br />- Erros de início de aplicação<br />- Eventos failfast<br />- Sistema trava<br />- Mensagens venenosas: traços de mensagens que causam a falha do aplicativo.|Administradores<br /><br /> Desenvolvedores de aplicativos|  
|Erro|Eventos "negativos": eventos que indicam um processamento inesperado ou uma condição de erro.|Um processamento inesperado aconteceu. O aplicativo não foi capaz de executar uma tarefa como esperado. No entanto, o aplicativo ainda está em funcionamento.|Todas as exceções estão registradas.|Administradores<br /><br /> Desenvolvedores de aplicativos|  
|Aviso|Eventos "negativos": eventos que indicam um processamento inesperado ou uma condição de erro.|Um possível problema ocorreu ou pode ocorrer, mas a aplicação ainda funciona corretamente. No entanto, pode não continuar funcionando corretamente.|- O aplicativo está recebendo mais solicitações do que suas configurações de estrangulamento permitem.<br />- A fila de recepção está próxima de sua capacidade máxima configurada.<br />- O tempo está fora.<br />- As credenciais são rejeitadas.|Administradores<br /><br /> Desenvolvedores de aplicativos|  
|Informações|Eventos "positivos": eventos que marcam marcos de sucesso|Marcos importantes e bem-sucedidos da execução do aplicativo, independentemente de o aplicativo estar funcionando corretamente ou não.|Em geral, são geradas mensagens úteis para monitorar e diagnosticar o estado do sistema, medir o desempenho ou traçar perfis. Você pode usar essas informações para planejamento de capacidade e gerenciamento de desempenho:<br /><br /> - Canais são criados.<br />- Ouvintes de ponto final são criados.<br />- A mensagem entra/sai do transporte.<br />- O token de segurança foi recuperado.<br />- A configuração é lida.|Administradores<br /><br /> Desenvolvedores de aplicativos<br /><br /> Desenvolvedores de produtos.|  
|Detalhado|Eventos "positivos": eventos que marcam marcos de sucesso.|Eventos de baixo nível para código de usuário e manutenção são emitidos.|Em geral, você pode usar este nível para depuração ou otimização de aplicativos.<br /><br /> - Entendido cabeçalho de mensagem.|Administradores<br /><br /> Desenvolvedores de aplicativos<br /><br /> Desenvolvedores de produtos.|  
|ActivityTracing||Eventos de fluxo entre atividades de processamento e componentes.|Esse nível permite que administradores e desenvolvedores correlacionam aplicativos no mesmo domínio de aplicativos:<br /><br /> - Traça para limites de atividade, como início/parada.<br />- Rastros para transferências.|Todos|  
|Todos||A aplicação pode funcionar corretamente. Todos os eventos são emitidos.|Todos os eventos anteriores.|Todos|  
  
 Os níveis de Verbose a Crítico são empilhados em cima um do outro, ou seja, cada nível de traço inclui todos os níveis acima dele, exceto o nível Off. Por exemplo, um ouvinte que ouve no nível de Aviso recebe traços críticos, de erro e de aviso. O nível All inclui eventos de Verbose a Eventos críticos e de rastreamento de atividades.  
  
> [!CAUTION]
> Os níveis de Informações, Verbose e ActivityTracing geram muitos traços, que podem impactar negativamente o throughput de mensagens se você tiver usado todos os recursos disponíveis na máquina.  
  
## <a name="configuring-activity-tracing-and-propagation-for-correlation"></a>Configurando rastreamento de atividades e propagação para correlação  
 O `activityTracing` valor especificado `switchValue` para o atributo é usado para permitir o rastreamento de atividades, que emite traços para limites de atividade e transferências dentro de endpoints.  
  
> [!NOTE]
> Quando você usa certos recursos de extensibilidade <xref:System.NullReferenceException> no WCF, você pode obter um rastreamento de atividades ativado. Para corrigir esse problema, verifique o arquivo de `switchValue` configuração do aplicativo e `activityTracing`certifique-se de que o atributo para sua fonte de rastreamento não está definido como .  
  
 O `propagateActivity` atributo indica se a atividade deve ser propagada para outros pontos finais que participam da troca de mensagens. Ao definir esse `true`valor para , você pode pegar arquivos de rastreamento gerados por qualquer dois pontos finais e observar como um conjunto de traços em um ponto final fluiu para um conjunto de traços em outro ponto final.  
  
 Para obter mais informações sobre rastreamento e propagação de atividades, consulte [Propagação](../../../../../docs/framework/wcf/diagnostics/tracing/propagation.md).  
  
 Ambos `propagateActivity` `ActivityTracing` e valores booleanos aplicam-se ao System.ServiceModel TraceSource. O `ActivityTracing` valor também se aplica a qualquer fonte de rastreamento, incluindo WCF ou definidos pelo usuário.  
  
 Não é `propagateActivity` possível usar o atributo com fontes de rastreamento definidas pelo usuário. Para a propagação do ID de atividade de `ActivityTracing`código do usuário, certifique-se de não definir ServiceModel, enquanto ainda tiver o atributo ServiceModel `propagateActivity` definido como `true`.  
  
## <a name="see-also"></a>Confira também

- [Rastreamento](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [Administração e Diagnósticos](../../../../../docs/framework/wcf/diagnostics/index.md)
- [Como criar e inicializar ouvintes de rastreamento](../../../debug-trace-profile/how-to-create-and-initialize-trace-listeners.md)
- [Criando um tracelistener personalizado](https://docs.microsoft.com/archive/msdn-magazine/2006/april/clr-inside-out-extending-system-diagnostics)
