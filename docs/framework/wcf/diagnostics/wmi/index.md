---
title: Usando Windows Management Instrumentation para diagnóstico
ms.date: 03/30/2017
ms.assetid: fe48738d-e31b-454d-b5ec-24c85c6bf79a
ms.openlocfilehash: 0c803e3988f7a63980d991190db87c263c992b80
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185682"
---
# <a name="using-windows-management-instrumentation-for-diagnostics"></a><span data-ttu-id="abf1e-102">Usando Windows Management Instrumentation para diagnóstico</span><span class="sxs-lookup"><span data-stu-id="abf1e-102">Using Windows Management Instrumentation for Diagnostics</span></span>
<span data-ttu-id="abf1e-103">A Windows Communication Foundation (WCF) expõe os dados de inspeção de um serviço em tempo de execução através de um provedor WCF Windows Management Instrumentation (WMI).</span><span class="sxs-lookup"><span data-stu-id="abf1e-103">Windows Communication Foundation (WCF) exposes inspection data of a service at runtime through a WCF Windows Management Instrumentation (WMI) provider.</span></span>  
  
## <a name="enabling-wmi"></a><span data-ttu-id="abf1e-104">Habilitando o WMI</span><span class="sxs-lookup"><span data-stu-id="abf1e-104">Enabling WMI</span></span>  
 <span data-ttu-id="abf1e-105">O WMI é a implementação da Microsoft do padrão WBEM (Web-Based Enterprise Management, gerenciamento de empresas baseado na Web).</span><span class="sxs-lookup"><span data-stu-id="abf1e-105">WMI is Microsoft's implementation of the Web-Based Enterprise Management (WBEM) standard.</span></span> <span data-ttu-id="abf1e-106">Para obter mais informações sobre o WMI SDK, consulte [A Instrumentação de Gerenciamento do Windows](/windows/desktop/WmiSdk/wmi-start-page).</span><span class="sxs-lookup"><span data-stu-id="abf1e-106">For more information about the WMI SDK, see [Windows Management Instrumentation](/windows/desktop/WmiSdk/wmi-start-page).</span></span> <span data-ttu-id="abf1e-107">O WBEM é um padrão do setor para como as aplicações expõem a instrumentação de gerenciamento a ferramentas de gestão externa.</span><span class="sxs-lookup"><span data-stu-id="abf1e-107">WBEM is an industry standard for how applications expose management instrumentation to external management tools.</span></span>  
  
 <span data-ttu-id="abf1e-108">Um provedor WMI é um componente que expõe a instrumentação em tempo de execução através de uma interface compatível com WBEM.</span><span class="sxs-lookup"><span data-stu-id="abf1e-108">A WMI provider is a component that exposes instrumentation at runtime through a WBEM-compatible interface.</span></span> <span data-ttu-id="abf1e-109">Consiste em um conjunto de objetos WMI que têm pares de atributos/valor.</span><span class="sxs-lookup"><span data-stu-id="abf1e-109">It consists of a set of WMI objects that have attribute/value pairs.</span></span> <span data-ttu-id="abf1e-110">Pares podem ser de vários tipos simples.</span><span class="sxs-lookup"><span data-stu-id="abf1e-110">Pairs can be of a number of simple types.</span></span> <span data-ttu-id="abf1e-111">As ferramentas de gerenciamento podem se conectar aos serviços através da interface em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="abf1e-111">Management tools can connect to the services through the interface at runtime.</span></span> <span data-ttu-id="abf1e-112">O WCF expõe atributos de serviços como endereços, vinculações, comportamentos e ouvintes.</span><span class="sxs-lookup"><span data-stu-id="abf1e-112">WCF exposes attributes of services such as addresses, bindings, behaviors, and listeners.</span></span>  
  
 <span data-ttu-id="abf1e-113">O provedor WMI incorporado pode ser ativado no arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="abf1e-113">The built-in WMI provider can be activated in the configuration file of the application.</span></span> <span data-ttu-id="abf1e-114">Isso é feito `wmiProviderEnabled` através do atributo do [ \<>de diagnóstico](../../../configure-apps/file-schema/wcf/diagnostics.md) na seção [ \<system.serviceModel>,](../../../configure-apps/file-schema/wcf/system-servicemodel.md) conforme mostrado na configuração da amostra a seguir.</span><span class="sxs-lookup"><span data-stu-id="abf1e-114">This is done through the `wmiProviderEnabled` attribute of the [\<diagnostics>](../../../configure-apps/file-schema/wcf/diagnostics.md) in the [\<system.serviceModel>](../../../configure-apps/file-schema/wcf/system-servicemodel.md) section, as shown in the following sample configuration.</span></span>  
  
```xml  
<system.serviceModel>  
    …  
    <diagnostics wmiProviderEnabled="true" />  
    …  
</system.serviceModel>  
```  
  
 <span data-ttu-id="abf1e-115">Esta entrada de configuração expõe uma interface WMI.</span><span class="sxs-lookup"><span data-stu-id="abf1e-115">This configuration entry exposes a WMI interface.</span></span> <span data-ttu-id="abf1e-116">Os aplicativos de gerenciamento agora podem se conectar através desta interface e acessar a instrumentação de gerenciamento do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="abf1e-116">Management applications can now connect through this interface and access the management instrumentation of the application.</span></span>  
  
## <a name="accessing-wmi-data"></a><span data-ttu-id="abf1e-117">Acessando dados WMI</span><span class="sxs-lookup"><span data-stu-id="abf1e-117">Accessing WMI Data</span></span>  
 <span data-ttu-id="abf1e-118">Os dados WMI podem ser acessados de muitas maneiras diferentes.</span><span class="sxs-lookup"><span data-stu-id="abf1e-118">WMI data can be accessed in many different ways.</span></span> <span data-ttu-id="abf1e-119">A Microsoft fornece APIs WMI para scripts, aplicativos Visual Basic, aplicativos C++ e o .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="abf1e-119">Microsoft provides WMI APIs for scripts, Visual Basic applications, C++ applications, and the .NET Framework.</span></span> <span data-ttu-id="abf1e-120">Para obter mais informações, consulte [Usando WMI](/windows/win32/wmisdk/using-wmi).</span><span class="sxs-lookup"><span data-stu-id="abf1e-120">For more information, see [Using WMI](/windows/win32/wmisdk/using-wmi).</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="abf1e-121">Se você usar os métodos fornecidos pelo .NET Framework para acessar programáticamente os dados do WMI, você deve estar ciente de que tais métodos podem lançar exceções quando a conexão for estabelecida.</span><span class="sxs-lookup"><span data-stu-id="abf1e-121">If you use the .NET Framework provided methods to programmatically access WMI data, you should be aware that such methods may throw exceptions when the connection is established.</span></span> <span data-ttu-id="abf1e-122">A conexão não é estabelecida <xref:System.Management.ManagementObject> durante a construção da instância, mas na primeira solicitação envolvendo troca de dados real.</span><span class="sxs-lookup"><span data-stu-id="abf1e-122">The connection is not established during the construction of the <xref:System.Management.ManagementObject> instance, but on the first request involving actual data exchange.</span></span> <span data-ttu-id="abf1e-123">Portanto, você deve `try..catch` usar um bloco para capturar as possíveis exceções.</span><span class="sxs-lookup"><span data-stu-id="abf1e-123">Therefore, you should use a `try..catch` block to catch the possible exceptions.</span></span>  
  
 <span data-ttu-id="abf1e-124">Você pode alterar o nível de registro de rastreamento `System.ServiceModel` e mensagens, bem como opções de registro de mensagens para a fonte de rastreamento no WMI.</span><span class="sxs-lookup"><span data-stu-id="abf1e-124">You can change the trace and message logging level, as well as message logging options for the `System.ServiceModel` trace source in WMI.</span></span> <span data-ttu-id="abf1e-125">Isso pode ser feito acessando a instância [AppDomainInfo,](appdomaininfo.md) `LogMessagesAtTransportLevel`que `LogMalformedMessages`expõe `TraceLevel`essas propriedades booleanas: `LogMessagesAtServiceLevel`, , e .</span><span class="sxs-lookup"><span data-stu-id="abf1e-125">This can be done by accessing the [AppDomainInfo](appdomaininfo.md) instance, which exposes these Boolean properties: `LogMessagesAtServiceLevel`, `LogMessagesAtTransportLevel`, `LogMalformedMessages`, and `TraceLevel`.</span></span> <span data-ttu-id="abf1e-126">Portanto, se você configurar um ouvinte de rastreamento para registro `false` de mensagens, mas `true` definir essas opções na configuração, você poderá alterá-las posteriormente para quando o aplicativo estiver sendo executado.</span><span class="sxs-lookup"><span data-stu-id="abf1e-126">Therefore, if you configure a trace listener for message logging, but set these options to `false` in configuration, you can later change them to `true` when the application is running.</span></span> <span data-ttu-id="abf1e-127">Isso permitirá efetivamente o registro de mensagens em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="abf1e-127">This will effectively enable message logging at runtime.</span></span> <span data-ttu-id="abf1e-128">Da mesma forma, se você habilitar o registro de mensagens em seu arquivo de configuração, você poderá desativá-lo em tempo de execução usando o WMI.</span><span class="sxs-lookup"><span data-stu-id="abf1e-128">Similarly, if you enable message logging in your configuration file, you can disable it at runtime using WMI.</span></span>  
  
 <span data-ttu-id="abf1e-129">Você deve estar ciente de que se nenhum registro `System.ServiceModel` de mensagem rastrear ouvintes para registro de mensagens ou nenhum rastreamento de rastreamento for especificado no arquivo de configuração, nenhuma de suas alterações será tomada em vigor, mesmo que as alterações sejam aceitas pelo WMI.</span><span class="sxs-lookup"><span data-stu-id="abf1e-129">You should be aware that if no message logging trace listeners for message logging, or no `System.ServiceModel` trace listeners for tracing are specified in the configuration file, none of your changes are taken into effect, even though the changes are accepted by WMI.</span></span> <span data-ttu-id="abf1e-130">Para obter mais informações sobre a configuração adequada dos respectivos ouvintes, consulte [Configurando o registro de mensagens](../configuring-message-logging.md) e [configurando o rastreamento](../tracing/configuring-tracing.md).</span><span class="sxs-lookup"><span data-stu-id="abf1e-130">For more information on properly setting up the respective listeners, see [Configuring Message Logging](../configuring-message-logging.md) and [Configuring Tracing](../tracing/configuring-tracing.md).</span></span> <span data-ttu-id="abf1e-131">O nível de rastreamento de todas as outras fontes de rastreamento especificadas pela configuração é eficaz quando o aplicativo é iniciado e não pode ser alterado.</span><span class="sxs-lookup"><span data-stu-id="abf1e-131">The trace level of all other trace sources specified by configuration is effective when the application starts, and cannot be changed.</span></span>  
  
 <span data-ttu-id="abf1e-132">O WCF `GetOperationCounterInstanceName` expõe um método de scripting.</span><span class="sxs-lookup"><span data-stu-id="abf1e-132">WCF exposes a `GetOperationCounterInstanceName` method for scripting.</span></span> <span data-ttu-id="abf1e-133">Este método retorna um nome de instância de contador de desempenho se você fornecê-lo com um nome de operação.</span><span class="sxs-lookup"><span data-stu-id="abf1e-133">This method returns a performance counter instance name if you provide it with an operation name.</span></span> <span data-ttu-id="abf1e-134">No entanto, ele não valida sua entrada.</span><span class="sxs-lookup"><span data-stu-id="abf1e-134">However, it does not validate your input.</span></span> <span data-ttu-id="abf1e-135">Portanto, se você fornecer um nome de operação incorreto, um nome de contador incorreto será devolvido.</span><span class="sxs-lookup"><span data-stu-id="abf1e-135">Therefore, if you provide an incorrect operation name, an incorrect counter name is returned.</span></span>  
  
 <span data-ttu-id="abf1e-136">A `OutgoingChannel` propriedade `Service` da instância não conta canais abertos por um serviço para se conectar a outro serviço, `Service` caso o cliente WCF ao serviço de destino não seja criado dentro do método.</span><span class="sxs-lookup"><span data-stu-id="abf1e-136">The `OutgoingChannel` property of the `Service` instance does not count channels opened by a service to connect to another service, if the WCF client to the destination service is not created within the `Service` method.</span></span>  
  
 <span data-ttu-id="abf1e-137">**Cuidado** O WMI só <xref:System.TimeSpan> suporta um valor de até 3 pontos decimais.</span><span class="sxs-lookup"><span data-stu-id="abf1e-137">**Caution** WMI only supports a <xref:System.TimeSpan> value up to 3 decimal points.</span></span> <span data-ttu-id="abf1e-138">Por exemplo, se o seu serviço <xref:System.TimeSpan.MaxValue>define uma de suas propriedades para , seu valor é truncado após 3 pontos decimais quando visualizado através de WMI.</span><span class="sxs-lookup"><span data-stu-id="abf1e-138">For example, if your service sets one of its properties to <xref:System.TimeSpan.MaxValue>, its value is truncated after 3 decimal points when viewed through WMI.</span></span>  
  
## <a name="security"></a><span data-ttu-id="abf1e-139">Segurança</span><span class="sxs-lookup"><span data-stu-id="abf1e-139">Security</span></span>  
 <span data-ttu-id="abf1e-140">Como o provedor WCF WMI permite a descoberta de serviços em um ambiente, você deve ter extrema cautela para conceder acesso a ele.</span><span class="sxs-lookup"><span data-stu-id="abf1e-140">Because the WCF WMI provider allows the discovery of services in an environment, you should exercise extreme caution for granting access to it.</span></span> <span data-ttu-id="abf1e-141">Se você relaxar o acesso padrão somente ao administrador, poderá permitir que partes menos confiáveis acessem dados confidenciais em seu ambiente.</span><span class="sxs-lookup"><span data-stu-id="abf1e-141">If you relax the default administrator-only access, you may allow less-trusted parties access to sensitive data in your environment.</span></span> <span data-ttu-id="abf1e-142">Especificamente, se você afrouxar permissões em acesso remoto WMI, ataques de inundação podem ocorrer.</span><span class="sxs-lookup"><span data-stu-id="abf1e-142">Specifically, if you loosen permissions on remote WMI access, flooding attacks can occur.</span></span> <span data-ttu-id="abf1e-143">Se um processo for inundado por solicitações excessivas de WMI, seu desempenho pode ser degradado.</span><span class="sxs-lookup"><span data-stu-id="abf1e-143">If a process is flooded by excessive WMI requests, its performance can be degraded.</span></span>  
  
 <span data-ttu-id="abf1e-144">Além disso, se você relaxar as permissões de acesso para o arquivo MOF, as partes menos confiáveis podem manipular o comportamento do WMI e alterar os objetos que estão carregados no esquema WMI.</span><span class="sxs-lookup"><span data-stu-id="abf1e-144">In addition, if you relax access permissions for the MOF file, less-trusted parties can manipulate the behavior of WMI and alter the objects that are loaded in the WMI schema.</span></span> <span data-ttu-id="abf1e-145">Por exemplo, os campos podem ser removidos de forma que os dados críticos sejam ocultados do administrador ou que campos que não preencham ou causem exceções sejam adicionados ao arquivo.</span><span class="sxs-lookup"><span data-stu-id="abf1e-145">For example, fields can be removed such that critical data is concealed from the administrator or that fields that do not populate or cause exceptions are added to the file.</span></span>  
  
 <span data-ttu-id="abf1e-146">Por padrão, o provedor WCF WMI concede permissão de "executar método", "gravação de provedor" e "habilitar conta" para administrador e "habilitar conta" para ASP.NET, Serviço Local e Serviço de Rede.</span><span class="sxs-lookup"><span data-stu-id="abf1e-146">By default, the WCF WMI provider grants "execute method", "provider write", and "enable account" permission for Administrator, and "enable account" permission for ASP.NET, Local Service and Network Service.</span></span> <span data-ttu-id="abf1e-147">Em particular, em plataformas não-Windows Vista, a conta ASP.NET leu acesso ao namespace WMI ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="abf1e-147">In particular, on non-Windows Vista platforms, the ASP.NET account has read access to the WMI ServiceModel namespace.</span></span> <span data-ttu-id="abf1e-148">Se você não quiser conceder esses privilégios a um determinado grupo de usuários, você deve desativar o provedor WMI (ele está desativado por padrão) ou desativar o acesso para o grupo de usuários específico.</span><span class="sxs-lookup"><span data-stu-id="abf1e-148">If you do not want to grant these privileges to a particular user group, you should either deactivate the WMI provider (it is disabled by default), or disable access for the specific user group.</span></span>  
  
 <span data-ttu-id="abf1e-149">Além disso, quando você tenta ativar o WMI através da configuração, o WMI pode não ser habilitado devido ao privilégio insuficiente do usuário.</span><span class="sxs-lookup"><span data-stu-id="abf1e-149">In addition, when you attempt to enable WMI through configuration, WMI may not be enabled due to insufficient user privilege.</span></span> <span data-ttu-id="abf1e-150">No entanto, nenhum evento é escrito no registro do evento para registrar essa falha.</span><span class="sxs-lookup"><span data-stu-id="abf1e-150">However, no event is written to the event log to record this failure.</span></span>  
  
 <span data-ttu-id="abf1e-151">Para modificar os níveis de privilégio do usuário, use as seguintes etapas.</span><span class="sxs-lookup"><span data-stu-id="abf1e-151">To modify user privilege levels, use the following steps.</span></span>  
  
1. <span data-ttu-id="abf1e-152">Clique em Iniciar e, em seguida, Executar e digitar **compmgmt.msc**.</span><span class="sxs-lookup"><span data-stu-id="abf1e-152">Click Start and then Run and type **compmgmt.msc**.</span></span>  
  
2. <span data-ttu-id="abf1e-153">Clique com o botão direito do mouse **em Serviços e controles de aplicativo/WMI** para selecionar **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="abf1e-153">Right-click **Services and Application/WMI Controls** to select **Properties**.</span></span>  
  
3. <span data-ttu-id="abf1e-154">Selecione a guia **de segurança** e navegue até o **namespace Root/ServiceModel.**</span><span class="sxs-lookup"><span data-stu-id="abf1e-154">Select the **Security** Tab, and navigate to the **Root/ServiceModel** namespace.</span></span> <span data-ttu-id="abf1e-155">Clique no botão **Segurança.**</span><span class="sxs-lookup"><span data-stu-id="abf1e-155">Click the **Security** button.</span></span>  
  
4. <span data-ttu-id="abf1e-156">Selecione o grupo ou usuário específico que deseja controlar o acesso e use a caixa de seleção **Permitir** ou **Negar** para configurar permissões.</span><span class="sxs-lookup"><span data-stu-id="abf1e-156">Select the specific group or user that you want to control access and use the **Allow** or **Deny** checkbox to configure permissions.</span></span>  
  
## <a name="granting-wcf-wmi-registration-permissions-to-additional-users"></a><span data-ttu-id="abf1e-157">Concessão de Permissões de Registro WCF WMI para usuários adicionais</span><span class="sxs-lookup"><span data-stu-id="abf1e-157">Granting WCF WMI Registration Permissions to Additional Users</span></span>  
 <span data-ttu-id="abf1e-158">O WCF expõe os dados de gerenciamento ao WMI.</span><span class="sxs-lookup"><span data-stu-id="abf1e-158">WCF exposes management data to WMI.</span></span> <span data-ttu-id="abf1e-159">Ele faz isso hospedando um provedor WMI em processo, às vezes chamado de "provedor dissociado".</span><span class="sxs-lookup"><span data-stu-id="abf1e-159">It does so by hosting an in-process WMI provider, sometimes called a "decoupled provider".</span></span> <span data-ttu-id="abf1e-160">Para que os dados de gerenciamento sejam expostos, a conta que registra este provedor deve ter as permissões apropriadas.</span><span class="sxs-lookup"><span data-stu-id="abf1e-160">For the management data to be exposed, the account that registers this provider must have the appropriate permissions.</span></span> <span data-ttu-id="abf1e-161">No Windows, apenas um pequeno conjunto de contas privilegiadas pode registrar provedores dissociados por padrão.</span><span class="sxs-lookup"><span data-stu-id="abf1e-161">In Windows, only a small set of privileged accounts can register decoupled providers by default.</span></span> <span data-ttu-id="abf1e-162">Isso é um problema porque os usuários geralmente querem expor dados WMI de um serviço WCF em execução em uma conta que não está no conjunto padrão.</span><span class="sxs-lookup"><span data-stu-id="abf1e-162">This is a problem because users commonly want to expose WMI data from a WCF service running under an account that is not in the default set.</span></span>  
  
 <span data-ttu-id="abf1e-163">Para fornecer esse acesso, um administrador deve conceder as seguintes permissões à conta adicional na seguinte ordem:</span><span class="sxs-lookup"><span data-stu-id="abf1e-163">To provide this access, an administrator must grant the following permissions to the additional account in the following order:</span></span>  
  
1. <span data-ttu-id="abf1e-164">Permissão para acesso ao WCF WMI Namespace.</span><span class="sxs-lookup"><span data-stu-id="abf1e-164">Permission to access to the WCF WMI Namespace.</span></span>  
  
2. <span data-ttu-id="abf1e-165">Permissão para registrar o Provedor WMI Desacoplado WCF.</span><span class="sxs-lookup"><span data-stu-id="abf1e-165">Permission to register the WCF Decoupled WMI Provider.</span></span>  
  
#### <a name="to-grant-wmi-namespace-access-permission"></a><span data-ttu-id="abf1e-166">Para conceder permissão de acesso ao namespace do WMI</span><span class="sxs-lookup"><span data-stu-id="abf1e-166">To grant WMI namespace access permission</span></span>  
  
1. <span data-ttu-id="abf1e-167">Execute o script do PowerShell a seguir.</span><span class="sxs-lookup"><span data-stu-id="abf1e-167">Run the following PowerShell script.</span></span>  
  
    ```powershell  
    write-host ""  
    write-host "Granting Access to root/servicemodel WMI namespace to built in users group"  
    write-host ""  
  
    # Create the binary representation of the permissions to grant in SDDL  
    $newPermissions = "O:BAG:BAD:P(A;CI;CCDCLCSWRPWPRCWD;;;BA)(A;CI;CC;;;NS)(A;CI;CC;;;LS)(A;CI;CC;;;BU)"  
    $converter = new-object system.management.ManagementClass Win32_SecurityDescriptorHelper  
    $binarySD = $converter.SDDLToBinarySD($newPermissions)  
    $convertedPermissions = ,$binarySD.BinarySD  
  
    # Get the object used to set the permissions  
    $security = gwmi -namespace root/servicemodel -class __SystemSecurity  
  
    # Get and output the current settings  
    $binarySD = @($null)  
    $result = $security.PsBase.InvokeMethod("GetSD",$binarySD)  
  
    $outsddl = $converter.BinarySDToSDDL($binarySD[0])  
    write-host "Previous ACL: "$outsddl.SDDL  
  
    # Change the Access Control List (ACL) using SDDL  
    $result = $security.PsBase.InvokeMethod("SetSD",$convertedPermissions)
  
    # Get and output the current settings  
    $binarySD = @($null)  
    $result = $security.PsBase.InvokeMethod("GetSD",$binarySD)  
  
    $outsddl = $converter.BinarySDToSDDL($binarySD[0])  
    write-host "New ACL:      "$outsddl.SDDL  
    write-host ""  
    ```  
  
     <span data-ttu-id="abf1e-168">Este script PowerShell usa o SDDL (Security Dscriptor Definition Language, linguagem de definição de descritor de segurança) para conceder ao grupo de usuários incorporados acesso ao espaço de nome WMI "root/servicemodel".</span><span class="sxs-lookup"><span data-stu-id="abf1e-168">This PowerShell script uses Security Descriptor Definition Language (SDDL) to grant the Built-In Users group access to the "root/servicemodel" WMI namespace.</span></span> <span data-ttu-id="abf1e-169">Ele especifica as seguintes ACLs:</span><span class="sxs-lookup"><span data-stu-id="abf1e-169">It specifies the following ACLs:</span></span>  
  
    - <span data-ttu-id="abf1e-170">Administrador embutido (BA) - Já tinha acesso.</span><span class="sxs-lookup"><span data-stu-id="abf1e-170">Built-In Administrator (BA) - Already Had Access.</span></span>  
  
    - <span data-ttu-id="abf1e-171">Serviço de Rede (NS) - Já tinha acesso.</span><span class="sxs-lookup"><span data-stu-id="abf1e-171">Network Service (NS) - Already Had Access.</span></span>  
  
    - <span data-ttu-id="abf1e-172">Sistema Local (LS) - Já tinha acesso.</span><span class="sxs-lookup"><span data-stu-id="abf1e-172">Local System (LS) - Already Had Access.</span></span>  
  
    - <span data-ttu-id="abf1e-173">Usuários Incorporados - O grupo para conceder acesso.</span><span class="sxs-lookup"><span data-stu-id="abf1e-173">Built-In Users - The group to grant access to.</span></span>  
  
#### <a name="to-grant-provider-registration-access"></a><span data-ttu-id="abf1e-174">Para conceder acesso ao registro do provedor</span><span class="sxs-lookup"><span data-stu-id="abf1e-174">To grant provider registration access</span></span>  
  
1. <span data-ttu-id="abf1e-175">Execute o script do PowerShell a seguir.</span><span class="sxs-lookup"><span data-stu-id="abf1e-175">Run the following PowerShell script.</span></span>  
  
    ```powershell  
    write-host ""  
    write-host "Granting WCF provider registration access to built in users group"  
    write-host ""  
    # Set security on ServiceModel provider  
    $provider = get-WmiObject -namespace "root\servicemodel" __Win32Provider  
  
    write-host "Previous ACL: "$provider.SecurityDescriptor  
    $result = $provider.SecurityDescriptor = "O:BUG:BUD:(A;;0x1;;;BA)(A;;0x1;;;NS)(A;;0x1;;;LS)(A;;0x1;;;BU)"  
  
    # Commit the changes and display it to the console  
    $result = $provider.Put()  
    write-host "New ACL:      "$provider.SecurityDescriptor  
    write-host ""  
    ```  
  
### <a name="granting-access-to-arbitrary-users-or-groups"></a><span data-ttu-id="abf1e-176">Concessão de acesso a usuários ou grupos arbitrários</span><span class="sxs-lookup"><span data-stu-id="abf1e-176">Granting Access to Arbitrary Users or Groups</span></span>  
 <span data-ttu-id="abf1e-177">O exemplo nesta seção concede privilégios de registro do Provedor WMI a todos os usuários locais.</span><span class="sxs-lookup"><span data-stu-id="abf1e-177">The example in this section grants WMI Provider registration privileges to all local users.</span></span> <span data-ttu-id="abf1e-178">Se você quiser conceder acesso a um usuário ou grupo que não esteja incorporado, então você deve obter o SID (Security Identifier, identificador de segurança) desse usuário ou grupo.</span><span class="sxs-lookup"><span data-stu-id="abf1e-178">If you want to grant access to a user or group that is not built in, then you must obtain that user or group’s Security Identifier (SID).</span></span> <span data-ttu-id="abf1e-179">Não há uma maneira simples de obter o SID para um usuário arbitrário.</span><span class="sxs-lookup"><span data-stu-id="abf1e-179">There is no simple way to get the SID for an arbitrary user.</span></span> <span data-ttu-id="abf1e-180">Um método é fazer logon como usuário desejado e, em seguida, emitir o seguinte comando shell.</span><span class="sxs-lookup"><span data-stu-id="abf1e-180">One method is to log on as the desired user and then issue the following shell command.</span></span>  
  
```console
Whoami /user  
```  
  
 <span data-ttu-id="abf1e-181">Isso fornece o SID do usuário atual, mas este método não pode ser usado para obter o SID em qualquer usuário arbitrário.</span><span class="sxs-lookup"><span data-stu-id="abf1e-181">This provides the SID of the current user, but this method cannot be used to get the SID on any arbitrary user.</span></span> <span data-ttu-id="abf1e-182">Outro método para obter o SID é usar a ferramenta [getsid.exe](/windows/win32/wmisdk/using-wmi) das Ferramentas de Kit de Recursos do Windows 2000 para tarefas administrativas.</span><span class="sxs-lookup"><span data-stu-id="abf1e-182">Another method to get the SID is to use the [getsid.exe](/windows/win32/wmisdk/using-wmi) tool from the Windows 2000 Resource Kit Tools for administrative tasks.</span></span> <span data-ttu-id="abf1e-183">Esta ferramenta compara o SID de dois usuários (local ou domínio), e como efeito colateral imprime os dois SIDs para a linha de comando.</span><span class="sxs-lookup"><span data-stu-id="abf1e-183">This tool compares the SID of two users (local or domain), and as a side effect prints the two SIDs to the command line.</span></span> <span data-ttu-id="abf1e-184">Para obter mais informações, consulte [SIDs bem conhecidos](https://support.microsoft.com/help/243330/well-known-security-identifiers-in-windows-operating-systems).</span><span class="sxs-lookup"><span data-stu-id="abf1e-184">For more information, see [Well Known SIDs](https://support.microsoft.com/help/243330/well-known-security-identifiers-in-windows-operating-systems).</span></span>  
  
## <a name="accessing-remote-wmi-object-instances"></a><span data-ttu-id="abf1e-185">Acessando instâncias remotas de objeto WMI</span><span class="sxs-lookup"><span data-stu-id="abf1e-185">Accessing Remote WMI Object Instances</span></span>  
 <span data-ttu-id="abf1e-186">Se você precisar acessar instâncias WCF WMI em uma máquina remota, você deve habilitar a privacidade do pacote nas ferramentas que você usa para acesso.</span><span class="sxs-lookup"><span data-stu-id="abf1e-186">If you need to access WCF WMI instances on a remote machine, you must enable packet privacy on the tools that you use for access.</span></span> <span data-ttu-id="abf1e-187">A seção a seguir descreve como alcançá-los usando o WMI CIM Studio, O Tester de Instrumentação de Gerenciamento do Windows, bem como o .NET SDK 2.0.</span><span class="sxs-lookup"><span data-stu-id="abf1e-187">The following section describes how to achieve these using the WMI CIM Studio, Windows Management Instrumentation Tester, as well as .NET SDK 2.0.</span></span>  
  
### <a name="wmi-cim-studio"></a><span data-ttu-id="abf1e-188">WMI CIM Studio</span><span class="sxs-lookup"><span data-stu-id="abf1e-188">WMI CIM Studio</span></span>  
 <span data-ttu-id="abf1e-189">Se você tiver instalado [ferramentas administrativas WMI,](https://go.microsoft.com/fwlink/?LinkId=95185)você pode usar o WMI CIM Studio para acessar instâncias WMI.</span><span class="sxs-lookup"><span data-stu-id="abf1e-189">If you have installed [WMI Administrative Tools](https://go.microsoft.com/fwlink/?LinkId=95185), you can use the WMI CIM Studio to access WMI instances.</span></span> <span data-ttu-id="abf1e-190">As ferramentas estão na seguinte pasta</span><span class="sxs-lookup"><span data-stu-id="abf1e-190">The tools are in the following folder</span></span>  
  
 <span data-ttu-id="abf1e-191">**%windir%\Arquivos do programa\WMI Ferramentas\\**</span><span class="sxs-lookup"><span data-stu-id="abf1e-191">**%windir%\Program Files\WMI Tools\\**</span></span>  
  
1. <span data-ttu-id="abf1e-192">No **Conecte-se ao namespace:** janela, digite **root\ServiceModel** e clique em **OK.**</span><span class="sxs-lookup"><span data-stu-id="abf1e-192">In the **Connect to namespace:** window, type **root\ServiceModel** and click **OK.**</span></span>  
  
2. <span data-ttu-id="abf1e-193">Na janela De login do **WMI CIM Studio,** clique no botão **Opções >>** para expandir a janela.</span><span class="sxs-lookup"><span data-stu-id="abf1e-193">In the **WMI CIM Studio Login** window, click the **Options >>** button to expand the window.</span></span> <span data-ttu-id="abf1e-194">Selecione **privacidade do pacote** para o nível de **autenticação**e clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="abf1e-194">Select **Packet privacy** for **Authentication level**, and click **OK**.</span></span>  
  
### <a name="windows-management-instrumentation-tester"></a><span data-ttu-id="abf1e-195">Testador de instrumentação de gerenciamento de Windows</span><span class="sxs-lookup"><span data-stu-id="abf1e-195">Windows Management Instrumentation Tester</span></span>  
 <span data-ttu-id="abf1e-196">Esta ferramenta é instalada pelo Windows.</span><span class="sxs-lookup"><span data-stu-id="abf1e-196">This tool is installed by Windows.</span></span> <span data-ttu-id="abf1e-197">Para executá-lo, inicie um console de comando digitando **cmd.exe** na caixa de diálogo **Iniciar/Executar** e clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="abf1e-197">To run it, launch a command console by typing **cmd.exe** in the **Start/Run** dialog box and click **OK**.</span></span> <span data-ttu-id="abf1e-198">Em seguida, digite **wbemtest.exe** na janela de comando.</span><span class="sxs-lookup"><span data-stu-id="abf1e-198">Then, type **wbemtest.exe** in the command window.</span></span> <span data-ttu-id="abf1e-199">A ferramenta Tester de Instrumentação de Gerenciamento do Windows é então lançada.</span><span class="sxs-lookup"><span data-stu-id="abf1e-199">The Windows Management Instrumentation Tester tool is then launched.</span></span>  
  
1. <span data-ttu-id="abf1e-200">Clique no botão **Conectar** no canto superior direito da janela.</span><span class="sxs-lookup"><span data-stu-id="abf1e-200">Click the **Connect** button on the top right corner of the window.</span></span>  
  
2. <span data-ttu-id="abf1e-201">Na nova janela, digite **root\ServiceModel** para o campo **Namespace** e selecione **Privacidade de pacotepara** **nível de autenticação**.</span><span class="sxs-lookup"><span data-stu-id="abf1e-201">In the new window, enter **root\ServiceModel** for the **Namespace** field, and select **Packet privacy** for **Authentication level**.</span></span> <span data-ttu-id="abf1e-202">Clique em **Conectar**.</span><span class="sxs-lookup"><span data-stu-id="abf1e-202">Click **Connect**.</span></span>  
  
### <a name="using-managed-code"></a><span data-ttu-id="abf1e-203">Usando código gerenciado</span><span class="sxs-lookup"><span data-stu-id="abf1e-203">Using Managed Code</span></span>  
 <span data-ttu-id="abf1e-204">Você também pode acessar instâncias remotas do WMI <xref:System.Management> programáticamente usando classes fornecidas pelo namespace.</span><span class="sxs-lookup"><span data-stu-id="abf1e-204">You can also access remote WMI instances programmatically by using classes provided by the <xref:System.Management> namespace.</span></span> <span data-ttu-id="abf1e-205">A amostra de código a seguir demonstra como fazer isso.</span><span class="sxs-lookup"><span data-stu-id="abf1e-205">The following code sample demonstrates how to do this.</span></span>  
  
```csharp
String wcfNamespace = $@"\\{this.serviceMachineName}\Root\ServiceModel");
  
ConnectionOptions connection = new ConnectionOptions();  
connection.Authentication = AuthenticationLevel.PacketPrivacy;  
ManagementScope scope = new ManagementScope(this.wcfNamespace, connection);  
```
