---
title: Bloqueio de segurança PII
ms.date: 03/30/2017
ms.assetid: c44fb338-9527-4dd0-8607-b8787d15acb4
ms.openlocfilehash: 62e1495927cad669771c560603919e8f6b94d863
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90559357"
---
# <a name="pii-security-lockdown"></a><span data-ttu-id="f0f4d-102">Bloqueio de segurança PII</span><span class="sxs-lookup"><span data-stu-id="f0f4d-102">PII Security Lockdown</span></span>
<span data-ttu-id="f0f4d-103">Este exemplo demonstra como controlar vários recursos relacionados à segurança de um serviço Windows Communication Foundation (WCF) da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="f0f4d-103">This sample demonstrates how to control several security-related features of a Windows Communication Foundation (WCF) service by:</span></span>  
  
- <span data-ttu-id="f0f4d-104">Criptografia de informações confidenciais no arquivo de configuração de um serviço.</span><span class="sxs-lookup"><span data-stu-id="f0f4d-104">Encrypting sensitive information in a service's configuration file.</span></span>  
  
- <span data-ttu-id="f0f4d-105">Bloqueando elementos no arquivo de configuração para que os subdiretórios de serviço aninhados não possam substituir as configurações.</span><span class="sxs-lookup"><span data-stu-id="f0f4d-105">Locking elements in the configuration file so that nested service subdirectories cannot override settings.</span></span>  
  
- <span data-ttu-id="f0f4d-106">Controle do log de informações de identificação pessoal (PII) em logs de mensagens e rastreamento.</span><span class="sxs-lookup"><span data-stu-id="f0f4d-106">Controlling the logging of Personally Identifiable Information (PII) in trace and message logs.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="f0f4d-107">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="f0f4d-107">The samples may already be installed on your computer.</span></span> <span data-ttu-id="f0f4d-108">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="f0f4d-108">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="f0f4d-109">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="f0f4d-109">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f0f4d-110">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="f0f4d-110">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\SecurityLockdown`  
  
## <a name="discussion"></a><span data-ttu-id="f0f4d-111">Discussão</span><span class="sxs-lookup"><span data-stu-id="f0f4d-111">Discussion</span></span>  
 <span data-ttu-id="f0f4d-112">Cada um desses recursos pode ser usado separadamente ou em conjunto para controlar aspectos da segurança de um serviço.</span><span class="sxs-lookup"><span data-stu-id="f0f4d-112">Each of these features can be used separately or together to control aspects of a service's security.</span></span> <span data-ttu-id="f0f4d-113">Esse não é um guia definitivo para proteger um serviço WCF.</span><span class="sxs-lookup"><span data-stu-id="f0f4d-113">This is not a definitive guide to securing a WCF service.</span></span>  
  
 <span data-ttu-id="f0f4d-114">Os arquivos de configuração de .NET Framework podem conter informações confidenciais, como cadeias de conexão para se conectar a bancos de dados.</span><span class="sxs-lookup"><span data-stu-id="f0f4d-114">The .NET Framework configuration files can contain sensitive information such as connection strings to connect to databases.</span></span> <span data-ttu-id="f0f4d-115">Em cenários hospedados na Web, pode ser desejável criptografar essas informações no arquivo de configuração para um serviço para que os dados contidos no arquivo de configuração sejam resistentes à exibição casual.</span><span class="sxs-lookup"><span data-stu-id="f0f4d-115">In shared, Web-hosted scenarios it may be desirable to encrypt this information in the configuration file for a service so that the data contained within the configuration file is resistant to casual viewing.</span></span> <span data-ttu-id="f0f4d-116">.NET Framework 2,0 e posteriores têm a capacidade de criptografar partes do arquivo de configuração usando a interface de programação de aplicativo de proteção de dados do Windows (DPAPI) ou o provedor de criptografia RSA.</span><span class="sxs-lookup"><span data-stu-id="f0f4d-116">.NET Framework 2.0 and later has the ability to encrypt portions of the configuration file using the Windows Data Protection application programming interface (DPAPI) or the RSA Cryptographic provider.</span></span> <span data-ttu-id="f0f4d-117">O aspnet_regiis.exe usando o DPAPI ou RSA pode criptografar partes selecionadas de um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="f0f4d-117">The aspnet_regiis.exe using the DPAPI or RSA can encrypt select portions of a configuration file.</span></span>  
  
 <span data-ttu-id="f0f4d-118">Em cenários hospedados na Web, é possível ter serviços em subdiretórios de outros serviços.</span><span class="sxs-lookup"><span data-stu-id="f0f4d-118">In Web-hosted scenarios it is possible to have services in subdirectories of other services.</span></span> <span data-ttu-id="f0f4d-119">A semântica padrão para determinar os valores de configuração permite que os arquivos de configuração nos diretórios aninhados substituam os valores de configuração no diretório pai.</span><span class="sxs-lookup"><span data-stu-id="f0f4d-119">The default semantic for determining configuration values allows configuration files in the nested directories to override the configuration values in the parent directory.</span></span> <span data-ttu-id="f0f4d-120">Em determinadas situações, isso pode ser indesejável por vários motivos.</span><span class="sxs-lookup"><span data-stu-id="f0f4d-120">In certain situations this may be undesirable for a variety of reasons.</span></span> <span data-ttu-id="f0f4d-121">A configuração do serviço WCF dá suporte ao bloqueio de valores de configuração para que a configuração aninhada gere exceções quando um serviço aninhado for executado usando valores de configuração substituídos.</span><span class="sxs-lookup"><span data-stu-id="f0f4d-121">WCF service configuration supports the locking of configuration values so that nested configuration generates exceptions when a nested service is run using overridden configuration values.</span></span>  
  
 <span data-ttu-id="f0f4d-122">Este exemplo demonstra como controlar o log de PII (informações de identificação pessoal) conhecidas em logs de rastreamento e de mensagens, como nome de usuário e senha.</span><span class="sxs-lookup"><span data-stu-id="f0f4d-122">This sample demonstrates how to control the logging of known Personally Identifiable Information (PII) in trace and message logs, such as username and password.</span></span> <span data-ttu-id="f0f4d-123">Por padrão, o log de PII conhecidas é desabilitado no entanto, em determinadas situações, o registro em log de PII pode ser importante na depuração de um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f0f4d-123">By default, logging of known PII is disabled however in certain situations logging of PII can be important in debugging an application.</span></span> <span data-ttu-id="f0f4d-124">Este exemplo é baseado na [introdução](getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="f0f4d-124">This sample is based on the [Getting Started](getting-started-sample.md).</span></span> <span data-ttu-id="f0f4d-125">Além disso, este exemplo usa rastreamento e log de mensagens.</span><span class="sxs-lookup"><span data-stu-id="f0f4d-125">In addition, this sample uses tracing and message logging.</span></span> <span data-ttu-id="f0f4d-126">Para obter mais informações, consulte o exemplo de [rastreamento e log de mensagens](tracing-and-message-logging.md) .</span><span class="sxs-lookup"><span data-stu-id="f0f4d-126">For more information, see the [Tracing and Message Logging](tracing-and-message-logging.md) sample.</span></span>  
  
## <a name="encrypting-configuration-file-elements"></a><span data-ttu-id="f0f4d-127">Criptografando elementos do arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="f0f4d-127">Encrypting Configuration File Elements</span></span>  
 <span data-ttu-id="f0f4d-128">Para fins de segurança em um ambiente de hospedagem na Web compartilhado, pode ser desejável criptografar determinados elementos de configuração, como cadeias de conexão de banco de dados que podem conter informações confidenciais.</span><span class="sxs-lookup"><span data-stu-id="f0f4d-128">For security purposes in a shared Web-hosting environment, it may be desirable to encrypt certain configuration elements, such as database connection strings that may contain sensitive information.</span></span> <span data-ttu-id="f0f4d-129">Um elemento de configuração pode ser criptografado usando a ferramenta de aspnet_regiis.exe encontrada na pasta .NET Framework, por exemplo,%WINDIR%\Microsoft.NET\Framework\v4.0.20728.</span><span class="sxs-lookup"><span data-stu-id="f0f4d-129">A configuration element may be encrypted using the aspnet_regiis.exe tool found in the .NET Framework folder For example, %WINDIR%\Microsoft.NET\Framework\v4.0.20728.</span></span>  
  
#### <a name="to-encrypt-the-values-in-the-appsettings-section-in-webconfig-for-the-sample"></a><span data-ttu-id="f0f4d-130">Para criptografar os valores na seção appSettings em Web.config para o exemplo</span><span class="sxs-lookup"><span data-stu-id="f0f4d-130">To encrypt the values in the appSettings section in Web.config for the sample</span></span>  
  
1. <span data-ttu-id="f0f4d-131">Abra um prompt de comando usando Start->executar....</span><span class="sxs-lookup"><span data-stu-id="f0f4d-131">Open a command prompt by using Start->Run….</span></span> <span data-ttu-id="f0f4d-132">Digite `cmd` e clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="f0f4d-132">Type in `cmd` and click **OK**.</span></span>  
  
2. <span data-ttu-id="f0f4d-133">Navegue até o diretório de .NET Framework atual emitindo o seguinte comando: `cd %WINDIR%\Microsoft.NET\Framework\v4.0.20728` .</span><span class="sxs-lookup"><span data-stu-id="f0f4d-133">Navigate to the current .NET Framework directory by issuing the following command: `cd %WINDIR%\Microsoft.NET\Framework\v4.0.20728`.</span></span>  
  
3. <span data-ttu-id="f0f4d-134">Criptografe as definições de configuração appSettings na pasta Web.config emitindo o seguinte comando: `aspnet_regiis -pe "appSettings" -app "/servicemodelsamples" -prov "DataProtectionConfigurationProvider"` .</span><span class="sxs-lookup"><span data-stu-id="f0f4d-134">Encrypt the appSettings configuration settings in the Web.config folder by issuing the following command: `aspnet_regiis -pe "appSettings" -app "/servicemodelsamples" -prov "DataProtectionConfigurationProvider"`.</span></span>  
  
 <span data-ttu-id="f0f4d-135">Mais informações sobre como criptografar seções de arquivos de configuração podem ser encontradas lendo um instruções sobre DPAPI na configuração do ASP.NET ([compilando aplicativos seguros do ASP.net: autenticação, autorização e comunicação segura](/previous-versions/msp-n-p/ff649248(v=pandp.10))) e um "como" na configuração do ASP.net ([como: criptografar seções de configuração no ASP.NET 2,0 usando RSA](/previous-versions/msp-n-p/ff650304(v=pandp.10))).</span><span class="sxs-lookup"><span data-stu-id="f0f4d-135">More information about encrypting sections of configuration files can be found by reading a how-to on DPAPI in ASP.NET configuration ([Building Secure ASP.NET Applications: Authentication, Authorization, and Secure Communication](/previous-versions/msp-n-p/ff649248(v=pandp.10))) and a how-to on RSA in ASP.NET configuration ([How To: Encrypt Configuration Sections in ASP.NET 2.0 Using RSA](/previous-versions/msp-n-p/ff650304(v=pandp.10))).</span></span>  
  
## <a name="locking-configuration-file-elements"></a><span data-ttu-id="f0f4d-136">Elementos do arquivo de configuração de bloqueio</span><span class="sxs-lookup"><span data-stu-id="f0f4d-136">Locking configuration file elements</span></span>  
 <span data-ttu-id="f0f4d-137">Em cenários hospedados na Web, é possível ter serviços em subdiretórios de serviços.</span><span class="sxs-lookup"><span data-stu-id="f0f4d-137">In Web-hosted scenarios, it is possible to have services in subdirectories of services.</span></span> <span data-ttu-id="f0f4d-138">Nessas situações, os valores de configuração para o serviço no subdiretório são calculados examinando valores em Machine.config e mesclando sucessivamente com qualquer Web.config arquivos em diretórios pai que se movem para baixo na árvore de diretórios e, por fim, mesclam o arquivo de Web.config no diretório que contém o serviço.</span><span class="sxs-lookup"><span data-stu-id="f0f4d-138">In these situations, configuration values for the service in the subdirectory are calculated by examining values in Machine.config and successively merging with any Web.config files in parent directories moving down the directory tree and finally merging the Web.config file in the directory that contains the service.</span></span> <span data-ttu-id="f0f4d-139">O comportamento padrão para a maioria dos elementos de configuração é permitir que os arquivos de configuração em subdiretórios substituam os valores definidos em diretórios pai.</span><span class="sxs-lookup"><span data-stu-id="f0f4d-139">The default behavior for most configuration elements is to allow configuration files in subdirectories to override the values set in parent directories.</span></span> <span data-ttu-id="f0f4d-140">Em determinadas situações, pode ser desejável impedir que arquivos de configuração em subdiretórios substituam valores definidos na configuração de diretório pai.</span><span class="sxs-lookup"><span data-stu-id="f0f4d-140">In certain situations it may be desirable to prevent configuration files in subdirectories from overriding values set in parent directory configuration.</span></span>  
  
 <span data-ttu-id="f0f4d-141">O .NET Framework fornece uma maneira de Bloquear elementos do arquivo de configuração para que as configurações que substituem elementos de configuração bloqueados lancem exceções em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="f0f4d-141">The .NET Framework provides a way to lock configuration file elements so that configurations that override locked configuration elements throw run-time exceptions.</span></span>  
  
 <span data-ttu-id="f0f4d-142">Um elemento de configuração pode ser bloqueado especificando o `lockItem` atributo para um nó no arquivo de configuração, por exemplo, para bloquear o nó CalculatorServiceBehavior no arquivo de configuração para que os serviços de calculadora em arquivos de configuração aninhados não possam alterar o comportamento, a configuração a seguir pode ser usada.</span><span class="sxs-lookup"><span data-stu-id="f0f4d-142">A configuration element can be locked by specifying the `lockItem` attribute for a node in the configuration file, for example, to lock the CalculatorServiceBehavior node in the configuration file so that calculator services in nested configuration files cannot change the behavior, the following configuration can be used.</span></span>  
  
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
  
 <span data-ttu-id="f0f4d-143">O bloqueio de elementos de configuração pode ser mais específico.</span><span class="sxs-lookup"><span data-stu-id="f0f4d-143">Locking of configuration elements can be more specific.</span></span> <span data-ttu-id="f0f4d-144">Uma lista de elementos pode ser especificada como o valor para `lockElements` para bloquear um conjunto de elementos dentro de uma coleção de subelementos.</span><span class="sxs-lookup"><span data-stu-id="f0f4d-144">A list of elements can be specified as the value to the `lockElements` to lock a set of elements within a collection of sub-elements.</span></span> <span data-ttu-id="f0f4d-145">Uma lista de atributos pode ser especificada como o valor para `lockAttributes` para bloquear um conjunto de atributos dentro de um elemento.</span><span class="sxs-lookup"><span data-stu-id="f0f4d-145">A list of attributes can be specified as the value to the `lockAttributes` to lock a set of attributes within an element.</span></span> <span data-ttu-id="f0f4d-146">Uma coleção inteira de elementos ou atributos pode ser bloqueada, exceto por uma lista especificada, especificando os `lockAllElementsExcept` `lockAllAttributesExcept` atributos ou em um nó.</span><span class="sxs-lookup"><span data-stu-id="f0f4d-146">An entire collection of elements or attributes can be locked except for a specified list by specifying the `lockAllElementsExcept` or `lockAllAttributesExcept` attributes on a node.</span></span>  
  
## <a name="pii-logging-configuration"></a><span data-ttu-id="f0f4d-147">Configuração de log de PII</span><span class="sxs-lookup"><span data-stu-id="f0f4d-147">PII Logging Configuration</span></span>  
 <span data-ttu-id="f0f4d-148">O registro em log de PII é controlado por duas opções: uma configuração em todo o computador foi encontrada em Machine.config que permite que um administrador de computador permita ou negue o registro em log de PII e uma configuração de aplicativo que permite que um administrador de aplicativo Alterne o registro de PII para cada fonte em um arquivo Web.config ou App.config.</span><span class="sxs-lookup"><span data-stu-id="f0f4d-148">Logging of PII is controlled by two switches: a computer-wide setting found in Machine.config that allows a computer administrator to permit or deny logging of PII and an application setting that allows an application administrator to toggle logging of PII for each source in a Web.config or App.config file.</span></span>  
  
 <span data-ttu-id="f0f4d-149">A configuração em todo o computador é controlada pela configuração `enableLoggingKnownPii` de `true` ou `false` , no `machineSettings` elemento no Machine.config. Por exemplo, o seguinte permite que os aplicativos ativem o registro em log de PII.</span><span class="sxs-lookup"><span data-stu-id="f0f4d-149">The computer-wide setting is controlled by setting `enableLoggingKnownPii` to `true` or `false`, in the `machineSettings` element in Machine.config. For example, the following allows applications to turn on logging of PII.</span></span>  
  
```xml  
<configuration>  
    <system.serviceModel>  
        <machineSettings enableLoggingKnownPii="true" />  
    </system.serviceModel>  
</configuration>  
```  
  
> [!NOTE]
> <span data-ttu-id="f0f4d-150">O arquivo de Machine.config tem um local padrão:%WINDIR%\Microsoft.NET\Framework\v2.0.50727\CONFIG.</span><span class="sxs-lookup"><span data-stu-id="f0f4d-150">The Machine.config file has a default location: %WINDIR%\Microsoft.NET\Framework\v2.0.50727\CONFIG.</span></span>  
  
 <span data-ttu-id="f0f4d-151">Se o `enableLoggingKnownPii` atributo não estiver presente no Machine.config, o registro em log de PII não será permitido.</span><span class="sxs-lookup"><span data-stu-id="f0f4d-151">If the `enableLoggingKnownPii` attribute is not present in Machine.config, logging of PII is not allowed.</span></span>  
  
 <span data-ttu-id="f0f4d-152">Habilitar o log de PII para um aplicativo é feito definindo o `logKnownPii` atributo do elemento de origem como `true` ou `false` no arquivo de Web.config ou App.config.</span><span class="sxs-lookup"><span data-stu-id="f0f4d-152">Enabling logging of PII for an application is done by setting the `logKnownPii` attribute of the source element to `true` or `false` in the Web.config or App.config file.</span></span> <span data-ttu-id="f0f4d-153">Por exemplo, o seguinte habilita o registro em log de PII para log de mensagens e log de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="f0f4d-153">For example, the following enables logging of PII for both message logging and trace logging.</span></span>  
  
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
  
 <span data-ttu-id="f0f4d-154">Se o `logKnownPii` atributo não for especificado, PII não será registrado.</span><span class="sxs-lookup"><span data-stu-id="f0f4d-154">If the `logKnownPii` attribute is not specified, then PII is not logged.</span></span>  
  
 <span data-ttu-id="f0f4d-155">PII só será registrado se ambos `enableLoggingKnownPii` for definido como `true` e `logKnownPii` for definido como `true` .</span><span class="sxs-lookup"><span data-stu-id="f0f4d-155">PII is only logged if both `enableLoggingKnownPii` is set to `true`, and `logKnownPii` is set to `true`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f0f4d-156">System. Diagnostics ignora todos os atributos de todas as fontes, exceto o primeiro listado no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="f0f4d-156">System.Diagnostics ignores all attributes on all sources except the first one listed in the configuration file.</span></span> <span data-ttu-id="f0f4d-157">Adicionar o `logKnownPii` atributo à segunda fonte no arquivo de configuração não tem nenhum efeito.</span><span class="sxs-lookup"><span data-stu-id="f0f4d-157">Adding the `logKnownPii` attribute to the second source in the configuration file has no effect.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="f0f4d-158">Para executar este exemplo envolve a modificação manual de Machine.config. Deve-se ter cuidado ao modificar Machine.config como valores incorretos ou a sintaxe pode impedir a execução de todos os aplicativos .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f0f4d-158">To run this sample involves manual modification of Machine.config. Care should be taken when modifying Machine.config as incorrect values or syntax may prevent all .NET Framework applications from running.</span></span>  
  
 <span data-ttu-id="f0f4d-159">Também é possível criptografar os elementos do arquivo de configuração usando DPAPI e RSA.</span><span class="sxs-lookup"><span data-stu-id="f0f4d-159">It is also possible to encrypt configuration file elements using DPAPI and RSA.</span></span> <span data-ttu-id="f0f4d-160">Para obter mais informações, consulte os seguintes links:</span><span class="sxs-lookup"><span data-stu-id="f0f4d-160">For more information, see the following links:</span></span>  
  
- <span data-ttu-id="f0f4d-161">[Criando aplicativos ASP.NET seguros: autenticação, autorização e comunicação segura](/previous-versions/msp-n-p/ff649248(v=pandp.10))</span><span class="sxs-lookup"><span data-stu-id="f0f4d-161">[Building Secure ASP.NET Applications: Authentication, Authorization, and Secure Communication](/previous-versions/msp-n-p/ff649248(v=pandp.10))</span></span>  
  
- <span data-ttu-id="f0f4d-162">[Como: criptografar seções de configuração no ASP.NET 2,0 usando RSA](/previous-versions/msp-n-p/ff650304(v=pandp.10))</span><span class="sxs-lookup"><span data-stu-id="f0f4d-162">[How To: Encrypt Configuration Sections in ASP.NET 2.0 Using RSA](/previous-versions/msp-n-p/ff650304(v=pandp.10))</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="f0f4d-163">Para configurar, compilar e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="f0f4d-163">To set up, build and run the sample</span></span>  
  
1. <span data-ttu-id="f0f4d-164">Verifique se você executou o [procedimento de configuração única para os exemplos de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f0f4d-164">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="f0f4d-165">Edite Machine.config para definir o `enableLoggingKnownPii` atributo como `true` , adicionando os nós pai, se necessário.</span><span class="sxs-lookup"><span data-stu-id="f0f4d-165">Edit Machine.config to set the `enableLoggingKnownPii` attribute to `true`, adding the parent nodes if necessary.</span></span>  
  
3. <span data-ttu-id="f0f4d-166">Para criar a edição C# ou Visual Basic .NET da solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f0f4d-166">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="f0f4d-167">Para executar o exemplo em uma configuração de computador único ou entre computadores, siga as instruções em [executando os exemplos de Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f0f4d-167">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
#### <a name="to-clean-up-the-sample"></a><span data-ttu-id="f0f4d-168">Para limpar o exemplo</span><span class="sxs-lookup"><span data-stu-id="f0f4d-168">To clean up the sample</span></span>  
  
1. <span data-ttu-id="f0f4d-169">Edite Machine.config para definir o `enableLoggingKnownPii` atributo como `false` .</span><span class="sxs-lookup"><span data-stu-id="f0f4d-169">Edit Machine.config to set the `enableLoggingKnownPii` attribute to `false`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0f4d-170">Confira também</span><span class="sxs-lookup"><span data-stu-id="f0f4d-170">See also</span></span>

- <span data-ttu-id="f0f4d-171">[AppFabric que monitora Exemplos](/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="f0f4d-171">[AppFabric Monitoring Samples](/previous-versions/appfabric/ff383407(v=azure.10))</span></span>
