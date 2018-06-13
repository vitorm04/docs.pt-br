---
title: ServiceBehaviorAttribute
ms.date: 03/30/2017
ms.assetid: 5faa266f-587f-4e03-828d-1c7dd5acfe65
ms.openlocfilehash: 514af4c6d9eaaf8929ca831e4e786c895d14c67d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33487193"
---
# <a name="servicebehaviorattribute"></a><span data-ttu-id="0d546-102">ServiceBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="0d546-102">ServiceBehaviorAttribute</span></span>
<span data-ttu-id="0d546-103">ServiceBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="0d546-103">ServiceBehaviorAttribute</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d546-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0d546-104">Syntax</span></span>  
  
```  
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
  
## <a name="methods"></a><span data-ttu-id="0d546-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="0d546-105">Methods</span></span>  
 <span data-ttu-id="0d546-106">A classe ServiceBehaviorAttribute não define nenhum método.</span><span class="sxs-lookup"><span data-stu-id="0d546-106">The ServiceBehaviorAttribute class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="0d546-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="0d546-107">Properties</span></span>  
 <span data-ttu-id="0d546-108">A classe ServiceBehaviorAttribute tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="0d546-108">The ServiceBehaviorAttribute class has the following properties:</span></span>  
  
### <a name="automaticsessionshutdown"></a><span data-ttu-id="0d546-109">AutomaticSessionShutdown</span><span class="sxs-lookup"><span data-stu-id="0d546-109">AutomaticSessionShutdown</span></span>  
 <span data-ttu-id="0d546-110">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="0d546-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="0d546-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="0d546-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0d546-112">Indica se fechar automaticamente uma sessão quando um cliente fechar uma sessão de saída.</span><span class="sxs-lookup"><span data-stu-id="0d546-112">Indicates whether to automatically close a session when a client closes an output session.</span></span>  
  
### <a name="concurrencymode"></a><span data-ttu-id="0d546-113">ConcurrencyMode</span><span class="sxs-lookup"><span data-stu-id="0d546-113">ConcurrencyMode</span></span>  
 <span data-ttu-id="0d546-114">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="0d546-114">Data type: string</span></span>  
<span data-ttu-id="0d546-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="0d546-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0d546-116">Indica se um serviço oferece suporte a um thread, vários threads ou chamadas reentrantes.</span><span class="sxs-lookup"><span data-stu-id="0d546-116">Indicates whether a service supports one thread, multiple threads, or reentrant calls.</span></span>  
  
### <a name="configurationname"></a><span data-ttu-id="0d546-117">ConfigurationName</span><span class="sxs-lookup"><span data-stu-id="0d546-117">ConfigurationName</span></span>  
 <span data-ttu-id="0d546-118">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="0d546-118">Data type: string</span></span>  
  
 <span data-ttu-id="0d546-119">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="0d546-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0d546-120">O nome da configuração do serviço.</span><span class="sxs-lookup"><span data-stu-id="0d546-120">The name of the service configuration.</span></span>  
  
### <a name="ignoreextensiondataobject"></a><span data-ttu-id="0d546-121">IgnoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="0d546-121">IgnoreExtensionDataObject</span></span>  
 <span data-ttu-id="0d546-122">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="0d546-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="0d546-123">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="0d546-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0d546-124">Especifica se deve enviar dados de serialização desconhecidos na conexão.</span><span class="sxs-lookup"><span data-stu-id="0d546-124">Specifies whether to send unknown serialization data onto the wire.</span></span>  
  
### <a name="includeexceptiondetailinfaults"></a><span data-ttu-id="0d546-125">includeExceptionDetailInFaults</span><span class="sxs-lookup"><span data-stu-id="0d546-125">IncludeExceptionDetailInFaults</span></span>  
 <span data-ttu-id="0d546-126">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="0d546-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="0d546-127">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="0d546-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0d546-128">Especifica se deve incluir informações de exceção gerenciada no detalhe de falhas SOAP retornadas aos clientes para fins de depuração.</span><span class="sxs-lookup"><span data-stu-id="0d546-128">Specifies whether to include managed exception information in the detail of SOAP faults returned to the clients for debugging purposes.</span></span>  
  
### <a name="instancecontextmode"></a><span data-ttu-id="0d546-129">InstanceContextMode</span><span class="sxs-lookup"><span data-stu-id="0d546-129">InstanceContextMode</span></span>  
 <span data-ttu-id="0d546-130">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="0d546-130">Data type: string</span></span>  
  
 <span data-ttu-id="0d546-131">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="0d546-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0d546-132">Especifica quando um novo objeto de serviço é criado.</span><span class="sxs-lookup"><span data-stu-id="0d546-132">Specifies when a new service object is created.</span></span>  
  
### <a name="maxitemsinobjectgraph"></a><span data-ttu-id="0d546-133">MaxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="0d546-133">MaxItemsInObjectGraph</span></span>  
 <span data-ttu-id="0d546-134">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="0d546-134">Data type: sint32</span></span>  
  
 <span data-ttu-id="0d546-135">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="0d546-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0d546-136">O número máximo de itens permitidos em um objeto serializado.</span><span class="sxs-lookup"><span data-stu-id="0d546-136">The maximum number of items allowed in a serialized object.</span></span>  
  
### <a name="name"></a><span data-ttu-id="0d546-137">Nome</span><span class="sxs-lookup"><span data-stu-id="0d546-137">Name</span></span>  
 <span data-ttu-id="0d546-138">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="0d546-138">Data type: string</span></span>  
  
 <span data-ttu-id="0d546-139">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="0d546-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0d546-140">O atributo de nome do serviço em WSDL.</span><span class="sxs-lookup"><span data-stu-id="0d546-140">The name attribute of the service in WSDL.</span></span>  
  
### <a name="namespace"></a><span data-ttu-id="0d546-141">Namespace</span><span class="sxs-lookup"><span data-stu-id="0d546-141">Namespace</span></span>  
 <span data-ttu-id="0d546-142">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="0d546-142">Data type: string</span></span>  
  
 <span data-ttu-id="0d546-143">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="0d546-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0d546-144">O namespace de destino do serviço em WSDL.</span><span class="sxs-lookup"><span data-stu-id="0d546-144">The target namespace of the service in WSDL.</span></span>  
  
### <a name="releaseserviceinstanceontransactioncomplete"></a><span data-ttu-id="0d546-145">ReleaseServiceInstanceOnTransactionComplete</span><span class="sxs-lookup"><span data-stu-id="0d546-145">ReleaseServiceInstanceOnTransactionComplete</span></span>  
 <span data-ttu-id="0d546-146">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="0d546-146">Data type: boolean</span></span>  
  
 <span data-ttu-id="0d546-147">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="0d546-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0d546-148">Especifica se o objeto de serviço será reciclado quando a transação atual seja concluída.</span><span class="sxs-lookup"><span data-stu-id="0d546-148">Specifies whether the service object is recycled when the current transaction completes.</span></span>  
  
### <a name="transactionautocompleteonsessionclose"></a><span data-ttu-id="0d546-149">TransactionAutoCompleteOnSessionClose</span><span class="sxs-lookup"><span data-stu-id="0d546-149">TransactionAutoCompleteOnSessionClose</span></span>  
 <span data-ttu-id="0d546-150">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="0d546-150">Data type: boolean</span></span>  
  
 <span data-ttu-id="0d546-151">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="0d546-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0d546-152">Especifica se as transações pendentes a são concluídos quando fecha a sessão atual.</span><span class="sxs-lookup"><span data-stu-id="0d546-152">Specifies whether pending transactions are completed when the current session closes.</span></span>  
  
### <a name="transactionisolationlevel"></a><span data-ttu-id="0d546-153">TransactionIsolationLevel</span><span class="sxs-lookup"><span data-stu-id="0d546-153">TransactionIsolationLevel</span></span>  
 <span data-ttu-id="0d546-154">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="0d546-154">Data type: string</span></span>  
  
 <span data-ttu-id="0d546-155">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="0d546-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0d546-156">Especifica o nível de isolamento da transação.</span><span class="sxs-lookup"><span data-stu-id="0d546-156">Specifies the transaction isolation level.</span></span>  
  
### <a name="transactiontimeout"></a><span data-ttu-id="0d546-157">TransactionTimeout</span><span class="sxs-lookup"><span data-stu-id="0d546-157">TransactionTimeout</span></span>  
 <span data-ttu-id="0d546-158">Tipo de dados: datetime</span><span class="sxs-lookup"><span data-stu-id="0d546-158">Data type: datetime</span></span>  
  
 <span data-ttu-id="0d546-159">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="0d546-159">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0d546-160">O período no qual uma transação deve ser concluída.</span><span class="sxs-lookup"><span data-stu-id="0d546-160">The period within which a transaction must complete.</span></span>  
  
### <a name="usesynchronizationcontext"></a><span data-ttu-id="0d546-161">UseSynchronizationContext</span><span class="sxs-lookup"><span data-stu-id="0d546-161">UseSynchronizationContext</span></span>  
 <span data-ttu-id="0d546-162">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="0d546-162">Data type: boolean</span></span>  
  
 <span data-ttu-id="0d546-163">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="0d546-163">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0d546-164">Especifica se deve usar o contexto de sincronização atual para escolher a execução de thread.</span><span class="sxs-lookup"><span data-stu-id="0d546-164">Specifies whether to use the current synchronization context to choose the thread execution.</span></span>  
  
### <a name="validatemustunderstand"></a><span data-ttu-id="0d546-165">ValidateMustUnderstand</span><span class="sxs-lookup"><span data-stu-id="0d546-165">ValidateMustUnderstand</span></span>  
 <span data-ttu-id="0d546-166">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="0d546-166">Data type: boolean</span></span>  
  
 <span data-ttu-id="0d546-167">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="0d546-167">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0d546-168">Especifica se o sistema ou o aplicativo reforça o processamento de cabeçalho MustUnderstand SOAP.</span><span class="sxs-lookup"><span data-stu-id="0d546-168">Specifies whether the system or the application enforces SOAP MustUnderstand header processing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0d546-169">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0d546-169">Requirements</span></span>  
  
|<span data-ttu-id="0d546-170">MOF</span><span class="sxs-lookup"><span data-stu-id="0d546-170">MOF</span></span>|<span data-ttu-id="0d546-171">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="0d546-171">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="0d546-172">Namespace</span><span class="sxs-lookup"><span data-stu-id="0d546-172">Namespace</span></span>|<span data-ttu-id="0d546-173">Definido em root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="0d546-173">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0d546-174">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0d546-174">See Also</span></span>  
 <xref:System.ServiceModel.ServiceBehaviorAttribute>
