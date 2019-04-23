---
title: Preocupações de segurança e dicas úteis para rastreamento
ms.date: 03/30/2017
ms.assetid: 88bc2880-ecb9-47cd-9816-39016a07076f
ms.openlocfilehash: 72d35230820e8466cd9c63a76b26c7a23bdfe024
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59130788"
---
# <a name="security-concerns-and-useful-tips-for-tracing"></a>Preocupações de segurança e dicas úteis para rastreamento
Este tópico descreve como você pode proteger informações confidenciais sejam expostas, bem como dicas úteis ao usar o WebHost.  
  
## <a name="using-a-custom-trace-listener-with-webhost"></a>Usando um ouvinte de rastreamento com o WebHost  
 Se você estiver escrevendo seu próprio ouvinte de rastreamento, você deve estar ciente da possibilidade de que os rastreamentos podem ser perdidos no caso de um serviço hospedado na Web. Quando se reciclar WebHost, ele desliga o processo ao vivo enquanto uma duplicata assume. No entanto, os dois processos ainda devem ter acesso ao mesmo recurso por algum tempo, o que é dependente do tipo de ouvinte. Nesse caso, `XmlWriterTraceListener` cria um novo arquivo de rastreamento para o segundo processo; enquanto gerencia vários processos dentro da mesma sessão de rastreamento de eventos do Windows e fornece acesso ao mesmo arquivo. Se o seu próprio ouvinte não fornece funcionalidades semelhantes, os rastreamentos podem ser perdidos quando o arquivo está bloqueado para cima por dois processos.  
  
 Você também deve estar ciente de que um ouvinte de rastreamento personalizado pode enviar rastreamentos e mensagens na transmissão, por exemplo, para um banco de dados remoto. Como um implantador de aplicativo, você deve configurar os ouvintes personalizados com controle de acesso apropriado. Você também deve aplicar o controle de segurança em todas as informações pessoais que podem ser expostos no local remoto.  
  
## <a name="logging-sensitive-information"></a>Registro em log informações confidenciais  
 Quando uma mensagem está no escopo os rastreamentos contêm cabeçalhos de mensagem. Quando o rastreamento está habilitado, informações pessoais nos cabeçalhos específicos do aplicativo, por exemplo, uma cadeia de caracteres de consulta; e o corpo de informações, como um número de cartão de crédito, pode se tornar visível nos logs. O implantador de aplicativo é responsável por impor o controle de acesso nos arquivos de configuração e o rastreamento. Se você não quiser esse tipo de informação fique visível, você deve desabilitar o rastreamento ou filtrar a parte dos dados se você quiser compartilhar os logs de rastreamento.  
  
 As dicas a seguir podem ajudar você a impedir que o conteúdo de um arquivo de rastreamento seja exposto indesejadamente:  
  
-   Certifique-se de que o log de arquivos são protegidos por listas de ACL (Access Control) no host Web e cenários de hospedagem interna.  
  
-   Escolha uma extensão de arquivo que não pode ser facilmente exposta com uma solicitação da Web. Por exemplo, a extensão de arquivo. XML não é uma opção segura. Você pode verificar o guia de administração do IIS para ver uma lista de extensões que podem ser atendidas.  
  
-   Especifique um caminho absoluto para o local de arquivo de log, que deve estar fora do diretório público vroot WebHost impedi-lo de que está sendo acessado por terceiros usando um navegador da Web.  
  
 Por padrão, as chaves e informações de identificação pessoal (PII), como nome de usuário e senha não são registradas em rastreamentos e registrado mensagens. No entanto, um administrador do computador, pode usar o `enableLoggingKnownPII` de atributo no `machineSettings` elemento do arquivo Machine. config para permitir que aplicativos em execução no computador para fazer logon conhecidas informações de identificação pessoal (PII) da seguinte maneira:  
  
```xml  
<configuration>  
   <system.ServiceModel>  
      <machineSettings enableLoggingKnownPii="Boolean"/>  
   </system.ServiceModel>  
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
            <add name="xml" />  
         </listeners>  
      </source>  
  </sources>  
</system.diagnostics>  
```  
  
 Se o `<machineSettings enableLoggingKnownPii="Boolean"/>` elemento existe fora do arquivo Machine. config, o sistema gera um <xref:System.Configuration.ConfigurationErrorsException>.  
  
 As alterações entrarão em vigor somente quando o aplicativo inicia ou reinicia. Um evento é registrado na inicialização, quando ambos os atributos são definidos como `true`. Também é registrado um evento se `logKnownPii` é definido como `true` mas `enableLoggingKnownPii` é `false`.  
  
 Para obter mais informações sobre registro em log o PII, consulte [bloqueio de segurança PII](../../../../../docs/framework/wcf/samples/pii-security-lockdown.md) exemplo.  
  
 O administrador da máquina e o implantador de aplicativo deve ter muito cuidado ao usar essas duas opções. Se o log de informações de identificação pessoal é habilitado, as chaves de segurança e informações de identificação pessoal são registradas. Se ele estiver desabilitado, os dados confidenciais e específicos do aplicativo ainda estão conectados em corpos e cabeçalhos de mensagem. Para obter uma discussão mais completa sobre privacidade e proteção de PII sejam expostas, consulte [privacidade do usuário](https://go.microsoft.com/fwlink/?LinkID=94647).  
  
 Além disso, o endereço IP do remetente da mensagem é registrado uma vez por conexão para transportes voltados para conexão e, uma vez por mensagem enviada, caso contrário. Isso é feito sem o consentimento do remetente. No entanto, esse registro em log somente ocorre nos níveis de rastreamento informações ou detalhado, que não são o padrão ou recomendado níveis de rastreamento em produção, com exceção de depuração ao vivo.  
  
## <a name="see-also"></a>Consulte também

- [Rastreamento](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
