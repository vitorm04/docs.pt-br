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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c5fd2858688634ee48a67b930755fc3ceebbebf8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="mtommessageencodingbindingelement"></a><span data-ttu-id="ac041-102">MtomMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="ac041-102">MtomMessageEncodingBindingElement</span></span>
<span data-ttu-id="ac041-103">MtomMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="ac041-103">MtomMessageEncodingBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac041-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ac041-104">Syntax</span></span>  
  
```  
class MtomMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  string Encoding;  
  sint32 MaxReadPoolSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="ac041-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="ac041-105">Methods</span></span>  
 <span data-ttu-id="ac041-106">A classe MtomMessageEncodingBindingElement não define nenhum método.</span><span class="sxs-lookup"><span data-stu-id="ac041-106">The MtomMessageEncodingBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="ac041-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="ac041-107">Properties</span></span>  
 <span data-ttu-id="ac041-108">A classe MtomMessageEncodingBindingElement tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="ac041-108">The MtomMessageEncodingBindingElement class has the following properties:</span></span>  
  
### <a name="encoding"></a><span data-ttu-id="ac041-109">Codificando</span><span class="sxs-lookup"><span data-stu-id="ac041-109">Encoding</span></span>  
 <span data-ttu-id="ac041-110">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="ac041-110">Data type: string</span></span>  
  
 <span data-ttu-id="ac041-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="ac041-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ac041-112">O conjunto de caracteres codificação a ser usada para emitir mensagens na associação.</span><span class="sxs-lookup"><span data-stu-id="ac041-112">The character set encoding to be used for emitting messages on the binding.</span></span>  
  
### <a name="maxreadpoolsize"></a><span data-ttu-id="ac041-113">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="ac041-113">MaxReadPoolSize</span></span>  
 <span data-ttu-id="ac041-114">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="ac041-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="ac041-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="ac041-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ac041-116">Um inteiro que define quantas mensagens pode ser lidas simultaneamente sem alocar novos leitores.</span><span class="sxs-lookup"><span data-stu-id="ac041-116">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span>  
  
### <a name="maxwritepoolsize"></a><span data-ttu-id="ac041-117">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="ac041-117">MaxWritePoolSize</span></span>  
 <span data-ttu-id="ac041-118">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="ac041-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="ac041-119">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="ac041-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ac041-120">Um inteiro que define quantas mensagens pode ser enviado simultaneamente sem alocar novos escritores.</span><span class="sxs-lookup"><span data-stu-id="ac041-120">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span>  
  
### <a name="readerquotas"></a><span data-ttu-id="ac041-121">ReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="ac041-121">ReaderQuotas</span></span>  
 <span data-ttu-id="ac041-122">Tipo de dados: XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="ac041-122">Data type: XmlDictionaryReaderQuotas</span></span>  
  
 <span data-ttu-id="ac041-123">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="ac041-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ac041-124">As cotas dos leitores.</span><span class="sxs-lookup"><span data-stu-id="ac041-124">The quotas of the readers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ac041-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ac041-125">Requirements</span></span>  
  
|<span data-ttu-id="ac041-126">MOF</span><span class="sxs-lookup"><span data-stu-id="ac041-126">MOF</span></span>|<span data-ttu-id="ac041-127">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="ac041-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="ac041-128">Namespace</span><span class="sxs-lookup"><span data-stu-id="ac041-128">Namespace</span></span>|<span data-ttu-id="ac041-129">Definido em root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="ac041-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ac041-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ac041-130">See Also</span></span>  
 <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>
