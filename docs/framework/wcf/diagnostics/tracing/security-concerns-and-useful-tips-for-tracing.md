---
title: Preocupações de segurança e dicas úteis para rastreamento
ms.date: 03/30/2017
ms.assetid: 88bc2880-ecb9-47cd-9816-39016a07076f
author: BrucePerlerMS
ms.openlocfilehash: 51db352913999d5527ead5273e6488cd09d88670
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48032680"
---
# <a name="security-concerns-and-useful-tips-for-tracing"></a><span data-ttu-id="0d339-102">Preocupações de segurança e dicas úteis para rastreamento</span><span class="sxs-lookup"><span data-stu-id="0d339-102">Security Concerns and Useful Tips for Tracing</span></span>
<span data-ttu-id="0d339-103">Este tópico descreve como você pode proteger informações confidenciais sejam expostas, bem como dicas úteis ao usar o WebHost.</span><span class="sxs-lookup"><span data-stu-id="0d339-103">This topic describes how you can protect sensitive information from being exposed, as well as useful tips when using WebHost.</span></span>  
  
## <a name="using-a-custom-trace-listener-with-webhost"></a><span data-ttu-id="0d339-104">Usando um ouvinte de rastreamento com o WebHost</span><span class="sxs-lookup"><span data-stu-id="0d339-104">Using a Custom Trace Listener with WebHost</span></span>  
 <span data-ttu-id="0d339-105">Se você estiver escrevendo seu próprio ouvinte de rastreamento, você deve estar ciente da possibilidade de que os rastreamentos podem ser perdidos no caso de um serviço hospedado na Web.</span><span class="sxs-lookup"><span data-stu-id="0d339-105">If you are writing your own trace listener, you should be aware of the possibility that traces might be lost in the case of a Web-hosted service.</span></span> <span data-ttu-id="0d339-106">Quando se reciclar WebHost, ele desliga o processo ao vivo enquanto uma duplicata assume.</span><span class="sxs-lookup"><span data-stu-id="0d339-106">When WebHost recycles, it shuts down the live process while a duplicate takes over.</span></span> <span data-ttu-id="0d339-107">No entanto, os dois processos ainda devem ter acesso ao mesmo recurso por algum tempo, o que é dependente do tipo de ouvinte.</span><span class="sxs-lookup"><span data-stu-id="0d339-107">However, the two processes must still have access to the same resource for some time, which is dependent on the listener type.</span></span> <span data-ttu-id="0d339-108">Nesse caso, `XmlWriterTraceListener` cria um novo arquivo de rastreamento para o segundo processo; enquanto gerencia vários processos dentro da mesma sessão de rastreamento de eventos do Windows e fornece acesso ao mesmo arquivo.</span><span class="sxs-lookup"><span data-stu-id="0d339-108">In this case, , `XmlWriterTraceListener` creates a new trace file for the second process; while Windows event tracing manages multiple processes within the same session and gives access to the same file.</span></span> <span data-ttu-id="0d339-109">Se o seu próprio ouvinte não fornece funcionalidades semelhantes, os rastreamentos podem ser perdidos quando o arquivo está bloqueado para cima por dois processos.</span><span class="sxs-lookup"><span data-stu-id="0d339-109">If your own listener does not provide similar functionalities, traces can be lost when the file is locked up by the two processes.</span></span>  
  
 <span data-ttu-id="0d339-110">Você também deve estar ciente de que um ouvinte de rastreamento personalizado pode enviar rastreamentos e mensagens na transmissão, por exemplo, para um banco de dados remoto.</span><span class="sxs-lookup"><span data-stu-id="0d339-110">You should also be aware that a custom trace listener can send traces and messages on the wire, for example, to a remote database.</span></span> <span data-ttu-id="0d339-111">Como um implantador de aplicativo, você deve configurar os ouvintes personalizados com controle de acesso apropriado.</span><span class="sxs-lookup"><span data-stu-id="0d339-111">As an application deployer, you should configure custom listeners with appropriate access control.</span></span> <span data-ttu-id="0d339-112">Você também deve aplicar o controle de segurança em todas as informações pessoais que podem ser expostos no local remoto.</span><span class="sxs-lookup"><span data-stu-id="0d339-112">You should also apply security control on any personal information that can be exposed at the remote location.</span></span>  
  
## <a name="logging-sensitive-information"></a><span data-ttu-id="0d339-113">Registro em log informações confidenciais</span><span class="sxs-lookup"><span data-stu-id="0d339-113">Logging Sensitive Information</span></span>  
 <span data-ttu-id="0d339-114">Quando uma mensagem está no escopo os rastreamentos contêm cabeçalhos de mensagem.</span><span class="sxs-lookup"><span data-stu-id="0d339-114">Traces contain message headers when a message is in scope.</span></span> <span data-ttu-id="0d339-115">Quando o rastreamento está habilitado, informações pessoais nos cabeçalhos específicos do aplicativo, por exemplo, uma cadeia de caracteres de consulta; e o corpo de informações, como um número de cartão de crédito, pode se tornar visível nos logs.</span><span class="sxs-lookup"><span data-stu-id="0d339-115">When tracing is enabled, personal information in application-specific headers, such as, a query string; and body information, such as, a credit card number, can become visible in the logs.</span></span> <span data-ttu-id="0d339-116">O implantador de aplicativo é responsável por impor o controle de acesso nos arquivos de configuração e o rastreamento.</span><span class="sxs-lookup"><span data-stu-id="0d339-116">The application deployer is responsible for enforcing access control on the configuration and trace files.</span></span> <span data-ttu-id="0d339-117">Se você não quiser esse tipo de informação fique visível, você deve desabilitar o rastreamento ou filtrar a parte dos dados se você quiser compartilhar os logs de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="0d339-117">If you do not want this kind of information to be visible, you should disable tracing, or filter out part of the data if you want to share the trace logs.</span></span>  
  
 <span data-ttu-id="0d339-118">As dicas a seguir podem ajudar você a impedir que o conteúdo de um arquivo de rastreamento seja exposto indesejadamente:</span><span class="sxs-lookup"><span data-stu-id="0d339-118">The following tips can help you to prevent the content of a trace file from being exposed unintentionally:</span></span>  
  
-   <span data-ttu-id="0d339-119">Certifique-se de que o log de arquivos são protegidos por listas de ACL (Access Control) no host Web e cenários de hospedagem interna.</span><span class="sxs-lookup"><span data-stu-id="0d339-119">Ensure that the log files are protected by Access Control Lists (ACL) both in WebHost and self-host scenarios.</span></span>  
  
-   <span data-ttu-id="0d339-120">Escolha uma extensão de arquivo que não pode ser facilmente exposta com uma solicitação da Web.</span><span class="sxs-lookup"><span data-stu-id="0d339-120">Choose a file extension that cannot be easily served using a Web request.</span></span> <span data-ttu-id="0d339-121">Por exemplo, a extensão de arquivo. XML não é uma opção segura.</span><span class="sxs-lookup"><span data-stu-id="0d339-121">For example, the .xml file extension is not a safe choice.</span></span> <span data-ttu-id="0d339-122">Você pode verificar o guia de administração do IIS para ver uma lista de extensões que podem ser atendidas.</span><span class="sxs-lookup"><span data-stu-id="0d339-122">You can check the IIS administration guide to see a list of extensions that can be served.</span></span>  
  
-   <span data-ttu-id="0d339-123">Especifique um caminho absoluto para o local de arquivo de log, que deve estar fora do diretório público vroot WebHost impedi-lo de que está sendo acessado por terceiros usando um navegador da Web.</span><span class="sxs-lookup"><span data-stu-id="0d339-123">Specify an absolute path for the log file location, which should be outside of the WebHost vroot public directory to prevent it from being accessed by an external party using a Web browser.</span></span>  
  
 <span data-ttu-id="0d339-124">Por padrão, as chaves e informações de identificação pessoal (PII), como nome de usuário e senha não são registradas em rastreamentos e registrado mensagens.</span><span class="sxs-lookup"><span data-stu-id="0d339-124">By default, keys and personally identifiable information (PII) such as username and password are not logged in traces and logged messages.</span></span> <span data-ttu-id="0d339-125">No entanto, um administrador do computador, pode usar o `enableLoggingKnownPII` de atributo no `machineSettings` elemento do arquivo Machine. config para permitir que aplicativos em execução no computador para fazer logon conhecidas informações de identificação pessoal (PII) da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="0d339-125">A machine administrator, however, can use the `enableLoggingKnownPII` attribute in the `machineSettings` element of the Machine.config file to permit applications running on the machine to log known personally identifiable information (PII) as follows:</span></span>  
  
```xml  
<configuration>  
   <system.ServiceModel>  
      <machineSettings enableLoggingKnownPii="Boolean"/>  
   </system.ServiceModel>  
</configuration>   
```  
  
 <span data-ttu-id="0d339-126">Um implantador de aplicativo, em seguida, pode usar o `logKnownPii` atributo no arquivo App. config ou Web. config para habilitar o log de PII da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="0d339-126">An application deployer can then use the `logKnownPii` attribute in either the App.config or Web.config file to enable PII logging as follows:</span></span>  
  
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
  
 <span data-ttu-id="0d339-127">Somente quando ambas as configurações forem `true` é o log de PII habilitado.</span><span class="sxs-lookup"><span data-stu-id="0d339-127">Only when both settings are `true` is PII logging enabled.</span></span> <span data-ttu-id="0d339-128">A combinação de dois comutadores permite a flexibilidade fazer logon PII conhecido para cada aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0d339-128">The combination of two switches allows the flexibility to log known PII for each application.</span></span>  
  
 <span data-ttu-id="0d339-129">Você deve estar ciente de que, se você especificar duas ou mais fontes personalizadas em um arquivo de configuração, somente os atributos da primeira fonte sejam lidos.</span><span class="sxs-lookup"><span data-stu-id="0d339-129">You should be aware that if you specify two or more custom sources in a configuration file, only the attributes of the first source are read.</span></span> <span data-ttu-id="0d339-130">Os outros são ignorados.</span><span class="sxs-lookup"><span data-stu-id="0d339-130">The others are ignored.</span></span> <span data-ttu-id="0d339-131">Isso significa que, para seguir App. config, arquivo, PII não está conectado para ambas as fontes, mesmo que o registro em log o PII explicitamente está habilitado para a segunda fonte.</span><span class="sxs-lookup"><span data-stu-id="0d339-131">This means that, for the following App.config, file, PII is not logged for both sources even though PII logging is explicitly enabled for the second source.</span></span>  
  
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
  
 <span data-ttu-id="0d339-132">Se o `<machineSettings enableLoggingKnownPii="Boolean"/>` elemento existe fora do arquivo Machine. config, o sistema gera um <xref:System.Configuration.ConfigurationErrorsException>.</span><span class="sxs-lookup"><span data-stu-id="0d339-132">If the `<machineSettings enableLoggingKnownPii="Boolean"/>` element exists outside the Machine.config file, the system throws a <xref:System.Configuration.ConfigurationErrorsException>.</span></span>  
  
 <span data-ttu-id="0d339-133">As alterações entrarão em vigor somente quando o aplicativo inicia ou reinicia.</span><span class="sxs-lookup"><span data-stu-id="0d339-133">The changes are effective only when the application starts or restarts.</span></span> <span data-ttu-id="0d339-134">Um evento é registrado na inicialização, quando ambos os atributos são definidos como `true`.</span><span class="sxs-lookup"><span data-stu-id="0d339-134">An event is logged at startup when both attributes are set to `true`.</span></span> <span data-ttu-id="0d339-135">Também é registrado um evento se `logKnownPii` é definido como `true` mas `enableLoggingKnownPii` é `false`.</span><span class="sxs-lookup"><span data-stu-id="0d339-135">An event is also logged if `logKnownPii` is set to `true` but `enableLoggingKnownPii` is `false`.</span></span>  
  
 <span data-ttu-id="0d339-136">Para obter mais informações sobre registro em log o PII, consulte [bloqueio de segurança PII](../../../../../docs/framework/wcf/samples/pii-security-lockdown.md) exemplo.</span><span class="sxs-lookup"><span data-stu-id="0d339-136">For more information on PII logging, see [PII Security Lockdown](../../../../../docs/framework/wcf/samples/pii-security-lockdown.md) sample.</span></span>  
  
 <span data-ttu-id="0d339-137">O administrador da máquina e o implantador de aplicativo deve ter muito cuidado ao usar essas duas opções.</span><span class="sxs-lookup"><span data-stu-id="0d339-137">The machine administrator and application deployer should exercise extreme caution when using these two switches.</span></span> <span data-ttu-id="0d339-138">Se o log de informações de identificação pessoal é habilitado, as chaves de segurança e informações de identificação pessoal são registradas.</span><span class="sxs-lookup"><span data-stu-id="0d339-138">If PII logging is enabled, security keys and PII are logged.</span></span> <span data-ttu-id="0d339-139">Se ele estiver desabilitado, os dados confidenciais e específicos do aplicativo ainda estão conectados em corpos e cabeçalhos de mensagem.</span><span class="sxs-lookup"><span data-stu-id="0d339-139">If it is disabled, sensitive and application-specific data is still logged in message headers and bodies.</span></span> <span data-ttu-id="0d339-140">Para obter uma discussão mais completa sobre privacidade e proteção de PII sejam expostas, consulte [privacidade do usuário](https://go.microsoft.com/fwlink/?LinkID=94647).</span><span class="sxs-lookup"><span data-stu-id="0d339-140">For a more thorough discussion on privacy and protecting PII from being exposed, see [User Privacy](https://go.microsoft.com/fwlink/?LinkID=94647).</span></span>  
  
 <span data-ttu-id="0d339-141">Além disso, o endereço IP do remetente da mensagem é registrado uma vez por conexão para transportes voltados para conexão e, uma vez por mensagem enviada, caso contrário.</span><span class="sxs-lookup"><span data-stu-id="0d339-141">In addition, the IP address of the message sender is logged once per connection for connection-oriented transports, and once per message sent otherwise.</span></span> <span data-ttu-id="0d339-142">Isso é feito sem o consentimento do remetente.</span><span class="sxs-lookup"><span data-stu-id="0d339-142">This is done without the consent of the sender.</span></span> <span data-ttu-id="0d339-143">No entanto, esse registro em log somente ocorre nos níveis de rastreamento informações ou detalhado, que não são o padrão ou recomendado níveis de rastreamento em produção, com exceção de depuração ao vivo.</span><span class="sxs-lookup"><span data-stu-id="0d339-143">However, this logging only occurs at the Information or Verbose tracing levels, which are not the default or recommended tracing levels in production, except for live debugging.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d339-144">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0d339-144">See Also</span></span>  
 [<span data-ttu-id="0d339-145">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="0d339-145">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
