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
ms.workload: dotnet
ms.openlocfilehash: 4c6916333d1efa99ba1c4a9d75d80be2193e8698
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="security-concerns-and-useful-tips-for-tracing"></a><span data-ttu-id="49db1-102">Preocupações de segurança e dicas úteis para rastreamento</span><span class="sxs-lookup"><span data-stu-id="49db1-102">Security Concerns and Useful Tips for Tracing</span></span>
<span data-ttu-id="49db1-103">Este tópico descreve como proteger informações confidenciais sejam expostas, bem como dicas úteis ao usar WebHost.</span><span class="sxs-lookup"><span data-stu-id="49db1-103">This topic describes how you can protect sensitive information from being exposed, as well as useful tips when using WebHost.</span></span>  
  
## <a name="using-a-custom-trace-listener-with-webhost"></a><span data-ttu-id="49db1-104">Usando um ouvinte de rastreamento personalizada com WebHost</span><span class="sxs-lookup"><span data-stu-id="49db1-104">Using a Custom Trace Listener with WebHost</span></span>  
 <span data-ttu-id="49db1-105">Se você estiver escrevendo seu próprio ouvinte de rastreamento, você deve estar atento a possibilidade de que os rastreamentos podem ser perdidos no caso de um serviço hospedado na Web.</span><span class="sxs-lookup"><span data-stu-id="49db1-105">If you are writing your own trace listener, you should be aware of the possibility that traces might be lost in the case of a Web-hosted service.</span></span> <span data-ttu-id="49db1-106">Quando se reciclar WebHost, desligar o processo em tempo real enquanto uma duplicata assume.</span><span class="sxs-lookup"><span data-stu-id="49db1-106">When WebHost recycles, it shuts down the live process while a duplicate takes over.</span></span> <span data-ttu-id="49db1-107">No entanto, os dois processos ainda devem ter acesso ao mesmo recurso por algum tempo, o que é dependente do tipo de ouvinte.</span><span class="sxs-lookup"><span data-stu-id="49db1-107">However, the two processes must still have access to the same resource for some time, which is dependent on the listener type.</span></span> <span data-ttu-id="49db1-108">Nesse caso, `XmlWriterTraceListener` cria um novo arquivo de rastreamento para o segundo processo; enquanto o rastreamento de eventos do Windows gerencia vários processos dentro da mesma sessão e fornece acesso para o mesmo arquivo.</span><span class="sxs-lookup"><span data-stu-id="49db1-108">In this case, , `XmlWriterTraceListener` creates a new trace file for the second process; while Windows event tracing manages multiple processes within the same session and gives access to the same file.</span></span> <span data-ttu-id="49db1-109">Se o seu próprio ouvinte não fornece funcionalidades semelhantes, os rastreamentos podem ser perdidos quando o arquivo está bloqueado para cima, os dois processos.</span><span class="sxs-lookup"><span data-stu-id="49db1-109">If your own listener does not provide similar functionalities, traces can be lost when the file is locked up by the two processes.</span></span>  
  
 <span data-ttu-id="49db1-110">Você também deve estar ciente de que um ouvinte de rastreamento personalizado pode enviar rastreamentos e mensagens de transmissão, por exemplo, um banco de dados remoto.</span><span class="sxs-lookup"><span data-stu-id="49db1-110">You should also be aware that a custom trace listener can send traces and messages on the wire, for example, to a remote database.</span></span> <span data-ttu-id="49db1-111">Como um implantador do aplicativo, você deve configurar ouvintes personalizados com controle de acesso apropriadas.</span><span class="sxs-lookup"><span data-stu-id="49db1-111">As an application deployer, you should configure custom listeners with appropriate access control.</span></span> <span data-ttu-id="49db1-112">Você também deve aplicar o controle de segurança em todas as informações pessoais que podem ser exibidos no local remoto.</span><span class="sxs-lookup"><span data-stu-id="49db1-112">You should also apply security control on any personal information that can be exposed at the remote location.</span></span>  
  
## <a name="logging-sensitive-information"></a><span data-ttu-id="49db1-113">O log de informações confidenciais</span><span class="sxs-lookup"><span data-stu-id="49db1-113">Logging Sensitive Information</span></span>  
 <span data-ttu-id="49db1-114">Quando uma mensagem no escopo, os rastreamentos contêm cabeçalhos de mensagem.</span><span class="sxs-lookup"><span data-stu-id="49db1-114">Traces contain message headers when a message is in scope.</span></span> <span data-ttu-id="49db1-115">Quando o rastreamento está habilitado, as informações pessoais em cabeçalhos específicos do aplicativo, como uma cadeia de caracteres de consulta; e corpo informações, como um número de cartão de crédito, pode se tornar visíveis nos logs.</span><span class="sxs-lookup"><span data-stu-id="49db1-115">When tracing is enabled, personal information in application-specific headers, such as, a query string; and body information, such as, a credit card number, can become visible in the logs.</span></span> <span data-ttu-id="49db1-116">O implantador de aplicativo é responsável por impor o controle de acesso nos arquivos de configuração e o rastreamento.</span><span class="sxs-lookup"><span data-stu-id="49db1-116">The application deployer is responsible for enforcing access control on the configuration and trace files.</span></span> <span data-ttu-id="49db1-117">Se você não deseja que esse tipo de informação fique visível, você deve desabilitar o rastreamento ou filtrar a parte dos dados se você quiser compartilhar os logs de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="49db1-117">If you do not want this kind of information to be visible, you should disable tracing, or filter out part of the data if you want to share the trace logs.</span></span>  
  
 <span data-ttu-id="49db1-118">As dicas a seguir podem ajudar a impedir que o conteúdo de um arquivo de rastreamento seja exposto indesejadamente:</span><span class="sxs-lookup"><span data-stu-id="49db1-118">The following tips can help you to prevent the content of a trace file from being exposed unintentionally:</span></span>  
  
-   <span data-ttu-id="49db1-119">Certifique-se de que o log de arquivos estão protegidos pelo controle listas acesso (ACL) no WebHost e cenários de hospedagem interna.</span><span class="sxs-lookup"><span data-stu-id="49db1-119">Ensure that the log files are protected by Access Control Lists (ACL) both in WebHost and self-host scenarios.</span></span>  
  
-   <span data-ttu-id="49db1-120">Escolha uma extensão de arquivo não pode ser facilmente exposta com uma solicitação da Web.</span><span class="sxs-lookup"><span data-stu-id="49db1-120">Choose a file extension that cannot be easily served using a Web request.</span></span> <span data-ttu-id="49db1-121">Por exemplo, a extensão de arquivo. XML não é uma opção segura.</span><span class="sxs-lookup"><span data-stu-id="49db1-121">For example, the .xml file extension is not a safe choice.</span></span> <span data-ttu-id="49db1-122">Você pode verificar o guia de administração do IIS para ver uma lista de extensões que podem ser usadas.</span><span class="sxs-lookup"><span data-stu-id="49db1-122">You can check the IIS administration guide to see a list of extensions that can be served.</span></span>  
  
-   <span data-ttu-id="49db1-123">Especifique um caminho absoluto para o local de arquivo de log, que deve estar fora do diretório público do WebHost vroot para impedir que ele seja acessado por terceiros usando um navegador da Web.</span><span class="sxs-lookup"><span data-stu-id="49db1-123">Specify an absolute path for the log file location, which should be outside of the WebHost vroot public directory to prevent it from being accessed by an external party using a Web browser.</span></span>  
  
 <span data-ttu-id="49db1-124">Por padrão, as chaves e informações de identificação pessoal (PII), como nome de usuário e senha não são registradas em rastreamentos e registrado mensagens.</span><span class="sxs-lookup"><span data-stu-id="49db1-124">By default, keys and personally identifiable information (PII) such as username and password are not logged in traces and logged messages.</span></span> <span data-ttu-id="49db1-125">No entanto, um administrador de máquina, pode usar o `enableLoggingKnownPII` atributo o `machineSettings` elemento do arquivo Machine. config para permitir que aplicativos em execução no computador para fazer logon conhecidas informações de identificação pessoal (PII) da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="49db1-125">A machine administrator, however, can use the `enableLoggingKnownPII` attribute in the `machineSettings` element of the Machine.config file to permit applications running on the machine to log known personally identifiable information (PII) as follows:</span></span>  
  
```xml  
<configuration>  
   <system.ServiceModel>  
      <machineSettings enableLoggingKnownPii="Boolean"/>  
   </system.ServiceModel>  
</configuration>   
```  
  
 <span data-ttu-id="49db1-126">Implantador um aplicativo pode usar o `logKnownPii` atributo no arquivo de App. config ou Web. config para habilitar o log de PII da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="49db1-126">An application deployer can then use the `logKnownPii` attribute in either the App.config or Web.config file to enable PII logging as follows:</span></span>  
  
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
  
 <span data-ttu-id="49db1-127">Somente quando as duas configurações são `true` é o log de PII habilitado.</span><span class="sxs-lookup"><span data-stu-id="49db1-127">Only when both settings are `true` is PII logging enabled.</span></span> <span data-ttu-id="49db1-128">A combinação das duas opções permite a flexibilidade fazer logon PII conhecido para cada aplicativo.</span><span class="sxs-lookup"><span data-stu-id="49db1-128">The combination of two switches allows the flexibility to log known PII for each application.</span></span>  
  
 <span data-ttu-id="49db1-129">Você deve estar ciente de que, se você especificar dois ou mais fontes personalizadas em um arquivo de configuração, somente os atributos da primeira fonte são lidos.</span><span class="sxs-lookup"><span data-stu-id="49db1-129">You should be aware that if you specify two or more custom sources in a configuration file, only the attributes of the first source are read.</span></span> <span data-ttu-id="49db1-130">Os outros são ignorados.</span><span class="sxs-lookup"><span data-stu-id="49db1-130">The others are ignored.</span></span> <span data-ttu-id="49db1-131">Isso significa que, para o seguinte App. config, arquivo, PII não é conectado para ambas as fontes, embora o log de PII explicitamente está habilitado para a segunda fonte.</span><span class="sxs-lookup"><span data-stu-id="49db1-131">This means that, for the following App.config, file, PII is not logged for both sources even though PII logging is explicitly enabled for the second source.</span></span>  
  
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
  
 <span data-ttu-id="49db1-132">Se o `<machineSettings enableLoggingKnownPii="Boolean"/>` elemento existe fora do arquivo Machine. config, o sistema gera um <xref:System.Configuration.ConfigurationErrorsException>.</span><span class="sxs-lookup"><span data-stu-id="49db1-132">If the `<machineSettings enableLoggingKnownPii="Boolean"/>` element exists outside the Machine.config file, the system throws a <xref:System.Configuration.ConfigurationErrorsException>.</span></span>  
  
 <span data-ttu-id="49db1-133">As alterações entrarão em vigor somente quando o aplicativo inicia ou reinicia.</span><span class="sxs-lookup"><span data-stu-id="49db1-133">The changes are effective only when the application starts or restarts.</span></span> <span data-ttu-id="49db1-134">Um evento é registrado na inicialização, quando ambos os atributos são definidos como `true`.</span><span class="sxs-lookup"><span data-stu-id="49db1-134">An event is logged at startup when both attributes are set to `true`.</span></span> <span data-ttu-id="49db1-135">Também é registrado um evento se `logKnownPii` é definido como `true` mas `enableLoggingKnownPii` é `false`.</span><span class="sxs-lookup"><span data-stu-id="49db1-135">An event is also logged if `logKnownPii` is set to `true` but `enableLoggingKnownPii` is `false`.</span></span>  
  
 <span data-ttu-id="49db1-136">Para obter mais informações sobre o log de PII, consulte [bloqueio de segurança PII](../../../../../docs/framework/wcf/samples/pii-security-lockdown.md) exemplo.</span><span class="sxs-lookup"><span data-stu-id="49db1-136">For more information on PII logging, see [PII Security Lockdown](../../../../../docs/framework/wcf/samples/pii-security-lockdown.md) sample.</span></span>  
  
 <span data-ttu-id="49db1-137">O administrador da máquina e o implantador de aplicativo deve ter muito cuidado ao usar essas duas opções.</span><span class="sxs-lookup"><span data-stu-id="49db1-137">The machine administrator and application deployer should exercise extreme caution when using these two switches.</span></span> <span data-ttu-id="49db1-138">Se o log de PII estiver habilitado, as chaves de segurança e informações de identificação pessoal são registradas.</span><span class="sxs-lookup"><span data-stu-id="49db1-138">If PII logging is enabled, security keys and PII are logged.</span></span> <span data-ttu-id="49db1-139">Se ele estiver desabilitado, os dados específicos do aplicativo ainda estão conectados em cabeçalhos e corpos.</span><span class="sxs-lookup"><span data-stu-id="49db1-139">If it is disabled, sensitive and application-specific data is still logged in message headers and bodies.</span></span> <span data-ttu-id="49db1-140">Para obter uma discussão mais completa sobre privacidade e proteção de informações de identificação pessoal sejam expostas, consulte [privacidade do usuário](http://go.microsoft.com/fwlink/?LinkID=94647).</span><span class="sxs-lookup"><span data-stu-id="49db1-140">For a more thorough discussion on privacy and protecting PII from being exposed, see [User Privacy](http://go.microsoft.com/fwlink/?LinkID=94647).</span></span>  
  
 <span data-ttu-id="49db1-141">Além disso, o endereço IP do remetente da mensagem é registrado uma vez por conexão de transportes voltados para conexão e uma vez por mensagem enviada caso contrário.</span><span class="sxs-lookup"><span data-stu-id="49db1-141">In addition, the IP address of the message sender is logged once per connection for connection-oriented transports, and once per message sent otherwise.</span></span> <span data-ttu-id="49db1-142">Isso é feito sem o consentimento do remetente.</span><span class="sxs-lookup"><span data-stu-id="49db1-142">This is done without the consent of the sender.</span></span> <span data-ttu-id="49db1-143">No entanto, esse log somente ocorre em níveis de rastreamento informações ou Verbose, que não são o padrão ou recomendado níveis de rastreamento em produção, exceto para depuração dinâmica.</span><span class="sxs-lookup"><span data-stu-id="49db1-143">However, this logging only occurs at the Information or Verbose tracing levels, which are not the default or recommended tracing levels in production, except for live debugging.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49db1-144">Consulte também</span><span class="sxs-lookup"><span data-stu-id="49db1-144">See Also</span></span>  
 [<span data-ttu-id="49db1-145">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="49db1-145">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
