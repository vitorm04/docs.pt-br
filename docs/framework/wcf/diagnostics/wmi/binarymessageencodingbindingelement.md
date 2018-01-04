---
title: BinaryMessageEncodingBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e2bb3cdd-3bbd-4bb5-85fe-570457500a66
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: adac65808853ec75e37245c8c9fa031a533c22a6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="binarymessageencodingbindingelement"></a><span data-ttu-id="4624a-102">BinaryMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="4624a-102">BinaryMessageEncodingBindingElement</span></span>
<span data-ttu-id="4624a-103">BinaryMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="4624a-103">BinaryMessageEncodingBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4624a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4624a-104">Syntax</span></span>  
  
```  
class BinaryMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  sint32 MaxReadPoolSize;  
  sint32 MaxSessionSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="4624a-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="4624a-105">Methods</span></span>  
 <span data-ttu-id="4624a-106">A classe BinaryMessageEncodingBindingElement não define nenhum método.</span><span class="sxs-lookup"><span data-stu-id="4624a-106">The BinaryMessageEncodingBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="4624a-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="4624a-107">Properties</span></span>  
 <span data-ttu-id="4624a-108">A classe BinaryMessageEncodingBindingElement tem as seguintes propriedades.</span><span class="sxs-lookup"><span data-stu-id="4624a-108">The BinaryMessageEncodingBindingElement class has the following properties.</span></span>  
  
## <a name="maxreadpoolsize"></a><span data-ttu-id="4624a-109">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="4624a-109">MaxReadPoolSize</span></span>  
 <span data-ttu-id="4624a-110">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="4624a-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="4624a-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="4624a-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4624a-112">Um inteiro que define quantas mensagens pode ser lidas simultaneamente sem alocar novos leitores.</span><span class="sxs-lookup"><span data-stu-id="4624a-112">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span>  
  
## <a name="maxsessionsize"></a><span data-ttu-id="4624a-113">maxSessionSize</span><span class="sxs-lookup"><span data-stu-id="4624a-113">MaxSessionSize</span></span>  
 <span data-ttu-id="4624a-114">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="4624a-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="4624a-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="4624a-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4624a-116">Um valor que especifica o tamanho, em bytes, do buffer usado para codificação.</span><span class="sxs-lookup"><span data-stu-id="4624a-116">A value that specifies the size, in bytes, of the buffer used for encoding.</span></span>  
  
## <a name="maxwritepoolsize"></a><span data-ttu-id="4624a-117">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="4624a-117">MaxWritePoolSize</span></span>  
 <span data-ttu-id="4624a-118">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="4624a-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="4624a-119">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="4624a-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4624a-120">Um inteiro que define quantas mensagens pode ser enviado simultaneamente sem alocar novos escritores.</span><span class="sxs-lookup"><span data-stu-id="4624a-120">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span>  
  
## <a name="readerquotas"></a><span data-ttu-id="4624a-121">ReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="4624a-121">ReaderQuotas</span></span>  
 <span data-ttu-id="4624a-122">Tipo de dados: XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="4624a-122">Data type: XmlDictionaryReaderQuotas</span></span>  
  
 <span data-ttu-id="4624a-123">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="4624a-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4624a-124">As cotas dos leitores.</span><span class="sxs-lookup"><span data-stu-id="4624a-124">The quotas of the readers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4624a-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4624a-125">Requirements</span></span>  
  
|<span data-ttu-id="4624a-126">MOF</span><span class="sxs-lookup"><span data-stu-id="4624a-126">MOF</span></span>|<span data-ttu-id="4624a-127">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="4624a-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="4624a-128">Namespace</span><span class="sxs-lookup"><span data-stu-id="4624a-128">Namespace</span></span>|<span data-ttu-id="4624a-129">Definido em root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="4624a-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4624a-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4624a-130">See Also</span></span>  
 <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>
