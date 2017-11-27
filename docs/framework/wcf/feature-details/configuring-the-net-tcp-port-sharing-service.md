---
title: "Configurando o serviço de compartilhamento de porta Net.TCP"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b6dd81fa-68b7-4e1b-868e-88e5901b7ea0
caps.latest.revision: "20"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: b8b0d1920e70f0d9b6f837800bcc049999f6fde7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="configuring-the-nettcp-port-sharing-service"></a><span data-ttu-id="4408f-102">Configurando o serviço de compartilhamento de porta Net.TCP</span><span class="sxs-lookup"><span data-stu-id="4408f-102">Configuring the Net.TCP Port Sharing Service</span></span>
<span data-ttu-id="4408f-103">Serviços de hospedagem interna que usam o transporte de NET. TCP podem controlar várias configurações avançadas, como `ListenBacklog` e `MaxPendingAccepts`, que determinam o comportamento de soquete TCP subjacente usado para comunicação de rede.</span><span class="sxs-lookup"><span data-stu-id="4408f-103">Self-hosted services that use the Net.TCP transport can control several advanced settings, such as `ListenBacklog` and `MaxPendingAccepts`, which govern the behavior of the underlying TCP socket used for network communication.</span></span> <span data-ttu-id="4408f-104">No entanto, essas configurações para cada soquete se aplicam somente no nível de associação se a associação de transporte tiver desabilitado o compartilhamento de porta, que é habilitado por padrão.</span><span class="sxs-lookup"><span data-stu-id="4408f-104">However, these settings for each socket only apply at the binding level if the transport binding has disabled port sharing, which is enabled by default.</span></span>  
  
 <span data-ttu-id="4408f-105">Quando uma associação de NET. TCP habilita o compartilhamento de porta (definindo `portSharingEnabled =true` no elemento de associação de transporte), ele implicitamente permite que um processo externo (ou seja, o SMSvcHost.exe, que hospeda o serviço de compartilhamento de porta NET. TCP) para gerenciar o soquete TCP em seu nome.</span><span class="sxs-lookup"><span data-stu-id="4408f-105">When a net.tcp binding enables port sharing (by setting `portSharingEnabled =true` on the transport binding element), it implicitly allows an external process (namely the SMSvcHost.exe, which hosts the Net.TCP Port Sharing Service) to manage the TCP socket on its behalf.</span></span> <span data-ttu-id="4408f-106">Por exemplo, ao usar TCP, especifique:</span><span class="sxs-lookup"><span data-stu-id="4408f-106">For example, when using TCP, specify:</span></span>  
  
```xml  
    <tcpTransport   
        portSharingEnabled="true"  
/>  
```  
  
 <span data-ttu-id="4408f-107">Quando configurado dessa forma, as configurações de soquete especificadas no elemento de associação de transporte do serviço são ignoradas em favor as configurações de soquete especificadas pelo SMSvcHost.exe.</span><span class="sxs-lookup"><span data-stu-id="4408f-107">When configured in this way, any socket settings specified on the service's transport binding element are ignored in favor of the socket settings specified by SMSvcHost.exe.</span></span>  
  
 <span data-ttu-id="4408f-108">Para configurar o SMSvcHost.exe, crie um arquivo de configuração XML chamado SMSvcHost.exe e coloque-o no mesmo diretório físico do executável de SMSvcHost.exe (por exemplo, C:\Windows\Microsoft.NET\Framework\v4.5).</span><span class="sxs-lookup"><span data-stu-id="4408f-108">To configure the SMSvcHost.exe, create an XML configuration file named SmSvcHost.exe.config and place it in the same physical directory as the SMSvcHost.exe executable (for example, C:\Windows\Microsoft.NET\Framework\v4.5).</span></span>  
  
 <span data-ttu-id="4408f-109">O exemplo a seguir ilustra um exemplo de SMSvcHost.exe, com as configurações padrão para todos os valores configuráveis declaradas explicitamente.</span><span class="sxs-lookup"><span data-stu-id="4408f-109">The following example illustrates a sample SMSvcHost.exe.config, with the default settings for all configurable values stated explicitly.</span></span>  
  
```xml  
<configuration>  
   <system.serviceModel.activation>  
       <net.tcp listenBacklog="16" <!—16 * # of processors -->  
          maxPendingAccepts="4"<!— 4 * # of processors -->  
          maxPendingConnections="100"  
          receiveTimeout="00:00:30" <!—30 seconds -->  
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
  
## <a name="when-to-modify-smsvchostexeconfig"></a><span data-ttu-id="4408f-110">Quando modificar SMSvcHost.exe</span><span class="sxs-lookup"><span data-stu-id="4408f-110">When to Modify SMSvcHost.exe.config</span></span>  
 <span data-ttu-id="4408f-111">Em geral, tome cuidado ao modificar o conteúdo do arquivo SMSvcHost.exe, porque todas as configurações especificadas neste arquivo afetam todos os serviços em um computador que usa o serviço de compartilhamento de porta NET. TCP.</span><span class="sxs-lookup"><span data-stu-id="4408f-111">In general, care should be taken when modifying the contents of the SMSvcHost.exe.config file, because any configuration settings specified in this file affect all of the services on a computer that uses the Net.TCP Port Sharing Service.</span></span> <span data-ttu-id="4408f-112">Isso inclui aplicativos em [!INCLUDE[wv](../../../../includes/wv-md.md)] que usam os recursos de ativação TCP de serviço de ativação de processos do Windows (WAS).</span><span class="sxs-lookup"><span data-stu-id="4408f-112">This includes applications on [!INCLUDE[wv](../../../../includes/wv-md.md)] that use the TCP Activation features of the Windows Process Activation Service (WAS).</span></span>  
  
 <span data-ttu-id="4408f-113">No entanto, às vezes, você precisará alterar a configuração padrão para o serviço de compartilhamento de porta NET. TCP.</span><span class="sxs-lookup"><span data-stu-id="4408f-113">However, sometimes you may need to change the default configuration for the Net.TCP Port Sharing Service.</span></span> <span data-ttu-id="4408f-114">Por exemplo, o valor padrão para `maxPendingAccepts` é 4 * número de processadores.</span><span class="sxs-lookup"><span data-stu-id="4408f-114">For example, the default value for `maxPendingAccepts` is 4 * number of processors.</span></span> <span data-ttu-id="4408f-115">Servidores que hospedam um grande número de serviços que usam o compartilhamento de porta podem aumentar esse valor para atingir a taxa de transferência máxima.</span><span class="sxs-lookup"><span data-stu-id="4408f-115">Servers that host a large number of services that use port sharing may increase this value to achieve maximum throughput.</span></span> <span data-ttu-id="4408f-116">O valor padrão para `maxPendingConnections` é 100.</span><span class="sxs-lookup"><span data-stu-id="4408f-116">The default value for `maxPendingConnections` is 100.</span></span> <span data-ttu-id="4408f-117">Você deve considerar o aumento desse valor também se há vários clientes simultâneos, chamar o serviço e o serviço está descartando as conexões de cliente.</span><span class="sxs-lookup"><span data-stu-id="4408f-117">You should consider increasing this value also if there are multiple concurrent clients calling the service and the service is dropping client connections.</span></span>  
  
 <span data-ttu-id="4408f-118">SMSvcHost.exe também contém informações sobre o processo de usam identidades que podem tornar a porta do serviço de compartilhamento.</span><span class="sxs-lookup"><span data-stu-id="4408f-118">SMSvcHost.exe.config also contains information about the process identities that may make use of the port sharing service.</span></span> <span data-ttu-id="4408f-119">Quando um processo se conecta à porta de serviço para usar um TCP compartilhado de compartilhamento de porta, a identidade do processo de conexão processo é verificado em relação uma lista de identidades que têm permissão para fazer uso do serviço de compartilhamento de porta.</span><span class="sxs-lookup"><span data-stu-id="4408f-119">When a process connects to the port sharing service to make use of a shared TCP port, the process identity of the connecting process is checked against a list of identities that are permitted to make use of the port sharing service.</span></span> <span data-ttu-id="4408f-120">Essas identidades são especificadas como identificadores de segurança (SIDs) no \<allowAccounts > seção do arquivo SMSvcHost.exe.</span><span class="sxs-lookup"><span data-stu-id="4408f-120">These identities are specified as security identifiers (SIDs) in the \<allowAccounts> section of the SMSvcHost.exe.config file.</span></span> <span data-ttu-id="4408f-121">Por padrão, a permissão para usar a serviço de compartilhamento de porta é concedida para contas do sistema (LocalService, sistema local e serviço de rede), bem como membros do grupo Administradores.</span><span class="sxs-lookup"><span data-stu-id="4408f-121">By default, permission to use the port sharing service is granted to system accounts (LocalService, LocalSystem, and NetworkService) as well as members of the Administrators group.</span></span> <span data-ttu-id="4408f-122">Aplicativos que permitem que um processo em execução como a identidade de outra (por exemplo, uma identidade de usuário) para se conectar ao serviço de compartilhamento de porta devem adicionar explicitamente o SID apropriado para o SMSvcHost.exe (essas alterações não são aplicadas até que o processo de SMSvc.exe reiniciar).</span><span class="sxs-lookup"><span data-stu-id="4408f-122">Applications that allow a process running as another identity (for example, a user identity) to connect to the port sharing service must explicitly add the appropriate SID to the SMSvcHost.exe.config (these changes are not applied until the SMSvc.exe process is restarted).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4408f-123">Em [!INCLUDE[wv](../../../../includes/wv-md.md)] sistemas com User Account Control (UAC) habilitados, o locais de usuários exigem permissões elevadas mesmo se sua conta é membro do grupo Administradores.</span><span class="sxs-lookup"><span data-stu-id="4408f-123">On [!INCLUDE[wv](../../../../includes/wv-md.md)] systems with User Account Control (UAC) enabled, local users require elevated permissions even if their account is a member of the Administrators group.</span></span> <span data-ttu-id="4408f-124">Para permitir que esses usuários façam uso da porta de serviço sem elevação de privilégio, o SID do usuário (ou o SID de um grupo no qual o usuário é um membro) de compartilhamento deve ser adicionado explicitamente para o \<allowAccounts > seção de SMSvcHost.exe.</span><span class="sxs-lookup"><span data-stu-id="4408f-124">To allow these users to make use of the port sharing service without elevation, the user's SID (or the SID of a group in which the user is a member) must be explicitly added to the \<allowAccounts> section of SMSvcHost.exe.config.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="4408f-125">O arquivo de SMSvcHost.exe padrão especifica um personalizado `etwProviderId` para impedir que o rastreamento de SMSvcHost.exe de interferir com rastreamentos de serviço.</span><span class="sxs-lookup"><span data-stu-id="4408f-125">The default SMSvcHost.exe.config file specifies a custom `etwProviderId` to prevent SMSvcHost.exe tracing from interfering with service traces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4408f-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4408f-126">See Also</span></span>  
 [<span data-ttu-id="4408f-127">\<NET. TCP ></span><span class="sxs-lookup"><span data-stu-id="4408f-127">\<net.tcp></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/net-tcp.md)
