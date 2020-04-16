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
# <a name="configuring-the-nettcp-port-sharing-service"></a>Configurando o serviço de compartilhamento de porta Net.TCP
Os serviços auto-hospedados que usam o transporte Net.TCP `ListenBacklog` `MaxPendingAccepts`podem controlar várias configurações avançadas, como e , que regem o comportamento do soquete TCP subjacente usado para comunicação de rede. No entanto, essas configurações para cada soquete só se aplicam no nível de vinculação se a vinculação de transporte tiver desativado o compartilhamento de porta, que é habilitado por padrão.  
  
 Quando uma vinculação net.tcp permite `portSharingEnabled =true` o compartilhamento de portas (configurando no elemento de vinculação de transporte), ele permite implicitamente que um processo externo (ou seja, o SMSvcHost.exe, que hospeda o Serviço de Compartilhamento de Portas Net.TCP) gerencie o soquete TCP em seu nome. Por exemplo, ao usar o TCP, especifique:  
  
```xml  
<tcpTransport portSharingEnabled="true"  />  
```  
  
 Quando configurado desta forma, quaisquer configurações de soquete especificadas no elemento de vinculação de transporte do serviço são ignoradas em favor das configurações de soquete especificadas pelo SMSvcHost.exe.  
  
 Para configurar o SMSvcHost.exe, crie um arquivo de configuração XML chamado SmSvcHost.exe.config e coloque-o no mesmo diretório físico que o Executável SMSvcHost.exe (por exemplo, C:\Windows\Microsoft.NET\Framework\v4.5).  
  
 O exemplo a seguir ilustra uma amostra SMSvcHost.exe.config, com as configurações padrão para todos os valores configuráveis indicados explicitamente.  
  
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
  
## <a name="when-to-modify-smsvchostexeconfig"></a>Quando modificar smsvcHost.exe.config  
 Em geral, deve-se tomar cuidado ao modificar o conteúdo do arquivo SMSvcHost.exe.config, pois quaisquer configurações especificadas neste arquivo afetam todos os serviços em um computador que usa o Serviço de Compartilhamento de Portas Net.TCP. Isso inclui aplicativos no Windows Vista que usam os recursos de ativação TCP do Serviço de Ativação de Processos do Windows (WAS).  
  
 No entanto, às vezes, você pode precisar alterar a configuração padrão para o Serviço de Compartilhamento de Portas Net.TCP. Por exemplo, o `maxPendingAccepts` valor padrão para é 4 * número de processadores. Os servidores que hospedam um grande número de serviços que usam o compartilhamento de portas podem aumentar esse valor para atingir o máximo de throughput. O valor `maxPendingConnections` padrão para é 100. Você deve considerar aumentar esse valor também se houver vários clientes simultâneos ligando para o serviço e o serviço está diminuindo as conexões com clientes.  
  
 O SMSvcHost.exe.config também contém informações sobre as identidades do processo que podem fazer uso do serviço de compartilhamento de portas. Quando um processo se conecta ao serviço de compartilhamento de portas para fazer uso de uma porta TCP compartilhada, a identidade do processo de conexão é verificada em uma lista de identidades que são permitidas para fazer uso do serviço de compartilhamento de portas. Essas identidades são especificadas como identificadores de segurança \<(SIDs) na seção permitirContas> do arquivo SMSvcHost.exe.config. Por padrão, a permissão para usar o serviço de compartilhamento de portas é concedida às contas do sistema (LocalService, LocalSystem e NetworkService), bem como aos membros do grupo Administradores. Os aplicativos que permitem que um processo executado como outra identidade (por exemplo, uma identidade de usuário) se conecte ao serviço de compartilhamento de portas deve adicionar explicitamente o SID apropriado ao SMSvcHost.exe.config (essas alterações não são aplicadas até que o processo SMSvc.exe seja reiniciado).  
  
> [!NOTE]
> Nos sistemas Windows Vista com controle de conta de usuário (UAC) ativados, os usuários locais exigem permissões elevadas, mesmo que sua conta seja um membro do grupo Administradores. Para permitir que esses usuários façam uso do serviço de compartilhamento de portas sem elevação, o SID do usuário (ou o SID de um grupo no qual o usuário é membro) deve ser explicitamente adicionado à seção \<de> de Contas permitidas do SMSvcHost.exe.config.  
  
> [!WARNING]
> O arquivo padrão SMSvcHost.exe.config `etwProviderId` especifica um costume para impedir que o rastreamento smsvcHost.exe interfira em rastreamentos de serviços.  
  
## <a name="see-also"></a>Confira também

- [\<net.tcp>](../../../../docs/framework/configure-apps/file-schema/wcf/net-tcp.md)
