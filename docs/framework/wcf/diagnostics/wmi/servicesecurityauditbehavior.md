---
title: ServiceSecurityAuditBehavior
ms.date: 03/30/2017
ms.assetid: 2c5809e7-5364-44ce-bc71-848be4672e2a
author: BrucePerlerMS
ms.openlocfilehash: 8f43ee752830d95db6bbbdbe311b6d77735e31b5
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47196883"
---
# <a name="servicesecurityauditbehavior"></a><span data-ttu-id="895ee-102">ServiceSecurityAuditBehavior</span><span class="sxs-lookup"><span data-stu-id="895ee-102">ServiceSecurityAuditBehavior</span></span>
<span data-ttu-id="895ee-103">ServiceSecurityAuditBehavior</span><span class="sxs-lookup"><span data-stu-id="895ee-103">ServiceSecurityAuditBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="895ee-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="895ee-104">Syntax</span></span>  
  
```  
class ServiceSecurityAuditBehavior : Behavior  
{  
  string AuditLogLocation;  
  string MessageAuthenticationAuditLevel;  
  string ServiceAuthorizationAuditLevel;  
  boolean SuppressAuditFailure;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="895ee-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="895ee-105">Methods</span></span>  
 <span data-ttu-id="895ee-106">A classe ServiceSecurityAuditBehavior não define quaisquer métodos.</span><span class="sxs-lookup"><span data-stu-id="895ee-106">The ServiceSecurityAuditBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="895ee-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="895ee-107">Properties</span></span>  
 <span data-ttu-id="895ee-108">A classe ServiceSecurityAuditBehavior tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="895ee-108">The ServiceSecurityAuditBehavior class has the following properties:</span></span>  
  
### <a name="auditloglocation"></a><span data-ttu-id="895ee-109">AuditLogLocation</span><span class="sxs-lookup"><span data-stu-id="895ee-109">AuditLogLocation</span></span>  
 <span data-ttu-id="895ee-110">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="895ee-110">Data type: string</span></span>  
  
 <span data-ttu-id="895ee-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="895ee-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="895ee-112">O local do log de auditoria.</span><span class="sxs-lookup"><span data-stu-id="895ee-112">The location of the audit log.</span></span>  
  
### <a name="messageauthenticationauditlevel"></a><span data-ttu-id="895ee-113">MessageAuthenticationAuditLevel</span><span class="sxs-lookup"><span data-stu-id="895ee-113">MessageAuthenticationAuditLevel</span></span>  
 <span data-ttu-id="895ee-114">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="895ee-114">Data type: string</span></span>  
  
 <span data-ttu-id="895ee-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="895ee-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="895ee-116">O tipo de nível de autenticação de mensagem que é usado para registrar eventos de auditoria.</span><span class="sxs-lookup"><span data-stu-id="895ee-116">The type of message authentication level that is used to log audit events.</span></span>  
  
### <a name="serviceauthorizationauditlevel"></a><span data-ttu-id="895ee-117">ServiceAuthorizationAuditLevel</span><span class="sxs-lookup"><span data-stu-id="895ee-117">ServiceAuthorizationAuditLevel</span></span>  
 <span data-ttu-id="895ee-118">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="895ee-118">Data type: string</span></span>  
  
 <span data-ttu-id="895ee-119">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="895ee-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="895ee-120">Os tipos de eventos de autorização que são registrados no log de auditoria.</span><span class="sxs-lookup"><span data-stu-id="895ee-120">The types of authorization events that are recorded in the audit log.</span></span>  
  
### <a name="suppressauditfailure"></a><span data-ttu-id="895ee-121">SuppressAuditFailure</span><span class="sxs-lookup"><span data-stu-id="895ee-121">SuppressAuditFailure</span></span>  
 <span data-ttu-id="895ee-122">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="895ee-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="895ee-123">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="895ee-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="895ee-124">Um valor booliano que especifica o comportamento para suprimir falhas de gravação no log de auditoria.</span><span class="sxs-lookup"><span data-stu-id="895ee-124">A boolean value that specifies the behavior for suppressing failures of writing to the audit log.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="895ee-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="895ee-125">Requirements</span></span>  
  
|<span data-ttu-id="895ee-126">MOF</span><span class="sxs-lookup"><span data-stu-id="895ee-126">MOF</span></span>|<span data-ttu-id="895ee-127">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="895ee-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="895ee-128">Namespace</span><span class="sxs-lookup"><span data-stu-id="895ee-128">Namespace</span></span>|<span data-ttu-id="895ee-129">Definido no root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="895ee-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="895ee-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="895ee-130">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>
