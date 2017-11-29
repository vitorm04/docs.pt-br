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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 739f8309e7a01eeecf921b50fcde24417fbbc515
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="operation-class"></a><span data-ttu-id="a93f8-102">Classe de operação</span><span class="sxs-lookup"><span data-stu-id="a93f8-102">Operation class</span></span>
<span data-ttu-id="a93f8-103">Operação</span><span class="sxs-lookup"><span data-stu-id="a93f8-103">Operation</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a93f8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a93f8-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="a93f8-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="a93f8-105">Methods</span></span>  
 <span data-ttu-id="a93f8-106">A classe de operação não define nenhum método.</span><span class="sxs-lookup"><span data-stu-id="a93f8-106">The Operation class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="a93f8-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="a93f8-107">Properties</span></span>  
 <span data-ttu-id="a93f8-108">A classe de operação tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="a93f8-108">The Operation class has the following properties:</span></span>  
  
### <a name="action"></a><span data-ttu-id="a93f8-109">Ação</span><span class="sxs-lookup"><span data-stu-id="a93f8-109">Action</span></span>  
 <span data-ttu-id="a93f8-110">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="a93f8-110">Data type: string</span></span>  
  
 <span data-ttu-id="a93f8-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="a93f8-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a93f8-112">A ação WS-Addressing da mensagem de solicitação.</span><span class="sxs-lookup"><span data-stu-id="a93f8-112">The WS-Addressing action of the request message.</span></span>  
  
### <a name="asyncpattern"></a><span data-ttu-id="a93f8-113">AsyncPattern</span><span class="sxs-lookup"><span data-stu-id="a93f8-113">AsyncPattern</span></span>  
 <span data-ttu-id="a93f8-114">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="a93f8-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="a93f8-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="a93f8-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a93f8-116">Indica que uma operação é implementada de forma assíncrona usando um `Begin`[colchetes de abertura/fechamento] e `End`par de métodos de [colchetes angulares de abertura/fechamento] em um contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="a93f8-116">Indicates that an operation is implemented asynchronously using a `Begin`[open/close angle brackets] and `End`[open/close angle brackets] method pair in a service contract.</span></span>  
  
### <a name="behaviors"></a><span data-ttu-id="a93f8-117">Comportamentos</span><span class="sxs-lookup"><span data-stu-id="a93f8-117">Behaviors</span></span>  
 <span data-ttu-id="a93f8-118">Tipo de dados: matriz de comportamento</span><span class="sxs-lookup"><span data-stu-id="a93f8-118">Data type: Behavior array</span></span>  
  
 <span data-ttu-id="a93f8-119">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="a93f8-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a93f8-120">Os comportamentos associados a essa operação.</span><span class="sxs-lookup"><span data-stu-id="a93f8-120">The behaviors associated with this operation.</span></span>  
  
### <a name="iscallback"></a><span data-ttu-id="a93f8-121">IsCallback</span><span class="sxs-lookup"><span data-stu-id="a93f8-121">IsCallback</span></span>  
 <span data-ttu-id="a93f8-122">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="a93f8-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="a93f8-123">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="a93f8-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a93f8-124">Verdadeiro quando a operação é uma operação de retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="a93f8-124">True when the operation is a callback operation.</span></span>  
  
### <a name="isinitiating"></a><span data-ttu-id="a93f8-125">IsInitiating</span><span class="sxs-lookup"><span data-stu-id="a93f8-125">IsInitiating</span></span>  
 <span data-ttu-id="a93f8-126">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="a93f8-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="a93f8-127">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="a93f8-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a93f8-128">Indica se o método implementa uma operação que pode iniciar uma sessão no servidor.</span><span class="sxs-lookup"><span data-stu-id="a93f8-128">Indicates whether the method implements an operation that can initiate a session on the server.</span></span>  
  
### <a name="isoneway"></a><span data-ttu-id="a93f8-129">IsOneWay</span><span class="sxs-lookup"><span data-stu-id="a93f8-129">IsOneWay</span></span>  
 <span data-ttu-id="a93f8-130">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="a93f8-130">Data type: boolean</span></span>  
  
 <span data-ttu-id="a93f8-131">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="a93f8-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a93f8-132">Indica se uma operação retorna uma mensagem de resposta.</span><span class="sxs-lookup"><span data-stu-id="a93f8-132">Indicates whether an operation returns a reply message.</span></span>  
  
### <a name="isterminating"></a><span data-ttu-id="a93f8-133">IsTerminating</span><span class="sxs-lookup"><span data-stu-id="a93f8-133">IsTerminating</span></span>  
 <span data-ttu-id="a93f8-134">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="a93f8-134">Data type: boolean</span></span>  
  
 <span data-ttu-id="a93f8-135">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="a93f8-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a93f8-136">Indica se uma operação retorna uma mensagem de resposta.</span><span class="sxs-lookup"><span data-stu-id="a93f8-136">Indicates whether an operation returns a reply message.</span></span>  
  
### <a name="methodsignature"></a><span data-ttu-id="a93f8-137">MethodSignature</span><span class="sxs-lookup"><span data-stu-id="a93f8-137">MethodSignature</span></span>  
 <span data-ttu-id="a93f8-138">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="a93f8-138">Data type: string</span></span>  
  
 <span data-ttu-id="a93f8-139">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="a93f8-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a93f8-140">A assinatura de método da operação.</span><span class="sxs-lookup"><span data-stu-id="a93f8-140">The method signature of the operation.</span></span>  
  
### <a name="name"></a><span data-ttu-id="a93f8-141">Nome</span><span class="sxs-lookup"><span data-stu-id="a93f8-141">Name</span></span>  
 <span data-ttu-id="a93f8-142">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="a93f8-142">Data type: string</span></span>  
  
 <span data-ttu-id="a93f8-143">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="a93f8-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a93f8-144">O nome da operação.</span><span class="sxs-lookup"><span data-stu-id="a93f8-144">The name of the operation.</span></span>  
  
### <a name="parametertypes"></a><span data-ttu-id="a93f8-145">ParameterTypes</span><span class="sxs-lookup"><span data-stu-id="a93f8-145">ParameterTypes</span></span>  
 <span data-ttu-id="a93f8-146">Tipo de dados: matriz de cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="a93f8-146">Data type: string array</span></span>  
  
 <span data-ttu-id="a93f8-147">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="a93f8-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a93f8-148">Os tipos dos parâmetros da operação.</span><span class="sxs-lookup"><span data-stu-id="a93f8-148">The types of the parameters of the operation.</span></span>  
  
### <a name="replyaction"></a><span data-ttu-id="a93f8-149">ReplyAction</span><span class="sxs-lookup"><span data-stu-id="a93f8-149">ReplyAction</span></span>  
 <span data-ttu-id="a93f8-150">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="a93f8-150">Data type: string</span></span>  
  
 <span data-ttu-id="a93f8-151">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="a93f8-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a93f8-152">O valor da ação SOAP para a mensagem de resposta da operação.</span><span class="sxs-lookup"><span data-stu-id="a93f8-152">The value of the SOAP action for the reply message of the operation.</span></span>  
  
### <a name="returntype"></a><span data-ttu-id="a93f8-153">Tipoderetorno</span><span class="sxs-lookup"><span data-stu-id="a93f8-153">ReturnType</span></span>  
 <span data-ttu-id="a93f8-154">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="a93f8-154">Data type: string</span></span>  
  
 <span data-ttu-id="a93f8-155">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="a93f8-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a93f8-156">O tipo de retorno da operação.</span><span class="sxs-lookup"><span data-stu-id="a93f8-156">The return type of the operation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a93f8-157">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a93f8-157">Requirements</span></span>  
  
|<span data-ttu-id="a93f8-158">MOF</span><span class="sxs-lookup"><span data-stu-id="a93f8-158">MOF</span></span>|<span data-ttu-id="a93f8-159">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="a93f8-159">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="a93f8-160">Namespace</span><span class="sxs-lookup"><span data-stu-id="a93f8-160">Namespace</span></span>|<span data-ttu-id="a93f8-161">Definido em root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="a93f8-161">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a93f8-162">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a93f8-162">See Also</span></span>  
 <xref:System.ServiceModel.Description.OperationDescription>
