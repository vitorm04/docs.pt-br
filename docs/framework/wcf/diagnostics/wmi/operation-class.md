---
title: Classe de operação
ms.date: 03/30/2017
ms.assetid: b19d1496-ef06-4d0c-b2ae-e728ec00cca0
ms.openlocfilehash: 9696a7f026e54afacb5ccbfa8703a2ba617a9f3d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59165068"
---
# <a name="operation-class"></a><span data-ttu-id="66b4c-102">Classe de operação</span><span class="sxs-lookup"><span data-stu-id="66b4c-102">Operation class</span></span>
<span data-ttu-id="66b4c-103">Operação</span><span class="sxs-lookup"><span data-stu-id="66b4c-103">Operation</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66b4c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="66b4c-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="66b4c-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="66b4c-105">Methods</span></span>  
 <span data-ttu-id="66b4c-106">A classe de operação não define quaisquer métodos.</span><span class="sxs-lookup"><span data-stu-id="66b4c-106">The Operation class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="66b4c-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="66b4c-107">Properties</span></span>  
 <span data-ttu-id="66b4c-108">A classe de operação tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="66b4c-108">The Operation class has the following properties:</span></span>  
  
### <a name="action"></a><span data-ttu-id="66b4c-109">Ação</span><span class="sxs-lookup"><span data-stu-id="66b4c-109">Action</span></span>  
 <span data-ttu-id="66b4c-110">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="66b4c-110">Data type: string</span></span>  
  
 <span data-ttu-id="66b4c-111">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="66b4c-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="66b4c-112">A ação WS-Addressing da mensagem de solicitação.</span><span class="sxs-lookup"><span data-stu-id="66b4c-112">The WS-Addressing action of the request message.</span></span>  
  
### <a name="asyncpattern"></a><span data-ttu-id="66b4c-113">AsyncPattern</span><span class="sxs-lookup"><span data-stu-id="66b4c-113">AsyncPattern</span></span>  
 <span data-ttu-id="66b4c-114">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="66b4c-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="66b4c-115">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="66b4c-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="66b4c-116">Indica que uma operação é implementada de forma assíncrona usando um `Begin`[colchetes de abertura/fechamento] e `End`par de métodos de [colchetes angulares de abertura/fechamento] em um contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="66b4c-116">Indicates that an operation is implemented asynchronously using a `Begin`[open/close angle brackets] and `End`[open/close angle brackets] method pair in a service contract.</span></span>  
  
### <a name="behaviors"></a><span data-ttu-id="66b4c-117">Comportamentos</span><span class="sxs-lookup"><span data-stu-id="66b4c-117">Behaviors</span></span>  
 <span data-ttu-id="66b4c-118">Tipo de dados: Matriz de comportamento</span><span class="sxs-lookup"><span data-stu-id="66b4c-118">Data type: Behavior array</span></span>  
  
 <span data-ttu-id="66b4c-119">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="66b4c-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="66b4c-120">Os comportamentos associados a essa operação.</span><span class="sxs-lookup"><span data-stu-id="66b4c-120">The behaviors associated with this operation.</span></span>  
  
### <a name="iscallback"></a><span data-ttu-id="66b4c-121">IsCallback</span><span class="sxs-lookup"><span data-stu-id="66b4c-121">IsCallback</span></span>  
 <span data-ttu-id="66b4c-122">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="66b4c-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="66b4c-123">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="66b4c-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="66b4c-124">True quando a operação é uma operação de retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="66b4c-124">True when the operation is a callback operation.</span></span>  
  
### <a name="isinitiating"></a><span data-ttu-id="66b4c-125">IsInitiating</span><span class="sxs-lookup"><span data-stu-id="66b4c-125">IsInitiating</span></span>  
 <span data-ttu-id="66b4c-126">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="66b4c-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="66b4c-127">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="66b4c-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="66b4c-128">Indica se o método implementa uma operação que pode iniciar uma sessão no servidor.</span><span class="sxs-lookup"><span data-stu-id="66b4c-128">Indicates whether the method implements an operation that can initiate a session on the server.</span></span>  
  
### <a name="isoneway"></a><span data-ttu-id="66b4c-129">IsOneWay</span><span class="sxs-lookup"><span data-stu-id="66b4c-129">IsOneWay</span></span>  
 <span data-ttu-id="66b4c-130">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="66b4c-130">Data type: boolean</span></span>  
  
 <span data-ttu-id="66b4c-131">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="66b4c-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="66b4c-132">Indica se uma operação retorna uma mensagem de resposta.</span><span class="sxs-lookup"><span data-stu-id="66b4c-132">Indicates whether an operation returns a reply message.</span></span>  
  
### <a name="isterminating"></a><span data-ttu-id="66b4c-133">IsTerminating</span><span class="sxs-lookup"><span data-stu-id="66b4c-133">IsTerminating</span></span>  
 <span data-ttu-id="66b4c-134">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="66b4c-134">Data type: boolean</span></span>  
  
 <span data-ttu-id="66b4c-135">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="66b4c-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="66b4c-136">Indica se uma operação retorna uma mensagem de resposta.</span><span class="sxs-lookup"><span data-stu-id="66b4c-136">Indicates whether an operation returns a reply message.</span></span>  
  
### <a name="methodsignature"></a><span data-ttu-id="66b4c-137">MethodSignature</span><span class="sxs-lookup"><span data-stu-id="66b4c-137">MethodSignature</span></span>  
 <span data-ttu-id="66b4c-138">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="66b4c-138">Data type: string</span></span>  
  
 <span data-ttu-id="66b4c-139">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="66b4c-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="66b4c-140">A assinatura do método da operação.</span><span class="sxs-lookup"><span data-stu-id="66b4c-140">The method signature of the operation.</span></span>  
  
### <a name="name"></a><span data-ttu-id="66b4c-141">Nome</span><span class="sxs-lookup"><span data-stu-id="66b4c-141">Name</span></span>  
 <span data-ttu-id="66b4c-142">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="66b4c-142">Data type: string</span></span>  
  
 <span data-ttu-id="66b4c-143">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="66b4c-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="66b4c-144">O nome da operação.</span><span class="sxs-lookup"><span data-stu-id="66b4c-144">The name of the operation.</span></span>  
  
### <a name="parametertypes"></a><span data-ttu-id="66b4c-145">ParameterTypes</span><span class="sxs-lookup"><span data-stu-id="66b4c-145">ParameterTypes</span></span>  
 <span data-ttu-id="66b4c-146">Tipo de dados: matriz de cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="66b4c-146">Data type: string array</span></span>  
  
 <span data-ttu-id="66b4c-147">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="66b4c-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="66b4c-148">Os tipos dos parâmetros da operação.</span><span class="sxs-lookup"><span data-stu-id="66b4c-148">The types of the parameters of the operation.</span></span>  
  
### <a name="replyaction"></a><span data-ttu-id="66b4c-149">ReplyAction</span><span class="sxs-lookup"><span data-stu-id="66b4c-149">ReplyAction</span></span>  
 <span data-ttu-id="66b4c-150">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="66b4c-150">Data type: string</span></span>  
  
 <span data-ttu-id="66b4c-151">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="66b4c-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="66b4c-152">O valor da ação de SOAP para a mensagem de resposta da operação.</span><span class="sxs-lookup"><span data-stu-id="66b4c-152">The value of the SOAP action for the reply message of the operation.</span></span>  
  
### <a name="returntype"></a><span data-ttu-id="66b4c-153">Tipoderetorno</span><span class="sxs-lookup"><span data-stu-id="66b4c-153">ReturnType</span></span>  
 <span data-ttu-id="66b4c-154">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="66b4c-154">Data type: string</span></span>  
  
 <span data-ttu-id="66b4c-155">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="66b4c-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="66b4c-156">O tipo de retorno da operação.</span><span class="sxs-lookup"><span data-stu-id="66b4c-156">The return type of the operation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="66b4c-157">Requisitos</span><span class="sxs-lookup"><span data-stu-id="66b4c-157">Requirements</span></span>  
  
|<span data-ttu-id="66b4c-158">MOF</span><span class="sxs-lookup"><span data-stu-id="66b4c-158">MOF</span></span>|<span data-ttu-id="66b4c-159">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="66b4c-159">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="66b4c-160">Namespace</span><span class="sxs-lookup"><span data-stu-id="66b4c-160">Namespace</span></span>|<span data-ttu-id="66b4c-161">Definido no root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="66b4c-161">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="66b4c-162">Consulte também</span><span class="sxs-lookup"><span data-stu-id="66b4c-162">See also</span></span>

- <xref:System.ServiceModel.Description.OperationDescription>
