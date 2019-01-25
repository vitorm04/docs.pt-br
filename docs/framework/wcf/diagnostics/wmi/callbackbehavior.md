---
title: CallbackBehavior
ms.date: 03/30/2017
ms.assetid: 42acd302-2b62-4849-a2d1-a03084343ecd
ms.openlocfilehash: 2854671eaabb37066b57d87a7496183c9e5bba4d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54562838"
---
# <a name="callbackbehavior"></a><span data-ttu-id="8db47-102">CallbackBehavior</span><span class="sxs-lookup"><span data-stu-id="8db47-102">CallbackBehavior</span></span>
<span data-ttu-id="8db47-103">CallbackBehavior</span><span class="sxs-lookup"><span data-stu-id="8db47-103">CallbackBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8db47-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8db47-104">Syntax</span></span>  
  
```csharp
class CallbackBehavior : Behavior  
{  
  boolean AutomaticSessionShutdown;  
  string ConcurrencyMode;  
  boolean IgnoreExtensionDataObject;  
  boolean IncludeExceptionDetailInFaults;  
  boolean MaxItemsInObjectGraph;  
  boolean UseSynchronizationContext;  
  boolean ValidateMustUnderstand;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="8db47-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="8db47-105">Methods</span></span>  
 <span data-ttu-id="8db47-106">A classe CallbackBehavior não define quaisquer métodos.</span><span class="sxs-lookup"><span data-stu-id="8db47-106">The CallbackBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="8db47-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="8db47-107">Properties</span></span>  
 <span data-ttu-id="8db47-108">A classe CallbackBehavior tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="8db47-108">The CallbackBehavior class has the following properties:</span></span>  
  
### <a name="automaticsessionshutdown"></a><span data-ttu-id="8db47-109">AutomaticSessionShutdown</span><span class="sxs-lookup"><span data-stu-id="8db47-109">AutomaticSessionShutdown</span></span>  
 <span data-ttu-id="8db47-110">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="8db47-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="8db47-111">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="8db47-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8db47-112">Quando for verdadeiro, a sessão é fechada automaticamente quando um serviço fecha uma sessão duplex.</span><span class="sxs-lookup"><span data-stu-id="8db47-112">When true, the session is automatically closed when a service closes a duplex session.</span></span>  
  
### <a name="concurrencymode"></a><span data-ttu-id="8db47-113">ConcurrencyMode</span><span class="sxs-lookup"><span data-stu-id="8db47-113">ConcurrencyMode</span></span>  
 <span data-ttu-id="8db47-114">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="8db47-114">Data type: string</span></span>  
<span data-ttu-id="8db47-115">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="8db47-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8db47-116">Especifica se o serviço dá suporte a um thread, vários threads ou chamadas reentrantes.</span><span class="sxs-lookup"><span data-stu-id="8db47-116">Specifies whether the service supports one thread, multiple threads, or reentrant calls.</span></span>  
  
### <a name="ignoreextensiondataobject"></a><span data-ttu-id="8db47-117">IgnoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="8db47-117">IgnoreExtensionDataObject</span></span>  
 <span data-ttu-id="8db47-118">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="8db47-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="8db47-119">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="8db47-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8db47-120">Um valor que especifica se é necessário enviar dados de serialização desconhecidos em trânsito.</span><span class="sxs-lookup"><span data-stu-id="8db47-120">A value that specifies whether to send unknown serialization data onto the wire.</span></span>  
  
### <a name="includeexceptiondetailinfaults"></a><span data-ttu-id="8db47-121">IncludeExceptionDetailInFaults</span><span class="sxs-lookup"><span data-stu-id="8db47-121">IncludeExceptionDetailInFaults</span></span>  
 <span data-ttu-id="8db47-122">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="8db47-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="8db47-123">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="8db47-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8db47-124">Quando habilitado, detalhes sobre exceções no retorno de chamada são anexados às falhas retornadas para o serviço.</span><span class="sxs-lookup"><span data-stu-id="8db47-124">When enabled, details about exceptions on the callback are attached to the faults returned to the service.</span></span>  
  
### <a name="maxitemsinobjectgraph"></a><span data-ttu-id="8db47-125">MaxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="8db47-125">MaxItemsInObjectGraph</span></span>  
 <span data-ttu-id="8db47-126">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="8db47-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="8db47-127">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="8db47-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8db47-128">O número máximo de itens permitidos em um objeto serializado.</span><span class="sxs-lookup"><span data-stu-id="8db47-128">The maximum number of items allowed in a serialized object.</span></span>  
  
### <a name="usesynchronizationcontext"></a><span data-ttu-id="8db47-129">UseSynchronizationContext</span><span class="sxs-lookup"><span data-stu-id="8db47-129">UseSynchronizationContext</span></span>  
 <span data-ttu-id="8db47-130">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="8db47-130">Data type: boolean</span></span>  
  
 <span data-ttu-id="8db47-131">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="8db47-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8db47-132">Especifica se deve usar o contexto de sincronização atual para escolher o thread de execução.</span><span class="sxs-lookup"><span data-stu-id="8db47-132">Specifies whether to use the current synchronization context to choose the thread of execution.</span></span>  
  
### <a name="validatemustunderstand"></a><span data-ttu-id="8db47-133">ValidateMustUnderstand</span><span class="sxs-lookup"><span data-stu-id="8db47-133">ValidateMustUnderstand</span></span>  
 <span data-ttu-id="8db47-134">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="8db47-134">Data type: boolean</span></span>  
  
 <span data-ttu-id="8db47-135">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="8db47-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8db47-136">Especifica se o sistema ou o aplicativo impõe o processamento do cabeçalho SOAP MustUnderstand.</span><span class="sxs-lookup"><span data-stu-id="8db47-136">Specifies whether the system or the application enforces SOAP MustUnderstand header processing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8db47-137">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8db47-137">Requirements</span></span>  
  
|<span data-ttu-id="8db47-138">MOF</span><span class="sxs-lookup"><span data-stu-id="8db47-138">MOF</span></span>|<span data-ttu-id="8db47-139">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="8db47-139">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="8db47-140">Namespace</span><span class="sxs-lookup"><span data-stu-id="8db47-140">Namespace</span></span>|<span data-ttu-id="8db47-141">Definido no root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="8db47-141">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8db47-142">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8db47-142">See also</span></span>
- <xref:System.ServiceModel.CallbackBehaviorAttribute>
