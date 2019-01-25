---
title: TransportBindingElement
ms.date: 03/30/2017
ms.assetid: 54ecfbee-53c0-410c-a7fa-a98f2e40c545
ms.openlocfilehash: 303e5523befb68c65bc50ee3933af58897929363
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54668437"
---
# <a name="transportbindingelement"></a><span data-ttu-id="600b9-102">TransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="600b9-102">TransportBindingElement</span></span>
<span data-ttu-id="600b9-103">TransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="600b9-103">TransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="600b9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="600b9-104">Syntax</span></span>  
  
```csharp
class TransportBindingElement : BindingElement  
{  
  boolean ManualAddressing;  
  sint64 MaxBufferPoolSize;  
  sint64 MaxReceivedMessageSize;  
  string Scheme;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="600b9-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="600b9-105">Methods</span></span>  
 <span data-ttu-id="600b9-106">A classe de TransportBindingElement não define quaisquer métodos.</span><span class="sxs-lookup"><span data-stu-id="600b9-106">The TransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="600b9-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="600b9-107">Properties</span></span>  
 <span data-ttu-id="600b9-108">A classe de TransportBindingElement tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="600b9-108">The TransportBindingElement class has the following properties:</span></span>  
  
### <a name="manualaddressing"></a><span data-ttu-id="600b9-109">ManualAddressing</span><span class="sxs-lookup"><span data-stu-id="600b9-109">ManualAddressing</span></span>  
 <span data-ttu-id="600b9-110">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="600b9-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="600b9-111">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="600b9-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="600b9-112">Um valor booliano que especifica se o usuário deseja assumir o controle do endereçamento de mensagem.</span><span class="sxs-lookup"><span data-stu-id="600b9-112">A boolean value that specifies whether the user wants to take control of message addressing.</span></span>  
  
### <a name="maxbufferpoolsize"></a><span data-ttu-id="600b9-113">MaxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="600b9-113">MaxBufferPoolSize</span></span>  
 <span data-ttu-id="600b9-114">Tipo de dados: sint64</span><span class="sxs-lookup"><span data-stu-id="600b9-114">Data type: sint64</span></span>  
  
 <span data-ttu-id="600b9-115">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="600b9-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="600b9-116">O tamanho máximo do buffer do pool para a associação.</span><span class="sxs-lookup"><span data-stu-id="600b9-116">The maximum buffer pool size for the binding.</span></span>  
  
### <a name="maxreceivedmessagesize"></a><span data-ttu-id="600b9-117">MaxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="600b9-117">MaxReceivedMessageSize</span></span>  
 <span data-ttu-id="600b9-118">Tipo de dados: sint64</span><span class="sxs-lookup"><span data-stu-id="600b9-118">Data type: sint64</span></span>  
  
 <span data-ttu-id="600b9-119">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="600b9-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="600b9-120">O tamanho máximo para uma mensagem que é processado por essa associação.</span><span class="sxs-lookup"><span data-stu-id="600b9-120">The maximum size for a message that is processed by this binding.</span></span>  
  
### <a name="scheme"></a><span data-ttu-id="600b9-121">Esquema</span><span class="sxs-lookup"><span data-stu-id="600b9-121">Scheme</span></span>  
 <span data-ttu-id="600b9-122">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="600b9-122">Data type: string</span></span>  
  
 <span data-ttu-id="600b9-123">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="600b9-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="600b9-124">O esquema URI para o transporte.</span><span class="sxs-lookup"><span data-stu-id="600b9-124">The URI scheme for the transport.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="600b9-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="600b9-125">Requirements</span></span>  
  
|<span data-ttu-id="600b9-126">MOF</span><span class="sxs-lookup"><span data-stu-id="600b9-126">MOF</span></span>|<span data-ttu-id="600b9-127">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="600b9-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="600b9-128">Namespace</span><span class="sxs-lookup"><span data-stu-id="600b9-128">Namespace</span></span>|<span data-ttu-id="600b9-129">Definido no root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="600b9-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="600b9-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="600b9-130">See also</span></span>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
