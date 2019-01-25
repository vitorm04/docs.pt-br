---
title: Classe de operação
ms.date: 03/30/2017
ms.assetid: b19d1496-ef06-4d0c-b2ae-e728ec00cca0
ms.openlocfilehash: 9453d67854bb8439891661b07e3ab3aa373e23eb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54668295"
---
# <a name="operation-class"></a><span data-ttu-id="5d20d-102">Classe de operação</span><span class="sxs-lookup"><span data-stu-id="5d20d-102">Operation class</span></span>
<span data-ttu-id="5d20d-103">Operação</span><span class="sxs-lookup"><span data-stu-id="5d20d-103">Operation</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d20d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5d20d-104">Syntax</span></span>  
  
```csharp
class Operation  
{  
  string Action;  
  boolean AsyncPattern;  
  Behavior Behaviors[];  
  boolean IsCallback;  
  boolean IsInitiating;  
  boolean IsOneWay;  
  boolean IsTerminating;  
  string MethodSignature;  
  string Name;  
  string ParameterTypes[];  
  string ReplyAction;  
  string ReturnType;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="5d20d-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="5d20d-105">Methods</span></span>  
 <span data-ttu-id="5d20d-106">A classe de operação não define quaisquer métodos.</span><span class="sxs-lookup"><span data-stu-id="5d20d-106">The Operation class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="5d20d-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="5d20d-107">Properties</span></span>  
 <span data-ttu-id="5d20d-108">A classe de operação tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="5d20d-108">The Operation class has the following properties:</span></span>  
  
### <a name="action"></a><span data-ttu-id="5d20d-109">Ação</span><span class="sxs-lookup"><span data-stu-id="5d20d-109">Action</span></span>  
 <span data-ttu-id="5d20d-110">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="5d20d-110">Data type: string</span></span>  
  
 <span data-ttu-id="5d20d-111">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="5d20d-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5d20d-112">A ação WS-Addressing da mensagem de solicitação.</span><span class="sxs-lookup"><span data-stu-id="5d20d-112">The WS-Addressing action of the request message.</span></span>  
  
### <a name="asyncpattern"></a><span data-ttu-id="5d20d-113">AsyncPattern</span><span class="sxs-lookup"><span data-stu-id="5d20d-113">AsyncPattern</span></span>  
 <span data-ttu-id="5d20d-114">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="5d20d-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="5d20d-115">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="5d20d-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5d20d-116">Indica que uma operação é implementada de forma assíncrona usando um `Begin`[colchetes de abertura/fechamento] e `End`par de métodos de [colchetes angulares de abertura/fechamento] em um contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="5d20d-116">Indicates that an operation is implemented asynchronously using a `Begin`[open/close angle brackets] and `End`[open/close angle brackets] method pair in a service contract.</span></span>  
  
### <a name="behaviors"></a><span data-ttu-id="5d20d-117">Comportamentos</span><span class="sxs-lookup"><span data-stu-id="5d20d-117">Behaviors</span></span>  
 <span data-ttu-id="5d20d-118">Tipo de dados: Matriz de comportamento</span><span class="sxs-lookup"><span data-stu-id="5d20d-118">Data type: Behavior array</span></span>  
  
 <span data-ttu-id="5d20d-119">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="5d20d-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5d20d-120">Os comportamentos associados a essa operação.</span><span class="sxs-lookup"><span data-stu-id="5d20d-120">The behaviors associated with this operation.</span></span>  
  
### <a name="iscallback"></a><span data-ttu-id="5d20d-121">IsCallback</span><span class="sxs-lookup"><span data-stu-id="5d20d-121">IsCallback</span></span>  
 <span data-ttu-id="5d20d-122">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="5d20d-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="5d20d-123">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="5d20d-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5d20d-124">True quando a operação é uma operação de retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="5d20d-124">True when the operation is a callback operation.</span></span>  
  
### <a name="isinitiating"></a><span data-ttu-id="5d20d-125">IsInitiating</span><span class="sxs-lookup"><span data-stu-id="5d20d-125">IsInitiating</span></span>  
 <span data-ttu-id="5d20d-126">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="5d20d-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="5d20d-127">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="5d20d-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5d20d-128">Indica se o método implementa uma operação que pode iniciar uma sessão no servidor.</span><span class="sxs-lookup"><span data-stu-id="5d20d-128">Indicates whether the method implements an operation that can initiate a session on the server.</span></span>  
  
### <a name="isoneway"></a><span data-ttu-id="5d20d-129">IsOneWay</span><span class="sxs-lookup"><span data-stu-id="5d20d-129">IsOneWay</span></span>  
 <span data-ttu-id="5d20d-130">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="5d20d-130">Data type: boolean</span></span>  
  
 <span data-ttu-id="5d20d-131">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="5d20d-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5d20d-132">Indica se uma operação retorna uma mensagem de resposta.</span><span class="sxs-lookup"><span data-stu-id="5d20d-132">Indicates whether an operation returns a reply message.</span></span>  
  
### <a name="isterminating"></a><span data-ttu-id="5d20d-133">IsTerminating</span><span class="sxs-lookup"><span data-stu-id="5d20d-133">IsTerminating</span></span>  
 <span data-ttu-id="5d20d-134">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="5d20d-134">Data type: boolean</span></span>  
  
 <span data-ttu-id="5d20d-135">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="5d20d-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5d20d-136">Indica se uma operação retorna uma mensagem de resposta.</span><span class="sxs-lookup"><span data-stu-id="5d20d-136">Indicates whether an operation returns a reply message.</span></span>  
  
### <a name="methodsignature"></a><span data-ttu-id="5d20d-137">MethodSignature</span><span class="sxs-lookup"><span data-stu-id="5d20d-137">MethodSignature</span></span>  
 <span data-ttu-id="5d20d-138">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="5d20d-138">Data type: string</span></span>  
  
 <span data-ttu-id="5d20d-139">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="5d20d-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5d20d-140">A assinatura do método da operação.</span><span class="sxs-lookup"><span data-stu-id="5d20d-140">The method signature of the operation.</span></span>  
  
### <a name="name"></a><span data-ttu-id="5d20d-141">Nome</span><span class="sxs-lookup"><span data-stu-id="5d20d-141">Name</span></span>  
 <span data-ttu-id="5d20d-142">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="5d20d-142">Data type: string</span></span>  
  
 <span data-ttu-id="5d20d-143">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="5d20d-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5d20d-144">O nome da operação.</span><span class="sxs-lookup"><span data-stu-id="5d20d-144">The name of the operation.</span></span>  
  
### <a name="parametertypes"></a><span data-ttu-id="5d20d-145">ParameterTypes</span><span class="sxs-lookup"><span data-stu-id="5d20d-145">ParameterTypes</span></span>  
 <span data-ttu-id="5d20d-146">Tipo de dados: matriz de cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="5d20d-146">Data type: string array</span></span>  
  
 <span data-ttu-id="5d20d-147">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="5d20d-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5d20d-148">Os tipos dos parâmetros da operação.</span><span class="sxs-lookup"><span data-stu-id="5d20d-148">The types of the parameters of the operation.</span></span>  
  
### <a name="replyaction"></a><span data-ttu-id="5d20d-149">ReplyAction</span><span class="sxs-lookup"><span data-stu-id="5d20d-149">ReplyAction</span></span>  
 <span data-ttu-id="5d20d-150">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="5d20d-150">Data type: string</span></span>  
  
 <span data-ttu-id="5d20d-151">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="5d20d-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5d20d-152">O valor da ação de SOAP para a mensagem de resposta da operação.</span><span class="sxs-lookup"><span data-stu-id="5d20d-152">The value of the SOAP action for the reply message of the operation.</span></span>  
  
### <a name="returntype"></a><span data-ttu-id="5d20d-153">Tipoderetorno</span><span class="sxs-lookup"><span data-stu-id="5d20d-153">ReturnType</span></span>  
 <span data-ttu-id="5d20d-154">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="5d20d-154">Data type: string</span></span>  
  
 <span data-ttu-id="5d20d-155">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="5d20d-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5d20d-156">O tipo de retorno da operação.</span><span class="sxs-lookup"><span data-stu-id="5d20d-156">The return type of the operation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5d20d-157">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5d20d-157">Requirements</span></span>  
  
|<span data-ttu-id="5d20d-158">MOF</span><span class="sxs-lookup"><span data-stu-id="5d20d-158">MOF</span></span>|<span data-ttu-id="5d20d-159">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="5d20d-159">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="5d20d-160">Namespace</span><span class="sxs-lookup"><span data-stu-id="5d20d-160">Namespace</span></span>|<span data-ttu-id="5d20d-161">Definido no root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="5d20d-161">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5d20d-162">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5d20d-162">See also</span></span>
- <xref:System.ServiceModel.Description.OperationDescription>
