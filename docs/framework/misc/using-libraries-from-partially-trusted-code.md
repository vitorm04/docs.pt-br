---
title: Usando bibliotecas de código parcialmente confiável
ms.date: 03/30/2017
helpviewer_keywords:
- security [.NET Framework], partially trusted code
- partially trusted code
- partial trust
- AllowPartiallyTrustedCallersAttribute attribute
- code access security, partially trusted code
- APTCA
ms.assetid: dd66cd4c-b087-415f-9c3e-94e3a1835f74
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 50428e4e28df812a3a0c985d0d1876dab7b5279c
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70206032"
---
# <a name="using-libraries-from-partially-trusted-code"></a>Usando bibliotecas de código parcialmente confiável
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
> [!NOTE]
> Este tópico aborda o comportamento de assemblies com nomes fortes e aplica-se somente a assemblies de [nível 1](security-transparent-code-level-1.md) . O [código de segurança transparente,](security-transparent-code-level-2.md) os assemblies de nível 2 no .NET Framework 4 ou posterior não são afetados por nomes fortes. Para obter mais informações sobre alterações no sistema de segurança, consulte [alterações de segurança](../security/security-changes.md).  
  
 Os aplicativos que recebem menos do que a confiança total do host ou da área restrita não têm permissão para chamar bibliotecas gerenciadas compartilhadas, a menos que o gravador <xref:System.Security.AllowPartiallyTrustedCallersAttribute> de biblioteca permita especificamente o uso do atributo. Portanto, os gravadores de aplicativo devem estar cientes de que algumas bibliotecas não estarão disponíveis para eles por meio de um contexto parcialmente confiável. Por padrão, todo o código que é executado em uma [área](how-to-run-partially-trusted-code-in-a-sandbox.md) de segurança parcialmente confiável e que não está na lista de assemblies de confiança total é parcialmente confiável. Se você não espera que seu código seja executado a partir de um contexto parcialmente confiável ou que seja chamado por código parcialmente confiável, você não precisa se preocupar com as informações nesta seção. No entanto, se você escrever código que deve interagir com código parcialmente confiável ou operar de um contexto parcialmente confiável, considere os seguintes fatores:  
  
- As bibliotecas devem ser assinadas com um nome forte para serem compartilhadas por vários aplicativos. Nomes fortes permitem que seu código seja colocado no cache de assembly global ou adicionado à lista de confiança total de uma área restrita <xref:System.AppDomain>e permite que os consumidores verifiquem se um determinado código móvel realmente se origina de você.  
  
- Por padrão, as bibliotecas compartilhadas de [nível 1](security-transparent-code-level-1.md) de nome forte executam um [LinkDemand](link-demands.md) implícito para confiança total automaticamente, sem que o gravador de biblioteca tenha que fazer nada.  
  
- Se um chamador não tiver confiança total, mas ainda tentar chamar essa biblioteca, o tempo de execução lançará <xref:System.Security.SecurityException> um e o chamador não terá permissão para vincular à biblioteca.  
  
- Para desabilitar o **LinkDemand** automático e impedir que a exceção seja gerada, você pode posicionar o atributo **AllowPartiallyTrustedCallersAttribute** no escopo do assembly de uma biblioteca compartilhada. Esse atributo permite que suas bibliotecas sejam chamadas a partir de código gerenciado parcialmente confiável.  
  
- O <xref:System.AppDomain>código parcialmente confiável que recebe acesso a uma biblioteca com esse atributo ainda está sujeito a restrições adicionais definidas pelo.  
  
- Não há nenhuma maneira programática para código parcialmente confiável chamar uma biblioteca que não tem o atributo **AllowPartiallyTrustedCallersAttribute** .  
  
 As bibliotecas que são privadas para um aplicativo específico não exigem um nome forte ou o atributo **AllowPartiallyTrustedCallersAttribute** e não podem ser referenciadas por código potencialmente mal-intencionado fora do aplicativo. Esse código é protegido contra uso indevido intencional ou não intencional pelo código móvel parcialmente confiável, sem que o desenvolvedor precise fazer algo extra.  
  
 Você deve considerar habilitar explicitamente o uso por código parcialmente confiável para os seguintes tipos de código:  
  
- O código que foi testado de vulnerabilidades de segurança e está em conformidade com as diretrizes descritas em [diretrizes de codificação segura](../../standard/security/secure-coding-guidelines.md).  
  
- Bibliotecas de código de nome forte que são escritas especificamente para cenários parcialmente confiáveis.  
  
- Todos os componentes (parcialmente ou totalmente confiáveis) assinados com um nome forte que será chamado pelo código baixado da Internet.  
  
> [!NOTE]
> Algumas classes na biblioteca de classes de .NET Framework não têm o atributo **AllowPartiallyTrustedCallersAttribute** e não podem ser chamadas por código parcialmente confiável.  
  
## <a name="see-also"></a>Consulte também

- [Segurança de acesso do código](code-access-security.md)
