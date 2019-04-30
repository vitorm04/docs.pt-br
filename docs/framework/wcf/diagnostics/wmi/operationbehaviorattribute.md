---
title: OperationBehaviorAttribute
ms.date: 03/30/2017
ms.assetid: 8c9b0755-9e83-411f-bdcb-61a586022797
ms.openlocfilehash: 79601308c66abe43dd5a7f72bd2a05b9d2346c2b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61963040"
---
# <a name="operationbehaviorattribute"></a><span data-ttu-id="7b030-102">OperationBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="7b030-102">OperationBehaviorAttribute</span></span>
<span data-ttu-id="7b030-103">OperationBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="7b030-103">OperationBehaviorAttribute</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b030-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7b030-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="7b030-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="7b030-105">Methods</span></span>  
 <span data-ttu-id="7b030-106">A classe OperationBehaviorAttribute não define quaisquer métodos.</span><span class="sxs-lookup"><span data-stu-id="7b030-106">The OperationBehaviorAttribute class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="7b030-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="7b030-107">Properties</span></span>  
 <span data-ttu-id="7b030-108">A classe OperationBehaviorAttribute tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="7b030-108">The OperationBehaviorAttribute class has the following properties:</span></span>  
  
### <a name="autodisposeparameters"></a><span data-ttu-id="7b030-109">AutoDisposeParameters</span><span class="sxs-lookup"><span data-stu-id="7b030-109">AutoDisposeParameters</span></span>  
 <span data-ttu-id="7b030-110">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="7b030-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="7b030-111">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="7b030-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7b030-112">O estado do recurso auto-dispose para parâmetros.</span><span class="sxs-lookup"><span data-stu-id="7b030-112">The state of the auto-dispose feature for parameters.</span></span>  
  
### <a name="impersonation"></a><span data-ttu-id="7b030-113">Representação</span><span class="sxs-lookup"><span data-stu-id="7b030-113">Impersonation</span></span>  
 <span data-ttu-id="7b030-114">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="7b030-114">Data type: string</span></span>  
  
 <span data-ttu-id="7b030-115">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="7b030-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7b030-116">Indica o nível de representação do chamador com suporte pela operação.</span><span class="sxs-lookup"><span data-stu-id="7b030-116">Indicates the level of caller impersonation that the operation supports.</span></span>  
  
### <a name="releaseinstancemode"></a><span data-ttu-id="7b030-117">ReleaseInstanceMode</span><span class="sxs-lookup"><span data-stu-id="7b030-117">ReleaseInstanceMode</span></span>  
 <span data-ttu-id="7b030-118">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="7b030-118">Data type: string</span></span>  
  
 <span data-ttu-id="7b030-119">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="7b030-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7b030-120">Indica quando no decorrer de uma invocação de operação para reciclar o objeto.</span><span class="sxs-lookup"><span data-stu-id="7b030-120">Indicates when in the course of an operation invocation to recycle the object.</span></span>  
  
### <a name="transactionautocomplete"></a><span data-ttu-id="7b030-121">TransactionAutoComplete</span><span class="sxs-lookup"><span data-stu-id="7b030-121">TransactionAutoComplete</span></span>  
 <span data-ttu-id="7b030-122">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="7b030-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="7b030-123">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="7b030-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7b030-124">Indica se é necessário confirmar a transação atual automaticamente se não ocorrer nenhuma exceção sem tratamento.</span><span class="sxs-lookup"><span data-stu-id="7b030-124">Indicates whether to automatically commit the current transaction if no unhandled exceptions occur.</span></span>  
  
### <a name="transactionscoperequired"></a><span data-ttu-id="7b030-125">TransactionScopeRequired</span><span class="sxs-lookup"><span data-stu-id="7b030-125">TransactionScopeRequired</span></span>  
 <span data-ttu-id="7b030-126">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="7b030-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="7b030-127">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="7b030-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7b030-128">Indica se a operação requer uma transação.</span><span class="sxs-lookup"><span data-stu-id="7b030-128">Indicates whether the operation requires a transaction.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7b030-129">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7b030-129">Requirements</span></span>  
  
|<span data-ttu-id="7b030-130">MOF</span><span class="sxs-lookup"><span data-stu-id="7b030-130">MOF</span></span>|<span data-ttu-id="7b030-131">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="7b030-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="7b030-132">Namespace</span><span class="sxs-lookup"><span data-stu-id="7b030-132">Namespace</span></span>|<span data-ttu-id="7b030-133">Definido no root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="7b030-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7b030-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7b030-134">See also</span></span>

- <xref:System.ServiceModel.OperationBehaviorAttribute>
