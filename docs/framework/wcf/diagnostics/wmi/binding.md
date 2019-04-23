---
title: Binding2
ms.date: 03/30/2017
ms.assetid: 09511c6c-5749-4bb0-874e-0f0be36bfe04
ms.openlocfilehash: a040cc6e12833d2c737eb14c591300e5873ddce7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59979154"
---
# <a name="binding"></a><span data-ttu-id="160f7-102">Associação</span><span class="sxs-lookup"><span data-stu-id="160f7-102">Binding</span></span>
<span data-ttu-id="160f7-103">WMI de associação</span><span class="sxs-lookup"><span data-stu-id="160f7-103">wmi Binding</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="160f7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="160f7-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="160f7-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="160f7-105">Methods</span></span>  
 <span data-ttu-id="160f7-106">A classe de associação não define quaisquer métodos.</span><span class="sxs-lookup"><span data-stu-id="160f7-106">The Binding class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="160f7-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="160f7-107">Properties</span></span>  
 <span data-ttu-id="160f7-108">A classe Binding tem as seguintes propriedades.</span><span class="sxs-lookup"><span data-stu-id="160f7-108">The Binding class has the following properties.</span></span>  
  
### <a name="bindingelements"></a><span data-ttu-id="160f7-109">BindingElements</span><span class="sxs-lookup"><span data-stu-id="160f7-109">BindingElements</span></span>  
 <span data-ttu-id="160f7-110">Tipo de dados: Matriz de BindingElement</span><span class="sxs-lookup"><span data-stu-id="160f7-110">Data type: BindingElement array</span></span>  
  
 <span data-ttu-id="160f7-111">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="160f7-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="160f7-112">A coleção de elementos implementados pela associação de associação.</span><span class="sxs-lookup"><span data-stu-id="160f7-112">The collection of binding elements implemented by the binding.</span></span>  
  
### <a name="closetimeout"></a><span data-ttu-id="160f7-113">CloseTimeout</span><span class="sxs-lookup"><span data-stu-id="160f7-113">CloseTimeout</span></span>  
 <span data-ttu-id="160f7-114">Tipo de dados: datetime</span><span class="sxs-lookup"><span data-stu-id="160f7-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="160f7-115">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="160f7-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="160f7-116">O intervalo de tempo fornecido para a conclusão de uma operação close.</span><span class="sxs-lookup"><span data-stu-id="160f7-116">The interval of time provided for a close operation to complete.</span></span>  
  
### <a name="name"></a><span data-ttu-id="160f7-117">Nome</span><span class="sxs-lookup"><span data-stu-id="160f7-117">Name</span></span>  
 <span data-ttu-id="160f7-118">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="160f7-118">Data type: string</span></span>  
  
 <span data-ttu-id="160f7-119">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="160f7-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="160f7-120">O nome da associação.</span><span class="sxs-lookup"><span data-stu-id="160f7-120">The name of the binding.</span></span>  
  
### <a name="namespace"></a><span data-ttu-id="160f7-121">Namespace</span><span class="sxs-lookup"><span data-stu-id="160f7-121">Namespace</span></span>  
 <span data-ttu-id="160f7-122">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="160f7-122">Data type: string</span></span>  
  
 <span data-ttu-id="160f7-123">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="160f7-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="160f7-124">O namespace XML da associação.</span><span class="sxs-lookup"><span data-stu-id="160f7-124">The XML namespace of the binding.</span></span>  
  
### <a name="opentimeout"></a><span data-ttu-id="160f7-125">OpenTimeout</span><span class="sxs-lookup"><span data-stu-id="160f7-125">OpenTimeout</span></span>  
 <span data-ttu-id="160f7-126">Tipo de dados: datetime</span><span class="sxs-lookup"><span data-stu-id="160f7-126">Data type: datetime</span></span>  
  
 <span data-ttu-id="160f7-127">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="160f7-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="160f7-128">O intervalo de tempo fornecido para a conclusão de uma operação open.</span><span class="sxs-lookup"><span data-stu-id="160f7-128">The interval of time provided for an open operation to complete.</span></span>  
  
### <a name="receivetimeout"></a><span data-ttu-id="160f7-129">ReceiveTimeout</span><span class="sxs-lookup"><span data-stu-id="160f7-129">ReceiveTimeout</span></span>  
 <span data-ttu-id="160f7-130">Tipo de dados: datetime</span><span class="sxs-lookup"><span data-stu-id="160f7-130">Data type: datetime</span></span>  
  
 <span data-ttu-id="160f7-131">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="160f7-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="160f7-132">O intervalo de tempo fornecido para uma operação de recebimento ser concluída.</span><span class="sxs-lookup"><span data-stu-id="160f7-132">The interval of time provided for a receive operation to complete.</span></span>  
  
### <a name="scheme"></a><span data-ttu-id="160f7-133">Esquema</span><span class="sxs-lookup"><span data-stu-id="160f7-133">Scheme</span></span>  
 <span data-ttu-id="160f7-134">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="160f7-134">Data type: string</span></span>  
  
 <span data-ttu-id="160f7-135">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="160f7-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="160f7-136">O esquema de transporte URI que é usado pelas fábricas de canal e de ouvinte que são criadas pela associação.</span><span class="sxs-lookup"><span data-stu-id="160f7-136">The URI transport scheme that is used by the channel and listener factories that are built by the binding.</span></span>  
  
### <a name="sendtimeout"></a><span data-ttu-id="160f7-137">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="160f7-137">SendTimeout</span></span>  
 <span data-ttu-id="160f7-138">Tipo de dados: datetime</span><span class="sxs-lookup"><span data-stu-id="160f7-138">Data type: datetime</span></span>  
  
 <span data-ttu-id="160f7-139">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="160f7-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="160f7-140">O intervalo de tempo fornecido para uma operação de envio ser concluída.</span><span class="sxs-lookup"><span data-stu-id="160f7-140">The interval of time provided for a send operation to complete.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="160f7-141">Requisitos</span><span class="sxs-lookup"><span data-stu-id="160f7-141">Requirements</span></span>  
  
|<span data-ttu-id="160f7-142">MOF</span><span class="sxs-lookup"><span data-stu-id="160f7-142">MOF</span></span>|<span data-ttu-id="160f7-143">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="160f7-143">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="160f7-144">Namespace</span><span class="sxs-lookup"><span data-stu-id="160f7-144">Namespace</span></span>|<span data-ttu-id="160f7-145">Definido no root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="160f7-145">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="160f7-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="160f7-146">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
