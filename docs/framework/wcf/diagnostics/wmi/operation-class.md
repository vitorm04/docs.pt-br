---
title: "Classe de operação"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b19d1496-ef06-4d0c-b2ae-e728ec00cca0
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 54566bc452baa2e02cef7d8d13d29fcd5864c95c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="operation-class"></a><span data-ttu-id="b4374-102">Classe de operação</span><span class="sxs-lookup"><span data-stu-id="b4374-102">Operation class</span></span>
<span data-ttu-id="b4374-103">Operação</span><span class="sxs-lookup"><span data-stu-id="b4374-103">Operation</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4374-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b4374-104">Syntax</span></span>  
  
```  
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
  
## <a name="methods"></a><span data-ttu-id="b4374-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="b4374-105">Methods</span></span>  
 <span data-ttu-id="b4374-106">A classe de operação não define nenhum método.</span><span class="sxs-lookup"><span data-stu-id="b4374-106">The Operation class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="b4374-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="b4374-107">Properties</span></span>  
 <span data-ttu-id="b4374-108">A classe de operação tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="b4374-108">The Operation class has the following properties:</span></span>  
  
### <a name="action"></a><span data-ttu-id="b4374-109">Ação</span><span class="sxs-lookup"><span data-stu-id="b4374-109">Action</span></span>  
 <span data-ttu-id="b4374-110">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="b4374-110">Data type: string</span></span>  
  
 <span data-ttu-id="b4374-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="b4374-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b4374-112">A ação WS-Addressing da mensagem de solicitação.</span><span class="sxs-lookup"><span data-stu-id="b4374-112">The WS-Addressing action of the request message.</span></span>  
  
### <a name="asyncpattern"></a><span data-ttu-id="b4374-113">AsyncPattern</span><span class="sxs-lookup"><span data-stu-id="b4374-113">AsyncPattern</span></span>  
 <span data-ttu-id="b4374-114">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="b4374-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="b4374-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="b4374-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b4374-116">Indica que uma operação é implementada de forma assíncrona usando um `Begin`[colchetes de abertura/fechamento] e `End`par de métodos de [colchetes angulares de abertura/fechamento] em um contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="b4374-116">Indicates that an operation is implemented asynchronously using a `Begin`[open/close angle brackets] and `End`[open/close angle brackets] method pair in a service contract.</span></span>  
  
### <a name="behaviors"></a><span data-ttu-id="b4374-117">Comportamentos</span><span class="sxs-lookup"><span data-stu-id="b4374-117">Behaviors</span></span>  
 <span data-ttu-id="b4374-118">Tipo de dados: matriz de comportamento</span><span class="sxs-lookup"><span data-stu-id="b4374-118">Data type: Behavior array</span></span>  
  
 <span data-ttu-id="b4374-119">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="b4374-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b4374-120">Os comportamentos associados a essa operação.</span><span class="sxs-lookup"><span data-stu-id="b4374-120">The behaviors associated with this operation.</span></span>  
  
### <a name="iscallback"></a><span data-ttu-id="b4374-121">IsCallback</span><span class="sxs-lookup"><span data-stu-id="b4374-121">IsCallback</span></span>  
 <span data-ttu-id="b4374-122">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="b4374-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="b4374-123">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="b4374-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b4374-124">Verdadeiro quando a operação é uma operação de retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="b4374-124">True when the operation is a callback operation.</span></span>  
  
### <a name="isinitiating"></a><span data-ttu-id="b4374-125">IsInitiating</span><span class="sxs-lookup"><span data-stu-id="b4374-125">IsInitiating</span></span>  
 <span data-ttu-id="b4374-126">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="b4374-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="b4374-127">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="b4374-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b4374-128">Indica se o método implementa uma operação que pode iniciar uma sessão no servidor.</span><span class="sxs-lookup"><span data-stu-id="b4374-128">Indicates whether the method implements an operation that can initiate a session on the server.</span></span>  
  
### <a name="isoneway"></a><span data-ttu-id="b4374-129">IsOneWay</span><span class="sxs-lookup"><span data-stu-id="b4374-129">IsOneWay</span></span>  
 <span data-ttu-id="b4374-130">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="b4374-130">Data type: boolean</span></span>  
  
 <span data-ttu-id="b4374-131">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="b4374-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b4374-132">Indica se uma operação retorna uma mensagem de resposta.</span><span class="sxs-lookup"><span data-stu-id="b4374-132">Indicates whether an operation returns a reply message.</span></span>  
  
### <a name="isterminating"></a><span data-ttu-id="b4374-133">IsTerminating</span><span class="sxs-lookup"><span data-stu-id="b4374-133">IsTerminating</span></span>  
 <span data-ttu-id="b4374-134">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="b4374-134">Data type: boolean</span></span>  
  
 <span data-ttu-id="b4374-135">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="b4374-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b4374-136">Indica se uma operação retorna uma mensagem de resposta.</span><span class="sxs-lookup"><span data-stu-id="b4374-136">Indicates whether an operation returns a reply message.</span></span>  
  
### <a name="methodsignature"></a><span data-ttu-id="b4374-137">MethodSignature</span><span class="sxs-lookup"><span data-stu-id="b4374-137">MethodSignature</span></span>  
 <span data-ttu-id="b4374-138">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="b4374-138">Data type: string</span></span>  
  
 <span data-ttu-id="b4374-139">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="b4374-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b4374-140">A assinatura de método da operação.</span><span class="sxs-lookup"><span data-stu-id="b4374-140">The method signature of the operation.</span></span>  
  
### <a name="name"></a><span data-ttu-id="b4374-141">Nome</span><span class="sxs-lookup"><span data-stu-id="b4374-141">Name</span></span>  
 <span data-ttu-id="b4374-142">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="b4374-142">Data type: string</span></span>  
  
 <span data-ttu-id="b4374-143">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="b4374-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b4374-144">O nome da operação.</span><span class="sxs-lookup"><span data-stu-id="b4374-144">The name of the operation.</span></span>  
  
### <a name="parametertypes"></a><span data-ttu-id="b4374-145">ParameterTypes</span><span class="sxs-lookup"><span data-stu-id="b4374-145">ParameterTypes</span></span>  
 <span data-ttu-id="b4374-146">Tipo de dados: matriz de cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="b4374-146">Data type: string array</span></span>  
  
 <span data-ttu-id="b4374-147">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="b4374-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b4374-148">Os tipos dos parâmetros da operação.</span><span class="sxs-lookup"><span data-stu-id="b4374-148">The types of the parameters of the operation.</span></span>  
  
### <a name="replyaction"></a><span data-ttu-id="b4374-149">ReplyAction</span><span class="sxs-lookup"><span data-stu-id="b4374-149">ReplyAction</span></span>  
 <span data-ttu-id="b4374-150">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="b4374-150">Data type: string</span></span>  
  
 <span data-ttu-id="b4374-151">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="b4374-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b4374-152">O valor da ação SOAP para a mensagem de resposta da operação.</span><span class="sxs-lookup"><span data-stu-id="b4374-152">The value of the SOAP action for the reply message of the operation.</span></span>  
  
### <a name="returntype"></a><span data-ttu-id="b4374-153">Tipoderetorno</span><span class="sxs-lookup"><span data-stu-id="b4374-153">ReturnType</span></span>  
 <span data-ttu-id="b4374-154">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="b4374-154">Data type: string</span></span>  
  
 <span data-ttu-id="b4374-155">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="b4374-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b4374-156">O tipo de retorno da operação.</span><span class="sxs-lookup"><span data-stu-id="b4374-156">The return type of the operation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b4374-157">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b4374-157">Requirements</span></span>  
  
|<span data-ttu-id="b4374-158">MOF</span><span class="sxs-lookup"><span data-stu-id="b4374-158">MOF</span></span>|<span data-ttu-id="b4374-159">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="b4374-159">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="b4374-160">Namespace</span><span class="sxs-lookup"><span data-stu-id="b4374-160">Namespace</span></span>|<span data-ttu-id="b4374-161">Definido em root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="b4374-161">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b4374-162">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b4374-162">See Also</span></span>  
 <xref:System.ServiceModel.Description.OperationDescription>
