---
title: TextMessageEncodingBindingElement
ms.date: 03/30/2017
ms.assetid: 885e2d7a-3436-4093-bc5f-0a404c62acdc
ms.openlocfilehash: 67c1083daa9acfd204d4de50d4e9178b25aafcf0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61858384"
---
# <a name="textmessageencodingbindingelement"></a><span data-ttu-id="4f5f6-102">TextMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="4f5f6-102">TextMessageEncodingBindingElement</span></span>
<span data-ttu-id="4f5f6-103">TextMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="4f5f6-103">TextMessageEncodingBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f5f6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4f5f6-104">Syntax</span></span>  
  
```csharp
class TextMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  string Encoding;  
  sint32 MaxReadPoolSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="4f5f6-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="4f5f6-105">Methods</span></span>  
 <span data-ttu-id="4f5f6-106">A classe TextMessageEncodingBindingElement não define quaisquer métodos.</span><span class="sxs-lookup"><span data-stu-id="4f5f6-106">The TextMessageEncodingBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="4f5f6-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="4f5f6-107">Properties</span></span>  
 <span data-ttu-id="4f5f6-108">A classe TextMessageEncodingBindingElement tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="4f5f6-108">The TextMessageEncodingBindingElement class has the following properties:</span></span>  
  
### <a name="encoding"></a><span data-ttu-id="4f5f6-109">Codificando</span><span class="sxs-lookup"><span data-stu-id="4f5f6-109">Encoding</span></span>  
 <span data-ttu-id="4f5f6-110">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="4f5f6-110">Data type: string</span></span>  
  
 <span data-ttu-id="4f5f6-111">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="4f5f6-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4f5f6-112">O conjunto de caracteres codificação a ser usada para emitir mensagens na associação.</span><span class="sxs-lookup"><span data-stu-id="4f5f6-112">The character set encoding to be used for emitting messages on the binding.</span></span>  
  
### <a name="maxreadpoolsize"></a><span data-ttu-id="4f5f6-113">MaxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="4f5f6-113">MaxReadPoolSize</span></span>  
 <span data-ttu-id="4f5f6-114">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="4f5f6-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="4f5f6-115">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="4f5f6-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4f5f6-116">Um inteiro que define quantas mensagens pode ser lidas simultaneamente sem alocar novos leitores.</span><span class="sxs-lookup"><span data-stu-id="4f5f6-116">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span>  
  
### <a name="maxwritepoolsize"></a><span data-ttu-id="4f5f6-117">MaxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="4f5f6-117">MaxWritePoolSize</span></span>  
 <span data-ttu-id="4f5f6-118">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="4f5f6-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="4f5f6-119">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="4f5f6-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4f5f6-120">Um inteiro que define quantas mensagens pode ser enviado simultaneamente sem alocar novos escritores.</span><span class="sxs-lookup"><span data-stu-id="4f5f6-120">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span>  
  
### <a name="readerquotas"></a><span data-ttu-id="4f5f6-121">ReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="4f5f6-121">ReaderQuotas</span></span>  
 <span data-ttu-id="4f5f6-122">Tipo de dados: XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="4f5f6-122">Data type: XmlDictionaryReaderQuotas</span></span>  
  
 <span data-ttu-id="4f5f6-123">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="4f5f6-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4f5f6-124">As cotas dos leitores.</span><span class="sxs-lookup"><span data-stu-id="4f5f6-124">The quotas of the readers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4f5f6-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4f5f6-125">Requirements</span></span>  
  
|<span data-ttu-id="4f5f6-126">MOF</span><span class="sxs-lookup"><span data-stu-id="4f5f6-126">MOF</span></span>|<span data-ttu-id="4f5f6-127">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="4f5f6-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="4f5f6-128">Namespace</span><span class="sxs-lookup"><span data-stu-id="4f5f6-128">Namespace</span></span>|<span data-ttu-id="4f5f6-129">Definido no root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="4f5f6-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4f5f6-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4f5f6-130">See also</span></span>

- <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>
