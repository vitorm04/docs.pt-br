---
title: TransportBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 54ecfbee-53c0-410c-a7fa-a98f2e40c545
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 062b45eb5d627903142ca1a5fd4db6df0855384b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="transportbindingelement"></a><span data-ttu-id="6ec1a-102">TransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="6ec1a-102">TransportBindingElement</span></span>
<span data-ttu-id="6ec1a-103">TransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="6ec1a-103">TransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ec1a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6ec1a-104">Syntax</span></span>  
  
```  
class TransportBindingElement : BindingElement  
{  
  boolean ManualAddressing;  
  sint64 MaxBufferPoolSize;  
  sint64 MaxReceivedMessageSize;  
  string Scheme;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="6ec1a-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="6ec1a-105">Methods</span></span>  
 <span data-ttu-id="6ec1a-106">A classe de TransportBindingElement não define nenhum método.</span><span class="sxs-lookup"><span data-stu-id="6ec1a-106">The TransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="6ec1a-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="6ec1a-107">Properties</span></span>  
 <span data-ttu-id="6ec1a-108">A classe de TransportBindingElement tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="6ec1a-108">The TransportBindingElement class has the following properties:</span></span>  
  
### <a name="manualaddressing"></a><span data-ttu-id="6ec1a-109">manualAddressing</span><span class="sxs-lookup"><span data-stu-id="6ec1a-109">ManualAddressing</span></span>  
 <span data-ttu-id="6ec1a-110">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="6ec1a-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="6ec1a-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="6ec1a-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6ec1a-112">Um valor booleano que especifica se o usuário deseja assumir o controle do endereçamento da mensagem.</span><span class="sxs-lookup"><span data-stu-id="6ec1a-112">A boolean value that specifies whether the user wants to take control of message addressing.</span></span>  
  
### <a name="maxbufferpoolsize"></a><span data-ttu-id="6ec1a-113">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="6ec1a-113">MaxBufferPoolSize</span></span>  
 <span data-ttu-id="6ec1a-114">Tipo de dados: sint64</span><span class="sxs-lookup"><span data-stu-id="6ec1a-114">Data type: sint64</span></span>  
  
 <span data-ttu-id="6ec1a-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="6ec1a-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6ec1a-116">O tamanho do pool de buffer máximo para a associação.</span><span class="sxs-lookup"><span data-stu-id="6ec1a-116">The maximum buffer pool size for the binding.</span></span>  
  
### <a name="maxreceivedmessagesize"></a><span data-ttu-id="6ec1a-117">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="6ec1a-117">MaxReceivedMessageSize</span></span>  
 <span data-ttu-id="6ec1a-118">Tipo de dados: sint64</span><span class="sxs-lookup"><span data-stu-id="6ec1a-118">Data type: sint64</span></span>  
  
 <span data-ttu-id="6ec1a-119">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="6ec1a-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6ec1a-120">O tamanho máximo para uma mensagem que é processada por essa associação.</span><span class="sxs-lookup"><span data-stu-id="6ec1a-120">The maximum size for a message that is processed by this binding.</span></span>  
  
### <a name="scheme"></a><span data-ttu-id="6ec1a-121">Esquema</span><span class="sxs-lookup"><span data-stu-id="6ec1a-121">Scheme</span></span>  
 <span data-ttu-id="6ec1a-122">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="6ec1a-122">Data type: string</span></span>  
  
 <span data-ttu-id="6ec1a-123">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="6ec1a-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6ec1a-124">O esquema URI para o transporte.</span><span class="sxs-lookup"><span data-stu-id="6ec1a-124">The URI scheme for the transport.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6ec1a-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6ec1a-125">Requirements</span></span>  
  
|<span data-ttu-id="6ec1a-126">MOF</span><span class="sxs-lookup"><span data-stu-id="6ec1a-126">MOF</span></span>|<span data-ttu-id="6ec1a-127">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="6ec1a-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="6ec1a-128">Namespace</span><span class="sxs-lookup"><span data-stu-id="6ec1a-128">Namespace</span></span>|<span data-ttu-id="6ec1a-129">Definido em root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="6ec1a-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6ec1a-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6ec1a-130">See Also</span></span>  
 <xref:System.ServiceModel.Channels.TransportBindingElement>
