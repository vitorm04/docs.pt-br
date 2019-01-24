---
title: OperationBehaviorAttribute
ms.date: 03/30/2017
ms.assetid: 8c9b0755-9e83-411f-bdcb-61a586022797
ms.openlocfilehash: d0bf59e6064748a045f761777a2f8f3e88f1cb5a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54504321"
---
# <a name="operationbehaviorattribute"></a><span data-ttu-id="3302b-102">OperationBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="3302b-102">OperationBehaviorAttribute</span></span>
<span data-ttu-id="3302b-103">OperationBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="3302b-103">OperationBehaviorAttribute</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3302b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3302b-104">Syntax</span></span>  
  
```csharp
class OperationBehaviorAttribute : Behavior  
{  
  boolean AutoDisposeParameters;  
  string Impersonation;  
  string ReleaseInstanceMode;  
  boolean TransactionAutoComplete;  
  boolean TransactionScopeRequired;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="3302b-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="3302b-105">Methods</span></span>  
 <span data-ttu-id="3302b-106">A classe OperationBehaviorAttribute não define quaisquer métodos.</span><span class="sxs-lookup"><span data-stu-id="3302b-106">The OperationBehaviorAttribute class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="3302b-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="3302b-107">Properties</span></span>  
 <span data-ttu-id="3302b-108">A classe OperationBehaviorAttribute tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="3302b-108">The OperationBehaviorAttribute class has the following properties:</span></span>  
  
### <a name="autodisposeparameters"></a><span data-ttu-id="3302b-109">AutoDisposeParameters</span><span class="sxs-lookup"><span data-stu-id="3302b-109">AutoDisposeParameters</span></span>  
 <span data-ttu-id="3302b-110">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="3302b-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="3302b-111">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="3302b-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3302b-112">O estado do recurso auto-dispose para parâmetros.</span><span class="sxs-lookup"><span data-stu-id="3302b-112">The state of the auto-dispose feature for parameters.</span></span>  
  
### <a name="impersonation"></a><span data-ttu-id="3302b-113">Representação</span><span class="sxs-lookup"><span data-stu-id="3302b-113">Impersonation</span></span>  
 <span data-ttu-id="3302b-114">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="3302b-114">Data type: string</span></span>  
  
 <span data-ttu-id="3302b-115">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="3302b-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3302b-116">Indica o nível de representação do chamador com suporte pela operação.</span><span class="sxs-lookup"><span data-stu-id="3302b-116">Indicates the level of caller impersonation that the operation supports.</span></span>  
  
### <a name="releaseinstancemode"></a><span data-ttu-id="3302b-117">ReleaseInstanceMode</span><span class="sxs-lookup"><span data-stu-id="3302b-117">ReleaseInstanceMode</span></span>  
 <span data-ttu-id="3302b-118">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="3302b-118">Data type: string</span></span>  
  
 <span data-ttu-id="3302b-119">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="3302b-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3302b-120">Indica quando no decorrer de uma invocação de operação para reciclar o objeto.</span><span class="sxs-lookup"><span data-stu-id="3302b-120">Indicates when in the course of an operation invocation to recycle the object.</span></span>  
  
### <a name="transactionautocomplete"></a><span data-ttu-id="3302b-121">TransactionAutoComplete</span><span class="sxs-lookup"><span data-stu-id="3302b-121">TransactionAutoComplete</span></span>  
 <span data-ttu-id="3302b-122">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="3302b-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="3302b-123">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="3302b-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3302b-124">Indica se é necessário confirmar a transação atual automaticamente se não ocorrer nenhuma exceção sem tratamento.</span><span class="sxs-lookup"><span data-stu-id="3302b-124">Indicates whether to automatically commit the current transaction if no unhandled exceptions occur.</span></span>  
  
### <a name="transactionscoperequired"></a><span data-ttu-id="3302b-125">TransactionScopeRequired</span><span class="sxs-lookup"><span data-stu-id="3302b-125">TransactionScopeRequired</span></span>  
 <span data-ttu-id="3302b-126">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="3302b-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="3302b-127">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="3302b-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3302b-128">Indica se a operação requer uma transação.</span><span class="sxs-lookup"><span data-stu-id="3302b-128">Indicates whether the operation requires a transaction.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3302b-129">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3302b-129">Requirements</span></span>  
  
|<span data-ttu-id="3302b-130">MOF</span><span class="sxs-lookup"><span data-stu-id="3302b-130">MOF</span></span>|<span data-ttu-id="3302b-131">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="3302b-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="3302b-132">Namespace</span><span class="sxs-lookup"><span data-stu-id="3302b-132">Namespace</span></span>|<span data-ttu-id="3302b-133">Definido no root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="3302b-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3302b-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3302b-134">See also</span></span>
- <xref:System.ServiceModel.OperationBehaviorAttribute>
