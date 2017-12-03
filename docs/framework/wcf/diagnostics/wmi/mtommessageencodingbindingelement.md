---
title: MtomMessageEncodingBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4a9c6c3d-e561-4b2d-a693-7e84bdd3534a
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 867b4a2b84a28dff4e3b9e4fc9d3c52065de212f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="mtommessageencodingbindingelement"></a><span data-ttu-id="b8834-102">MtomMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="b8834-102">MtomMessageEncodingBindingElement</span></span>
<span data-ttu-id="b8834-103">MtomMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="b8834-103">MtomMessageEncodingBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8834-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b8834-104">Syntax</span></span>  
  
```  
class MtomMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  string Encoding;  
  sint32 MaxReadPoolSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="b8834-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="b8834-105">Methods</span></span>  
 <span data-ttu-id="b8834-106">A classe MtomMessageEncodingBindingElement não define nenhum método.</span><span class="sxs-lookup"><span data-stu-id="b8834-106">The MtomMessageEncodingBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="b8834-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="b8834-107">Properties</span></span>  
 <span data-ttu-id="b8834-108">A classe MtomMessageEncodingBindingElement tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="b8834-108">The MtomMessageEncodingBindingElement class has the following properties:</span></span>  
  
### <a name="encoding"></a><span data-ttu-id="b8834-109">Codificando</span><span class="sxs-lookup"><span data-stu-id="b8834-109">Encoding</span></span>  
 <span data-ttu-id="b8834-110">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="b8834-110">Data type: string</span></span>  
  
 <span data-ttu-id="b8834-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="b8834-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b8834-112">O conjunto de caracteres codificação a ser usada para emitir mensagens na associação.</span><span class="sxs-lookup"><span data-stu-id="b8834-112">The character set encoding to be used for emitting messages on the binding.</span></span>  
  
### <a name="maxreadpoolsize"></a><span data-ttu-id="b8834-113">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="b8834-113">MaxReadPoolSize</span></span>  
 <span data-ttu-id="b8834-114">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="b8834-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="b8834-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="b8834-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b8834-116">Um inteiro que define quantas mensagens pode ser lidas simultaneamente sem alocar novos leitores.</span><span class="sxs-lookup"><span data-stu-id="b8834-116">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span>  
  
### <a name="maxwritepoolsize"></a><span data-ttu-id="b8834-117">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="b8834-117">MaxWritePoolSize</span></span>  
 <span data-ttu-id="b8834-118">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="b8834-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="b8834-119">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="b8834-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b8834-120">Um inteiro que define quantas mensagens pode ser enviado simultaneamente sem alocar novos escritores.</span><span class="sxs-lookup"><span data-stu-id="b8834-120">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span>  
  
### <a name="readerquotas"></a><span data-ttu-id="b8834-121">ReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="b8834-121">ReaderQuotas</span></span>  
 <span data-ttu-id="b8834-122">Tipo de dados: XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="b8834-122">Data type: XmlDictionaryReaderQuotas</span></span>  
  
 <span data-ttu-id="b8834-123">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="b8834-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b8834-124">As cotas dos leitores.</span><span class="sxs-lookup"><span data-stu-id="b8834-124">The quotas of the readers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b8834-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b8834-125">Requirements</span></span>  
  
|<span data-ttu-id="b8834-126">MOF</span><span class="sxs-lookup"><span data-stu-id="b8834-126">MOF</span></span>|<span data-ttu-id="b8834-127">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="b8834-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="b8834-128">Namespace</span><span class="sxs-lookup"><span data-stu-id="b8834-128">Namespace</span></span>|<span data-ttu-id="b8834-129">Definido em root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="b8834-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b8834-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b8834-130">See Also</span></span>  
 <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>
