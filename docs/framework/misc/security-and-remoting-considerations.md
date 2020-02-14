---
title: Considerações sobre segurança e comunicação remota
ms.date: 03/30/2017
helpviewer_keywords:
- code security, remoting
- remoting, security
- security [.NET Framework], remoting
- secure coding, remoting
ms.assetid: 125d2ab8-55a4-4e5f-af36-a7d401a37ab0
ms.openlocfilehash: 7a56c9894da88382f40dcd475e89776a83a59322
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77215777"
---
# <a name="security-and-remoting-considerations"></a>Considerações sobre segurança e comunicação remota
A comunicação remota permite que você configure a chamada transparente entre domínios de aplicativo, processos ou computadores. No entanto, a movimentação de pilha de segurança de acesso ao código não pode cruzar os limites do processo ou da máquina (ela se aplica entre os domínios do aplicativo do mesmo processo).  
  
 Qualquer classe que seja remota (derivada de uma classe <xref:System.MarshalByRefObject>) precisa assumir a responsabilidade pela segurança. O código deve ser usado somente em ambientes fechados em que o código de chamada pode ser implicitamente confiável, ou as chamadas remotas devem ser projetadas para que não sejam sujeitas a código protegido a entradas externas que poderiam ser usadas maliciosamente.  
  
 Geralmente, você nunca deve expor métodos, propriedades ou eventos que são protegidos por [LinkDemand](link-demands.md) declarativo e <xref:System.Security.Permissions.SecurityAction.InheritanceDemand> verificações de segurança. Com a comunicação remota, essas verificações não são impostas. Outras verificações de segurança, como <xref:System.Security.Permissions.SecurityAction.Demand>, [Assert](using-the-assert-method.md)e assim por diante, funcionam entre domínios de aplicativo dentro de um processo, mas não funcionam em cenários de processo cruzado ou entre máquinas.  
  
## <a name="protected-objects"></a>Objetos protegidos  
 Alguns objetos mantêm o estado de segurança em si. Esses objetos não devem ser passados para código não confiável, o que, por sua conta, adquiriria a autorização de segurança além de suas próprias permissões.  
  
 Um exemplo é a criação de um objeto de <xref:System.IO.FileStream>. A <xref:System.Security.Permissions.FileIOPermission> é solicitada no momento da criação e, se tiver sucesso, o objeto de arquivo será retornado. No entanto, se essa referência de objeto for passada para o código sem permissões de arquivo, o objeto poderá ler e gravar nesse arquivo específico.  
  
 A defesa mais simples para tal objeto é exigir a mesma **FileIOPermission** de qualquer código que busca obter a referência de objeto por meio de um elemento de API pública.  
  
## <a name="application-domain-crossing-issues"></a>Problemas de cruzamento de domínio de aplicativo  
 Para isolar o código em ambientes de hospedagem gerenciados, é comum gerar vários domínios de aplicativo filho com política explícita, reduzindo os níveis de permissão para vários assemblies. No entanto, a política para esses assemblies permanece inalterada no domínio do aplicativo padrão. Se um dos domínios do aplicativo filho puder forçar o domínio de aplicativo padrão a carregar um assembly, o efeito do isolamento de código será perdido e os tipos no assembly de tentativa forçado poderão executar o código em um nível mais alto de confiança.  
  
 Um domínio de aplicativo pode forçar outro domínio de aplicativo a carregar um assembly e executar o código contido nele chamando um proxy para um objeto hospedado no outro domínio de aplicativo. Para obter um proxy de domínio entre aplicativos, o domínio do aplicativo que hospeda o objeto deve distribuir um por meio de um parâmetro de chamada de método ou valor de retorno. Ou, se o domínio do aplicativo acabou de ser criado, o criador tem um proxy para o objeto <xref:System.AppDomain> por padrão. Portanto, para evitar a interrupção do isolamento de código, um domínio de aplicativo com um nível mais alto de confiança não deve distribuir referências a objetos de marshaling por referência (instâncias de classes derivadas de <xref:System.MarshalByRefObject>) em seu domínio para domínios de aplicativo com níveis inferiores de confiança.  
  
 Normalmente, o domínio de aplicativo padrão cria os domínios de aplicativo filho com um objeto de controle em cada um. O objeto Control gerencia o novo domínio de aplicativo e, eventualmente, recebe pedidos do domínio de aplicativo padrão, mas não pode realmente entrar em contato diretamente com o domínio. Ocasionalmente, o domínio de aplicativo padrão chama seu proxy para o objeto de controle. No entanto, pode haver casos em que é necessário que o objeto de controle chame de volta para o domínio de aplicativo padrão. Nesses casos, o domínio de aplicativo padrão passa um objeto de retorno de chamada Marshal-by-reference para o construtor do objeto de controle. É responsabilidade do objeto de controle proteger esse proxy. Se o objeto de controle fosse colocar o proxy em um campo estático público de uma classe pública ou expor publicamente o proxy, isso abriria um mecanismo perigoso para que outro código chame de volta no domínio de aplicativo padrão. Por esse motivo, os objetos de controle sempre são implicitamente confiáveis para manter o proxy privado.  
  
## <a name="see-also"></a>Confira também

- [Diretrizes de codificação segura](../../standard/security/secure-coding-guidelines.md)
