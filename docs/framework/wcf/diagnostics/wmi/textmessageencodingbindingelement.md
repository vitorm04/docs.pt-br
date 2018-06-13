---
title: TextMessageEncodingBindingElement
ms.date: 03/30/2017
ms.assetid: 885e2d7a-3436-4093-bc5f-0a404c62acdc
ms.openlocfilehash: f9b94e946413967cc14282e85743a23327683b89
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33486010"
---
# <a name="textmessageencodingbindingelement"></a><span data-ttu-id="4316c-102">TextMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="4316c-102">TextMessageEncodingBindingElement</span></span>
<span data-ttu-id="4316c-103">TextMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="4316c-103">TextMessageEncodingBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4316c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4316c-104">Syntax</span></span>  
  
```  
class TextMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  string Encoding;  
  sint32 MaxReadPoolSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="4316c-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="4316c-105">Methods</span></span>  
 <span data-ttu-id="4316c-106">A classe TextMessageEncodingBindingElement não define nenhum método.</span><span class="sxs-lookup"><span data-stu-id="4316c-106">The TextMessageEncodingBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="4316c-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="4316c-107">Properties</span></span>  
 <span data-ttu-id="4316c-108">A classe TextMessageEncodingBindingElement tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="4316c-108">The TextMessageEncodingBindingElement class has the following properties:</span></span>  
  
### <a name="encoding"></a><span data-ttu-id="4316c-109">Codificando</span><span class="sxs-lookup"><span data-stu-id="4316c-109">Encoding</span></span>  
 <span data-ttu-id="4316c-110">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="4316c-110">Data type: string</span></span>  
  
 <span data-ttu-id="4316c-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="4316c-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4316c-112">O conjunto de caracteres codificação a ser usada para emitir mensagens na associação.</span><span class="sxs-lookup"><span data-stu-id="4316c-112">The character set encoding to be used for emitting messages on the binding.</span></span>  
  
### <a name="maxreadpoolsize"></a><span data-ttu-id="4316c-113">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="4316c-113">MaxReadPoolSize</span></span>  
 <span data-ttu-id="4316c-114">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="4316c-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="4316c-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="4316c-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4316c-116">Um inteiro que define quantas mensagens pode ser lidas simultaneamente sem alocar novos leitores.</span><span class="sxs-lookup"><span data-stu-id="4316c-116">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span>  
  
### <a name="maxwritepoolsize"></a><span data-ttu-id="4316c-117">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="4316c-117">MaxWritePoolSize</span></span>  
 <span data-ttu-id="4316c-118">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="4316c-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="4316c-119">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="4316c-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4316c-120">Um inteiro que define quantas mensagens pode ser enviado simultaneamente sem alocar novos escritores.</span><span class="sxs-lookup"><span data-stu-id="4316c-120">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span>  
  
### <a name="readerquotas"></a><span data-ttu-id="4316c-121">ReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="4316c-121">ReaderQuotas</span></span>  
 <span data-ttu-id="4316c-122">Tipo de dados: XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="4316c-122">Data type: XmlDictionaryReaderQuotas</span></span>  
  
 <span data-ttu-id="4316c-123">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="4316c-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4316c-124">As cotas dos leitores.</span><span class="sxs-lookup"><span data-stu-id="4316c-124">The quotas of the readers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4316c-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4316c-125">Requirements</span></span>  
  
|<span data-ttu-id="4316c-126">MOF</span><span class="sxs-lookup"><span data-stu-id="4316c-126">MOF</span></span>|<span data-ttu-id="4316c-127">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="4316c-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="4316c-128">Namespace</span><span class="sxs-lookup"><span data-stu-id="4316c-128">Namespace</span></span>|<span data-ttu-id="4316c-129">Definido em root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="4316c-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4316c-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4316c-130">See Also</span></span>  
 <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>
