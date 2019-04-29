---
title: TransportBindingElement
ms.date: 03/30/2017
ms.assetid: 54ecfbee-53c0-410c-a7fa-a98f2e40c545
ms.openlocfilehash: bdb5ca7400a41dd724c2ad7fc76695a82874ded6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61641613"
---
# <a name="transportbindingelement"></a><span data-ttu-id="277ca-102">TransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="277ca-102">TransportBindingElement</span></span>
<span data-ttu-id="277ca-103">TransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="277ca-103">TransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="277ca-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="277ca-104">Syntax</span></span>  
  
```csharp
class TransportBindingElement : BindingElement  
{  
  boolean ManualAddressing;  
  sint64 MaxBufferPoolSize;  
  sint64 MaxReceivedMessageSize;  
  string Scheme;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="277ca-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="277ca-105">Methods</span></span>  
 <span data-ttu-id="277ca-106">A classe de TransportBindingElement não define quaisquer métodos.</span><span class="sxs-lookup"><span data-stu-id="277ca-106">The TransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="277ca-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="277ca-107">Properties</span></span>  
 <span data-ttu-id="277ca-108">A classe de TransportBindingElement tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="277ca-108">The TransportBindingElement class has the following properties:</span></span>  
  
### <a name="manualaddressing"></a><span data-ttu-id="277ca-109">ManualAddressing</span><span class="sxs-lookup"><span data-stu-id="277ca-109">ManualAddressing</span></span>  
 <span data-ttu-id="277ca-110">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="277ca-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="277ca-111">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="277ca-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="277ca-112">Um valor booliano que especifica se o usuário deseja assumir o controle do endereçamento de mensagem.</span><span class="sxs-lookup"><span data-stu-id="277ca-112">A boolean value that specifies whether the user wants to take control of message addressing.</span></span>  
  
### <a name="maxbufferpoolsize"></a><span data-ttu-id="277ca-113">MaxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="277ca-113">MaxBufferPoolSize</span></span>  
 <span data-ttu-id="277ca-114">Tipo de dados: sint64</span><span class="sxs-lookup"><span data-stu-id="277ca-114">Data type: sint64</span></span>  
  
 <span data-ttu-id="277ca-115">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="277ca-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="277ca-116">O tamanho máximo do buffer do pool para a associação.</span><span class="sxs-lookup"><span data-stu-id="277ca-116">The maximum buffer pool size for the binding.</span></span>  
  
### <a name="maxreceivedmessagesize"></a><span data-ttu-id="277ca-117">MaxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="277ca-117">MaxReceivedMessageSize</span></span>  
 <span data-ttu-id="277ca-118">Tipo de dados: sint64</span><span class="sxs-lookup"><span data-stu-id="277ca-118">Data type: sint64</span></span>  
  
 <span data-ttu-id="277ca-119">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="277ca-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="277ca-120">O tamanho máximo para uma mensagem que é processado por essa associação.</span><span class="sxs-lookup"><span data-stu-id="277ca-120">The maximum size for a message that is processed by this binding.</span></span>  
  
### <a name="scheme"></a><span data-ttu-id="277ca-121">Esquema</span><span class="sxs-lookup"><span data-stu-id="277ca-121">Scheme</span></span>  
 <span data-ttu-id="277ca-122">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="277ca-122">Data type: string</span></span>  
  
 <span data-ttu-id="277ca-123">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="277ca-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="277ca-124">O esquema URI para o transporte.</span><span class="sxs-lookup"><span data-stu-id="277ca-124">The URI scheme for the transport.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="277ca-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="277ca-125">Requirements</span></span>  
  
|<span data-ttu-id="277ca-126">MOF</span><span class="sxs-lookup"><span data-stu-id="277ca-126">MOF</span></span>|<span data-ttu-id="277ca-127">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="277ca-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="277ca-128">Namespace</span><span class="sxs-lookup"><span data-stu-id="277ca-128">Namespace</span></span>|<span data-ttu-id="277ca-129">Definido no root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="277ca-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="277ca-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="277ca-130">See also</span></span>

- <xref:System.ServiceModel.Channels.TransportBindingElement>
