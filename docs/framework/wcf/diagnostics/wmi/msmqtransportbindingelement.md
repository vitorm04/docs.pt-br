---
title: MsmqTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 1c89f073-9ed3-4025-a8c5-13535a0f526b
ms.openlocfilehash: 706cec5c414197ebabda7939728b95be32582e0f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61963300"
---
# <a name="msmqtransportbindingelement"></a><span data-ttu-id="8296d-102">MsmqTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="8296d-102">MsmqTransportBindingElement</span></span>
<span data-ttu-id="8296d-103">MsmqTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="8296d-103">MsmqTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8296d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8296d-104">Syntax</span></span>  
  
```csharp
class MsmqTransportBindingElement : MsmqBindingElementBase  
{  
  sint32 MaxPoolSize;  
  string QueueTransferProtocol;  
  boolean UseActiveDirectory;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="8296d-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="8296d-105">Methods</span></span>  
 <span data-ttu-id="8296d-106">A classe MsmqTransportBindingElement não define quaisquer métodos.</span><span class="sxs-lookup"><span data-stu-id="8296d-106">The MsmqTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="8296d-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="8296d-107">Properties</span></span>  
 <span data-ttu-id="8296d-108">A classe MsmqTransportBindingElement tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="8296d-108">The MsmqTransportBindingElement class has the following properties:</span></span>  
  
### <a name="maxpoolsize"></a><span data-ttu-id="8296d-109">MaxPoolSize</span><span class="sxs-lookup"><span data-stu-id="8296d-109">MaxPoolSize</span></span>  
 <span data-ttu-id="8296d-110">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="8296d-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="8296d-111">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="8296d-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8296d-112">O tamanho máximo do pool que contém objetos de mensagem MSMQ internos.</span><span class="sxs-lookup"><span data-stu-id="8296d-112">The maximum size of the pool that contains internal MSMQ message objects.</span></span>  
  
### <a name="queuetransferprotocol"></a><span data-ttu-id="8296d-113">QueueTransferProtocol</span><span class="sxs-lookup"><span data-stu-id="8296d-113">QueueTransferProtocol</span></span>  
 <span data-ttu-id="8296d-114">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="8296d-114">Data type: string</span></span>  
  
 <span data-ttu-id="8296d-115">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="8296d-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8296d-116">Um valor de enumeração que indica o transporte de canal de comunicação em fila que esta associação usa.</span><span class="sxs-lookup"><span data-stu-id="8296d-116">An enumeration value that indicates the queued communication channel transport that this binding uses.</span></span>  
  
### <a name="useactivedirectory"></a><span data-ttu-id="8296d-117">UseActiveDirectory</span><span class="sxs-lookup"><span data-stu-id="8296d-117">UseActiveDirectory</span></span>  
 <span data-ttu-id="8296d-118">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="8296d-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="8296d-119">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="8296d-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8296d-120">Retorna um valor booliano que indica se os endereços da fila devem ser convertidos usando o Active Directory.</span><span class="sxs-lookup"><span data-stu-id="8296d-120">Returns a Boolean value that indicates whether queue addresses should be converted using Active Directory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8296d-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8296d-121">Requirements</span></span>  
  
|<span data-ttu-id="8296d-122">MOF</span><span class="sxs-lookup"><span data-stu-id="8296d-122">MOF</span></span>|<span data-ttu-id="8296d-123">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="8296d-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="8296d-124">Namespace</span><span class="sxs-lookup"><span data-stu-id="8296d-124">Namespace</span></span>|<span data-ttu-id="8296d-125">Definido no root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="8296d-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8296d-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8296d-126">See also</span></span>

- <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>
