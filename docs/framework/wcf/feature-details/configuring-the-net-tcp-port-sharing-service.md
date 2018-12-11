---
title: Configurando o serviço de compartilhamento de porta Net.TCP
ms.date: 03/30/2017
ms.assetid: b6dd81fa-68b7-4e1b-868e-88e5901b7ea0
ms.openlocfilehash: 7232fc587aa7f63167034f7474d6c5e7476048ed
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53153469"
---
# <a name="configuring-the-nettcp-port-sharing-service"></a>Configurando o serviço de compartilhamento de porta Net.TCP
Os serviços são hospedados que usam o transporte NET. TCP podem controlar várias configurações avançadas, como `ListenBacklog` e `MaxPendingAccepts`, que determinam o comportamento de soquete TCP subjacente usado para comunicação de rede. No entanto, essas configurações para cada soquete só se aplicam no nível de associação se a associação de transporte tiver desabilitado o compartilhamento de porta, que é habilitado por padrão.  
  
 Quando uma associação de NET. TCP habilita o compartilhamento de porta (definindo `portSharingEnabled =true` no elemento de associação de transporte), ele permite implicitamente que um processo externo (ou seja, o SMSvcHost.exe, que hospeda o serviço de compartilhamento de porta NET. TCP) para gerenciar o soquete TCP em seu nome. Por exemplo, ao usar TCP, especifique:  
  
```xml  
<tcpTransport portSharingEnabled="true"  />  
```  
  
 Quando configurado dessa forma, as configurações de soquete especificadas no elemento de associação de transporte do serviço são ignoradas em favor das configurações de soquete especificadas pelo SMSvcHost.exe.  
  
 Para configurar o SMSvcHost.exe, crie um arquivo de configuração XML chamado SMSvcHost e coloque-o no mesmo diretório físico do executável SMSvcHost.exe (por exemplo, C:\Windows\Microsoft.NET\Framework\v4.5).  
  
 O exemplo a seguir ilustra um exemplo de SMSvcHost, com as configurações padrão para todos os valores configuráveis declarados explicitamente.  
  
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
  
## <a name="when-to-modify-smsvchostexeconfig"></a>Quando modificar SMSvcHost  
 Em geral, tome cuidado ao modificar o conteúdo do arquivo de SMSvcHost, porque as definições de configuração especificadas neste arquivo afetam todos os serviços em um computador que usa o serviço de compartilhamento de porta NET. TCP. Isso inclui aplicativos no [!INCLUDE[wv](../../../../includes/wv-md.md)] que usam os recursos de ativação de TCP de serviço de ativação de processos para Windows (WAS).  
  
 No entanto, às vezes, você talvez precise alterar a configuração padrão para o serviço de compartilhamento de porta NET. TCP. Por exemplo, o valor padrão para `maxPendingAccepts` é 4 * número de processadores. Servidores que hospedam um grande número de serviços que usam o compartilhamento de porta podem aumentar esse valor para atingir a taxa de transferência máxima. O valor padrão para `maxPendingConnections` é 100. Você deve considerar aumentar esse valor também se há vários clientes simultâneos para chamar o serviço e o serviço está descartando as conexões de cliente.  
  
 SMSvcHost também contém informações sobre o processo de usarem identidades que podem tornar da porta de serviço de compartilhamento. Quando um processo se conecta à porta de serviço para utilizar um TCP compartilhado de compartilhamento de porta, a identidade do processo da conexão processo é verificado em relação uma lista de identidades têm permissão para fazer uso do serviço de compartilhamento de porta. Essas identidades são especificadas como identificadores de segurança (SIDs) na \<allowAccounts > seção do arquivo de SMSvcHost. Por padrão, a permissão para usar a serviço de compartilhamento de porta é concedida para contas do sistema (LocalService, LocalSystem e NetworkService), bem como membros do grupo Administradores. Aplicativos que permitem que um processo em execução como outra identidade (por exemplo, uma identidade de usuário) para se conectar ao serviço de compartilhamento de porta devem adicionar explicitamente o SID apropriado para o SMSvcHost (essas alterações não serão aplicadas até que o processo de SMSvc.exe é reiniciado).  
  
> [!NOTE]
>  Em [!INCLUDE[wv](../../../../includes/wv-md.md)] sistemas com User Account Control (UAC) habilitados, o locais de usuários exigem permissões elevadas, mesmo se sua conta é membro do grupo Administradores. Para permitir que esses usuários fazer uso do serviço sem a elevação de privilégio, o SID do usuário (ou o SID de um grupo no qual o usuário é membro) de compartilhamento de porta deve ser adicionado explicitamente para o \<allowAccounts > seção do SMSvcHost.  
  
> [!WARNING]
>  O arquivo de SMSvcHost padrão especifica um personalizado `etwProviderId` para impedir que o rastreamento SMSvcHost.exe interfira com rastreamentos de serviço.  
  
## <a name="see-also"></a>Consulte também  
 [\<NET. TCP >](../../../../docs/framework/configure-apps/file-schema/wcf/net-tcp.md)
