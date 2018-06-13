---
title: TransportBindingElement
ms.date: 03/30/2017
ms.assetid: 54ecfbee-53c0-410c-a7fa-a98f2e40c545
ms.openlocfilehash: dc7a29e5911a9d0a774e36f5be8c1f3cacad69b9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33486611"
---
# <a name="transportbindingelement"></a><span data-ttu-id="7398d-102">TransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="7398d-102">TransportBindingElement</span></span>
<span data-ttu-id="7398d-103">TransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="7398d-103">TransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7398d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7398d-104">Syntax</span></span>  
  
```  
class TransportBindingElement : BindingElement  
{  
  boolean ManualAddressing;  
  sint64 MaxBufferPoolSize;  
  sint64 MaxReceivedMessageSize;  
  string Scheme;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="7398d-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="7398d-105">Methods</span></span>  
 <span data-ttu-id="7398d-106">A classe de TransportBindingElement não define nenhum método.</span><span class="sxs-lookup"><span data-stu-id="7398d-106">The TransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="7398d-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="7398d-107">Properties</span></span>  
 <span data-ttu-id="7398d-108">A classe de TransportBindingElement tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="7398d-108">The TransportBindingElement class has the following properties:</span></span>  
  
### <a name="manualaddressing"></a><span data-ttu-id="7398d-109">manualAddressing</span><span class="sxs-lookup"><span data-stu-id="7398d-109">ManualAddressing</span></span>  
 <span data-ttu-id="7398d-110">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="7398d-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="7398d-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="7398d-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7398d-112">Um valor booleano que especifica se o usuário deseja assumir o controle do endereçamento da mensagem.</span><span class="sxs-lookup"><span data-stu-id="7398d-112">A boolean value that specifies whether the user wants to take control of message addressing.</span></span>  
  
### <a name="maxbufferpoolsize"></a><span data-ttu-id="7398d-113">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="7398d-113">MaxBufferPoolSize</span></span>  
 <span data-ttu-id="7398d-114">Tipo de dados: sint64</span><span class="sxs-lookup"><span data-stu-id="7398d-114">Data type: sint64</span></span>  
  
 <span data-ttu-id="7398d-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="7398d-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7398d-116">O tamanho do pool de buffer máximo para a associação.</span><span class="sxs-lookup"><span data-stu-id="7398d-116">The maximum buffer pool size for the binding.</span></span>  
  
### <a name="maxreceivedmessagesize"></a><span data-ttu-id="7398d-117">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="7398d-117">MaxReceivedMessageSize</span></span>  
 <span data-ttu-id="7398d-118">Tipo de dados: sint64</span><span class="sxs-lookup"><span data-stu-id="7398d-118">Data type: sint64</span></span>  
  
 <span data-ttu-id="7398d-119">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="7398d-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7398d-120">O tamanho máximo para uma mensagem que é processada por essa associação.</span><span class="sxs-lookup"><span data-stu-id="7398d-120">The maximum size for a message that is processed by this binding.</span></span>  
  
### <a name="scheme"></a><span data-ttu-id="7398d-121">Esquema</span><span class="sxs-lookup"><span data-stu-id="7398d-121">Scheme</span></span>  
 <span data-ttu-id="7398d-122">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="7398d-122">Data type: string</span></span>  
  
 <span data-ttu-id="7398d-123">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="7398d-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7398d-124">O esquema URI para o transporte.</span><span class="sxs-lookup"><span data-stu-id="7398d-124">The URI scheme for the transport.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7398d-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7398d-125">Requirements</span></span>  
  
|<span data-ttu-id="7398d-126">MOF</span><span class="sxs-lookup"><span data-stu-id="7398d-126">MOF</span></span>|<span data-ttu-id="7398d-127">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="7398d-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="7398d-128">Namespace</span><span class="sxs-lookup"><span data-stu-id="7398d-128">Namespace</span></span>|<span data-ttu-id="7398d-129">Definido em root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="7398d-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7398d-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7398d-130">See Also</span></span>  
 <xref:System.ServiceModel.Channels.TransportBindingElement>
