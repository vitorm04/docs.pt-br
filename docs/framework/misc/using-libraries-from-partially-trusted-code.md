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
ms.openlocfilehash: 61291a07639c3f92a05f78dff49f6b20f1aee77e
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645716"
---
# <a name="using-libraries-from-partially-trusted-code"></a>Usando bibliotecas de código parcialmente confiável
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
> [!NOTE]
> Este tópico aborda o comportamento de assembléias com nomes fortes e se aplica apenas a assembléias [de Nível 1.](security-transparent-code-level-1.md) [Código transparente de segurança,](security-transparent-code-level-2.md) conjuntos de nível 2 no .NET Framework 4 ou posterior esnobou não são afetados por nomes fortes. Para obter mais informações sobre alterações no sistema de segurança, consulte [Alterações de segurança](https://docs.microsoft.com/previous-versions/dotnet/framework/security/security-changes).  
  
 Aplicativos que recebem menos de confiança total de seu host ou caixa de areia não podem chamar bibliotecas gerenciadas <xref:System.Security.AllowPartiallyTrustedCallersAttribute> compartilhadas, a menos que o escritor da biblioteca permita especificamente que eles usem o atributo. Portanto, os autores de aplicativos devem estar cientes de que algumas bibliotecas não estarão disponíveis para eles a partir de um contexto parcialmente confiável. Por padrão, todo o código que é executado em uma caixa de [areia](how-to-run-partially-trusted-code-in-a-sandbox.md) de confiança parcial e não está na lista de conjuntos de confiança total é parcialmente confiável. Se você não espera que seu código seja executado a partir de um contexto parcialmente confiável ou seja chamado por código parcialmente confiável, você não precisa se preocupar com as informações nesta seção. No entanto, se você escrever código que deve interagir com código parcialmente confiável ou operar a partir de um contexto parcialmente confiável, você deve considerar os seguintes fatores:  
  
- As bibliotecas devem ser assinadas com um nome forte para serem compartilhadas por vários aplicativos. Nomes fortes permitem que seu código seja colocado no cache de montagem global <xref:System.AppDomain>ou adicionado à lista de confiança completa de um sandboxing , e permitem que os consumidores verifiquem se um determinado pedaço de código móvel realmente se origina de você.  
  
- Por padrão, bibliotecas compartilhadas de [nível 1](security-transparent-code-level-1.md) com nome forte executam um [LinkDemand](link-demands.md) implícito para total confiança automaticamente, sem que o escritor da biblioteca tenha que fazer nada.  
  
- Se um chamador não tiver total confiança, mas ainda tentar <xref:System.Security.SecurityException> chamar tal biblioteca, o tempo de execução lança um e o chamador não tem permissão para vincular à biblioteca.  
  
- Para desativar o **LinkDemand** automático e impedir que a exceção seja lançada, você pode colocar o atributo **AllowPartiallyTrustedCallersAttribute** no escopo de montagem de uma biblioteca compartilhada. Esse atributo permite que suas bibliotecas sejam chamadas de código gerenciado parcialmente confiável.  
  
- O código parcialmente confiável que é concedido acesso a uma biblioteca com <xref:System.AppDomain>esse atributo ainda está sujeito a novas restrições definidas pelo .  
  
- Não há nenhuma maneira programática para que o código parcialmente confiável ligue para uma biblioteca que não tenha o atributo **AllowPartiallyTrustedCallersAttribute.**  
  
 Bibliotecas privadas de um aplicativo específico não exigem um nome forte ou o atributo **AllowPartiallyTrustedCallersAttribute** e não podem ser referenciadas por código potencialmente malicioso fora do aplicativo. Esse código é protegido contra uso indevido intencional ou não por código móvel parcialmente confiável sem que o desenvolvedor tenha que fazer nada extra.  
  
 Você deve considerar a habilitação explícita do uso por código parcialmente confiável para os seguintes tipos de código:  
  
- Código que foi diligentemente testado para vulnerabilidades de segurança e está em conformidade com as diretrizes descritas em [Diretrizes de Codificação Segura](../../standard/security/secure-coding-guidelines.md).  
  
- Bibliotecas de código com nome forte que são especificamente escritas para cenários parcialmente confiáveis.  
  
- Quaisquer componentes (parcialmente ou totalmente confiáveis) assinados com um nome forte que será chamado por código que é baixado da Internet.  
  
> [!NOTE]
> Algumas classes na biblioteca de classes .NET Framework não têm o atributo **AllowPartiallyTrustedCallersAttribute** e não podem ser chamadas por código parcialmente confiável.  
  
## <a name="see-also"></a>Confira também

- [Segurança de acesso a código](code-access-security.md)
