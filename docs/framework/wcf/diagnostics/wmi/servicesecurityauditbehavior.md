---
title: ServiceSecurityAuditBehavior
ms.date: 03/30/2017
ms.assetid: 2c5809e7-5364-44ce-bc71-848be4672e2a
ms.openlocfilehash: e8b24877c2d76a3f2f90c27ae83374c7bca1328b
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50181154"
---
# <a name="servicesecurityauditbehavior"></a><span data-ttu-id="ef53b-102">ServiceSecurityAuditBehavior</span><span class="sxs-lookup"><span data-stu-id="ef53b-102">ServiceSecurityAuditBehavior</span></span>
<span data-ttu-id="ef53b-103">ServiceSecurityAuditBehavior</span><span class="sxs-lookup"><span data-stu-id="ef53b-103">ServiceSecurityAuditBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef53b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ef53b-104">Syntax</span></span>  
  
```csharp  
class ServiceSecurityAuditBehavior : Behavior  
{  
  string AuditLogLocation;  
  string MessageAuthenticationAuditLevel;  
  string ServiceAuthorizationAuditLevel;  
  boolean SuppressAuditFailure;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="ef53b-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="ef53b-105">Methods</span></span>  
 <span data-ttu-id="ef53b-106">A classe ServiceSecurityAuditBehavior não define quaisquer métodos.</span><span class="sxs-lookup"><span data-stu-id="ef53b-106">The ServiceSecurityAuditBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="ef53b-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="ef53b-107">Properties</span></span>  
 <span data-ttu-id="ef53b-108">A classe ServiceSecurityAuditBehavior tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="ef53b-108">The ServiceSecurityAuditBehavior class has the following properties:</span></span>  
  
### <a name="auditloglocation"></a><span data-ttu-id="ef53b-109">AuditLogLocation</span><span class="sxs-lookup"><span data-stu-id="ef53b-109">AuditLogLocation</span></span>  
 <span data-ttu-id="ef53b-110">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="ef53b-110">Data type: string</span></span>  
  
 <span data-ttu-id="ef53b-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="ef53b-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ef53b-112">O local do log de auditoria.</span><span class="sxs-lookup"><span data-stu-id="ef53b-112">The location of the audit log.</span></span>  
  
### <a name="messageauthenticationauditlevel"></a><span data-ttu-id="ef53b-113">MessageAuthenticationAuditLevel</span><span class="sxs-lookup"><span data-stu-id="ef53b-113">MessageAuthenticationAuditLevel</span></span>  
 <span data-ttu-id="ef53b-114">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="ef53b-114">Data type: string</span></span>  
  
 <span data-ttu-id="ef53b-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="ef53b-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ef53b-116">O tipo de nível de autenticação de mensagem que é usado para registrar eventos de auditoria.</span><span class="sxs-lookup"><span data-stu-id="ef53b-116">The type of message authentication level that is used to log audit events.</span></span>  
  
### <a name="serviceauthorizationauditlevel"></a><span data-ttu-id="ef53b-117">ServiceAuthorizationAuditLevel</span><span class="sxs-lookup"><span data-stu-id="ef53b-117">ServiceAuthorizationAuditLevel</span></span>  
 <span data-ttu-id="ef53b-118">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="ef53b-118">Data type: string</span></span>  
  
 <span data-ttu-id="ef53b-119">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="ef53b-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ef53b-120">Os tipos de eventos de autorização que são registrados no log de auditoria.</span><span class="sxs-lookup"><span data-stu-id="ef53b-120">The types of authorization events that are recorded in the audit log.</span></span>  
  
### <a name="suppressauditfailure"></a><span data-ttu-id="ef53b-121">SuppressAuditFailure</span><span class="sxs-lookup"><span data-stu-id="ef53b-121">SuppressAuditFailure</span></span>  
 <span data-ttu-id="ef53b-122">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="ef53b-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="ef53b-123">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="ef53b-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ef53b-124">Um valor booliano que especifica o comportamento para suprimir falhas de gravação no log de auditoria.</span><span class="sxs-lookup"><span data-stu-id="ef53b-124">A boolean value that specifies the behavior for suppressing failures of writing to the audit log.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ef53b-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ef53b-125">Requirements</span></span>  
  
|<span data-ttu-id="ef53b-126">MOF</span><span class="sxs-lookup"><span data-stu-id="ef53b-126">MOF</span></span>|<span data-ttu-id="ef53b-127">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="ef53b-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="ef53b-128">Namespace</span><span class="sxs-lookup"><span data-stu-id="ef53b-128">Namespace</span></span>|<span data-ttu-id="ef53b-129">Definido no root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="ef53b-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ef53b-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ef53b-130">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>
