---
title: MtomMessageEncodingBindingElement
ms.date: 03/30/2017
ms.assetid: 4a9c6c3d-e561-4b2d-a693-7e84bdd3534a
ms.openlocfilehash: ad4f2cc3b03111854d10d6a1c1128f090a629a07
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54490967"
---
# <a name="mtommessageencodingbindingelement"></a><span data-ttu-id="e4ef0-102">MtomMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="e4ef0-102">MtomMessageEncodingBindingElement</span></span>
<span data-ttu-id="e4ef0-103">MtomMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="e4ef0-103">MtomMessageEncodingBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4ef0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e4ef0-104">Syntax</span></span>  
  
```csharp
class MtomMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  string Encoding;  
  sint32 MaxReadPoolSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="e4ef0-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="e4ef0-105">Methods</span></span>  
 <span data-ttu-id="e4ef0-106">A classe MtomMessageEncodingBindingElement não define quaisquer métodos.</span><span class="sxs-lookup"><span data-stu-id="e4ef0-106">The MtomMessageEncodingBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="e4ef0-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="e4ef0-107">Properties</span></span>  
 <span data-ttu-id="e4ef0-108">A classe MtomMessageEncodingBindingElement tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="e4ef0-108">The MtomMessageEncodingBindingElement class has the following properties:</span></span>  
  
### <a name="encoding"></a><span data-ttu-id="e4ef0-109">Codificando</span><span class="sxs-lookup"><span data-stu-id="e4ef0-109">Encoding</span></span>  
 <span data-ttu-id="e4ef0-110">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="e4ef0-110">Data type: string</span></span>  
  
 <span data-ttu-id="e4ef0-111">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="e4ef0-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e4ef0-112">O conjunto de caracteres codificação a ser usada para emitir mensagens na associação.</span><span class="sxs-lookup"><span data-stu-id="e4ef0-112">The character set encoding to be used for emitting messages on the binding.</span></span>  
  
### <a name="maxreadpoolsize"></a><span data-ttu-id="e4ef0-113">MaxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="e4ef0-113">MaxReadPoolSize</span></span>  
 <span data-ttu-id="e4ef0-114">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="e4ef0-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="e4ef0-115">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="e4ef0-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e4ef0-116">Um inteiro que define quantas mensagens pode ser lidas simultaneamente sem alocar novos leitores.</span><span class="sxs-lookup"><span data-stu-id="e4ef0-116">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span>  
  
### <a name="maxwritepoolsize"></a><span data-ttu-id="e4ef0-117">MaxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="e4ef0-117">MaxWritePoolSize</span></span>  
 <span data-ttu-id="e4ef0-118">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="e4ef0-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="e4ef0-119">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="e4ef0-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e4ef0-120">Um inteiro que define quantas mensagens pode ser enviado simultaneamente sem alocar novos escritores.</span><span class="sxs-lookup"><span data-stu-id="e4ef0-120">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span>  
  
### <a name="readerquotas"></a><span data-ttu-id="e4ef0-121">ReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="e4ef0-121">ReaderQuotas</span></span>  
 <span data-ttu-id="e4ef0-122">Tipo de dados: XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="e4ef0-122">Data type: XmlDictionaryReaderQuotas</span></span>  
  
 <span data-ttu-id="e4ef0-123">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="e4ef0-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e4ef0-124">As cotas dos leitores.</span><span class="sxs-lookup"><span data-stu-id="e4ef0-124">The quotas of the readers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e4ef0-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e4ef0-125">Requirements</span></span>  
  
|<span data-ttu-id="e4ef0-126">MOF</span><span class="sxs-lookup"><span data-stu-id="e4ef0-126">MOF</span></span>|<span data-ttu-id="e4ef0-127">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="e4ef0-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="e4ef0-128">Namespace</span><span class="sxs-lookup"><span data-stu-id="e4ef0-128">Namespace</span></span>|<span data-ttu-id="e4ef0-129">Definido no root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="e4ef0-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e4ef0-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e4ef0-130">See also</span></span>
- <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>
