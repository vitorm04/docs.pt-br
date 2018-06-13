---
title: MsmqTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 1c89f073-9ed3-4025-a8c5-13535a0f526b
ms.openlocfilehash: 643ab0f30c771f79df8ef7dd885013d5186fba59
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33485902"
---
# <a name="msmqtransportbindingelement"></a><span data-ttu-id="07673-102">MsmqTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="07673-102">MsmqTransportBindingElement</span></span>
<span data-ttu-id="07673-103">MsmqTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="07673-103">MsmqTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07673-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="07673-104">Syntax</span></span>  
  
```  
class MsmqTransportBindingElement : MsmqBindingElementBase  
{  
  sint32 MaxPoolSize;  
  string QueueTransferProtocol;  
  boolean UseActiveDirectory;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="07673-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="07673-105">Methods</span></span>  
 <span data-ttu-id="07673-106">A classe MsmqTransportBindingElement não define nenhum método.</span><span class="sxs-lookup"><span data-stu-id="07673-106">The MsmqTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="07673-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="07673-107">Properties</span></span>  
 <span data-ttu-id="07673-108">A classe MsmqTransportBindingElement tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="07673-108">The MsmqTransportBindingElement class has the following properties:</span></span>  
  
### <a name="maxpoolsize"></a><span data-ttu-id="07673-109">MaxPoolSize</span><span class="sxs-lookup"><span data-stu-id="07673-109">MaxPoolSize</span></span>  
 <span data-ttu-id="07673-110">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="07673-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="07673-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="07673-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="07673-112">O tamanho máximo do pool que contém objetos de mensagem MSMQ internos.</span><span class="sxs-lookup"><span data-stu-id="07673-112">The maximum size of the pool that contains internal MSMQ message objects.</span></span>  
  
### <a name="queuetransferprotocol"></a><span data-ttu-id="07673-113">QueueTransferProtocol</span><span class="sxs-lookup"><span data-stu-id="07673-113">QueueTransferProtocol</span></span>  
 <span data-ttu-id="07673-114">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="07673-114">Data type: string</span></span>  
  
 <span data-ttu-id="07673-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="07673-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="07673-116">Um valor de enumeração que indica o transporte de canal de comunicação em fila que esta associação usa.</span><span class="sxs-lookup"><span data-stu-id="07673-116">An enumeration value that indicates the queued communication channel transport that this binding uses.</span></span>  
  
### <a name="useactivedirectory"></a><span data-ttu-id="07673-117">Propriedade UseActiveDirectory</span><span class="sxs-lookup"><span data-stu-id="07673-117">UseActiveDirectory</span></span>  
 <span data-ttu-id="07673-118">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="07673-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="07673-119">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="07673-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="07673-120">Retorna um valor booliano que indica se os endereços da fila devem ser convertidos usando o Active Directory.</span><span class="sxs-lookup"><span data-stu-id="07673-120">Returns a Boolean value that indicates whether queue addresses should be converted using Active Directory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="07673-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="07673-121">Requirements</span></span>  
  
|<span data-ttu-id="07673-122">MOF</span><span class="sxs-lookup"><span data-stu-id="07673-122">MOF</span></span>|<span data-ttu-id="07673-123">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="07673-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="07673-124">Namespace</span><span class="sxs-lookup"><span data-stu-id="07673-124">Namespace</span></span>|<span data-ttu-id="07673-125">Definido em root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="07673-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="07673-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="07673-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>
