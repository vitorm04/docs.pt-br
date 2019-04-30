---
title: ServiceSecurityAuditBehavior
ms.date: 03/30/2017
ms.assetid: 2c5809e7-5364-44ce-bc71-848be4672e2a
ms.openlocfilehash: 30679e1f67c6943bf674a6bbd8bf12be090765a8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61956885"
---
# <a name="servicesecurityauditbehavior"></a><span data-ttu-id="62e82-102">ServiceSecurityAuditBehavior</span><span class="sxs-lookup"><span data-stu-id="62e82-102">ServiceSecurityAuditBehavior</span></span>
<span data-ttu-id="62e82-103">ServiceSecurityAuditBehavior</span><span class="sxs-lookup"><span data-stu-id="62e82-103">ServiceSecurityAuditBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62e82-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="62e82-104">Syntax</span></span>  
  
```csharp  
class ServiceSecurityAuditBehavior : Behavior  
{  
  string AuditLogLocation;  
  string MessageAuthenticationAuditLevel;  
  string ServiceAuthorizationAuditLevel;  
  boolean SuppressAuditFailure;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="62e82-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="62e82-105">Methods</span></span>  
 <span data-ttu-id="62e82-106">A classe ServiceSecurityAuditBehavior não define quaisquer métodos.</span><span class="sxs-lookup"><span data-stu-id="62e82-106">The ServiceSecurityAuditBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="62e82-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="62e82-107">Properties</span></span>  
 <span data-ttu-id="62e82-108">A classe ServiceSecurityAuditBehavior tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="62e82-108">The ServiceSecurityAuditBehavior class has the following properties:</span></span>  
  
### <a name="auditloglocation"></a><span data-ttu-id="62e82-109">AuditLogLocation</span><span class="sxs-lookup"><span data-stu-id="62e82-109">AuditLogLocation</span></span>  
 <span data-ttu-id="62e82-110">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62e82-110">Data type: string</span></span>  
  
 <span data-ttu-id="62e82-111">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="62e82-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="62e82-112">O local do log de auditoria.</span><span class="sxs-lookup"><span data-stu-id="62e82-112">The location of the audit log.</span></span>  
  
### <a name="messageauthenticationauditlevel"></a><span data-ttu-id="62e82-113">MessageAuthenticationAuditLevel</span><span class="sxs-lookup"><span data-stu-id="62e82-113">MessageAuthenticationAuditLevel</span></span>  
 <span data-ttu-id="62e82-114">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62e82-114">Data type: string</span></span>  
  
 <span data-ttu-id="62e82-115">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="62e82-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="62e82-116">O tipo de nível de autenticação de mensagem que é usado para registrar eventos de auditoria.</span><span class="sxs-lookup"><span data-stu-id="62e82-116">The type of message authentication level that is used to log audit events.</span></span>  
  
### <a name="serviceauthorizationauditlevel"></a><span data-ttu-id="62e82-117">ServiceAuthorizationAuditLevel</span><span class="sxs-lookup"><span data-stu-id="62e82-117">ServiceAuthorizationAuditLevel</span></span>  
 <span data-ttu-id="62e82-118">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="62e82-118">Data type: string</span></span>  
  
 <span data-ttu-id="62e82-119">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="62e82-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="62e82-120">Os tipos de eventos de autorização que são registrados no log de auditoria.</span><span class="sxs-lookup"><span data-stu-id="62e82-120">The types of authorization events that are recorded in the audit log.</span></span>  
  
### <a name="suppressauditfailure"></a><span data-ttu-id="62e82-121">SuppressAuditFailure</span><span class="sxs-lookup"><span data-stu-id="62e82-121">SuppressAuditFailure</span></span>  
 <span data-ttu-id="62e82-122">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="62e82-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="62e82-123">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="62e82-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="62e82-124">Um valor booliano que especifica o comportamento para suprimir falhas de gravação no log de auditoria.</span><span class="sxs-lookup"><span data-stu-id="62e82-124">A boolean value that specifies the behavior for suppressing failures of writing to the audit log.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="62e82-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="62e82-125">Requirements</span></span>  
  
|<span data-ttu-id="62e82-126">MOF</span><span class="sxs-lookup"><span data-stu-id="62e82-126">MOF</span></span>|<span data-ttu-id="62e82-127">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="62e82-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="62e82-128">Namespace</span><span class="sxs-lookup"><span data-stu-id="62e82-128">Namespace</span></span>|<span data-ttu-id="62e82-129">Definido no root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="62e82-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="62e82-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="62e82-130">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>
