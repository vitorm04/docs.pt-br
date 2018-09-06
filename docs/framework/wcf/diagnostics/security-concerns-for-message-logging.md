---
title: Problemas de segurança de registro em log de mensagens
ms.date: 03/30/2017
ms.assetid: 21f513f2-815b-47f3-85a6-03c008510038
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 6da641ec5da20c80f4c1034ded8a3be7d036b5a8
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43785538"
---
# <a name="security-concerns-for-message-logging"></a>Problemas de segurança de registro em log de mensagens
Este tópico descreve como você pode proteger dados confidenciais sejam expostas em logs de mensagens, bem como os eventos gerados pelo log de mensagens.  
  
## <a name="security-concerns"></a>Problemas de segurança  
  
### <a name="logging-sensitive-information"></a>Registro em log informações confidenciais  
 Windows Communication Foundation (WCF) não modifica nenhum dado no cabeçalhos específicos de aplicativo e o corpo. O WCF também não rastreia informações pessoais em cabeçalhos específicos de aplicativo ou o corpo de dados.  
  
 Quando o log de mensagens está habilitado, informações pessoais nos cabeçalhos específicos do aplicativo, por exemplo, uma cadeia de caracteres de consulta; e o corpo de informações, como um número de cartão de crédito, pode se tornar visível nos logs. O implantador de aplicativo é responsável por impor o controle de acesso nos arquivos de configuração e de log. Se você não quiser esse tipo de informação fique visível, você deve desabilitar o log ou filtrar parte dos dados, se você quiser compartilhar os logs.  
  
 As dicas a seguir podem ajudar você a impedir que o conteúdo de um arquivo de log seja exposto indesejadamente:  
  
-   Certifique-se de que o log de arquivos são protegidos por listas de ACL (Access Control) no host da Web e cenários de hospedagem interna.  
  
-   Escolha uma extensão de arquivo que não pode ser facilmente exposta com uma solicitação da Web. Por exemplo, a extensão de arquivo. XML não é uma opção segura. Você pode verificar o guia de administração de serviços de informações da Internet (IIS) para ver uma lista de extensões que podem ser atendidas.  
  
-   Especifique um caminho absoluto para o local de arquivo de log, que deve estar fora do diretório da Web host vroot público impedi-lo de que está sendo acessado por terceiros usando um navegador da Web.  
  
 Por padrão, as chaves e informações de identificação pessoal (PII), como nome de usuário e senha não são registradas em rastreamentos e registrado mensagens. No entanto, um administrador do computador, pode usar o `enableLoggingKnownPII` de atributo no `machineSettings` elemento do arquivo Machine. config para permitir que aplicativos em execução no computador para fazer logon conhecidas informações de identificação pessoal (PII). A configuração a seguir demonstra como fazer isso:  
  
```xml  
<configuration>  
   <system.serviceModel>  
      <machineSettings enableLoggingKnownPii="true"/>  
   </system.serviceModel>  
</configuration>   
```  
  
 Um implantador de aplicativo, em seguida, pode usar o `logKnownPii` atributo no arquivo App. config ou Web. config para habilitar o log de PII da seguinte maneira:  
  
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
  
 Somente quando ambas as configurações forem `true` é o log de PII habilitado. A combinação de dois comutadores permite a flexibilidade fazer logon PII conhecido para cada aplicativo.  
  
> [!IMPORTANT]
>  Na [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] as `logEntireMessage` e `logKnownPii` sinalizadores também devem ser definidos como `true` no arquivo Web. config ou o arquivo App. config para habilitar o log de informações de identificação pessoal, conforme mostrado no exemplo a seguir `<system.serviceModel><messageLogging logEntireMessage="true" logKnownPii="true" …`.  
  
 Você deve estar ciente de que, se você especificar duas ou mais fontes personalizadas em um arquivo de configuração, somente os atributos da primeira fonte sejam lidos. Os outros são ignorados. Isso significa que, para seguir App. config, arquivo, PII não está conectado para ambas as fontes, mesmo que o registro em log o PII explicitamente está habilitado para a segunda fonte.  
  
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
  
 Se o `<machineSettings enableLoggingKnownPii="Boolean"/>` elemento existe fora do arquivo Machine. config, o sistema gera um <xref:System.Configuration.ConfigurationErrorsException>.  
  
 As alterações entrarão em vigor somente quando o aplicativo inicia ou reinicia. Um evento é registrado na inicialização, quando ambos os atributos são definidos como `true`. Também é registrado um evento se `logKnownPii` é definido como `true` mas `enableLoggingKnownPii` é `false`.  
  
 O administrador da máquina e o implantador de aplicativo deve ter muito cuidado ao usar essas duas opções. Se o log de informações de identificação pessoal é habilitado, as chaves de segurança e informações de identificação pessoal são registradas. Se ele estiver desabilitado, os dados confidenciais e específicos do aplicativo ainda estão conectados em corpos e cabeçalhos de mensagem. Para obter uma discussão mais completa sobre privacidade e proteção de PII sejam expostas, consulte [privacidade do usuário](https://go.microsoft.com/fwlink/?LinkID=94647).  
  
> [!CAUTION]
>  PII não fica oculta em mensagens malformadas. Como as mensagens são registrados como-está, sem qualquer modificação. Atributos mencionados anteriormente não têm efeito sobre isso.  
  
### <a name="custom-trace-listener"></a>Ouvinte de rastreamento personalizado  
 Adicionar um ouvinte de rastreamento no log de mensagem de origem de rastreamento é um privilégio que deve ser restritos ao administrador. Isso ocorre porque os ouvintes personalizados mal-intencionado podem ser configurados para enviar mensagens remotamente, o que leva à divulgação de informações confidenciais. Além disso, se você configurar um ouvinte personalizado para enviar mensagens durante a transmissão, tais como, um banco de dados remoto, você deve aplicar o controle de acesso adequado nos logs de mensagem no computador remoto.  
  
## <a name="events-triggered-by-message-logging"></a>Eventos disparados pelo log de mensagens  
 O exemplo a seguir lista todos os eventos emitidos pelo log de mensagens.  
  
-   Logon da mensagem: esse evento é emitido quando o log de mensagens está habilitado na configuração ou por meio do WMI. O conteúdo do evento é "mensagem de log foi ativado. Informações confidenciais podem ser registradas em texto não criptografado, mesmo se eles foram criptografados durante a transmissão, por exemplo, corpos de mensagem."  
  
-   Fazer logoff da mensagem: esse evento é emitido quando o log de mensagens é desabilitado por meio do WMI. O conteúdo do evento é "Mensagem de log foi desativado."  
  
-   Log conhecido PII em: Esse evento é emitido quando o log de PII conhecido é habilitado. Isso acontece quando o `enableLoggingKnownPii` de atributo na `machineSettings` do arquivo Machine. config é definido como `true`e o `logKnownPii` atributo do `source` elemento no arquivo App. config ou Web. config é definido como `true`.  
  
-   Faça logon conhecidos PII não permitido: esse evento é emitido quando o registro em log de PII conhecido não é permitido. Isso acontece quando o `logKnownPii` atributo do `source` elemento no arquivo App. config ou Web. config é definido como `true`, mas o `enableLoggingKnownPii` atributo no `machineSettings` elemento do arquivo Machine. config é definido como `false`. Nenhuma exceção é lançada.  
  
 Esses eventos podem ser exibidos na ferramenta do Visualizador de eventos que vem com o Windows. Para obter mais informações sobre isso, consulte [log de eventos](../../../../docs/framework/wcf/diagnostics/event-logging/index.md).  
  
## <a name="see-also"></a>Consulte também  
 [Registro de mensagens em log](../../../../docs/framework/wcf/diagnostics/message-logging.md)  
 [Questões de segurança e dicas úteis para rastreamento](../../../../docs/framework/wcf/diagnostics/tracing/security-concerns-and-useful-tips-for-tracing.md)
