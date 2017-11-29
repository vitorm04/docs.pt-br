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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 09d43ed76ef70f4478aa1029c254a7b1686a8d08
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="binarymessageencodingbindingelement"></a><span data-ttu-id="d7b7c-102">BinaryMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="d7b7c-102">BinaryMessageEncodingBindingElement</span></span>
<span data-ttu-id="d7b7c-103">BinaryMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="d7b7c-103">BinaryMessageEncodingBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7b7c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d7b7c-104">Syntax</span></span>  
  
```  
class BinaryMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  sint32 MaxReadPoolSize;  
  sint32 MaxSessionSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="d7b7c-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="d7b7c-105">Methods</span></span>  
 <span data-ttu-id="d7b7c-106">A classe BinaryMessageEncodingBindingElement não define nenhum método.</span><span class="sxs-lookup"><span data-stu-id="d7b7c-106">The BinaryMessageEncodingBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="d7b7c-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="d7b7c-107">Properties</span></span>  
 <span data-ttu-id="d7b7c-108">A classe BinaryMessageEncodingBindingElement tem as seguintes propriedades.</span><span class="sxs-lookup"><span data-stu-id="d7b7c-108">The BinaryMessageEncodingBindingElement class has the following properties.</span></span>  
  
## <a name="maxreadpoolsize"></a><span data-ttu-id="d7b7c-109">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="d7b7c-109">MaxReadPoolSize</span></span>  
 <span data-ttu-id="d7b7c-110">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="d7b7c-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="d7b7c-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="d7b7c-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d7b7c-112">Um inteiro que define quantas mensagens pode ser lidas simultaneamente sem alocar novos leitores.</span><span class="sxs-lookup"><span data-stu-id="d7b7c-112">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span>  
  
## <a name="maxsessionsize"></a><span data-ttu-id="d7b7c-113">maxSessionSize</span><span class="sxs-lookup"><span data-stu-id="d7b7c-113">MaxSessionSize</span></span>  
 <span data-ttu-id="d7b7c-114">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="d7b7c-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="d7b7c-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="d7b7c-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d7b7c-116">Um valor que especifica o tamanho, em bytes, do buffer usado para codificação.</span><span class="sxs-lookup"><span data-stu-id="d7b7c-116">A value that specifies the size, in bytes, of the buffer used for encoding.</span></span>  
  
## <a name="maxwritepoolsize"></a><span data-ttu-id="d7b7c-117">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="d7b7c-117">MaxWritePoolSize</span></span>  
 <span data-ttu-id="d7b7c-118">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="d7b7c-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="d7b7c-119">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="d7b7c-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d7b7c-120">Um inteiro que define quantas mensagens pode ser enviado simultaneamente sem alocar novos escritores.</span><span class="sxs-lookup"><span data-stu-id="d7b7c-120">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span>  
  
## <a name="readerquotas"></a><span data-ttu-id="d7b7c-121">ReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="d7b7c-121">ReaderQuotas</span></span>  
 <span data-ttu-id="d7b7c-122">Tipo de dados: XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="d7b7c-122">Data type: XmlDictionaryReaderQuotas</span></span>  
  
 <span data-ttu-id="d7b7c-123">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="d7b7c-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d7b7c-124">As cotas dos leitores.</span><span class="sxs-lookup"><span data-stu-id="d7b7c-124">The quotas of the readers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d7b7c-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d7b7c-125">Requirements</span></span>  
  
|<span data-ttu-id="d7b7c-126">MOF</span><span class="sxs-lookup"><span data-stu-id="d7b7c-126">MOF</span></span>|<span data-ttu-id="d7b7c-127">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="d7b7c-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="d7b7c-128">Namespace</span><span class="sxs-lookup"><span data-stu-id="d7b7c-128">Namespace</span></span>|<span data-ttu-id="d7b7c-129">Definido em root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="d7b7c-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d7b7c-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d7b7c-130">See Also</span></span>  
 <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>
