---
title: OperationBehaviorAttribute
ms.date: 03/30/2017
ms.assetid: 8c9b0755-9e83-411f-bdcb-61a586022797
ms.openlocfilehash: 4f731d146885265d9f956c182f1bebdba5db924b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33486865"
---
# <a name="operationbehaviorattribute"></a><span data-ttu-id="8e081-102">OperationBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="8e081-102">OperationBehaviorAttribute</span></span>
<span data-ttu-id="8e081-103">OperationBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="8e081-103">OperationBehaviorAttribute</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e081-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8e081-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="8e081-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="8e081-105">Methods</span></span>  
 <span data-ttu-id="8e081-106">A classe OperationBehaviorAttribute não define nenhum método.</span><span class="sxs-lookup"><span data-stu-id="8e081-106">The OperationBehaviorAttribute class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="8e081-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="8e081-107">Properties</span></span>  
 <span data-ttu-id="8e081-108">A classe OperationBehaviorAttribute tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="8e081-108">The OperationBehaviorAttribute class has the following properties:</span></span>  
  
### <a name="autodisposeparameters"></a><span data-ttu-id="8e081-109">AutoDisposeParameters</span><span class="sxs-lookup"><span data-stu-id="8e081-109">AutoDisposeParameters</span></span>  
 <span data-ttu-id="8e081-110">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="8e081-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="8e081-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="8e081-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8e081-112">O estado do recurso auto-dispose para parâmetros.</span><span class="sxs-lookup"><span data-stu-id="8e081-112">The state of the auto-dispose feature for parameters.</span></span>  
  
### <a name="impersonation"></a><span data-ttu-id="8e081-113">Representação</span><span class="sxs-lookup"><span data-stu-id="8e081-113">Impersonation</span></span>  
 <span data-ttu-id="8e081-114">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="8e081-114">Data type: string</span></span>  
  
 <span data-ttu-id="8e081-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="8e081-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8e081-116">Indica o nível de representação do chamador que a operação oferece suporte.</span><span class="sxs-lookup"><span data-stu-id="8e081-116">Indicates the level of caller impersonation that the operation supports.</span></span>  
  
### <a name="releaseinstancemode"></a><span data-ttu-id="8e081-117">ReleaseInstanceMode</span><span class="sxs-lookup"><span data-stu-id="8e081-117">ReleaseInstanceMode</span></span>  
 <span data-ttu-id="8e081-118">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="8e081-118">Data type: string</span></span>  
  
 <span data-ttu-id="8e081-119">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="8e081-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8e081-120">Indica quando no curso de uma invocação de operação reciclar o objeto.</span><span class="sxs-lookup"><span data-stu-id="8e081-120">Indicates when in the course of an operation invocation to recycle the object.</span></span>  
  
### <a name="transactionautocomplete"></a><span data-ttu-id="8e081-121">TransactionAutoComplete</span><span class="sxs-lookup"><span data-stu-id="8e081-121">TransactionAutoComplete</span></span>  
 <span data-ttu-id="8e081-122">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="8e081-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="8e081-123">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="8e081-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8e081-124">Indica se deve confirmar a transação atual automaticamente se nenhuma exceção não tratada ocorrer.</span><span class="sxs-lookup"><span data-stu-id="8e081-124">Indicates whether to automatically commit the current transaction if no unhandled exceptions occur.</span></span>  
  
### <a name="transactionscoperequired"></a><span data-ttu-id="8e081-125">TransactionScopeRequired</span><span class="sxs-lookup"><span data-stu-id="8e081-125">TransactionScopeRequired</span></span>  
 <span data-ttu-id="8e081-126">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="8e081-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="8e081-127">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="8e081-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8e081-128">Indica se a operação requer uma transação.</span><span class="sxs-lookup"><span data-stu-id="8e081-128">Indicates whether the operation requires a transaction.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8e081-129">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8e081-129">Requirements</span></span>  
  
|<span data-ttu-id="8e081-130">MOF</span><span class="sxs-lookup"><span data-stu-id="8e081-130">MOF</span></span>|<span data-ttu-id="8e081-131">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="8e081-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="8e081-132">Namespace</span><span class="sxs-lookup"><span data-stu-id="8e081-132">Namespace</span></span>|<span data-ttu-id="8e081-133">Definido em root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="8e081-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8e081-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8e081-134">See Also</span></span>  
 <xref:System.ServiceModel.OperationBehaviorAttribute>
