---
title: MsmqTransportBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1c89f073-9ed3-4025-a8c5-13535a0f526b
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c0c2c5d54050216c91a318a407341c4ffb9cb687
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="msmqtransportbindingelement"></a><span data-ttu-id="c5984-102">MsmqTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="c5984-102">MsmqTransportBindingElement</span></span>
<span data-ttu-id="c5984-103">MsmqTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="c5984-103">MsmqTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5984-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c5984-104">Syntax</span></span>  
  
```  
class MsmqTransportBindingElement : MsmqBindingElementBase  
{  
  sint32 MaxPoolSize;  
  string QueueTransferProtocol;  
  boolean UseActiveDirectory;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="c5984-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="c5984-105">Methods</span></span>  
 <span data-ttu-id="c5984-106">A classe MsmqTransportBindingElement não define nenhum método.</span><span class="sxs-lookup"><span data-stu-id="c5984-106">The MsmqTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="c5984-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="c5984-107">Properties</span></span>  
 <span data-ttu-id="c5984-108">A classe MsmqTransportBindingElement tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="c5984-108">The MsmqTransportBindingElement class has the following properties:</span></span>  
  
### <a name="maxpoolsize"></a><span data-ttu-id="c5984-109">MaxPoolSize</span><span class="sxs-lookup"><span data-stu-id="c5984-109">MaxPoolSize</span></span>  
 <span data-ttu-id="c5984-110">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="c5984-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="c5984-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="c5984-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c5984-112">O tamanho máximo do pool que contém objetos de mensagem MSMQ internos.</span><span class="sxs-lookup"><span data-stu-id="c5984-112">The maximum size of the pool that contains internal MSMQ message objects.</span></span>  
  
### <a name="queuetransferprotocol"></a><span data-ttu-id="c5984-113">QueueTransferProtocol</span><span class="sxs-lookup"><span data-stu-id="c5984-113">QueueTransferProtocol</span></span>  
 <span data-ttu-id="c5984-114">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="c5984-114">Data type: string</span></span>  
  
 <span data-ttu-id="c5984-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="c5984-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c5984-116">Um valor de enumeração que indica o transporte de canal de comunicação em fila que esta associação usa.</span><span class="sxs-lookup"><span data-stu-id="c5984-116">An enumeration value that indicates the queued communication channel transport that this binding uses.</span></span>  
  
### <a name="useactivedirectory"></a><span data-ttu-id="c5984-117">Propriedade UseActiveDirectory</span><span class="sxs-lookup"><span data-stu-id="c5984-117">UseActiveDirectory</span></span>  
 <span data-ttu-id="c5984-118">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="c5984-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="c5984-119">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="c5984-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c5984-120">Retorna um valor booliano que indica se os endereços de fila devem ser convertidos usando o Active Directory.</span><span class="sxs-lookup"><span data-stu-id="c5984-120">Returns a Boolean value that indicates whether queue addresses should be converted using Active Directory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c5984-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c5984-121">Requirements</span></span>  
  
|<span data-ttu-id="c5984-122">MOF</span><span class="sxs-lookup"><span data-stu-id="c5984-122">MOF</span></span>|<span data-ttu-id="c5984-123">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="c5984-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="c5984-124">Namespace</span><span class="sxs-lookup"><span data-stu-id="c5984-124">Namespace</span></span>|<span data-ttu-id="c5984-125">Definido em root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="c5984-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c5984-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c5984-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>
