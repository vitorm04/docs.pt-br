---
title: Configurando o serviço de compartilhamento de porta Net.TCP
ms.date: 03/30/2017
ms.assetid: b6dd81fa-68b7-4e1b-868e-88e5901b7ea0
ms.openlocfilehash: fea2e734099c4c623dcde2a37f4c164cf9ce61ac
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81464195"
---
# <a name="configuring-the-nettcp-port-sharing-service"></a><span data-ttu-id="07aa8-102">Configurando o serviço de compartilhamento de porta Net.TCP</span><span class="sxs-lookup"><span data-stu-id="07aa8-102">Configuring the Net.TCP Port Sharing Service</span></span>
<span data-ttu-id="07aa8-103">Os serviços auto-hospedados que usam o transporte Net.TCP `ListenBacklog` `MaxPendingAccepts`podem controlar várias configurações avançadas, como e , que regem o comportamento do soquete TCP subjacente usado para comunicação de rede.</span><span class="sxs-lookup"><span data-stu-id="07aa8-103">Self-hosted services that use the Net.TCP transport can control several advanced settings, such as `ListenBacklog` and `MaxPendingAccepts`, which govern the behavior of the underlying TCP socket used for network communication.</span></span> <span data-ttu-id="07aa8-104">No entanto, essas configurações para cada soquete só se aplicam no nível de vinculação se a vinculação de transporte tiver desativado o compartilhamento de porta, que é habilitado por padrão.</span><span class="sxs-lookup"><span data-stu-id="07aa8-104">However, these settings for each socket only apply at the binding level if the transport binding has disabled port sharing, which is enabled by default.</span></span>  
  
 <span data-ttu-id="07aa8-105">Quando uma vinculação net.tcp permite `portSharingEnabled =true` o compartilhamento de portas (configurando no elemento de vinculação de transporte), ele permite implicitamente que um processo externo (ou seja, o SMSvcHost.exe, que hospeda o Serviço de Compartilhamento de Portas Net.TCP) gerencie o soquete TCP em seu nome.</span><span class="sxs-lookup"><span data-stu-id="07aa8-105">When a net.tcp binding enables port sharing (by setting `portSharingEnabled =true` on the transport binding element), it implicitly allows an external process (namely the SMSvcHost.exe, which hosts the Net.TCP Port Sharing Service) to manage the TCP socket on its behalf.</span></span> <span data-ttu-id="07aa8-106">Por exemplo, ao usar o TCP, especifique:</span><span class="sxs-lookup"><span data-stu-id="07aa8-106">For example, when using TCP, specify:</span></span>  
  
```xml  
<tcpTransport portSharingEnabled="true"  />  
```  
  
 <span data-ttu-id="07aa8-107">Quando configurado desta forma, quaisquer configurações de soquete especificadas no elemento de vinculação de transporte do serviço são ignoradas em favor das configurações de soquete especificadas pelo SMSvcHost.exe.</span><span class="sxs-lookup"><span data-stu-id="07aa8-107">When configured in this way, any socket settings specified on the service's transport binding element are ignored in favor of the socket settings specified by SMSvcHost.exe.</span></span>  
  
 <span data-ttu-id="07aa8-108">Para configurar o SMSvcHost.exe, crie um arquivo de configuração XML chamado SmSvcHost.exe.config e coloque-o no mesmo diretório físico que o Executável SMSvcHost.exe (por exemplo, C:\Windows\Microsoft.NET\Framework\v4.5).</span><span class="sxs-lookup"><span data-stu-id="07aa8-108">To configure the SMSvcHost.exe, create an XML configuration file named SmSvcHost.exe.config and place it in the same physical directory as the SMSvcHost.exe executable (for example, C:\Windows\Microsoft.NET\Framework\v4.5).</span></span>  
  
 <span data-ttu-id="07aa8-109">O exemplo a seguir ilustra uma amostra SMSvcHost.exe.config, com as configurações padrão para todos os valores configuráveis indicados explicitamente.</span><span class="sxs-lookup"><span data-stu-id="07aa8-109">The following example illustrates a sample SMSvcHost.exe.config, with the default settings for all configurable values stated explicitly.</span></span>  
  
```xml  
<configuration>  
   <system.serviceModel.activation>  
       <net.tcp listenBacklog="16" <!-- 16 * # of processors -->  
          maxPendingAccepts="4"<!-- 4 * # of processors -->  
          maxPendingConnections="100"  
          receiveTimeout="00:00:30" <!-- 30 seconds -->  
          teredoEnabled="false">  
          <allowAccounts>  
             <!-- LocalSystem account -->  
             <add securityIdentifier="S-1-5-18"/>  
             <!-- LocalService account -->  
             <add securityIdentifier="S-1-5-19"/>  
             <!-- Administrators account -->  
             <add securityIdentifier="S-1-5-20"/>  
             <!-- Network Service account -->  
             <add securityIdentifier="S-1-5-32-544" />  
             <!-- IIS_IUSRS account (Vista only) -->  
             <add securityIdentifier="S-1-5-32-568"/>  
           </allowAccounts>  
       </net.tcp>  
    </system.serviceModel.activation>
</configuration>  
```  
  
## <a name="when-to-modify-smsvchostexeconfig"></a><span data-ttu-id="07aa8-110">Quando modificar smsvcHost.exe.config</span><span class="sxs-lookup"><span data-stu-id="07aa8-110">When to Modify SMSvcHost.exe.config</span></span>  
 <span data-ttu-id="07aa8-111">Em geral, deve-se tomar cuidado ao modificar o conteúdo do arquivo SMSvcHost.exe.config, pois quaisquer configurações especificadas neste arquivo afetam todos os serviços em um computador que usa o Serviço de Compartilhamento de Portas Net.TCP.</span><span class="sxs-lookup"><span data-stu-id="07aa8-111">In general, care should be taken when modifying the contents of the SMSvcHost.exe.config file, because any configuration settings specified in this file affect all of the services on a computer that uses the Net.TCP Port Sharing Service.</span></span> <span data-ttu-id="07aa8-112">Isso inclui aplicativos no Windows Vista que usam os recursos de ativação TCP do Serviço de Ativação de Processos do Windows (WAS).</span><span class="sxs-lookup"><span data-stu-id="07aa8-112">This includes applications on Windows Vista that use the TCP Activation features of the Windows Process Activation Service (WAS).</span></span>  
  
 <span data-ttu-id="07aa8-113">No entanto, às vezes, você pode precisar alterar a configuração padrão para o Serviço de Compartilhamento de Portas Net.TCP.</span><span class="sxs-lookup"><span data-stu-id="07aa8-113">However, sometimes you may need to change the default configuration for the Net.TCP Port Sharing Service.</span></span> <span data-ttu-id="07aa8-114">Por exemplo, o `maxPendingAccepts` valor padrão para é 4 \* número de processadores.</span><span class="sxs-lookup"><span data-stu-id="07aa8-114">For example, the default value for `maxPendingAccepts` is 4 \* number of processors.</span></span> <span data-ttu-id="07aa8-115">Os servidores que hospedam um grande número de serviços que usam o compartilhamento de portas podem aumentar esse valor para atingir o máximo de throughput.</span><span class="sxs-lookup"><span data-stu-id="07aa8-115">Servers that host a large number of services that use port sharing may increase this value to achieve maximum throughput.</span></span> <span data-ttu-id="07aa8-116">O valor `maxPendingConnections` padrão para é 100.</span><span class="sxs-lookup"><span data-stu-id="07aa8-116">The default value for `maxPendingConnections` is 100.</span></span> <span data-ttu-id="07aa8-117">Você deve considerar aumentar esse valor também se houver vários clientes simultâneos ligando para o serviço e o serviço está diminuindo as conexões com clientes.</span><span class="sxs-lookup"><span data-stu-id="07aa8-117">You should consider increasing this value also if there are multiple concurrent clients calling the service and the service is dropping client connections.</span></span>  
  
 <span data-ttu-id="07aa8-118">O SMSvcHost.exe.config também contém informações sobre as identidades do processo que podem fazer uso do serviço de compartilhamento de portas.</span><span class="sxs-lookup"><span data-stu-id="07aa8-118">SMSvcHost.exe.config also contains information about the process identities that may make use of the port sharing service.</span></span> <span data-ttu-id="07aa8-119">Quando um processo se conecta ao serviço de compartilhamento de portas para fazer uso de uma porta TCP compartilhada, a identidade do processo de conexão é verificada em uma lista de identidades que são permitidas para fazer uso do serviço de compartilhamento de portas.</span><span class="sxs-lookup"><span data-stu-id="07aa8-119">When a process connects to the port sharing service to make use of a shared TCP port, the process identity of the connecting process is checked against a list of identities that are permitted to make use of the port sharing service.</span></span> <span data-ttu-id="07aa8-120">Essas identidades são especificadas como identificadores de segurança \<(SIDs) na seção permitirContas> do arquivo SMSvcHost.exe.config.</span><span class="sxs-lookup"><span data-stu-id="07aa8-120">These identities are specified as security identifiers (SIDs) in the \<allowAccounts> section of the SMSvcHost.exe.config file.</span></span> <span data-ttu-id="07aa8-121">Por padrão, a permissão para usar o serviço de compartilhamento de portas é concedida às contas do sistema (LocalService, LocalSystem e NetworkService), bem como aos membros do grupo Administradores.</span><span class="sxs-lookup"><span data-stu-id="07aa8-121">By default, permission to use the port sharing service is granted to system accounts (LocalService, LocalSystem, and NetworkService) as well as members of the Administrators group.</span></span> <span data-ttu-id="07aa8-122">Os aplicativos que permitem que um processo executado como outra identidade (por exemplo, uma identidade de usuário) se conecte ao serviço de compartilhamento de portas deve adicionar explicitamente o SID apropriado ao SMSvcHost.exe.config (essas alterações não são aplicadas até que o processo SMSvc.exe seja reiniciado).</span><span class="sxs-lookup"><span data-stu-id="07aa8-122">Applications that allow a process running as another identity (for example, a user identity) to connect to the port sharing service must explicitly add the appropriate SID to the SMSvcHost.exe.config (these changes are not applied until the SMSvc.exe process is restarted).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="07aa8-123">Nos sistemas Windows Vista com controle de conta de usuário (UAC) ativados, os usuários locais exigem permissões elevadas, mesmo que sua conta seja um membro do grupo Administradores.</span><span class="sxs-lookup"><span data-stu-id="07aa8-123">On Windows Vista systems with User Account Control (UAC) enabled, local users require elevated permissions even if their account is a member of the Administrators group.</span></span> <span data-ttu-id="07aa8-124">Para permitir que esses usuários façam uso do serviço de compartilhamento de portas sem elevação, o SID do usuário (ou o SID de um grupo no qual o usuário é membro) deve ser explicitamente adicionado à seção \<de> de Contas permitidas do SMSvcHost.exe.config.</span><span class="sxs-lookup"><span data-stu-id="07aa8-124">To allow these users to make use of the port sharing service without elevation, the user's SID (or the SID of a group in which the user is a member) must be explicitly added to the \<allowAccounts> section of SMSvcHost.exe.config.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="07aa8-125">O arquivo padrão SMSvcHost.exe.config `etwProviderId` especifica um costume para impedir que o rastreamento smsvcHost.exe interfira em rastreamentos de serviços.</span><span class="sxs-lookup"><span data-stu-id="07aa8-125">The default SMSvcHost.exe.config file specifies a custom `etwProviderId` to prevent SMSvcHost.exe tracing from interfering with service traces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07aa8-126">Confira também</span><span class="sxs-lookup"><span data-stu-id="07aa8-126">See also</span></span>

- [<span data-ttu-id="07aa8-127">\<net.tcp></span><span class="sxs-lookup"><span data-stu-id="07aa8-127">\<net.tcp></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/net-tcp.md)
