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
ms.openlocfilehash: db4a5ee5673ef96c9fb7f39798ab32dd8c910f43
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="security-and-remoting-considerations"></a>Considerações sobre segurança e comunicação remota
Comunicação remota permite que você configure transparente chamadas entre domínios de aplicativo, processos ou computadores. No entanto, a movimentação da pilha código acesso segurança não pode ultrapassar os limites de processo ou máquinas (Aplicar entre domínios de aplicativos do mesmo processo).  
  
 Qualquer classe que é remota (derivado de um <xref:System.MarshalByRefObject> classe) deve assumir a responsabilidade de segurança. Tanto o código deve ser usado somente em ambientes fechados onde o código de chamada pode ser implicitamente confiável, ou chamadas de comunicação remota devem ser projetadas para que eles não sujeito código protegido a entrada externa que poderia ser usada maliciosamente.  
  
 Em geral, você deve expor nunca os métodos, propriedades ou eventos que são protegidos pelo declarativa [LinkDemand](../../../docs/framework/misc/link-demands.md) e <xref:System.Security.Permissions.SecurityAction.InheritanceDemand> verificações de segurança. Com a comunicação remota, essas verificações não são impostas. Verificações de outros dispositivos, como <xref:System.Security.Permissions.SecurityAction.Demand>, [Assert](../../../docs/framework/misc/using-the-assert-method.md), e assim por diante, entre domínios de aplicativo dentro de um processo de trabalho, mas não funcionam em cenários entre processos ou entre computadores.  
  
## <a name="protected-objects"></a>Objetos protegidos  
 Alguns objetos mantêm o estado de segurança em si. Esses objetos não devem ser passados para código não confiável, que, em seguida, poderia obter autorização de segurança além de suas próprias permissões.  
  
 Um exemplo é criar um <xref:System.IO.FileStream> objeto. O <xref:System.Security.Permissions.FileIOPermission> é exigida no momento da criação e, se for bem-sucedida, o objeto de arquivo é retornado. No entanto, se essa referência de objeto é passada para código sem permissões de arquivo, o objeto será capaz de ler e gravar este arquivo específico.  
  
 A defesa mais simples para tal objeto é solicitar o mesmo **FileIOPermission** de qualquer código que tenta obter a referência de objeto por meio de um elemento de API público.  
  
## <a name="application-domain-crossing-issues"></a>Problemas de cruzamento de domínio de aplicativo  
 Para isolar o código em ambientes de hospedagem gerenciados, é comum para gerar vários domínios de aplicativo filho com diretiva explícita, reduzindo os níveis de permissão para vários assemblies. No entanto, a política para esses assemblies permanece inalterada no domínio de aplicativo padrão. Se um dos domínios de aplicativo filho pode forçar o domínio de aplicativo padrão para carregar um assembly, o efeito de isolamento de código é perdido e tipos no assembly carregado forçado será capazes de executar código em um nível mais alto de confiança.  
  
 Um domínio de aplicativo pode forçar o outro domínio de aplicativo para carregar um assembly e executar código contido por um proxy para um objeto hospedado no domínio do aplicativo de chamada. Para obter um proxy entre domínios de aplicativo, o domínio de aplicativo que hospeda o objeto deve distribuir um a um valor de parâmetro ou retorno de chamada do método. Ou, se o domínio de aplicativo recém-criado, o criador de um proxy para o <xref:System.AppDomain> objeto por padrão. Portanto, para evitar a interrupção de isolamento de código, um domínio de aplicativo com um nível mais alto de confiança deve não distribuir as referências a objetos de marshaling por referência (instâncias de classes derivam de <xref:System.MarshalByRefObject>) em seu domínio para os domínios de aplicativo com inferior níveis de confiança.  
  
 Normalmente, o domínio de aplicativo padrão cria o filho domínios de aplicativo com um objeto de controle em cada uma. O objeto control gerencia o novo domínio de aplicativo e, ocasionalmente, leva pedidos do domínio de aplicativo padrão, mas que, na verdade, não é possível contatar o domínio diretamente. Ocasionalmente, o domínio de aplicativo padrão chama seu proxy para o objeto de controle. No entanto, pode haver casos em que é necessário para o objeto de controle para retorno de chamada para o domínio de aplicativo padrão. Nesses casos, o domínio de aplicativo padrão passa um objeto de retorno de chamada de marshaling por referência para o construtor do objeto de controle. É responsabilidade do objeto de controle para proteger esse proxy. Se o objeto control colocar o proxy em um campo estático público de uma classe pública ou expor publicamente o proxy, caso contrário, isso abriria um mecanismo perigoso para outro código de retorno de chamada para o domínio de aplicativo padrão. Por esse motivo, os objetos de controle são sempre implicitamente confiáveis para manter a privacidade do proxy.  
  
## <a name="see-also"></a>Consulte também  
 [Diretrizes de codificação segura](../../../docs/standard/security/secure-coding-guidelines.md)
