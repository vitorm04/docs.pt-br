---
title: ServiceSecurityAuditBehavior
ms.date: 03/30/2017
ms.assetid: 2c5809e7-5364-44ce-bc71-848be4672e2a
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 3adc721dd8ad0fb706e172373e5da70fe6032db6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33485889"
---
# <a name="servicesecurityauditbehavior"></a><span data-ttu-id="0f275-102">ServiceSecurityAuditBehavior</span><span class="sxs-lookup"><span data-stu-id="0f275-102">ServiceSecurityAuditBehavior</span></span>
<span data-ttu-id="0f275-103">ServiceSecurityAuditBehavior</span><span class="sxs-lookup"><span data-stu-id="0f275-103">ServiceSecurityAuditBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f275-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0f275-104">Syntax</span></span>  
  
```  
class ServiceSecurityAuditBehavior : Behavior  
{  
  string AuditLogLocation;  
  string MessageAuthenticationAuditLevel;  
  string ServiceAuthorizationAuditLevel;  
  boolean SuppressAuditFailure;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="0f275-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="0f275-105">Methods</span></span>  
 <span data-ttu-id="0f275-106">A classe ServiceSecurityAuditBehavior não define nenhum método.</span><span class="sxs-lookup"><span data-stu-id="0f275-106">The ServiceSecurityAuditBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="0f275-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="0f275-107">Properties</span></span>  
 <span data-ttu-id="0f275-108">A classe ServiceSecurityAuditBehavior tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="0f275-108">The ServiceSecurityAuditBehavior class has the following properties:</span></span>  
  
### <a name="auditloglocation"></a><span data-ttu-id="0f275-109">auditLogLocation</span><span class="sxs-lookup"><span data-stu-id="0f275-109">AuditLogLocation</span></span>  
 <span data-ttu-id="0f275-110">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="0f275-110">Data type: string</span></span>  
  
 <span data-ttu-id="0f275-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="0f275-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0f275-112">O local do log de auditoria.</span><span class="sxs-lookup"><span data-stu-id="0f275-112">The location of the audit log.</span></span>  
  
### <a name="messageauthenticationauditlevel"></a><span data-ttu-id="0f275-113">messageAuthenticationAuditLevel</span><span class="sxs-lookup"><span data-stu-id="0f275-113">MessageAuthenticationAuditLevel</span></span>  
 <span data-ttu-id="0f275-114">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="0f275-114">Data type: string</span></span>  
  
 <span data-ttu-id="0f275-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="0f275-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0f275-116">O tipo de nível de autenticação de mensagem que é usado para registrar eventos de auditoria.</span><span class="sxs-lookup"><span data-stu-id="0f275-116">The type of message authentication level that is used to log audit events.</span></span>  
  
### <a name="serviceauthorizationauditlevel"></a><span data-ttu-id="0f275-117">serviceAuthorizationAuditLevel</span><span class="sxs-lookup"><span data-stu-id="0f275-117">ServiceAuthorizationAuditLevel</span></span>  
 <span data-ttu-id="0f275-118">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="0f275-118">Data type: string</span></span>  
  
 <span data-ttu-id="0f275-119">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="0f275-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0f275-120">Os tipos de eventos de autorização que são registrados no log de auditoria.</span><span class="sxs-lookup"><span data-stu-id="0f275-120">The types of authorization events that are recorded in the audit log.</span></span>  
  
### <a name="suppressauditfailure"></a><span data-ttu-id="0f275-121">suppressAuditFailure</span><span class="sxs-lookup"><span data-stu-id="0f275-121">SuppressAuditFailure</span></span>  
 <span data-ttu-id="0f275-122">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="0f275-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="0f275-123">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="0f275-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0f275-124">Um valor booleano que especifica o comportamento para suprimir falhas de gravação no log de auditoria.</span><span class="sxs-lookup"><span data-stu-id="0f275-124">A boolean value that specifies the behavior for suppressing failures of writing to the audit log.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0f275-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0f275-125">Requirements</span></span>  
  
|<span data-ttu-id="0f275-126">MOF</span><span class="sxs-lookup"><span data-stu-id="0f275-126">MOF</span></span>|<span data-ttu-id="0f275-127">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="0f275-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="0f275-128">Namespace</span><span class="sxs-lookup"><span data-stu-id="0f275-128">Namespace</span></span>|<span data-ttu-id="0f275-129">Definido em root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="0f275-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0f275-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0f275-130">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>
