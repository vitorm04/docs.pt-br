---
title: "Preocupações de segurança e dicas úteis para rastreamento"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 88bc2880-ecb9-47cd-9816-39016a07076f
caps.latest.revision: "11"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 07ac814253a563a0cbdad1014970af3d18c6fdde
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="security-concerns-and-useful-tips-for-tracing"></a>Preocupações de segurança e dicas úteis para rastreamento
Este tópico descreve como proteger informações confidenciais sejam expostas, bem como dicas úteis ao usar WebHost.  
  
## <a name="using-a-custom-trace-listener-with-webhost"></a>Usando um ouvinte de rastreamento personalizada com WebHost  
 Se você estiver escrevendo seu próprio ouvinte de rastreamento, você deve estar atento a possibilidade de que os rastreamentos podem ser perdidos no caso de um serviço hospedado na Web. Quando se reciclar WebHost, desligar o processo em tempo real enquanto uma duplicata assume. No entanto, os dois processos ainda devem ter acesso ao mesmo recurso por algum tempo, o que é dependente do tipo de ouvinte. Nesse caso, `XmlWriterTraceListener` cria um novo arquivo de rastreamento para o segundo processo; enquanto o rastreamento de eventos do Windows gerencia vários processos dentro da mesma sessão e fornece acesso para o mesmo arquivo. Se o seu próprio ouvinte não fornece funcionalidades semelhantes, os rastreamentos podem ser perdidos quando o arquivo está bloqueado para cima, os dois processos.  
  
 Você também deve estar ciente de que um ouvinte de rastreamento personalizado pode enviar rastreamentos e mensagens de transmissão, por exemplo, um banco de dados remoto. Como um implantador do aplicativo, você deve configurar ouvintes personalizados com controle de acesso apropriadas. Você também deve aplicar o controle de segurança em todas as informações pessoais que podem ser exibidos no local remoto.  
  
## <a name="logging-sensitive-information"></a>O log de informações confidenciais  
 Quando uma mensagem no escopo, os rastreamentos contêm cabeçalhos de mensagem. Quando o rastreamento está habilitado, as informações pessoais em cabeçalhos específicos do aplicativo, como uma cadeia de caracteres de consulta; e corpo informações, como um número de cartão de crédito, pode se tornar visíveis nos logs. O implantador de aplicativo é responsável por impor o controle de acesso nos arquivos de configuração e o rastreamento. Se você não deseja que esse tipo de informação fique visível, você deve desabilitar o rastreamento ou filtrar a parte dos dados se você quiser compartilhar os logs de rastreamento.  
  
 As dicas a seguir podem ajudar a impedir que o conteúdo de um arquivo de rastreamento seja exposto indesejadamente:  
  
-   Certifique-se de que o log de arquivos estão protegidos pelo controle listas acesso (ACL) no WebHost e cenários de hospedagem interna.  
  
-   Escolha uma extensão de arquivo não pode ser facilmente exposta com uma solicitação da Web. Por exemplo, a extensão de arquivo. XML não é uma opção segura. Você pode verificar o guia de administração do IIS para ver uma lista de extensões que podem ser usadas.  
  
-   Especifique um caminho absoluto para o local de arquivo de log, que deve estar fora do diretório público do WebHost vroot para impedir que ele seja acessado por terceiros usando um navegador da Web.  
  
 Por padrão, as chaves e informações de identificação pessoal (PII), como nome de usuário e senha não são registradas em rastreamentos e registrado mensagens. No entanto, um administrador de máquina, pode usar o `enableLoggingKnownPII` atributo o `machineSettings` elemento do arquivo Machine. config para permitir que aplicativos em execução no computador para fazer logon conhecidas informações de identificação pessoal (PII) da seguinte maneira:  
  
```xml  
<configuration>  
   <system.ServiceModel>  
      <machineSettings enableLoggingKnownPii="Boolean"/>  
   </system.ServiceModel>  
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
            <add name="xml" />  
         </listeners>  
      </source>  
  </sources>  
</system.diagnostics>  
```  
  
 Se o `<machineSettings enableLoggingKnownPii="Boolean"/>` elemento existe fora do arquivo Machine. config, o sistema gera um <xref:System.Configuration.ConfigurationErrorsException>.  
  
 As alterações entrarão em vigor somente quando o aplicativo inicia ou reinicia. Um evento é registrado na inicialização, quando ambos os atributos são definidos como `true`. Também é registrado um evento se `logKnownPii` é definido como `true` mas `enableLoggingKnownPii` é `false`.  
  
 Para obter mais informações sobre o log de PII, consulte [bloqueio de segurança PII](../../../../../docs/framework/wcf/samples/pii-security-lockdown.md) exemplo.  
  
 O administrador da máquina e o implantador de aplicativo deve ter muito cuidado ao usar essas duas opções. Se o log de PII estiver habilitado, as chaves de segurança e informações de identificação pessoal são registradas. Se ele estiver desabilitado, os dados específicos do aplicativo ainda estão conectados em cabeçalhos e corpos. Para obter uma discussão mais completa sobre privacidade e proteção de informações de identificação pessoal sejam expostas, consulte [privacidade do usuário](http://go.microsoft.com/fwlink/?LinkID=94647).  
  
 Além disso, o endereço IP do remetente da mensagem é registrado uma vez por conexão de transportes voltados para conexão e uma vez por mensagem enviada caso contrário. Isso é feito sem o consentimento do remetente. No entanto, esse log somente ocorre em níveis de rastreamento informações ou Verbose, que não são o padrão ou recomendado níveis de rastreamento em produção, exceto para depuração dinâmica.  
  
## <a name="see-also"></a>Consulte também  
 [Rastreamento](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
