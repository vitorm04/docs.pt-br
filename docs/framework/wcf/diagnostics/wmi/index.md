---
title: Usando Windows Management Instrumentation para diagnóstico
ms.date: 03/30/2017
ms.assetid: fe48738d-e31b-454d-b5ec-24c85c6bf79a
ms.openlocfilehash: 0b67f06b9a99d7e9001c8415d0e94adef8436a3d
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855807"
---
# <a name="using-windows-management-instrumentation-for-diagnostics"></a><span data-ttu-id="286eb-102">Usando Windows Management Instrumentation para diagnóstico</span><span class="sxs-lookup"><span data-stu-id="286eb-102">Using Windows Management Instrumentation for Diagnostics</span></span>
<span data-ttu-id="286eb-103">Windows Communication Foundation (WCF) expõe os dados de inspeção de um serviço em tempo de execução por meio de um provedor de Instrumentação de Gerenciamento do Windows do WCF (WMI).</span><span class="sxs-lookup"><span data-stu-id="286eb-103">Windows Communication Foundation (WCF) exposes inspection data of a service at runtime through a WCF Windows Management Instrumentation (WMI) provider.</span></span>  
  
## <a name="enabling-wmi"></a><span data-ttu-id="286eb-104">Habilitando o WMI</span><span class="sxs-lookup"><span data-stu-id="286eb-104">Enabling WMI</span></span>  
 <span data-ttu-id="286eb-105">O WMI é a implementação do padrão Web-Based Enterprise Management (WBEM) da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="286eb-105">WMI is Microsoft's implementation of the Web-Based Enterprise Management (WBEM) standard.</span></span> <span data-ttu-id="286eb-106">Para obter mais informações sobre o SDK do WMI, consulte [Instrumentação de gerenciamento do Windows](/windows/desktop/WmiSdk/wmi-start-page).</span><span class="sxs-lookup"><span data-stu-id="286eb-106">For more information about the WMI SDK, see [Windows Management Instrumentation](/windows/desktop/WmiSdk/wmi-start-page).</span></span> <span data-ttu-id="286eb-107">O WBEM é um padrão do setor para a forma como os aplicativos expõem a instrumentação de gerenciamento para ferramentas de gerenciamento externas.</span><span class="sxs-lookup"><span data-stu-id="286eb-107">WBEM is an industry standard for how applications expose management instrumentation to external management tools.</span></span>  
  
 <span data-ttu-id="286eb-108">Um provedor WMI é um componente que expõe a instrumentação em tempo de execução por meio de uma interface compatível com o WBEM.</span><span class="sxs-lookup"><span data-stu-id="286eb-108">A WMI provider is a component that exposes instrumentation at runtime through a WBEM-compatible interface.</span></span> <span data-ttu-id="286eb-109">Ele consiste em um conjunto de objetos WMI que têm pares de atributo/valor.</span><span class="sxs-lookup"><span data-stu-id="286eb-109">It consists of a set of WMI objects that have attribute/value pairs.</span></span> <span data-ttu-id="286eb-110">Os pares podem ser de vários tipos simples.</span><span class="sxs-lookup"><span data-stu-id="286eb-110">Pairs can be of a number of simple types.</span></span> <span data-ttu-id="286eb-111">As ferramentas de gerenciamento podem se conectar aos serviços por meio da interface em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="286eb-111">Management tools can connect to the services through the interface at runtime.</span></span> <span data-ttu-id="286eb-112">O WCF expõe atributos de serviços como endereços, associações, comportamentos e ouvintes.</span><span class="sxs-lookup"><span data-stu-id="286eb-112">WCF exposes attributes of services such as addresses, bindings, behaviors, and listeners.</span></span>  
  
 <span data-ttu-id="286eb-113">O provedor WMI interno pode ser ativado no arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="286eb-113">The built-in WMI provider can be activated in the configuration file of the application.</span></span> <span data-ttu-id="286eb-114">Isso é feito por meio `wmiProviderEnabled` do atributo [ \<do > de diagnóstico](../../../configure-apps/file-schema/wcf/diagnostics.md) na [ \<seção System. ServiceModel >](../../../configure-apps/file-schema/wcf/system-servicemodel.md) , conforme mostrado na seguinte configuração de exemplo.</span><span class="sxs-lookup"><span data-stu-id="286eb-114">This is done through the `wmiProviderEnabled` attribute of the [\<diagnostics>](../../../configure-apps/file-schema/wcf/diagnostics.md) in the [\<system.serviceModel>](../../../configure-apps/file-schema/wcf/system-servicemodel.md) section, as shown in the following sample configuration.</span></span>  
  
```xml  
<system.serviceModel>  
    …  
    <diagnostics wmiProviderEnabled="true" />  
    …  
</system.serviceModel>  
```  
  
 <span data-ttu-id="286eb-115">Essa entrada de configuração expõe uma interface WMI.</span><span class="sxs-lookup"><span data-stu-id="286eb-115">This configuration entry exposes a WMI interface.</span></span> <span data-ttu-id="286eb-116">Os aplicativos de gerenciamento agora podem se conectar por meio dessa interface e acessar a instrumentação de gerenciamento do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="286eb-116">Management applications can now connect through this interface and access the management instrumentation of the application.</span></span>  
  
## <a name="accessing-wmi-data"></a><span data-ttu-id="286eb-117">Acessando dados do WMI</span><span class="sxs-lookup"><span data-stu-id="286eb-117">Accessing WMI Data</span></span>  
 <span data-ttu-id="286eb-118">Os dados do WMI podem ser acessados de várias maneiras diferentes.</span><span class="sxs-lookup"><span data-stu-id="286eb-118">WMI data can be accessed in many different ways.</span></span> <span data-ttu-id="286eb-119">A Microsoft fornece APIs WMI para scripts, Visual Basic aplicativos C++ , aplicativos e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="286eb-119">Microsoft provides WMI APIs for scripts, Visual Basic applications, C++ applications, and the .NET Framework.</span></span> <span data-ttu-id="286eb-120">Para obter mais informações, consulte [usando o WMI](https://go.microsoft.com/fwlink/?LinkId=95183).</span><span class="sxs-lookup"><span data-stu-id="286eb-120">For more information, see [Using WMI](https://go.microsoft.com/fwlink/?LinkId=95183).</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="286eb-121">Se você usar os métodos .NET Framework fornecidos para acessar os dados do WMI programaticamente, você deve estar ciente de que esses métodos podem gerar exceções quando a conexão é estabelecida.</span><span class="sxs-lookup"><span data-stu-id="286eb-121">If you use the .NET Framework provided methods to programmatically access WMI data, you should be aware that such methods may throw exceptions when the connection is established.</span></span> <span data-ttu-id="286eb-122">A conexão não é estabelecida durante a construção da <xref:System.Management.ManagementObject> instância, mas na primeira solicitação que envolve a troca de dados real.</span><span class="sxs-lookup"><span data-stu-id="286eb-122">The connection is not established during the construction of the <xref:System.Management.ManagementObject> instance, but on the first request involving actual data exchange.</span></span> <span data-ttu-id="286eb-123">Portanto, você deve usar um `try..catch` bloco para capturar as possíveis exceções.</span><span class="sxs-lookup"><span data-stu-id="286eb-123">Therefore, you should use a `try..catch` block to catch the possible exceptions.</span></span>  
  
 <span data-ttu-id="286eb-124">Você pode alterar o rastreamento e o nível de log de mensagens, bem como as opções de `System.ServiceModel` log de mensagens para a origem do rastreamento no WMI.</span><span class="sxs-lookup"><span data-stu-id="286eb-124">You can change the trace and message logging level, as well as message logging options for the `System.ServiceModel` trace source in WMI.</span></span> <span data-ttu-id="286eb-125">Isso pode ser feito acessando a instância [AppDomainInfo](appdomaininfo.md) , que expõe essas propriedades booleanas `LogMessagesAtServiceLevel`: `LogMessagesAtTransportLevel`, `LogMalformedMessages`, e `TraceLevel`.</span><span class="sxs-lookup"><span data-stu-id="286eb-125">This can be done by accessing the [AppDomainInfo](appdomaininfo.md) instance, which exposes these Boolean properties: `LogMessagesAtServiceLevel`, `LogMessagesAtTransportLevel`, `LogMalformedMessages`, and `TraceLevel`.</span></span> <span data-ttu-id="286eb-126">Portanto, se você configurar um ouvinte de rastreamento para o log de mensagens, mas `false` definir essas opções como em configuração, você poderá `true` alterá-las posteriormente para quando o aplicativo estiver em execução.</span><span class="sxs-lookup"><span data-stu-id="286eb-126">Therefore, if you configure a trace listener for message logging, but set these options to `false` in configuration, you can later change them to `true` when the application is running.</span></span> <span data-ttu-id="286eb-127">Isso habilitará efetivamente o registro em log de mensagens em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="286eb-127">This will effectively enable message logging at runtime.</span></span> <span data-ttu-id="286eb-128">Da mesma forma, se você habilitar o log de mensagens em seu arquivo de configuração, poderá desabilitá-lo em tempo de execução usando o WMI.</span><span class="sxs-lookup"><span data-stu-id="286eb-128">Similarly, if you enable message logging in your configuration file, you can disable it at runtime using WMI.</span></span>  
  
 <span data-ttu-id="286eb-129">Você deve estar ciente de que, se nenhum ouvinte de rastreamento de log de mensagens do `System.ServiceModel` log de mensagens ou nenhum ouvinte de rastreamento para rastreamento for especificado no arquivo de configuração, nenhuma das alterações será levada em vigor, mesmo que as alterações sejam aceitas pelo WMI.</span><span class="sxs-lookup"><span data-stu-id="286eb-129">You should be aware that if no message logging trace listeners for message logging, or no `System.ServiceModel` trace listeners for tracing are specified in the configuration file, none of your changes are taken into effect, even though the changes are accepted by WMI.</span></span> <span data-ttu-id="286eb-130">Para obter mais informações sobre como configurar corretamente os respectivos ouvintes, consulte [Configurando o log de mensagens](../configuring-message-logging.md) e [Configurando o rastreamento](../tracing/configuring-tracing.md).</span><span class="sxs-lookup"><span data-stu-id="286eb-130">For more information on properly setting up the respective listeners, see [Configuring Message Logging](../configuring-message-logging.md) and [Configuring Tracing](../tracing/configuring-tracing.md).</span></span> <span data-ttu-id="286eb-131">O nível de rastreamento de todas as outras origens de rastreamento especificadas pela configuração é efetivo quando o aplicativo é iniciado e não pode ser alterado.</span><span class="sxs-lookup"><span data-stu-id="286eb-131">The trace level of all other trace sources specified by configuration is effective when the application starts, and cannot be changed.</span></span>  
  
 <span data-ttu-id="286eb-132">O WCF expõe `GetOperationCounterInstanceName` um método para scripts.</span><span class="sxs-lookup"><span data-stu-id="286eb-132">WCF exposes a `GetOperationCounterInstanceName` method for scripting.</span></span> <span data-ttu-id="286eb-133">Esse método retornará um nome de instância do contador de desempenho se você fornecê-lo com um nome de operação.</span><span class="sxs-lookup"><span data-stu-id="286eb-133">This method returns a performance counter instance name if you provide it with an operation name.</span></span> <span data-ttu-id="286eb-134">No entanto, ele não valida sua entrada.</span><span class="sxs-lookup"><span data-stu-id="286eb-134">However, it does not validate your input.</span></span> <span data-ttu-id="286eb-135">Portanto, se você fornecer um nome de operação incorreto, um nome de contador incorreto será retornado.</span><span class="sxs-lookup"><span data-stu-id="286eb-135">Therefore, if you provide an incorrect operation name, an incorrect counter name is returned.</span></span>  
  
 <span data-ttu-id="286eb-136">A `OutgoingChannel` propriedade `Service` da instância não conta canais abertos por um serviço para se conectar a outro serviço, se o cliente WCF para o serviço de destino não for criado dentro do método. `Service`</span><span class="sxs-lookup"><span data-stu-id="286eb-136">The `OutgoingChannel` property of the `Service` instance does not count channels opened by a service to connect to another service, if the WCF client to the destination service is not created within the `Service` method.</span></span>  
  
 <span data-ttu-id="286eb-137">**Cuidado** O WMI só dá <xref:System.TimeSpan> suporte a um valor de até 3 pontos decimais.</span><span class="sxs-lookup"><span data-stu-id="286eb-137">**Caution** WMI only supports a <xref:System.TimeSpan> value up to 3 decimal points.</span></span> <span data-ttu-id="286eb-138">Por exemplo, se o serviço definir uma de suas propriedades como <xref:System.TimeSpan.MaxValue>, seu valor será truncado após 3 pontos decimais quando exibido por meio do WMI.</span><span class="sxs-lookup"><span data-stu-id="286eb-138">For example, if your service sets one of its properties to <xref:System.TimeSpan.MaxValue>, its value is truncated after 3 decimal points when viewed through WMI.</span></span>  
  
## <a name="security"></a><span data-ttu-id="286eb-139">Segurança</span><span class="sxs-lookup"><span data-stu-id="286eb-139">Security</span></span>  
 <span data-ttu-id="286eb-140">Como o provedor WMI WCF permite a descoberta de serviços em um ambiente, você deve ter muito cuidado para conceder acesso a ele.</span><span class="sxs-lookup"><span data-stu-id="286eb-140">Because the WCF WMI provider allows the discovery of services in an environment, you should exercise extreme caution for granting access to it.</span></span> <span data-ttu-id="286eb-141">Se você relaxar o acesso padrão somente ao administrador, poderá permitir que partes menos confiáveis acessem dados confidenciais em seu ambiente.</span><span class="sxs-lookup"><span data-stu-id="286eb-141">If you relax the default administrator-only access, you may allow less-trusted parties access to sensitive data in your environment.</span></span> <span data-ttu-id="286eb-142">Especificamente, se você afrouxar permissões no acesso WMI remoto, poderão ocorrer ataques de inundação.</span><span class="sxs-lookup"><span data-stu-id="286eb-142">Specifically, if you loosen permissions on remote WMI access, flooding attacks can occur.</span></span> <span data-ttu-id="286eb-143">Se um processo for inundado por solicitações excessivas do WMI, seu desempenho poderá ser degradado.</span><span class="sxs-lookup"><span data-stu-id="286eb-143">If a process is flooded by excessive WMI requests, its performance can be degraded.</span></span>  
  
 <span data-ttu-id="286eb-144">Além disso, se você relaxar as permissões de acesso para o arquivo MOF, partes menos confiáveis poderão manipular o comportamento do WMI e alterar os objetos que são carregados no esquema WMI.</span><span class="sxs-lookup"><span data-stu-id="286eb-144">In addition, if you relax access permissions for the MOF file, less-trusted parties can manipulate the behavior of WMI and alter the objects that are loaded in the WMI schema.</span></span> <span data-ttu-id="286eb-145">Por exemplo, os campos podem ser removidos de modo que os dados críticos sejam ocultados do administrador ou que os campos que não populem ou façam com que exceções sejam adicionadas ao arquivo.</span><span class="sxs-lookup"><span data-stu-id="286eb-145">For example, fields can be removed such that critical data is concealed from the administrator or that fields that do not populate or cause exceptions are added to the file.</span></span>  
  
 <span data-ttu-id="286eb-146">Por padrão, o provedor WCF WMI concede a permissão "executar método", "gravação do provedor" e "Habilitar conta" para o administrador e a permissão "Habilitar conta" para ASP.NET, serviço local e serviço de rede.</span><span class="sxs-lookup"><span data-stu-id="286eb-146">By default, the WCF WMI provider grants "execute method", "provider write", and "enable account" permission for Administrator, and "enable account" permission for ASP.NET, Local Service and Network Service.</span></span> <span data-ttu-id="286eb-147">Em particular, em não[!INCLUDE[wv](../../../../../includes/wv-md.md)] plataformas, a conta ASP.net tem acesso de leitura ao namespace WMI ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="286eb-147">In particular, on non-[!INCLUDE[wv](../../../../../includes/wv-md.md)] platforms, the ASP.NET account has read access to the WMI ServiceModel namespace.</span></span> <span data-ttu-id="286eb-148">Se você não quiser conceder esses privilégios a um grupo de usuários específico, desative o provedor WMI (ele está desabilitado por padrão) ou desabilite o acesso para o grupo de usuários específico.</span><span class="sxs-lookup"><span data-stu-id="286eb-148">If you do not want to grant these privileges to a particular user group, you should either deactivate the WMI provider (it is disabled by default), or disable access for the specific user group.</span></span>  
  
 <span data-ttu-id="286eb-149">Além disso, quando você tenta habilitar o WMI por meio da configuração, o WMI pode não ser habilitado devido a um privilégio de usuário insuficiente.</span><span class="sxs-lookup"><span data-stu-id="286eb-149">In addition, when you attempt to enable WMI through configuration, WMI may not be enabled due to insufficient user privilege.</span></span> <span data-ttu-id="286eb-150">No entanto, nenhum evento é gravado no log de eventos para registrar essa falha.</span><span class="sxs-lookup"><span data-stu-id="286eb-150">However, no event is written to the event log to record this failure.</span></span>  
  
 <span data-ttu-id="286eb-151">Para modificar os níveis de privilégio do usuário, use as etapas a seguir.</span><span class="sxs-lookup"><span data-stu-id="286eb-151">To modify user privilege levels, use the following steps.</span></span>  
  
1. <span data-ttu-id="286eb-152">Clique em Iniciar e em executar e digite **compmgmt. msc**.</span><span class="sxs-lookup"><span data-stu-id="286eb-152">Click Start and then Run and type **compmgmt.msc**.</span></span>  
  
2. <span data-ttu-id="286eb-153">Clique com o botão direito do mouse em **serviços e aplicativos/controles WMI** para selecionar **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="286eb-153">Right-click **Services and Application/WMI Controls** to select **Properties**.</span></span>  
  
3. <span data-ttu-id="286eb-154">Selecione a guia **segurança** e navegue até o namespace **raiz/ServiceModel** .</span><span class="sxs-lookup"><span data-stu-id="286eb-154">Select the **Security** Tab, and navigate to the **Root/ServiceModel** namespace.</span></span> <span data-ttu-id="286eb-155">Clique no botão **segurança** .</span><span class="sxs-lookup"><span data-stu-id="286eb-155">Click the **Security** button.</span></span>  
  
4. <span data-ttu-id="286eb-156">Selecione o grupo ou usuário específico para o qual você deseja controlar o acesso e use a caixa de seleção **permitir** ou **negar** para configurar permissões.</span><span class="sxs-lookup"><span data-stu-id="286eb-156">Select the specific group or user that you want to control access and use the **Allow** or **Deny** checkbox to configure permissions.</span></span>  
  
## <a name="granting-wcf-wmi-registration-permissions-to-additional-users"></a><span data-ttu-id="286eb-157">Concedendo permissões de registro do WCF WMI a usuários adicionais</span><span class="sxs-lookup"><span data-stu-id="286eb-157">Granting WCF WMI Registration Permissions to Additional Users</span></span>  
 <span data-ttu-id="286eb-158">O WCF expõe dados de gerenciamento para o WMI.</span><span class="sxs-lookup"><span data-stu-id="286eb-158">WCF exposes management data to WMI.</span></span> <span data-ttu-id="286eb-159">Ele faz isso hospedando um provedor WMI em processo, às vezes chamado de "provedor desacoplado".</span><span class="sxs-lookup"><span data-stu-id="286eb-159">It does so by hosting an in-process WMI provider, sometimes called a "decoupled provider".</span></span> <span data-ttu-id="286eb-160">Para que os dados de gerenciamento sejam expostos, a conta que registra esse provedor deve ter as permissões apropriadas.</span><span class="sxs-lookup"><span data-stu-id="286eb-160">For the management data to be exposed, the account that registers this provider must have the appropriate permissions.</span></span> <span data-ttu-id="286eb-161">No Windows, apenas um pequeno conjunto de contas com privilégios pode registrar provedores dissociados por padrão.</span><span class="sxs-lookup"><span data-stu-id="286eb-161">In Windows, only a small set of privileged accounts can register decoupled providers by default.</span></span> <span data-ttu-id="286eb-162">Isso é um problema porque os usuários normalmente desejam expor dados WMI de um serviço WCF em execução em uma conta que não está no conjunto padrão.</span><span class="sxs-lookup"><span data-stu-id="286eb-162">This is a problem because users commonly want to expose WMI data from a WCF service running under an account that is not in the default set.</span></span>  
  
 <span data-ttu-id="286eb-163">Para fornecer esse acesso, um administrador deve conceder as seguintes permissões para a conta adicional na seguinte ordem:</span><span class="sxs-lookup"><span data-stu-id="286eb-163">To provide this access, an administrator must grant the following permissions to the additional account in the following order:</span></span>  
  
1. <span data-ttu-id="286eb-164">Permissão para acessar o namespace WCF WMI.</span><span class="sxs-lookup"><span data-stu-id="286eb-164">Permission to access to the WCF WMI Namespace.</span></span>  
  
2. <span data-ttu-id="286eb-165">Permissão para registrar o provedor WMI dissociado do WCF.</span><span class="sxs-lookup"><span data-stu-id="286eb-165">Permission to register the WCF Decoupled WMI Provider.</span></span>  
  
#### <a name="to-grant-wmi-namespace-access-permission"></a><span data-ttu-id="286eb-166">Para conceder permissão de acesso do namespace WMI</span><span class="sxs-lookup"><span data-stu-id="286eb-166">To grant WMI namespace access permission</span></span>  
  
1. <span data-ttu-id="286eb-167">Execute o seguinte script do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="286eb-167">Run the following PowerShell script.</span></span>  
  
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
  
     <span data-ttu-id="286eb-168">Esse script do PowerShell usa SDDL (Security Descriptor Definition Language) para conceder ao grupo usuários internos acesso ao namespace WMI "root/ServiceModel".</span><span class="sxs-lookup"><span data-stu-id="286eb-168">This PowerShell script uses Security Descriptor Definition Language (SDDL) to grant the Built-In Users group access to the "root/servicemodel" WMI namespace.</span></span> <span data-ttu-id="286eb-169">Ele especifica as seguintes ACLs:</span><span class="sxs-lookup"><span data-stu-id="286eb-169">It specifies the following ACLs:</span></span>  
  
    - <span data-ttu-id="286eb-170">Administrador interno (BA)-já tinha acesso.</span><span class="sxs-lookup"><span data-stu-id="286eb-170">Built-In Administrator (BA) - Already Had Access.</span></span>  
  
    - <span data-ttu-id="286eb-171">Serviço de rede (NS)-já tinha acesso.</span><span class="sxs-lookup"><span data-stu-id="286eb-171">Network Service (NS) - Already Had Access.</span></span>  
  
    - <span data-ttu-id="286eb-172">Sistema local (LS)-já tinha acesso.</span><span class="sxs-lookup"><span data-stu-id="286eb-172">Local System (LS) - Already Had Access.</span></span>  
  
    - <span data-ttu-id="286eb-173">Usuários internos-o grupo ao qual conceder acesso.</span><span class="sxs-lookup"><span data-stu-id="286eb-173">Built-In Users - The group to grant access to.</span></span>  
  
#### <a name="to-grant-provider-registration-access"></a><span data-ttu-id="286eb-174">Para conceder acesso ao registro do provedor</span><span class="sxs-lookup"><span data-stu-id="286eb-174">To grant provider registration access</span></span>  
  
1. <span data-ttu-id="286eb-175">Execute o seguinte script do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="286eb-175">Run the following PowerShell script.</span></span>  
  
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
  
### <a name="granting-access-to-arbitrary-users-or-groups"></a><span data-ttu-id="286eb-176">Concedendo acesso a usuários ou grupos arbitrários</span><span class="sxs-lookup"><span data-stu-id="286eb-176">Granting Access to Arbitrary Users or Groups</span></span>  
 <span data-ttu-id="286eb-177">O exemplo nesta seção concede privilégios de registro do provedor WMI a todos os usuários locais.</span><span class="sxs-lookup"><span data-stu-id="286eb-177">The example in this section grants WMI Provider registration privileges to all local users.</span></span> <span data-ttu-id="286eb-178">Se você quiser conceder acesso a um usuário ou grupo que não esteja interno, deverá obter o SID (identificador de segurança) do usuário ou do grupo.</span><span class="sxs-lookup"><span data-stu-id="286eb-178">If you want to grant access to a user or group that is not built in, then you must obtain that user or group’s Security Identifier (SID).</span></span> <span data-ttu-id="286eb-179">Não há uma maneira simples de obter o SID para um usuário arbitrário.</span><span class="sxs-lookup"><span data-stu-id="286eb-179">There is no simple way to get the SID for an arbitrary user.</span></span> <span data-ttu-id="286eb-180">Um método é fazer logon como o usuário desejado e, em seguida, emitir o comando do Shell a seguir.</span><span class="sxs-lookup"><span data-stu-id="286eb-180">One method is to log on as the desired user and then issue the following shell command.</span></span>  
  
```console
Whoami /user  
```  
  
 <span data-ttu-id="286eb-181">Isso fornece o SID do usuário atual, mas esse método não pode ser usado para obter o SID em qualquer usuário arbitrário.</span><span class="sxs-lookup"><span data-stu-id="286eb-181">This provides the SID of the current user, but this method cannot be used to get the SID on any arbitrary user.</span></span> <span data-ttu-id="286eb-182">Outro método para obter o SID é usar a ferramenta [Getsid. exe](https://go.microsoft.com/fwlink/?LinkId=186467) das ferramentas do [Windows 2000 Resource Kit para tarefas administrativas](https://go.microsoft.com/fwlink/?LinkId=178660).</span><span class="sxs-lookup"><span data-stu-id="286eb-182">Another method to get the SID is to use the [getsid.exe](https://go.microsoft.com/fwlink/?LinkId=186467) tool from the [Windows 2000 Resource Kit Tools for administrative tasks](https://go.microsoft.com/fwlink/?LinkId=178660).</span></span> <span data-ttu-id="286eb-183">Essa ferramenta compara o SID de dois usuários (local ou domínio) e, como um efeito colateral, imprime os dois SIDs na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="286eb-183">This tool compares the SID of two users (local or domain), and as a side effect prints the two SIDs to the command line.</span></span> <span data-ttu-id="286eb-184">Para obter mais informações, consulte [SIDs bem conhecidos](https://go.microsoft.com/fwlink/?LinkId=186468).</span><span class="sxs-lookup"><span data-stu-id="286eb-184">For more information, see [Well Known SIDs](https://go.microsoft.com/fwlink/?LinkId=186468).</span></span>  
  
## <a name="accessing-remote-wmi-object-instances"></a><span data-ttu-id="286eb-185">Acessando instâncias de objeto WMI remoto</span><span class="sxs-lookup"><span data-stu-id="286eb-185">Accessing Remote WMI Object Instances</span></span>  
 <span data-ttu-id="286eb-186">Se você precisar acessar as instâncias WMI do WCF em um computador remoto, deverá habilitar a privacidade do pacote nas ferramentas que você usa para acesso.</span><span class="sxs-lookup"><span data-stu-id="286eb-186">If you need to access WCF WMI instances on a remote machine, you must enable packet privacy on the tools that you use for access.</span></span> <span data-ttu-id="286eb-187">A seção a seguir descreve como fazer isso usando o WMI CIM Studio, o Instrumentação de Gerenciamento do Windows Tester, bem como o SDK do .NET 2,0.</span><span class="sxs-lookup"><span data-stu-id="286eb-187">The following section describes how to achieve these using the WMI CIM Studio, Windows Management Instrumentation Tester, as well as .NET SDK 2.0.</span></span>  
  
### <a name="wmi-cim-studio"></a><span data-ttu-id="286eb-188">WMI CIM Studio</span><span class="sxs-lookup"><span data-stu-id="286eb-188">WMI CIM Studio</span></span>  
 <span data-ttu-id="286eb-189">Se você tiver instalado as [Ferramentas administrativas do WMI](https://go.microsoft.com/fwlink/?LinkId=95185), poderá usar o WMI CIM Studio para acessar as instâncias do WMI.</span><span class="sxs-lookup"><span data-stu-id="286eb-189">If you have installed [WMI Administrative Tools](https://go.microsoft.com/fwlink/?LinkId=95185), you can use the WMI CIM Studio to access WMI instances.</span></span> <span data-ttu-id="286eb-190">As ferramentas estão na seguinte pasta</span><span class="sxs-lookup"><span data-stu-id="286eb-190">The tools are in the following folder</span></span>  
  
 <span data-ttu-id="286eb-191">**Ferramentas do%windir%\Program Files\WMI\\**</span><span class="sxs-lookup"><span data-stu-id="286eb-191">**%windir%\Program Files\WMI Tools\\**</span></span>  
  
1. <span data-ttu-id="286eb-192">Na janela **conectar ao namespace:** , digite **root\ServiceModel** e clique em **OK.**</span><span class="sxs-lookup"><span data-stu-id="286eb-192">In the **Connect to namespace:** window, type **root\ServiceModel** and click **OK.**</span></span>  
  
2. <span data-ttu-id="286eb-193">Na janela de **logon do WMI CIM Studio** , clique no botão **Opções > >** para expandir a janela.</span><span class="sxs-lookup"><span data-stu-id="286eb-193">In the **WMI CIM Studio Login** window, click the **Options >>** button to expand the window.</span></span> <span data-ttu-id="286eb-194">Selecione **privacidade de pacote** para **nível de autenticação**e clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="286eb-194">Select **Packet privacy** for **Authentication level**, and click **OK**.</span></span>  
  
### <a name="windows-management-instrumentation-tester"></a><span data-ttu-id="286eb-195">Instrumentação de Gerenciamento do Windows testador</span><span class="sxs-lookup"><span data-stu-id="286eb-195">Windows Management Instrumentation Tester</span></span>  
 <span data-ttu-id="286eb-196">Essa ferramenta é instalada pelo Windows.</span><span class="sxs-lookup"><span data-stu-id="286eb-196">This tool is installed by Windows.</span></span> <span data-ttu-id="286eb-197">Para executá-lo, inicie um console de comando digitando **cmd. exe** na caixa de diálogo **Iniciar/Executar** e clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="286eb-197">To run it, launch a command console by typing **cmd.exe** in the **Start/Run** dialog box and click **OK**.</span></span> <span data-ttu-id="286eb-198">Em seguida, digite **WBEMTest. exe** na janela de comando.</span><span class="sxs-lookup"><span data-stu-id="286eb-198">Then, type **wbemtest.exe** in the command window.</span></span> <span data-ttu-id="286eb-199">Em seguida, a ferramenta de testador Instrumentação de Gerenciamento do Windows é iniciada.</span><span class="sxs-lookup"><span data-stu-id="286eb-199">The Windows Management Instrumentation Tester tool is then launched.</span></span>  
  
1. <span data-ttu-id="286eb-200">Clique no botão **conectar** no canto superior direito da janela.</span><span class="sxs-lookup"><span data-stu-id="286eb-200">Click the **Connect** button on the top right corner of the window.</span></span>  
  
2. <span data-ttu-id="286eb-201">Na nova janela, insira **root\ServiceModel** para o campo **namespace** e selecione privacidade de **pacote** para o **nível de autenticação**.</span><span class="sxs-lookup"><span data-stu-id="286eb-201">In the new window, enter **root\ServiceModel** for the **Namespace** field, and select **Packet privacy** for **Authentication level**.</span></span> <span data-ttu-id="286eb-202">Clique em **Conectar**.</span><span class="sxs-lookup"><span data-stu-id="286eb-202">Click **Connect**.</span></span>  
  
### <a name="using-managed-code"></a><span data-ttu-id="286eb-203">Usando código gerenciado</span><span class="sxs-lookup"><span data-stu-id="286eb-203">Using Managed Code</span></span>  
 <span data-ttu-id="286eb-204">Você também pode acessar instâncias WMI remotas programaticamente usando classes fornecidas <xref:System.Management> pelo namespace.</span><span class="sxs-lookup"><span data-stu-id="286eb-204">You can also access remote WMI instances programmatically by using classes provided by the <xref:System.Management> namespace.</span></span> <span data-ttu-id="286eb-205">O exemplo de código a seguir demonstra como fazer isso.</span><span class="sxs-lookup"><span data-stu-id="286eb-205">The following code sample demonstrates how to do this.</span></span>  
  
```csharp
String wcfNamespace = $@"\\{this.serviceMachineName}\Root\ServiceModel");
  
ConnectionOptions connection = new ConnectionOptions();  
connection.Authentication = AuthenticationLevel.PacketPrivacy;  
ManagementScope scope = new ManagementScope(this.wcfNamespace, connection);  
```
