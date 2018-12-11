---
title: Proteção estendida para visão geral de autenticação
ms.date: 03/30/2017
ms.assetid: 3d2ceffe-a7bf-4bd9-a5a2-9406423bd7f8
ms.openlocfilehash: 6063aa7093ed6c70e835364fdf5dd1c4293dd2eb
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53149738"
---
# <a name="extended-protection-for-authentication-overview"></a>Proteção estendida para visão geral de autenticação
Proteção estendida para autenticação ajuda a proteger contra ataques de (MITM) man-in-the-middle, nos quais um invasor intercepta as credenciais de um cliente e encaminha-as para um servidor.  
  
 Considere um cenário com três participantes: um cliente, o servidor e o invasor. O servidor tem a URL `https://server`, enquanto que o invasor tem a URL `https://attacker`. O invasor truques o cliente para acessar o invasor como se fosse o servidor. O invasor, em seguida, envia uma solicitação ao servidor. Se o invasor está tentando acessar um recurso seguro, o servidor responde ao invasor com um cabeçalho WWW-Authenticate. O invasor não tem as informações de autenticação, portanto, ele envia o cabeçalho WWW-Authenticate logon no cliente. O cliente envia o cabeçalho de autorização para o invasor e o invasor envia o cabeçalho de logon no servidor e obtém acesso aos recursos seguros usando as credenciais do cliente.  
  
 Atualmente, quando um aplicativo cliente se autentica no servidor usando Kerberos, Digest ou NTLM usando HTTPS, primeiro é estabelecer um canal de segurança de nível de transporte (TLS) e a autenticação é feita usando este canal. No entanto, não há nenhuma associação entre a chave de sessão gerada pelo protocolo (SSL) e a chave de sessão que é gerada durante a autenticação. Assim, no cenário anterior, se a comunicação ocorre via um TLS (por exemplo, um canal HTTPS), existem dois canais SSL criados: um entre o cliente e o invasor e outro entre o invasor e o servidor. As credenciais do cliente são enviadas do cliente ao servidor pela primeira vez no canal SSL entre o cliente e o invasor e, em seguida, no canal entre o invasor e o servidor. Depois que as credenciais do cliente acessar o servidor, o servidor verifica as credenciais sem detectar que o canal pelo qual essas credenciais foram enviadas originou-se com o invasor e não pelo cliente.  
  
 A solução é usar um canal externo protegido por TLS e um canal interno autenticado pelo cliente e para passar um canal de associação de Token (CBT) para o servidor. O CBT é uma propriedade do canal externo protegido por TLS e é usado para associar o canal externo para uma conversa sobre o canal interno autenticado pelo cliente.  
  
 No cenário anterior, o CBT do canal TLS cliente invasor é mesclado com as informações de autorização que são enviadas ao servidor. Um servidor compatível com o CBT compara o CBT contido nas informações de autenticação de cliente, que corresponde ao canal de cliente invasor, para o CBT anexado para o canal de servidor do invasor. Um CBT é específico para o destino do canal, portanto o CBT de invasor cliente não coincide com o CBT de invasor-server. Isso permite que o servidor de detectar um ataque MITM e se recusar a solicitação de autenticação.  
  
 O lado do cliente não exige qualquer parâmetro de configuração. Depois que o cliente foi atualizado para passar o CBT para o servidor, ele sempre faz isso. Se o servidor também foi atualizado, ele pode ser configurado para usar o CBT ou ignorá-lo. Se não tiver sido atualizado, ignorá-la.  
  
 O servidor pode ter os seguintes níveis de proteção:  
  
-   nenhuma. Nenhuma validação de associação de canal é executada. Esse é o comportamento de todos os servidores que não foram atualizados.  
  
-   Parcial. Todos os clientes que foram atualizados devem fornecer informações de associação de canal para o servidor. Os clientes que não foram atualizados não é necessário fazê-lo. Isso é uma opção intermediária que permite a compatibilidade de aplicativos.  
  
-   Completo. Todos os clientes devem fornecer informações de associação de canal. O servidor rejeita solicitações de autenticação de clientes que não faça isso.  
  
 Para obter mais informações, consulte o exemplo de proteção de CBT/estendida Win7.  
  
## <a name="see-also"></a>Consulte também  
 [Modelo de segurança do Windows Server App Fabric](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
