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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62018574"
---
# <a name="role-based-security"></a>Segurança baseada em função
Funções são geralmente usadas em aplicativos financeiros ou de negócios para impor a política. Por exemplo, um aplicativo pode impor limites de tamanho da transação que está sendo processada, dependendo se o usuário que fez a solicitação é um membro de uma função especificada. Administradores de memória podem ter autorização para processar as transações que são menores que um limite especificado, supervisores podem ter um limite mais alto e vice-presidentes podem ter um limite ainda maior (ou nenhum limite todos os). Segurança baseada em função também pode ser usada quando um aplicativo exigir vários aprovações para concluir uma ação. Nesse caso, pode ser um sistema de compra em que qualquer funcionário pode gerar uma solicitação de compra, mas apenas um agente de compras pode converter essa solicitação em uma ordem de compra que pode ser enviada a um fornecedor.  
  
 Segurança baseada em função do .NET framework oferece suporte à autorização, tornando as informações sobre a entidade de segurança, que é construída a partir de uma identidade associada disponível para o thread atual. A identidade (e isso ajuda a definir a entidade de segurança) seja baseadas em uma conta do Windows ou ser uma identidade personalizada não relacionada a uma conta do Windows. Aplicativos do .NET framework podem tomar decisões de autorização com base em identidade da entidade de segurança ou associação de função ou ambos. Uma função é um conjunto nomeado de entidades que têm os mesmos privilégios em relação à segurança (como um caixa eletrônico ou gerente). Uma entidade de segurança pode ser um membro de uma ou mais funções. Portanto, os aplicativos podem usar associação de função para determinar se uma entidade de segurança está autorizada a executar uma ação solicitada.  
  
 Para fornecer facilidade de uso e consistência com a segurança de acesso do código, segurança baseada em função do .NET Framework fornece <xref:System.Security.Permissions.PrincipalPermission?displayProperty=nameWithType> verificações de segurança de acesso de objetos que permitem que o common language runtime executar a autorização de uma maneira que é semelhante ao código. O <xref:System.Security.Permissions.PrincipalPermission> classe representa a identidade ou uma função que a entidade de segurança deve corresponder ao e é compatível com ambas as verificações de segurança declarativas e imperativas. Você também pode acessar informações de identidade da entidade de segurança diretamente e executar a função e verificações de identidade em seu código quando necessário.  
  
 O .NET Framework fornece suporte de segurança baseada em função que é flexível e extensível o suficiente para atender às necessidades de um amplo espectro de aplicativos. Você pode escolher para interoperar com infra-estruturas existentes de autenticação, como serviços COM+ 1.0, ou para criar um sistema de autenticação personalizada. Segurança baseada em função é especialmente adequada para uso em aplicativos Web do ASP.NET, que são processadas principalmente no servidor. No entanto, a segurança baseada em função do .NET Framework pode ser usada no cliente ou servidor.  
  
 Antes de ler esta seção, certifique-se de que você compreenda o material apresentado [conceitos fundamentais de segurança](../../../docs/standard/security/key-security-concepts.md).  
  
## <a name="related-topics"></a>Tópicos relacionados  
  
|Título|Descrição|  
|-----------|-----------------|  
|[Objetos Principal e Identity](../../../docs/standard/security/principal-and-identity-objects.md)|Explica como configurar e gerenciar o Windows e identidades genéricas e entidades de segurança.|  
|[Principais conceitos de segurança](../../../docs/standard/security/key-security-concepts.md)|Apresenta os conceitos fundamentais que você deve compreender antes de usar a segurança do .NET Framework.|  
  
## <a name="reference"></a>Referência  
 <xref:System.Security.Permissions.PrincipalPermission?displayProperty=nameWithType>
