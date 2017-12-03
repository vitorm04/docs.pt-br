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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0932494e1d64192070db0177c35b4eb03496bebb
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="configuring-the-nettcp-port-sharing-service"></a>Configurando o serviço de compartilhamento de porta Net.TCP
Serviços de hospedagem interna que usam o transporte de NET. TCP podem controlar várias configurações avançadas, como `ListenBacklog` e `MaxPendingAccepts`, que determinam o comportamento de soquete TCP subjacente usado para comunicação de rede. No entanto, essas configurações para cada soquete se aplicam somente no nível de associação se a associação de transporte tiver desabilitado o compartilhamento de porta, que é habilitado por padrão.  
  
 Quando uma associação de NET. TCP habilita o compartilhamento de porta (definindo `portSharingEnabled =true` no elemento de associação de transporte), ele implicitamente permite que um processo externo (ou seja, o SMSvcHost.exe, que hospeda o serviço de compartilhamento de porta NET. TCP) para gerenciar o soquete TCP em seu nome. Por exemplo, ao usar TCP, especifique:  
  
```xml  
    <tcpTransport   
        portSharingEnabled="true"  
/>  
```  
  
 Quando configurado dessa forma, as configurações de soquete especificadas no elemento de associação de transporte do serviço são ignoradas em favor as configurações de soquete especificadas pelo SMSvcHost.exe.  
  
 Para configurar o SMSvcHost.exe, crie um arquivo de configuração XML chamado SMSvcHost.exe e coloque-o no mesmo diretório físico do executável de SMSvcHost.exe (por exemplo, C:\Windows\Microsoft.NET\Framework\v4.5).  
  
 O exemplo a seguir ilustra um exemplo de SMSvcHost.exe, com as configurações padrão para todos os valores configuráveis declaradas explicitamente.  
  
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
  
## <a name="when-to-modify-smsvchostexeconfig"></a>Quando modificar SMSvcHost.exe  
 Em geral, tome cuidado ao modificar o conteúdo do arquivo SMSvcHost.exe, porque todas as configurações especificadas neste arquivo afetam todos os serviços em um computador que usa o serviço de compartilhamento de porta NET. TCP. Isso inclui aplicativos em [!INCLUDE[wv](../../../../includes/wv-md.md)] que usam os recursos de ativação TCP de serviço de ativação de processos do Windows (WAS).  
  
 No entanto, às vezes, você precisará alterar a configuração padrão para o serviço de compartilhamento de porta NET. TCP. Por exemplo, o valor padrão para `maxPendingAccepts` é 4 * número de processadores. Servidores que hospedam um grande número de serviços que usam o compartilhamento de porta podem aumentar esse valor para atingir a taxa de transferência máxima. O valor padrão para `maxPendingConnections` é 100. Você deve considerar o aumento desse valor também se há vários clientes simultâneos, chamar o serviço e o serviço está descartando as conexões de cliente.  
  
 SMSvcHost.exe também contém informações sobre o processo de usam identidades que podem tornar a porta do serviço de compartilhamento. Quando um processo se conecta à porta de serviço para usar um TCP compartilhado de compartilhamento de porta, a identidade do processo de conexão processo é verificado em relação uma lista de identidades que têm permissão para fazer uso do serviço de compartilhamento de porta. Essas identidades são especificadas como identificadores de segurança (SIDs) no \<allowAccounts > seção do arquivo SMSvcHost.exe. Por padrão, a permissão para usar a serviço de compartilhamento de porta é concedida para contas do sistema (LocalService, sistema local e serviço de rede), bem como membros do grupo Administradores. Aplicativos que permitem que um processo em execução como a identidade de outra (por exemplo, uma identidade de usuário) para se conectar ao serviço de compartilhamento de porta devem adicionar explicitamente o SID apropriado para o SMSvcHost.exe (essas alterações não são aplicadas até que o processo de SMSvc.exe reiniciar).  
  
> [!NOTE]
>  Em [!INCLUDE[wv](../../../../includes/wv-md.md)] sistemas com User Account Control (UAC) habilitados, o locais de usuários exigem permissões elevadas mesmo se sua conta é membro do grupo Administradores. Para permitir que esses usuários façam uso da porta de serviço sem elevação de privilégio, o SID do usuário (ou o SID de um grupo no qual o usuário é um membro) de compartilhamento deve ser adicionado explicitamente para o \<allowAccounts > seção de SMSvcHost.exe.  
  
> [!WARNING]
>  O arquivo de SMSvcHost.exe padrão especifica um personalizado `etwProviderId` para impedir que o rastreamento de SMSvcHost.exe de interferir com rastreamentos de serviço.  
  
## <a name="see-also"></a>Consulte também  
 [\<NET. TCP >](../../../../docs/framework/configure-apps/file-schema/wcf/net-tcp.md)
