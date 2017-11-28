---
title: "Usando bibliotecas de código parcialmente confiável"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security [.NET Framework], partially trusted code
- partially trusted code
- partial trust
- AllowPartiallyTrustedCallersAttribute attribute
- code access security, partially trusted code
- APTCA
ms.assetid: dd66cd4c-b087-415f-9c3e-94e3a1835f74
caps.latest.revision: "25"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 7a452370df7c18f3e3f0190a14979099152485f9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="using-libraries-from-partially-trusted-code"></a>Usando bibliotecas de código parcialmente confiável
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
> [!NOTE]
>  Este tópico aborda o comportamento de assemblies de nomes fortes e aplica-se somente a [nível 1](../../../docs/framework/misc/security-transparent-code-level-1.md) assemblies. [Código transparente de segurança, nível 2](../../../docs/framework/misc/security-transparent-code-level-2.md) assemblies no [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] ou posterior, não são afetados por nomes fortes. Para obter mais informações sobre as alterações no sistema de segurança, consulte [alterações de segurança](../../../docs/framework/security/security-changes.md).  
  
 Aplicativos que recebem menos do que a confiança total do seu host ou de área restrita não tem permissão para chamar compartilhado bibliotecas gerenciadas, a menos que o gravador da biblioteca permita, especificamente, através do uso do <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atributo. Portanto, autores de aplicativos devem estar cientes de que algumas bibliotecas não estarão disponíveis para eles em um contexto parcialmente confiável. Por padrão, todo o código que que executa em uma confiança parcial [sandbox](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md) e não é a lista de assemblies de confiança total é parcialmente confiável. Se você não espera que seu código deve ser executado em um contexto parcialmente confiável ou ser chamado por código parcialmente confiável, você não precisa se preocupar com as informações nesta seção. No entanto, se você escrever código que deve interagir com código parcialmente confiável ou não funcione em um contexto parcialmente confiável, você deve considerar os seguintes fatores:  
  
-   Bibliotecas devem ser assinadas com um nome forte para ser compartilhado por vários aplicativos. Nomes fortes permitir que seu código seja colocado no cache de assembly global ou adicionado à lista de confiança total de um modo seguro <xref:System.AppDomain>, e permitem que os consumidores verificar se uma determinada parte do código móvel realmente provém de você.  
  
-   Por padrão, nomes fortes [nível 1](../../../docs/framework/misc/security-transparent-code-level-1.md) bibliotecas compartilhadas executam implícita [LinkDemand](../../../docs/framework/misc/link-demands.md) completa confiar automaticamente, sem o gravador da biblioteca precisar fazer algo.  
  
-   Se um chamador não tem a confiança total, mas ainda tenta chamar uma biblioteca, o tempo de execução lança um <xref:System.Security.SecurityException> e o chamador não tem permissão para vincular à biblioteca.  
  
-   Para desabilitar o automático **LinkDemand** e evitar a exceção de que está sendo lançada, você pode colocar o **AllowPartiallyTrustedCallersAttribute** atributo no escopo do assembly de compartilhado biblioteca. Este atributo permite suas bibliotecas ser chamado do código parcialmente confiável.  
  
-   Código parcialmente confiável que é concedido acesso a uma biblioteca com esse atributo é ainda sujeita a mais restrições definidas pelo <xref:System.AppDomain>.  
  
-   Não é possível através de programação para código parcialmente confiável chame uma biblioteca que não tem o **AllowPartiallyTrustedCallersAttribute** atributo.  
  
 Bibliotecas que são particulares a um aplicativo específico não exigem um nome forte ou **AllowPartiallyTrustedCallersAttribute** de atributos e não pode ser referenciado por códigos possivelmente mal-intencionados fora do aplicativo. Esse código está protegido contra uso indevido intencional ou não pelo código parcialmente confiável de móvel sem que o desenvolvedor precisar fazer mais nada.  
  
 Considere a possibilidade de habilitar explicitamente o uso por código parcialmente confiável para os seguintes tipos de código:  
  
-   Código que foi testado cuidadosamente quanto a vulnerabilidades de segurança e está em conformidade com as diretrizes descritas em [diretrizes de codificação segura](../../../docs/standard/security/secure-coding-guidelines.md).  
  
-   Bibliotecas de código fortes que são escritas especificamente para cenários parcialmente confiáveis.  
  
-   Todos os componentes (se parcialmente ou totalmente confiável) assinado com um nome forte que será chamado pelo código que é baixado da Internet.  
  
> [!NOTE]
>  Algumas classes na biblioteca de classes do .NET Framework não tem o **AllowPartiallyTrustedCallersAttribute** de atributos e não pode ser chamado por código parcialmente confiável.  
  
## <a name="see-also"></a>Consulte também  
 [Segurança de acesso do código](../../../docs/framework/misc/code-access-security.md)
