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
ms.openlocfilehash: 8986e778e84fdf211d11fd7a897508acc7412207
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291195"
---
# <a name="role-based-security"></a>Segurança baseada em função
As funções geralmente são usadas em aplicativos financeiros ou de negócios para impor a política. Por exemplo, um aplicativo pode impor limites quanto ao tamanho da transação que está sendo processada dependendo se o usuário que está fazendo a solicitação é membro de uma função especificada. Os auxiliares podem ter autorização para processar transações que são menores que um limite especificado, os supervisores podem ter um limite maior e o presidentes pode ter um limite ainda maior (ou nenhum limite). A segurança baseada em função também pode ser usada quando um aplicativo requer várias aprovações para concluir uma ação. Esse caso pode ser um sistema de compra no qual qualquer funcionário possa gerar uma solicitação de compra, mas apenas um agente de compras pode converter essa solicitação em uma ordem de compra que pode ser enviada a um fornecedor.  
  
 .NET Framework segurança baseada em função dá suporte à autorização, disponibilizando informações sobre a entidade, que é construída com base em uma identidade associada, disponível para o thread atual. A identidade (e a entidade de segurança que ajuda a definir) pode ser baseada em uma conta do Windows ou ser uma identidade personalizada não relacionada a uma conta do Windows. .NET Framework aplicativos podem tomar decisões de autorização com base na identidade da entidade de segurança ou na associação de função, ou ambos. Uma função é um conjunto nomeado de entidades que têm os mesmos privilégios em relação à segurança (como um ou um gerente). Uma entidade de segurança pode ser um membro de uma ou mais funções. Portanto, os aplicativos podem usar a associação de função para determinar se uma entidade de segurança está autorizada a executar uma ação solicitada.  
  
 Para fornecer facilidade de uso e consistência com a segurança de acesso ao código, .NET Framework segurança baseada em função fornece <xref:System.Security.Permissions.PrincipalPermission?displayProperty=nameWithType> objetos que permitem que o Common Language Runtime execute a autorização de forma semelhante às verificações de segurança de acesso ao código. A <xref:System.Security.Permissions.PrincipalPermission> classe representa a identidade ou função que o principal deve corresponder e é compatível com verificações de segurança declarativas e imperativas. Você também pode acessar as informações de identidade de uma entidade de segurança diretamente e executar verificações de função e de identidade em seu código quando necessário.  
  
 O .NET Framework fornece suporte à segurança baseada em função que é flexível e extensível o suficiente para atender às necessidades de um amplo espectro de aplicativos. Você pode optar por interoperar com as infraestruturas de autenticação existentes, como os serviços do COM+ 1,0, ou para criar um sistema de autenticação personalizado. A segurança baseada em função é especialmente adequada para uso em aplicativos Web ASP.NET, que são processados principalmente no servidor. No entanto, .NET Framework segurança baseada em função pode ser usada no cliente ou no servidor.  
  
 Antes de ler esta seção, verifique se você entendeu o material apresentado nos [principais conceitos de segurança](key-security-concepts.md).  
  
## <a name="related-topics"></a>Tópicos relacionados  
  
|Title|Descrição|  
|-----------|-----------------|  
|[Objetos Principal e Identity](principal-and-identity-objects.md)|Explica como configurar e gerenciar identidades e entidades genéricas e do Windows.|  
|[Conceitos principais de segurança](key-security-concepts.md)|Apresenta conceitos fundamentais que você deve entender antes de usar .NET Framework segurança.|  
  
## <a name="reference"></a>Referência  
 <xref:System.Security.Permissions.PrincipalPermission?displayProperty=nameWithType>
