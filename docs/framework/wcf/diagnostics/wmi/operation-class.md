---
title: Classe de operação
ms.date: 03/30/2017
ms.assetid: b19d1496-ef06-4d0c-b2ae-e728ec00cca0
ms.openlocfilehash: 9696a7f026e54afacb5ccbfa8703a2ba617a9f3d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59973194"
---
# <a name="operation-class"></a><span data-ttu-id="ac3b5-102">Classe de operação</span><span class="sxs-lookup"><span data-stu-id="ac3b5-102">Operation class</span></span>
<span data-ttu-id="ac3b5-103">Operação</span><span class="sxs-lookup"><span data-stu-id="ac3b5-103">Operation</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac3b5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ac3b5-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="ac3b5-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="ac3b5-105">Methods</span></span>  
 <span data-ttu-id="ac3b5-106">A classe de operação não define quaisquer métodos.</span><span class="sxs-lookup"><span data-stu-id="ac3b5-106">The Operation class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="ac3b5-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="ac3b5-107">Properties</span></span>  
 <span data-ttu-id="ac3b5-108">A classe de operação tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="ac3b5-108">The Operation class has the following properties:</span></span>  
  
### <a name="action"></a><span data-ttu-id="ac3b5-109">Ação</span><span class="sxs-lookup"><span data-stu-id="ac3b5-109">Action</span></span>  
 <span data-ttu-id="ac3b5-110">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="ac3b5-110">Data type: string</span></span>  
  
 <span data-ttu-id="ac3b5-111">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="ac3b5-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ac3b5-112">A ação WS-Addressing da mensagem de solicitação.</span><span class="sxs-lookup"><span data-stu-id="ac3b5-112">The WS-Addressing action of the request message.</span></span>  
  
### <a name="asyncpattern"></a><span data-ttu-id="ac3b5-113">AsyncPattern</span><span class="sxs-lookup"><span data-stu-id="ac3b5-113">AsyncPattern</span></span>  
 <span data-ttu-id="ac3b5-114">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="ac3b5-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="ac3b5-115">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="ac3b5-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ac3b5-116">Indica que uma operação é implementada de forma assíncrona usando um `Begin`[colchetes de abertura/fechamento] e `End`par de métodos de [colchetes angulares de abertura/fechamento] em um contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="ac3b5-116">Indicates that an operation is implemented asynchronously using a `Begin`[open/close angle brackets] and `End`[open/close angle brackets] method pair in a service contract.</span></span>  
  
### <a name="behaviors"></a><span data-ttu-id="ac3b5-117">Comportamentos</span><span class="sxs-lookup"><span data-stu-id="ac3b5-117">Behaviors</span></span>  
 <span data-ttu-id="ac3b5-118">Tipo de dados: Matriz de comportamento</span><span class="sxs-lookup"><span data-stu-id="ac3b5-118">Data type: Behavior array</span></span>  
  
 <span data-ttu-id="ac3b5-119">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="ac3b5-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ac3b5-120">Os comportamentos associados a essa operação.</span><span class="sxs-lookup"><span data-stu-id="ac3b5-120">The behaviors associated with this operation.</span></span>  
  
### <a name="iscallback"></a><span data-ttu-id="ac3b5-121">IsCallback</span><span class="sxs-lookup"><span data-stu-id="ac3b5-121">IsCallback</span></span>  
 <span data-ttu-id="ac3b5-122">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="ac3b5-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="ac3b5-123">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="ac3b5-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ac3b5-124">True quando a operação é uma operação de retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="ac3b5-124">True when the operation is a callback operation.</span></span>  
  
### <a name="isinitiating"></a><span data-ttu-id="ac3b5-125">IsInitiating</span><span class="sxs-lookup"><span data-stu-id="ac3b5-125">IsInitiating</span></span>  
 <span data-ttu-id="ac3b5-126">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="ac3b5-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="ac3b5-127">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="ac3b5-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ac3b5-128">Indica se o método implementa uma operação que pode iniciar uma sessão no servidor.</span><span class="sxs-lookup"><span data-stu-id="ac3b5-128">Indicates whether the method implements an operation that can initiate a session on the server.</span></span>  
  
### <a name="isoneway"></a><span data-ttu-id="ac3b5-129">IsOneWay</span><span class="sxs-lookup"><span data-stu-id="ac3b5-129">IsOneWay</span></span>  
 <span data-ttu-id="ac3b5-130">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="ac3b5-130">Data type: boolean</span></span>  
  
 <span data-ttu-id="ac3b5-131">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="ac3b5-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ac3b5-132">Indica se uma operação retorna uma mensagem de resposta.</span><span class="sxs-lookup"><span data-stu-id="ac3b5-132">Indicates whether an operation returns a reply message.</span></span>  
  
### <a name="isterminating"></a><span data-ttu-id="ac3b5-133">IsTerminating</span><span class="sxs-lookup"><span data-stu-id="ac3b5-133">IsTerminating</span></span>  
 <span data-ttu-id="ac3b5-134">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="ac3b5-134">Data type: boolean</span></span>  
  
 <span data-ttu-id="ac3b5-135">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="ac3b5-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ac3b5-136">Indica se uma operação retorna uma mensagem de resposta.</span><span class="sxs-lookup"><span data-stu-id="ac3b5-136">Indicates whether an operation returns a reply message.</span></span>  
  
### <a name="methodsignature"></a><span data-ttu-id="ac3b5-137">MethodSignature</span><span class="sxs-lookup"><span data-stu-id="ac3b5-137">MethodSignature</span></span>  
 <span data-ttu-id="ac3b5-138">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="ac3b5-138">Data type: string</span></span>  
  
 <span data-ttu-id="ac3b5-139">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="ac3b5-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ac3b5-140">A assinatura do método da operação.</span><span class="sxs-lookup"><span data-stu-id="ac3b5-140">The method signature of the operation.</span></span>  
  
### <a name="name"></a><span data-ttu-id="ac3b5-141">Nome</span><span class="sxs-lookup"><span data-stu-id="ac3b5-141">Name</span></span>  
 <span data-ttu-id="ac3b5-142">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="ac3b5-142">Data type: string</span></span>  
  
 <span data-ttu-id="ac3b5-143">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="ac3b5-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ac3b5-144">O nome da operação.</span><span class="sxs-lookup"><span data-stu-id="ac3b5-144">The name of the operation.</span></span>  
  
### <a name="parametertypes"></a><span data-ttu-id="ac3b5-145">ParameterTypes</span><span class="sxs-lookup"><span data-stu-id="ac3b5-145">ParameterTypes</span></span>  
 <span data-ttu-id="ac3b5-146">Tipo de dados: matriz de cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="ac3b5-146">Data type: string array</span></span>  
  
 <span data-ttu-id="ac3b5-147">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="ac3b5-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ac3b5-148">Os tipos dos parâmetros da operação.</span><span class="sxs-lookup"><span data-stu-id="ac3b5-148">The types of the parameters of the operation.</span></span>  
  
### <a name="replyaction"></a><span data-ttu-id="ac3b5-149">ReplyAction</span><span class="sxs-lookup"><span data-stu-id="ac3b5-149">ReplyAction</span></span>  
 <span data-ttu-id="ac3b5-150">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="ac3b5-150">Data type: string</span></span>  
  
 <span data-ttu-id="ac3b5-151">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="ac3b5-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ac3b5-152">O valor da ação de SOAP para a mensagem de resposta da operação.</span><span class="sxs-lookup"><span data-stu-id="ac3b5-152">The value of the SOAP action for the reply message of the operation.</span></span>  
  
### <a name="returntype"></a><span data-ttu-id="ac3b5-153">Tipoderetorno</span><span class="sxs-lookup"><span data-stu-id="ac3b5-153">ReturnType</span></span>  
 <span data-ttu-id="ac3b5-154">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="ac3b5-154">Data type: string</span></span>  
  
 <span data-ttu-id="ac3b5-155">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="ac3b5-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ac3b5-156">O tipo de retorno da operação.</span><span class="sxs-lookup"><span data-stu-id="ac3b5-156">The return type of the operation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ac3b5-157">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ac3b5-157">Requirements</span></span>  
  
|<span data-ttu-id="ac3b5-158">MOF</span><span class="sxs-lookup"><span data-stu-id="ac3b5-158">MOF</span></span>|<span data-ttu-id="ac3b5-159">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="ac3b5-159">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="ac3b5-160">Namespace</span><span class="sxs-lookup"><span data-stu-id="ac3b5-160">Namespace</span></span>|<span data-ttu-id="ac3b5-161">Definido no root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="ac3b5-161">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ac3b5-162">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ac3b5-162">See also</span></span>

- <xref:System.ServiceModel.Description.OperationDescription>
