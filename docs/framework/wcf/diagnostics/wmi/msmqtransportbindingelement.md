---
title: MsmqTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 1c89f073-9ed3-4025-a8c5-13535a0f526b
ms.openlocfilehash: d37ee4527226d9347e24fc2ee8007a263c71f198
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54564871"
---
# <a name="msmqtransportbindingelement"></a><span data-ttu-id="9c6aa-102">MsmqTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="9c6aa-102">MsmqTransportBindingElement</span></span>
<span data-ttu-id="9c6aa-103">MsmqTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="9c6aa-103">MsmqTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c6aa-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9c6aa-104">Syntax</span></span>  
  
```csharp
class MsmqTransportBindingElement : MsmqBindingElementBase  
{  
  sint32 MaxPoolSize;  
  string QueueTransferProtocol;  
  boolean UseActiveDirectory;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="9c6aa-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="9c6aa-105">Methods</span></span>  
 <span data-ttu-id="9c6aa-106">A classe MsmqTransportBindingElement não define quaisquer métodos.</span><span class="sxs-lookup"><span data-stu-id="9c6aa-106">The MsmqTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="9c6aa-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="9c6aa-107">Properties</span></span>  
 <span data-ttu-id="9c6aa-108">A classe MsmqTransportBindingElement tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="9c6aa-108">The MsmqTransportBindingElement class has the following properties:</span></span>  
  
### <a name="maxpoolsize"></a><span data-ttu-id="9c6aa-109">MaxPoolSize</span><span class="sxs-lookup"><span data-stu-id="9c6aa-109">MaxPoolSize</span></span>  
 <span data-ttu-id="9c6aa-110">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="9c6aa-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="9c6aa-111">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="9c6aa-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9c6aa-112">O tamanho máximo do pool que contém objetos de mensagem MSMQ internos.</span><span class="sxs-lookup"><span data-stu-id="9c6aa-112">The maximum size of the pool that contains internal MSMQ message objects.</span></span>  
  
### <a name="queuetransferprotocol"></a><span data-ttu-id="9c6aa-113">QueueTransferProtocol</span><span class="sxs-lookup"><span data-stu-id="9c6aa-113">QueueTransferProtocol</span></span>  
 <span data-ttu-id="9c6aa-114">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="9c6aa-114">Data type: string</span></span>  
  
 <span data-ttu-id="9c6aa-115">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="9c6aa-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9c6aa-116">Um valor de enumeração que indica o transporte de canal de comunicação em fila que esta associação usa.</span><span class="sxs-lookup"><span data-stu-id="9c6aa-116">An enumeration value that indicates the queued communication channel transport that this binding uses.</span></span>  
  
### <a name="useactivedirectory"></a><span data-ttu-id="9c6aa-117">UseActiveDirectory</span><span class="sxs-lookup"><span data-stu-id="9c6aa-117">UseActiveDirectory</span></span>  
 <span data-ttu-id="9c6aa-118">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="9c6aa-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="9c6aa-119">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="9c6aa-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9c6aa-120">Retorna um valor booliano que indica se os endereços da fila devem ser convertidos usando o Active Directory.</span><span class="sxs-lookup"><span data-stu-id="9c6aa-120">Returns a Boolean value that indicates whether queue addresses should be converted using Active Directory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9c6aa-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9c6aa-121">Requirements</span></span>  
  
|<span data-ttu-id="9c6aa-122">MOF</span><span class="sxs-lookup"><span data-stu-id="9c6aa-122">MOF</span></span>|<span data-ttu-id="9c6aa-123">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="9c6aa-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="9c6aa-124">Namespace</span><span class="sxs-lookup"><span data-stu-id="9c6aa-124">Namespace</span></span>|<span data-ttu-id="9c6aa-125">Definido no root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="9c6aa-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9c6aa-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9c6aa-126">See also</span></span>
- <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>
