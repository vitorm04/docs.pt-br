---
title: Como criar uma identidade principal personalizada
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- IPrincipal
- IAuthorizationPolicy
- PrincipalPermissionMode
- PrincipalPermissionAttribute
ms.assetid: c4845fca-0ed9-4adf-bbdc-10812be69b61
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 973b3ebbedf80a7c33047f74306232805989646c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-custom-principal-identity"></a>Como criar uma identidade principal personalizada
O <xref:System.Security.Permissions.PrincipalPermissionAttribute> é uma forma declarativa de controlar o acesso aos métodos do serviço. Ao usar esse atributo, o <xref:System.ServiceModel.Description.PrincipalPermissionMode> enumeração Especifica o modo para executar verificações de autorização. Quando esse modo é definido como <xref:System.ServiceModel.Description.PrincipalPermissionMode.Custom>, ele permite que o usuário especifique um personalizado <xref:System.Security.Principal.IPrincipal> classe retornado pelo <xref:System.Threading.Thread.CurrentPrincipal%2A> propriedade. Este tópico ilustra o cenário quando <xref:System.ServiceModel.Description.PrincipalPermissionMode.Custom> é usado em combinação com uma política de autorização personalizada e uma entidade de segurança personalizada.  
  
 Para obter mais informações sobre como usar o <xref:System.Security.Permissions.PrincipalPermissionAttribute>, consulte [como: restringir o acesso com a PrincipalPermissionAttribute Class](../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md).  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[PrincipalPermissionMode#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/principalpermissionmode/cs/source.cs#8)]
 [!code-vb[PrincipalPermissionMode#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/principalpermissionmode/vb/source.vb#8)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Referências aos namespaces a seguir são necessários para compilar o código:  
  
-   <xref:System>  
  
-   <xref:System.Collections.Generic>  
  
-   <xref:System.Security.Permissions>  
  
-   <xref:System.Security.Principal>  
  
-   <xref:System.Threading>  
  
-   <xref:System.ServiceModel>  
  
-   <xref:System.ServiceModel.Channels>  
  
-   <xref:System.ServiceModel.Description>  
  
-   <xref:System.IdentityModel.Claims>  
  
-   <xref:System.IdentityModel.Policy>  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Description.PrincipalPermissionMode>  
 <xref:System.ServiceModel.Description.PrincipalPermissionMode>  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute>  
 [Como: usar o provedor de função ASP.NET com um serviço](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)  
 [How to: Restrict Access with the PrincipalPermissionAttribute Class](../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md) (Como restringir o acesso com a classe PrincipalPermissionAttribute)
