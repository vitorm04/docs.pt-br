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
ms.openlocfilehash: b89792f9579da2d72c0a7f90a983308b172093fb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33390715"
---
# <a name="dangerous-permissions-and-policy-administration"></a>Permissões perigosas e administração de políticas
Várias das operações protegidas para o qual o .NET Framework fornece permissões potencialmente podem permitir que o sistema de segurança ser contornadas. Essas permissões perigosas devem ser fornecidas apenas para o código confiável e, em seguida, somente quando necessário. Geralmente, há nenhuma defesa contra um código mal-intencionado se essas permissões é concedido.  
  
> [!NOTE]
>  No [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], houve alterações importantes para o modelo de segurança do .NET Framework e terminologia. Para obter mais informações sobre essas alterações, consulte [alterações de segurança](../../../docs/framework/security/security-changes.md).  
  
 As permissões perigosas são explicadas na tabela a seguir.  
  
|Permissão|Risco potencial|  
|----------------|--------------------|  
|<xref:System.Security.Permissions.SecurityPermission>||  
|<xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode>|Permite que o código gerenciado para chamar código não gerenciado, que geralmente é perigoso.|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.SkipVerification>|Sem a verificação, o código pode fazer nada.|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlEvidence>|Evidência invalidada pode enganar política de segurança.|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlPolicy>|A capacidade de modificar a política de segurança pode desativar a segurança.|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter>|O uso de serialização pode contornar mecanismos de acessibilidade. Para obter detalhes, consulte [segurança e serialização](../../../docs/framework/misc/security-and-serialization.md).|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlPrincipal>|A capacidade de definir o servidor principal atual pode instruir a segurança baseada em função.|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlThread>|Manipulação de threads é perigosa devido ao estado de segurança associado com segmentos.|  
|<xref:System.Security.Permissions.ReflectionPermission>||  
|<xref:System.MemberAccessException>|Pode usar membros particulares para anular os mecanismos de acessibilidade.|  
  
## <a name="see-also"></a>Consulte também  
 [Diretrizes de codificação segura](../../../docs/standard/security/secure-coding-guidelines.md)
