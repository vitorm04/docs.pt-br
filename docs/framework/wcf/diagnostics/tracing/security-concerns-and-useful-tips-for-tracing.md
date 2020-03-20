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
# <a name="security-concerns-and-useful-tips-for-tracing"></a><span data-ttu-id="c49bb-102">Preocupações de segurança e dicas úteis para rastreamento</span><span class="sxs-lookup"><span data-stu-id="c49bb-102">Security Concerns and Useful Tips for Tracing</span></span>
<span data-ttu-id="c49bb-103">Este tópico descreve como você pode proteger informações confidenciais de serem expostas, bem como dicas úteis ao usar o WebHost.</span><span class="sxs-lookup"><span data-stu-id="c49bb-103">This topic describes how you can protect sensitive information from being exposed, as well as useful tips when using WebHost.</span></span>  
  
## <a name="using-a-custom-trace-listener-with-webhost"></a><span data-ttu-id="c49bb-104">Usando um ouvinte de rastreamento personalizado com webhost</span><span class="sxs-lookup"><span data-stu-id="c49bb-104">Using a Custom Trace Listener with WebHost</span></span>  
 <span data-ttu-id="c49bb-105">Se você está escrevendo seu próprio ouvinte de rastreamento, você deve estar ciente da possibilidade de que os traços possam ser perdidos no caso de um serviço hospedado na Web.</span><span class="sxs-lookup"><span data-stu-id="c49bb-105">If you are writing your own trace listener, you should be aware of the possibility that traces might be lost in the case of a Web-hosted service.</span></span> <span data-ttu-id="c49bb-106">Quando o WebHost recicla, ele desliga o processo ao vivo enquanto uma duplicata assume o cargo.</span><span class="sxs-lookup"><span data-stu-id="c49bb-106">When WebHost recycles, it shuts down the live process while a duplicate takes over.</span></span> <span data-ttu-id="c49bb-107">No entanto, os dois processos ainda devem ter acesso ao mesmo recurso por algum tempo, que depende do tipo ouvinte.</span><span class="sxs-lookup"><span data-stu-id="c49bb-107">However, the two processes must still have access to the same resource for some time, which is dependent on the listener type.</span></span> <span data-ttu-id="c49bb-108">Neste caso, `XmlWriterTraceListener` cria um novo arquivo de rastreamento para o segundo processo; enquanto o rastreamento de eventos do Windows gerencia vários processos dentro da mesma sessão e dá acesso ao mesmo arquivo.</span><span class="sxs-lookup"><span data-stu-id="c49bb-108">In this case, , `XmlWriterTraceListener` creates a new trace file for the second process; while Windows event tracing manages multiple processes within the same session and gives access to the same file.</span></span> <span data-ttu-id="c49bb-109">Se o seu próprio ouvinte não fornecer funcionalidades semelhantes, os vestígios podem ser perdidos quando o arquivo é bloqueado pelos dois processos.</span><span class="sxs-lookup"><span data-stu-id="c49bb-109">If your own listener does not provide similar functionalities, traces can be lost when the file is locked up by the two processes.</span></span>  
  
 <span data-ttu-id="c49bb-110">Você também deve estar ciente de que um ouvinte de rastreamento personalizado pode enviar vestígios e mensagens no fio, por exemplo, para um banco de dados remoto.</span><span class="sxs-lookup"><span data-stu-id="c49bb-110">You should also be aware that a custom trace listener can send traces and messages on the wire, for example, to a remote database.</span></span> <span data-ttu-id="c49bb-111">Como implantador de aplicativos, você deve configurar ouvintes personalizados com controle de acesso apropriado.</span><span class="sxs-lookup"><span data-stu-id="c49bb-111">As an application deployer, you should configure custom listeners with appropriate access control.</span></span> <span data-ttu-id="c49bb-112">Você também deve aplicar o controle de segurança em qualquer informação pessoal que possa ser exposta no local remoto.</span><span class="sxs-lookup"><span data-stu-id="c49bb-112">You should also apply security control on any personal information that can be exposed at the remote location.</span></span>  
  
## <a name="logging-sensitive-information"></a><span data-ttu-id="c49bb-113">Registro de informações confidenciais</span><span class="sxs-lookup"><span data-stu-id="c49bb-113">Logging Sensitive Information</span></span>  
 <span data-ttu-id="c49bb-114">Os rastreamentos contêm cabeçalhos de mensagem quando uma mensagem está no escopo.</span><span class="sxs-lookup"><span data-stu-id="c49bb-114">Traces contain message headers when a message is in scope.</span></span> <span data-ttu-id="c49bb-115">Quando o rastreamento é ativado, as informações pessoais em cabeçalhos específicos do aplicativo, como, uma seqüência de consultas; e informações do corpo, como, por isso, um número de cartão de crédito, podem se tornar visíveis nos registros.</span><span class="sxs-lookup"><span data-stu-id="c49bb-115">When tracing is enabled, personal information in application-specific headers, such as, a query string; and body information, such as, a credit card number, can become visible in the logs.</span></span> <span data-ttu-id="c49bb-116">O implantador de aplicativos é responsável por reforçar o controle de acesso na configuração e rastrear arquivos.</span><span class="sxs-lookup"><span data-stu-id="c49bb-116">The application deployer is responsible for enforcing access control on the configuration and trace files.</span></span> <span data-ttu-id="c49bb-117">Se você não quiser que esse tipo de informação seja visível, você deve desativar o rastreamento ou filtrar parte dos dados se quiser compartilhar os registros de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="c49bb-117">If you do not want this kind of information to be visible, you should disable tracing, or filter out part of the data if you want to share the trace logs.</span></span>  
  
 <span data-ttu-id="c49bb-118">As seguintes dicas podem ajudá-lo a evitar que o conteúdo de um arquivo de rastreamento seja exposto sem querer:</span><span class="sxs-lookup"><span data-stu-id="c49bb-118">The following tips can help you to prevent the content of a trace file from being exposed unintentionally:</span></span>  
  
- <span data-ttu-id="c49bb-119">Certifique-se de que os arquivos de log estão protegidos por Listas de Controle de Acesso (ACL) tanto no WebHost quanto em cenários de auto-host.</span><span class="sxs-lookup"><span data-stu-id="c49bb-119">Ensure that the log files are protected by Access Control Lists (ACL) both in WebHost and self-host scenarios.</span></span>  
  
- <span data-ttu-id="c49bb-120">Escolha uma extensão de arquivo que não possa ser facilmente atendida usando uma solicitação da Web.</span><span class="sxs-lookup"><span data-stu-id="c49bb-120">Choose a file extension that cannot be easily served using a Web request.</span></span> <span data-ttu-id="c49bb-121">Por exemplo, a extensão de arquivo .xml não é uma escolha segura.</span><span class="sxs-lookup"><span data-stu-id="c49bb-121">For example, the .xml file extension is not a safe choice.</span></span> <span data-ttu-id="c49bb-122">Você pode verificar o guia de administração do IIS para ver uma lista de extensões que podem ser atendidas.</span><span class="sxs-lookup"><span data-stu-id="c49bb-122">You can check the IIS administration guide to see a list of extensions that can be served.</span></span>  
  
- <span data-ttu-id="c49bb-123">Especifique um caminho absoluto para o local do arquivo de log, que deve estar fora do diretório público vroot do WebHost para evitar que ele seja acessado por uma parte externa usando um navegador da Web.</span><span class="sxs-lookup"><span data-stu-id="c49bb-123">Specify an absolute path for the log file location, which should be outside of the WebHost vroot public directory to prevent it from being accessed by an external party using a Web browser.</span></span>  
  
 <span data-ttu-id="c49bb-124">Por padrão, chaves e informações pessoalmente identificáveis (PII), como nome de usuário e senha, não estão registradas em vestígios e mensagens registradas.</span><span class="sxs-lookup"><span data-stu-id="c49bb-124">By default, keys and personally identifiable information (PII) such as username and password are not logged in traces and logged messages.</span></span> <span data-ttu-id="c49bb-125">Um administrador de máquina, `enableLoggingKnownPII` no entanto, pode usar o atributo no `machineSettings` elemento do arquivo Machine.config para permitir que os aplicativos em execução na máquina registrem informações pessoais identificáveis (PII) da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="c49bb-125">A machine administrator, however, can use the `enableLoggingKnownPII` attribute in the `machineSettings` element of the Machine.config file to permit applications running on the machine to log known personally identifiable information (PII) as follows:</span></span>  
  
```xml  
<configuration>  
   <system.ServiceModel>  
      <machineSettings enableLoggingKnownPii="Boolean"/>  
   </system.ServiceModel>  
</configuration>
```  
  
 <span data-ttu-id="c49bb-126">Um implantador de aplicativos `logKnownPii` pode usar o atributo no arquivo App.config ou Web.config para ativar o registro de PII da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="c49bb-126">An application deployer can then use the `logKnownPii` attribute in either the App.config or Web.config file to enable PII logging as follows:</span></span>  
  
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
  
 <span data-ttu-id="c49bb-127">Somente quando ambas `true` as configurações estiverem habilitadas para o login do PII.</span><span class="sxs-lookup"><span data-stu-id="c49bb-127">Only when both settings are `true` is PII logging enabled.</span></span> <span data-ttu-id="c49bb-128">A combinação de dois switches permite a flexibilidade de registrar PII conhecido para cada aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c49bb-128">The combination of two switches allows the flexibility to log known PII for each application.</span></span>  
  
 <span data-ttu-id="c49bb-129">Você deve estar ciente de que se você especificar duas ou mais fontes personalizadas em um arquivo de configuração, apenas os atributos da primeira fonte serão lidos.</span><span class="sxs-lookup"><span data-stu-id="c49bb-129">You should be aware that if you specify two or more custom sources in a configuration file, only the attributes of the first source are read.</span></span> <span data-ttu-id="c49bb-130">Os outros são ignorados.</span><span class="sxs-lookup"><span data-stu-id="c49bb-130">The others are ignored.</span></span> <span data-ttu-id="c49bb-131">Isso significa que, para o seguinte App.config, file, o PII não está registrado para ambas as fontes, embora o registro pii esteja explicitamente habilitado para a segunda fonte.</span><span class="sxs-lookup"><span data-stu-id="c49bb-131">This means that, for the following App.config, file, PII is not logged for both sources even though PII logging is explicitly enabled for the second source.</span></span>  
  
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
  
 <span data-ttu-id="c49bb-132">Se `<machineSettings enableLoggingKnownPii="Boolean"/>` o elemento existir fora do arquivo Machine.config, o sistema lança um <xref:System.Configuration.ConfigurationErrorsException>.</span><span class="sxs-lookup"><span data-stu-id="c49bb-132">If the `<machineSettings enableLoggingKnownPii="Boolean"/>` element exists outside the Machine.config file, the system throws a <xref:System.Configuration.ConfigurationErrorsException>.</span></span>  
  
 <span data-ttu-id="c49bb-133">As alterações só são eficazes quando o aplicativo é iniciado ou reiniciado.</span><span class="sxs-lookup"><span data-stu-id="c49bb-133">The changes are effective only when the application starts or restarts.</span></span> <span data-ttu-id="c49bb-134">Um evento é registrado na inicialização quando `true`ambos os atributos são definidos para .</span><span class="sxs-lookup"><span data-stu-id="c49bb-134">An event is logged at startup when both attributes are set to `true`.</span></span> <span data-ttu-id="c49bb-135">Um evento também é `logKnownPii` registrado `true` se `enableLoggingKnownPii` `false`estiver definido, mas é .</span><span class="sxs-lookup"><span data-stu-id="c49bb-135">An event is also logged if `logKnownPii` is set to `true` but `enableLoggingKnownPii` is `false`.</span></span>  
  
 <span data-ttu-id="c49bb-136">Para obter mais informações sobre o registro de PII, consulte a amostra [de bloqueio de segurança do PII.](../../../../../docs/framework/wcf/samples/pii-security-lockdown.md)</span><span class="sxs-lookup"><span data-stu-id="c49bb-136">For more information on PII logging, see [PII Security Lockdown](../../../../../docs/framework/wcf/samples/pii-security-lockdown.md) sample.</span></span>  
  
 <span data-ttu-id="c49bb-137">O administrador da máquina e o implantador de aplicativos devem ter extrema cautela ao usar estes dois switches.</span><span class="sxs-lookup"><span data-stu-id="c49bb-137">The machine administrator and application deployer should exercise extreme caution when using these two switches.</span></span> <span data-ttu-id="c49bb-138">Se o registro do PII estiver ativado, as chaves de segurança e o PII serão registrados.</span><span class="sxs-lookup"><span data-stu-id="c49bb-138">If PII logging is enabled, security keys and PII are logged.</span></span> <span data-ttu-id="c49bb-139">Se estiver desativado, dados confidenciais e específicos do aplicativo ainda serão registrados em cabeçalhos de mensagens e corpos.</span><span class="sxs-lookup"><span data-stu-id="c49bb-139">If it is disabled, sensitive and application-specific data is still logged in message headers and bodies.</span></span> <span data-ttu-id="c49bb-140">Para uma discussão mais aprofundada sobre privacidade e proteção do PII de ser exposta, consulte [Privacidade do Usuário](https://docs.microsoft.com/previous-versions/dotnet/articles/aa480490(v=msdn.10)).</span><span class="sxs-lookup"><span data-stu-id="c49bb-140">For a more thorough discussion on privacy and protecting PII from being exposed, see [User Privacy](https://docs.microsoft.com/previous-versions/dotnet/articles/aa480490(v=msdn.10)).</span></span>  
  
 <span data-ttu-id="c49bb-141">Além disso, o endereço IP do remetente de mensagens é registrado uma vez por conexão para transportes orientados à conexão e uma vez por mensagem enviada em contrário.</span><span class="sxs-lookup"><span data-stu-id="c49bb-141">In addition, the IP address of the message sender is logged once per connection for connection-oriented transports, and once per message sent otherwise.</span></span> <span data-ttu-id="c49bb-142">Isso é feito sem o consentimento do remetente.</span><span class="sxs-lookup"><span data-stu-id="c49bb-142">This is done without the consent of the sender.</span></span> <span data-ttu-id="c49bb-143">No entanto, esse registro só ocorre nos níveis de rastreamento De Informações ou Verbose, que não são os níveis de rastreamento padrão ou recomendados na produção, exceto para depuração ao vivo.</span><span class="sxs-lookup"><span data-stu-id="c49bb-143">However, this logging only occurs at the Information or Verbose tracing levels, which are not the default or recommended tracing levels in production, except for live debugging.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c49bb-144">Confira também</span><span class="sxs-lookup"><span data-stu-id="c49bb-144">See also</span></span>

- [<span data-ttu-id="c49bb-145">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="c49bb-145">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
