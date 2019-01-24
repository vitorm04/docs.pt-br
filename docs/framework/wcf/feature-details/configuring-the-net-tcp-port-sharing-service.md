---
title: Configurando o serviço de compartilhamento de porta Net.TCP
ms.date: 03/30/2017
ms.assetid: b6dd81fa-68b7-4e1b-868e-88e5901b7ea0
ms.openlocfilehash: 9bc625f9e998f27b6227a5951f11c7d85220ae7f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54585517"
---
# <a name="configuring-the-nettcp-port-sharing-service"></a><span data-ttu-id="66259-102">Configurando o serviço de compartilhamento de porta Net.TCP</span><span class="sxs-lookup"><span data-stu-id="66259-102">Configuring the Net.TCP Port Sharing Service</span></span>
<span data-ttu-id="66259-103">Os serviços são hospedados que usam o transporte NET. TCP podem controlar várias configurações avançadas, como `ListenBacklog` e `MaxPendingAccepts`, que determinam o comportamento de soquete TCP subjacente usado para comunicação de rede.</span><span class="sxs-lookup"><span data-stu-id="66259-103">Self-hosted services that use the Net.TCP transport can control several advanced settings, such as `ListenBacklog` and `MaxPendingAccepts`, which govern the behavior of the underlying TCP socket used for network communication.</span></span> <span data-ttu-id="66259-104">No entanto, essas configurações para cada soquete só se aplicam no nível de associação se a associação de transporte tiver desabilitado o compartilhamento de porta, que é habilitado por padrão.</span><span class="sxs-lookup"><span data-stu-id="66259-104">However, these settings for each socket only apply at the binding level if the transport binding has disabled port sharing, which is enabled by default.</span></span>  
  
 <span data-ttu-id="66259-105">Quando uma associação de NET. TCP habilita o compartilhamento de porta (definindo `portSharingEnabled =true` no elemento de associação de transporte), ele permite implicitamente que um processo externo (ou seja, o SMSvcHost.exe, que hospeda o serviço de compartilhamento de porta NET. TCP) para gerenciar o soquete TCP em seu nome.</span><span class="sxs-lookup"><span data-stu-id="66259-105">When a net.tcp binding enables port sharing (by setting `portSharingEnabled =true` on the transport binding element), it implicitly allows an external process (namely the SMSvcHost.exe, which hosts the Net.TCP Port Sharing Service) to manage the TCP socket on its behalf.</span></span> <span data-ttu-id="66259-106">Por exemplo, ao usar TCP, especifique:</span><span class="sxs-lookup"><span data-stu-id="66259-106">For example, when using TCP, specify:</span></span>  
  
```xml  
<tcpTransport portSharingEnabled="true"  />  
```  
  
 <span data-ttu-id="66259-107">Quando configurado dessa forma, as configurações de soquete especificadas no elemento de associação de transporte do serviço são ignoradas em favor das configurações de soquete especificadas pelo SMSvcHost.exe.</span><span class="sxs-lookup"><span data-stu-id="66259-107">When configured in this way, any socket settings specified on the service's transport binding element are ignored in favor of the socket settings specified by SMSvcHost.exe.</span></span>  
  
 <span data-ttu-id="66259-108">Para configurar o SMSvcHost.exe, crie um arquivo de configuração XML chamado SMSvcHost e coloque-o no mesmo diretório físico do executável SMSvcHost.exe (por exemplo, C:\Windows\Microsoft.NET\Framework\v4.5).</span><span class="sxs-lookup"><span data-stu-id="66259-108">To configure the SMSvcHost.exe, create an XML configuration file named SmSvcHost.exe.config and place it in the same physical directory as the SMSvcHost.exe executable (for example, C:\Windows\Microsoft.NET\Framework\v4.5).</span></span>  
  
 <span data-ttu-id="66259-109">O exemplo a seguir ilustra um exemplo de SMSvcHost, com as configurações padrão para todos os valores configuráveis declarados explicitamente.</span><span class="sxs-lookup"><span data-stu-id="66259-109">The following example illustrates a sample SMSvcHost.exe.config, with the default settings for all configurable values stated explicitly.</span></span>  
  
```xml  
<configuration>  
   <system.serviceModel.activation>  
       <net.tcp listenBacklog="16" <!--16 * # of processors -->  
          maxPendingAccepts="4"<!-- 4 * # of processors -->  
          maxPendingConnections="100"  
          receiveTimeout="00:00:30" <!--30 seconds -->  
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
</configuration>  
```  
  
## <a name="when-to-modify-smsvchostexeconfig"></a><span data-ttu-id="66259-110">Quando modificar SMSvcHost</span><span class="sxs-lookup"><span data-stu-id="66259-110">When to Modify SMSvcHost.exe.config</span></span>  
 <span data-ttu-id="66259-111">Em geral, tome cuidado ao modificar o conteúdo do arquivo de SMSvcHost, porque as definições de configuração especificadas neste arquivo afetam todos os serviços em um computador que usa o serviço de compartilhamento de porta NET. TCP.</span><span class="sxs-lookup"><span data-stu-id="66259-111">In general, care should be taken when modifying the contents of the SMSvcHost.exe.config file, because any configuration settings specified in this file affect all of the services on a computer that uses the Net.TCP Port Sharing Service.</span></span> <span data-ttu-id="66259-112">Isso inclui aplicativos no [!INCLUDE[wv](../../../../includes/wv-md.md)] que usam os recursos de ativação de TCP de serviço de ativação de processos para Windows (WAS).</span><span class="sxs-lookup"><span data-stu-id="66259-112">This includes applications on [!INCLUDE[wv](../../../../includes/wv-md.md)] that use the TCP Activation features of the Windows Process Activation Service (WAS).</span></span>  
  
 <span data-ttu-id="66259-113">No entanto, às vezes, você talvez precise alterar a configuração padrão para o serviço de compartilhamento de porta NET. TCP.</span><span class="sxs-lookup"><span data-stu-id="66259-113">However, sometimes you may need to change the default configuration for the Net.TCP Port Sharing Service.</span></span> <span data-ttu-id="66259-114">Por exemplo, o valor padrão para `maxPendingAccepts` é 4 \* número de processadores.</span><span class="sxs-lookup"><span data-stu-id="66259-114">For example, the default value for `maxPendingAccepts` is 4 \* number of processors.</span></span> <span data-ttu-id="66259-115">Servidores que hospedam um grande número de serviços que usam o compartilhamento de porta podem aumentar esse valor para atingir a taxa de transferência máxima.</span><span class="sxs-lookup"><span data-stu-id="66259-115">Servers that host a large number of services that use port sharing may increase this value to achieve maximum throughput.</span></span> <span data-ttu-id="66259-116">O valor padrão para `maxPendingConnections` é 100.</span><span class="sxs-lookup"><span data-stu-id="66259-116">The default value for `maxPendingConnections` is 100.</span></span> <span data-ttu-id="66259-117">Você deve considerar aumentar esse valor também se há vários clientes simultâneos para chamar o serviço e o serviço está descartando as conexões de cliente.</span><span class="sxs-lookup"><span data-stu-id="66259-117">You should consider increasing this value also if there are multiple concurrent clients calling the service and the service is dropping client connections.</span></span>  
  
 <span data-ttu-id="66259-118">SMSvcHost também contém informações sobre o processo de usarem identidades que podem tornar da porta de serviço de compartilhamento.</span><span class="sxs-lookup"><span data-stu-id="66259-118">SMSvcHost.exe.config also contains information about the process identities that may make use of the port sharing service.</span></span> <span data-ttu-id="66259-119">Quando um processo se conecta à porta de serviço para utilizar um TCP compartilhado de compartilhamento de porta, a identidade do processo da conexão processo é verificado em relação uma lista de identidades têm permissão para fazer uso do serviço de compartilhamento de porta.</span><span class="sxs-lookup"><span data-stu-id="66259-119">When a process connects to the port sharing service to make use of a shared TCP port, the process identity of the connecting process is checked against a list of identities that are permitted to make use of the port sharing service.</span></span> <span data-ttu-id="66259-120">Essas identidades são especificadas como identificadores de segurança (SIDs) na \<allowAccounts > seção do arquivo de SMSvcHost.</span><span class="sxs-lookup"><span data-stu-id="66259-120">These identities are specified as security identifiers (SIDs) in the \<allowAccounts> section of the SMSvcHost.exe.config file.</span></span> <span data-ttu-id="66259-121">Por padrão, a permissão para usar a serviço de compartilhamento de porta é concedida para contas do sistema (LocalService, LocalSystem e NetworkService), bem como membros do grupo Administradores.</span><span class="sxs-lookup"><span data-stu-id="66259-121">By default, permission to use the port sharing service is granted to system accounts (LocalService, LocalSystem, and NetworkService) as well as members of the Administrators group.</span></span> <span data-ttu-id="66259-122">Aplicativos que permitem que um processo em execução como outra identidade (por exemplo, uma identidade de usuário) para se conectar ao serviço de compartilhamento de porta devem adicionar explicitamente o SID apropriado para o SMSvcHost (essas alterações não serão aplicadas até que o processo de SMSvc.exe é reiniciado).</span><span class="sxs-lookup"><span data-stu-id="66259-122">Applications that allow a process running as another identity (for example, a user identity) to connect to the port sharing service must explicitly add the appropriate SID to the SMSvcHost.exe.config (these changes are not applied until the SMSvc.exe process is restarted).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="66259-123">Em [!INCLUDE[wv](../../../../includes/wv-md.md)] sistemas com User Account Control (UAC) habilitados, o locais de usuários exigem permissões elevadas, mesmo se sua conta é membro do grupo Administradores.</span><span class="sxs-lookup"><span data-stu-id="66259-123">On [!INCLUDE[wv](../../../../includes/wv-md.md)] systems with User Account Control (UAC) enabled, local users require elevated permissions even if their account is a member of the Administrators group.</span></span> <span data-ttu-id="66259-124">Para permitir que esses usuários fazer uso do serviço sem a elevação de privilégio, o SID do usuário (ou o SID de um grupo no qual o usuário é membro) de compartilhamento de porta deve ser adicionado explicitamente para o \<allowAccounts > seção do SMSvcHost.</span><span class="sxs-lookup"><span data-stu-id="66259-124">To allow these users to make use of the port sharing service without elevation, the user's SID (or the SID of a group in which the user is a member) must be explicitly added to the \<allowAccounts> section of SMSvcHost.exe.config.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="66259-125">O arquivo de SMSvcHost padrão especifica um personalizado `etwProviderId` para impedir que o rastreamento SMSvcHost.exe interfira com rastreamentos de serviço.</span><span class="sxs-lookup"><span data-stu-id="66259-125">The default SMSvcHost.exe.config file specifies a custom `etwProviderId` to prevent SMSvcHost.exe tracing from interfering with service traces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66259-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="66259-126">See also</span></span>
- [<span data-ttu-id="66259-127">\<net.tcp></span><span class="sxs-lookup"><span data-stu-id="66259-127">\<net.tcp></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/net-tcp.md)
