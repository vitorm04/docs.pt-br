---
title: Problemas de segurança de registro em log de mensagens
ms.date: 03/30/2017
ms.assetid: 21f513f2-815b-47f3-85a6-03c008510038
ms.openlocfilehash: bb1a6ab84ceba27b398d397b4407a55aa02c4cae
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185768"
---
# <a name="security-concerns-for-message-logging"></a>Problemas de segurança de registro em log de mensagens
Este tópico descreve como você pode proteger dados confidenciais de serem expostos em registros de mensagens, bem como eventos gerados pelo registro de mensagens.  
  
## <a name="security-concerns"></a>Problemas de segurança  
  
### <a name="logging-sensitive-information"></a>Registro de informações confidenciais  
 O Windows Communication Foundation (WCF) não modifica nenhum dado em cabeçalhos e corpo específicos de aplicativos. O WCF também não rastreia informações pessoais em cabeçalhos específicos de aplicativos ou dados do corpo.  
  
 Quando o registro de mensagens estiver ativado, as informações pessoais em cabeçalhos específicos do aplicativo, como, uma seqüência de consultas; e informações do corpo, como, por isso, um número de cartão de crédito, podem se tornar visíveis nos registros. O implantador de aplicativos é responsável por reforçar o controle de acesso na configuração e registrar arquivos. Se você não quiser que esse tipo de informação seja visível, você deve desativar o registro ou filtrar parte dos dados se quiser compartilhar os logs.  
  
 As seguintes dicas podem ajudá-lo a evitar que o conteúdo de um arquivo de log seja exposto sem querer:  
  
- Certifique-se de que os arquivos de log estão protegidos por Listas de Controle de Acesso (ACL) tanto em cenários de host da Web quanto de auto-host.  
  
- Escolha uma extensão de arquivo que não possa ser facilmente atendida usando uma solicitação da Web. Por exemplo, a extensão de arquivo .xml não é uma escolha segura. Você pode conferir o guia de administração de ISS (Serviços de Informações da Internet) para ver uma lista das extensões que podem ser usadas.  
  
- Especifique um caminho absoluto para o local do arquivo de log, que deve estar fora do diretório público vroot do host da Web para evitar que ele seja acessado por uma parte externa usando um navegador da Web.  
  
 Por padrão, chaves e informações pessoalmente identificáveis (PII), como nome de usuário e senha, não estão registradas em vestígios e mensagens registradas. Um administrador de máquina, `enableLoggingKnownPII` no entanto, pode usar o atributo no `machineSettings` elemento do arquivo Machine.config para permitir que os aplicativos em execução na máquina registrem informações pessoais identificáveis (PII). A seguinte configuração demonstra como fazer isso:  
  
```xml  
<configuration>  
   <system.serviceModel>  
      <machineSettings enableLoggingKnownPii="true"/>  
   </system.serviceModel>  
</configuration>
```  
  
 Um implantador de aplicativos `logKnownPii` pode usar o atributo no arquivo App.config ou Web.config para ativar o registro de PII da seguinte forma:  
  
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
  
 Somente quando ambas `true` as configurações estiverem habilitadas para o login do PII. A combinação de dois switches permite a flexibilidade de registrar PII conhecido para cada aplicativo.  
  
> [!IMPORTANT]
> Nos [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] `logEntireMessage` e `logKnownPii` os sinalizadores `true` também devem ser definidos no arquivo Web.config ou no arquivo App.config para ativar o registro do PII, como mostrar no exemplo a seguir `<system.serviceModel><messageLogging logEntireMessage="true" logKnownPii="true" …`.  
  
 Você deve estar ciente de que se você especificar duas ou mais fontes personalizadas em um arquivo de configuração, apenas os atributos da primeira fonte serão lidos. Os outros são ignorados. Isso significa que, para o seguinte App.config, file, o PII não está registrado para ambas as fontes, embora o registro pii esteja explicitamente habilitado para a segunda fonte.  
  
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
  
 Se `<machineSettings enableLoggingKnownPii="Boolean"/>` o elemento existir fora do arquivo Machine.config, o sistema lança um <xref:System.Configuration.ConfigurationErrorsException>.  
  
 As alterações só são eficazes quando o aplicativo é iniciado ou reiniciado. Um evento é registrado na inicialização quando `true`ambos os atributos são definidos para . Um evento também é `logKnownPii` registrado `true` se `enableLoggingKnownPii` `false`estiver definido, mas é .  
  
 O administrador da máquina e o implantador de aplicativos devem ter extrema cautela ao usar estes dois switches. Se o registro do PII estiver ativado, as chaves de segurança e o PII serão registrados. Se estiver desativado, dados confidenciais e específicos do aplicativo ainda serão registrados em cabeçalhos de mensagens e corpos. Para uma discussão mais aprofundada sobre privacidade e proteção do PII de ser exposta, consulte [Privacidade do Usuário](https://docs.microsoft.com/previous-versions/dotnet/articles/aa480490(v=msdn.10)).  
  
> [!CAUTION]
> O PII não está escondido em mensagens malformadas. Tais mensagens são registradas como-é sem qualquer modificação. Atributos mencionados anteriormente não têm efeito sobre isso.  
  
### <a name="custom-trace-listener"></a>Ouvinte de rastreamento personalizado  
 Adicionar um ouvinte de rastreamento personalizado na fonte de rastreamento de registro de mensagens é um privilégio que deve ser restrito ao administrador. Isso porque ouvintes personalizados maliciosos podem ser configurados para enviar mensagens remotamente, o que leva à divulgação de informações confidenciais. Além disso, se você configurar um ouvinte personalizado para enviar mensagens no fio, como, em um banco de dados remoto, você deve impor o controle de acesso adequado nos registros de mensagens na máquina remota.  
  
## <a name="events-triggered-by-message-logging"></a>Eventos desencadeados pelo registro de mensagens  
 A seguir lista todos os eventos emitidos pelo registro de mensagens.  
  
- Registro de mensagens: Este evento é emitido quando o registro de mensagens é ativado na configuração ou através do WMI. O conteúdo do evento é "O registro de mensagens foi ligado. Informações confidenciais podem ser registradas em texto claro, mesmo que tenham sido criptografadas no fio, por exemplo, corpos de mensagens."  
  
- Desativação de mensagens: Este evento é emitido quando o registro de mensagens é desativado através do WMI. O conteúdo do evento é "O registro de mensagens foi desligado".  
  
- Log Known PII On: Este evento é emitido quando o registro de PII conhecido é ativado. Isso acontece `enableLoggingKnownPii` quando o `machineSettings` atributo no elemento do arquivo `true`Machine.config é definido para , e o atributo `logKnownPii` `source` do `true`elemento no arquivo App.config ou Web.config é definido como .  
  
- Log Known PII Não Permitido: Este evento é emitido quando o registro de PII conhecido não é permitido. Isso acontece `logKnownPii` quando o `source` atributo do elemento no arquivo App.config `true`ou Web.config `machineSettings` é definido para , mas `false`o atributo `enableLoggingKnownPii` no elemento do arquivo Machine.config é definido como . Nenhuma exceção é lançada.  
  
 Esses eventos podem ser visualizados na ferramenta Event Viewer que vem com o Windows. Para obter mais informações sobre isso, consulte [Registro de eventos](./event-logging/index.md).  
  
## <a name="see-also"></a>Confira também

- [Registro em log de mensagens](message-logging.md)
- [Preocupações de segurança e dicas úteis para rastreamento](./tracing/security-concerns-and-useful-tips-for-tracing.md)
