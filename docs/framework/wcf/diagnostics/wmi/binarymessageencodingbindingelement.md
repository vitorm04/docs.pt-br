---
title: BinaryMessageEncodingBindingElement
ms.date: 03/30/2017
ms.assetid: e2bb3cdd-3bbd-4bb5-85fe-570457500a66
ms.openlocfilehash: 03a33f01fe6b6f75e81749c96c31770009350b05
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33486557"
---
# <a name="binarymessageencodingbindingelement"></a><span data-ttu-id="17d96-102">BinaryMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="17d96-102">BinaryMessageEncodingBindingElement</span></span>
<span data-ttu-id="17d96-103">BinaryMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="17d96-103">BinaryMessageEncodingBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17d96-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="17d96-104">Syntax</span></span>  
  
```  
class BinaryMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  sint32 MaxReadPoolSize;  
  sint32 MaxSessionSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="17d96-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="17d96-105">Methods</span></span>  
 <span data-ttu-id="17d96-106">A classe BinaryMessageEncodingBindingElement não define nenhum método.</span><span class="sxs-lookup"><span data-stu-id="17d96-106">The BinaryMessageEncodingBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="17d96-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="17d96-107">Properties</span></span>  
 <span data-ttu-id="17d96-108">A classe BinaryMessageEncodingBindingElement tem as seguintes propriedades.</span><span class="sxs-lookup"><span data-stu-id="17d96-108">The BinaryMessageEncodingBindingElement class has the following properties.</span></span>  
  
## <a name="maxreadpoolsize"></a><span data-ttu-id="17d96-109">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="17d96-109">MaxReadPoolSize</span></span>  
 <span data-ttu-id="17d96-110">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="17d96-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="17d96-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="17d96-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="17d96-112">Um inteiro que define quantas mensagens pode ser lidas simultaneamente sem alocar novos leitores.</span><span class="sxs-lookup"><span data-stu-id="17d96-112">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span>  
  
## <a name="maxsessionsize"></a><span data-ttu-id="17d96-113">maxSessionSize</span><span class="sxs-lookup"><span data-stu-id="17d96-113">MaxSessionSize</span></span>  
 <span data-ttu-id="17d96-114">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="17d96-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="17d96-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="17d96-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="17d96-116">Um valor que especifica o tamanho, em bytes, do buffer usado para codificação.</span><span class="sxs-lookup"><span data-stu-id="17d96-116">A value that specifies the size, in bytes, of the buffer used for encoding.</span></span>  
  
## <a name="maxwritepoolsize"></a><span data-ttu-id="17d96-117">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="17d96-117">MaxWritePoolSize</span></span>  
 <span data-ttu-id="17d96-118">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="17d96-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="17d96-119">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="17d96-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="17d96-120">Um inteiro que define quantas mensagens pode ser enviado simultaneamente sem alocar novos escritores.</span><span class="sxs-lookup"><span data-stu-id="17d96-120">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span>  
  
## <a name="readerquotas"></a><span data-ttu-id="17d96-121">ReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="17d96-121">ReaderQuotas</span></span>  
 <span data-ttu-id="17d96-122">Tipo de dados: XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="17d96-122">Data type: XmlDictionaryReaderQuotas</span></span>  
  
 <span data-ttu-id="17d96-123">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="17d96-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="17d96-124">As cotas dos leitores.</span><span class="sxs-lookup"><span data-stu-id="17d96-124">The quotas of the readers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="17d96-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="17d96-125">Requirements</span></span>  
  
|<span data-ttu-id="17d96-126">MOF</span><span class="sxs-lookup"><span data-stu-id="17d96-126">MOF</span></span>|<span data-ttu-id="17d96-127">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="17d96-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="17d96-128">Namespace</span><span class="sxs-lookup"><span data-stu-id="17d96-128">Namespace</span></span>|<span data-ttu-id="17d96-129">Definido em root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="17d96-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="17d96-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="17d96-130">See Also</span></span>  
 <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>
