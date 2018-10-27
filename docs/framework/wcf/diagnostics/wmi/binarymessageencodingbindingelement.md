---
title: BinaryMessageEncodingBindingElement
ms.date: 03/30/2017
ms.assetid: e2bb3cdd-3bbd-4bb5-85fe-570457500a66
ms.openlocfilehash: 326fe6a7ca8dc5dba0dd64b1c5fc97cec49279c7
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50180868"
---
# <a name="binarymessageencodingbindingelement"></a><span data-ttu-id="f358b-102">BinaryMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="f358b-102">BinaryMessageEncodingBindingElement</span></span>
<span data-ttu-id="f358b-103">BinaryMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="f358b-103">BinaryMessageEncodingBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f358b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f358b-104">Syntax</span></span>  
  
```csharp  
class BinaryMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  sint32 MaxReadPoolSize;  
  sint32 MaxSessionSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="f358b-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="f358b-105">Methods</span></span>  
 <span data-ttu-id="f358b-106">A classe BinaryMessageEncodingBindingElement não define quaisquer métodos.</span><span class="sxs-lookup"><span data-stu-id="f358b-106">The BinaryMessageEncodingBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="f358b-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="f358b-107">Properties</span></span>  
 <span data-ttu-id="f358b-108">A classe BinaryMessageEncodingBindingElement tem as seguintes propriedades.</span><span class="sxs-lookup"><span data-stu-id="f358b-108">The BinaryMessageEncodingBindingElement class has the following properties.</span></span>  
  
## <a name="maxreadpoolsize"></a><span data-ttu-id="f358b-109">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="f358b-109">MaxReadPoolSize</span></span>  
 <span data-ttu-id="f358b-110">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="f358b-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="f358b-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="f358b-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f358b-112">Um inteiro que define quantas mensagens pode ser lidas simultaneamente sem alocar novos leitores.</span><span class="sxs-lookup"><span data-stu-id="f358b-112">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span>  
  
## <a name="maxsessionsize"></a><span data-ttu-id="f358b-113">maxSessionSize</span><span class="sxs-lookup"><span data-stu-id="f358b-113">MaxSessionSize</span></span>  
 <span data-ttu-id="f358b-114">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="f358b-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="f358b-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="f358b-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f358b-116">Um valor que especifica o tamanho, em bytes, do buffer usado para codificação.</span><span class="sxs-lookup"><span data-stu-id="f358b-116">A value that specifies the size, in bytes, of the buffer used for encoding.</span></span>  
  
## <a name="maxwritepoolsize"></a><span data-ttu-id="f358b-117">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="f358b-117">MaxWritePoolSize</span></span>  
 <span data-ttu-id="f358b-118">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="f358b-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="f358b-119">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="f358b-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f358b-120">Um inteiro que define quantas mensagens pode ser enviado simultaneamente sem alocar novos escritores.</span><span class="sxs-lookup"><span data-stu-id="f358b-120">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span>  
  
## <a name="readerquotas"></a><span data-ttu-id="f358b-121">readerQuotas</span><span class="sxs-lookup"><span data-stu-id="f358b-121">ReaderQuotas</span></span>  
 <span data-ttu-id="f358b-122">Tipo de dados: XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="f358b-122">Data type: XmlDictionaryReaderQuotas</span></span>  
  
 <span data-ttu-id="f358b-123">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="f358b-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f358b-124">As cotas dos leitores.</span><span class="sxs-lookup"><span data-stu-id="f358b-124">The quotas of the readers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f358b-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f358b-125">Requirements</span></span>  
  
|<span data-ttu-id="f358b-126">MOF</span><span class="sxs-lookup"><span data-stu-id="f358b-126">MOF</span></span>|<span data-ttu-id="f358b-127">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="f358b-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="f358b-128">Namespace</span><span class="sxs-lookup"><span data-stu-id="f358b-128">Namespace</span></span>|<span data-ttu-id="f358b-129">Definido no root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="f358b-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f358b-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f358b-130">See Also</span></span>  
 <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>
