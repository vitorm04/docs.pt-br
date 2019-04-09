---
title: ServiceBehaviorAttribute
ms.date: 03/30/2017
ms.assetid: 5faa266f-587f-4e03-828d-1c7dd5acfe65
ms.openlocfilehash: b6221e93f10b87a368bd594932a8c36ae14df8f3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59206870"
---
# <a name="servicebehaviorattribute"></a><span data-ttu-id="7b539-102">ServiceBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="7b539-102">ServiceBehaviorAttribute</span></span>
<span data-ttu-id="7b539-103">ServiceBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="7b539-103">ServiceBehaviorAttribute</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b539-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7b539-104">Syntax</span></span>  
  
```csharp
class ServiceBehaviorAttribute : Behavior  
{  
  boolean AutomaticSessionShutdown;  
  string ConcurrencyMode;  
  string ConfigurationName;  
  boolean IgnoreExtensionDataObject;  
  boolean IncludeExceptionDetailInFaults;  
  string InstanceContextMode;  
  sint32 MaxItemsInObjectGraph;  
  string Name;  
  string Namespace;  
  boolean ReleaseServiceInstanceOnTransactionComplete;  
  boolean TransactionAutoCompleteOnSessionClose;  
  string TransactionIsolationLevel;  
  datetime TransactionTimeout;  
  boolean UseSynchronizationContext;  
  boolean ValidateMustUnderstand;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="7b539-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="7b539-105">Methods</span></span>  
 <span data-ttu-id="7b539-106">A classe ServiceBehaviorAttribute não define quaisquer métodos.</span><span class="sxs-lookup"><span data-stu-id="7b539-106">The ServiceBehaviorAttribute class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="7b539-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="7b539-107">Properties</span></span>  
 <span data-ttu-id="7b539-108">A classe ServiceBehaviorAttribute tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="7b539-108">The ServiceBehaviorAttribute class has the following properties:</span></span>  
  
### <a name="automaticsessionshutdown"></a><span data-ttu-id="7b539-109">AutomaticSessionShutdown</span><span class="sxs-lookup"><span data-stu-id="7b539-109">AutomaticSessionShutdown</span></span>  
 <span data-ttu-id="7b539-110">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="7b539-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="7b539-111">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="7b539-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7b539-112">Indica se deve fechar automaticamente uma sessão quando um cliente fechar uma sessão de saída.</span><span class="sxs-lookup"><span data-stu-id="7b539-112">Indicates whether to automatically close a session when a client closes an output session.</span></span>  
  
### <a name="concurrencymode"></a><span data-ttu-id="7b539-113">ConcurrencyMode</span><span class="sxs-lookup"><span data-stu-id="7b539-113">ConcurrencyMode</span></span>  
 <span data-ttu-id="7b539-114">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="7b539-114">Data type: string</span></span>  
<span data-ttu-id="7b539-115">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="7b539-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7b539-116">Indica se um serviço dá suporte a um thread, vários threads ou chamadas reentrantes.</span><span class="sxs-lookup"><span data-stu-id="7b539-116">Indicates whether a service supports one thread, multiple threads, or reentrant calls.</span></span>  
  
### <a name="configurationname"></a><span data-ttu-id="7b539-117">ConfigurationName</span><span class="sxs-lookup"><span data-stu-id="7b539-117">ConfigurationName</span></span>  
 <span data-ttu-id="7b539-118">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="7b539-118">Data type: string</span></span>  
  
 <span data-ttu-id="7b539-119">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="7b539-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7b539-120">O nome da configuração do serviço.</span><span class="sxs-lookup"><span data-stu-id="7b539-120">The name of the service configuration.</span></span>  
  
### <a name="ignoreextensiondataobject"></a><span data-ttu-id="7b539-121">IgnoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="7b539-121">IgnoreExtensionDataObject</span></span>  
 <span data-ttu-id="7b539-122">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="7b539-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="7b539-123">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="7b539-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7b539-124">Especifica se deve enviar dados de serialização desconhecidos em trânsito.</span><span class="sxs-lookup"><span data-stu-id="7b539-124">Specifies whether to send unknown serialization data onto the wire.</span></span>  
  
### <a name="includeexceptiondetailinfaults"></a><span data-ttu-id="7b539-125">IncludeExceptionDetailInFaults</span><span class="sxs-lookup"><span data-stu-id="7b539-125">IncludeExceptionDetailInFaults</span></span>  
 <span data-ttu-id="7b539-126">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="7b539-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="7b539-127">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="7b539-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7b539-128">Especifica se deve incluir informações de exceção gerenciada nos detalhes das falhas SOAP retornadas aos clientes para fins de depuração.</span><span class="sxs-lookup"><span data-stu-id="7b539-128">Specifies whether to include managed exception information in the detail of SOAP faults returned to the clients for debugging purposes.</span></span>  
  
### <a name="instancecontextmode"></a><span data-ttu-id="7b539-129">InstanceContextMode</span><span class="sxs-lookup"><span data-stu-id="7b539-129">InstanceContextMode</span></span>  
 <span data-ttu-id="7b539-130">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="7b539-130">Data type: string</span></span>  
  
 <span data-ttu-id="7b539-131">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="7b539-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7b539-132">Especifica quando um novo objeto de serviço é criado.</span><span class="sxs-lookup"><span data-stu-id="7b539-132">Specifies when a new service object is created.</span></span>  
  
### <a name="maxitemsinobjectgraph"></a><span data-ttu-id="7b539-133">MaxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="7b539-133">MaxItemsInObjectGraph</span></span>  
 <span data-ttu-id="7b539-134">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="7b539-134">Data type: sint32</span></span>  
  
 <span data-ttu-id="7b539-135">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="7b539-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7b539-136">O número máximo de itens permitidos em um objeto serializado.</span><span class="sxs-lookup"><span data-stu-id="7b539-136">The maximum number of items allowed in a serialized object.</span></span>  
  
### <a name="name"></a><span data-ttu-id="7b539-137">Nome</span><span class="sxs-lookup"><span data-stu-id="7b539-137">Name</span></span>  
 <span data-ttu-id="7b539-138">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="7b539-138">Data type: string</span></span>  
  
 <span data-ttu-id="7b539-139">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="7b539-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7b539-140">O atributo de nome do serviço no WSDL.</span><span class="sxs-lookup"><span data-stu-id="7b539-140">The name attribute of the service in WSDL.</span></span>  
  
### <a name="namespace"></a><span data-ttu-id="7b539-141">Namespace</span><span class="sxs-lookup"><span data-stu-id="7b539-141">Namespace</span></span>  
 <span data-ttu-id="7b539-142">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="7b539-142">Data type: string</span></span>  
  
 <span data-ttu-id="7b539-143">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="7b539-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7b539-144">O namespace de destino do serviço em WSDL.</span><span class="sxs-lookup"><span data-stu-id="7b539-144">The target namespace of the service in WSDL.</span></span>  
  
### <a name="releaseserviceinstanceontransactioncomplete"></a><span data-ttu-id="7b539-145">ReleaseServiceInstanceOnTransactionComplete</span><span class="sxs-lookup"><span data-stu-id="7b539-145">ReleaseServiceInstanceOnTransactionComplete</span></span>  
 <span data-ttu-id="7b539-146">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="7b539-146">Data type: boolean</span></span>  
  
 <span data-ttu-id="7b539-147">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="7b539-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7b539-148">Especifica se o objeto de serviço é reciclado quando a transação atual seja concluída.</span><span class="sxs-lookup"><span data-stu-id="7b539-148">Specifies whether the service object is recycled when the current transaction completes.</span></span>  
  
### <a name="transactionautocompleteonsessionclose"></a><span data-ttu-id="7b539-149">TransactionAutoCompleteOnSessionClose</span><span class="sxs-lookup"><span data-stu-id="7b539-149">TransactionAutoCompleteOnSessionClose</span></span>  
 <span data-ttu-id="7b539-150">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="7b539-150">Data type: boolean</span></span>  
  
 <span data-ttu-id="7b539-151">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="7b539-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7b539-152">Especifica se as transações pendentes são foi concluída quando a sessão atual é fechada.</span><span class="sxs-lookup"><span data-stu-id="7b539-152">Specifies whether pending transactions are completed when the current session closes.</span></span>  
  
### <a name="transactionisolationlevel"></a><span data-ttu-id="7b539-153">TransactionIsolationLevel</span><span class="sxs-lookup"><span data-stu-id="7b539-153">TransactionIsolationLevel</span></span>  
 <span data-ttu-id="7b539-154">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="7b539-154">Data type: string</span></span>  
  
 <span data-ttu-id="7b539-155">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="7b539-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7b539-156">Especifica o nível de isolamento da transação.</span><span class="sxs-lookup"><span data-stu-id="7b539-156">Specifies the transaction isolation level.</span></span>  
  
### <a name="transactiontimeout"></a><span data-ttu-id="7b539-157">TransactionTimeout</span><span class="sxs-lookup"><span data-stu-id="7b539-157">TransactionTimeout</span></span>  
 <span data-ttu-id="7b539-158">Tipo de dados: datetime</span><span class="sxs-lookup"><span data-stu-id="7b539-158">Data type: datetime</span></span>  
  
 <span data-ttu-id="7b539-159">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="7b539-159">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7b539-160">O período dentro do qual uma transação deve ser concluída.</span><span class="sxs-lookup"><span data-stu-id="7b539-160">The period within which a transaction must complete.</span></span>  
  
### <a name="usesynchronizationcontext"></a><span data-ttu-id="7b539-161">UseSynchronizationContext</span><span class="sxs-lookup"><span data-stu-id="7b539-161">UseSynchronizationContext</span></span>  
 <span data-ttu-id="7b539-162">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="7b539-162">Data type: boolean</span></span>  
  
 <span data-ttu-id="7b539-163">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="7b539-163">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7b539-164">Especifica se deve usar o contexto de sincronização atual para escolher a execução de thread.</span><span class="sxs-lookup"><span data-stu-id="7b539-164">Specifies whether to use the current synchronization context to choose the thread execution.</span></span>  
  
### <a name="validatemustunderstand"></a><span data-ttu-id="7b539-165">ValidateMustUnderstand</span><span class="sxs-lookup"><span data-stu-id="7b539-165">ValidateMustUnderstand</span></span>  
 <span data-ttu-id="7b539-166">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="7b539-166">Data type: boolean</span></span>  
  
 <span data-ttu-id="7b539-167">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="7b539-167">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7b539-168">Especifica se o sistema ou o aplicativo impõe o processamento do cabeçalho SOAP MustUnderstand.</span><span class="sxs-lookup"><span data-stu-id="7b539-168">Specifies whether the system or the application enforces SOAP MustUnderstand header processing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7b539-169">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7b539-169">Requirements</span></span>  
  
|<span data-ttu-id="7b539-170">MOF</span><span class="sxs-lookup"><span data-stu-id="7b539-170">MOF</span></span>|<span data-ttu-id="7b539-171">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="7b539-171">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="7b539-172">Namespace</span><span class="sxs-lookup"><span data-stu-id="7b539-172">Namespace</span></span>|<span data-ttu-id="7b539-173">Definido no root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="7b539-173">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7b539-174">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7b539-174">See also</span></span>

- <xref:System.ServiceModel.ServiceBehaviorAttribute>
