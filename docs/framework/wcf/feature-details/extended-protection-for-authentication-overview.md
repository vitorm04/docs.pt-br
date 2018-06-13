---
title: Proteção estendida para visão geral de autenticação
ms.date: 03/30/2017
ms.assetid: 3d2ceffe-a7bf-4bd9-a5a2-9406423bd7f8
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: fdf18564d3545e0061d8323e544aecfeed621d0c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33489977"
---
# <a name="extended-protection-for-authentication-overview"></a>Proteção estendida para visão geral de autenticação
Proteção estendida para autenticação ajuda a impedir ataques man-in-the-middle (MITM), em que um invasor intercepta as credenciais do cliente e encaminha-os para um servidor.  
  
 Considere um cenário com três participantes: um invasor, cliente e servidor. O servidor tem a URL `https://server`, enquanto que o invasor terá a URL `https://attacker`. O invasor truques do cliente para acessar o invasor, como se fosse o servidor. O invasor, em seguida, envia uma solicitação ao servidor. Se o invasor está tentando acessar um recurso seguro, o servidor responde ao invasor com um cabeçalho WWW-Authenticate. O invasor não tem as informações de autenticação, portanto, ele envia o cabeçalho WWW-Authenticate logon no cliente. O cliente envia o cabeçalho de autorização para o invasor, e o invasor envia o cabeçalho de logon no servidor e obtém acesso aos recursos de segurança usando as credenciais do cliente.  
  
 Atualmente, quando um aplicativo cliente autentica o servidor usando Kerberos, Digest ou NTLM usando HTTPS, primeiro é estabelecer um canal de segurança de nível de transporte (TLS) e a autenticação é feita usando esse canal. No entanto, não há nenhuma associação entre a chave de sessão gerada pelo protocolo (SSL) e a chave de sessão que é gerada durante a autenticação. Assim, no cenário anterior, se a comunicação ocorre por um TLS (como um canal HTTPS), existem dois canais SSL criados: um entre o cliente e o invasor e outra entre o invasor e o servidor. As credenciais do cliente são enviadas do cliente para o servidor pela primeira vez no canal SSL entre o cliente e o invasor e, em seguida, o canal entre o invasor e o servidor. Depois que as credenciais do cliente acessar o servidor, o servidor verifica as credenciais sem detectar que o canal em que essas credenciais foram enviadas originou-se com o invasor e não no cliente.  
  
 A solução é usar um canal externo protegida por TLS e um canal interno cliente autenticado e passar um canal de associação CBT (Token) para o servidor. Quando o CBT é uma propriedade do canal externa protegida por TLS e é usado para associar o canal externo para uma conversa no canal interno do cliente autenticado.  
  
 No cenário anterior, quando o CBT do canal TLS cliente invasor é mesclado com as informações de autorização que são enviadas ao servidor. Um servidor com reconhecimento de CBT compara o CBT contido nas informações de autenticação de cliente, que corresponde ao canal de invasor do cliente para o CBT anexado ao canal de servidor do invasor. Um CBT é específico para o destino do canal, para que o cliente-invasor CBT não coincide com o servidor de invasor CBT. Isso permite que o servidor detecta o ataque MITM e recusar a solicitação de autenticação.  
  
 O lado do cliente não requer qualquer configuração. Depois que o cliente foi atualizado para passar o CBT para o servidor, ele sempre faz isso. Se o servidor também foi atualizado, ele pode ser configurado para usar o CBT ou ignorá-lo. Se não tiver sido atualizado, ela será ignorada.  
  
 O servidor pode ter os seguintes níveis de proteção:  
  
-   nenhuma. Nenhuma validação de associação de canal é executada. Esse é o comportamento de todos os servidores que não foram atualizados.  
  
-   Parcial. Todos os clientes que foram atualizados devem fornecer informações de associação de canal para o servidor. Clientes que não foram atualizados não precisa fazer isso. Isso é uma opção intermediária que permite a compatibilidade de aplicativos.  
  
-   Completo. Todos os clientes devem fornecer informações de associação de canal. O servidor rejeita solicitações de autenticação de clientes que não faça isso.  
  
 Para obter mais informações, consulte o exemplo de proteção de CBT/estendida Win7.  
  
## <a name="see-also"></a>Consulte também  
 [Modelo de segurança para o Windows Server App Fabric](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
