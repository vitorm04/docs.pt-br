---
title: "Usando Windows Management Instrumentation para diagnóstico"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fe48738d-e31b-454d-b5ec-24c85c6bf79a
caps.latest.revision: "24"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7ad39675f0ecdda4706276e112d95ffbecd409ba
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="using-windows-management-instrumentation-for-diagnostics"></a><span data-ttu-id="17426-102">Usando Windows Management Instrumentation para diagnóstico</span><span class="sxs-lookup"><span data-stu-id="17426-102">Using Windows Management Instrumentation for Diagnostics</span></span>
[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]<span data-ttu-id="17426-103">expõe dados de inspeção de um serviço em tempo de execução por meio de um [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] provedor do Windows Management Instrumentation (WMI).</span><span class="sxs-lookup"><span data-stu-id="17426-103"> exposes inspection data of a service at runtime through a [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] Windows Management Instrumentation (WMI) provider.</span></span>  
  
## <a name="enabling-wmi"></a><span data-ttu-id="17426-104">Habilitando o WMI</span><span class="sxs-lookup"><span data-stu-id="17426-104">Enabling WMI</span></span>  
 <span data-ttu-id="17426-105">O WMI é a implementação da Microsoft a Web-Based Enterprise Management (WBEM) padrão.</span><span class="sxs-lookup"><span data-stu-id="17426-105">WMI is Microsoft's implementation of the Web-Based Enterprise Management (WBEM) standard.</span></span> [!INCLUDE[crabout](../../../../../includes/crabout-md.md)]<span data-ttu-id="17426-106">o SDK do WMI, consulte [Windows Management Instrumentation](https://msdn.microsoft.com/library/aa394582.aspx).</span><span class="sxs-lookup"><span data-stu-id="17426-106"> the WMI SDK, see [Windows Management Instrumentation](https://msdn.microsoft.com/library/aa394582.aspx).</span></span> <span data-ttu-id="17426-107">O WBEM é um padrão da indústria para como aplicativos expõem instrumentação de gerenciamento para as ferramentas de gerenciamento externo.</span><span class="sxs-lookup"><span data-stu-id="17426-107">WBEM is an industry standard for how applications expose management instrumentation to external management tools.</span></span>  
  
 <span data-ttu-id="17426-108">Um provedor WMI é um componente que expõe instrumentação em tempo de execução por meio de uma interface compatível com o WBEM.</span><span class="sxs-lookup"><span data-stu-id="17426-108">A WMI provider is a component that exposes instrumentation at runtime through a WBEM-compatible interface.</span></span> <span data-ttu-id="17426-109">Ele consiste em um conjunto de objetos WMI com pares de atributo/valor.</span><span class="sxs-lookup"><span data-stu-id="17426-109">It consists of a set of WMI objects that have attribute/value pairs.</span></span> <span data-ttu-id="17426-110">Pares de podem ser de um número de tipos simples.</span><span class="sxs-lookup"><span data-stu-id="17426-110">Pairs can be of a number of simple types.</span></span> <span data-ttu-id="17426-111">Ferramentas de gerenciamento podem se conectar aos serviços por meio da interface em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="17426-111">Management tools can connect to the services through the interface at runtime.</span></span> [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]<span data-ttu-id="17426-112">expõe os atributos de serviços, como endereços, associações, comportamentos e ouvintes.</span><span class="sxs-lookup"><span data-stu-id="17426-112"> exposes attributes of services such as addresses, bindings, behaviors, and listeners.</span></span>  
  
 <span data-ttu-id="17426-113">O provedor WMI interno pode ser ativado no arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="17426-113">The built-in WMI provider can be activated in the configuration file of the application.</span></span> <span data-ttu-id="17426-114">Isso é feito por meio de `wmiProviderEnabled` atributo do [ \<diagnóstico >](../../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md) no [ \<System. ServiceModel >](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) seção, conforme mostrado no exemplo a seguir configuração.</span><span class="sxs-lookup"><span data-stu-id="17426-114">This is done through the `wmiProviderEnabled` attribute of the [\<diagnostics>](../../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md) in the [\<system.serviceModel>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) section, as shown in the following sample configuration.</span></span>  
  
```xml  
<system.serviceModel>  
    …  
    <diagnostics wmiProviderEnabled="true" />  
    …  
</system.serviceModel>  
```  
  
 <span data-ttu-id="17426-115">Essa entrada de configuração expõe uma interface WMI.</span><span class="sxs-lookup"><span data-stu-id="17426-115">This configuration entry exposes a WMI interface.</span></span> <span data-ttu-id="17426-116">Aplicativos de gerenciamento podem se conectar por meio dessa interface e acessar a instrumentação de gerenciamento do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="17426-116">Management applications can now connect through this interface and access the management instrumentation of the application.</span></span>  
  
## <a name="accessing-wmi-data"></a><span data-ttu-id="17426-117">Acessando dados do WMI</span><span class="sxs-lookup"><span data-stu-id="17426-117">Accessing WMI Data</span></span>  
 <span data-ttu-id="17426-118">Dados do WMI podem ser acessados de várias maneiras diferentes.</span><span class="sxs-lookup"><span data-stu-id="17426-118">WMI data can be accessed in many different ways.</span></span> <span data-ttu-id="17426-119">A Microsoft fornece as APIs do WMI para scripts, [!INCLUDE[vbprvb](../../../../../includes/vbprvb-md.md)] aplicativos, aplicativos C++ e o [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="17426-119">Microsoft provides WMI APIs for scripts, [!INCLUDE[vbprvb](../../../../../includes/vbprvb-md.md)] applications, C++ applications, and the [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="17426-120">Para obter mais informações, consulte [WMI usando](http://go.microsoft.com/fwlink/?LinkId=95183).</span><span class="sxs-lookup"><span data-stu-id="17426-120">For more information, see [Using WMI](http://go.microsoft.com/fwlink/?LinkId=95183).</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="17426-121">Se você usar o .NET Framework ofereceu métodos para acessar programaticamente os dados do WMI, você deve estar ciente de que esses métodos podem lançar exceções quando a conexão é estabelecida.</span><span class="sxs-lookup"><span data-stu-id="17426-121">If you use the .NET Framework provided methods to programmatically access WMI data, you should be aware that such methods may throw exceptions when the connection is established.</span></span> <span data-ttu-id="17426-122">A conexão não for estabelecida durante a construção do <xref:System.Management.ManagementObject> instância, mas, na primeira solicitação que envolvem a troca de dados real.</span><span class="sxs-lookup"><span data-stu-id="17426-122">The connection is not established during the construction of the <xref:System.Management.ManagementObject> instance, but on the first request involving actual data exchange.</span></span> <span data-ttu-id="17426-123">Portanto, você deve usar um `try..catch` bloco catch possíveis exceções.</span><span class="sxs-lookup"><span data-stu-id="17426-123">Therefore, you should use a `try..catch` block to catch the possible exceptions.</span></span>  
  
 <span data-ttu-id="17426-124">Você pode alterar o rastreamento e nível de log de mensagem, bem como opções de log de mensagem para o `System.ServiceModel` origem de rastreamento no WMI.</span><span class="sxs-lookup"><span data-stu-id="17426-124">You can change the trace and message logging level, as well as message logging options for the `System.ServiceModel` trace source in WMI.</span></span> <span data-ttu-id="17426-125">Isso pode ser feito, acessando o [AppDomainInfo](../../../../../docs/framework/wcf/diagnostics/wmi/appdomaininfo.md) instância, que expõe essas propriedades Boolianas: `LogMessagesAtServiceLevel`, `LogMessagesAtTransportLevel`, `LogMalformedMessages`, e `TraceLevel`.</span><span class="sxs-lookup"><span data-stu-id="17426-125">This can be done by accessing the [AppDomainInfo](../../../../../docs/framework/wcf/diagnostics/wmi/appdomaininfo.md) instance, which exposes these Boolean properties: `LogMessagesAtServiceLevel`, `LogMessagesAtTransportLevel`, `LogMalformedMessages`, and `TraceLevel`.</span></span> <span data-ttu-id="17426-126">Portanto, se você configura um ouvinte de rastreamento para o log de mensagens, mas definir essas opções para `false` na configuração, você pode posteriormente alterá-los para `true` quando o aplicativo está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="17426-126">Therefore, if you configure a trace listener for message logging, but set these options to `false` in configuration, you can later change them to `true` when the application is running.</span></span> <span data-ttu-id="17426-127">Isso efetivamente habilitará o log de mensagem em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="17426-127">This will effectively enable message logging at runtime.</span></span> <span data-ttu-id="17426-128">Da mesma forma, se você habilitar o registro em log no arquivo de configuração de mensagem, você pode desabilitá-lo em tempo de execução usando a WMI.</span><span class="sxs-lookup"><span data-stu-id="17426-128">Similarly, if you enable message logging in your configuration file, you can disable it at runtime using WMI.</span></span>  
  
 <span data-ttu-id="17426-129">Você deve estar ciente de que, se nenhum registro de mensagem rastreamento ouvintes para mensagens em log ou não `System.ServiceModel` ouvintes de rastreamento para rastreamento são especificados no arquivo de configuração, nenhuma de suas alterações são levadas em vigor, mesmo que as alterações são aceitas pelo WMI.</span><span class="sxs-lookup"><span data-stu-id="17426-129">You should be aware that if no message logging trace listeners for message logging, or no `System.ServiceModel` trace listeners for tracing are specified in the configuration file, none of your changes are taken into effect, even though the changes are accepted by WMI.</span></span> <span data-ttu-id="17426-130">Para obter mais informações sobre como configurar corretamente os respectivos ouvintes, consulte [Configurando o log de mensagens](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md) e [Configurando rastreamento](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md).</span><span class="sxs-lookup"><span data-stu-id="17426-130">For more information on properly setting up the respective listeners, see [Configuring Message Logging](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md) and [Configuring Tracing](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md).</span></span> <span data-ttu-id="17426-131">O nível de rastreamento de todas as outras fontes de rastreamento especificado pela configuração é eficaz quando o aplicativo for iniciado e não pode ser alterado.</span><span class="sxs-lookup"><span data-stu-id="17426-131">The trace level of all other trace sources specified by configuration is effective when the application starts, and cannot be changed.</span></span>  
  
 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]<span data-ttu-id="17426-132">expõe um `GetOperationCounterInstanceName` método para script.</span><span class="sxs-lookup"><span data-stu-id="17426-132"> exposes a `GetOperationCounterInstanceName` method for scripting.</span></span> <span data-ttu-id="17426-133">Esse método retorna um nome de instância do contador de desempenho se fornecê-la com um nome de operação.</span><span class="sxs-lookup"><span data-stu-id="17426-133">This method returns a performance counter instance name if you provide it with an operation name.</span></span> <span data-ttu-id="17426-134">No entanto, ele não valida sua entrada.</span><span class="sxs-lookup"><span data-stu-id="17426-134">However, it does not validate your input.</span></span> <span data-ttu-id="17426-135">Portanto, se você fornecer um nome de operação incorreta, um nome de contador incorreto é retornado.</span><span class="sxs-lookup"><span data-stu-id="17426-135">Therefore, if you provide an incorrect operation name, an incorrect counter name is returned.</span></span>  
  
 <span data-ttu-id="17426-136">O `OutgoingChannel` propriedade do `Service` instância não conta canais abertos por um serviço para se conectar a outro serviço, se o [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] cliente para o serviço de destino não é criada dentro de `Service` método.</span><span class="sxs-lookup"><span data-stu-id="17426-136">The `OutgoingChannel` property of the `Service` instance does not count channels opened by a service to connect to another service, if the [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] client to the destination service is not created within the `Service` method.</span></span>  
  
 <span data-ttu-id="17426-137">**Cuidado** WMI oferece suporte apenas a um <xref:System.TimeSpan> valor até 3 decimais.</span><span class="sxs-lookup"><span data-stu-id="17426-137">**Caution** WMI only supports a <xref:System.TimeSpan> value up to 3 decimal points.</span></span> <span data-ttu-id="17426-138">Por exemplo, se o serviço define uma de suas propriedades para <xref:System.TimeSpan.MaxValue>, seu valor é truncado após 3 pontos decimais quando exibidas por meio do WMI.</span><span class="sxs-lookup"><span data-stu-id="17426-138">For example, if your service sets one of its properties to <xref:System.TimeSpan.MaxValue>, its value is truncated after 3 decimal points when viewed through WMI.</span></span>  
  
## <a name="security"></a><span data-ttu-id="17426-139">Segurança</span><span class="sxs-lookup"><span data-stu-id="17426-139">Security</span></span>  
 <span data-ttu-id="17426-140">Porque o [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] provedor WMI permite a descoberta de serviços em um ambiente, você deve ter extremo cuidado para conceder acesso a ele.</span><span class="sxs-lookup"><span data-stu-id="17426-140">Because the [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] WMI provider allows the discovery of services in an environment, you should exercise extreme caution for granting access to it.</span></span> <span data-ttu-id="17426-141">Se você relaxar o acesso de somente administrador padrão, você pode permitir o acesso de partes menos confiável para dados confidenciais em seu ambiente.</span><span class="sxs-lookup"><span data-stu-id="17426-141">If you relax the default administrator-only access, you may allow less-trusted parties access to sensitive data in your environment.</span></span> <span data-ttu-id="17426-142">Especificamente, se você solte permissões de acesso WMI remoto, ataques de inundação podem ocorrer.</span><span class="sxs-lookup"><span data-stu-id="17426-142">Specifically, if you loosen permissions on remote WMI access, flooding attacks can occur.</span></span> <span data-ttu-id="17426-143">Se um processo é a inundação de solicitações excessivas do WMI, o desempenho pode ser degradado.</span><span class="sxs-lookup"><span data-stu-id="17426-143">If a process is flooded by excessive WMI requests, its performance can be degraded.</span></span>  
  
 <span data-ttu-id="17426-144">Além disso, se você relaxar as permissões de acesso para o arquivo MOF, partes menos confiável podem manipular o comportamento do WMI e alterar os objetos que são carregados no esquema do WMI.</span><span class="sxs-lookup"><span data-stu-id="17426-144">In addition, if you relax access permissions for the MOF file, less-trusted parties can manipulate the behavior of WMI and alter the objects that are loaded in the WMI schema.</span></span> <span data-ttu-id="17426-145">Por exemplo, os campos podem ser removidos, de forma que dados críticos é oculto com o administrador ou campos que preencher ou causam exceções não são adicionados ao arquivo.</span><span class="sxs-lookup"><span data-stu-id="17426-145">For example, fields can be removed such that critical data is concealed from the administrator or that fields that do not populate or cause exceptions are added to the file.</span></span>  
  
 <span data-ttu-id="17426-146">Por padrão, o [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] provedor WMI concede "método execute", "gravação do provedor" e "Habilitar conta" permissão de administrador e a permissão "Habilitar conta" para ASP.NET, serviço Local e serviço de rede.</span><span class="sxs-lookup"><span data-stu-id="17426-146">By default, the [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] WMI provider grants "execute method", "provider write", and "enable account" permission for Administrator, and "enable account" permission for ASP.NET, Local Service and Network Service.</span></span> <span data-ttu-id="17426-147">Em particular, em não -[!INCLUDE[wv](../../../../../includes/wv-md.md)] plataformas, a conta do ASP.NET tem acesso de leitura ao namespace WMI ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="17426-147">In particular, on non-[!INCLUDE[wv](../../../../../includes/wv-md.md)] platforms, the ASP.NET account has read access to the WMI ServiceModel namespace.</span></span> <span data-ttu-id="17426-148">Se você não deseja conceder a esses privilégios a um grupo de usuários, você deve desativar o provedor WMI (desabilitado por padrão) ou desabilitar o acesso para o grupo de usuários específicos.</span><span class="sxs-lookup"><span data-stu-id="17426-148">If you do not want to grant these privileges to a particular user group, you should either deactivate the WMI provider (it is disabled by default), or disable access for the specific user group.</span></span>  
  
 <span data-ttu-id="17426-149">Além disso, quando você tentar habilitar a WMI por meio de configuração, o WMI não pode ser habilitada devido a privilégios insuficientes do usuário.</span><span class="sxs-lookup"><span data-stu-id="17426-149">In addition, when you attempt to enable WMI through configuration, WMI may not be enabled due to insufficient user privilege.</span></span> <span data-ttu-id="17426-150">No entanto, nenhum evento será gravado no log de eventos para registrar essa falha.</span><span class="sxs-lookup"><span data-stu-id="17426-150">However, no event is written to the event log to record this failure.</span></span>  
  
 <span data-ttu-id="17426-151">Para modificar os níveis de privilégio de usuário, use as etapas a seguir.</span><span class="sxs-lookup"><span data-stu-id="17426-151">To modify user privilege levels, use the following steps.</span></span>  
  
1.  <span data-ttu-id="17426-152">Clique em Iniciar e, em seguida, executar e digite **compmgmt.msc**.</span><span class="sxs-lookup"><span data-stu-id="17426-152">Click Start and then Run and type **compmgmt.msc**.</span></span>  
  
2.  <span data-ttu-id="17426-153">Clique com botão direito **Services e controles de aplicativo/WMI** para selecionar **propriedades**.</span><span class="sxs-lookup"><span data-stu-id="17426-153">Right-click **Services and Application/WMI Controls** to select **Properties**.</span></span>  
  
3.  <span data-ttu-id="17426-154">Selecione o **segurança** guia e navegue até o **raiz/ServiceModel** namespace.</span><span class="sxs-lookup"><span data-stu-id="17426-154">Select the **Security** Tab, and navigate to the **Root/ServiceModel** namespace.</span></span> <span data-ttu-id="17426-155">Clique o **segurança** botão.</span><span class="sxs-lookup"><span data-stu-id="17426-155">Click the **Security** button.</span></span>  
  
4.  <span data-ttu-id="17426-156">Selecione o grupo específico ou usuário que você deseja controlar o acesso e usar o **permitir** ou **Deny** caixa de seleção para configurar permissões.</span><span class="sxs-lookup"><span data-stu-id="17426-156">Select the specific group or user that you want to control access and use the **Allow** or **Deny** checkbox to configure permissions.</span></span>  
  
## <a name="granting-wcf-wmi-registration-permissions-to-additional-users"></a><span data-ttu-id="17426-157">Concedendo permissões de registro de WMI do WCF para usuários adicionais</span><span class="sxs-lookup"><span data-stu-id="17426-157">Granting WCF WMI Registration Permissions to Additional Users</span></span>  
 <span data-ttu-id="17426-158">WCF expõe dados de gerenciamento de WMI.</span><span class="sxs-lookup"><span data-stu-id="17426-158">WCF exposes management data to WMI.</span></span> <span data-ttu-id="17426-159">Isso é feito por um provedor WMI no processo, às vezes chamado de "provedor desacoplado" de hospedagem.</span><span class="sxs-lookup"><span data-stu-id="17426-159">It does so by hosting an in-process WMI provider, sometimes called a "decoupled provider".</span></span> <span data-ttu-id="17426-160">Para os dados de gerenciamento a ser exposto, a conta que registra o provedor deve ter as permissões apropriadas.</span><span class="sxs-lookup"><span data-stu-id="17426-160">For the management data to be exposed, the account that registers this provider must have the appropriate permissions.</span></span> <span data-ttu-id="17426-161">No Windows, um pequeno conjunto de contas privilegiadas pode registrar provedores separados por padrão.</span><span class="sxs-lookup"><span data-stu-id="17426-161">In Windows, only a small set of privileged accounts can register decoupled providers by default.</span></span> <span data-ttu-id="17426-162">Isso é um problema porque os usuários normalmente desejam expor dados de WMI de um serviço WCF executado em uma conta que não está no conjunto de padrão.</span><span class="sxs-lookup"><span data-stu-id="17426-162">This is a problem because users commonly want to expose WMI data from a WCF service running under an account that is not in the default set.</span></span>  
  
 <span data-ttu-id="17426-163">Para fornecer esse acesso, um administrador deve conceder as seguintes permissões para a conta adicional na seguinte ordem:</span><span class="sxs-lookup"><span data-stu-id="17426-163">To provide this access, an administrator must grant the following permissions to the additional account in the following order:</span></span>  
  
1.  <span data-ttu-id="17426-164">Permissão para acessar o Namespace de WMI do WCF.</span><span class="sxs-lookup"><span data-stu-id="17426-164">Permission to access to the WCF WMI Namespace.</span></span>  
  
2.  <span data-ttu-id="17426-165">Permissão para registrar o provedor de WMI desacoplado do WCF.</span><span class="sxs-lookup"><span data-stu-id="17426-165">Permission to register the WCF Decoupled WMI Provider.</span></span>  
  
#### <a name="to-grant-wmi-namespace-access-permission"></a><span data-ttu-id="17426-166">Para conceder permissão de acesso de namespace do WMI</span><span class="sxs-lookup"><span data-stu-id="17426-166">To grant WMI namespace access permission</span></span>  
  
1.  <span data-ttu-id="17426-167">Execute o seguinte script do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="17426-167">Run the following PowerShell script.</span></span>  
  
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
  
     <span data-ttu-id="17426-168">Este script do PowerShell usa SDDL Security Descriptor Definition Language () para conceder acesso a usuários internos para o namespace do WMI "raiz/servicemodel".</span><span class="sxs-lookup"><span data-stu-id="17426-168">This PowerShell script uses Security Descriptor Definition Language (SDDL) to grant the Built-In Users group access to the "root/servicemodel" WMI namespace.</span></span> <span data-ttu-id="17426-169">Especifica as seguintes ACLs:</span><span class="sxs-lookup"><span data-stu-id="17426-169">It specifies the following ACLs:</span></span>  
  
    -   <span data-ttu-id="17426-170">Administrador interno (BA) - já tinha acesso.</span><span class="sxs-lookup"><span data-stu-id="17426-170">Built-In Administrator (BA) - Already Had Access.</span></span>  
  
    -   <span data-ttu-id="17426-171">Serviço (NS) - de rede já tinha acesso.</span><span class="sxs-lookup"><span data-stu-id="17426-171">Network Service (NS) - Already Had Access.</span></span>  
  
    -   <span data-ttu-id="17426-172">Sistema local (LS) - já tinha acesso.</span><span class="sxs-lookup"><span data-stu-id="17426-172">Local System (LS) - Already Had Access.</span></span>  
  
    -   <span data-ttu-id="17426-173">Usuários internos - para conceder acesso para o grupo.</span><span class="sxs-lookup"><span data-stu-id="17426-173">Built-In Users - The group to grant access to.</span></span>  
  
#### <a name="to-grant-provider-registration-access"></a><span data-ttu-id="17426-174">Para conceder o provedor de registro de acesso</span><span class="sxs-lookup"><span data-stu-id="17426-174">To grant provider registration access</span></span>  
  
1.  <span data-ttu-id="17426-175">Execute o seguinte script do PowerShell.</span><span class="sxs-lookup"><span data-stu-id="17426-175">Run the following PowerShell script.</span></span>  
  
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
  
### <a name="granting-access-to-arbitrary-users-or-groups"></a><span data-ttu-id="17426-176">Concedendo acesso a outros usuários ou grupos</span><span class="sxs-lookup"><span data-stu-id="17426-176">Granting Access to Arbitrary Users or Groups</span></span>  
 <span data-ttu-id="17426-177">O exemplo nesta seção concede privilégios de registro do provedor WMI para todos os usuários locais.</span><span class="sxs-lookup"><span data-stu-id="17426-177">The example in this section grants WMI Provider registration privileges to all local users.</span></span> <span data-ttu-id="17426-178">Se você quiser conceder acesso a um usuário ou grupo que não é interno no, você deve obter esse usuário ou segurança SID do grupo de (identificador).</span><span class="sxs-lookup"><span data-stu-id="17426-178">If you want to grant access to a user or group that is not built in, then you must obtain that user or group’s Security Identifier (SID).</span></span> <span data-ttu-id="17426-179">Não há nenhuma maneira simple de obter o SID para um usuário arbitrário.</span><span class="sxs-lookup"><span data-stu-id="17426-179">There is no simple way to get the SID for an arbitrary user.</span></span> <span data-ttu-id="17426-180">É um método fazer logon como usuário desejado e, em seguida, execute o seguinte comando do shell.</span><span class="sxs-lookup"><span data-stu-id="17426-180">One method is to log on as the desired user and then issue the following shell command.</span></span>  
  
```  
Whoami /user  
```  
  
 <span data-ttu-id="17426-181">Isso fornece o SID do usuário atual, mas esse método não pode ser usado para obter o SID em qualquer usuário arbitrário.</span><span class="sxs-lookup"><span data-stu-id="17426-181">This provides the SID of the current user, but this method cannot be used to get the SID on any arbitrary user.</span></span> <span data-ttu-id="17426-182">Outro método para obter o SID é usar o [getsid.exe](http://go.microsoft.com/fwlink/?LinkId=186467) ferramenta do [ferramentas para tarefas administrativas do Windows 2000 Resource Kit](http://go.microsoft.com/fwlink/?LinkId=178660).</span><span class="sxs-lookup"><span data-stu-id="17426-182">Another method to get the SID is to use the [getsid.exe](http://go.microsoft.com/fwlink/?LinkId=186467) tool from the [Windows 2000 Resource Kit Tools for administrative tasks](http://go.microsoft.com/fwlink/?LinkId=178660).</span></span> <span data-ttu-id="17426-183">Essa ferramenta compara o SID de dois usuários (local ou domínio), e como efeito imprime os SIDs dois à linha de comando.</span><span class="sxs-lookup"><span data-stu-id="17426-183">This tool compares the SID of two users (local or domain), and as a side effect prints the two SIDs to the command line.</span></span> [!INCLUDE[crdefault](../../../../../includes/crdefault-md.md)]<span data-ttu-id="17426-184">[Conhecidos SIDs](http://go.microsoft.com/fwlink/?LinkId=186468).</span><span class="sxs-lookup"><span data-stu-id="17426-184"> [Well Known SIDs](http://go.microsoft.com/fwlink/?LinkId=186468).</span></span>  
  
## <a name="accessing-remote-wmi-object-instances"></a><span data-ttu-id="17426-185">Acessando instâncias de objeto WMI remoto</span><span class="sxs-lookup"><span data-stu-id="17426-185">Accessing Remote WMI Object Instances</span></span>  
 <span data-ttu-id="17426-186">Se você precisar acessar [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] instâncias de WMI em um computador remoto, você deve habilitar privacidade de pacotes de ferramentas que você usa para acessar.</span><span class="sxs-lookup"><span data-stu-id="17426-186">If you need to access [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] WMI instances on a remote machine, you must enable packet privacy on the tools that you use for access.</span></span> <span data-ttu-id="17426-187">A seção a seguir descreve como conseguir isto usando o WMI CIM Studio, o Testador de instrumentação de gerenciamento do Windows, bem como os .NET SDK 2.0.</span><span class="sxs-lookup"><span data-stu-id="17426-187">The following section describes how to achieve these using the WMI CIM Studio, Windows Management Instrumentation Tester, as well as .NET SDK 2.0.</span></span>  
  
### <a name="wmi-cim-studio"></a><span data-ttu-id="17426-188">CIM Studio do WMI</span><span class="sxs-lookup"><span data-stu-id="17426-188">WMI CIM Studio</span></span>  
 <span data-ttu-id="17426-189">Se você tiver instalado o [ferramentas administrativas do WMI](http://go.microsoft.com/fwlink/?LinkId=95185), você pode usar o CIM Studio do WMI para acessar instâncias WMI.</span><span class="sxs-lookup"><span data-stu-id="17426-189">If you have installed [WMI Administrative Tools](http://go.microsoft.com/fwlink/?LinkId=95185), you can use the WMI CIM Studio to access WMI instances.</span></span> <span data-ttu-id="17426-190">As ferramentas estão na seguinte pasta</span><span class="sxs-lookup"><span data-stu-id="17426-190">The tools are in the following folder</span></span>  
  
 <span data-ttu-id="17426-191">**Ferramentas de Files\WMI %Windir%\Program\\**</span><span class="sxs-lookup"><span data-stu-id="17426-191">**%windir%\Program Files\WMI Tools\\**</span></span>  
  
1.  <span data-ttu-id="17426-192">No **conectar ao namespace:** , digite **root\ServiceModel** e clique em **Okey.**</span><span class="sxs-lookup"><span data-stu-id="17426-192">In the **Connect to namespace:** window, type **root\ServiceModel** and click **OK.**</span></span>  
  
2.  <span data-ttu-id="17426-193">No **WMI CIM Studio logon** janela, clique no **opções >>** botão para expandir a janela.</span><span class="sxs-lookup"><span data-stu-id="17426-193">In the **WMI CIM Studio Login** window, click the **Options >>** button to expand the window.</span></span> <span data-ttu-id="17426-194">Selecione **privacidade do pacote** para **nível de autenticação**e clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="17426-194">Select **Packet privacy** for **Authentication level**, and click **OK**.</span></span>  
  
### <a name="windows-management-instrumentation-tester"></a><span data-ttu-id="17426-195">Testador de instrumentação de gerenciamento do Windows</span><span class="sxs-lookup"><span data-stu-id="17426-195">Windows Management Instrumentation Tester</span></span>  
 <span data-ttu-id="17426-196">Essa ferramenta é instalada pelo Windows.</span><span class="sxs-lookup"><span data-stu-id="17426-196">This tool is installed by Windows.</span></span> <span data-ttu-id="17426-197">Para executá-lo, inicie o console de comando digitando **cmd.exe** no **iniciar/executar** caixa de diálogo e clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="17426-197">To run it, launch a command console by typing **cmd.exe** in the **Start/Run** dialog box and click **OK**.</span></span> <span data-ttu-id="17426-198">Em seguida, digite **wbemtest.exe** na janela de comando.</span><span class="sxs-lookup"><span data-stu-id="17426-198">Then, type **wbemtest.exe** in the command window.</span></span> <span data-ttu-id="17426-199">A ferramenta Testador de instrumentação de gerenciamento do Windows, em seguida, é iniciada.</span><span class="sxs-lookup"><span data-stu-id="17426-199">The Windows Management Instrumentation Tester tool is then launched.</span></span>  
  
1.  <span data-ttu-id="17426-200">Clique o **conectar** botão no canto superior direito da janela.</span><span class="sxs-lookup"><span data-stu-id="17426-200">Click the **Connect** button on the top right corner of the window.</span></span>  
  
2.  <span data-ttu-id="17426-201">Na nova janela, digite **root\ServiceModel** para o **Namespace** campo e selecione **privacidade do pacote** para **nível de autenticação**.</span><span class="sxs-lookup"><span data-stu-id="17426-201">In the new window, enter **root\ServiceModel** for the **Namespace** field, and select **Packet privacy** for **Authentication level**.</span></span> <span data-ttu-id="17426-202">Clique em **Conectar**.</span><span class="sxs-lookup"><span data-stu-id="17426-202">Click **Connect**.</span></span>  
  
### <a name="using-managed-code"></a><span data-ttu-id="17426-203">Usando código gerenciado</span><span class="sxs-lookup"><span data-stu-id="17426-203">Using Managed Code</span></span>  
 <span data-ttu-id="17426-204">Você também pode acessar instâncias remotas do WMI programaticamente usando classes fornecidas pelo <xref:System.Management> namespace.</span><span class="sxs-lookup"><span data-stu-id="17426-204">You can also access remote WMI instances programmatically by using classes provided by the <xref:System.Management> namespace.</span></span> <span data-ttu-id="17426-205">O exemplo de código a seguir demonstra como fazer isso.</span><span class="sxs-lookup"><span data-stu-id="17426-205">The following code sample demonstrates how to do this.</span></span>  
  
```  
String wcfNamespace = String.Format(@"\\{0}\Root\ServiceModel",      
   this.serviceMachineName);  
  
ConnectionOptions connection = new ConnectionOptions();  
connection.Authentication = AuthenticationLevel.PacketPrivacy;  
ManagementScope scope = new ManagementScope(this.wcfNamespace, connection);  
```
