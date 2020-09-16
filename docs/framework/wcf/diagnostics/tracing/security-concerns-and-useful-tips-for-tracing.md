---
title: Preocupações de segurança e dicas úteis para rastreamento
ms.date: 03/30/2017
ms.assetid: 88bc2880-ecb9-47cd-9816-39016a07076f
ms.openlocfilehash: 91a1b4bab3ac47f41821ad69228310c3993cf037
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555036"
---
# <a name="security-concerns-and-useful-tips-for-tracing"></a><span data-ttu-id="0a54b-102">Preocupações de segurança e dicas úteis para rastreamento</span><span class="sxs-lookup"><span data-stu-id="0a54b-102">Security Concerns and Useful Tips for Tracing</span></span>
<span data-ttu-id="0a54b-103">Este tópico descreve como você pode proteger informações confidenciais de serem expostas, bem como dicas úteis ao usar o webhost.</span><span class="sxs-lookup"><span data-stu-id="0a54b-103">This topic describes how you can protect sensitive information from being exposed, as well as useful tips when using WebHost.</span></span>  
  
## <a name="using-a-custom-trace-listener-with-webhost"></a><span data-ttu-id="0a54b-104">Usando um ouvinte de rastreamento personalizado com Webhost</span><span class="sxs-lookup"><span data-stu-id="0a54b-104">Using a Custom Trace Listener with WebHost</span></span>  
 <span data-ttu-id="0a54b-105">Se estiver escrevendo seu próprio ouvinte de rastreamento, você deve estar ciente da possibilidade de que os rastreamentos possam ser perdidos no caso de um serviço hospedado na Web.</span><span class="sxs-lookup"><span data-stu-id="0a54b-105">If you are writing your own trace listener, you should be aware of the possibility that traces might be lost in the case of a Web-hosted service.</span></span> <span data-ttu-id="0a54b-106">Quando o Webhost é reciclado, ele desliga o processo em tempo real enquanto uma duplicata assume.</span><span class="sxs-lookup"><span data-stu-id="0a54b-106">When WebHost recycles, it shuts down the live process while a duplicate takes over.</span></span> <span data-ttu-id="0a54b-107">No entanto, os dois processos ainda devem ter acesso ao mesmo recurso por algum tempo, o que depende do tipo de ouvinte.</span><span class="sxs-lookup"><span data-stu-id="0a54b-107">However, the two processes must still have access to the same resource for some time, which is dependent on the listener type.</span></span> <span data-ttu-id="0a54b-108">Nesse caso, o `XmlWriterTraceListener` cria um novo arquivo de rastreamento para o segundo processo; enquanto o rastreamento de eventos do Windows gerencia vários processos dentro da mesma sessão e fornece acesso ao mesmo arquivo.</span><span class="sxs-lookup"><span data-stu-id="0a54b-108">In this case, , `XmlWriterTraceListener` creates a new trace file for the second process; while Windows event tracing manages multiple processes within the same session and gives access to the same file.</span></span> <span data-ttu-id="0a54b-109">Se seu próprio ouvinte não fornecer funcionalidades semelhantes, os rastreamentos poderão ser perdidos quando o arquivo for bloqueado pelos dois processos.</span><span class="sxs-lookup"><span data-stu-id="0a54b-109">If your own listener does not provide similar functionalities, traces can be lost when the file is locked up by the two processes.</span></span>  
  
 <span data-ttu-id="0a54b-110">Você também deve estar ciente de que um ouvinte de rastreamento personalizado pode enviar rastreamentos e mensagens na conexão, por exemplo, para um banco de dados remoto.</span><span class="sxs-lookup"><span data-stu-id="0a54b-110">You should also be aware that a custom trace listener can send traces and messages on the wire, for example, to a remote database.</span></span> <span data-ttu-id="0a54b-111">Como um implantador de aplicativos, você deve configurar ouvintes personalizados com o controle de acesso apropriado.</span><span class="sxs-lookup"><span data-stu-id="0a54b-111">As an application deployer, you should configure custom listeners with appropriate access control.</span></span> <span data-ttu-id="0a54b-112">Você também deve aplicar o controle de segurança em qualquer informação pessoal que possa ser exposta no local remoto.</span><span class="sxs-lookup"><span data-stu-id="0a54b-112">You should also apply security control on any personal information that can be exposed at the remote location.</span></span>  
  
## <a name="logging-sensitive-information"></a><span data-ttu-id="0a54b-113">Registrando informações confidenciais</span><span class="sxs-lookup"><span data-stu-id="0a54b-113">Logging Sensitive Information</span></span>  
 <span data-ttu-id="0a54b-114">Os rastreamentos contêm cabeçalhos de mensagem quando uma mensagem está no escopo.</span><span class="sxs-lookup"><span data-stu-id="0a54b-114">Traces contain message headers when a message is in scope.</span></span> <span data-ttu-id="0a54b-115">Quando o rastreamento está habilitado, as informações pessoais em cabeçalhos específicos do aplicativo, como uma cadeia de caracteres de consulta; e as informações de corpo, como um número de cartão de crédito, podem se tornar visíveis nos logs.</span><span class="sxs-lookup"><span data-stu-id="0a54b-115">When tracing is enabled, personal information in application-specific headers, such as, a query string; and body information, such as, a credit card number, can become visible in the logs.</span></span> <span data-ttu-id="0a54b-116">O implantador de aplicativos é responsável por impor o controle de acesso nos arquivos de configuração e de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="0a54b-116">The application deployer is responsible for enforcing access control on the configuration and trace files.</span></span> <span data-ttu-id="0a54b-117">Se você não quiser que esse tipo de informação fique visível, desabilite o rastreamento ou filtre parte dos dados se desejar compartilhar os logs de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="0a54b-117">If you do not want this kind of information to be visible, you should disable tracing, or filter out part of the data if you want to share the trace logs.</span></span>  
  
 <span data-ttu-id="0a54b-118">As dicas a seguir podem ajudá-lo a impedir que o conteúdo de um arquivo de rastreamento seja exposto de forma não intencional:</span><span class="sxs-lookup"><span data-stu-id="0a54b-118">The following tips can help you to prevent the content of a trace file from being exposed unintentionally:</span></span>  
  
- <span data-ttu-id="0a54b-119">Verifique se os arquivos de log estão protegidos por ACLs (listas de controle de acesso) em cenários de hospedagem interna e de host.</span><span class="sxs-lookup"><span data-stu-id="0a54b-119">Ensure that the log files are protected by Access Control Lists (ACL) both in WebHost and self-host scenarios.</span></span>  
  
- <span data-ttu-id="0a54b-120">Escolha uma extensão de arquivo que não possa ser facilmente servida usando uma solicitação da Web.</span><span class="sxs-lookup"><span data-stu-id="0a54b-120">Choose a file extension that cannot be easily served using a Web request.</span></span> <span data-ttu-id="0a54b-121">Por exemplo, a extensão de arquivo. xml não é uma opção segura.</span><span class="sxs-lookup"><span data-stu-id="0a54b-121">For example, the .xml file extension is not a safe choice.</span></span> <span data-ttu-id="0a54b-122">Você pode verificar o guia de administração do IIS para ver uma lista de extensões que podem ser servidas.</span><span class="sxs-lookup"><span data-stu-id="0a54b-122">You can check the IIS administration guide to see a list of extensions that can be served.</span></span>  
  
- <span data-ttu-id="0a54b-123">Especifique um caminho absoluto para o local do arquivo de log, que deve estar fora do diretório público do Webhost vroot para impedir que ele seja acessado por uma parte externa usando um navegador da Web.</span><span class="sxs-lookup"><span data-stu-id="0a54b-123">Specify an absolute path for the log file location, which should be outside of the WebHost vroot public directory to prevent it from being accessed by an external party using a Web browser.</span></span>  
  
 <span data-ttu-id="0a54b-124">Por padrão, as chaves e as informações de identificação pessoal (PII), como nome de usuário e senha, não são registradas em rastreamentos e mensagens registradas.</span><span class="sxs-lookup"><span data-stu-id="0a54b-124">By default, keys and personally identifiable information (PII) such as username and password are not logged in traces and logged messages.</span></span> <span data-ttu-id="0a54b-125">Um administrador de máquina, no entanto, pode usar o `enableLoggingKnownPII` atributo no `machineSettings` elemento do arquivo de Machine.config para permitir que os aplicativos em execução no computador registrem PII (informações de identificação pessoal) conhecidas da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="0a54b-125">A machine administrator, however, can use the `enableLoggingKnownPII` attribute in the `machineSettings` element of the Machine.config file to permit applications running on the machine to log known personally identifiable information (PII) as follows:</span></span>  
  
```xml  
<configuration>  
   <system.ServiceModel>  
      <machineSettings enableLoggingKnownPii="Boolean"/>  
   </system.ServiceModel>  
</configuration>
```  
  
 <span data-ttu-id="0a54b-126">Um implantador de aplicativo pode usar o `logKnownPii` atributo no arquivo App.config ou Web.config para habilitar o log de PII da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="0a54b-126">An application deployer can then use the `logKnownPii` attribute in either the App.config or Web.config file to enable PII logging as follows:</span></span>  
  
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
  
 <span data-ttu-id="0a54b-127">Somente quando as duas configurações são o `true` log de PII habilitado.</span><span class="sxs-lookup"><span data-stu-id="0a54b-127">Only when both settings are `true` is PII logging enabled.</span></span> <span data-ttu-id="0a54b-128">A combinação de duas opções permite a flexibilidade de registrar PII conhecida para cada aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0a54b-128">The combination of two switches allows the flexibility to log known PII for each application.</span></span>  
  
 <span data-ttu-id="0a54b-129">Você deve estar ciente de que, se você especificar duas ou mais fontes personalizadas em um arquivo de configuração, somente os atributos da primeira fonte serão lidos.</span><span class="sxs-lookup"><span data-stu-id="0a54b-129">You should be aware that if you specify two or more custom sources in a configuration file, only the attributes of the first source are read.</span></span> <span data-ttu-id="0a54b-130">Os outros são ignorados.</span><span class="sxs-lookup"><span data-stu-id="0a54b-130">The others are ignored.</span></span> <span data-ttu-id="0a54b-131">Isso significa que, para o seguinte App.config, File, PII não é registrado para ambas as fontes, mesmo que o log de PII seja explicitamente habilitado para a segunda fonte.</span><span class="sxs-lookup"><span data-stu-id="0a54b-131">This means that, for the following App.config, file, PII is not logged for both sources even though PII logging is explicitly enabled for the second source.</span></span>  
  
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
  
 <span data-ttu-id="0a54b-132">Se o `<machineSettings enableLoggingKnownPii="Boolean"/>` elemento existir fora do arquivo de Machine.config, o sistema lançará um <xref:System.Configuration.ConfigurationErrorsException> .</span><span class="sxs-lookup"><span data-stu-id="0a54b-132">If the `<machineSettings enableLoggingKnownPii="Boolean"/>` element exists outside the Machine.config file, the system throws a <xref:System.Configuration.ConfigurationErrorsException>.</span></span>  
  
 <span data-ttu-id="0a54b-133">As alterações entram em vigor somente quando o aplicativo é iniciado ou reiniciado.</span><span class="sxs-lookup"><span data-stu-id="0a54b-133">The changes are effective only when the application starts or restarts.</span></span> <span data-ttu-id="0a54b-134">Um evento é registrado na inicialização quando ambos os atributos são definidos como `true` .</span><span class="sxs-lookup"><span data-stu-id="0a54b-134">An event is logged at startup when both attributes are set to `true`.</span></span> <span data-ttu-id="0a54b-135">Um evento também será registrado se `logKnownPii` for definido como `true` , mas `enableLoggingKnownPii` for `false` .</span><span class="sxs-lookup"><span data-stu-id="0a54b-135">An event is also logged if `logKnownPii` is set to `true` but `enableLoggingKnownPii` is `false`.</span></span>  
  
 <span data-ttu-id="0a54b-136">Para obter mais informações sobre o log de PII, consulte exemplo de [bloqueio de segurança de PII](../../samples/pii-security-lockdown.md) .</span><span class="sxs-lookup"><span data-stu-id="0a54b-136">For more information on PII logging, see [PII Security Lockdown](../../samples/pii-security-lockdown.md) sample.</span></span>  
  
 <span data-ttu-id="0a54b-137">O administrador do computador e o implantador de aplicativos devem ter muito cuidado ao usar essas duas opções.</span><span class="sxs-lookup"><span data-stu-id="0a54b-137">The machine administrator and application deployer should exercise extreme caution when using these two switches.</span></span> <span data-ttu-id="0a54b-138">Se o log de PII estiver habilitado, as chaves de segurança e PII serão registradas.</span><span class="sxs-lookup"><span data-stu-id="0a54b-138">If PII logging is enabled, security keys and PII are logged.</span></span> <span data-ttu-id="0a54b-139">Se estiver desabilitado, os dados confidenciais e específicos do aplicativo ainda serão registrados em cabeçalhos e corpos de mensagens.</span><span class="sxs-lookup"><span data-stu-id="0a54b-139">If it is disabled, sensitive and application-specific data is still logged in message headers and bodies.</span></span> <span data-ttu-id="0a54b-140">Para obter uma discussão mais completa sobre privacidade e proteger a PII de ser exposta, consulte [privacidade do usuário](/previous-versions/dotnet/articles/aa480490(v=msdn.10)).</span><span class="sxs-lookup"><span data-stu-id="0a54b-140">For a more thorough discussion on privacy and protecting PII from being exposed, see [User Privacy](/previous-versions/dotnet/articles/aa480490(v=msdn.10)).</span></span>  
  
 <span data-ttu-id="0a54b-141">Além disso, o endereço IP do remetente da mensagem é registrado uma vez por conexão para transportes orientados por conexão e uma vez por mensagem enviada de outra forma.</span><span class="sxs-lookup"><span data-stu-id="0a54b-141">In addition, the IP address of the message sender is logged once per connection for connection-oriented transports, and once per message sent otherwise.</span></span> <span data-ttu-id="0a54b-142">Isso é feito sem o consentimento do remetente.</span><span class="sxs-lookup"><span data-stu-id="0a54b-142">This is done without the consent of the sender.</span></span> <span data-ttu-id="0a54b-143">No entanto, esse log só ocorre nas informações ou níveis de rastreamento detalhados, que não são os níveis de rastreamento padrão ou recomendados na produção, exceto para a depuração dinâmica.</span><span class="sxs-lookup"><span data-stu-id="0a54b-143">However, this logging only occurs at the Information or Verbose tracing levels, which are not the default or recommended tracing levels in production, except for live debugging.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a54b-144">Confira também</span><span class="sxs-lookup"><span data-stu-id="0a54b-144">See also</span></span>

- [<span data-ttu-id="0a54b-145">Rastreamento</span><span class="sxs-lookup"><span data-stu-id="0a54b-145">Tracing</span></span>](index.md)
