---
title: BinaryMessageEncodingBindingElement
ms.date: 03/30/2017
ms.assetid: e2bb3cdd-3bbd-4bb5-85fe-570457500a66
ms.openlocfilehash: e0551e7b4b05151490625912742aa6b26ef0216e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59768053"
---
# <a name="binarymessageencodingbindingelement"></a><span data-ttu-id="7bbd3-102">BinaryMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="7bbd3-102">BinaryMessageEncodingBindingElement</span></span>
<span data-ttu-id="7bbd3-103">BinaryMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="7bbd3-103">BinaryMessageEncodingBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7bbd3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7bbd3-104">Syntax</span></span>  
  
```csharp  
class BinaryMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  sint32 MaxReadPoolSize;  
  sint32 MaxSessionSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="7bbd3-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="7bbd3-105">Methods</span></span>  
 <span data-ttu-id="7bbd3-106">A classe BinaryMessageEncodingBindingElement não define quaisquer métodos.</span><span class="sxs-lookup"><span data-stu-id="7bbd3-106">The BinaryMessageEncodingBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="7bbd3-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="7bbd3-107">Properties</span></span>  
 <span data-ttu-id="7bbd3-108">A classe BinaryMessageEncodingBindingElement tem as seguintes propriedades.</span><span class="sxs-lookup"><span data-stu-id="7bbd3-108">The BinaryMessageEncodingBindingElement class has the following properties.</span></span>  
  
## <a name="maxreadpoolsize"></a><span data-ttu-id="7bbd3-109">MaxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="7bbd3-109">MaxReadPoolSize</span></span>  
 <span data-ttu-id="7bbd3-110">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="7bbd3-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="7bbd3-111">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="7bbd3-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7bbd3-112">Um inteiro que define quantas mensagens pode ser lidas simultaneamente sem alocar novos leitores.</span><span class="sxs-lookup"><span data-stu-id="7bbd3-112">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span>  
  
## <a name="maxsessionsize"></a><span data-ttu-id="7bbd3-113">MaxSessionSize</span><span class="sxs-lookup"><span data-stu-id="7bbd3-113">MaxSessionSize</span></span>  
 <span data-ttu-id="7bbd3-114">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="7bbd3-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="7bbd3-115">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="7bbd3-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7bbd3-116">Um valor que especifica o tamanho, em bytes, do buffer usado para codificação.</span><span class="sxs-lookup"><span data-stu-id="7bbd3-116">A value that specifies the size, in bytes, of the buffer used for encoding.</span></span>  
  
## <a name="maxwritepoolsize"></a><span data-ttu-id="7bbd3-117">MaxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="7bbd3-117">MaxWritePoolSize</span></span>  
 <span data-ttu-id="7bbd3-118">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="7bbd3-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="7bbd3-119">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="7bbd3-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7bbd3-120">Um inteiro que define quantas mensagens pode ser enviado simultaneamente sem alocar novos escritores.</span><span class="sxs-lookup"><span data-stu-id="7bbd3-120">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span>  
  
## <a name="readerquotas"></a><span data-ttu-id="7bbd3-121">ReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="7bbd3-121">ReaderQuotas</span></span>  
 <span data-ttu-id="7bbd3-122">Tipo de dados: XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="7bbd3-122">Data type: XmlDictionaryReaderQuotas</span></span>  
  
 <span data-ttu-id="7bbd3-123">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="7bbd3-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7bbd3-124">As cotas dos leitores.</span><span class="sxs-lookup"><span data-stu-id="7bbd3-124">The quotas of the readers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7bbd3-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7bbd3-125">Requirements</span></span>  
  
|<span data-ttu-id="7bbd3-126">MOF</span><span class="sxs-lookup"><span data-stu-id="7bbd3-126">MOF</span></span>|<span data-ttu-id="7bbd3-127">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="7bbd3-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="7bbd3-128">Namespace</span><span class="sxs-lookup"><span data-stu-id="7bbd3-128">Namespace</span></span>|<span data-ttu-id="7bbd3-129">Definido no root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="7bbd3-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7bbd3-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7bbd3-130">See also</span></span>

- <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>
