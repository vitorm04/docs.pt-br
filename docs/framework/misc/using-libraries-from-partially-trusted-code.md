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
ms.openlocfilehash: 6d858ef4c2f70c55b0a36e845f90d9a8e08f5e2d
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66487816"
---
# <a name="using-libraries-from-partially-trusted-code"></a>Usando bibliotecas de código parcialmente confiável
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
> [!NOTE]
>  Este tópico aborda o comportamento de assemblies de nome forte e só se aplica ao [nível 1](../../../docs/framework/misc/security-transparent-code-level-1.md) assemblies. [Código transparente de segurança, nível 2](../../../docs/framework/misc/security-transparent-code-level-2.md) assemblies no .NET Framework 4 ou posterior não são afetados por nomes fortes. Para obter mais informações sobre as alterações no sistema de segurança, consulte [alterações de segurança](../../../docs/framework/security/security-changes.md).  
  
 Aplicativos que recebem menos do que a relação de confiança total do seu host ou de área restrita não têm permissão para chamar compartilhado bibliotecas gerenciadas, a menos que o escritor da biblioteca permita, especificamente por meio do uso do <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atributo. Portanto, os criadores de aplicativo devem estar cientes de que algumas bibliotecas não estarão disponíveis a eles em um contexto parcialmente confiável. Por padrão, todo o código que é executado em uma confiança parcial [área restrita](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md) e não é a lista de assemblies de confiança total é parcialmente confiável. Se você não espera que seu código deve ser executado em um contexto parcialmente confiável ou ser chamado por código parcialmente confiável, você não precisa se preocupar com as informações nesta seção. No entanto, se você escrever código que deve interagir com código parcialmente confiável ou que operam em um contexto parcialmente confiável, você deve considerar os seguintes fatores:  
  
- Bibliotecas devem ser assinadas com um nome forte para serem compartilhados por vários aplicativos. Nomes fortes permitem que seu código seja colocado no cache de assembly global ou adicionado à lista de confiança total de um modo seguro <xref:System.AppDomain>, e permitir que os consumidores verificar se uma determinada parte do código móvel realmente provém de você.  
  
- Por padrão, nome forte [nível 1](../../../docs/framework/misc/security-transparent-code-level-1.md) bibliotecas compartilhadas executam implícito [LinkDemand](../../../docs/framework/misc/link-demands.md) completa confiar automaticamente, sem o escritor da biblioteca precisar fazer nada.  
  
- Se um chamador não tem confiança total, mas ainda tenta chamar uma biblioteca, o tempo de execução gera uma <xref:System.Security.SecurityException> e o chamador não tem permissão para vincular à biblioteca.  
  
- Para desabilitar o automático **LinkDemand** e impede que a exceção sendo lançada, você pode colocar o **AllowPartiallyTrustedCallersAttribute** atributo no assembly escopo compartilhado biblioteca. Este atributo permite suas bibliotecas a ser chamado do código gerenciado parcialmente confiável.  
  
- Código parcialmente confiável que é concedido acesso a uma biblioteca com esse atributo ainda está sujeito à mais restrições definidas pelo <xref:System.AppDomain>.  
  
- Não há nenhuma maneira programático para código parcialmente confiável chamar uma biblioteca que não tem o **AllowPartiallyTrustedCallersAttribute** atributo.  
  
 As bibliotecas que são particulares a um aplicativo específico não exigem um nome forte ou o **AllowPartiallyTrustedCallersAttribute** de atributo e não pode ser referenciado pelo código potencialmente mal-intencionado fora do aplicativo. Esse código é protegido contra uso indevido intencional ou não pelo código parcialmente confiável de móvel sem que o desenvolvedor que precise fazer nada extra.  
  
 Você deve considerar habilitar explicitamente o uso pelo código parcialmente confiável para os seguintes tipos de código:  
  
- Código que foi testado cuidadosamente para vulnerabilidades de segurança e está em conformidade com as diretrizes descritas em [diretrizes de codificação segura](../../../docs/standard/security/secure-coding-guidelines.md).  
  
- Bibliotecas de código de nome forte que são escritas especificamente para cenários parcialmente confiáveis.  
  
- Todos os componentes (seja parcial ou totalmente confiável) assinado com um nome forte que será chamado pelo código que é baixado da Internet.  
  
> [!NOTE]
>  Algumas classes na biblioteca de classes do .NET Framework não tem o **AllowPartiallyTrustedCallersAttribute** de atributo e não pode ser chamado pelo código parcialmente confiável.  
  
## <a name="see-also"></a>Consulte também

- [Segurança de acesso do código](../../../docs/framework/misc/code-access-security.md)
