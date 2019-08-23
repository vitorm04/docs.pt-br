---
title: Permissões perigosas e administração de políticas
ms.date: 03/30/2017
helpviewer_keywords:
- permissions [.NET Framework], policy administration
- security [.NET Framework], dangerous permissions
- code security, dangerous permissions
- secure coding, dangerous permissions
- permissions [.NET Framework], dangerous
ms.assetid: 1929e854-23a0-4bb1-94be-e8aa3b609e32
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f79fd3e0678fc0bba0d3074904f9ce9460fc6c20
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69910926"
---
# <a name="dangerous-permissions-and-policy-administration"></a>Permissões perigosas e administração de políticas
Várias das operações protegidas para as quais a .NET Framework fornece permissões podem potencialmente permitir que o sistema de segurança seja burlado. Essas permissões perigosas devem ser fornecidas apenas ao código digno de confiança e, em seguida, somente conforme necessário. Normalmente, não há nenhuma defesa contra código mal-intencionado se ele receber essas permissões.  
  
> [!NOTE]
> No .NET Framework 4, houve alterações importantes na .NET Framework modelo e terminologia de segurança. Para obter mais informações sobre essas alterações, consulte [Security Changes](../../../docs/framework/security/security-changes.md).  
  
 As permissões perigosas são explicadas na tabela a seguir.  
  
|Permissão|Risco potencial|  
|----------------|--------------------|  
|<xref:System.Security.Permissions.SecurityPermission>||  
|<xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode>|Permite que o código gerenciado chame código não gerenciado, o que geralmente é perigoso.|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.SkipVerification>|Sem a verificação, o código pode fazer qualquer coisa.|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlEvidence>|Evidências invalidadas podem enganar a política de segurança.|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlPolicy>|A capacidade de modificar a política de segurança pode desabilitar a segurança.|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter>|O uso da serialização pode burlar os mecanismos de acessibilidade. Para obter detalhes, consulte [segurança e serialização](../../../docs/framework/misc/security-and-serialization.md).|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlPrincipal>|A capacidade de definir a entidade atual pode enganar a segurança baseada em função.|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlThread>|A manipulação de threads é perigosa devido ao estado de segurança associado a threads.|  
|<xref:System.Security.Permissions.ReflectionPermission>||  
|<xref:System.MemberAccessException>|Pode usar membros privados para derrotar os mecanismos de acessibilidade.|  
  
## <a name="see-also"></a>Consulte também

- [Diretrizes de codificação segura](../../standard/security/secure-coding-guidelines.md)
