---
title: ServiceBehaviorAttribute
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5faa266f-587f-4e03-828d-1c7dd5acfe65
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f7401acd5aefcb7a8c02ea6c05a94374e41d9b9d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="servicebehaviorattribute"></a><span data-ttu-id="bafc6-102">ServiceBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="bafc6-102">ServiceBehaviorAttribute</span></span>
<span data-ttu-id="bafc6-103">ServiceBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="bafc6-103">ServiceBehaviorAttribute</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bafc6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bafc6-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="bafc6-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="bafc6-105">Methods</span></span>  
 <span data-ttu-id="bafc6-106">A classe ServiceBehaviorAttribute não define nenhum método.</span><span class="sxs-lookup"><span data-stu-id="bafc6-106">The ServiceBehaviorAttribute class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="bafc6-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="bafc6-107">Properties</span></span>  
 <span data-ttu-id="bafc6-108">A classe ServiceBehaviorAttribute tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="bafc6-108">The ServiceBehaviorAttribute class has the following properties:</span></span>  
  
### <a name="automaticsessionshutdown"></a><span data-ttu-id="bafc6-109">AutomaticSessionShutdown</span><span class="sxs-lookup"><span data-stu-id="bafc6-109">AutomaticSessionShutdown</span></span>  
 <span data-ttu-id="bafc6-110">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="bafc6-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="bafc6-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="bafc6-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bafc6-112">Indica se fechar automaticamente uma sessão quando um cliente fechar uma sessão de saída.</span><span class="sxs-lookup"><span data-stu-id="bafc6-112">Indicates whether to automatically close a session when a client closes an output session.</span></span>  
  
### <a name="concurrencymode"></a><span data-ttu-id="bafc6-113">ConcurrencyMode</span><span class="sxs-lookup"><span data-stu-id="bafc6-113">ConcurrencyMode</span></span>  
 <span data-ttu-id="bafc6-114">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="bafc6-114">Data type: string</span></span>  
<span data-ttu-id="bafc6-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="bafc6-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bafc6-116">Indica se um serviço oferece suporte a um thread, vários threads ou chamadas reentrantes.</span><span class="sxs-lookup"><span data-stu-id="bafc6-116">Indicates whether a service supports one thread, multiple threads, or reentrant calls.</span></span>  
  
### <a name="configurationname"></a><span data-ttu-id="bafc6-117">ConfigurationName</span><span class="sxs-lookup"><span data-stu-id="bafc6-117">ConfigurationName</span></span>  
 <span data-ttu-id="bafc6-118">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="bafc6-118">Data type: string</span></span>  
  
 <span data-ttu-id="bafc6-119">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="bafc6-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bafc6-120">O nome da configuração do serviço.</span><span class="sxs-lookup"><span data-stu-id="bafc6-120">The name of the service configuration.</span></span>  
  
### <a name="ignoreextensiondataobject"></a><span data-ttu-id="bafc6-121">IgnoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="bafc6-121">IgnoreExtensionDataObject</span></span>  
 <span data-ttu-id="bafc6-122">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="bafc6-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="bafc6-123">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="bafc6-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bafc6-124">Especifica se deve enviar dados de serialização desconhecidos na conexão.</span><span class="sxs-lookup"><span data-stu-id="bafc6-124">Specifies whether to send unknown serialization data onto the wire.</span></span>  
  
### <a name="includeexceptiondetailinfaults"></a><span data-ttu-id="bafc6-125">includeExceptionDetailInFaults</span><span class="sxs-lookup"><span data-stu-id="bafc6-125">IncludeExceptionDetailInFaults</span></span>  
 <span data-ttu-id="bafc6-126">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="bafc6-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="bafc6-127">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="bafc6-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bafc6-128">Especifica se deve incluir informações de exceção gerenciada no detalhe de falhas SOAP retornadas aos clientes para fins de depuração.</span><span class="sxs-lookup"><span data-stu-id="bafc6-128">Specifies whether to include managed exception information in the detail of SOAP faults returned to the clients for debugging purposes.</span></span>  
  
### <a name="instancecontextmode"></a><span data-ttu-id="bafc6-129">InstanceContextMode</span><span class="sxs-lookup"><span data-stu-id="bafc6-129">InstanceContextMode</span></span>  
 <span data-ttu-id="bafc6-130">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="bafc6-130">Data type: string</span></span>  
  
 <span data-ttu-id="bafc6-131">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="bafc6-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bafc6-132">Especifica quando um novo objeto de serviço é criado.</span><span class="sxs-lookup"><span data-stu-id="bafc6-132">Specifies when a new service object is created.</span></span>  
  
### <a name="maxitemsinobjectgraph"></a><span data-ttu-id="bafc6-133">MaxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="bafc6-133">MaxItemsInObjectGraph</span></span>  
 <span data-ttu-id="bafc6-134">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="bafc6-134">Data type: sint32</span></span>  
  
 <span data-ttu-id="bafc6-135">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="bafc6-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bafc6-136">O número máximo de itens permitidos em um objeto serializado.</span><span class="sxs-lookup"><span data-stu-id="bafc6-136">The maximum number of items allowed in a serialized object.</span></span>  
  
### <a name="name"></a><span data-ttu-id="bafc6-137">Nome</span><span class="sxs-lookup"><span data-stu-id="bafc6-137">Name</span></span>  
 <span data-ttu-id="bafc6-138">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="bafc6-138">Data type: string</span></span>  
  
 <span data-ttu-id="bafc6-139">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="bafc6-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bafc6-140">O atributo de nome do serviço em WSDL.</span><span class="sxs-lookup"><span data-stu-id="bafc6-140">The name attribute of the service in WSDL.</span></span>  
  
### <a name="namespace"></a><span data-ttu-id="bafc6-141">Namespace</span><span class="sxs-lookup"><span data-stu-id="bafc6-141">Namespace</span></span>  
 <span data-ttu-id="bafc6-142">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="bafc6-142">Data type: string</span></span>  
  
 <span data-ttu-id="bafc6-143">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="bafc6-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bafc6-144">O namespace de destino do serviço em WSDL.</span><span class="sxs-lookup"><span data-stu-id="bafc6-144">The target namespace of the service in WSDL.</span></span>  
  
### <a name="releaseserviceinstanceontransactioncomplete"></a><span data-ttu-id="bafc6-145">ReleaseServiceInstanceOnTransactionComplete</span><span class="sxs-lookup"><span data-stu-id="bafc6-145">ReleaseServiceInstanceOnTransactionComplete</span></span>  
 <span data-ttu-id="bafc6-146">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="bafc6-146">Data type: boolean</span></span>  
  
 <span data-ttu-id="bafc6-147">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="bafc6-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bafc6-148">Especifica se o objeto de serviço será reciclado quando a transação atual seja concluída.</span><span class="sxs-lookup"><span data-stu-id="bafc6-148">Specifies whether the service object is recycled when the current transaction completes.</span></span>  
  
### <a name="transactionautocompleteonsessionclose"></a><span data-ttu-id="bafc6-149">TransactionAutoCompleteOnSessionClose</span><span class="sxs-lookup"><span data-stu-id="bafc6-149">TransactionAutoCompleteOnSessionClose</span></span>  
 <span data-ttu-id="bafc6-150">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="bafc6-150">Data type: boolean</span></span>  
  
 <span data-ttu-id="bafc6-151">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="bafc6-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bafc6-152">Especifica se as transações pendentes a são concluídos quando fecha a sessão atual.</span><span class="sxs-lookup"><span data-stu-id="bafc6-152">Specifies whether pending transactions are completed when the current session closes.</span></span>  
  
### <a name="transactionisolationlevel"></a><span data-ttu-id="bafc6-153">TransactionIsolationLevel</span><span class="sxs-lookup"><span data-stu-id="bafc6-153">TransactionIsolationLevel</span></span>  
 <span data-ttu-id="bafc6-154">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="bafc6-154">Data type: string</span></span>  
  
 <span data-ttu-id="bafc6-155">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="bafc6-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bafc6-156">Especifica o nível de isolamento da transação.</span><span class="sxs-lookup"><span data-stu-id="bafc6-156">Specifies the transaction isolation level.</span></span>  
  
### <a name="transactiontimeout"></a><span data-ttu-id="bafc6-157">TransactionTimeout</span><span class="sxs-lookup"><span data-stu-id="bafc6-157">TransactionTimeout</span></span>  
 <span data-ttu-id="bafc6-158">Tipo de dados: datetime</span><span class="sxs-lookup"><span data-stu-id="bafc6-158">Data type: datetime</span></span>  
  
 <span data-ttu-id="bafc6-159">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="bafc6-159">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bafc6-160">O período no qual uma transação deve ser concluída.</span><span class="sxs-lookup"><span data-stu-id="bafc6-160">The period within which a transaction must complete.</span></span>  
  
### <a name="usesynchronizationcontext"></a><span data-ttu-id="bafc6-161">UseSynchronizationContext</span><span class="sxs-lookup"><span data-stu-id="bafc6-161">UseSynchronizationContext</span></span>  
 <span data-ttu-id="bafc6-162">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="bafc6-162">Data type: boolean</span></span>  
  
 <span data-ttu-id="bafc6-163">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="bafc6-163">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bafc6-164">Especifica se deve usar o contexto de sincronização atual para escolher a execução de thread.</span><span class="sxs-lookup"><span data-stu-id="bafc6-164">Specifies whether to use the current synchronization context to choose the thread execution.</span></span>  
  
### <a name="validatemustunderstand"></a><span data-ttu-id="bafc6-165">ValidateMustUnderstand</span><span class="sxs-lookup"><span data-stu-id="bafc6-165">ValidateMustUnderstand</span></span>  
 <span data-ttu-id="bafc6-166">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="bafc6-166">Data type: boolean</span></span>  
  
 <span data-ttu-id="bafc6-167">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="bafc6-167">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bafc6-168">Especifica se o sistema ou o aplicativo reforça o processamento de cabeçalho MustUnderstand SOAP.</span><span class="sxs-lookup"><span data-stu-id="bafc6-168">Specifies whether the system or the application enforces SOAP MustUnderstand header processing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bafc6-169">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bafc6-169">Requirements</span></span>  
  
|<span data-ttu-id="bafc6-170">MOF</span><span class="sxs-lookup"><span data-stu-id="bafc6-170">MOF</span></span>|<span data-ttu-id="bafc6-171">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="bafc6-171">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="bafc6-172">Namespace</span><span class="sxs-lookup"><span data-stu-id="bafc6-172">Namespace</span></span>|<span data-ttu-id="bafc6-173">Definido em root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="bafc6-173">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bafc6-174">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bafc6-174">See Also</span></span>  
 <xref:System.ServiceModel.ServiceBehaviorAttribute>
