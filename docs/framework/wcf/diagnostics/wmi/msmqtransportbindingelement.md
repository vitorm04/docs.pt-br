---
title: MsmqTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 1c89f073-9ed3-4025-a8c5-13535a0f526b
ms.openlocfilehash: 33cd9c427ed5ad04eaf9e9889f60f091f335d1e7
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50045982"
---
# <a name="msmqtransportbindingelement"></a><span data-ttu-id="062a1-102">MsmqTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="062a1-102">MsmqTransportBindingElement</span></span>
<span data-ttu-id="062a1-103">MsmqTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="062a1-103">MsmqTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="062a1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="062a1-104">Syntax</span></span>  
  
```csharp
class MsmqTransportBindingElement : MsmqBindingElementBase  
{  
  sint32 MaxPoolSize;  
  string QueueTransferProtocol;  
  boolean UseActiveDirectory;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="062a1-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="062a1-105">Methods</span></span>  
 <span data-ttu-id="062a1-106">A classe MsmqTransportBindingElement não define quaisquer métodos.</span><span class="sxs-lookup"><span data-stu-id="062a1-106">The MsmqTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="062a1-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="062a1-107">Properties</span></span>  
 <span data-ttu-id="062a1-108">A classe MsmqTransportBindingElement tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="062a1-108">The MsmqTransportBindingElement class has the following properties:</span></span>  
  
### <a name="maxpoolsize"></a><span data-ttu-id="062a1-109">MaxPoolSize</span><span class="sxs-lookup"><span data-stu-id="062a1-109">MaxPoolSize</span></span>  
 <span data-ttu-id="062a1-110">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="062a1-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="062a1-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="062a1-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="062a1-112">O tamanho máximo do pool que contém objetos de mensagem MSMQ internos.</span><span class="sxs-lookup"><span data-stu-id="062a1-112">The maximum size of the pool that contains internal MSMQ message objects.</span></span>  
  
### <a name="queuetransferprotocol"></a><span data-ttu-id="062a1-113">queueTransferProtocol</span><span class="sxs-lookup"><span data-stu-id="062a1-113">QueueTransferProtocol</span></span>  
 <span data-ttu-id="062a1-114">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="062a1-114">Data type: string</span></span>  
  
 <span data-ttu-id="062a1-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="062a1-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="062a1-116">Um valor de enumeração que indica o transporte de canal de comunicação em fila que esta associação usa.</span><span class="sxs-lookup"><span data-stu-id="062a1-116">An enumeration value that indicates the queued communication channel transport that this binding uses.</span></span>  
  
### <a name="useactivedirectory"></a><span data-ttu-id="062a1-117">UseActiveDirectory</span><span class="sxs-lookup"><span data-stu-id="062a1-117">UseActiveDirectory</span></span>  
 <span data-ttu-id="062a1-118">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="062a1-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="062a1-119">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="062a1-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="062a1-120">Retorna um valor booliano que indica se os endereços da fila devem ser convertidos usando o Active Directory.</span><span class="sxs-lookup"><span data-stu-id="062a1-120">Returns a Boolean value that indicates whether queue addresses should be converted using Active Directory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="062a1-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="062a1-121">Requirements</span></span>  
  
|<span data-ttu-id="062a1-122">MOF</span><span class="sxs-lookup"><span data-stu-id="062a1-122">MOF</span></span>|<span data-ttu-id="062a1-123">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="062a1-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="062a1-124">Namespace</span><span class="sxs-lookup"><span data-stu-id="062a1-124">Namespace</span></span>|<span data-ttu-id="062a1-125">Definido no root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="062a1-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="062a1-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="062a1-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>
