---
title: OperationBehaviorAttribute
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8c9b0755-9e83-411f-bdcb-61a586022797
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 63824ae2171053bee2af204e748a6fa811f2ba82
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="operationbehaviorattribute"></a><span data-ttu-id="86952-102">OperationBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="86952-102">OperationBehaviorAttribute</span></span>
<span data-ttu-id="86952-103">OperationBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="86952-103">OperationBehaviorAttribute</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86952-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="86952-104">Syntax</span></span>  
  
```  
class OperationBehaviorAttribute : Behavior  
{  
  boolean AutoDisposeParameters;  
  string Impersonation;  
  string ReleaseInstanceMode;  
  boolean TransactionAutoComplete;  
  boolean TransactionScopeRequired;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="86952-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="86952-105">Methods</span></span>  
 <span data-ttu-id="86952-106">A classe OperationBehaviorAttribute não define nenhum método.</span><span class="sxs-lookup"><span data-stu-id="86952-106">The OperationBehaviorAttribute class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="86952-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="86952-107">Properties</span></span>  
 <span data-ttu-id="86952-108">A classe OperationBehaviorAttribute tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="86952-108">The OperationBehaviorAttribute class has the following properties:</span></span>  
  
### <a name="autodisposeparameters"></a><span data-ttu-id="86952-109">AutoDisposeParameters</span><span class="sxs-lookup"><span data-stu-id="86952-109">AutoDisposeParameters</span></span>  
 <span data-ttu-id="86952-110">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="86952-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="86952-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="86952-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="86952-112">O estado do recurso auto-dispose para parâmetros.</span><span class="sxs-lookup"><span data-stu-id="86952-112">The state of the auto-dispose feature for parameters.</span></span>  
  
### <a name="impersonation"></a><span data-ttu-id="86952-113">Representação</span><span class="sxs-lookup"><span data-stu-id="86952-113">Impersonation</span></span>  
 <span data-ttu-id="86952-114">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="86952-114">Data type: string</span></span>  
  
 <span data-ttu-id="86952-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="86952-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="86952-116">Indica o nível de representação do chamador que a operação oferece suporte.</span><span class="sxs-lookup"><span data-stu-id="86952-116">Indicates the level of caller impersonation that the operation supports.</span></span>  
  
### <a name="releaseinstancemode"></a><span data-ttu-id="86952-117">ReleaseInstanceMode</span><span class="sxs-lookup"><span data-stu-id="86952-117">ReleaseInstanceMode</span></span>  
 <span data-ttu-id="86952-118">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="86952-118">Data type: string</span></span>  
  
 <span data-ttu-id="86952-119">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="86952-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="86952-120">Indica quando no curso de uma invocação de operação reciclar o objeto.</span><span class="sxs-lookup"><span data-stu-id="86952-120">Indicates when in the course of an operation invocation to recycle the object.</span></span>  
  
### <a name="transactionautocomplete"></a><span data-ttu-id="86952-121">TransactionAutoComplete</span><span class="sxs-lookup"><span data-stu-id="86952-121">TransactionAutoComplete</span></span>  
 <span data-ttu-id="86952-122">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="86952-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="86952-123">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="86952-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="86952-124">Indica se deve confirmar a transação atual automaticamente se nenhuma exceção não tratada ocorrer.</span><span class="sxs-lookup"><span data-stu-id="86952-124">Indicates whether to automatically commit the current transaction if no unhandled exceptions occur.</span></span>  
  
### <a name="transactionscoperequired"></a><span data-ttu-id="86952-125">TransactionScopeRequired</span><span class="sxs-lookup"><span data-stu-id="86952-125">TransactionScopeRequired</span></span>  
 <span data-ttu-id="86952-126">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="86952-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="86952-127">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="86952-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="86952-128">Indica se a operação requer uma transação.</span><span class="sxs-lookup"><span data-stu-id="86952-128">Indicates whether the operation requires a transaction.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="86952-129">Requisitos</span><span class="sxs-lookup"><span data-stu-id="86952-129">Requirements</span></span>  
  
|<span data-ttu-id="86952-130">MOF</span><span class="sxs-lookup"><span data-stu-id="86952-130">MOF</span></span>|<span data-ttu-id="86952-131">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="86952-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="86952-132">Namespace</span><span class="sxs-lookup"><span data-stu-id="86952-132">Namespace</span></span>|<span data-ttu-id="86952-133">Definido em root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="86952-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="86952-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="86952-134">See Also</span></span>  
 <xref:System.ServiceModel.OperationBehaviorAttribute>
