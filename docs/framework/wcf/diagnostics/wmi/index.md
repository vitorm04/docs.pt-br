---
title: Usando Windows Management Instrumentation para diagnóstico
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fe48738d-e31b-454d-b5ec-24c85c6bf79a
caps.latest.revision: 24
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e8fd88edd711513d1b143029d8088401c9945d13
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2018
---
# <a name="using-windows-management-instrumentation-for-diagnostics"></a>Usando Windows Management Instrumentation para diagnóstico
[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] expõe dados de inspeção de um serviço em tempo de execução por meio de um [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] provedor do Windows Management Instrumentation (WMI).  
  
## <a name="enabling-wmi"></a>Habilitando o WMI  
 O WMI é a implementação da Microsoft a Web-Based Enterprise Management (WBEM) padrão. [!INCLUDE[crabout](../../../../../includes/crabout-md.md)] o SDK do WMI, consulte [Windows Management Instrumentation](https://msdn.microsoft.com/library/aa394582.aspx). O WBEM é um padrão da indústria para como aplicativos expõem instrumentação de gerenciamento para as ferramentas de gerenciamento externo.  
  
 Um provedor WMI é um componente que expõe instrumentação em tempo de execução por meio de uma interface compatível com o WBEM. Ele consiste em um conjunto de objetos WMI com pares de atributo/valor. Pares de podem ser de um número de tipos simples. Ferramentas de gerenciamento podem se conectar aos serviços por meio da interface em tempo de execução. [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] expõe os atributos de serviços, como endereços, associações, comportamentos e ouvintes.  
  
 O provedor WMI interno pode ser ativado no arquivo de configuração do aplicativo. Isso é feito por meio de `wmiProviderEnabled` atributo do [ \<diagnóstico >](../../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md) no [ \<System. ServiceModel >](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) seção, conforme mostrado no exemplo a seguir configuração.  
  
```xml  
<system.serviceModel>  
    …  
    <diagnostics wmiProviderEnabled="true" />  
    …  
</system.serviceModel>  
```  
  
 Essa entrada de configuração expõe uma interface WMI. Aplicativos de gerenciamento podem se conectar por meio dessa interface e acessar a instrumentação de gerenciamento do aplicativo.  
  
## <a name="accessing-wmi-data"></a>Acessando dados do WMI  
 Dados do WMI podem ser acessados de várias maneiras diferentes. A Microsoft fornece as APIs do WMI para scripts, aplicativos do Visual Basic, aplicativos C++ e o [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)]. Para obter mais informações, consulte [WMI usando](http://go.microsoft.com/fwlink/?LinkId=95183).  
  
> [!CAUTION]
>  Se você usar o .NET Framework ofereceu métodos para acessar programaticamente os dados do WMI, você deve estar ciente de que esses métodos podem lançar exceções quando a conexão é estabelecida. A conexão não for estabelecida durante a construção do <xref:System.Management.ManagementObject> instância, mas, na primeira solicitação que envolvem a troca de dados real. Portanto, você deve usar um `try..catch` bloco catch possíveis exceções.  
  
 Você pode alterar o rastreamento e nível de log de mensagem, bem como opções de log de mensagem para o `System.ServiceModel` origem de rastreamento no WMI. Isso pode ser feito, acessando o [AppDomainInfo](../../../../../docs/framework/wcf/diagnostics/wmi/appdomaininfo.md) instância, que expõe essas propriedades Boolianas: `LogMessagesAtServiceLevel`, `LogMessagesAtTransportLevel`, `LogMalformedMessages`, e `TraceLevel`. Portanto, se você configura um ouvinte de rastreamento para o log de mensagens, mas definir essas opções para `false` na configuração, você pode posteriormente alterá-los para `true` quando o aplicativo está sendo executado. Isso efetivamente habilitará o log de mensagem em tempo de execução. Da mesma forma, se você habilitar o registro em log no arquivo de configuração de mensagem, você pode desabilitá-lo em tempo de execução usando a WMI.  
  
 Você deve estar ciente de que, se nenhum registro de mensagem rastreamento ouvintes para mensagens em log ou não `System.ServiceModel` ouvintes de rastreamento para rastreamento são especificados no arquivo de configuração, nenhuma de suas alterações são levadas em vigor, mesmo que as alterações são aceitas pelo WMI. Para obter mais informações sobre como configurar corretamente os respectivos ouvintes, consulte [Configurando o log de mensagens](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md) e [Configurando rastreamento](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md). O nível de rastreamento de todas as outras fontes de rastreamento especificado pela configuração é eficaz quando o aplicativo for iniciado e não pode ser alterado.  
  
 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] expõe um `GetOperationCounterInstanceName` método para script. Esse método retorna um nome de instância do contador de desempenho se fornecê-la com um nome de operação. No entanto, ele não valida sua entrada. Portanto, se você fornecer um nome de operação incorreta, um nome de contador incorreto é retornado.  
  
 O `OutgoingChannel` propriedade do `Service` instância não conta canais abertos por um serviço para se conectar a outro serviço, se o [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] cliente para o serviço de destino não é criada dentro de `Service` método.  
  
 **Cuidado** WMI oferece suporte apenas a um <xref:System.TimeSpan> valor até 3 decimais. Por exemplo, se o serviço define uma de suas propriedades para <xref:System.TimeSpan.MaxValue>, seu valor é truncado após 3 pontos decimais quando exibidas por meio do WMI.  
  
## <a name="security"></a>Segurança  
 Porque o [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] provedor WMI permite a descoberta de serviços em um ambiente, você deve ter extremo cuidado para conceder acesso a ele. Se você relaxar o acesso de somente administrador padrão, você pode permitir o acesso de partes menos confiável para dados confidenciais em seu ambiente. Especificamente, se você solte permissões de acesso WMI remoto, ataques de inundação podem ocorrer. Se um processo é a inundação de solicitações excessivas do WMI, o desempenho pode ser degradado.  
  
 Além disso, se você relaxar as permissões de acesso para o arquivo MOF, partes menos confiável podem manipular o comportamento do WMI e alterar os objetos que são carregados no esquema do WMI. Por exemplo, os campos podem ser removidos, de forma que dados críticos é oculto com o administrador ou campos que preencher ou causam exceções não são adicionados ao arquivo.  
  
 Por padrão, o [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] provedor WMI concede "método execute", "gravação do provedor" e "Habilitar conta" permissão de administrador e a permissão "Habilitar conta" para ASP.NET, serviço Local e serviço de rede. Em particular, em não -[!INCLUDE[wv](../../../../../includes/wv-md.md)] plataformas, a conta do ASP.NET tem acesso de leitura ao namespace WMI ServiceModel. Se você não deseja conceder a esses privilégios a um grupo de usuários, você deve desativar o provedor WMI (desabilitado por padrão) ou desabilitar o acesso para o grupo de usuários específicos.  
  
 Além disso, quando você tentar habilitar a WMI por meio de configuração, o WMI não pode ser habilitada devido a privilégios insuficientes do usuário. No entanto, nenhum evento será gravado no log de eventos para registrar essa falha.  
  
 Para modificar os níveis de privilégio de usuário, use as etapas a seguir.  
  
1.  Clique em Iniciar e, em seguida, executar e digite **compmgmt.msc**.  
  
2.  Clique com botão direito **Services e controles de aplicativo/WMI** para selecionar **propriedades**.  
  
3.  Selecione o **segurança** guia e navegue até o **raiz/ServiceModel** namespace. Clique o **segurança** botão.  
  
4.  Selecione o grupo específico ou usuário que você deseja controlar o acesso e usar o **permitir** ou **Deny** caixa de seleção para configurar permissões.  
  
## <a name="granting-wcf-wmi-registration-permissions-to-additional-users"></a>Concedendo permissões de registro de WMI do WCF para usuários adicionais  
 WCF expõe dados de gerenciamento de WMI. Isso é feito por um provedor WMI no processo, às vezes chamado de "provedor desacoplado" de hospedagem. Para os dados de gerenciamento a ser exposto, a conta que registra o provedor deve ter as permissões apropriadas. No Windows, um pequeno conjunto de contas privilegiadas pode registrar provedores separados por padrão. Isso é um problema porque os usuários normalmente desejam expor dados de WMI de um serviço WCF executado em uma conta que não está no conjunto de padrão.  
  
 Para fornecer esse acesso, um administrador deve conceder as seguintes permissões para a conta adicional na seguinte ordem:  
  
1.  Permissão para acessar o Namespace de WMI do WCF.  
  
2.  Permissão para registrar o provedor de WMI desacoplado do WCF.  
  
#### <a name="to-grant-wmi-namespace-access-permission"></a>Para conceder permissão de acesso de namespace do WMI  
  
1.  Execute o seguinte script do PowerShell.  
  
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
  
     Este script do PowerShell usa SDDL Security Descriptor Definition Language () para conceder acesso a usuários internos para o namespace do WMI "raiz/servicemodel". Especifica as seguintes ACLs:  
  
    -   Administrador interno (BA) - já tinha acesso.  
  
    -   Serviço (NS) - de rede já tinha acesso.  
  
    -   Sistema local (LS) - já tinha acesso.  
  
    -   Usuários internos - para conceder acesso para o grupo.  
  
#### <a name="to-grant-provider-registration-access"></a>Para conceder o provedor de registro de acesso  
  
1.  Execute o seguinte script do PowerShell.  
  
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
  
### <a name="granting-access-to-arbitrary-users-or-groups"></a>Concedendo acesso a outros usuários ou grupos  
 O exemplo nesta seção concede privilégios de registro do provedor WMI para todos os usuários locais. Se você quiser conceder acesso a um usuário ou grupo que não é interno no, você deve obter esse usuário ou segurança SID do grupo de (identificador). Não há nenhuma maneira simple de obter o SID para um usuário arbitrário. É um método fazer logon como usuário desejado e, em seguida, execute o seguinte comando do shell.  
  
```  
Whoami /user  
```  
  
 Isso fornece o SID do usuário atual, mas esse método não pode ser usado para obter o SID em qualquer usuário arbitrário. Outro método para obter o SID é usar o [getsid.exe](http://go.microsoft.com/fwlink/?LinkId=186467) ferramenta do [ferramentas para tarefas administrativas do Windows 2000 Resource Kit](http://go.microsoft.com/fwlink/?LinkId=178660). Essa ferramenta compara o SID de dois usuários (local ou domínio), e como efeito imprime os SIDs dois à linha de comando. Para obter mais informações, consulte [Well Known SIDs](http://go.microsoft.com/fwlink/?LinkId=186468).  
  
## <a name="accessing-remote-wmi-object-instances"></a>Acessando instâncias de objeto WMI remoto  
 Se você precisar acessar [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] instâncias de WMI em um computador remoto, você deve habilitar privacidade de pacotes de ferramentas que você usa para acessar. A seção a seguir descreve como conseguir isto usando o WMI CIM Studio, o Testador de instrumentação de gerenciamento do Windows, bem como os .NET SDK 2.0.  
  
### <a name="wmi-cim-studio"></a>CIM Studio do WMI  
 Se você tiver instalado o [ferramentas administrativas do WMI](http://go.microsoft.com/fwlink/?LinkId=95185), você pode usar o CIM Studio do WMI para acessar instâncias WMI. As ferramentas estão na seguinte pasta  
  
 **Ferramentas de Files\WMI %Windir%\Program\\**  
  
1.  No **conectar ao namespace:** , digite **root\ServiceModel** e clique em **Okey.**  
  
2.  No **WMI CIM Studio logon** janela, clique no **opções >>** botão para expandir a janela. Selecione **privacidade do pacote** para **nível de autenticação**e clique em **Okey**.  
  
### <a name="windows-management-instrumentation-tester"></a>Testador de instrumentação de gerenciamento do Windows  
 Essa ferramenta é instalada pelo Windows. Para executá-lo, inicie o console de comando digitando **cmd.exe** no **iniciar/executar** caixa de diálogo e clique em **Okey**. Em seguida, digite **wbemtest.exe** na janela de comando. A ferramenta Testador de instrumentação de gerenciamento do Windows, em seguida, é iniciada.  
  
1.  Clique o **conectar** botão no canto superior direito da janela.  
  
2.  Na nova janela, digite **root\ServiceModel** para o **Namespace** campo e selecione **privacidade do pacote** para **nível de autenticação**. Clique em **Conectar**.  
  
### <a name="using-managed-code"></a>Usando código gerenciado  
 Você também pode acessar instâncias remotas do WMI programaticamente usando classes fornecidas pelo <xref:System.Management> namespace. O exemplo de código a seguir demonstra como fazer isso.  
  
```  
String wcfNamespace = String.Format(@"\\{0}\Root\ServiceModel",      
   this.serviceMachineName);  
  
ConnectionOptions connection = new ConnectionOptions();  
connection.Authentication = AuthenticationLevel.PacketPrivacy;  
ManagementScope scope = new ManagementScope(this.wcfNamespace, connection);  
```
