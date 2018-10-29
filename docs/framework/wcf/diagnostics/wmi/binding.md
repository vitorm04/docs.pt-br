---
title: Binding2
ms.date: 03/30/2017
ms.assetid: 09511c6c-5749-4bb0-874e-0f0be36bfe04
ms.openlocfilehash: 84e304f3dedcbd785d6238e6cb5eb142c288b995
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/28/2018
ms.locfileid: "50198883"
---
# <a name="binding"></a><span data-ttu-id="daafa-102">Associação</span><span class="sxs-lookup"><span data-stu-id="daafa-102">Binding</span></span>
<span data-ttu-id="daafa-103">WMI de associação</span><span class="sxs-lookup"><span data-stu-id="daafa-103">wmi Binding</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="daafa-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="daafa-104">Syntax</span></span>  
  
```csharp
class Binding  
{  
  BindingElement BindingElements[];  
  datetime CloseTimeout;  
  string Name;  
  string Namespace;  
  datetime OpenTimeout;  
  datetime ReceiveTimeout;  
  string Scheme;  
  datetime SendTimeout;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="daafa-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="daafa-105">Methods</span></span>  
 <span data-ttu-id="daafa-106">A classe de associação não define quaisquer métodos.</span><span class="sxs-lookup"><span data-stu-id="daafa-106">The Binding class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="daafa-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="daafa-107">Properties</span></span>  
 <span data-ttu-id="daafa-108">A classe Binding tem as seguintes propriedades.</span><span class="sxs-lookup"><span data-stu-id="daafa-108">The Binding class has the following properties.</span></span>  
  
### <a name="bindingelements"></a><span data-ttu-id="daafa-109">BindingElements</span><span class="sxs-lookup"><span data-stu-id="daafa-109">BindingElements</span></span>  
 <span data-ttu-id="daafa-110">Tipo de dados: matriz BindingElement</span><span class="sxs-lookup"><span data-stu-id="daafa-110">Data type: BindingElement array</span></span>  
  
 <span data-ttu-id="daafa-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="daafa-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="daafa-112">A coleção de elementos implementados pela associação de associação.</span><span class="sxs-lookup"><span data-stu-id="daafa-112">The collection of binding elements implemented by the binding.</span></span>  
  
### <a name="closetimeout"></a><span data-ttu-id="daafa-113">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="daafa-113">CloseTimeout</span></span>  
 <span data-ttu-id="daafa-114">Tipo de dados: datetime</span><span class="sxs-lookup"><span data-stu-id="daafa-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="daafa-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="daafa-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="daafa-116">O intervalo de tempo fornecido para a conclusão de uma operação close.</span><span class="sxs-lookup"><span data-stu-id="daafa-116">The interval of time provided for a close operation to complete.</span></span>  
  
### <a name="name"></a><span data-ttu-id="daafa-117">Nome</span><span class="sxs-lookup"><span data-stu-id="daafa-117">Name</span></span>  
 <span data-ttu-id="daafa-118">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="daafa-118">Data type: string</span></span>  
  
 <span data-ttu-id="daafa-119">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="daafa-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="daafa-120">O nome da associação.</span><span class="sxs-lookup"><span data-stu-id="daafa-120">The name of the binding.</span></span>  
  
### <a name="namespace"></a><span data-ttu-id="daafa-121">Namespace</span><span class="sxs-lookup"><span data-stu-id="daafa-121">Namespace</span></span>  
 <span data-ttu-id="daafa-122">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="daafa-122">Data type: string</span></span>  
  
 <span data-ttu-id="daafa-123">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="daafa-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="daafa-124">O namespace XML da associação.</span><span class="sxs-lookup"><span data-stu-id="daafa-124">The XML namespace of the binding.</span></span>  
  
### <a name="opentimeout"></a><span data-ttu-id="daafa-125">openTimeout</span><span class="sxs-lookup"><span data-stu-id="daafa-125">OpenTimeout</span></span>  
 <span data-ttu-id="daafa-126">Tipo de dados: datetime</span><span class="sxs-lookup"><span data-stu-id="daafa-126">Data type: datetime</span></span>  
  
 <span data-ttu-id="daafa-127">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="daafa-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="daafa-128">O intervalo de tempo fornecido para a conclusão de uma operação open.</span><span class="sxs-lookup"><span data-stu-id="daafa-128">The interval of time provided for an open operation to complete.</span></span>  
  
### <a name="receivetimeout"></a><span data-ttu-id="daafa-129">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="daafa-129">ReceiveTimeout</span></span>  
 <span data-ttu-id="daafa-130">Tipo de dados: datetime</span><span class="sxs-lookup"><span data-stu-id="daafa-130">Data type: datetime</span></span>  
  
 <span data-ttu-id="daafa-131">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="daafa-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="daafa-132">O intervalo de tempo fornecido para uma operação de recebimento ser concluída.</span><span class="sxs-lookup"><span data-stu-id="daafa-132">The interval of time provided for a receive operation to complete.</span></span>  
  
### <a name="scheme"></a><span data-ttu-id="daafa-133">Esquema</span><span class="sxs-lookup"><span data-stu-id="daafa-133">Scheme</span></span>  
 <span data-ttu-id="daafa-134">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="daafa-134">Data type: string</span></span>  
  
 <span data-ttu-id="daafa-135">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="daafa-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="daafa-136">O esquema de transporte URI que é usado pelas fábricas de canal e de ouvinte que são criadas pela associação.</span><span class="sxs-lookup"><span data-stu-id="daafa-136">The URI transport scheme that is used by the channel and listener factories that are built by the binding.</span></span>  
  
### <a name="sendtimeout"></a><span data-ttu-id="daafa-137">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="daafa-137">SendTimeout</span></span>  
 <span data-ttu-id="daafa-138">Tipo de dados: datetime</span><span class="sxs-lookup"><span data-stu-id="daafa-138">Data type: datetime</span></span>  
  
 <span data-ttu-id="daafa-139">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="daafa-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="daafa-140">O intervalo de tempo fornecido para uma operação de envio ser concluída.</span><span class="sxs-lookup"><span data-stu-id="daafa-140">The interval of time provided for a send operation to complete.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="daafa-141">Requisitos</span><span class="sxs-lookup"><span data-stu-id="daafa-141">Requirements</span></span>  
  
|<span data-ttu-id="daafa-142">MOF</span><span class="sxs-lookup"><span data-stu-id="daafa-142">MOF</span></span>|<span data-ttu-id="daafa-143">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="daafa-143">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="daafa-144">Namespace</span><span class="sxs-lookup"><span data-stu-id="daafa-144">Namespace</span></span>|<span data-ttu-id="daafa-145">Definido no root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="daafa-145">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="daafa-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="daafa-146">See Also</span></span>  
 <xref:System.ServiceModel.Channels.Binding>
