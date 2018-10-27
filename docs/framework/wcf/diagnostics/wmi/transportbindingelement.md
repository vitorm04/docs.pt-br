---
title: TransportBindingElement
ms.date: 03/30/2017
ms.assetid: 54ecfbee-53c0-410c-a7fa-a98f2e40c545
ms.openlocfilehash: 79d8b1f4a5127ca36eb57954cff6ee6a97e55e41
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50182652"
---
# <a name="transportbindingelement"></a><span data-ttu-id="b3171-102">TransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="b3171-102">TransportBindingElement</span></span>
<span data-ttu-id="b3171-103">TransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="b3171-103">TransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3171-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b3171-104">Syntax</span></span>  
  
```csharp
class TransportBindingElement : BindingElement  
{  
  boolean ManualAddressing;  
  sint64 MaxBufferPoolSize;  
  sint64 MaxReceivedMessageSize;  
  string Scheme;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="b3171-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="b3171-105">Methods</span></span>  
 <span data-ttu-id="b3171-106">A classe de TransportBindingElement não define quaisquer métodos.</span><span class="sxs-lookup"><span data-stu-id="b3171-106">The TransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="b3171-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="b3171-107">Properties</span></span>  
 <span data-ttu-id="b3171-108">A classe de TransportBindingElement tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="b3171-108">The TransportBindingElement class has the following properties:</span></span>  
  
### <a name="manualaddressing"></a><span data-ttu-id="b3171-109">manualAddressing</span><span class="sxs-lookup"><span data-stu-id="b3171-109">ManualAddressing</span></span>  
 <span data-ttu-id="b3171-110">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="b3171-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="b3171-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="b3171-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b3171-112">Um valor booliano que especifica se o usuário deseja assumir o controle do endereçamento de mensagem.</span><span class="sxs-lookup"><span data-stu-id="b3171-112">A boolean value that specifies whether the user wants to take control of message addressing.</span></span>  
  
### <a name="maxbufferpoolsize"></a><span data-ttu-id="b3171-113">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="b3171-113">MaxBufferPoolSize</span></span>  
 <span data-ttu-id="b3171-114">Tipo de dados: sint64</span><span class="sxs-lookup"><span data-stu-id="b3171-114">Data type: sint64</span></span>  
  
 <span data-ttu-id="b3171-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="b3171-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b3171-116">O tamanho máximo do buffer do pool para a associação.</span><span class="sxs-lookup"><span data-stu-id="b3171-116">The maximum buffer pool size for the binding.</span></span>  
  
### <a name="maxreceivedmessagesize"></a><span data-ttu-id="b3171-117">MaxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="b3171-117">MaxReceivedMessageSize</span></span>  
 <span data-ttu-id="b3171-118">Tipo de dados: sint64</span><span class="sxs-lookup"><span data-stu-id="b3171-118">Data type: sint64</span></span>  
  
 <span data-ttu-id="b3171-119">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="b3171-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b3171-120">O tamanho máximo para uma mensagem que é processado por essa associação.</span><span class="sxs-lookup"><span data-stu-id="b3171-120">The maximum size for a message that is processed by this binding.</span></span>  
  
### <a name="scheme"></a><span data-ttu-id="b3171-121">Esquema</span><span class="sxs-lookup"><span data-stu-id="b3171-121">Scheme</span></span>  
 <span data-ttu-id="b3171-122">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="b3171-122">Data type: string</span></span>  
  
 <span data-ttu-id="b3171-123">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="b3171-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b3171-124">O esquema URI para o transporte.</span><span class="sxs-lookup"><span data-stu-id="b3171-124">The URI scheme for the transport.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b3171-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b3171-125">Requirements</span></span>  
  
|<span data-ttu-id="b3171-126">MOF</span><span class="sxs-lookup"><span data-stu-id="b3171-126">MOF</span></span>|<span data-ttu-id="b3171-127">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="b3171-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="b3171-128">Namespace</span><span class="sxs-lookup"><span data-stu-id="b3171-128">Namespace</span></span>|<span data-ttu-id="b3171-129">Definido no root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="b3171-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b3171-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b3171-130">See Also</span></span>  
 <xref:System.ServiceModel.Channels.TransportBindingElement>
