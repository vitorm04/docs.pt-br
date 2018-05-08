---
title: Problemas de segurança de registro em log de mensagens
ms.date: 03/30/2017
ms.assetid: 21f513f2-815b-47f3-85a6-03c008510038
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: c8b2fe3300bacc76e63f9d533c613171d03600d7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="security-concerns-for-message-logging"></a>Problemas de segurança de registro em log de mensagens
Este tópico descreve como você pode proteger dados confidenciais de serem expostas em logs de mensagem, bem como os eventos gerados pelo log de mensagens.  
  
## <a name="security-concerns"></a>Problemas de segurança  
  
### <a name="logging-sensitive-information"></a>O log de informações confidenciais  
 Windows Communication Foundation (WCF) não modifica os dados no cabeçalhos específicos do aplicativo e corpo. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] também não rastreia informações pessoais em cabeçalhos específicos do aplicativo ou o corpo de dados.  
  
 Quando o log de mensagens está habilitado, as informações pessoais em cabeçalhos específicos do aplicativo, como uma cadeia de caracteres de consulta; e corpo informações, como um número de cartão de crédito, pode se tornar visíveis nos logs. O implantador de aplicativo é responsável por impor o controle de acesso nos arquivos de configuração e de log. Se você não deseja que esse tipo de informação fique visível, você deve desabilitar o log ou filtrar a parte dos dados se você quiser compartilhar os logs.  
  
 As dicas a seguir podem ajudar a impedir que o conteúdo de um arquivo de log seja exposto indesejadamente:  
  
-   Certifique-se de que o log de arquivos estão protegidos pelo controle listas acesso (ACL) no host da Web e cenários de hospedagem interna.  
  
-   Escolha uma extensão de arquivo não pode ser facilmente exposta com uma solicitação da Web. Por exemplo, a extensão de arquivo. XML não é uma opção segura. Você pode verificar o guia de administração de serviços de informações da Internet (IIS) para ver uma lista de extensões que podem ser usadas.  
  
-   Especifique um caminho absoluto para o local de arquivo de log, que deve estar fora do diretório Web host vroot público para impedir que ele seja acessado por terceiros usando um navegador da Web.  
  
 Por padrão, as chaves e informações de identificação pessoal (PII), como nome de usuário e senha não são registradas em rastreamentos e registrado mensagens. No entanto, um administrador de máquina, pode usar o `enableLoggingKnownPII` atributo o `machineSettings` elemento do arquivo Machine. config para permitir que aplicativos em execução no computador para fazer logon conhecidas informações de identificação pessoal (PII). A configuração a seguir demonstra como fazer isso:  
  
```xml  
<configuration>  
   <system.serviceModel>  
      <machineSettings enableLoggingKnownPii="true"/>  
   </system.serviceModel>  
</configuration>   
```  
  
 Implantador um aplicativo pode usar o `logKnownPii` atributo no arquivo de App. config ou Web. config para habilitar o log de PII da seguinte maneira:  
  
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
  
 Somente quando as duas configurações são `true` é o log de PII habilitado. A combinação das duas opções permite a flexibilidade fazer logon PII conhecido para cada aplicativo.  
  
> [!IMPORTANT]
>  Em [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] o `logEntireMessage` e `logKnownPii` sinalizadores também devem ser definidos como `true` no arquivo Web. config ou o arquivo App. config para habilitar o log de PII, como mostrar no exemplo a seguir `<system.serviceModel><messageLogging logEntireMessage="true" logKnownPii="true" …`.  
  
 Você deve estar ciente de que, se você especificar dois ou mais fontes personalizadas em um arquivo de configuração, somente os atributos da primeira fonte são lidos. Os outros são ignorados. Isso significa que, para o seguinte App. config, arquivo, PII não é conectado para ambas as fontes, embora o log de PII explicitamente está habilitado para a segunda fonte.  
  
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
  
 O administrador da máquina e o implantador de aplicativo deve ter muito cuidado ao usar essas duas opções. Se o log de PII estiver habilitado, as chaves de segurança e informações de identificação pessoal são registradas. Se ele estiver desabilitado, os dados específicos do aplicativo ainda estão conectados em cabeçalhos e corpos. Para obter uma discussão mais completa sobre privacidade e proteção de informações de identificação pessoal sejam expostas, consulte [privacidade do usuário](http://go.microsoft.com/fwlink/?LinkID=94647).  
  
> [!CAUTION]
>  Informações de identificação pessoal não está oculto em mensagens malformadas. Tal mensagem são registradas como-sem qualquer modificação. Atributos mencionados anteriormente não têm efeito sobre isso.  
  
### <a name="custom-trace-listener"></a>Ouvinte de rastreamento personalizado  
 Adicionando um ouvinte de rastreamento no log de mensagem de origem de rastreamento é um privilégio que deve ser restrita para o administrador. Isso ocorre porque mal-intencionado ouvintes personalizados podem ser configurados para enviar mensagens remotamente, o que leva à divulgação de informações confidenciais. Além disso, se você configurar um ouvinte personalizado para enviar mensagens na rede, como um banco de dados remoto, você deve aplicar o controle de acesso adequada nos logs de mensagem no computador remoto.  
  
## <a name="events-triggered-by-message-logging"></a>Eventos disparados pelo log de mensagens  
 O exemplo a seguir lista todos os eventos emitidos pelo log de mensagens.  
  
-   Registro em log da mensagem: esse evento é emitido quando o log de mensagens está habilitado na configuração ou por meio do WMI. O conteúdo do evento é "mensagem de log foi ativado. Informações confidenciais podem ser registradas em texto não criptografado, mesmo se eles foram criptografados durante a transmissão, por exemplo, corpos de mensagens."  
  
-   Fazer logoff da mensagem: esse evento é emitido quando o log de mensagens é desabilitado por meio do WMI. O conteúdo do evento é "Mensagem de log foi desativado."  
  
-   Log conhecido PII em: Esse evento é emitido quando o log de PII conhecido está habilitado. Isso acontece quando o `enableLoggingKnownPii` atributo o `machineSettings` do arquivo Machine. config é definido como `true`e o `logKnownPii` atributo do `source` no arquivo de App. config ou Web. config é definido como `true`.  
  
-   Log conhecidos PII não permitida: esse evento é emitido quando o log de PII conhecido não é permitido. Isso acontece quando o `logKnownPii` atributo do `source` no arquivo de App. config ou Web. config é definido como `true`, mas o `enableLoggingKnownPii` atributo no `machineSettings` do arquivo Machine. config é definido como `false`. Nenhuma exceção é lançada.  
  
 Esses eventos podem ser exibidos na ferramenta do Visualizador de eventos que vem com o Windows. Para obter mais informações sobre isso, consulte [log de eventos](../../../../docs/framework/wcf/diagnostics/event-logging/index.md).  
  
## <a name="see-also"></a>Consulte também  
 [Registro de mensagens em log](../../../../docs/framework/wcf/diagnostics/message-logging.md)  
 [Questões de segurança e dicas úteis para rastreamento](../../../../docs/framework/wcf/diagnostics/tracing/security-concerns-and-useful-tips-for-tracing.md)
