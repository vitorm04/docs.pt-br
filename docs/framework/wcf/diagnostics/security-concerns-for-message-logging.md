---
title: Problemas de segurança de registro em log de mensagens
ms.date: 03/30/2017
ms.assetid: 21f513f2-815b-47f3-85a6-03c008510038
ms.openlocfilehash: c5db9fbf0dfb91ecb903660ebfb42c33f55b27bc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933608"
---
# <a name="security-concerns-for-message-logging"></a>Problemas de segurança de registro em log de mensagens
Este tópico descreve como você pode proteger dados confidenciais de serem expostos em logs de mensagens, bem como eventos gerados pelo log de mensagens.  
  
## <a name="security-concerns"></a>Problemas de segurança  
  
### <a name="logging-sensitive-information"></a>Registrando informações confidenciais  
 Windows Communication Foundation (WCF) não modifica nenhum dado em cabeçalhos e corpo específicos do aplicativo. O WCF também não rastreia informações pessoais em cabeçalhos específicos do aplicativo ou dados de corpo.  
  
 Quando o log de mensagens está habilitado, as informações pessoais em cabeçalhos específicos do aplicativo, como uma cadeia de caracteres de consulta; e as informações de corpo, como um número de cartão de crédito, podem se tornar visíveis nos logs. O implantador de aplicativos é responsável por impor o controle de acesso nos arquivos de configuração e de log. Se você não quiser que esse tipo de informação fique visível, desabilite o registro em log ou filtre parte dos dados se quiser compartilhar os logs.  
  
 As dicas a seguir podem ajudá-lo a impedir que o conteúdo de um arquivo de log seja exposto de forma não intencional:  
  
- Verifique se os arquivos de log estão protegidos por listas de controle de acesso (ACL) tanto em cenários de host da Web quanto de hospedagem interna.  
  
- Escolha uma extensão de arquivo que não possa ser facilmente servida usando uma solicitação da Web. Por exemplo, a extensão de arquivo. xml não é uma opção segura. Você pode verificar o guia de administração do Serviços de Informações da Internet (IIS) para ver uma lista de extensões que podem ser servidas.  
  
- Especifique um caminho absoluto para o local do arquivo de log, que deve estar fora do diretório público do Web host vroot para impedir que ele seja acessado por uma parte externa usando um navegador da Web.  
  
 Por padrão, as chaves e as informações de identificação pessoal (PII), como nome de usuário e senha, não são registradas em rastreamentos e mensagens registradas. Um administrador de máquina, no entanto, `enableLoggingKnownPII` pode usar o `machineSettings` atributo no elemento do arquivo Machine. config para permitir que os aplicativos em execução no computador registrem PII (informações de identificação pessoal) conhecidas. A configuração a seguir demonstra como fazer isso:  
  
```xml  
<configuration>  
   <system.serviceModel>  
      <machineSettings enableLoggingKnownPii="true"/>  
   </system.serviceModel>  
</configuration>   
```  
  
 Um implantador de aplicativo pode usar `logKnownPii` o atributo no arquivo app. config ou Web. config para habilitar o log de PII da seguinte maneira:  
  
```xml  
<system.diagnostics>  
  <sources>  
      <source name="System.ServiceModel.MessageLogging"  
        logKnownPii="true">  
        <listeners>  
                 <add name="messages"  
                 type="System.Diagnostics.XmlWriterTraceListener"  
                 initializeData="c:\logs\messages.svclog" />  
          </listeners>  
      </source>  
    </sources>  
</system.diagnostics>  
```  
  
 Somente quando as duas configurações `true` são o log de PII habilitado. A combinação de duas opções permite a flexibilidade de registrar PII conhecida para cada aplicativo.  
  
> [!IMPORTANT]
> [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] `true` Nos sinalizadores e`logKnownPii`também devem ser definidos como no arquivo Web. config ou no arquivo app. config para habilitar o log de PII, como mostrado no exemplo `<system.serviceModel><messageLogging logEntireMessage="true" logKnownPii="true" …`a seguir. `logEntireMessage`  
  
 Você deve estar ciente de que, se você especificar duas ou mais fontes personalizadas em um arquivo de configuração, somente os atributos da primeira fonte serão lidos. Os outros são ignorados. Isso significa que, para o seguinte app. config, o arquivo, PII não é registrado para ambas as fontes, embora o log de PII esteja explicitamente habilitado para a segunda fonte.  
  
```xml  
<system.diagnostics>  
   <sources>  
      <source name="System.ServiceModel.MessageLogging"  
              logKnownPii="false">  
              <listeners>  
                 <add name="messages"  
                      type="System.Diagnostics.XmlWriterTraceListener"  
                      initializeData="c:\logs\messages.svclog" />  
              </listeners>  
            </source>  
      <source name="System.ServiceModel"   
              logKnownPii="true">  
              <listeners>  
                 <add name="traces"  
                      type="System.Diagnostics.XmlWriterTraceListener"  
                      initializeData="c:\logs\traces.svclog" />  
              </listeners>  
      </source>  
   </sources>  
</system.diagnostics>  
```  
  
 Se o `<machineSettings enableLoggingKnownPii="Boolean"/>` elemento existir fora do arquivo Machine. config, o sistema lançará <xref:System.Configuration.ConfigurationErrorsException>um.  
  
 As alterações entram em vigor somente quando o aplicativo é iniciado ou reiniciado. Um evento é registrado na inicialização quando ambos os atributos são definidos `true`como. Um evento também será registrado se `logKnownPii` for definido como `true` , `enableLoggingKnownPii` mas `false`for.  
  
 O administrador do computador e o implantador de aplicativos devem ter muito cuidado ao usar essas duas opções. Se o log de PII estiver habilitado, as chaves de segurança e PII serão registradas. Se estiver desabilitado, os dados confidenciais e específicos do aplicativo ainda serão registrados em cabeçalhos e corpos de mensagens. Para obter uma discussão mais detalhada sobre privacidade e proteger a PII de ser exposta, consulte [privacidade do usuário](https://go.microsoft.com/fwlink/?LinkID=94647).  
  
> [!CAUTION]
>  PII não está oculta em mensagens malformadas. Essa mensagem é registrada como está sem qualquer modificação. Os atributos mencionados anteriormente não têm nenhum efeito sobre isso.  
  
### <a name="custom-trace-listener"></a>Ouvinte de rastreamento personalizado  
 A adição de um ouvinte de rastreamento personalizado na origem do rastreamento de log de mensagens é um privilégio que deve ser restrito ao administrador. Isso ocorre porque os ouvintes personalizados mal-intencionados podem ser configurados para enviar mensagens remotamente, o que leva à divulgação de informações confidenciais. Além disso, se você configurar um ouvinte personalizado para enviar mensagens na conexão, como, para um banco de dados remoto, deverá impor o controle de acesso apropriado nos logs de mensagens no computador remoto.  
  
## <a name="events-triggered-by-message-logging"></a>Eventos disparados pelo log de mensagens  
 O a seguir lista todos os eventos emitidos pelo log de mensagens.  
  
- Log de mensagens em: Esse evento é emitido quando o log de mensagens está habilitado na configuração ou por meio do WMI. O conteúdo do evento é "o log de mensagens foi ativado. As informações confidenciais podem ser registradas em texto não criptografado, mesmo que elas tenham sido criptografadas na conexão, por exemplo, corpos de mensagens. "  
  
- Registro em log de mensagem: Esse evento é emitido quando o log de mensagens é desabilitado por meio do WMI. O conteúdo do evento é "o registro de mensagem foi desativado".  
  
- Registrar PII conhecido em: Esse evento é emitido quando o log de PII conhecido está habilitado. Isso acontece quando o `enableLoggingKnownPii` atributo `machineSettings` no elemento do arquivo Machine. config é definido como `true`, e o `logKnownPii` atributo do `source` elemento no arquivo app. config ou Web. config é definido como `true`.  
  
- PII conhecida de log não permitido: Esse evento é emitido quando o log de PII conhecido não é permitido. Isso acontece quando o `logKnownPii` atributo `source` do elemento no arquivo app. config ou Web. config é definido como `true`, mas o `enableLoggingKnownPii` atributo no `machineSettings` elemento do arquivo Machine. config é definido como `false`. Nenhuma exceção é lançada.  
  
 Esses eventos podem ser exibidos na ferramenta de Visualizador de Eventos que vem com o Windows. Para obter mais informações sobre isso, consulte [log de eventos](../../../../docs/framework/wcf/diagnostics/event-logging/index.md).  
  
## <a name="see-also"></a>Consulte também

- [Registro de mensagens em log](../../../../docs/framework/wcf/diagnostics/message-logging.md)
- [Questões de segurança e dicas úteis para rastreamento](../../../../docs/framework/wcf/diagnostics/tracing/security-concerns-and-useful-tips-for-tracing.md)
