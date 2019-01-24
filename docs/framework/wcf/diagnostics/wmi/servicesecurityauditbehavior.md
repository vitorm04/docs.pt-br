---
title: ServiceSecurityAuditBehavior
ms.date: 03/30/2017
ms.assetid: 2c5809e7-5364-44ce-bc71-848be4672e2a
ms.openlocfilehash: dc48b8742c60714720be3cf4b22ba672f73c720a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54570220"
---
# <a name="servicesecurityauditbehavior"></a>ServiceSecurityAuditBehavior
ServiceSecurityAuditBehavior  
  
## <a name="syntax"></a>Sintaxe  
  
```csharp  
class ServiceSecurityAuditBehavior : Behavior  
{  
  string AuditLogLocation;  
  string MessageAuthenticationAuditLevel;  
  string ServiceAuthorizationAuditLevel;  
  boolean SuppressAuditFailure;  
};  
```  
  
## <a name="methods"></a>Métodos  
 A classe ServiceSecurityAuditBehavior não define quaisquer métodos.  
  
## <a name="properties"></a>Propriedades  
 A classe ServiceSecurityAuditBehavior tem as seguintes propriedades:  
  
### <a name="auditloglocation"></a>AuditLogLocation  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: Somente leitura  
  
 O local do log de auditoria.  
  
### <a name="messageauthenticationauditlevel"></a>MessageAuthenticationAuditLevel  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: Somente leitura  
  
 O tipo de nível de autenticação de mensagem que é usado para registrar eventos de auditoria.  
  
### <a name="serviceauthorizationauditlevel"></a>ServiceAuthorizationAuditLevel  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: Somente leitura  
  
 Os tipos de eventos de autorização que são registrados no log de auditoria.  
  
### <a name="suppressauditfailure"></a>SuppressAuditFailure  
 Tipo de dados: boolean  
  
 Tipo de acesso: Somente leitura  
  
 Um valor booliano que especifica o comportamento para suprimir falhas de gravação no log de auditoria.  
  
## <a name="requirements"></a>Requisitos  
  
|MOF|Declarado em Servicemodel.mof.|  
|---------|-----------------------------------|  
|Namespace|Definido no root\ServiceModel|  
  
## <a name="see-also"></a>Consulte também
- <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>
