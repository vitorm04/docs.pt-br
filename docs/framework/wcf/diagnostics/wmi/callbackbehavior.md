---
title: CallbackBehavior
ms.date: 03/30/2017
ms.assetid: 42acd302-2b62-4849-a2d1-a03084343ecd
ms.openlocfilehash: 9d8f4335c304d164daafeb0ad4de5b4e3bba4590
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59115031"
---
# <a name="callbackbehavior"></a><span data-ttu-id="e9221-102">CallbackBehavior</span><span class="sxs-lookup"><span data-stu-id="e9221-102">CallbackBehavior</span></span>
<span data-ttu-id="e9221-103">CallbackBehavior</span><span class="sxs-lookup"><span data-stu-id="e9221-103">CallbackBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9221-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e9221-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="e9221-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="e9221-105">Methods</span></span>  
 <span data-ttu-id="e9221-106">A classe CallbackBehavior não define quaisquer métodos.</span><span class="sxs-lookup"><span data-stu-id="e9221-106">The CallbackBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="e9221-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="e9221-107">Properties</span></span>  
 <span data-ttu-id="e9221-108">A classe CallbackBehavior tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="e9221-108">The CallbackBehavior class has the following properties:</span></span>  
  
### <a name="automaticsessionshutdown"></a><span data-ttu-id="e9221-109">AutomaticSessionShutdown</span><span class="sxs-lookup"><span data-stu-id="e9221-109">AutomaticSessionShutdown</span></span>  
 <span data-ttu-id="e9221-110">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="e9221-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="e9221-111">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="e9221-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e9221-112">Quando for verdadeiro, a sessão é fechada automaticamente quando um serviço fecha uma sessão duplex.</span><span class="sxs-lookup"><span data-stu-id="e9221-112">When true, the session is automatically closed when a service closes a duplex session.</span></span>  
  
### <a name="concurrencymode"></a><span data-ttu-id="e9221-113">ConcurrencyMode</span><span class="sxs-lookup"><span data-stu-id="e9221-113">ConcurrencyMode</span></span>  
 <span data-ttu-id="e9221-114">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="e9221-114">Data type: string</span></span>  
<span data-ttu-id="e9221-115">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="e9221-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e9221-116">Especifica se o serviço dá suporte a um thread, vários threads ou chamadas reentrantes.</span><span class="sxs-lookup"><span data-stu-id="e9221-116">Specifies whether the service supports one thread, multiple threads, or reentrant calls.</span></span>  
  
### <a name="ignoreextensiondataobject"></a><span data-ttu-id="e9221-117">IgnoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="e9221-117">IgnoreExtensionDataObject</span></span>  
 <span data-ttu-id="e9221-118">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="e9221-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="e9221-119">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="e9221-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e9221-120">Um valor que especifica se é necessário enviar dados de serialização desconhecidos em trânsito.</span><span class="sxs-lookup"><span data-stu-id="e9221-120">A value that specifies whether to send unknown serialization data onto the wire.</span></span>  
  
### <a name="includeexceptiondetailinfaults"></a><span data-ttu-id="e9221-121">IncludeExceptionDetailInFaults</span><span class="sxs-lookup"><span data-stu-id="e9221-121">IncludeExceptionDetailInFaults</span></span>  
 <span data-ttu-id="e9221-122">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="e9221-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="e9221-123">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="e9221-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e9221-124">Quando habilitado, detalhes sobre exceções no retorno de chamada são anexados às falhas retornadas para o serviço.</span><span class="sxs-lookup"><span data-stu-id="e9221-124">When enabled, details about exceptions on the callback are attached to the faults returned to the service.</span></span>  
  
### <a name="maxitemsinobjectgraph"></a><span data-ttu-id="e9221-125">MaxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="e9221-125">MaxItemsInObjectGraph</span></span>  
 <span data-ttu-id="e9221-126">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="e9221-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="e9221-127">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="e9221-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e9221-128">O número máximo de itens permitidos em um objeto serializado.</span><span class="sxs-lookup"><span data-stu-id="e9221-128">The maximum number of items allowed in a serialized object.</span></span>  
  
### <a name="usesynchronizationcontext"></a><span data-ttu-id="e9221-129">UseSynchronizationContext</span><span class="sxs-lookup"><span data-stu-id="e9221-129">UseSynchronizationContext</span></span>  
 <span data-ttu-id="e9221-130">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="e9221-130">Data type: boolean</span></span>  
  
 <span data-ttu-id="e9221-131">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="e9221-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e9221-132">Especifica se deve usar o contexto de sincronização atual para escolher o thread de execução.</span><span class="sxs-lookup"><span data-stu-id="e9221-132">Specifies whether to use the current synchronization context to choose the thread of execution.</span></span>  
  
### <a name="validatemustunderstand"></a><span data-ttu-id="e9221-133">ValidateMustUnderstand</span><span class="sxs-lookup"><span data-stu-id="e9221-133">ValidateMustUnderstand</span></span>  
 <span data-ttu-id="e9221-134">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="e9221-134">Data type: boolean</span></span>  
  
 <span data-ttu-id="e9221-135">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="e9221-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e9221-136">Especifica se o sistema ou o aplicativo impõe o processamento do cabeçalho SOAP MustUnderstand.</span><span class="sxs-lookup"><span data-stu-id="e9221-136">Specifies whether the system or the application enforces SOAP MustUnderstand header processing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e9221-137">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e9221-137">Requirements</span></span>  
  
|<span data-ttu-id="e9221-138">MOF</span><span class="sxs-lookup"><span data-stu-id="e9221-138">MOF</span></span>|<span data-ttu-id="e9221-139">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="e9221-139">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="e9221-140">Namespace</span><span class="sxs-lookup"><span data-stu-id="e9221-140">Namespace</span></span>|<span data-ttu-id="e9221-141">Definido no root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="e9221-141">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e9221-142">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e9221-142">See also</span></span>

- <xref:System.ServiceModel.CallbackBehaviorAttribute>
