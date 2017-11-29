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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: fd01c5c4d37f5c0ec5673dc9aa4a47cb8affbc29
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="operationbehaviorattribute"></a><span data-ttu-id="51fd5-102">OperationBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="51fd5-102">OperationBehaviorAttribute</span></span>
<span data-ttu-id="51fd5-103">OperationBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="51fd5-103">OperationBehaviorAttribute</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51fd5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="51fd5-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="51fd5-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="51fd5-105">Methods</span></span>  
 <span data-ttu-id="51fd5-106">A classe OperationBehaviorAttribute não define nenhum método.</span><span class="sxs-lookup"><span data-stu-id="51fd5-106">The OperationBehaviorAttribute class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="51fd5-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="51fd5-107">Properties</span></span>  
 <span data-ttu-id="51fd5-108">A classe OperationBehaviorAttribute tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="51fd5-108">The OperationBehaviorAttribute class has the following properties:</span></span>  
  
### <a name="autodisposeparameters"></a><span data-ttu-id="51fd5-109">AutoDisposeParameters</span><span class="sxs-lookup"><span data-stu-id="51fd5-109">AutoDisposeParameters</span></span>  
 <span data-ttu-id="51fd5-110">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="51fd5-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="51fd5-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="51fd5-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="51fd5-112">O estado do recurso auto-dispose para parâmetros.</span><span class="sxs-lookup"><span data-stu-id="51fd5-112">The state of the auto-dispose feature for parameters.</span></span>  
  
### <a name="impersonation"></a><span data-ttu-id="51fd5-113">Representação</span><span class="sxs-lookup"><span data-stu-id="51fd5-113">Impersonation</span></span>  
 <span data-ttu-id="51fd5-114">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="51fd5-114">Data type: string</span></span>  
  
 <span data-ttu-id="51fd5-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="51fd5-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="51fd5-116">Indica o nível de representação do chamador que a operação oferece suporte.</span><span class="sxs-lookup"><span data-stu-id="51fd5-116">Indicates the level of caller impersonation that the operation supports.</span></span>  
  
### <a name="releaseinstancemode"></a><span data-ttu-id="51fd5-117">ReleaseInstanceMode</span><span class="sxs-lookup"><span data-stu-id="51fd5-117">ReleaseInstanceMode</span></span>  
 <span data-ttu-id="51fd5-118">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="51fd5-118">Data type: string</span></span>  
  
 <span data-ttu-id="51fd5-119">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="51fd5-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="51fd5-120">Indica quando no curso de uma invocação de operação reciclar o objeto.</span><span class="sxs-lookup"><span data-stu-id="51fd5-120">Indicates when in the course of an operation invocation to recycle the object.</span></span>  
  
### <a name="transactionautocomplete"></a><span data-ttu-id="51fd5-121">TransactionAutoComplete</span><span class="sxs-lookup"><span data-stu-id="51fd5-121">TransactionAutoComplete</span></span>  
 <span data-ttu-id="51fd5-122">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="51fd5-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="51fd5-123">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="51fd5-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="51fd5-124">Indica se deve confirmar a transação atual automaticamente se nenhuma exceção não tratada ocorrer.</span><span class="sxs-lookup"><span data-stu-id="51fd5-124">Indicates whether to automatically commit the current transaction if no unhandled exceptions occur.</span></span>  
  
### <a name="transactionscoperequired"></a><span data-ttu-id="51fd5-125">TransactionScopeRequired</span><span class="sxs-lookup"><span data-stu-id="51fd5-125">TransactionScopeRequired</span></span>  
 <span data-ttu-id="51fd5-126">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="51fd5-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="51fd5-127">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="51fd5-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="51fd5-128">Indica se a operação requer uma transação.</span><span class="sxs-lookup"><span data-stu-id="51fd5-128">Indicates whether the operation requires a transaction.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="51fd5-129">Requisitos</span><span class="sxs-lookup"><span data-stu-id="51fd5-129">Requirements</span></span>  
  
|<span data-ttu-id="51fd5-130">MOF</span><span class="sxs-lookup"><span data-stu-id="51fd5-130">MOF</span></span>|<span data-ttu-id="51fd5-131">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="51fd5-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="51fd5-132">Namespace</span><span class="sxs-lookup"><span data-stu-id="51fd5-132">Namespace</span></span>|<span data-ttu-id="51fd5-133">Definido em root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="51fd5-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="51fd5-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="51fd5-134">See Also</span></span>  
 <xref:System.ServiceModel.OperationBehaviorAttribute>
