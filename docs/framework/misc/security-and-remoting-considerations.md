---
title: Considerações sobre segurança e comunicação remota
ms.date: 03/30/2017
helpviewer_keywords:
- code security, remoting
- remoting, security
- security [.NET Framework], remoting
- secure coding, remoting
ms.assetid: 125d2ab8-55a4-4e5f-af36-a7d401a37ab0
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 46e2e1c327a683782b68069ace2ad6c40bbc856e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59225281"
---
# <a name="security-and-remoting-considerations"></a>Considerações sobre segurança e comunicação remota
Comunicação remota permite que você configure transparente chamando entre domínios de aplicativos, processos ou computadores. No entanto, a movimentação de pilha de segurança de acesso de código não pode cruzar os limites de processo ou computadores (Aplicar entre domínios de aplicativo do mesmo processo).  
  
 Qualquer classe que é remota (derivado de um <xref:System.MarshalByRefObject> classe) precisa para assumir a responsabilidade pela segurança. Tanto o código deve ser usado somente em ambientes fechados em que o código de chamada pode ser implicitamente confiável, ou chamadas de comunicação remota devem ser projetadas para que eles não sujeito código protegido a entrada externa que poderia ser usada maliciosamente.  
  
 Em geral, você deve nunca exponha métodos, propriedades ou eventos que são protegidos pelo declarativa [LinkDemand](../../../docs/framework/misc/link-demands.md) e <xref:System.Security.Permissions.SecurityAction.InheritanceDemand> verificações de segurança. Com a comunicação remota, essas verificações não são impostas. Outro security verifica, tais como <xref:System.Security.Permissions.SecurityAction.Demand>, [Assert](../../../docs/framework/misc/using-the-assert-method.md)e assim por diante, funcionam entre domínios do aplicativo dentro de um processo, mas não funcionam em cenários entre processos ou entre computadores.  
  
## <a name="protected-objects"></a>Objetos protegidos  
 Alguns objetos mantêm o estado de segurança em si. Esses objetos não devem ser passados para código não confiável, que, em seguida, poderia adquirir a autorização de segurança, além de suas próprias permissões.  
  
 Um exemplo é criar um <xref:System.IO.FileStream> objeto. O <xref:System.Security.Permissions.FileIOPermission> é solicitada no momento da criação e, se tiver êxito, o objeto de arquivo é retornado. No entanto, se essa referência de objeto é passada para código sem permissões de arquivo, o objeto será capaz de ler e gravar nesse arquivo específico.  
  
 A defesa mais simples para esse objeto é solicitar o mesmo **FileIOPermission** de qualquer código que tenta obter a referência de objeto por meio de um elemento de API público.  
  
## <a name="application-domain-crossing-issues"></a>Problemas do cruzamento de domínio de aplicativo  
 Para isolar o código em ambientes de hospedagem gerenciadas, é comum gerar vários domínios de aplicativo filho com diretiva explícita, reduzindo os níveis de permissão para vários assemblies. No entanto, a política para esses assemblies permanece inalterada no domínio do aplicativo padrão. Se um dos domínios de aplicativo filho pode forçar o domínio de aplicativo padrão para carregar um assembly, o efeito de isolamento de código será perdido e os tipos no assembly carregado à força será capazes de executar código em um nível mais alto de confiança.  
  
 Um domínio de aplicativo pode forçar outro domínio de aplicativo para carregar um assembly e executar o código contido nele, chamando um proxy para um objeto hospedado no domínio do aplicativo. Para obter um proxy entre domínios de aplicativo, o domínio de aplicativo que hospeda o objeto deve distribuir o meio de um valor de parâmetro ou retorno de chamada do método. Ou, se o domínio do aplicativo acabou de ser criado, o criador tem um proxy para o <xref:System.AppDomain> objeto por padrão. Portanto, para evitar a interrupção de isolamento de código, um domínio de aplicativo com um nível mais alto de confiança deve não distribuir as referências a objetos de marshaling por referência (instâncias de classes derivam de <xref:System.MarshalByRefObject>) em seu domínio para domínios de aplicativo com inferior níveis de confiança.  
  
 Normalmente, o domínio de aplicativo padrão cria o filho domínios de aplicativo com um objeto de controle em cada um. O objeto de controle gerencia o novo domínio de aplicativo e, ocasionalmente, recebe pedidos de domínio de aplicativo padrão, mas ele não pode, na verdade, entre em contato com o domínio diretamente. Ocasionalmente, o domínio de aplicativo padrão chama seu proxy para o objeto de controle. No entanto, pode haver casos em que é necessário para o objeto de controle para o retorno de chamada para o domínio de aplicativo padrão. Nesses casos, o domínio de aplicativo padrão passa um objeto de retorno de chamada de marshaling por referência para o construtor do objeto de controle. É responsabilidade do objeto de controle para proteger esse proxy. Se o objeto de controle colocar o proxy em um campo estático público de uma classe pública ou expor publicamente o proxy, caso contrário, isso abriria um mecanismo perigoso para outro código de retorno de chamada no domínio de aplicativo padrão. Por esse motivo, os objetos de controle são sempre implicitamente confiáveis para manter o proxy particulares.  
  
## <a name="see-also"></a>Consulte também

- [Diretrizes de codificação segura](../../../docs/standard/security/secure-coding-guidelines.md)
