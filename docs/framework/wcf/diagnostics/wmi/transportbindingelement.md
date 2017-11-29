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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c130093b9600c324e7179febce6857341b8a7d3c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="transportbindingelement"></a><span data-ttu-id="70098-102">TransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="70098-102">TransportBindingElement</span></span>
<span data-ttu-id="70098-103">TransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="70098-103">TransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70098-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="70098-104">Syntax</span></span>  
  
```  
class TransportBindingElement : BindingElement  
{  
  boolean ManualAddressing;  
  sint64 MaxBufferPoolSize;  
  sint64 MaxReceivedMessageSize;  
  string Scheme;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="70098-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="70098-105">Methods</span></span>  
 <span data-ttu-id="70098-106">A classe de TransportBindingElement não define nenhum método.</span><span class="sxs-lookup"><span data-stu-id="70098-106">The TransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="70098-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="70098-107">Properties</span></span>  
 <span data-ttu-id="70098-108">A classe de TransportBindingElement tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="70098-108">The TransportBindingElement class has the following properties:</span></span>  
  
### <a name="manualaddressing"></a><span data-ttu-id="70098-109">manualAddressing</span><span class="sxs-lookup"><span data-stu-id="70098-109">ManualAddressing</span></span>  
 <span data-ttu-id="70098-110">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="70098-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="70098-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="70098-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="70098-112">Um valor booleano que especifica se o usuário deseja assumir o controle do endereçamento da mensagem.</span><span class="sxs-lookup"><span data-stu-id="70098-112">A boolean value that specifies whether the user wants to take control of message addressing.</span></span>  
  
### <a name="maxbufferpoolsize"></a><span data-ttu-id="70098-113">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="70098-113">MaxBufferPoolSize</span></span>  
 <span data-ttu-id="70098-114">Tipo de dados: sint64</span><span class="sxs-lookup"><span data-stu-id="70098-114">Data type: sint64</span></span>  
  
 <span data-ttu-id="70098-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="70098-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="70098-116">O tamanho do pool de buffer máximo para a associação.</span><span class="sxs-lookup"><span data-stu-id="70098-116">The maximum buffer pool size for the binding.</span></span>  
  
### <a name="maxreceivedmessagesize"></a><span data-ttu-id="70098-117">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="70098-117">MaxReceivedMessageSize</span></span>  
 <span data-ttu-id="70098-118">Tipo de dados: sint64</span><span class="sxs-lookup"><span data-stu-id="70098-118">Data type: sint64</span></span>  
  
 <span data-ttu-id="70098-119">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="70098-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="70098-120">O tamanho máximo para uma mensagem que é processada por essa associação.</span><span class="sxs-lookup"><span data-stu-id="70098-120">The maximum size for a message that is processed by this binding.</span></span>  
  
### <a name="scheme"></a><span data-ttu-id="70098-121">Esquema</span><span class="sxs-lookup"><span data-stu-id="70098-121">Scheme</span></span>  
 <span data-ttu-id="70098-122">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="70098-122">Data type: string</span></span>  
  
 <span data-ttu-id="70098-123">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="70098-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="70098-124">O esquema URI para o transporte.</span><span class="sxs-lookup"><span data-stu-id="70098-124">The URI scheme for the transport.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="70098-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="70098-125">Requirements</span></span>  
  
|<span data-ttu-id="70098-126">MOF</span><span class="sxs-lookup"><span data-stu-id="70098-126">MOF</span></span>|<span data-ttu-id="70098-127">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="70098-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="70098-128">Namespace</span><span class="sxs-lookup"><span data-stu-id="70098-128">Namespace</span></span>|<span data-ttu-id="70098-129">Definido em root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="70098-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="70098-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="70098-130">See Also</span></span>  
 <xref:System.ServiceModel.Channels.TransportBindingElement>
