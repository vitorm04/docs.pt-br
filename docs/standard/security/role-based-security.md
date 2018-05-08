---
title: Segurança baseada em função
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- role-based security, about role-based security
- user authentication, principals
- principals [.NET Framework]
- security [.NET Framework], role-based
- permissions [.NET Framework], principals
- authentication [.NET Framework], principals
- role-based security, principals
ms.assetid: 578cc32b-5654-4d8b-9d8c-ebcbc5c75390
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 596165bfac9c65898448714a4477b7f045bd87d7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="role-based-security"></a>Segurança baseada em função
Funções geralmente são usadas em aplicativos financeiros ou de negócios para impor a política. Por exemplo, um aplicativo pode impor limites de tamanho da transação que está sendo processada dependendo se o usuário que fez a solicitação é um membro de uma função especificada. Administradores podem ter autorização para processar as transações que são menores que o limite especificado, supervisores podem ter um limite superior e vice-presidentes podem ter um limite ainda maior (ou nenhum limite em todos os). Segurança baseada em função também pode ser usada quando um aplicativo requer vários aprovações para concluir uma ação. Caso seja um sistema de compras em que qualquer funcionário pode gerar uma solicitação de compra, mas apenas um agente de compras pode converter essa solicitação em uma ordem de compra que pode ser enviada para um fornecedor.  
  
 Segurança baseada em função do .NET framework oferece suporte à autorização, tornando as informações sobre a entidade de segurança, que é construída a partir de uma identidade associado, disponível para o thread atual. A identidade (e a entidade de segurança que ajuda a definir) seja baseadas em uma conta do Windows ou ser uma identidade personalizada não relacionada a uma conta do Windows. Aplicativos do .NET framework podem tomar decisões de autorização com base na identidade da entidade ou associação de função ou ambos. Uma função é um conjunto nomeado de entidades que têm os mesmos privilégios em relação à segurança (como uma caixa ou um gerente). Um objeto pode ser um membro de uma ou mais funções. Portanto, os aplicativos podem usar associação de função para determinar se uma entidade de segurança está autorizada a executar uma ação solicitada.  
  
 Para fornecer a facilidade de uso e consistência com a segurança de acesso do código, a segurança baseada em função do .NET Framework fornece <xref:System.Security.Permissions.PrincipalPermission?displayProperty=nameWithType> verificações de segurança de acesso a objetos que permitem que o common language runtime para executar a autorização de uma maneira que é semelhante ao código. O <xref:System.Security.Permissions.PrincipalPermission> classe representa a identidade ou a função que a entidade deve corresponder e é compatível com as verificações de segurança declarativa e fundamental. Você também pode acessar informações de identidade de uma entidade de segurança diretamente e executar funções e verificações de identidade em seu código, quando necessário.  
  
 O .NET Framework fornece suporte de segurança baseada em função que é flexível e extensível o suficiente para atender às necessidades de uma ampla variedade de aplicativos. Você pode escolher para interoperar com infraestruturas de autenticação existente, como serviços COM+ 1.0, ou para criar um sistema de autenticação personalizada. Segurança baseada em função é particularmente adequada para uso em aplicativos Web do ASP.NET, que são processadas principalmente no servidor. No entanto, a segurança baseada em função do .NET Framework pode ser usada no cliente ou no servidor.  
  
 Antes de ler esta seção, certifique-se de que você compreenda o material apresentado [conceitos de segurança de chave](../../../docs/standard/security/key-security-concepts.md).  
  
## <a name="related-topics"></a>Tópicos relacionados  
  
|Título|Descrição|  
|-----------|-----------------|  
|[Objetos Principal e Identity](../../../docs/standard/security/principal-and-identity-objects.md)|Explica como configurar e gerenciar o Windows e identidades genéricas e entidades de segurança.|  
|[Principais conceitos de segurança](../../../docs/standard/security/key-security-concepts.md)|Apresenta os conceitos fundamentais que você deve compreender antes de usar a segurança do .NET Framework.|  
  
## <a name="reference"></a>Referência  
 <xref:System.Security.Permissions.PrincipalPermission?displayProperty=nameWithType>
