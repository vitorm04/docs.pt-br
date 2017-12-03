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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0a3bc0116ec34a3370012472c31a9191cf26f720
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="servicebehaviorattribute"></a><span data-ttu-id="65d17-102">ServiceBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="65d17-102">ServiceBehaviorAttribute</span></span>
<span data-ttu-id="65d17-103">ServiceBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="65d17-103">ServiceBehaviorAttribute</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65d17-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="65d17-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="65d17-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="65d17-105">Methods</span></span>  
 <span data-ttu-id="65d17-106">A classe ServiceBehaviorAttribute não define nenhum método.</span><span class="sxs-lookup"><span data-stu-id="65d17-106">The ServiceBehaviorAttribute class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="65d17-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="65d17-107">Properties</span></span>  
 <span data-ttu-id="65d17-108">A classe ServiceBehaviorAttribute tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="65d17-108">The ServiceBehaviorAttribute class has the following properties:</span></span>  
  
### <a name="automaticsessionshutdown"></a><span data-ttu-id="65d17-109">AutomaticSessionShutdown</span><span class="sxs-lookup"><span data-stu-id="65d17-109">AutomaticSessionShutdown</span></span>  
 <span data-ttu-id="65d17-110">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="65d17-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="65d17-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="65d17-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="65d17-112">Indica se fechar automaticamente uma sessão quando um cliente fechar uma sessão de saída.</span><span class="sxs-lookup"><span data-stu-id="65d17-112">Indicates whether to automatically close a session when a client closes an output session.</span></span>  
  
### <a name="concurrencymode"></a><span data-ttu-id="65d17-113">ConcurrencyMode</span><span class="sxs-lookup"><span data-stu-id="65d17-113">ConcurrencyMode</span></span>  
 <span data-ttu-id="65d17-114">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="65d17-114">Data type: string</span></span>  
<span data-ttu-id="65d17-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="65d17-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="65d17-116">Indica se um serviço oferece suporte a um thread, vários threads ou chamadas reentrantes.</span><span class="sxs-lookup"><span data-stu-id="65d17-116">Indicates whether a service supports one thread, multiple threads, or reentrant calls.</span></span>  
  
### <a name="configurationname"></a><span data-ttu-id="65d17-117">ConfigurationName</span><span class="sxs-lookup"><span data-stu-id="65d17-117">ConfigurationName</span></span>  
 <span data-ttu-id="65d17-118">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="65d17-118">Data type: string</span></span>  
  
 <span data-ttu-id="65d17-119">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="65d17-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="65d17-120">O nome da configuração do serviço.</span><span class="sxs-lookup"><span data-stu-id="65d17-120">The name of the service configuration.</span></span>  
  
### <a name="ignoreextensiondataobject"></a><span data-ttu-id="65d17-121">IgnoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="65d17-121">IgnoreExtensionDataObject</span></span>  
 <span data-ttu-id="65d17-122">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="65d17-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="65d17-123">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="65d17-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="65d17-124">Especifica se deve enviar dados de serialização desconhecidos na conexão.</span><span class="sxs-lookup"><span data-stu-id="65d17-124">Specifies whether to send unknown serialization data onto the wire.</span></span>  
  
### <a name="includeexceptiondetailinfaults"></a><span data-ttu-id="65d17-125">includeExceptionDetailInFaults</span><span class="sxs-lookup"><span data-stu-id="65d17-125">IncludeExceptionDetailInFaults</span></span>  
 <span data-ttu-id="65d17-126">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="65d17-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="65d17-127">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="65d17-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="65d17-128">Especifica se deve incluir informações de exceção gerenciada no detalhe de falhas SOAP retornadas aos clientes para fins de depuração.</span><span class="sxs-lookup"><span data-stu-id="65d17-128">Specifies whether to include managed exception information in the detail of SOAP faults returned to the clients for debugging purposes.</span></span>  
  
### <a name="instancecontextmode"></a><span data-ttu-id="65d17-129">InstanceContextMode</span><span class="sxs-lookup"><span data-stu-id="65d17-129">InstanceContextMode</span></span>  
 <span data-ttu-id="65d17-130">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="65d17-130">Data type: string</span></span>  
  
 <span data-ttu-id="65d17-131">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="65d17-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="65d17-132">Especifica quando um novo objeto de serviço é criado.</span><span class="sxs-lookup"><span data-stu-id="65d17-132">Specifies when a new service object is created.</span></span>  
  
### <a name="maxitemsinobjectgraph"></a><span data-ttu-id="65d17-133">MaxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="65d17-133">MaxItemsInObjectGraph</span></span>  
 <span data-ttu-id="65d17-134">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="65d17-134">Data type: sint32</span></span>  
  
 <span data-ttu-id="65d17-135">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="65d17-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="65d17-136">O número máximo de itens permitidos em um objeto serializado.</span><span class="sxs-lookup"><span data-stu-id="65d17-136">The maximum number of items allowed in a serialized object.</span></span>  
  
### <a name="name"></a><span data-ttu-id="65d17-137">Nome</span><span class="sxs-lookup"><span data-stu-id="65d17-137">Name</span></span>  
 <span data-ttu-id="65d17-138">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="65d17-138">Data type: string</span></span>  
  
 <span data-ttu-id="65d17-139">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="65d17-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="65d17-140">O atributo de nome do serviço em WSDL.</span><span class="sxs-lookup"><span data-stu-id="65d17-140">The name attribute of the service in WSDL.</span></span>  
  
### <a name="namespace"></a><span data-ttu-id="65d17-141">Namespace</span><span class="sxs-lookup"><span data-stu-id="65d17-141">Namespace</span></span>  
 <span data-ttu-id="65d17-142">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="65d17-142">Data type: string</span></span>  
  
 <span data-ttu-id="65d17-143">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="65d17-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="65d17-144">O namespace de destino do serviço em WSDL.</span><span class="sxs-lookup"><span data-stu-id="65d17-144">The target namespace of the service in WSDL.</span></span>  
  
### <a name="releaseserviceinstanceontransactioncomplete"></a><span data-ttu-id="65d17-145">ReleaseServiceInstanceOnTransactionComplete</span><span class="sxs-lookup"><span data-stu-id="65d17-145">ReleaseServiceInstanceOnTransactionComplete</span></span>  
 <span data-ttu-id="65d17-146">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="65d17-146">Data type: boolean</span></span>  
  
 <span data-ttu-id="65d17-147">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="65d17-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="65d17-148">Especifica se o objeto de serviço será reciclado quando a transação atual seja concluída.</span><span class="sxs-lookup"><span data-stu-id="65d17-148">Specifies whether the service object is recycled when the current transaction completes.</span></span>  
  
### <a name="transactionautocompleteonsessionclose"></a><span data-ttu-id="65d17-149">TransactionAutoCompleteOnSessionClose</span><span class="sxs-lookup"><span data-stu-id="65d17-149">TransactionAutoCompleteOnSessionClose</span></span>  
 <span data-ttu-id="65d17-150">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="65d17-150">Data type: boolean</span></span>  
  
 <span data-ttu-id="65d17-151">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="65d17-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="65d17-152">Especifica se as transações pendentes a são concluídos quando fecha a sessão atual.</span><span class="sxs-lookup"><span data-stu-id="65d17-152">Specifies whether pending transactions are completed when the current session closes.</span></span>  
  
### <a name="transactionisolationlevel"></a><span data-ttu-id="65d17-153">TransactionIsolationLevel</span><span class="sxs-lookup"><span data-stu-id="65d17-153">TransactionIsolationLevel</span></span>  
 <span data-ttu-id="65d17-154">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="65d17-154">Data type: string</span></span>  
  
 <span data-ttu-id="65d17-155">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="65d17-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="65d17-156">Especifica o nível de isolamento da transação.</span><span class="sxs-lookup"><span data-stu-id="65d17-156">Specifies the transaction isolation level.</span></span>  
  
### <a name="transactiontimeout"></a><span data-ttu-id="65d17-157">TransactionTimeout</span><span class="sxs-lookup"><span data-stu-id="65d17-157">TransactionTimeout</span></span>  
 <span data-ttu-id="65d17-158">Tipo de dados: datetime</span><span class="sxs-lookup"><span data-stu-id="65d17-158">Data type: datetime</span></span>  
  
 <span data-ttu-id="65d17-159">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="65d17-159">Access type: Read-only</span></span>  
  
 <span data-ttu-id="65d17-160">O período no qual uma transação deve ser concluída.</span><span class="sxs-lookup"><span data-stu-id="65d17-160">The period within which a transaction must complete.</span></span>  
  
### <a name="usesynchronizationcontext"></a><span data-ttu-id="65d17-161">UseSynchronizationContext</span><span class="sxs-lookup"><span data-stu-id="65d17-161">UseSynchronizationContext</span></span>  
 <span data-ttu-id="65d17-162">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="65d17-162">Data type: boolean</span></span>  
  
 <span data-ttu-id="65d17-163">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="65d17-163">Access type: Read-only</span></span>  
  
 <span data-ttu-id="65d17-164">Especifica se deve usar o contexto de sincronização atual para escolher a execução de thread.</span><span class="sxs-lookup"><span data-stu-id="65d17-164">Specifies whether to use the current synchronization context to choose the thread execution.</span></span>  
  
### <a name="validatemustunderstand"></a><span data-ttu-id="65d17-165">ValidateMustUnderstand</span><span class="sxs-lookup"><span data-stu-id="65d17-165">ValidateMustUnderstand</span></span>  
 <span data-ttu-id="65d17-166">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="65d17-166">Data type: boolean</span></span>  
  
 <span data-ttu-id="65d17-167">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="65d17-167">Access type: Read-only</span></span>  
  
 <span data-ttu-id="65d17-168">Especifica se o sistema ou o aplicativo reforça o processamento de cabeçalho MustUnderstand SOAP.</span><span class="sxs-lookup"><span data-stu-id="65d17-168">Specifies whether the system or the application enforces SOAP MustUnderstand header processing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65d17-169">Requisitos</span><span class="sxs-lookup"><span data-stu-id="65d17-169">Requirements</span></span>  
  
|<span data-ttu-id="65d17-170">MOF</span><span class="sxs-lookup"><span data-stu-id="65d17-170">MOF</span></span>|<span data-ttu-id="65d17-171">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="65d17-171">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="65d17-172">Namespace</span><span class="sxs-lookup"><span data-stu-id="65d17-172">Namespace</span></span>|<span data-ttu-id="65d17-173">Definido em root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="65d17-173">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="65d17-174">Consulte também</span><span class="sxs-lookup"><span data-stu-id="65d17-174">See Also</span></span>  
 <xref:System.ServiceModel.ServiceBehaviorAttribute>
