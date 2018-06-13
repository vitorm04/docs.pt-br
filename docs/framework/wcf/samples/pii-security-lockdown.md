---
title: Bloqueio de segurança PII
ms.date: 03/30/2017
ms.assetid: c44fb338-9527-4dd0-8607-b8787d15acb4
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: ec8af8c7df9335774b1f3953f88c2aad438963b6
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33809024"
---
# <a name="pii-security-lockdown"></a><span data-ttu-id="c51f2-102">Bloqueio de segurança PII</span><span class="sxs-lookup"><span data-stu-id="c51f2-102">PII Security Lockdown</span></span>
<span data-ttu-id="c51f2-103">Este exemplo demonstra como controlar vários recursos relacionados à segurança de um serviço do Windows Communication Foundation (WCF) por:</span><span class="sxs-lookup"><span data-stu-id="c51f2-103">This sample demonstrates how to control several security-related features of a Windows Communication Foundation (WCF) service by:</span></span>  
  
-   <span data-ttu-id="c51f2-104">Criptografar informações confidenciais no arquivo de configuração do serviço.</span><span class="sxs-lookup"><span data-stu-id="c51f2-104">Encrypting sensitive information in a service's configuration file.</span></span>  
  
-   <span data-ttu-id="c51f2-105">Bloqueio de elementos no arquivo de configuração para que aninhados subdiretórios de serviço não é possível substituir as configurações.</span><span class="sxs-lookup"><span data-stu-id="c51f2-105">Locking elements in the configuration file so that nested service subdirectories cannot override settings.</span></span>  
  
-   <span data-ttu-id="c51f2-106">Controlando o registro em log da identificação informações pessoal (PII) em logs de rastreamento e a mensagem.</span><span class="sxs-lookup"><span data-stu-id="c51f2-106">Controlling the logging of Personally Identifiable Information (PII) in trace and message logs.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c51f2-107">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="c51f2-107">The samples may already be installed on your computer.</span></span> <span data-ttu-id="c51f2-108">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="c51f2-108">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="c51f2-109">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="c51f2-109">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c51f2-110">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="c51f2-110">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\SecurityLockdown`  
  
## <a name="discussion"></a><span data-ttu-id="c51f2-111">Discussão</span><span class="sxs-lookup"><span data-stu-id="c51f2-111">Discussion</span></span>  
 <span data-ttu-id="c51f2-112">Cada um desses recursos pode ser usadas separadamente ou em conjunto controle aspectos de segurança do serviço.</span><span class="sxs-lookup"><span data-stu-id="c51f2-112">Each of these features can be used separately or together to control aspects of a service's security.</span></span> <span data-ttu-id="c51f2-113">Isso não é um guia definitivo para proteger um serviço WCF.</span><span class="sxs-lookup"><span data-stu-id="c51f2-113">This is not a definitive guide to securing a WCF service.</span></span>  
  
 <span data-ttu-id="c51f2-114">Os arquivos de configuração do .NET Framework podem conter informações confidenciais, como cadeias de caracteres de conexão para se conectar aos bancos de dados.</span><span class="sxs-lookup"><span data-stu-id="c51f2-114">The .NET Framework configuration files can contain sensitive information such as connection strings to connect to databases.</span></span> <span data-ttu-id="c51f2-115">Em cenários compartilhados hospedado na Web, pode ser desejável para criptografar essas informações no arquivo de configuração para um serviço de forma que os dados contidos no arquivo de configuração são resistentes a visualização casual.</span><span class="sxs-lookup"><span data-stu-id="c51f2-115">In shared, Web-hosted scenarios it may be desirable to encrypt this information in the configuration file for a service so that the data contained within the configuration file is resistant to casual viewing.</span></span> <span data-ttu-id="c51f2-116">.NET framework 2.0 e posteriores tem a capacidade de criptografar partes do arquivo de configuração usando o DPAPI (interface) ou o provedor de criptografia RSA de programação de aplicativo de proteção de dados do Windows.</span><span class="sxs-lookup"><span data-stu-id="c51f2-116">.NET Framework 2.0 and later has the ability to encrypt portions of the configuration file using the Windows Data Protection application programming interface (DPAPI) or the RSA Cryptographic provider.</span></span> <span data-ttu-id="c51f2-117">O aspnet_regiis.exe usando a DPAPI ou RSA pode criptografar partes específicas de um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="c51f2-117">The aspnet_regiis.exe using the DPAPI or RSA can encrypt select portions of a configuration file.</span></span>  
  
 <span data-ttu-id="c51f2-118">Em cenários hospedado na Web, é possível ter serviços em subdiretórios de outros serviços.</span><span class="sxs-lookup"><span data-stu-id="c51f2-118">In Web-hosted scenarios it is possible to have services in subdirectories of other services.</span></span> <span data-ttu-id="c51f2-119">O padrão a semântico para determinar os valores de configuração permite que os arquivos de configuração nos diretórios aninhados para substituir os valores de configuração no diretório pai.</span><span class="sxs-lookup"><span data-stu-id="c51f2-119">The default semantic for determining configuration values allows configuration files in the nested directories to override the configuration values in the parent directory.</span></span> <span data-ttu-id="c51f2-120">Em determinadas situações, isso pode ser indesejável para uma variedade de razões.</span><span class="sxs-lookup"><span data-stu-id="c51f2-120">In certain situations this may be undesirable for a variety of reasons.</span></span> <span data-ttu-id="c51f2-121">WCF serviço configuração suporta o bloqueio de valores de configuração para que aninhados configuração gera exceções quando um serviço aninhado é executado usando substituído valores de configuração.</span><span class="sxs-lookup"><span data-stu-id="c51f2-121">WCF service configuration supports the locking of configuration values so that nested configuration generates exceptions when a nested service is run using overridden configuration values.</span></span>  
  
 <span data-ttu-id="c51f2-122">Este exemplo demonstra como controlar o registro em log de conhecidos identificação informações pessoal (PII) em logs de rastreamento e a mensagem, como nome de usuário e senha.</span><span class="sxs-lookup"><span data-stu-id="c51f2-122">This sample demonstrates how to control the logging of known Personally Identifiable Information (PII) in trace and message logs, such as username and password.</span></span> <span data-ttu-id="c51f2-123">Por padrão, o log de PII conhecido está desabilitado no entanto, em certas situações o log de PII pode ser importante na depuração de um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c51f2-123">By default, logging of known PII is disabled however in certain situations logging of PII can be important in debugging an application.</span></span> <span data-ttu-id="c51f2-124">Este exemplo se baseia o [Introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="c51f2-124">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span> <span data-ttu-id="c51f2-125">Além disso, este exemplo usa o rastreamento e o registro de mensagem.</span><span class="sxs-lookup"><span data-stu-id="c51f2-125">In addition, this sample uses tracing and message logging.</span></span> <span data-ttu-id="c51f2-126">Para obter mais informações, consulte o [rastreamento e registro em log de mensagem](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) exemplo.</span><span class="sxs-lookup"><span data-stu-id="c51f2-126">For more information, see the [Tracing and Message Logging](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) sample.</span></span>  
  
## <a name="encrypting-configuration-file-elements"></a><span data-ttu-id="c51f2-127">Elementos do arquivo de configuração de criptografia</span><span class="sxs-lookup"><span data-stu-id="c51f2-127">Encrypting Configuration File Elements</span></span>  
 <span data-ttu-id="c51f2-128">Para fins de segurança em um ambiente compartilhado de hospedagem na Web, pode ser desejável para criptografar determinados elementos de configuração, como cadeias de caracteres de conexão de banco de dados que podem conter informações confidenciais.</span><span class="sxs-lookup"><span data-stu-id="c51f2-128">For security purposes in a shared Web-hosting environment, it may be desirable to encrypt certain configuration elements, such as database connection strings that may contain sensitive information.</span></span> <span data-ttu-id="c51f2-129">Um elemento de configuração pode ser criptografado usando a ferramenta aspnet_regiis.exe encontrada na pasta do .NET Framework, por exemplo, % WINDIR%\Micrsoft.NET\Framework\v4.0.20728.</span><span class="sxs-lookup"><span data-stu-id="c51f2-129">A configuration element may be encrypted using the aspnet_regiis.exe tool found in the .NET Framework folder For example, %WINDIR%\Micrsoft.NET\Framework\v4.0.20728.</span></span>  
  
#### <a name="to-encrypt-the-values-in-the-appsettings-section-in-webconfig-for-the-sample"></a><span data-ttu-id="c51f2-130">Para criptografar os valores na seção appSettings no Web. config para o exemplo</span><span class="sxs-lookup"><span data-stu-id="c51f2-130">To encrypt the values in the appSettings section in Web.config for the sample</span></span>  
  
1.  <span data-ttu-id="c51f2-131">Abra um prompt de comando usando Iniciar -> Executar...</span><span class="sxs-lookup"><span data-stu-id="c51f2-131">Open a command prompt by using Start->Run….</span></span> <span data-ttu-id="c51f2-132">Digite `cmd` e clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="c51f2-132">Type in `cmd` and click **OK**.</span></span>  
  
2.  <span data-ttu-id="c51f2-133">Navegue até o diretório do .NET Framework atual emitindo o comando a seguir: `cd %WINDIR%\Microsoft.NET\Framework\v4.0.20728`.</span><span class="sxs-lookup"><span data-stu-id="c51f2-133">Navigate to the current .NET Framework directory by issuing the following command: `cd %WINDIR%\Microsoft.NET\Framework\v4.0.20728`.</span></span>  
  
3.  <span data-ttu-id="c51f2-134">Criptografar as definições de configuração appSettings na pasta de Web. config, emitindo o comando a seguir: `aspnet_regiis -pe "appSettings" -app "/servicemodelsamples" -prov "DataProtectionConfigurationProvider"`.</span><span class="sxs-lookup"><span data-stu-id="c51f2-134">Encrypt the appSettings configuration settings in the Web.config folder by issuing the following command: `aspnet_regiis -pe "appSettings" -app "/servicemodelsamples" -prov "DataProtectionConfigurationProvider"`.</span></span>  
  
 <span data-ttu-id="c51f2-135">Para obter mais informações sobre como criptografar seções de arquivos de configuração podem ser encontradas lendo um como DPAPI na configuração do ASP.NET ([Building Secure ASP.NET Applications: autenticação, autorização e comunicação segura](http://go.microsoft.com/fwlink/?LinkId=95137)) e um em RSA na configuração do ASP.NET ([How To: criptografar seções de configuração no ASP.NET 2.0 usando RSA](http://go.microsoft.com/fwlink/?LinkId=95138)).</span><span class="sxs-lookup"><span data-stu-id="c51f2-135">More information about encrypting sections of configuration files can be found by reading a how-to on DPAPI in ASP.NET configuration ([Building Secure ASP.NET Applications: Authentication, Authorization, and Secure Communication](http://go.microsoft.com/fwlink/?LinkId=95137)) and a how-to on RSA in ASP.NET configuration ([How To: Encrypt Configuration Sections in ASP.NET 2.0 Using RSA](http://go.microsoft.com/fwlink/?LinkId=95138)).</span></span>  
  
## <a name="locking-configuration-file-elements"></a><span data-ttu-id="c51f2-136">Elementos travamento do arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="c51f2-136">Locking configuration file elements</span></span>  
 <span data-ttu-id="c51f2-137">Em cenários de hospedado na Web, é possível ter serviços em subdiretórios de serviços.</span><span class="sxs-lookup"><span data-stu-id="c51f2-137">In Web-hosted scenarios, it is possible to have services in subdirectories of services.</span></span> <span data-ttu-id="c51f2-138">Nessas situações, os valores de configuração para o serviço no subdiretório são calculados examinando os valores em Machine. config e mesclagem sucessivamente com todos os arquivos Web. config em diretórios pai mover para baixo na árvore do diretório e, finalmente, mesclando os Arquivo Web. config no diretório que contém o serviço.</span><span class="sxs-lookup"><span data-stu-id="c51f2-138">In these situations, configuration values for the service in the subdirectory are calculated by examining values in Machine.config and successively merging with any Web.config files in parent directories moving down the directory tree and finally merging the Web.config file in the directory that contains the service.</span></span> <span data-ttu-id="c51f2-139">É o comportamento padrão para a maioria dos elementos de configuração Permitir que os arquivos de configuração em subdiretórios para substituir os valores definidos nos diretórios pai.</span><span class="sxs-lookup"><span data-stu-id="c51f2-139">The default behavior for most configuration elements is to allow configuration files in subdirectories to override the values set in parent directories.</span></span> <span data-ttu-id="c51f2-140">Em determinadas situações pode ser desejável para impedir que arquivos de configuração em subdiretórios substituindo valores definidos na configuração do diretório pai.</span><span class="sxs-lookup"><span data-stu-id="c51f2-140">In certain situations it may be desirable to prevent configuration files in subdirectories from overriding values set in parent directory configuration.</span></span>  
  
 <span data-ttu-id="c51f2-141">O .NET Framework fornece uma maneira de bloquear elementos do arquivo de configuração para que as configurações que substituem elementos de configuração bloqueada lançam exceções de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="c51f2-141">The .NET Framework provides a way to lock configuration file elements so that configurations that override locked configuration elements throw run-time exceptions.</span></span>  
  
 <span data-ttu-id="c51f2-142">Um elemento de configuração pode ser bloqueado, especificando o `lockItem` de atributo para um nó no arquivo de configuração, por exemplo, para bloquear o nó CalculatorServiceBehavior no arquivo de configuração para que os serviços de cálculo no aninhados arquivos de configuração não é possível alterar o comportamento, a configuração a seguir pode ser usado.</span><span class="sxs-lookup"><span data-stu-id="c51f2-142">A configuration element can be locked by specifying the `lockItem` attribute for a node in the configuration file, for example, to lock the CalculatorServiceBehavior node in the configuration file so that calculator services in nested configuration files cannot change the behavior, the following configuration can be used.</span></span>  
  
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
  
 <span data-ttu-id="c51f2-143">Bloqueio de elementos de configuração pode ser mais específico.</span><span class="sxs-lookup"><span data-stu-id="c51f2-143">Locking of configuration elements can be more specific.</span></span> <span data-ttu-id="c51f2-144">Uma lista de elementos pode ser especificada como o valor para o `lockElements` para bloquear um conjunto de elementos em uma coleção de subelementos.</span><span class="sxs-lookup"><span data-stu-id="c51f2-144">A list of elements can be specified as the value to the `lockElements` to lock a set of elements within a collection of sub-elements.</span></span> <span data-ttu-id="c51f2-145">Uma lista de atributos pode ser especificada como o valor para o `lockAttributes` para bloquear um conjunto de atributos dentro de um elemento.</span><span class="sxs-lookup"><span data-stu-id="c51f2-145">A list of attributes can be specified as the value to the `lockAttributes` to lock a set of attributes within an element.</span></span> <span data-ttu-id="c51f2-146">Uma coleção inteira de elementos ou atributos pode ser bloqueada, exceto uma lista especificada, especificando o `lockAllElementsExcept` ou `lockAllAttributesExcept` atributos em um nó.</span><span class="sxs-lookup"><span data-stu-id="c51f2-146">An entire collection of elements or attributes can be locked except for a specified list by specifying the `lockAllElementsExcept` or `lockAllAttributesExcept` attributes on a node.</span></span>  
  
## <a name="pii-logging-configuration"></a><span data-ttu-id="c51f2-147">Configuração de log de PII</span><span class="sxs-lookup"><span data-stu-id="c51f2-147">PII Logging Configuration</span></span>  
 <span data-ttu-id="c51f2-148">Log de PII é controlado por duas opções: uma configuração de todo o computador encontrada em Machine. config que permite que um administrador do computador permitir ou negar o log de informações de identificação pessoal e uma configuração de aplicativo que permite que um administrador de aplicativo ativar o log de PII para cada fonte em um arquivo App. config ou Web. config.</span><span class="sxs-lookup"><span data-stu-id="c51f2-148">Logging of PII is controlled by two switches: a computer-wide setting found in Machine.config that allows a computer administrator to permit or deny logging of PII and an application setting that allows an application administrator to toggle logging of PII for each source in a Web.config or App.config file.</span></span>  
  
 <span data-ttu-id="c51f2-149">A configuração de todo o computador é controlada pela configuração `enableLoggingKnownPii` para `true` ou `false`, além de `machineSettings` elemento em Machine. config. Por exemplo, o exemplo a seguir permite que aplicativos ativar o log de PII.</span><span class="sxs-lookup"><span data-stu-id="c51f2-149">The computer-wide setting is controlled by setting `enableLoggingKnownPii` to `true` or `false`, in the `machineSettings` element in Machine.config. For example, the following allows applications to turn on logging of PII.</span></span>  
  
```xml  
<configuration>  
    <system.serviceModel>  
        <machineSettings enableLoggingKnownPii="true" />  
    </system.serviceModel>  
</configuration>  
```  
  
> [!NOTE]
>  <span data-ttu-id="c51f2-150">O arquivo Machine. config tem um local padrão: % WINDIR%\Microsoft.NET\Framework\v2.0.50727\CONFIG.</span><span class="sxs-lookup"><span data-stu-id="c51f2-150">The Machine.config file has a default location: %WINDIR%\Microsoft.NET\Framework\v2.0.50727\CONFIG.</span></span>  
  
 <span data-ttu-id="c51f2-151">Se o `enableLoggingKnownPii` atributo não estiver presente em Machine. config, o log de PII não é permitido.</span><span class="sxs-lookup"><span data-stu-id="c51f2-151">If the `enableLoggingKnownPii` attribute is not present in Machine.config, logging of PII is not allowed.</span></span>  
  
 <span data-ttu-id="c51f2-152">Habilitar o log de PII para um aplicativo é feito definindo o `logKnownPii` atributo do elemento de origem para `true` ou `false` no arquivo Web. config ou App. config.</span><span class="sxs-lookup"><span data-stu-id="c51f2-152">Enabling logging of PII for an application is done by setting the `logKnownPii` attribute of the source element to `true` or `false` in the Web.config or App.config file.</span></span> <span data-ttu-id="c51f2-153">Por exemplo, a seguir habilita o log de PII para log de mensagens e logs de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="c51f2-153">For example, the following enables logging of PII for both message logging and trace logging.</span></span>  
  
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
  
 <span data-ttu-id="c51f2-154">Se o `logKnownPii` atributo não for especificado, em seguida, informações de identificação pessoal não está conectada.</span><span class="sxs-lookup"><span data-stu-id="c51f2-154">If the `logKnownPii` attribute is not specified, then PII is not logged.</span></span>  
  
 <span data-ttu-id="c51f2-155">Informações de identificação pessoal são registradas apenas se os dois `enableLoggingKnownPii` é definido como `true`, e `logKnownPii` é definido como `true`.</span><span class="sxs-lookup"><span data-stu-id="c51f2-155">PII is only logged if both `enableLoggingKnownPii` is set to `true`, and `logKnownPii` is set to `true`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c51f2-156">System. Diagnostics ignora todos os atributos em todas as fontes, exceto o primeiro listados no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="c51f2-156">System.Diagnostics ignores all attributes on all sources except the first one listed in the configuration file.</span></span> <span data-ttu-id="c51f2-157">Adicionando o `logKnownPii` atributo para a segunda fonte no arquivo de configuração não tem nenhum efeito.</span><span class="sxs-lookup"><span data-stu-id="c51f2-157">Adding the `logKnownPii` attribute to the second source in the configuration file has no effect.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c51f2-158">Para executar esse exemplo envolve a modificação manual de Machine. config. Deve-se ter cuidado ao modificar o Machine. config como valores incorretos ou sintaxe pode impedir que todos os aplicativos do .NET Framework em execução.</span><span class="sxs-lookup"><span data-stu-id="c51f2-158">To run this sample involves manual modification of Machine.config. Care should be taken when modifying Machine.config as incorrect values or syntax may prevent all .NET Framework applications from running.</span></span>  
  
 <span data-ttu-id="c51f2-159">Também é possível criptografar os elementos do arquivo de configuração usando DPAPI e RSA.</span><span class="sxs-lookup"><span data-stu-id="c51f2-159">It is also possible to encrypt configuration file elements using DPAPI and RSA.</span></span> <span data-ttu-id="c51f2-160">Para obter mais informações, consulte os links a seguir:</span><span class="sxs-lookup"><span data-stu-id="c51f2-160">For more information, see the following links:</span></span>  
  
-   [<span data-ttu-id="c51f2-161">Criando aplicativos do ASP.NET seguros: Autenticação, autorização e comunicação segura</span><span class="sxs-lookup"><span data-stu-id="c51f2-161">Building Secure ASP.NET Applications: Authentication, Authorization, and Secure Communication</span></span>](http://go.microsoft.com/fwlink/?LinkId=95137)  
  
-   [<span data-ttu-id="c51f2-162">Como: Criptografar seções de configuração no ASP.NET 2.0 usando o RSA</span><span class="sxs-lookup"><span data-stu-id="c51f2-162">How To: Encrypt Configuration Sections in ASP.NET 2.0 Using RSA</span></span>](http://go.microsoft.com/fwlink/?LinkId=95138)  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c51f2-163">Para configurar, compilar e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="c51f2-163">To set up, build and run the sample</span></span>  
  
1.  <span data-ttu-id="c51f2-164">Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c51f2-164">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="c51f2-165">Editar o Machine. config para definir o `enableLoggingKnownPii` atributo `true`, adicionar os nós pai, se necessário.</span><span class="sxs-lookup"><span data-stu-id="c51f2-165">Edit Machine.config to set the `enableLoggingKnownPii` attribute to `true`, adding the parent nodes if necessary.</span></span>  
  
3.  <span data-ttu-id="c51f2-166">Para compilar o c# ou Visual Basic .NET edição da solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c51f2-166">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="c51f2-167">Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c51f2-167">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
#### <a name="to-clean-up-the-sample"></a><span data-ttu-id="c51f2-168">Para limpar o exemplo</span><span class="sxs-lookup"><span data-stu-id="c51f2-168">To clean up the sample</span></span>  
  
1.  <span data-ttu-id="c51f2-169">Editar o Machine. config para definir o `enableLoggingKnownPii` atributo `false`.</span><span class="sxs-lookup"><span data-stu-id="c51f2-169">Edit Machine.config to set the `enableLoggingKnownPii` attribute to `false`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c51f2-170">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c51f2-170">See Also</span></span>  
 [<span data-ttu-id="c51f2-171">Exemplos de monitoramento do AppFabric</span><span class="sxs-lookup"><span data-stu-id="c51f2-171">AppFabric Monitoring Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193959)
