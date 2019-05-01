---
title: BinaryMessageEncodingBindingElement
ms.date: 03/30/2017
ms.assetid: e2bb3cdd-3bbd-4bb5-85fe-570457500a66
ms.openlocfilehash: e0551e7b4b05151490625912742aa6b26ef0216e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61964088"
---
# <a name="binarymessageencodingbindingelement"></a><span data-ttu-id="1c0ac-102">BinaryMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="1c0ac-102">BinaryMessageEncodingBindingElement</span></span>
<span data-ttu-id="1c0ac-103">BinaryMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="1c0ac-103">BinaryMessageEncodingBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c0ac-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1c0ac-104">Syntax</span></span>  
  
```csharp  
class BinaryMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  sint32 MaxReadPoolSize;  
  sint32 MaxSessionSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="1c0ac-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="1c0ac-105">Methods</span></span>  
 <span data-ttu-id="1c0ac-106">A classe BinaryMessageEncodingBindingElement não define quaisquer métodos.</span><span class="sxs-lookup"><span data-stu-id="1c0ac-106">The BinaryMessageEncodingBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="1c0ac-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="1c0ac-107">Properties</span></span>  
 <span data-ttu-id="1c0ac-108">A classe BinaryMessageEncodingBindingElement tem as seguintes propriedades.</span><span class="sxs-lookup"><span data-stu-id="1c0ac-108">The BinaryMessageEncodingBindingElement class has the following properties.</span></span>  
  
## <a name="maxreadpoolsize"></a><span data-ttu-id="1c0ac-109">MaxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="1c0ac-109">MaxReadPoolSize</span></span>  
 <span data-ttu-id="1c0ac-110">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="1c0ac-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="1c0ac-111">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="1c0ac-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1c0ac-112">Um inteiro que define quantas mensagens pode ser lidas simultaneamente sem alocar novos leitores.</span><span class="sxs-lookup"><span data-stu-id="1c0ac-112">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span>  
  
## <a name="maxsessionsize"></a><span data-ttu-id="1c0ac-113">MaxSessionSize</span><span class="sxs-lookup"><span data-stu-id="1c0ac-113">MaxSessionSize</span></span>  
 <span data-ttu-id="1c0ac-114">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="1c0ac-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="1c0ac-115">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="1c0ac-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1c0ac-116">Um valor que especifica o tamanho, em bytes, do buffer usado para codificação.</span><span class="sxs-lookup"><span data-stu-id="1c0ac-116">A value that specifies the size, in bytes, of the buffer used for encoding.</span></span>  
  
## <a name="maxwritepoolsize"></a><span data-ttu-id="1c0ac-117">MaxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="1c0ac-117">MaxWritePoolSize</span></span>  
 <span data-ttu-id="1c0ac-118">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="1c0ac-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="1c0ac-119">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="1c0ac-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1c0ac-120">Um inteiro que define quantas mensagens pode ser enviado simultaneamente sem alocar novos escritores.</span><span class="sxs-lookup"><span data-stu-id="1c0ac-120">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span>  
  
## <a name="readerquotas"></a><span data-ttu-id="1c0ac-121">ReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="1c0ac-121">ReaderQuotas</span></span>  
 <span data-ttu-id="1c0ac-122">Tipo de dados: XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="1c0ac-122">Data type: XmlDictionaryReaderQuotas</span></span>  
  
 <span data-ttu-id="1c0ac-123">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="1c0ac-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1c0ac-124">As cotas dos leitores.</span><span class="sxs-lookup"><span data-stu-id="1c0ac-124">The quotas of the readers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1c0ac-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1c0ac-125">Requirements</span></span>  
  
|<span data-ttu-id="1c0ac-126">MOF</span><span class="sxs-lookup"><span data-stu-id="1c0ac-126">MOF</span></span>|<span data-ttu-id="1c0ac-127">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="1c0ac-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="1c0ac-128">Namespace</span><span class="sxs-lookup"><span data-stu-id="1c0ac-128">Namespace</span></span>|<span data-ttu-id="1c0ac-129">Definido no root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="1c0ac-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1c0ac-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1c0ac-130">See also</span></span>

- <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>
