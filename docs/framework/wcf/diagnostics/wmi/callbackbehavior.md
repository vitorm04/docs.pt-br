---
title: CallbackBehavior
ms.date: 03/30/2017
ms.assetid: 42acd302-2b62-4849-a2d1-a03084343ecd
ms.openlocfilehash: 38a38a71db2927d187ccdd93e5e364b0d4955373
ms.sourcegitcommit: b22705f1540b237c566721018f974822d5cd8758
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2018
ms.locfileid: "49452606"
---
# <a name="callbackbehavior"></a><span data-ttu-id="2e38b-102">CallbackBehavior</span><span class="sxs-lookup"><span data-stu-id="2e38b-102">CallbackBehavior</span></span>
<span data-ttu-id="2e38b-103">CallbackBehavior</span><span class="sxs-lookup"><span data-stu-id="2e38b-103">CallbackBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e38b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2e38b-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="2e38b-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="2e38b-105">Methods</span></span>  
 <span data-ttu-id="2e38b-106">A classe CallbackBehavior não define quaisquer métodos.</span><span class="sxs-lookup"><span data-stu-id="2e38b-106">The CallbackBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="2e38b-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="2e38b-107">Properties</span></span>  
 <span data-ttu-id="2e38b-108">A classe CallbackBehavior tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="2e38b-108">The CallbackBehavior class has the following properties:</span></span>  
  
### <a name="automaticsessionshutdown"></a><span data-ttu-id="2e38b-109">AutomaticSessionShutdown</span><span class="sxs-lookup"><span data-stu-id="2e38b-109">AutomaticSessionShutdown</span></span>  
 <span data-ttu-id="2e38b-110">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="2e38b-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="2e38b-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="2e38b-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2e38b-112">Quando for verdadeiro, a sessão é fechada automaticamente quando um serviço fecha uma sessão duplex.</span><span class="sxs-lookup"><span data-stu-id="2e38b-112">When true, the session is automatically closed when a service closes a duplex session.</span></span>  
  
### <a name="concurrencymode"></a><span data-ttu-id="2e38b-113">ConcurrencyMode</span><span class="sxs-lookup"><span data-stu-id="2e38b-113">ConcurrencyMode</span></span>  
 <span data-ttu-id="2e38b-114">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="2e38b-114">Data type: string</span></span>  
<span data-ttu-id="2e38b-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="2e38b-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2e38b-116">Especifica se o serviço dá suporte a um thread, vários threads ou chamadas reentrantes.</span><span class="sxs-lookup"><span data-stu-id="2e38b-116">Specifies whether the service supports one thread, multiple threads, or reentrant calls.</span></span>  
  
### <a name="ignoreextensiondataobject"></a><span data-ttu-id="2e38b-117">IgnoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="2e38b-117">IgnoreExtensionDataObject</span></span>  
 <span data-ttu-id="2e38b-118">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="2e38b-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="2e38b-119">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="2e38b-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2e38b-120">Um valor que especifica se é necessário enviar dados de serialização desconhecidos em trânsito.</span><span class="sxs-lookup"><span data-stu-id="2e38b-120">A value that specifies whether to send unknown serialization data onto the wire.</span></span>  
  
### <a name="includeexceptiondetailinfaults"></a><span data-ttu-id="2e38b-121">IncludeExceptionDetailInFaults</span><span class="sxs-lookup"><span data-stu-id="2e38b-121">IncludeExceptionDetailInFaults</span></span>  
 <span data-ttu-id="2e38b-122">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="2e38b-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="2e38b-123">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="2e38b-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2e38b-124">Quando habilitado, detalhes sobre exceções no retorno de chamada são anexados às falhas retornadas para o serviço.</span><span class="sxs-lookup"><span data-stu-id="2e38b-124">When enabled, details about exceptions on the callback are attached to the faults returned to the service.</span></span>  
  
### <a name="maxitemsinobjectgraph"></a><span data-ttu-id="2e38b-125">MaxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="2e38b-125">MaxItemsInObjectGraph</span></span>  
 <span data-ttu-id="2e38b-126">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="2e38b-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="2e38b-127">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="2e38b-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2e38b-128">O número máximo de itens permitidos em um objeto serializado.</span><span class="sxs-lookup"><span data-stu-id="2e38b-128">The maximum number of items allowed in a serialized object.</span></span>  
  
### <a name="usesynchronizationcontext"></a><span data-ttu-id="2e38b-129">UseSynchronizationContext</span><span class="sxs-lookup"><span data-stu-id="2e38b-129">UseSynchronizationContext</span></span>  
 <span data-ttu-id="2e38b-130">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="2e38b-130">Data type: boolean</span></span>  
  
 <span data-ttu-id="2e38b-131">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="2e38b-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2e38b-132">Especifica se deve usar o contexto de sincronização atual para escolher o thread de execução.</span><span class="sxs-lookup"><span data-stu-id="2e38b-132">Specifies whether to use the current synchronization context to choose the thread of execution.</span></span>  
  
### <a name="validatemustunderstand"></a><span data-ttu-id="2e38b-133">ValidateMustUnderstand</span><span class="sxs-lookup"><span data-stu-id="2e38b-133">ValidateMustUnderstand</span></span>  
 <span data-ttu-id="2e38b-134">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="2e38b-134">Data type: boolean</span></span>  
  
 <span data-ttu-id="2e38b-135">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="2e38b-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2e38b-136">Especifica se o sistema ou o aplicativo impõe o processamento do cabeçalho SOAP MustUnderstand.</span><span class="sxs-lookup"><span data-stu-id="2e38b-136">Specifies whether the system or the application enforces SOAP MustUnderstand header processing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2e38b-137">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2e38b-137">Requirements</span></span>  
  
|<span data-ttu-id="2e38b-138">MOF</span><span class="sxs-lookup"><span data-stu-id="2e38b-138">MOF</span></span>|<span data-ttu-id="2e38b-139">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="2e38b-139">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="2e38b-140">Namespace</span><span class="sxs-lookup"><span data-stu-id="2e38b-140">Namespace</span></span>|<span data-ttu-id="2e38b-141">Definido no root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="2e38b-141">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2e38b-142">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2e38b-142">See Also</span></span>  
 <xref:System.ServiceModel.CallbackBehaviorAttribute>
