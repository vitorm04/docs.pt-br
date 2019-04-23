---
title: ServiceSecurityAuditBehavior
ms.date: 03/30/2017
ms.assetid: 2c5809e7-5364-44ce-bc71-848be4672e2a
ms.openlocfilehash: 30679e1f67c6943bf674a6bbd8bf12be090765a8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59979124"
---
# <a name="servicesecurityauditbehavior"></a><span data-ttu-id="1c1f8-102">ServiceSecurityAuditBehavior</span><span class="sxs-lookup"><span data-stu-id="1c1f8-102">ServiceSecurityAuditBehavior</span></span>
<span data-ttu-id="1c1f8-103">ServiceSecurityAuditBehavior</span><span class="sxs-lookup"><span data-stu-id="1c1f8-103">ServiceSecurityAuditBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c1f8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1c1f8-104">Syntax</span></span>  
  
```csharp  
class ServiceSecurityAuditBehavior : Behavior  
{  
  string AuditLogLocation;  
  string MessageAuthenticationAuditLevel;  
  string ServiceAuthorizationAuditLevel;  
  boolean SuppressAuditFailure;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="1c1f8-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="1c1f8-105">Methods</span></span>  
 <span data-ttu-id="1c1f8-106">A classe ServiceSecurityAuditBehavior não define quaisquer métodos.</span><span class="sxs-lookup"><span data-stu-id="1c1f8-106">The ServiceSecurityAuditBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="1c1f8-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="1c1f8-107">Properties</span></span>  
 <span data-ttu-id="1c1f8-108">A classe ServiceSecurityAuditBehavior tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="1c1f8-108">The ServiceSecurityAuditBehavior class has the following properties:</span></span>  
  
### <a name="auditloglocation"></a><span data-ttu-id="1c1f8-109">AuditLogLocation</span><span class="sxs-lookup"><span data-stu-id="1c1f8-109">AuditLogLocation</span></span>  
 <span data-ttu-id="1c1f8-110">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="1c1f8-110">Data type: string</span></span>  
  
 <span data-ttu-id="1c1f8-111">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="1c1f8-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1c1f8-112">O local do log de auditoria.</span><span class="sxs-lookup"><span data-stu-id="1c1f8-112">The location of the audit log.</span></span>  
  
### <a name="messageauthenticationauditlevel"></a><span data-ttu-id="1c1f8-113">MessageAuthenticationAuditLevel</span><span class="sxs-lookup"><span data-stu-id="1c1f8-113">MessageAuthenticationAuditLevel</span></span>  
 <span data-ttu-id="1c1f8-114">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="1c1f8-114">Data type: string</span></span>  
  
 <span data-ttu-id="1c1f8-115">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="1c1f8-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1c1f8-116">O tipo de nível de autenticação de mensagem que é usado para registrar eventos de auditoria.</span><span class="sxs-lookup"><span data-stu-id="1c1f8-116">The type of message authentication level that is used to log audit events.</span></span>  
  
### <a name="serviceauthorizationauditlevel"></a><span data-ttu-id="1c1f8-117">ServiceAuthorizationAuditLevel</span><span class="sxs-lookup"><span data-stu-id="1c1f8-117">ServiceAuthorizationAuditLevel</span></span>  
 <span data-ttu-id="1c1f8-118">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="1c1f8-118">Data type: string</span></span>  
  
 <span data-ttu-id="1c1f8-119">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="1c1f8-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1c1f8-120">Os tipos de eventos de autorização que são registrados no log de auditoria.</span><span class="sxs-lookup"><span data-stu-id="1c1f8-120">The types of authorization events that are recorded in the audit log.</span></span>  
  
### <a name="suppressauditfailure"></a><span data-ttu-id="1c1f8-121">SuppressAuditFailure</span><span class="sxs-lookup"><span data-stu-id="1c1f8-121">SuppressAuditFailure</span></span>  
 <span data-ttu-id="1c1f8-122">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="1c1f8-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="1c1f8-123">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="1c1f8-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1c1f8-124">Um valor booliano que especifica o comportamento para suprimir falhas de gravação no log de auditoria.</span><span class="sxs-lookup"><span data-stu-id="1c1f8-124">A boolean value that specifies the behavior for suppressing failures of writing to the audit log.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1c1f8-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1c1f8-125">Requirements</span></span>  
  
|<span data-ttu-id="1c1f8-126">MOF</span><span class="sxs-lookup"><span data-stu-id="1c1f8-126">MOF</span></span>|<span data-ttu-id="1c1f8-127">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="1c1f8-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="1c1f8-128">Namespace</span><span class="sxs-lookup"><span data-stu-id="1c1f8-128">Namespace</span></span>|<span data-ttu-id="1c1f8-129">Definido no root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="1c1f8-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1c1f8-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1c1f8-130">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>
