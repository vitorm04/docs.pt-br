---
title: TextMessageEncodingBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 885e2d7a-3436-4093-bc5f-0a404c62acdc
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3f1e026296745f6fc40171866c81f91818789e01
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="textmessageencodingbindingelement"></a><span data-ttu-id="4bdc4-102">TextMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="4bdc4-102">TextMessageEncodingBindingElement</span></span>
<span data-ttu-id="4bdc4-103">TextMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="4bdc4-103">TextMessageEncodingBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4bdc4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4bdc4-104">Syntax</span></span>  
  
```  
class TextMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  string Encoding;  
  sint32 MaxReadPoolSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="4bdc4-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="4bdc4-105">Methods</span></span>  
 <span data-ttu-id="4bdc4-106">A classe TextMessageEncodingBindingElement não define nenhum método.</span><span class="sxs-lookup"><span data-stu-id="4bdc4-106">The TextMessageEncodingBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="4bdc4-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="4bdc4-107">Properties</span></span>  
 <span data-ttu-id="4bdc4-108">A classe TextMessageEncodingBindingElement tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="4bdc4-108">The TextMessageEncodingBindingElement class has the following properties:</span></span>  
  
### <a name="encoding"></a><span data-ttu-id="4bdc4-109">Codificando</span><span class="sxs-lookup"><span data-stu-id="4bdc4-109">Encoding</span></span>  
 <span data-ttu-id="4bdc4-110">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="4bdc4-110">Data type: string</span></span>  
  
 <span data-ttu-id="4bdc4-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="4bdc4-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4bdc4-112">O conjunto de caracteres codificação a ser usada para emitir mensagens na associação.</span><span class="sxs-lookup"><span data-stu-id="4bdc4-112">The character set encoding to be used for emitting messages on the binding.</span></span>  
  
### <a name="maxreadpoolsize"></a><span data-ttu-id="4bdc4-113">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="4bdc4-113">MaxReadPoolSize</span></span>  
 <span data-ttu-id="4bdc4-114">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="4bdc4-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="4bdc4-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="4bdc4-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4bdc4-116">Um inteiro que define quantas mensagens pode ser lidas simultaneamente sem alocar novos leitores.</span><span class="sxs-lookup"><span data-stu-id="4bdc4-116">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span>  
  
### <a name="maxwritepoolsize"></a><span data-ttu-id="4bdc4-117">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="4bdc4-117">MaxWritePoolSize</span></span>  
 <span data-ttu-id="4bdc4-118">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="4bdc4-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="4bdc4-119">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="4bdc4-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4bdc4-120">Um inteiro que define quantas mensagens pode ser enviado simultaneamente sem alocar novos escritores.</span><span class="sxs-lookup"><span data-stu-id="4bdc4-120">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span>  
  
### <a name="readerquotas"></a><span data-ttu-id="4bdc4-121">ReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="4bdc4-121">ReaderQuotas</span></span>  
 <span data-ttu-id="4bdc4-122">Tipo de dados: XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="4bdc4-122">Data type: XmlDictionaryReaderQuotas</span></span>  
  
 <span data-ttu-id="4bdc4-123">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="4bdc4-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4bdc4-124">As cotas dos leitores.</span><span class="sxs-lookup"><span data-stu-id="4bdc4-124">The quotas of the readers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4bdc4-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4bdc4-125">Requirements</span></span>  
  
|<span data-ttu-id="4bdc4-126">MOF</span><span class="sxs-lookup"><span data-stu-id="4bdc4-126">MOF</span></span>|<span data-ttu-id="4bdc4-127">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="4bdc4-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="4bdc4-128">Namespace</span><span class="sxs-lookup"><span data-stu-id="4bdc4-128">Namespace</span></span>|<span data-ttu-id="4bdc4-129">Definido em root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="4bdc4-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4bdc4-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4bdc4-130">See Also</span></span>  
 <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>
