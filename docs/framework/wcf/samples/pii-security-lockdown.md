---
title: Bloqueio de segurança PII
ms.date: 03/30/2017
ms.assetid: c44fb338-9527-4dd0-8607-b8787d15acb4
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: ca85a620638509e183703f7e80c01ea20fadbc81
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43778023"
---
# <a name="pii-security-lockdown"></a><span data-ttu-id="faa8f-102">Bloqueio de segurança PII</span><span class="sxs-lookup"><span data-stu-id="faa8f-102">PII Security Lockdown</span></span>
<span data-ttu-id="faa8f-103">Este exemplo demonstra como controlar vários recursos relacionados à segurança de um serviço do Windows Communication Foundation (WCF) por:</span><span class="sxs-lookup"><span data-stu-id="faa8f-103">This sample demonstrates how to control several security-related features of a Windows Communication Foundation (WCF) service by:</span></span>  
  
-   <span data-ttu-id="faa8f-104">Criptografar informações confidenciais no arquivo de configuração do serviço.</span><span class="sxs-lookup"><span data-stu-id="faa8f-104">Encrypting sensitive information in a service's configuration file.</span></span>  
  
-   <span data-ttu-id="faa8f-105">Bloqueio de elementos no arquivo de configuração, de modo que aninhados subdiretórios de serviço não é possível substituir as configurações.</span><span class="sxs-lookup"><span data-stu-id="faa8f-105">Locking elements in the configuration file so that nested service subdirectories cannot override settings.</span></span>  
  
-   <span data-ttu-id="faa8f-106">Controlando o registro em log de pessoalmente identificáveis PII (informações) nos logs de rastreamento e a mensagem.</span><span class="sxs-lookup"><span data-stu-id="faa8f-106">Controlling the logging of Personally Identifiable Information (PII) in trace and message logs.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="faa8f-107">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="faa8f-107">The samples may already be installed on your computer.</span></span> <span data-ttu-id="faa8f-108">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="faa8f-108">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="faa8f-109">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="faa8f-109">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="faa8f-110">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="faa8f-110">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\SecurityLockdown`  
  
## <a name="discussion"></a><span data-ttu-id="faa8f-111">Discussão</span><span class="sxs-lookup"><span data-stu-id="faa8f-111">Discussion</span></span>  
 <span data-ttu-id="faa8f-112">Cada um desses recursos pode ser usadas separadamente ou em conjunto para controlem aspectos de segurança do serviço.</span><span class="sxs-lookup"><span data-stu-id="faa8f-112">Each of these features can be used separately or together to control aspects of a service's security.</span></span> <span data-ttu-id="faa8f-113">Isso não é um guia definitivo para proteger um serviço WCF.</span><span class="sxs-lookup"><span data-stu-id="faa8f-113">This is not a definitive guide to securing a WCF service.</span></span>  
  
 <span data-ttu-id="faa8f-114">Os arquivos de configuração do .NET Framework podem conter informações confidenciais como cadeias de caracteres de conexão para se conectar aos bancos de dados.</span><span class="sxs-lookup"><span data-stu-id="faa8f-114">The .NET Framework configuration files can contain sensitive information such as connection strings to connect to databases.</span></span> <span data-ttu-id="faa8f-115">Em cenários hospedados na Web e compartilhados pode ser desejável para criptografar essas informações no arquivo de configuração para um serviço para que os dados contidos no arquivo de configuração são resistentes a visualização casual.</span><span class="sxs-lookup"><span data-stu-id="faa8f-115">In shared, Web-hosted scenarios it may be desirable to encrypt this information in the configuration file for a service so that the data contained within the configuration file is resistant to casual viewing.</span></span> <span data-ttu-id="faa8f-116">.NET framework 2.0 e posterior tem a capacidade de criptografar as partes do arquivo de configuração usando a DPAPI (interface) ou o provedor de criptografia RSA de programação de aplicativo de proteção de dados do Windows.</span><span class="sxs-lookup"><span data-stu-id="faa8f-116">.NET Framework 2.0 and later has the ability to encrypt portions of the configuration file using the Windows Data Protection application programming interface (DPAPI) or the RSA Cryptographic provider.</span></span> <span data-ttu-id="faa8f-117">O aspnet_regiis.exe usando o RSA ou DPAPI pode criptografar as partes específicas de um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="faa8f-117">The aspnet_regiis.exe using the DPAPI or RSA can encrypt select portions of a configuration file.</span></span>  
  
 <span data-ttu-id="faa8f-118">Em cenários hospedados na Web, é possível ter serviços em subdiretórios de outros serviços.</span><span class="sxs-lookup"><span data-stu-id="faa8f-118">In Web-hosted scenarios it is possible to have services in subdirectories of other services.</span></span> <span data-ttu-id="faa8f-119">O padrão a semântico para determinar os valores de configuração permite que os arquivos de configuração nos diretórios aninhados para substituir os valores de configuração no diretório pai.</span><span class="sxs-lookup"><span data-stu-id="faa8f-119">The default semantic for determining configuration values allows configuration files in the nested directories to override the configuration values in the parent directory.</span></span> <span data-ttu-id="faa8f-120">Em determinadas situações, isso pode ser indesejável para uma variedade de motivos.</span><span class="sxs-lookup"><span data-stu-id="faa8f-120">In certain situations this may be undesirable for a variety of reasons.</span></span> <span data-ttu-id="faa8f-121">WCF serviço configuração oferece suporte o bloqueio dos valores de configuração, de modo que aninhados configuração gera exceções quando um serviço aninhado é executado usando substituído valores de configuração.</span><span class="sxs-lookup"><span data-stu-id="faa8f-121">WCF service configuration supports the locking of configuration values so that nested configuration generates exceptions when a nested service is run using overridden configuration values.</span></span>  
  
 <span data-ttu-id="faa8f-122">Este exemplo demonstra como controlar o registro em log de conhecidos pessoalmente identificáveis PII (informações) nos logs de rastreamento e a mensagem, como nome de usuário e senha.</span><span class="sxs-lookup"><span data-stu-id="faa8f-122">This sample demonstrates how to control the logging of known Personally Identifiable Information (PII) in trace and message logs, such as username and password.</span></span> <span data-ttu-id="faa8f-123">Por padrão, o log de PII conhecido é desabilitado no entanto, em determinadas situações, registro em log das informações de identificação pessoal pode ser importante na depuração de um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="faa8f-123">By default, logging of known PII is disabled however in certain situations logging of PII can be important in debugging an application.</span></span> <span data-ttu-id="faa8f-124">Este exemplo se baseia a [Introdução ao](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="faa8f-124">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span> <span data-ttu-id="faa8f-125">Além disso, este exemplo usa o rastreamento e o registro de mensagem.</span><span class="sxs-lookup"><span data-stu-id="faa8f-125">In addition, this sample uses tracing and message logging.</span></span> <span data-ttu-id="faa8f-126">Para obter mais informações, consulte o [rastreamento e registro em log de mensagem](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) exemplo.</span><span class="sxs-lookup"><span data-stu-id="faa8f-126">For more information, see the [Tracing and Message Logging](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) sample.</span></span>  
  
## <a name="encrypting-configuration-file-elements"></a><span data-ttu-id="faa8f-127">Elementos do arquivo de configuração de criptografia</span><span class="sxs-lookup"><span data-stu-id="faa8f-127">Encrypting Configuration File Elements</span></span>  
 <span data-ttu-id="faa8f-128">Para fins de segurança em um ambiente compartilhado de hospedagem na Web, ele pode ser desejável para criptografar alguns elementos de configuração, como cadeias de caracteres de conexão de banco de dados que podem conter informações confidenciais.</span><span class="sxs-lookup"><span data-stu-id="faa8f-128">For security purposes in a shared Web-hosting environment, it may be desirable to encrypt certain configuration elements, such as database connection strings that may contain sensitive information.</span></span> <span data-ttu-id="faa8f-129">Um elemento de configuração pode ser criptografado usando a ferramenta aspnet_regiis.exe encontrada na pasta do .NET Framework, por exemplo, % WINDIR%\Micrsoft.NET\Framework\v4.0.20728.</span><span class="sxs-lookup"><span data-stu-id="faa8f-129">A configuration element may be encrypted using the aspnet_regiis.exe tool found in the .NET Framework folder For example, %WINDIR%\Micrsoft.NET\Framework\v4.0.20728.</span></span>  
  
#### <a name="to-encrypt-the-values-in-the-appsettings-section-in-webconfig-for-the-sample"></a><span data-ttu-id="faa8f-130">Para criptografar os valores na seção appSettings no Web. config para o exemplo</span><span class="sxs-lookup"><span data-stu-id="faa8f-130">To encrypt the values in the appSettings section in Web.config for the sample</span></span>  
  
1.  <span data-ttu-id="faa8f-131">Abra um prompt de comando usando Iniciar -> Executar...</span><span class="sxs-lookup"><span data-stu-id="faa8f-131">Open a command prompt by using Start->Run….</span></span> <span data-ttu-id="faa8f-132">Digite `cmd` e clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="faa8f-132">Type in `cmd` and click **OK**.</span></span>  
  
2.  <span data-ttu-id="faa8f-133">Navegue até o diretório atual do .NET Framework, emitindo o comando a seguir: `cd %WINDIR%\Microsoft.NET\Framework\v4.0.20728`.</span><span class="sxs-lookup"><span data-stu-id="faa8f-133">Navigate to the current .NET Framework directory by issuing the following command: `cd %WINDIR%\Microsoft.NET\Framework\v4.0.20728`.</span></span>  
  
3.  <span data-ttu-id="faa8f-134">Criptografar as definições de configuração appSettings na pasta Web. config, emitindo o comando a seguir: `aspnet_regiis -pe "appSettings" -app "/servicemodelsamples" -prov "DataProtectionConfigurationProvider"`.</span><span class="sxs-lookup"><span data-stu-id="faa8f-134">Encrypt the appSettings configuration settings in the Web.config folder by issuing the following command: `aspnet_regiis -pe "appSettings" -app "/servicemodelsamples" -prov "DataProtectionConfigurationProvider"`.</span></span>  
  
 <span data-ttu-id="faa8f-135">Para obter mais informações sobre como criptografar seções de arquivos de configuração podem ser encontradas lendo instruções DPAPI na configuração do ASP.NET ([Building Secure ASP.NET Applications: autenticação, autorização e comunicação segura](https://go.microsoft.com/fwlink/?LinkId=95137)) e instruções sobre o RSA na configuração do ASP.NET ([How To: criptografar seções de configuração no ASP.NET 2.0 usando RSA](https://go.microsoft.com/fwlink/?LinkId=95138)).</span><span class="sxs-lookup"><span data-stu-id="faa8f-135">More information about encrypting sections of configuration files can be found by reading a how-to on DPAPI in ASP.NET configuration ([Building Secure ASP.NET Applications: Authentication, Authorization, and Secure Communication](https://go.microsoft.com/fwlink/?LinkId=95137)) and a how-to on RSA in ASP.NET configuration ([How To: Encrypt Configuration Sections in ASP.NET 2.0 Using RSA](https://go.microsoft.com/fwlink/?LinkId=95138)).</span></span>  
  
## <a name="locking-configuration-file-elements"></a><span data-ttu-id="faa8f-136">Elementos de arquivo de configuração de bloqueio</span><span class="sxs-lookup"><span data-stu-id="faa8f-136">Locking configuration file elements</span></span>  
 <span data-ttu-id="faa8f-137">Em cenários hospedados na Web, é possível ter serviços em subdiretórios de serviços.</span><span class="sxs-lookup"><span data-stu-id="faa8f-137">In Web-hosted scenarios, it is possible to have services in subdirectories of services.</span></span> <span data-ttu-id="faa8f-138">Nessas situações, os valores de configuração para o serviço no subdiretório são calculados examinando os valores em Machine. config e mesclando sucessivamente com todos os arquivos Web. config em diretórios pai ao mover para baixo a árvore de diretório e, finalmente, mesclando o Arquivo Web. config no diretório que contém o serviço.</span><span class="sxs-lookup"><span data-stu-id="faa8f-138">In these situations, configuration values for the service in the subdirectory are calculated by examining values in Machine.config and successively merging with any Web.config files in parent directories moving down the directory tree and finally merging the Web.config file in the directory that contains the service.</span></span> <span data-ttu-id="faa8f-139">É o comportamento padrão para a maioria dos elementos de configuração Permitir que os arquivos de configuração em subpastas para substituir os valores definidos em diretórios pai.</span><span class="sxs-lookup"><span data-stu-id="faa8f-139">The default behavior for most configuration elements is to allow configuration files in subdirectories to override the values set in parent directories.</span></span> <span data-ttu-id="faa8f-140">Em determinadas situações, talvez seja desejável para impedir que arquivos de configuração em subdiretórios substituindo os valores definidos na configuração do diretório pai.</span><span class="sxs-lookup"><span data-stu-id="faa8f-140">In certain situations it may be desirable to prevent configuration files in subdirectories from overriding values set in parent directory configuration.</span></span>  
  
 <span data-ttu-id="faa8f-141">O .NET Framework fornece uma maneira de bloquear elementos do arquivo de configuração para que as configurações que substituem elementos de configuração bloqueados lançam exceções de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="faa8f-141">The .NET Framework provides a way to lock configuration file elements so that configurations that override locked configuration elements throw run-time exceptions.</span></span>  
  
 <span data-ttu-id="faa8f-142">Um elemento de configuração pode ser bloqueado, especificando o `lockItem` de atributo para um nó no arquivo de configuração, por exemplo, para bloquear o nó CalculatorServiceBehavior no arquivo de configuração para que os serviços de calculadora no aninhados arquivos de configuração não é possível alterar o comportamento, a configuração a seguir pode ser usado.</span><span class="sxs-lookup"><span data-stu-id="faa8f-142">A configuration element can be locked by specifying the `lockItem` attribute for a node in the configuration file, for example, to lock the CalculatorServiceBehavior node in the configuration file so that calculator services in nested configuration files cannot change the behavior, the following configuration can be used.</span></span>  
  
```xml  
<configuration>  
   <system.serviceModel>  
      <behaviors>   
          <serviceBehaviors>   
             <behavior name="CalculatorServiceBehavior" lockItem="true">   
               <serviceMetadata httpGetEnabled="True"/>   
               <serviceDebug includeExceptionDetailInFaults="False" />   
             </behavior>   
          </serviceBehaviors>   
       </behaviors>   
    </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="faa8f-143">Bloqueio de elementos de configuração pode ser mais específico.</span><span class="sxs-lookup"><span data-stu-id="faa8f-143">Locking of configuration elements can be more specific.</span></span> <span data-ttu-id="faa8f-144">Uma lista de elementos pode ser especificada como o valor para o `lockElements` para bloquear um conjunto de elementos dentro de uma coleção de subelementos.</span><span class="sxs-lookup"><span data-stu-id="faa8f-144">A list of elements can be specified as the value to the `lockElements` to lock a set of elements within a collection of sub-elements.</span></span> <span data-ttu-id="faa8f-145">Uma lista de atributos pode ser especificada como o valor para o `lockAttributes` para bloquear um conjunto de atributos dentro de um elemento.</span><span class="sxs-lookup"><span data-stu-id="faa8f-145">A list of attributes can be specified as the value to the `lockAttributes` to lock a set of attributes within an element.</span></span> <span data-ttu-id="faa8f-146">Uma coleção inteira de elementos ou atributos pode ser bloqueada, exceto para uma lista especificada, especificando o `lockAllElementsExcept` ou `lockAllAttributesExcept` atributos em um nó.</span><span class="sxs-lookup"><span data-stu-id="faa8f-146">An entire collection of elements or attributes can be locked except for a specified list by specifying the `lockAllElementsExcept` or `lockAllAttributesExcept` attributes on a node.</span></span>  
  
## <a name="pii-logging-configuration"></a><span data-ttu-id="faa8f-147">Configuração de log de PII</span><span class="sxs-lookup"><span data-stu-id="faa8f-147">PII Logging Configuration</span></span>  
 <span data-ttu-id="faa8f-148">Registro em log das informações de identificação pessoal é controlado por duas opções: uma configuração de todo o computador encontrada em Machine. config que permite que um administrador do computador permitir ou negar o log de informações de identificação pessoal e uma configuração de aplicativo que permite que um administrador do aplicativo ativar/desativar o registro em log de informações de identificação pessoal para cada o código-fonte em um arquivo Web. config ou App. config.</span><span class="sxs-lookup"><span data-stu-id="faa8f-148">Logging of PII is controlled by two switches: a computer-wide setting found in Machine.config that allows a computer administrator to permit or deny logging of PII and an application setting that allows an application administrator to toggle logging of PII for each source in a Web.config or App.config file.</span></span>  
  
 <span data-ttu-id="faa8f-149">A configuração de todo o computador é controlada pela configuração `enableLoggingKnownPii` à `true` ou `false`, no `machineSettings` elemento em Machine. config. Por exemplo, a seguir permite que os aplicativos ativar o log de PII.</span><span class="sxs-lookup"><span data-stu-id="faa8f-149">The computer-wide setting is controlled by setting `enableLoggingKnownPii` to `true` or `false`, in the `machineSettings` element in Machine.config. For example, the following allows applications to turn on logging of PII.</span></span>  
  
```xml  
<configuration>  
    <system.serviceModel>  
        <machineSettings enableLoggingKnownPii="true" />  
    </system.serviceModel>  
</configuration>  
```  
  
> [!NOTE]
>  <span data-ttu-id="faa8f-150">O arquivo Machine. config tem um local padrão: % WINDIR%\Microsoft.NET\Framework\v2.0.50727\CONFIG.</span><span class="sxs-lookup"><span data-stu-id="faa8f-150">The Machine.config file has a default location: %WINDIR%\Microsoft.NET\Framework\v2.0.50727\CONFIG.</span></span>  
  
 <span data-ttu-id="faa8f-151">Se o `enableLoggingKnownPii` atributo não estiver presente em Machine. config, registro em log de PII não é permitido.</span><span class="sxs-lookup"><span data-stu-id="faa8f-151">If the `enableLoggingKnownPii` attribute is not present in Machine.config, logging of PII is not allowed.</span></span>  
  
 <span data-ttu-id="faa8f-152">Habilitar registro em log de PII para um aplicativo é feito definindo a `logKnownPii` atributo do elemento de origem à `true` ou `false` no arquivo Web. config ou App. config.</span><span class="sxs-lookup"><span data-stu-id="faa8f-152">Enabling logging of PII for an application is done by setting the `logKnownPii` attribute of the source element to `true` or `false` in the Web.config or App.config file.</span></span> <span data-ttu-id="faa8f-153">Por exemplo, a seguir habilita o log de PII para log de mensagens e logs de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="faa8f-153">For example, the following enables logging of PII for both message logging and trace logging.</span></span>  
  
```xml  
<configuration>  
    <system.diagnostics>  
        <sources>  
            <source name="System.ServiceModel.MessageLogging" logKnownPii="true">  
                <listeners>   
                ...   
                </listeners>  
            </source>  
            <source name="System.ServiceModel" switchValue="Verbose, ActivityTracing">  
            <listeners>  
        ...   
            </listeners>  
            </source>  
        </sources>  
    </system.diagnostics>  
</configuration>  
```  
  
 <span data-ttu-id="faa8f-154">Se o `logKnownPii` atributo não for especificado, em seguida, PII não está conectado.</span><span class="sxs-lookup"><span data-stu-id="faa8f-154">If the `logKnownPii` attribute is not specified, then PII is not logged.</span></span>  
  
 <span data-ttu-id="faa8f-155">PII é registrada somente se os dois `enableLoggingKnownPii` é definido como `true`, e `logKnownPii` é definido como `true`.</span><span class="sxs-lookup"><span data-stu-id="faa8f-155">PII is only logged if both `enableLoggingKnownPii` is set to `true`, and `logKnownPii` is set to `true`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="faa8f-156">System. Diagnostics ignora todos os atributos em todas as fontes, exceto o primeiro listados no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="faa8f-156">System.Diagnostics ignores all attributes on all sources except the first one listed in the configuration file.</span></span> <span data-ttu-id="faa8f-157">Adicionando o `logKnownPii` atributo para a segunda fonte no arquivo de configuração não tem nenhum efeito.</span><span class="sxs-lookup"><span data-stu-id="faa8f-157">Adding the `logKnownPii` attribute to the second source in the configuration file has no effect.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="faa8f-158">Para executar este exemplo envolve a modificação manual de Machine. config. Tome cuidado ao modificar o Machine. config como valores incorretos ou sintaxe pode impedir que todos os aplicativos do .NET Framework seja executado.</span><span class="sxs-lookup"><span data-stu-id="faa8f-158">To run this sample involves manual modification of Machine.config. Care should be taken when modifying Machine.config as incorrect values or syntax may prevent all .NET Framework applications from running.</span></span>  
  
 <span data-ttu-id="faa8f-159">Também é possível criptografar os elementos do arquivo de configuração usando DPAPI e RSA.</span><span class="sxs-lookup"><span data-stu-id="faa8f-159">It is also possible to encrypt configuration file elements using DPAPI and RSA.</span></span> <span data-ttu-id="faa8f-160">Para obter mais informações, consulte os links a seguir:</span><span class="sxs-lookup"><span data-stu-id="faa8f-160">For more information, see the following links:</span></span>  
  
-   [<span data-ttu-id="faa8f-161">Criação de aplicativos ASP.NET seguros: Autenticação, autorização e comunicação segura</span><span class="sxs-lookup"><span data-stu-id="faa8f-161">Building Secure ASP.NET Applications: Authentication, Authorization, and Secure Communication</span></span>](https://go.microsoft.com/fwlink/?LinkId=95137)  
  
-   [<span data-ttu-id="faa8f-162">Como: Criptografar seções de configuração no ASP.NET 2.0 usando o RSA</span><span class="sxs-lookup"><span data-stu-id="faa8f-162">How To: Encrypt Configuration Sections in ASP.NET 2.0 Using RSA</span></span>](https://go.microsoft.com/fwlink/?LinkId=95138)  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="faa8f-163">Para configurar, compilar e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="faa8f-163">To set up, build and run the sample</span></span>  
  
1.  <span data-ttu-id="faa8f-164">Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="faa8f-164">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="faa8f-165">Editar Machine. config para definir a `enableLoggingKnownPii` atributo `true`, adicionando os nós pai, se necessário.</span><span class="sxs-lookup"><span data-stu-id="faa8f-165">Edit Machine.config to set the `enableLoggingKnownPii` attribute to `true`, adding the parent nodes if necessary.</span></span>  
  
3.  <span data-ttu-id="faa8f-166">Para compilar a edição em C# ou Visual Basic .NET da solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="faa8f-166">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="faa8f-167">Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="faa8f-167">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
#### <a name="to-clean-up-the-sample"></a><span data-ttu-id="faa8f-168">Para limpar o exemplo</span><span class="sxs-lookup"><span data-stu-id="faa8f-168">To clean up the sample</span></span>  
  
1.  <span data-ttu-id="faa8f-169">Editar Machine. config para definir a `enableLoggingKnownPii` atributo `false`.</span><span class="sxs-lookup"><span data-stu-id="faa8f-169">Edit Machine.config to set the `enableLoggingKnownPii` attribute to `false`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="faa8f-170">Consulte também</span><span class="sxs-lookup"><span data-stu-id="faa8f-170">See Also</span></span>  
 [<span data-ttu-id="faa8f-171">AppFabric que monitora exemplos</span><span class="sxs-lookup"><span data-stu-id="faa8f-171">AppFabric Monitoring Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193959)
