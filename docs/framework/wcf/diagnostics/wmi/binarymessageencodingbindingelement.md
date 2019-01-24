---
title: BinaryMessageEncodingBindingElement
ms.date: 03/30/2017
ms.assetid: e2bb3cdd-3bbd-4bb5-85fe-570457500a66
ms.openlocfilehash: 330496d5f0f80affcb6bc44a1f66f4321a635f00
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54580584"
---
# <a name="binarymessageencodingbindingelement"></a><span data-ttu-id="6e14a-102">BinaryMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="6e14a-102">BinaryMessageEncodingBindingElement</span></span>
<span data-ttu-id="6e14a-103">BinaryMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="6e14a-103">BinaryMessageEncodingBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e14a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6e14a-104">Syntax</span></span>  
  
```csharp  
class BinaryMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  sint32 MaxReadPoolSize;  
  sint32 MaxSessionSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="6e14a-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="6e14a-105">Methods</span></span>  
 <span data-ttu-id="6e14a-106">A classe BinaryMessageEncodingBindingElement não define quaisquer métodos.</span><span class="sxs-lookup"><span data-stu-id="6e14a-106">The BinaryMessageEncodingBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="6e14a-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="6e14a-107">Properties</span></span>  
 <span data-ttu-id="6e14a-108">A classe BinaryMessageEncodingBindingElement tem as seguintes propriedades.</span><span class="sxs-lookup"><span data-stu-id="6e14a-108">The BinaryMessageEncodingBindingElement class has the following properties.</span></span>  
  
## <a name="maxreadpoolsize"></a><span data-ttu-id="6e14a-109">MaxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="6e14a-109">MaxReadPoolSize</span></span>  
 <span data-ttu-id="6e14a-110">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="6e14a-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="6e14a-111">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="6e14a-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6e14a-112">Um inteiro que define quantas mensagens pode ser lidas simultaneamente sem alocar novos leitores.</span><span class="sxs-lookup"><span data-stu-id="6e14a-112">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span>  
  
## <a name="maxsessionsize"></a><span data-ttu-id="6e14a-113">MaxSessionSize</span><span class="sxs-lookup"><span data-stu-id="6e14a-113">MaxSessionSize</span></span>  
 <span data-ttu-id="6e14a-114">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="6e14a-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="6e14a-115">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="6e14a-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6e14a-116">Um valor que especifica o tamanho, em bytes, do buffer usado para codificação.</span><span class="sxs-lookup"><span data-stu-id="6e14a-116">A value that specifies the size, in bytes, of the buffer used for encoding.</span></span>  
  
## <a name="maxwritepoolsize"></a><span data-ttu-id="6e14a-117">MaxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="6e14a-117">MaxWritePoolSize</span></span>  
 <span data-ttu-id="6e14a-118">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="6e14a-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="6e14a-119">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="6e14a-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6e14a-120">Um inteiro que define quantas mensagens pode ser enviado simultaneamente sem alocar novos escritores.</span><span class="sxs-lookup"><span data-stu-id="6e14a-120">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span>  
  
## <a name="readerquotas"></a><span data-ttu-id="6e14a-121">ReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="6e14a-121">ReaderQuotas</span></span>  
 <span data-ttu-id="6e14a-122">Tipo de dados: XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="6e14a-122">Data type: XmlDictionaryReaderQuotas</span></span>  
  
 <span data-ttu-id="6e14a-123">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="6e14a-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6e14a-124">As cotas dos leitores.</span><span class="sxs-lookup"><span data-stu-id="6e14a-124">The quotas of the readers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6e14a-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6e14a-125">Requirements</span></span>  
  
|<span data-ttu-id="6e14a-126">MOF</span><span class="sxs-lookup"><span data-stu-id="6e14a-126">MOF</span></span>|<span data-ttu-id="6e14a-127">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="6e14a-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="6e14a-128">Namespace</span><span class="sxs-lookup"><span data-stu-id="6e14a-128">Namespace</span></span>|<span data-ttu-id="6e14a-129">Definido no root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="6e14a-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6e14a-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6e14a-130">See also</span></span>
- <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>
