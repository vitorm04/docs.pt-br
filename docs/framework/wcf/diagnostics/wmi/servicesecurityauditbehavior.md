---
title: ServiceSecurityAuditBehavior
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2c5809e7-5364-44ce-bc71-848be4672e2a
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 1ce712bbdb258c477a2ee56f47281b1a1d09ec54
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="servicesecurityauditbehavior"></a><span data-ttu-id="017bc-102">ServiceSecurityAuditBehavior</span><span class="sxs-lookup"><span data-stu-id="017bc-102">ServiceSecurityAuditBehavior</span></span>
<span data-ttu-id="017bc-103">ServiceSecurityAuditBehavior</span><span class="sxs-lookup"><span data-stu-id="017bc-103">ServiceSecurityAuditBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="017bc-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="017bc-104">Syntax</span></span>  
  
```  
class ServiceSecurityAuditBehavior : Behavior  
{  
  string AuditLogLocation;  
  string MessageAuthenticationAuditLevel;  
  string ServiceAuthorizationAuditLevel;  
  boolean SuppressAuditFailure;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="017bc-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="017bc-105">Methods</span></span>  
 <span data-ttu-id="017bc-106">A classe ServiceSecurityAuditBehavior não define nenhum método.</span><span class="sxs-lookup"><span data-stu-id="017bc-106">The ServiceSecurityAuditBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="017bc-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="017bc-107">Properties</span></span>  
 <span data-ttu-id="017bc-108">A classe ServiceSecurityAuditBehavior tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="017bc-108">The ServiceSecurityAuditBehavior class has the following properties:</span></span>  
  
### <a name="auditloglocation"></a><span data-ttu-id="017bc-109">auditLogLocation</span><span class="sxs-lookup"><span data-stu-id="017bc-109">AuditLogLocation</span></span>  
 <span data-ttu-id="017bc-110">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="017bc-110">Data type: string</span></span>  
  
 <span data-ttu-id="017bc-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="017bc-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="017bc-112">O local do log de auditoria.</span><span class="sxs-lookup"><span data-stu-id="017bc-112">The location of the audit log.</span></span>  
  
### <a name="messageauthenticationauditlevel"></a><span data-ttu-id="017bc-113">messageAuthenticationAuditLevel</span><span class="sxs-lookup"><span data-stu-id="017bc-113">MessageAuthenticationAuditLevel</span></span>  
 <span data-ttu-id="017bc-114">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="017bc-114">Data type: string</span></span>  
  
 <span data-ttu-id="017bc-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="017bc-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="017bc-116">O tipo de nível de autenticação de mensagem que é usado para registrar eventos de auditoria.</span><span class="sxs-lookup"><span data-stu-id="017bc-116">The type of message authentication level that is used to log audit events.</span></span>  
  
### <a name="serviceauthorizationauditlevel"></a><span data-ttu-id="017bc-117">serviceAuthorizationAuditLevel</span><span class="sxs-lookup"><span data-stu-id="017bc-117">ServiceAuthorizationAuditLevel</span></span>  
 <span data-ttu-id="017bc-118">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="017bc-118">Data type: string</span></span>  
  
 <span data-ttu-id="017bc-119">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="017bc-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="017bc-120">Os tipos de eventos de autorização que são registrados no log de auditoria.</span><span class="sxs-lookup"><span data-stu-id="017bc-120">The types of authorization events that are recorded in the audit log.</span></span>  
  
### <a name="suppressauditfailure"></a><span data-ttu-id="017bc-121">suppressAuditFailure</span><span class="sxs-lookup"><span data-stu-id="017bc-121">SuppressAuditFailure</span></span>  
 <span data-ttu-id="017bc-122">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="017bc-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="017bc-123">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="017bc-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="017bc-124">Um valor booleano que especifica o comportamento para suprimir falhas de gravação no log de auditoria.</span><span class="sxs-lookup"><span data-stu-id="017bc-124">A boolean value that specifies the behavior for suppressing failures of writing to the audit log.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="017bc-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="017bc-125">Requirements</span></span>  
  
|<span data-ttu-id="017bc-126">MOF</span><span class="sxs-lookup"><span data-stu-id="017bc-126">MOF</span></span>|<span data-ttu-id="017bc-127">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="017bc-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="017bc-128">Namespace</span><span class="sxs-lookup"><span data-stu-id="017bc-128">Namespace</span></span>|<span data-ttu-id="017bc-129">Definido em root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="017bc-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="017bc-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="017bc-130">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>
