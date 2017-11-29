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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6e1eccbaae35a16fe4fb133296698d347c190e94
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="textmessageencodingbindingelement"></a><span data-ttu-id="c4501-102">TextMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="c4501-102">TextMessageEncodingBindingElement</span></span>
<span data-ttu-id="c4501-103">TextMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="c4501-103">TextMessageEncodingBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4501-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c4501-104">Syntax</span></span>  
  
```  
class TextMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  string Encoding;  
  sint32 MaxReadPoolSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="c4501-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="c4501-105">Methods</span></span>  
 <span data-ttu-id="c4501-106">A classe TextMessageEncodingBindingElement não define nenhum método.</span><span class="sxs-lookup"><span data-stu-id="c4501-106">The TextMessageEncodingBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="c4501-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="c4501-107">Properties</span></span>  
 <span data-ttu-id="c4501-108">A classe TextMessageEncodingBindingElement tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="c4501-108">The TextMessageEncodingBindingElement class has the following properties:</span></span>  
  
### <a name="encoding"></a><span data-ttu-id="c4501-109">Codificando</span><span class="sxs-lookup"><span data-stu-id="c4501-109">Encoding</span></span>  
 <span data-ttu-id="c4501-110">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="c4501-110">Data type: string</span></span>  
  
 <span data-ttu-id="c4501-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="c4501-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c4501-112">O conjunto de caracteres codificação a ser usada para emitir mensagens na associação.</span><span class="sxs-lookup"><span data-stu-id="c4501-112">The character set encoding to be used for emitting messages on the binding.</span></span>  
  
### <a name="maxreadpoolsize"></a><span data-ttu-id="c4501-113">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="c4501-113">MaxReadPoolSize</span></span>  
 <span data-ttu-id="c4501-114">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="c4501-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="c4501-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="c4501-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c4501-116">Um inteiro que define quantas mensagens pode ser lidas simultaneamente sem alocar novos leitores.</span><span class="sxs-lookup"><span data-stu-id="c4501-116">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span>  
  
### <a name="maxwritepoolsize"></a><span data-ttu-id="c4501-117">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="c4501-117">MaxWritePoolSize</span></span>  
 <span data-ttu-id="c4501-118">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="c4501-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="c4501-119">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="c4501-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c4501-120">Um inteiro que define quantas mensagens pode ser enviado simultaneamente sem alocar novos escritores.</span><span class="sxs-lookup"><span data-stu-id="c4501-120">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span>  
  
### <a name="readerquotas"></a><span data-ttu-id="c4501-121">ReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="c4501-121">ReaderQuotas</span></span>  
 <span data-ttu-id="c4501-122">Tipo de dados: XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="c4501-122">Data type: XmlDictionaryReaderQuotas</span></span>  
  
 <span data-ttu-id="c4501-123">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="c4501-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c4501-124">As cotas dos leitores.</span><span class="sxs-lookup"><span data-stu-id="c4501-124">The quotas of the readers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4501-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c4501-125">Requirements</span></span>  
  
|<span data-ttu-id="c4501-126">MOF</span><span class="sxs-lookup"><span data-stu-id="c4501-126">MOF</span></span>|<span data-ttu-id="c4501-127">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="c4501-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="c4501-128">Namespace</span><span class="sxs-lookup"><span data-stu-id="c4501-128">Namespace</span></span>|<span data-ttu-id="c4501-129">Definido em root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="c4501-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c4501-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c4501-130">See Also</span></span>  
 <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>
