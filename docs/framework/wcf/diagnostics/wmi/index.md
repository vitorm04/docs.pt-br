---
title: Usando Windows Management Instrumentation para diagnóstico
ms.date: 03/30/2017
ms.assetid: fe48738d-e31b-454d-b5ec-24c85c6bf79a
ms.openlocfilehash: 47aece36368be12a2a63283367e95dcaa64ef484
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64662463"
---
# <a name="using-windows-management-instrumentation-for-diagnostics"></a>Usando Windows Management Instrumentation para diagnóstico
Windows Communication Foundation (WCF) expõe dados de inspeção de um serviço em tempo de execução através de um provedor de instrumentação de gerenciamento do Windows (WMI) do WCF.  
  
## <a name="enabling-wmi"></a>Habilitando o WMI  
 O WMI é a implementação da Microsoft do Web-Based Enterprise Management (WBEM) padrão. Para obter mais informações sobre o SDK do WMI, consulte [instrumentação de gerenciamento do Windows](/windows/desktop/WmiSdk/wmi-start-page). O WBEM é um padrão do setor para como os aplicativos expõem instrumentação de gerenciamento para as ferramentas de gerenciamento externo.  
  
 Um provedor WMI é um componente que expõe a instrumentação no tempo de execução por meio de uma interface compatível com a iniciativa WBEM. Ele consiste em um conjunto de objetos WMI que têm pares de atributo/valor. Pares podem ser de um número de tipos simples. Ferramentas de gerenciamento podem se conectar aos serviços por meio da interface em tempo de execução. O WCF expõe atributos de serviços, como endereços, associações, comportamentos e ouvintes.  
  
 O provedor WMI interno pode ser ativado no arquivo de configuração do aplicativo. Isso é feito por meio das `wmiProviderEnabled` atributo do [ \<diagnóstico >](../../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md) no [ \<System. ServiceModel >](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) seção, conforme mostrado no exemplo a seguir configuração.  
  
```xml  
<system.serviceModel>  
    …  
    <diagnostics wmiProviderEnabled="true" />  
    …  
</system.serviceModel>  
```  
  
 Essa entrada de configuração expõe uma interface WMI. Aplicativos de gerenciamento agora podem se conectar por meio dessa interface e acessar a instrumentação de gerenciamento do aplicativo.  
  
## <a name="accessing-wmi-data"></a>Acessando dados do WMI  
 Dados do WMI podem ser acessados de várias maneiras diferentes. A Microsoft fornece as APIs do WMI para scripts, aplicativos do Visual Basic, aplicativos de C++ e o [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)]. Para obter mais informações, consulte [WMI usando](https://go.microsoft.com/fwlink/?LinkId=95183).  
  
> [!CAUTION]
>  Se você usar o .NET Framework ofereceu métodos para acessar programaticamente os dados do WMI, você deve estar ciente de que esses métodos podem gerar exceções quando a conexão é estabelecida. A conexão não for estabelecida durante a construção do <xref:System.Management.ManagementObject> instância, mas, na primeira solicitação que envolve a troca de dados real. Portanto, você deve usar um `try..catch` bloco para capturar possíveis exceções.  
  
 Você pode alterar o rastreamento e nível de log de mensagem, bem como opções de log de mensagem para o `System.ServiceModel` origem de rastreamento no WMI. Isso pode ser feito, acessando o [AppDomainInfo](../../../../../docs/framework/wcf/diagnostics/wmi/appdomaininfo.md) instância, que expõe essas propriedades Boolianas: `LogMessagesAtServiceLevel`, `LogMessagesAtTransportLevel`, `LogMalformedMessages`, e `TraceLevel`. Portanto, se você configura um ouvinte de rastreamento para o log de mensagens, mas definir essas opções para `false` na configuração, você pode alterar a `true` quando o aplicativo está em execução. Isso permitirá que o log de mensagens em tempo de execução com eficiência. Da mesma forma, se você habilitar o registro em log no arquivo de configuração de mensagem, você pode desabilitá-lo em tempo de execução usando o WMI.  
  
 Você deve estar ciente que, se nenhum log de mensagem rastrear ouvintes para receber mensagens em log ou não `System.ServiceModel` ouvintes de rastreamento para rastreamento são especificados no arquivo de configuração, nenhuma de suas alterações ficam em vigor, mesmo que as alterações sejam aceitas pelo WMI. Para obter mais informações sobre como configurar corretamente os respectivos ouvintes, consulte [Configurando o log de mensagens](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md) e [Configurando o rastreamento](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md). O nível de rastreamento de todas as outras origens de rastreamento especificado por configuração é eficaz quando o aplicativo é iniciado e não pode ser alterado.  
  
 O WCF expõe um `GetOperationCounterInstanceName` método para execução de scripts. Esse método retorna um nome de instância do contador de desempenho se fornecê-la com um nome de operação. No entanto, ele não valida sua entrada. Portanto, se você fornecer um nome de operação incorreta, um nome de contador incorreto é retornado.  
  
 O `OutgoingChannel` propriedade do `Service` instância não conta canais abertos por um serviço para se conectar a outro serviço, se o cliente do WCF para o serviço de destino não for criado dentro de `Service` método.  
  
 **Cuidado** WMI dá suporte apenas a um <xref:System.TimeSpan> decimais até 3 de valor. Por exemplo, se seu serviço define uma de suas propriedades para <xref:System.TimeSpan.MaxValue>, seu valor é truncado após 3 pontos decimais quando visualizado por meio do WMI.  
  
## <a name="security"></a>Segurança  
 Como o provedor de WMI do WCF permite a descoberta de serviços em um ambiente, você deve ter muito cuidado para conceder acesso a ele. Se você relaxar o acesso de somente de administrador padrão, você pode permitir o acesso de partes menos confiável a dados confidenciais em seu ambiente. Especificamente, se você Flexibilize as permissões de acesso WMI remoto, ataques de inundação podem ocorrer. Se um processo é a inundação de excesso de solicitações WMI, seu desempenho pode ser prejudicado.  
  
 Além disso, se você relaxar as permissões de acesso para o arquivo MOF, partes de menos confiáveis podem manipular o comportamento de WMI e alterar os objetos que são carregados no esquema do WMI. Por exemplo, os campos podem ser removidos, de modo que os dados críticos são escondidos do administrador ou campos que não preencher ou fazer com que as exceções são adicionados ao arquivo.  
  
 Por padrão, o provedor WMI do WCF concede "método de execução", "gravação do provedor" e "Habilitar conta" permissão de administrador e a permissão "Habilitar conta" para ASP.NET, serviço Local e serviço de rede. Em particular, em não -[!INCLUDE[wv](../../../../../includes/wv-md.md)] plataformas, a conta do ASP.NET tem acesso de leitura ao namespace WMI ServiceModel. Se você não quiser conceder esses privilégios a um grupo de usuários, você deve desativar o provedor WMI (desabilitado por padrão) ou desabilite o acesso para o grupo de usuários específicos.  
  
 Além disso, quando você tentar ativar o WMI por meio da configuração, o WMI não pode ser habilitado devido ao privilégio de usuário insuficientes. No entanto, nenhum evento é gravado no log de eventos para registrar essa falha.  
  
 Para modificar os níveis de privilégio de usuário, use as etapas a seguir.  
  
1. Clique em Iniciar e, em seguida, executar e digite **compmgmt. msc**.  
  
2. Clique com botão direito **serviços e os controles de aplicativo/WMI** para selecionar **propriedades**.  
  
3. Selecione o **segurança** guia e navegue até a **raiz/ServiceModel** namespace. Clique o **segurança** botão.  
  
4. Selecione o grupo específico ou usuário que você deseja controlar o acesso e usar o **Allow** ou **Deny** caixa de seleção para configurar permissões.  
  
## <a name="granting-wcf-wmi-registration-permissions-to-additional-users"></a>Conceder permissões de registro de WMI do WCF a usuários adicionais  
 O WCF expõe dados de gerenciamento ao WMI. Ele faz isso por um provedor WMI no processo, às vezes chamado de "provedor desacoplado" de hospedagem. Para os dados de gerenciamento a ser exposta, a conta que registre este provedor deve ter as permissões apropriadas. No Windows, somente um pequeno conjunto de contas com privilégios pode registrar os provedores desacoplados por padrão. Esse é um problema porque os usuários normalmente desejam expor dados WMI do serviço WCF executado em uma conta que não está no conjunto padrão.  
  
 Para fornecer esse acesso, um administrador deve conceder as seguintes permissões para a conta adicional na seguinte ordem:  
  
1. Permissão para acessar o Namespace de WMI do WCF.  
  
2. Permissão para registrar o provedor de WMI do WCF separados.  
  
#### <a name="to-grant-wmi-namespace-access-permission"></a>Para conceder permissão de acesso do namespace WMI  
  
1. Execute o seguinte script do PowerShell.  
  
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
  
     Este script do PowerShell usa SDDL Security Descriptor Definition Language () para conceder o acesso de grupo interno usuários para o namespace do WMI "raiz/servicemodel". Especifica as seguintes ACLs:  
  
    - Administrador interno (BA) - já tinham acesso.  
  
    - (NS) - serviço de rede já tinha acesso.  
  
    - Sistema local (LS) - já tinham acesso.  
  
    - Usuários internos - o grupo para conceder acesso a.  
  
#### <a name="to-grant-provider-registration-access"></a>Para conceder o provedor de registro de acesso  
  
1. Execute o seguinte script do PowerShell.  
  
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
 O exemplo nesta seção concede privilégios de registro do provedor WMI para todos os usuários locais. Se você quiser conceder acesso a um usuário ou grupo que não é interno, você deve obter esse usuário ou segurança SID do grupo de (identificador). Não há nenhuma maneira simples de obter o SID para um usuário arbitrários. Um método é fazer logon como o usuário desejado e, em seguida, emita o seguinte comando de shell.  
  
```  
Whoami /user  
```  
  
 Isso fornece o SID do usuário atual, mas esse método não pode ser usado para obter o SID em qualquer usuário arbitrário. Outro método para obter o SID é usar o [getsid.exe](https://go.microsoft.com/fwlink/?LinkId=186467) ferramenta da [Windows 2000 Resource Kit Tools para tarefas administrativas](https://go.microsoft.com/fwlink/?LinkId=178660). Essa ferramenta compara o SID de dois usuários (local ou domínio) e como um lado efeito imprime os dois SIDs à linha de comando. Para obter mais informações, consulte [SIDs bem conhecidos](https://go.microsoft.com/fwlink/?LinkId=186468).  
  
## <a name="accessing-remote-wmi-object-instances"></a>Acessando instâncias de objeto WMI remoto  
 Se você precisar acessar instâncias do WMI do WCF em um computador remoto, você deve habilitar privacidade de pacote nas ferramentas de que você usa para acesso. A seção a seguir descreve como conseguir isto usando o CIM Studio WMI, o Testador de instrumentação de gerenciamento do Windows, bem como os SDK do .NET 2.0.  
  
### <a name="wmi-cim-studio"></a>CIM Studio do WMI  
 Se você tiver instalado [ferramentas administrativas do WMI](https://go.microsoft.com/fwlink/?LinkId=95185), você pode usar o CIM Studio WMI para acessar instâncias do WMI. As ferramentas estão na seguinte pasta  
  
 **Ferramentas de Files\WMI %Windir%\Program\\**  
  
1. No **conectar-se ao namespace:** , digite **root\ServiceModel** e clique em **Okey.**  
  
2. No **WMI CIM Studio Login** janela, clique no **opções >>** botão para expandir a janela. Selecione **privacidade de pacote** para **nível de autenticação**e clique em **Okey**.  
  
### <a name="windows-management-instrumentation-tester"></a>Testador de instrumentação de gerenciamento do Windows  
 Essa ferramenta é instalada pelo Windows. Para executá-lo, inicie um console de comando digitando **cmd.exe** na **iniciar/executar** caixa de diálogo e clique em **Okey**. Em seguida, digite **wbemtest.exe** na janela de comando. A ferramenta do Testador de instrumentação de gerenciamento do Windows, em seguida, é iniciada.  
  
1. Clique o **Connect** botão no canto superior direito da janela.  
  
2. Na nova janela, insira **root\ServiceModel** para o **Namespace** campo e selecione **privacidade de pacote** para **nível de autenticação**. Clique em **Conectar**.  
  
### <a name="using-managed-code"></a>Usando código gerenciado  
 Você também pode acessar instâncias remotas do WMI programaticamente usando classes fornecidas pelo <xref:System.Management> namespace. O exemplo de código a seguir demonstra como fazer isso.  
  
```csharp
String wcfNamespace = $@"\\{this.serviceMachineName}\Root\ServiceModel");
  
ConnectionOptions connection = new ConnectionOptions();  
connection.Authentication = AuthenticationLevel.PacketPrivacy;  
ManagementScope scope = new ManagementScope(this.wcfNamespace, connection);  
```
