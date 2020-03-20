---
title: Preocupações de segurança e dicas úteis para rastreamento
ms.date: 03/30/2017
ms.assetid: 88bc2880-ecb9-47cd-9816-39016a07076f
ms.openlocfilehash: 5ced4f3a3a5e83564703db88b28ee2b3c6eeb1a0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185717"
---
# <a name="security-concerns-and-useful-tips-for-tracing"></a>Preocupações de segurança e dicas úteis para rastreamento
Este tópico descreve como você pode proteger informações confidenciais de serem expostas, bem como dicas úteis ao usar o WebHost.  
  
## <a name="using-a-custom-trace-listener-with-webhost"></a>Usando um ouvinte de rastreamento personalizado com webhost  
 Se você está escrevendo seu próprio ouvinte de rastreamento, você deve estar ciente da possibilidade de que os traços possam ser perdidos no caso de um serviço hospedado na Web. Quando o WebHost recicla, ele desliga o processo ao vivo enquanto uma duplicata assume o cargo. No entanto, os dois processos ainda devem ter acesso ao mesmo recurso por algum tempo, que depende do tipo ouvinte. Neste caso, `XmlWriterTraceListener` cria um novo arquivo de rastreamento para o segundo processo; enquanto o rastreamento de eventos do Windows gerencia vários processos dentro da mesma sessão e dá acesso ao mesmo arquivo. Se o seu próprio ouvinte não fornecer funcionalidades semelhantes, os vestígios podem ser perdidos quando o arquivo é bloqueado pelos dois processos.  
  
 Você também deve estar ciente de que um ouvinte de rastreamento personalizado pode enviar vestígios e mensagens no fio, por exemplo, para um banco de dados remoto. Como implantador de aplicativos, você deve configurar ouvintes personalizados com controle de acesso apropriado. Você também deve aplicar o controle de segurança em qualquer informação pessoal que possa ser exposta no local remoto.  
  
## <a name="logging-sensitive-information"></a>Registro de informações confidenciais  
 Os rastreamentos contêm cabeçalhos de mensagem quando uma mensagem está no escopo. Quando o rastreamento é ativado, as informações pessoais em cabeçalhos específicos do aplicativo, como, uma seqüência de consultas; e informações do corpo, como, por isso, um número de cartão de crédito, podem se tornar visíveis nos registros. O implantador de aplicativos é responsável por reforçar o controle de acesso na configuração e rastrear arquivos. Se você não quiser que esse tipo de informação seja visível, você deve desativar o rastreamento ou filtrar parte dos dados se quiser compartilhar os registros de rastreamento.  
  
 As seguintes dicas podem ajudá-lo a evitar que o conteúdo de um arquivo de rastreamento seja exposto sem querer:  
  
- Certifique-se de que os arquivos de log estão protegidos por Listas de Controle de Acesso (ACL) tanto no WebHost quanto em cenários de auto-host.  
  
- Escolha uma extensão de arquivo que não possa ser facilmente atendida usando uma solicitação da Web. Por exemplo, a extensão de arquivo .xml não é uma escolha segura. Você pode verificar o guia de administração do IIS para ver uma lista de extensões que podem ser atendidas.  
  
- Especifique um caminho absoluto para o local do arquivo de log, que deve estar fora do diretório público vroot do WebHost para evitar que ele seja acessado por uma parte externa usando um navegador da Web.  
  
 Por padrão, chaves e informações pessoalmente identificáveis (PII), como nome de usuário e senha, não estão registradas em vestígios e mensagens registradas. Um administrador de máquina, `enableLoggingKnownPII` no entanto, pode usar o atributo no `machineSettings` elemento do arquivo Machine.config para permitir que os aplicativos em execução na máquina registrem informações pessoais identificáveis (PII) da seguinte forma:  
  
```xml  
<configuration>  
   <system.ServiceModel>  
      <machineSettings enableLoggingKnownPii="Boolean"/>  
   </system.ServiceModel>  
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
            <add name="xml" />  
         </listeners>  
      </source>  
  </sources>  
</system.diagnostics>  
```  
  
 Se `<machineSettings enableLoggingKnownPii="Boolean"/>` o elemento existir fora do arquivo Machine.config, o sistema lança um <xref:System.Configuration.ConfigurationErrorsException>.  
  
 As alterações só são eficazes quando o aplicativo é iniciado ou reiniciado. Um evento é registrado na inicialização quando `true`ambos os atributos são definidos para . Um evento também é `logKnownPii` registrado `true` se `enableLoggingKnownPii` `false`estiver definido, mas é .  
  
 Para obter mais informações sobre o registro de PII, consulte a amostra [de bloqueio de segurança do PII.](../../../../../docs/framework/wcf/samples/pii-security-lockdown.md)  
  
 O administrador da máquina e o implantador de aplicativos devem ter extrema cautela ao usar estes dois switches. Se o registro do PII estiver ativado, as chaves de segurança e o PII serão registrados. Se estiver desativado, dados confidenciais e específicos do aplicativo ainda serão registrados em cabeçalhos de mensagens e corpos. Para uma discussão mais aprofundada sobre privacidade e proteção do PII de ser exposta, consulte [Privacidade do Usuário](https://docs.microsoft.com/previous-versions/dotnet/articles/aa480490(v=msdn.10)).  
  
 Além disso, o endereço IP do remetente de mensagens é registrado uma vez por conexão para transportes orientados à conexão e uma vez por mensagem enviada em contrário. Isso é feito sem o consentimento do remetente. No entanto, esse registro só ocorre nos níveis de rastreamento De Informações ou Verbose, que não são os níveis de rastreamento padrão ou recomendados na produção, exceto para depuração ao vivo.  
  
## <a name="see-also"></a>Confira também

- [Rastreamento](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
